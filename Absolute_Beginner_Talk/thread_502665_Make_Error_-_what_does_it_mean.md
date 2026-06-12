---
title: "Make Error - what does it mean?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by arsenik on 2007-07-16
I run ./reconf fine..
then ./configure fine

and then when i do make it runs for a while and then....

....
-I/usr/include/openssl -I/usr/local/include/openssl -I. -I./../../dep/include  -I/usr/include/mysql -I/usr/local/include/mysql -I/usr/include/openssl -I/usr/local/include/openssl   -MT PostgreDatabase.o -MD -MP -MF ".deps/PostgreDatabase.Tpo" -c -o PostgreDatabase.o `test -f 'Database/impl/PostgreDatabase.cpp' || echo './'`Database/impl/PostgreDatabase.cpp; \
then mv -f ".deps/PostgreDatabase.Tpo" ".deps/PostgreDatabase.Po"; else rm -f ".deps/PostgreDatabase.Tpo"; exit 1; fi
rm -f libdatabase.a
ar cru libdatabase.a DBC.o Database.o DBCStores.o dbcfile.o MySQLDatabase.o PostgreDatabase.o
ranlib libdatabase.a
make[3]: *** No rule to make target `Network/Socket.cpp', needed by `Socket.o'.  Stop.
make[3]: Leaving directory `/home/antrix/antrix/src/shared'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/antrix/antrix/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/antrix/antrix'
make: *** [all] Error 2
[root@wvu antrix]#

...

What do the errors mean? do they give me any hints on what I need to fix?

Thanks in advance.

---

### Post by Happy_Man on 2007-07-16
Have you tried running "make install" anyway? Sometimes, errors are thrown, but you can still keep going.

---

### Post by arsenik on 2007-07-16
make install also gives an error. so I guess the problem with make is important.

---

