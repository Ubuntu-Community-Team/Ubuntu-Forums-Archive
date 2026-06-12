---
title: "trouble updating Miro"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-03-21
I am trying to update to the latest versio of miro.
I did as it says on this page [http://www.getmiro.com/download/ubuntu.php](http://www.getmiro.com/download/ubuntu.php)
However when i lsearch for miro in the packages part. It still lists the latest version as 1.1.2
How can i get the newest version?

---

### Post by compiledkernel on 2008-03-21
compile from source. 

[http://ftp.osuosl.org/pub/pculture.org/miro/src/](http://ftp.osuosl.org/pub/pculture.org/miro/src/)

read here for further info. 

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by Falc7 on 2008-03-22
I am trying to do that, i am following that guide, but once i have natigated to the directory and type in configure tis happens:
mj@mj-desktop:~/Desktop/Miro-1.2$ ./configure
bash: ./configure: No such file or directory

and it says i need to get checkinstall
mj@mj-desktop:~/Desktop/Miro-1.2$ sudo checkinstall
sudo: checkinstall: command not found

one more:
mj@mj-desktop:~/Desktop/Miro-1.2$ sudo make install
make: *** No rule to make target `install'. Stop.

---

### Post by zvacet on 2008-03-22
You have latest deb for Ubuntu.

```
gksudo gedit /etc/apt/sources.list
```

add line

deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/


save ans close


```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bleedingpowers on 2008-03-22
FYI: the repository doesn't have the latest build of Miro 1.2.

Therefore, I'm also building Miro 1.2  from source based on instructions at:
[https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs]("https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs")
:confused:  although, their documentation is incomplete as now...They don't tell you how to install it in your system...so one has to figure it out. Like this:

1) First, uninstall the older version of Miro (from your package manager)
   [INDENT]BUT, leave your Miro-data installed 'cuz your database is there...Also, you can back it up if you want to....
   The database is found in your /home/username/.miro[/INDENT]
2) Installing prerequisites:
```
sudo apt-get install subversion python libboost-python-dev python-gnome2 \
python-gnome2-extras python-gnome2-extras-dev python-pyrex python-gtk2 \
python-glade2 python-gtk2-dev firefox-dev libxine-dev gettext \
libxine1-ffmpeg libxmu-dev python-pysqlite2 libxv-dev libx11-dev \
libssl-dev libboost-date-time-dev libboost-filesystem-dev libboost-serialization-dev \
libboost-thread-dev
```

2) Running Miro from source
[INDENT]a) ```
cd wherever_you_unpacked_Miro-1.2/platform/gtk-x11
```
b)  The following line compiles and runs Miro in place and does not install the program on your system.
(I'm not sure if it's necessary)...I did it anyway
```
./run.sh
```
c) Install Miro
```
python setup.py install
```
just make sure you are in wherever_you_unpacked_Miro-1.2/platform/gtk-x11[/INDENT]

This worked for me after figuring out that MIRO is written in Python, so you have to installed as you would normally install a Python application.

Let me know if this helps.

---

### Post by tonieisner on 2008-03-23
I also had to install g++ before i could compile it.

```
sudo apt-get install g++
```

---

### Post by zvacet on 2008-03-23
@ **bleedingpowers**

> FYI: the repository doesn't have the latest build of Miro 1.2.

I know that and that is why I suggested to **add the line** which will give you latest version in synaptic.That´s all.

---

### Post by Falc7 on 2008-03-23
This is my terminal readout, when after i typed in part c
The last part just repeated itself seemingly endlessly

mj@mj-desktop:~$ cd /home/mj/Desktop/Miro-1.2/platform/gtk-x11
mj@mj-desktop:~/Desktop/Miro-1.2/platform/gtk-x11$ python setup.py install
Attempting to detect your system information
32bit x86 system detected
Linux operating system detected
Libraries mt
Using the Xine driver hack. If you experience trouble playing video,
   try setting USE_XINE_HACK to False in setup.py.
