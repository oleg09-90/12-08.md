# Резервное копирование баз данных

**Перваков Олег**

## Решения заданий

### Задание 1
![image](https://github.com/user-attachments/assets/45a81a68-4dff-4c93-b55d-ce50084635f1)
1.1 Для восстановления данных за предыдущей день оптимальным вариантом будет полное резервное копирование,в этом случае ежедневно создается полная копия баз данных,и если потребуется откат данных на 
предыдущей день,можно будет использовать эту копию 
1.2 Для восстановления данных за час до предполагаемой поломки лучше использовать инкреиентное резервное копирование,оно делает копии только тех данных которые изменились с момента последнего полного 
бэкапа или инкрементного бэкапа,можно настроить полный бэкап каждый день и инкрементные копии каждые несколько часов 
1.3 Моментальное переключение при сбое возможно с ипсользованием репликаций,данные из основной мастер базы копируются на slave-сервер,который может быть автоматически или вручную активирован 
в случае поломки,это обеспечит минимальную задержку при переключении
### Задание 2
![image](https://github.com/user-attachments/assets/a1f894cf-6ff0-4065-ac66-64e246caaced)
2.1 Примеры команд восстановления и резервного копирования в PostgreSQL:Резервное копирование с помощью pg_dump: pg_dump -U <username> -h <hostname> -p <port> -F c -b -v -f /path/to/backup_file.backup <dbname>
-U <username> - имя пользователя PostgreSQL
-h <hostname> - адрес сервера БД
-p <port> - порт подключения 
-F c - формат копии
-b - бэкап всех больших объектов 
-v - вывод команды в вербозном режиме 
-f /path/to/backup_file.backup - путь для сохранения резервной копии 
<dbname> - имя БД для резервного копирования 
Пример команды с помощью pg_restore: pg_restore -U <username> -h <hostname> -p <port> -d <dbname> -v /path/to/backup_file.backup
-U <username> - имя пользователя PostgreSQL
-h <hostname> - адрес сервера БД
-p <port> - порт подключения 
-d <dbname> - БД в которую выполняется восстановление 
-v - вывод команды в вербозном режиме 
/path/to/backup_file.backup - путь к файлу резервной копии
### Задание 3
![image](https://github.com/user-attachments/assets/e1f1216f-af26-4a6f-ba23-192d98814cd1)
Для выполнения полного резервного копирования в MySQL используется утилита xtrabackup
создается полное резервное копирование с помощью команды: xtrabackup --backup --target-dir=/path/to/backup --datadir=/var/lib/mysql
--backup - выполняет резервное копирование
--target-dir - каталог для хранения резервной копии
--datadir - путь к каталогу данных MySQL
Команда для инкрементного резервного копирования: xtrabackup --backup --target-dir=/path/to/incremental_backup --incremental-basedir=/path/to/backup --datadir=/var/lib/mysql
--incremental-basedir - путь к предыдущему полному или инкрементному бэкапу, на основе которого будет сделана инкрементная копия
--target-dir - каталог для хранения нового инкрементного бэкапа
