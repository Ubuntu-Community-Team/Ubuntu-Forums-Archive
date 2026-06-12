---
title: "Help extremely needed for installation of Pando."
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-05-02
I did everything but can't figure out how to launch pando itself.
with one exception, I skipped the "tar xvfj pandodl-xx.tar.bz2" part of the downloading instructions. I tried inputting "tar xvfj pandodl-xx.tar.bz2" into the terminal but this came out:


> john@john-desktop:~$ tar xvfj pandodl-xx.tar.bz2
tar: pandodl-xx.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@john-desktop:~$



ok this is what the page says to download pando:
These are the instructions:
> 
Hello,

Please see below for the link to download the Pando Linux Downloader (v0.9 Beta), please read the following instructions before installing/running this software.

We are very interested in hearing about your experiences with this software so please create posts sharing your feedback, don't forget to include the distribution you are running and it's version!

Thanks.

[http://www.pando.com/dl/download/pandodl-0.9.0.0.tar.bz2](http://www.pando.com/dl/download/pandodl-0.9.0.0.tar.bz2)

Prerequisites
===========

Debian/Ubuntu
------------------

The packages listed below can be installed by becoming root and typing,
'apt-get install <package>'

libgtk2.0-0
libuuid1
libexpat1
zlib1g
libstdc++5

Fedora
---------

The packages listed below can be installed by becoming root and typing,
'yum install <package>'

gtk2
e2fsprogs-libs
expat
zlib
compat-libstdc++-33

Note: If installing on Fedora, after following the installation steps below
the following additional step has to be taken.

Go to the pandodl directory and run 'ln -s /lib/libexpat.so.0 lib/libexpat.so.1'

Installation
=========

After the prerequisites are installed the Pando Downloader Beta can be
installed by following the steps below.

1. If a systemwide install is desired become root and run the command below
from the /usr/local/bin directory, for a user install run it in the user's home dir.

tar xvfj pandodl-xx.tar.bz2

2. Run 'export PANDO_HOME=/PATH/TO/PANDODL_DIR'

3. $PANDO_HOME/pandodl may be run to launch the Pando Downloader.

Configuration
===========

After first run a file named .pandoDownloader will be created, the following
values can be added to it.

Listen_Port - is the listening port for other peers to connect to.
Limit_Upload_Rate - is the upload rate in KB/s.
Proxy_Host - Hostname or IP of the Proxy server.
Proxy_Port - Port the proxy server is listening on.
Proxy_User - Username for the proxy server.
Proxy_Pass - Password for the proxy server.

---

### Post by taurus on 2007-05-02
Are you sure you are in the right directory where you have downloaded pandodl-xx.tar.bz2?  Perhaps you saved it to ~/Desktop.

```
cd ~/Desktop
tar xvjf pandodl-xx.tar.bz2
```

---

### Post by sad_iq on 2007-05-02
Have you changed the xx in** tar xvjf pandodl-xx.tar.bz2** with the right version???
 I think it shoul be **tar xvjf pandodl-0.9.0.0.tar.bz2**...also install libgtk2.0-0 libuuid1libexpat1zlib1g libstdc++5 (**sudo apt-get install libgtk2.0-0 libuuid1libexpat1zlib1g libstdc++5** )

---

### Post by annda on 2007-05-02
and make sure you substitute 'xx' with 0.9.0.0 - the version number

---

### Post by Parasitesss on 2007-05-02
I type in "cd /"??

---

### Post by Parasitesss on 2007-05-02
This is what happened:
> john@john-desktop:~$ cd /
john@john-desktop:/$  tar xvfj pandodl-xx.tar.bz2
tar: pandodl-xx.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@john-desktop:/$

---

### Post by Parasitesss on 2007-05-02
This is what happened when I used, "tar xvjf pandodl-0.9.0.0.tar.bz2"
> 
john@john-desktop:~$ tar xvjf pandodl-0.9.0.0.tar.bz2
tar: pandodl-0.9.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@john-desktop:~$

---

### Post by taurus on 2007-05-02
What's the output of this command

```
ls -la ~/Desktop
```
or even this?

```
ls -la ~
```

---

### Post by Parasitesss on 2007-05-02
this is the out put of "ls -la ~/Desktop"

> drwxr-xr-x  4 john john    4096 2007-05-02 16:41 .
drwxr-xr-x 42 john john    4096 2007-05-02 15:14 ..
-rw-r--r--  1 john john   82944 2007-05-01 21:21 CITR.doc
-rw-r--r--  1 john john    2122 2007-04-19 15:54 firefox.desktop
-rw-r--r--  1 john john    4163 2006-06-15 11:25 gnome-terminal.desktop
-rw-r--r--  1 john john     283 2007-03-30 17:57 IE6.0.desktop
drwxr-xr-x  6 john john    4096 2007-03-30 17:47 ies4linux-2.0.5
-rw-r--r--  1 john john 2127690 2006-12-09 07:41 lolafunny.JPG
-rw-r--r--  1 john john 2268957 2006-06-03 13:55 lolofun.JPG
-rw-r--r--  1 john john    2026 2006-08-02 23:03 nautilus-computer.desktop
drwxr-xr-x  3 john john    4096 2007-03-08 21:05 pandodl-0.9.0.0.tar.bz2_FILES
-rw-r--r--  1 john john 4621920 2007-04-29 14:49 xGumbyx - Kill everyone.mp3


---

### Post by sad_iq on 2007-05-02
Download the file again...I think it's not complete!!!

---

### Post by Parasitesss on 2007-05-02
hopefully your correct.

---

### Post by Parasitesss on 2007-05-02
do I save it to this directory???
> 
john@john-desktop:~$

---

### Post by Parasitesss on 2007-05-02
OMG!!! I installed the download link and then did this:

> john@john-desktop:~$ tar xvjf pandodl-0.9.0.0.tar.bz2
tar: pandodl-0.9.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@john-desktop:~$

---

### Post by sad_iq on 2007-05-02
Save it anyware inside your home directory...just remember where you saved it!!!
 The file could be deleted after you compile and install!!!

---

### Post by sad_iq on 2007-05-02
Ok...just make sure you have the entire file...and remember where you saved it!!!

---

### Post by Parasitesss on 2007-05-02
wait, I don't understand do I save "tar xvjf pandodl-0.9.0.0.tar.bz2" anywhere in my home directory? if so how do I do it?

---

### Post by sad_iq on 2007-05-02
ok...in a terminal type ```
wget -c http://www.pando.com/dl/download/pandodl-0.9.0.0.tar.bz2 
```... that should save it where you are (if you do a **cd Desktop** before this comand it will save that file in your Desktop...and if you do **cd /home/yourusername** before that comand it will save the file in your home folder)!!!
 After it finishes downloading install all the required packages and then continue with the tar whatever command (no need to do any cd somewere now)!!!

---

### Post by annda on 2007-05-02
if you have downloaded the pandodl**** file, note where it is. you can use the file manager (nautilus) to track it down.

then, in the terminal, navigate to the appropriate directory. use the 'ls' command to make sure the file is there - it should be listed.

type:

```
tar xvjf pandodl
```

and hit the TAB key - this will complete the name for you, so you don't make a mistake typing. hit RETURN. the archive will be extracted into the same directory - you home (/home/john) or the desktop (/home/john/Desktop)

---

### Post by Parasitesss on 2007-05-02
ok this is what I did:
> 
john@john-desktop:~$ wget -c [http://www.pando.com/dl/download/pandodl-0.9.0.0.tar.bz2](http://www.pando.com/dl/download/pandodl-0.9.0.0.tar.bz2)
--17:24:46--  [http://www.pando.com/dl/download/pandodl-0.9.0.0.tar.bz2](http://www.pando.com/dl/download/pandodl-0.9.0.0.tar.bz2)
           => `pandodl-0.9.0.0.tar.bz2'
Resolving [www.pando.com](www.pando.com)... 208.72.31.50
Connecting to www.pando.com|208.72.31.50|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,724,300 (3.6M) [application/x-tar]

100%[====================================>] 3,724,300     89.74K/s    ETA 00:00l
17:25:27 (89.49 KB/s) - `pandodl-0.9.0.0.tar.bz2' saved [3724300/3724300]

---

### Post by Parasitesss on 2007-05-02
I followed Sad_iq's instrucs. and it worked but do I follow it up with this?:

> Installation
=========

After the prerequisites are installed the Pando Downloader Beta can be
installed by following the steps below.

1. If a systemwide install is desired become root and run the command below
from the /usr/local/bin directory, for a user install run it in the user's home dir.

tar xvfj pandodl-xx.tar.bz2

2. Run 'export PANDO_HOME=/PATH/TO/PANDODL_DIR'

3. $PANDO_HOME/pandodl may be run to launch the Pando Downloader.

 

---

### Post by Parasitesss on 2007-05-02
I got the files extracted:

> john@john-desktop:~$ tar xvjf pandodl-0.9.0.0.tar.bz2
./
./pandodl-16837/
./pandodl-16837/bin/
./pandodl-16837/bin/pandoDownloader
./pandodl-16837/lib/
./pandodl-16837/lib/libfreebl3.so
./pandodl-16837/lib/libnspr4.so
./pandodl-16837/lib/libnss3.so
./pandodl-16837/lib/libnssckbi.so
./pandodl-16837/lib/libplc4.so
./pandodl-16837/lib/libplds4.so
./pandodl-16837/lib/libsmime3.so
./pandodl-16837/lib/libsoftokn3.so
./pandodl-16837/lib/libssl3.so
./pandodl-16837/lib/libwx_gtk2_aui-2.8.so.0
./pandodl-16837/lib/libwx_gtk2_xrc-2.8.so.0
./pandodl-16837/lib/libwx_gtk2_qa-2.8.so.0
./pandodl-16837/lib/libwx_gtk2_html-2.8.so.0
./pandodl-16837/lib/libwx_gtk2_adv-2.8.so.0
./pandodl-16837/lib/libwx_gtk2_core-2.8.so.0
./pandodl-16837/lib/libwx_base_xml-2.8.so.0
./pandodl-16837/lib/libwx_base_net-2.8.so.0
./pandodl-16837/lib/libwx_base-2.8.so.0
./pandodl-16837/pandodl
./pandodl-16837/pando_icon48.png
./pandodl-16837/README
./pandodl

---

### Post by Parasitesss on 2007-05-02
Do I run the following as instructed?

> 2. Run 'export PANDO_HOME=/PATH/TO/PANDODL_DIR'

3. $PANDO_HOME/pandodl may be run to launch the Pando Downloader. 

---

### Post by sad_iq on 2007-05-02
Type **cd /usr/local/bin** then type **sudo export PANDO_HOME=/home/john/pandodl-16837** (I had to download the file wich gave me the pandodl-16837...yours should be the same)!!!

---

### Post by Parasitesss on 2007-05-02
this is what happened:

> john@john-desktop:~$ cd /usr/local/bin
john@john-desktop:/usr/local/bin$ sudo export PANDO_HOME=/home/john/pandodl-16837
Password:
sudo: export: command not found
john@john-desktop:/usr/local/bin$ sudo export PANDO_HOME=/home/john/pandodl-16837

---

### Post by Parasitesss on 2007-05-02
Help!!!1

---

### Post by sad_iq on 2007-05-03
Type ```
cd ./pandodl
``` then do ```
./pandodl
``` ....that should work!!!

---

### Post by barkhat on 2007-05-12
i'm having trouble getting this installed, too.  i get as far as #3 (from the directions above):

After the prerequisites are installed the Pando Downloader Beta can be
installed by following the steps below.

1. If a systemwide install is desired become root and run the command below
from the /usr/local/bin directory, for a user install run it in the user's home dir.

tar xvfj pandodl-xx.tar.bz2

2. Run 'export PANDO_HOME=/PATH/TO/PANDODL_DIR'

3. $PANDO_HOME/pandodl may be run to launch the Pando Downloader.

But nothing happens.  Is there something wrong with these directions in #3?

---

### Post by barkhat on 2007-05-12
> **sad_iq said:**
> Type ```
cd ./pandodl
``` then do ```
./pandodl
``` ....that should work!!!

i tried this and i get this:

berijoy@Egyirba:~/pandodl$ ./pandodl
[: 16: ==: unexpected operator
exec: 24: /PATH/TO/PANDODL_DIR/bin/pandoDownloader: not found


Can anyone help me?

---

### Post by barkhat on 2007-05-28
> **Parasitesss said:**
> I did everything but can't figure out how to launch pando itself.
with one exception, I skipped the "tar xvfj pandodl-xx.tar.bz2" part of the downloading instructions. I tried inputting "tar xvfj pandodl-xx.tar.bz2" into the terminal but this came out:






ok this is what the page says to download pando:
These are the instructions:

so how do you add the values it suggests?  i don't understand how to do this in Linux as I'm relatively new.

---

### Post by ReapingWildOats on 2007-06-25
I tried the export command but that doesn't seem to work for me.

so I did the cd /topandodl/
./pandodl

and that gave me this error

/home/roland/Desktop/pandodl/bin/pandoDownloader: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory

same error with sudo

---

