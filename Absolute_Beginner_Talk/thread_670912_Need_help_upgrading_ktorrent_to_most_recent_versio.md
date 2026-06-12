---
title: "Need help upgrading ktorrent to most recent version"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by rbrittner on 2008-01-18
Hello, I've recently switched from Windows so I need some help upgrading a version of Ktorrent on my box.  I currently have version 2.2.1 but there is a bug in that version which doesn't allow my machine to connect to my trackers.  anyways, I've downloaded the source code from the ktorrent site but need help compiling.   The site says to do this:

Compiling and installing from the source code goes as follows : (replacing X.Y by the correct version number) 
tar -xvzf ktorrent-X.Y.tar.gz 
cd ktorrent-X.Y 
./configure 
make 
make install

this is where I get lost.....I placed the source code folder in my tmp folder but need some help.  Do i have to navigate to that folder in the terminal.....and what is the wild card in linux so i don't have to type it all, windows it's *.  Many thanks

Ryan

---

### Post by rexxxlo on 2008-01-18
you might want to use ktorrent for some reason but i like deluge personally
easy gui  im a newb too so it helps while i learn linux better,just a comment 
its in the synaptic... deluge-torrent  i believe

---

### Post by wolfen69 on 2008-01-18
here [http://jdong.mit.edu/~jdong/motu/ktorrent_2.2.4-0ubuntu1~7.10prevu1_i386.deb](http://jdong.mit.edu/~jdong/motu/ktorrent_2.2.4-0ubuntu1~7.10prevu1_i386.deb) is the deb file for 2.2.4  just click to install.

---

### Post by jleaker01z on 2008-01-18
Let me simplify...

When you click the link to download the source, you can choose to save to disk, or open with the archive manager.  Either way the archive manager will unpack the file for you with a GUI.  (.tar.gz is kind of like a .zip file for windows).  Extract it into your home directory.  Then, open a terminal (Applications->Accessories->Terminal).  Type in cd /home/your user name/ktorrent-X.Y (or whatever...its normally a folder with the same name as the file you downloaded).  Then type:

sudo ./configure (will ask for your password)
sudo make
sudo make install

Presuming you have the necessary prerequisites (other programs ktorrent needs to operate) and the proper development files (these are files that compile a program from source, such as gcc and libc6) you are done and it is installed.  

It may or may not put an entry into your App menu.  If it doesnt you can run it from the terminal from within your desktop (probably with the command ktorrent).

Also take note:  Linux recognizes capitalizations.  So if anything you are trying to do, such as change to a directory, or run a file, it must be typed EXACTLY as it is on your hard drive.  So if the developers were to name the file KtoRRenT.x.Y, you would have to type it exactly like that for it to work.

---

### Post by jleaker01z on 2008-01-18
Oh and yes...* is the wildcard for Linux as well.  It's a holdover from the old DOS days.

---

### Post by rbrittner on 2008-01-18
Ok thanks guys, I really appreciate the help.  This linux change over would be a lot harder without help.

Thanks again.

---

### Post by monte48lowes on 2008-01-18
> **jleaker01z said:**
> 
sudo ./configure (will ask for your password)
sudo make
sudo make install


Configuring and compiling './configure' and 'make' do not require sudo. It is my preferrence to run those commands as a normal user. Just in case something happens, there is no write permissions to the system files.

Mike

---

### Post by kvonb on 2008-01-18
-

---

### Post by Christmas on 2008-01-18
So install 'build-essential' which contains GNU C compiler and some more utilities. Then install KTorrent's dependencies using this:
```
sudo apt-get build-dep ktorrent
```
Untar the archive and compile KTorrent:
```
./configure
make
sudo make install

```
This should do it.

---

### Post by kvonb on 2008-01-18
-

---

### Post by munkyboy on 2008-06-29
Okay so I'm trying to do this to install v3.1.0. because one if the trackers i use is insisting that i use this version. But all I keep getting is "command not found" and other such messages?

Can some one tell me what I'm doing wrong. 

russ@russ-desktop:~$ cd /home/russ/ktorrent-3.1
russ@russ-desktop:~/ktorrent-3.1$ sudo ./configure
sudo: ./configure: command not found
russ@russ-desktop:~/ktorrent-3.1$ ./configure
bash: ./configure: No such file or directory
russ@russ-desktop:~/ktorrent-3.1$

thanks

Solved it it works pefect if you put this in terminal

sudo apt-get build-dep ktorrent-kde4
sudo apt-get install libqt4-opengl-dev automoc
tar -xvjf ktorrent-3.1.tar.bz2
cd ktorrent-3.1
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr/lib/kde4 ..
make
sudo make install

Ive no idea what it all means, but it magically works

---

### Post by david.inspired on 2008-07-12
This does not work for me.

I get the following error, at 69% (when running make)
```

[ 69%] Building CXX object plugins/bwscheduler/CMakeFiles/ktbwschedulerplugin.dir/ktbwschedulerplugin_automoc.o
In file included from /home/david/ktorrent-3.1/build/plugins/bwscheduler/../../../plugins/bwscheduler/bwprefpage.h:25,
                 from /home/david/ktorrent-3.1/build/plugins/bwscheduler/moc_bwprefpage.cpp:10,
                 from /home/david/ktorrent-3.1/build/plugins/bwscheduler/ktbwschedulerplugin_automoc.cpp:3:
/home/david/ktorrent-3.1/build/plugins/bwscheduler/ui_bwprefpage.h:25:25: error: qformlayout.h: No such file or directory
In file included from /home/david/ktorrent-3.1/build/plugins/bwscheduler/../../../plugins/bwscheduler/bwprefpage.h:25,
                 from /home/david/ktorrent-3.1/build/plugins/bwscheduler/moc_bwprefpage.cpp:10,
                 from /home/david/ktorrent-3.1/build/plugins/bwscheduler/ktbwschedulerplugin_automoc.cpp:3:
/home/david/ktorrent-3.1/build/plugins/bwscheduler/ui_bwprefpage.h:33: error: ISO C++ forbids declaration of ‘QFormLayout’ with no type
/home/david/ktorrent-3.1/build/plugins/bwscheduler/ui_bwprefpage.h:33: error: expected ‘;’ before ‘*’ token
/home/david/ktorrent-3.1/build/plugins/bwscheduler/ui_bwprefpage.h: In member function ‘void Ui_BWPrefPage::setupUi(QWidget*)’:
/home/david/ktorrent-3.1/build/plugins/bwscheduler/ui_bwprefpage.h:53: error: ‘formLayout’ was not declared in this scope
/home/david/ktorrent-3.1/build/plugins/bwscheduler/ui_bwprefpage.h:53: error: expected type-specifier before ‘QFormLayout’
/home/david/ktorrent-3.1/build/plugins/bwscheduler/ui_bwprefpage.h:53: error: expected `;' before ‘QFormLayout’
make[2]: *** [plugins/bwscheduler/CMakeFiles/ktbwschedulerplugin.dir/ktbwschedulerplugin_automoc.o] Error 1
make[1]: *** [plugins/bwscheduler/CMakeFiles/ktbwschedulerplugin.dir/all] Error 2
make: *** [all] Error 2

```

---

