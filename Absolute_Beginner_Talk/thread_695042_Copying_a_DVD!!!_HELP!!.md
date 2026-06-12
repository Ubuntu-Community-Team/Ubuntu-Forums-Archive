---
title: "Copying a DVD!!! HELP!!"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by whos2know on 2008-02-12
hi,

I am trying to get some software to make backups of my DVD's.  I tried to install k9copy but I have been unsuccessful.  Any help would be great!! Thank you!!

Bobby

---

### Post by Therion on 2008-02-12
What kind of DVD's and what kind of problem/s are you having with K9?

---

### Post by jaytek13 on 2008-02-12
I find K3b to be the best application for my cd/dvd needs. You should be able to install it from the command line and afterwards everything should be good to go.

```
sudo apt-get install k3b
```

I'm sure some others have other applications they prefer, too.

---

### Post by whos2know on 2008-02-12
I've installed it with sudo apt-get install k3b and everything install ok... when I use it.... and start to copy it crashes about 2 mins in....  I read that the new version is the one to install.... I used make and fail the first time because I didn't have all of the dependices.  After install the dependices I got this...

[PHP]bobby@TheOne:~/Desktop/kk$ ls
k9copy-1.0.4-2  k9copy-1.0.4-2.tar.gz
bobby@TheOne:~/Desktop/kk$ cd k9copy-1.0.4-2
bobby@TheOne:~/Desktop/kk/k9copy-1.0.4-2$ make
make  all-recursive
make[1]: Entering directory `/home/bobby/Desktop/kk/k9copy-1.0.4-2'
Making all in k9vamps
make[2]: Entering directory `/home/bobby/Desktop/kk/k9copy-1.0.4-2/k9vamps'
source='k9vamps.cpp' object='k9vamps.lo' libtool=yes \
        depfile='.deps/k9vamps.Plo' tmpdepfile='.deps/k9vamps.TPlo' \
        depmode=gcc3 /bin/bash ../admin/depcomp \
        /bin/bash ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../libk9copy -I. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o k9vamps.lo `test -f 'k9vamps.cpp' || echo './'`k9vamps.cpp
In file included from k9vamps.h:15,
                 from k9vamps.cpp:13:
../libk9copy/k9common.h:28:31: error: dvdread/ifo_types.h: No such file or directory
../libk9copy/k9common.h:29:32: error: dvdread/dvd_reader.h: No such file or directory
../libk9copy/k9common.h:30:30: error: dvdread/ifo_read.h: No such file or directory
../libk9copy/k9common.h:31:31: error: dvdread/ifo_print.h: No such file or directory
../libk9copy/k9common.h:32:30: error: dvdread/nav_read.h: No such file or directory
../libk9copy/k9dvdread.h:23: error: ISO C++ forbids declaration of 'dvd_file_t' with no type
../libk9copy/k9dvdread.h:23: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:41: error: ISO C++ forbids declaration of 'dvd_reader_t' with no type
../libk9copy/k9dvdread.h:41: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:53: error: ISO C++ forbids declaration of 'dvd_reader_t' with no type
../libk9copy/k9dvdread.h:53: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:58: error: expected `;' before '}' token
../libk9copy/k9dvd.h:149: error: 'ifo_handle_t' has not been declared
../libk9copy/k9dvd.h:152: error: 'dvd_time_t' has not been declared
../libk9copy/k9dvd.h:158: error: 'ifo_handle_t' has not been declared
../libk9copy/k9ifo.h:38: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:38: error: expected ';' before '*' token
../libk9copy/k9ifo.h:41: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:41: error: expected ';' before '*' token
../libk9copy/k9ifo.h:42: error: 'pci_t' has not been declared
../libk9copy/k9ifo.h:47: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:47: error: expected ';' before '*' token
../libk9copy/k9ifo.h:58: error: 'pgc_command_tbl_t' has not been declared
../libk9copy/k9ifo.h:59: error: 'pgc_program_map_t' has not been declared
../libk9copy/k9ifo.h:60: error: 'cell_playback_t' has not been declared
../libk9copy/k9ifo.h:61: error: 'cell_position_t' has not been declared
../libk9copy/k9ifo.h:62: error: 'pgc_t' has not been declared
../libk9copy/k9ifo.h:71: error: 'pgcit_t' has not been declared
../libk9copy/k9ifo.h:75: error: 'c_adt_t' has not been declared
../libk9copy/k9ifo.h:76: error: 'vobu_admap_t' has not been declared
../libk9copy/k9dvdbackup.h:58: error: 'cell_adr_t' was not declared in this scope
../libk9copy/k9dvdbackup.h:58: error: template argument 1 is invalid
../libk9copy/k9dvdbackup.h:110: error: 'ifo_handle_t' has not been declared
../libk9copy/k9dvdbackup.h:111: error: 'ifo_handle_t' has not been declared
k9vamps.cpp: In member function 'virtual void k9vamps::run()':
k9vamps.cpp:195: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::lock(int)':
k9vamps.cpp:254: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::copy(int)':
k9vamps.cpp:269: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::check_pack(uchar*)':
k9vamps.cpp:328: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:331: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:339: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::check_video_packet(uchar*)':
k9vamps.cpp:355: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:362: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:367: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:397: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:407: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::new_private_1_type(uchar*)':
k9vamps.cpp:503: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_leader()':
k9vamps.cpp:623: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:629: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_trailer(int)':
k9vamps.cpp:666: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::vap_phase1()':
k9vamps.cpp:737: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:785: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:791: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_phase2(int)':
k9vamps.cpp:921: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:927: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::fatal(char*, ...)':
k9vamps.cpp:1049: warning: function might be possible candidate for 'printf' format attribute
make[2]: *** [k9vamps.lo] Error 1
make[2]: Leaving directory `/home/bobby/Desktop/kk/k9copy-1.0.4-2/k9vamps'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bobby/Desktop/kk/k9copy-1.0.4-2'
make: *** [all] Error 2
 [/PHP]

