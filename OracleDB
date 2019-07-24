import cx_Oracle

class DB:
    def __init__(self, host, port, user, password, service):
        CONN_INFO = {
            'host': host,
            'port': port,
            'user': user,
            'psw': password,
            'service': service
        }
        CONN_STR = '{user}/{psw}@{host}:{port}/{service}'.format(**CONN_INFO)
        self.conn = cx_Oracle.connect(CONN_STR)

    def query(self, query, params=None):
        cursor = self.conn.cursor()
        cursor.execute(query)
        column_names_list = [x[0] for x in cursor.description]
        result_dicts = [dict(zip(column_names_list, row)) for row in cursor.fetchall()]
        cursor.close()
        return result_dicts