running install
running build
running build_py
copying /home/mj/Desktop/Miro-1.2/portable/dl_daemon/daemon.py -> build/lib.linux-i686-2.5/miro/dl_daemon
running build_ext
building 'miro.libtorrent' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -fPIC -I/home/mj/Desktop/Miro-1.2/portable/libtorrent/include -I/home/mj/Desktop/Miro-1.2/portable/libtorrent/include/libtorrent -I/usr/include/python2.5 -c /home/mj/Desktop/Miro-1.2/portable/libtorrent/src/torrent_handle.cpp -o build/temp.linux-i686-2.5/home/mj/Desktop/Miro-1.2/portable/libtorrent/src/torrent_handle.o -Wno-missing-braces -DHAVE_INCLUDE_LIBTORRENT_ASIO____ASIO_HPP=1 -DHAVE_INCLUDE_LIBTORRENT_ASIO_SSL_STREAM_HPP=1 -DHAVE_INCLUDE_LIBTORRENT_ASIO_IP_TCP_HPP=1 -DHAVE_PTHREAD=1 -DTORRENT_USE_OPENSSL=1 -DHAVE_SSL=1 -DNDEBUG=1 -O2
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -fPIC -I/home/mj/Desktop/Miro-1.2/portable/libtorrent/include -I/home/mj/Desktop/Miro-1.2/portable/libtorrent/include/libtorrent -I/usr/include/python2.5 -c /home/mj/Desktop/Miro-1.2/portable/libtorrent/src/torrent_info.cpp -o build/temp.linux-i686-2.5/home/mj/Desktop/Miro-1.2/portable/libtorrent/src/torrent_info.o -Wno-missing-braces -DHAVE_INCLUDE_LIBTORRENT_ASIO____ASIO_HPP=1 -DHAVE_INCLUDE_LIBTORRENT_ASIO_SSL_STREAM_HPP=1 -DHAVE_INCLUDE_LIBTORRENT_ASIO_IP_TCP_HPP=1 -DHAVE_PTHREAD=1 -DTORRENT_USE_OPENSSL=1 -DHAVE_SSL=1 -DNDEBUG=1 -O2


@znacet
The text file already had the line
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
But when i typed in sudo apt-get update && sudo apt-get upgrade
It updated WIne, but not Miro

---

### Post by bleedingpowers on 2008-03-23
**zvacet: **The Miro's official repository (the one you're directing us to) doesn't have the lastes Miro 1.2, yet...It has only up to miro_1.1.2-0pcf2.

Now, that's why our only option is to install Miro 1.2 from source.

**Falc7: **Before attempting to install Miro in your system, try running the script ```
./run.sh
``` as I suggested in my approach. It worked for me in that sequence...Also Make sure you're fulfilling all the prerequisites

---

### Post by Falc7 on 2008-03-23
The following happens when i try to run this code:
./run.sh

Again the last peice just repeats endlessly. If i wait longer will the repositories get Miro 1.2 later? Allowing me to install them that way?

mj@mj-desktop:~/Desktop/Miro-1.2/platform/gtk-x11$ ./run.sh
Attempting to detect your system information
32bit x86 system detected
Linux operating system detected
Libraries mt
Using the Xine driver hack. If you experience trouble playing video,
   try setting USE_XINE_HACK to False in setup.py.
running install
running build
running build_py
copying /home/mj/Desktop/Miro-1.2/portable/dl_daemon/daemon.py -> build/lib.linux-i686-2.5/miro/dl_daemon
running build_ext
building 'miro.libtorrent' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -fPIC -I/home/mj/Desktop/Miro-1.2/portable/libtorrent/include -I/home/mj/Desktop/Miro-1.2/portable/libtorrent/include/libtorrent -I/usr/include/python2.5 -c /home/mj/Desktop/Miro-1.2/portable/libtorrent/src/bt_peer_connection.cpp -o build/temp.linux-i686-2.5/home/mj/Desktop/Miro-1.2/portable/libtorrent/src/bt_peer_connection.o -Wno-missing-braces -DHAVE_INCLUDE_LIBTORRENT_ASIO____ASIO_HPP=1 -DHAVE_INCLUDE_LIBTORRENT_ASIO_SSL_STREAM_HPP=1 -DHAVE_INCLUDE_LIBTORRENT_ASIO_IP_TCP_HPP=1 -DHAVE_PTHREAD=1 -DTORRENT_USE_OPENSSL=1 -DHAVE_SSL=1 -DNDEBUG=1 -O2

---

### Post by tonieisner on 2008-03-23
Compiling miro can take some time, depending on your system.
However, during compilation the outputlines **look** very similar.
Give it some time to compile. On my old Pentium 4 Mobile, it took nearly 40 minutes to compile. But the restult was worth waiting.

---

### Post by zvacet on 2008-03-24
@ **bleedingpowers**


So,I have trouble reading.[Here](http://www.getmiro.com/download/)

---

### Post by Falc7 on 2008-03-24
ah yes you are right, Miro now starts when i complite the script, however i get this error, is it important or should i go right ahead and install miro?

WARNING  eventloop: Interrupted system call
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]

---

### Post by Annoyance on 2008-03-25
Miro 1.2 is in the repository.  I could not get it to install from the repository.

miro:
  Depends: libxine1 (<1.1.8) but 1.1.10-1~gutsy1 is to be installed

---