a bit confused...  any and all help would be great.. thank you again!

Bobby

---

### Post by jaytek13 on 2008-02-12
You have do to a ```
./configure
``` in the directory before doing make. But before you do, it's always best to read the README and INSTALL files beforehand.

---

### Post by stchman on 2008-02-12
> **whos2know said:**
> hi,

I am trying to get some software to make backups of my DVD's.  I tried to install k9copy but I have been unsuccessful.  Any help would be great!! Thank you!!

Bobby

To install K9Copy do the following:

```
sudo apt-get install k9copy
```

Make sure you have the multiverse repository enabled.  If you want to backup unencrypted DVDs then use K3B.

---

### Post by whos2know on 2008-02-12
yes i did the ./configure before that... and still same problem... :(  

and 

when I do sudo apt-get install k9copy it says I already have to latest copy on it.... in which... I don't... that is why I'm trying to install the newer one...
 

thanks again!

---

### Post by mc4man on 2008-02-12
here's latest in .deb
[http://www.getdeb.net/search.php?keywords=k9copy](http://www.getdeb.net/search.php?keywords=k9copy)
uninstall repo version 1st., dl,  double click to install

---

### Post by stchman on 2008-02-13
> **whos2know said:**
> yes i did the ./configure before that... and still same problem... :(  

and 

when I do sudo apt-get install k9copy it says I already have to latest copy on it.... in which... I don't... that is why I'm trying to install the newer one...
 

thanks again!

K9Copy is under Sound & Video

---

### Post by Cubby on 2008-02-13
Hi,
 
 I used the information at this thread. I installed the latest k9copy from sourceforge, version 1.2.3
 
[http://ubuntuforums.org/showthread.php?t=607991&highlight=k9copy](http://ubuntuforums.org/showthread.php?t=607991&highlight=k9copy)
 
 Just make sure you do as wjston says, and get all of your dependencies first. I also installed cdrtools and smake. smake is installabble through synaptic and I downloaded and installed cdrtools tar.gz file using smake command to install. It took me many hours to get all of the dependencies, as I am using dial-up, especially that kdebase-dev.
 
 I also had to install g++, vamps, dvdauthor, automake 1.7, checkinstall, libavcodec, libavformat, vobcopy, kde-devel (large pkg.) g77, besides the stuff wjston mentions.
 A compiller nightmare  . Usually the error messages during install will tell you what you are missing.

Oh, as for installing, I did do the "make" command, and then did "sudo make install" for the final command.  If you type in just "make install" it says it cannot create directory /usr/share/doc/HTML.

---

