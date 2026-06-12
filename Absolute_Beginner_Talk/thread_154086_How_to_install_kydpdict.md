---
title: "How to install kydpdict ??"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-04-02
Hi  !!
   
First of all: 
I installed : 

> ######## installing qt3
apt-get -f -y install qt3-dev-tools
apt-get -f -y install qt3-apps-dev
apt-get -f -y install libqt3-headers
apt-get -f -y install qca-dev
apt-get -f -y install libqt3c102-mt



> $ tar jxf kydpdict-0.6.0.tar.bz2
Nast&#281;pnie przechodzimy do utworzonego katalogu kydpdict-0.6.0 i przeprowadzamy standartowy proces kompilacji ( ./configure; make; make install)

cd kydpdict-0.6.0
QTDIR=/usr/share/qt3/lib
./configure --prefix=/usr

 make
.....
.....
$ su
Password:
# make install
with $ ./configure --prefix=/usr
i get the following error : 
cannot compile a simple QT execurateble.
Check you have the right $QTDIR
  
I dont really understand 'cos the echo $QTDIR gives:
/usr/share/qt3/lib
    
ls /usr/share/qt3/lib:
> ls /usr/share/qt3/lib
libqt-mt.prl  libqt-mt.so.3    libqui.prl  libqui.so.1
libqt-mt.so   libqt-mt.so.3.3  libqui.so   libqui.so.1.0

Thank you !!

Patrick

---

### Post by patrick295767 on 2006-04-09
SOLVED 
   
   
I made a very clear HOW TO there : [http://www.ubuntuforums.org/showthread.php?p=905770#post905770](http://www.ubuntuforums.org/showthread.php?p=905770#post905770)
  
If you like it, let me know !!
  
Patrick

---

