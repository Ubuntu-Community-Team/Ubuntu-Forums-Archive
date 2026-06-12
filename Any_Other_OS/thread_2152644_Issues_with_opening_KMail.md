---
title: "Issues with opening KMail"
date: 2013-06-08
forum: Any Other OS
---

### Post by silentarts on 2013-06-08
Whenever I open KMail, it says "the akonadi personal information management service is not operational"


I have done some research and I was reading that I had to go to /root/.config/akonadi/ and edit akonadiserverrc. I changed the Driver=*whatever* to Driver=QMYSQL. I then typed akonadictl start in Terminal and this is what I got below:




```
[root@localhost ~]# akonadictl start
[root@localhost ~]# Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
search paths:  ("/usr/lib/qt-3.3/bin", "/usr/lib/ccache", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/root/bin", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Database process exited unexpectedly during initial connection!
executable: "/usr/libexec/mysqld"
arguments: ("--defaults-file=/root/.local/share/akonadi/mysql.conf", "--datadir=/root/.local/share/akonadi/db_data/", "--socket=/root/.local/share/akonadi/socket-localhost.localdomain/mysql.socket")
stdout: ""
stderr: "130608 11:50:14 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!


130608 11:50:14 [ERROR] Aborting


130608 11:50:14 [Note] /usr/libexec/mysqld: Shutdown complete


"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x36) [0x8092406]
1: akonadiserver() [0x809276c]
2: [0xb77da400]
3: [0xb77da424]
4: /lib/libc.so.6(gsignal+0x4f) [0x4f149b7f]
5: /lib/libc.so.6(abort+0x143) [0x4f14b4d3]
6: /lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x96) [0x4fcd8336]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xda) [0x809450a]
8: /lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xe0) [0x4fd82990]
9: /lib/libQtCore.so.4() [0x4fd8ed6e]
10: /lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3f) [0x4fd9806f]
11: akonadiserver(_ZN13DbConfigMysql19startInternalServerEv+0x1956) [0x81033d6]
12: akonadiserver(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xe3) [0x8095253]
13: akonadiserver(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xc8) [0x8096218]
14: akonadiserver(_ZN7Akonadi13AkonadiServer8instanceEv+0x46) [0x8097866]
15: akonadiserver(main+0x261) [0x808bac1]
16: /lib/libc.so.6(__libc_start_main+0xf5) [0x4f134865]
17: akonadiserver() [0x808c631]
]
"
ProcessControl: Application 'akonadiserver' returned with exit code 255 (Unknown error)
search paths:  ("/usr/lib/qt-3.3/bin", "/usr/lib/ccache", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/root/bin", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Database process exited unexpectedly during initial connection!
executable: "/usr/libexec/mysqld"
arguments: ("--defaults-file=/root/.local/share/akonadi/mysql.conf", "--datadir=/root/.local/share/akonadi/db_data/", "--socket=/root/.local/share/akonadi/socket-localhost.localdomain/mysql.socket")
stdout: ""
stderr: "130608 11:50:14 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!


130608 11:50:14 [ERROR] Aborting


130608 11:50:14 [Note] /usr/libexec/mysqld: Shutdown complete


"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x36) [0x8092406]
1: akonadiserver() [0x809276c]
2: [0xb7775400]
3: [0xb7775424]
4: /lib/libc.so.6(gsignal+0x4f) [0x4f149b7f]
5: /lib/libc.so.6(abort+0x143) [0x4f14b4d3]
6: /lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x96) [0x4fcd8336]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xda) [0x809450a]
8: /lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xe0) [0x4fd82990]
9: /lib/libQtCore.so.4() [0x4fd8ed6e]
10: /lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3f) [0x4fd9806f]
11: akonadiserver(_ZN13DbConfigMysql19startInternalServerEv+0x1956) [0x81033d6]
12: akonadiserver(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xe3) [0x8095253]
13: akonadiserver(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xc8) [0x8096218]
14: akonadiserver(_ZN7Akonadi13AkonadiServer8instanceEv+0x46) [0x8097866]
15: akonadiserver(main+0x261) [0x808bac1]
16: /lib/libc.so.6(__libc_start_main+0xf5) [0x4f134865]
17: akonadiserver() [0x808c631]
]
"
ProcessControl: Application 'akonadiserver' returned with exit code 255 (Unknown error)
search paths:  ("/usr/lib/qt-3.3/bin", "/usr/lib/ccache", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/root/bin", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Database process exited unexpectedly during initial connection!
executable: "/usr/libexec/mysqld"
arguments: ("--defaults-file=/root/.local/share/akonadi/mysql.conf", "--datadir=/root/.local/share/akonadi/db_data/", "--socket=/root/.local/share/akonadi/socket-localhost.localdomain/mysql.socket")
stdout: ""
stderr: "130608 11:50:14 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!


130608 11:50:14 [ERROR] Aborting


130608 11:50:14 [Note] /usr/libexec/mysqld: Shutdown complete


"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x36) [0x8092406]
1: akonadiserver() [0x809276c]
2: [0xb77c7400]
3: [0xb77c7424]
4: /lib/libc.so.6(gsignal+0x4f) [0x4f149b7f]
5: /lib/libc.so.6(abort+0x143) [0x4f14b4d3]
6: /lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x96) [0x4fcd8336]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xda) [0x809450a]
8: /lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xe0) [0x4fd82990]
9: /lib/libQtCore.so.4() [0x4fd8ed6e]
10: /lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3f) [0x4fd9806f]
11: akonadiserver(_ZN13DbConfigMysql19startInternalServerEv+0x1956) [0x81033d6]
12: akonadiserver(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xe3) [0x8095253]
13: akonadiserver(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xc8) [0x8096218]
14: akonadiserver(_ZN7Akonadi13AkonadiServer8instanceEv+0x46) [0x8097866]
15: akonadiserver(main+0x261) [0x808bac1]
16: /lib/libc.so.6(__libc_start_main+0xf5) [0x4f134865]
17: akonadiserver() [0x808c631]
]
"
ProcessControl: Application 'akonadiserver' returned with exit code 255 (Unknown error)
search paths:  ("/usr/lib/qt-3.3/bin", "/usr/lib/ccache", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/root/bin", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Database process exited unexpectedly during initial connection!
executable: "/usr/libexec/mysqld"
arguments: ("--defaults-file=/root/.local/share/akonadi/mysql.conf", "--datadir=/root/.local/share/akonadi/db_data/", "--socket=/root/.local/share/akonadi/socket-localhost.localdomain/mysql.socket")
stdout: ""
stderr: "130608 11:50:14 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!


130608 11:50:14 [ERROR] Aborting


130608 11:50:14 [Note] /usr/libexec/mysqld: Shutdown complete


"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x36) [0x8092406]
1: akonadiserver() [0x809276c]
2: [0xb7800400]
3: [0xb7800424]
4: /lib/libc.so.6(gsignal+0x4f) [0x4f149b7f]
5: /lib/libc.so.6(abort+0x143) [0x4f14b4d3]
6: /lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x96) [0x4fcd8336]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xda) [0x809450a]
8: /lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xe0) [0x4fd82990]
9: /lib/libQtCore.so.4() [0x4fd8ed6e]
10: /lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3f) [0x4fd9806f]
11: akonadiserver(_ZN13DbConfigMysql19startInternalServerEv+0x1956) [0x81033d6]
12: akonadiserver(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xe3) [0x8095253]
13: akonadiserver(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xc8) [0x8096218]
14: akonadiserver(_ZN7Akonadi13AkonadiServer8instanceEv+0x46) [0x8097866]
15: akonadiserver(main+0x261) [0x808bac1]
16: /lib/libc.so.6(__libc_start_main+0xf5) [0x4f134865]
17: akonadiserver() [0x808c631]
]
"
ProcessControl: Application 'akonadiserver' returned with exit code 255 (Unknown error)
"akonadiserver" crashed too often and will not be restarted! 


[root@localhost ~]# 

```








Please help me out!


If screenshots would make this easier for you, please let me know!


Tell me what to do to get this thing back up and running!


Thanks a lot!

---

### Post by oldos2er on 2013-06-08
What OS are you using? Regardless, shouldn't you edit your user's akonadiserverrc, not root's?

---

### Post by silentarts on 2013-06-08
I am using Fedora 18...

---

