---
title: "Mplayer/Multimedia Help codecs"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by RowdyDowdy1 on 2006-01-19
I am a newbie to this whole linux experience so bare with me.... 

After I had loaded my Ubuntu 5.0.4 on my Dual boot Machine. I have gotten it to run smoothly and on the internet except for one thing. And that is the Video and Music players. 

I have gone to many different sites and have tried to go threw the steps they describe it acts like parts of the media player files arn't there and/or it has " dependences" on things and can not complete the operation. 

Here is a copy of my terminal: ( Note: this is new for me, but I have experience with dos). 

[SIZE="2"][SIZE="1"][SIZE="2"][SIZE="1"][FONT="Arial"][FONT="Courier New"]charles@ubuntu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
charles@ubuntu:~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate
charles@ubuntu:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libdirectfb-0.9-20 but it is not installable
               Depends: libfaad2-0 (>= 2.0.0-0.3) but it is not installable
               Depends: libggi2 (>= 1:2.0.5) but it is not installable
               Depends: libglib1.2 (>= 1.2.0) but it is not installable
               Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
               Depends: libmad0 (>= 0.15.1b) but it is not installable
               Depends: libsvga1 but it is not installable or
                        svgalib-dummyg1 but it is not installable
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
               Depends: xmms but it is not installable
E: Broken packages
charles@ubuntu:~$ sudo apt-get install mplayer-fonts
Reading package lists... Done
Building dependency tree... Done
Package mplayer-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-fonts has no installation candidate
charles@ubuntu:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-mplayer
charles@ubuntu:~$ sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
cp: cannot stat `/etc/mplayer/mplayer.conf': No such file or directory
charles@ubuntu:~$ sudo gedit /etc/mplayer/mplayer.conf
charles@ubuntu:~$ sudo apt-get install xmms
Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
charles@ubuntu:~$ wget -c [http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb](http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb)
--11:14:35--  [http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb](http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb)
           => `xmms-wma_1.0.4-2_i386.deb'
Resolving frankandjacq.com... 66.246.156.115
Connecting to frankandjacq.com[66.246.156.115]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:14:35 ERROR 404: Not Found.

charles@ubuntu:~$ sudo dpkg -i xmms-wma_1.0.4-2_i386.deb
dpkg: error processing xmms-wma_1.0.4-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xmms-wma_1.0.4-2_i386.deb
charles@ubuntu:~$ sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
charles@ubuntu:~$ sudo cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp
charles@ubuntu:~$ sudo sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3
charles@ubuntu:~$ sudo sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u
charles@ubuntu:~$ sudo sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list
charles@ubuntu:~$ sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
charles@ubuntu:~$ sudo rm -f /tmp/defaults.*
charles@ubuntu:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate[/FONT][/FONT][/SIZE][/SIZE][/SIZE][/SIZE]


If anyone has any suggestions.... Let me know. I have tried stuff from the unofficial Guide for Ubuntu and other selected sites.

---

### Post by dueY on 2006-01-19
```
charles@ubuntu:~$ wget -c http://frankandjacq.com/ubuntuguide/...0.4-2_i386.deb
--11:14:35-- http://frankandjacq.com/ubuntuguide/...0.4-2_i386.deb
=> `xmms-wma_1.0.4-2_i386.deb'
Resolving frankandjacq.com... 66.246.156.115
Connecting to frankandjacq.com[66.246.156.115]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:14:35 ERROR 404: Not Found.

charles@ubuntu:~$ sudo dpkg -i xmms-wma_1.0.4-2_i386.deb
dpkg: error processing xmms-wma_1.0.4-2_i386.deb (--install):
cannot access archive: No such file or directory
```

Well one problem is that as you can see you never downloaded the file you were trying to.  So when you tried to install it there was nothing to install.  Probably due to an out of date link on the guide you read.

Do you use Synaptic?  You should if possible since you are a beginer.  Have you ```
sudo apt-get install build-essential
``` in the terminal?

---

### Post by dueY on 2006-01-19
Also you should consider upgrading from 5.04 to 5.10 I think.

---

### Post by RaiSuli on 2006-01-19
The Automatix installer would probably help you set up your media players and the necessary video and audio codecs. Worked without a flaw for me.

---

### Post by dueY on 2006-01-19
[QUOTE=RaiSuli]The Automatix installer would probably help you set up your media players and the necessary video and audio codecs. Worked without a flaw for me.[/QUOTE]

Yeah, that works, but it takes all the fun out of it :razz:

---

