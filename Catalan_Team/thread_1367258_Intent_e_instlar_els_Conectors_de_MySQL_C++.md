---
title: "Intent e instlar els Conectors de MySQL C++"
date: 2009-12-29
forum: Catalan Team
---

### Post by carlesbm on 2009-12-29
Hola

   Estic desesperat en el meu intent de poder realitzar una aplicació en C++ per aixó he de accedir a una base de dades MySQL i he descarregat el conector de la web oficial.

   Segueixo les instruccions i en el moment de fer un make m'apareix els següent missatge:

carles@carles-Despatx:~/democodeblocks/mysql-connector-c++-1.0.5$ make
[  0%] Building CXX object driver/CMakeFiles/mysqlcppconn.dir/mysql_art_resultset.o
/home/carles/democodeblocks/mysql-connector-c++-1.0.5/driver/mysql_art_resultset.cpp: In member function ‘std::string sql::mysql::MyVal::getString()’:
/home/carles/democodeblocks/mysql-connector-c++-1.0.5/driver/mysql_art_resultset.cpp:57: error: ‘snprintf’ was not declared in this scope
/home/carles/democodeblocks/mysql-connector-c++-1.0.5/driver/mysql_art_resultset.cpp:63: error: ‘snprintf’ was not declared in this scope
/home/carles/democodeblocks/mysql-connector-c++-1.0.5/driver/mysql_art_resultset.cpp:69: error: ‘snprintf’ was not declared in this scope
/home/carles/democodeblocks/mysql-connector-c++-1.0.5/driver/mysql_art_resultset.cpp:75: error: ‘snprintf’ was not declared in this scope
make[2]: *** [driver/CMakeFiles/mysqlcppconn.dir/mysql_art_resultset.o] Error 1
make[1]: *** [driver/CMakeFiles/mysqlcppconn.dir/all] Error 2
make: *** [all] Error 2
carles@carles-Despatx:~/democodeblocks/mysql-connector-c++-1.0.5$ 

Algu hem pot donar algun consell que no he sabut reobar per la red de com solucionar aixó.

Moltes gracies

---

