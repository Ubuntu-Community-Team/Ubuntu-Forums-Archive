---
title: "Guide to Installing StarOffice for Beginners"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2006-10-31
Some people will prefer StarOffice to OpenOffice for whatever reason. A lot of people can get StarOffice free simply by being in education. Sun don't make a big thing of it on their web-site but if you are in education you can download StarOffice for free (I think it usually costs about $70), you just have to dig around.

A word of warning: StarOffice is great on XP, better than OpenOffice; however, on Ubuntu Edgy it seems to be behind OpenOffice (esp. Oo 2.0.4). The fonts do not display crisply ](*,) .

Here's how to install.

1. Go to [www.staroffice.com](www.staroffice.com). Find the download page then download the Linux version. It's about 180mb. The easiest thing is to download it onto your desktop so you can 'see' the file. Ubuntu will often download it to this location automatically. If not, choose as the file path: 

/home/yourcomputername/Desktop

2.) While it's download install a piece of software called Alien. Go to Terminal (in Applications / Accessories). 
Type: sudo apt-get install alien. 

Alien should then install automatically. If it doesn't then you need to enable all the software repositories (see forum for details).

3.) Once Alien has installed and StarOffice has fully down loaded then you need to do the following:

4.) In terminal type:

sudo -i (press return)

5.) Then, still in terminal, type the name of the directory (place) where you downloaded the StarOffice file to (remember above we suggested the Desktop - /home/yourcomputername/Desktop). So you'd type in terminal:

cd /home/yourcomputername/Desktop (press return) (if you didn't use Desktop as the directory (place) for the download then type cd /thedirectoryyoudidchoose).

6.) Then, still in terminal, type:

sh ./so-8-pp3-bin-linux-en-US.sh (press return)

(IMPORTANT: "so-8-pp3-bin-linux-en-US.sh" is the name of StarOffice 8 file as it currently downloads, it's the name Sun have chosen, they might change this. In which case you would type: sh ./thenameoffileasitdownloaded. The name of the file to use is the name found directly under the file icon, wherever it's downloaded on your Desktop/system)

7.) If all is going well you should now see in terminal:

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice]

8.) This next bit is where I went wrong. You need to make up a file name / directory which DOES NOT exist on your system (I chose a file name which did exist). You can just make one up. However, you need to specify the correct path. Simply writing something like: StarOffice Install Folder will not work. You need something like:

/home/yourcomputername/StarOfficeinstall (then press return)

9.) Terminal will then go haywire for a few seconds and unpack files the the StarOffice interface will automatically launch and you should see a Graphical interface so well known to Windows users. Then just follow the prompts and StarOffice will install.

With thanks to disc and tronica who walked me through this to get it installed on my own system. I hope this post has not been too patronising, I wanted to include every basic command so newcomer might be able to follow it.

---

### Post by Roadrunner1 on 2006-10-31
Quick question? Do you have sound when using Star Office on Ubuntu? We've had sound problems with OO and Dapper.

---

### Post by Peter The Plumber on 2006-11-23
> **Tweedicus said:**
> Some people will prefer StarOffice to OpenOffice for whatever reason. A lot of people can get StarOffice free simply by being in education. Sun don't make a big thing of it on their web-site but if you are in education you can download StarOffice for free (I think it usually costs about $70), you just have to dig around.

A word of warning: StarOffice is great on XP, better than OpenOffice; however, on Ubuntu Edgy it seems to be behind OpenOffice (esp. Oo 2.0.4). The fonts do not display crisply ](*,) .

Here's how to install.




  Thanks very much for the directions, you're not talking down at all. I do want to share my adventures, because they're slightly different. If you happen to have SO on disk; and you issue the 'alien' command at that location; you will get an error because alien will want to create directories and of course it can't on a cd. No laughing!!!!! ](*,), it only took me about 1/2 an hour to figure that one out, doh! So if you have and rpm on a cd you'll need to copy it locally somewhere, mine went into /tmp. The command came out as 'alien -i -c -v -k RPMS/*.i586.rpm'. That will install, run scripts, verbose output, keep version. Of course issued in my case in /tmp where the /RPMS was. It still didn't install the icons and shortcuts though. Drag n drop. Bummer. Alien is available from the repositories listed elsewhere on this site through Synaptic as well. A little cleanup and off to the races!

Regards,

Peter

---

### Post by dizzyfingers on 2006-11-23
> **Peter The Plumber said:**
> Thanks very much for the directions, you're not talking down at all. I do want to share my adventures, because they're slightly different. If you happen to have SO on disk; and you issue the 'alien' command at that location; you will get an error because alien will want to create directories and of course it can't on a cd. No laughing!!!!! ](*,), it only took me about 1/2 an hour to figure that one out, doh! So if you have and rpm on a cd you'll need to copy it locally somewhere, mine went into /tmp. The command came out as 'alien -i -c -v -k RPMS/*.i586.rpm'. That will install, run scripts, verbose output, keep version. Of course issued in my case in /tmp where the /RPMS was. It still didn't install the icons and shortcuts though. Drag n drop. Bummer. Alien is available from the repositories listed elsewhere on this site through Synaptic as well. A little cleanup and off to the races!

Regards,

Peter
I have alien installed and tried to install Staroffice 8 as described bu as you can see from the terminal output - no success.  Any help will be appreciated.

root@kubuntu:/home/wayne/Desktop# sh ./so-8-pp3-bin-linux-en-US.sh

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice]
/home/wayne/Desktop/sun
File is being checked for errors ...
Unpacking ...
All files have been successfully unpacked.
Unpacking...
Checksumming...
Extracting...
Done.
Running installer
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


The Installation Wizard can't run in GUI mode.
Maybe the DISPLAY environment variable isn't set correctly.

---

### Post by Peter The Plumber on 2006-11-23
I'm not sure how to do what you're trying to do. I installed off of a cd on the command line, so that would be /media/office8_id2038/office/RPMS. I copied /RPMS off the cd to /tmp and then while root and in that directory isuued 'alien -i -c -v -k RPMS/*.i586.rpm'. /RPMS contains all the rpms for the install, maybe if you find out what directory the rpm's extracted to you can modify what I used to install. Be aware that it does *not* automatically put shortcuts in the menu or the icons on the desktop. I c&p the icons from the StarOffice website; I did pay for the box set so I felt justified; and put them in /opt/staroffice8/share/pixmap. I did clean them up a bit with Gimp. I right clicked the 'applications' menu and manually added the links and the above icons which will then allow me to put the shortcuts on the appropriate users desktop. The links to the prgrams will be in /opt/staroffice8/program, look for executables named spadim, soffice, sbase, scalc, sdraw, simpress.
  All in all a big pain to install something that OO basically is but I prefer SO for it's useability. Good Luck!

Regards,

Peter

---

### Post by sabitha on 2006-11-24
> 1. Go to [www.staroffice.com](www.staroffice.com). Find the download page then download the Linux version. It's about 180mb. 

is this free ?? i dont see the download page

---

### Post by dizzyfingers on 2006-12-16
I have had no success installing Star Office 8 on Kubuntu 6.01 I need help please!  Here is my terminal output.

root@kubuntu:/home/wayne/Desktop/SO8# sh ./so-8-pp3-bin-linux-en-US.sh

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice]
/home/wayne/test
File is being checked for errors ...
Unpacking ...
All files have been successfully unpacked.
Unpacking...
Checksumming...
Extracting...
Done.
Running installer
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


The Installation Wizard can't run in GUI mode.
Maybe the DISPLAY environment variable isn't set correctly.

root@kubuntu:/home/wayne/Desktop/SO8#

---

### Post by Peter The Plumber on 2006-12-21
Check for step 8 on the original post?

---

### Post by darrowconley on 2007-04-05
Thank you very much. Very help full and everything worked the first time.

---

### Post by nfoav8or on 2007-06-26
Great Post! no problems at all.

---

### Post by minhaaj on 2008-07-17
root@minhaaj-laptop:/home/minhaaj# sh ./staroffice.sh

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice] 
/home/minhaaj/starofficeinstall
File is being checked for errors ...
Unpacking ...
All files have been successfully unpacked.
Unpacking...
Checksumming...
Extracting...
Done.
Running installer
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2ad8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb2ad88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xaa20a1bd]
#3 /var/tmp/install_22642/jre1.5.0_01/lib/i386/xawt/libmawt.so [0xaa30129e]
#4 /var/tmp/install_22642/jre1.5.0_01/lib/i386/xawt/libmawt.so [0xaa2e7386]
#5 /var/tmp/install_22642/jre1.5.0_01/lib/i386/xawt/libmawt.so [0xaa2e75cd]
#6 /var/tmp/install_22642/jre1.5.0_01/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xaa2e77d8]
#7 [0xb2b65b8b]
#8 [0xb2b5fa7b]
#9 [0xb2b5fa7b]
#10 [0xb2b5d157]
#11 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so [0xb7840c1c]
#12 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so [0xb792c668]
#13 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so [0xb7840a4f]
#14 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb789682b]
#15 /var/tmp/install_22642/jre1.5.0_01/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb76532cd]
#16 [0xb2b6543b]
#17 [0xb2b5f9a4]
#18 [0xb2b5d157]
#19 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so [0xb7840c1c]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2ad8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb2ad881e]
#2 /usr/lib/libX11.so.6 [0xaa209518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xaa2000a6]
#4 /var/tmp/install_22642/jre1.5.0_01/lib/i386/xawt/libmawt.so [0xaa2e625b]
#5 /var/tmp/install_22642/jre1.5.0_01/lib/i386/xawt/libmawt.so [0xaa2e64ec]
#6 /var/tmp/install_22642/jre1.5.0_01/lib/i386/xawt/libmawt.so [0xaa2e7714]
#7 /var/tmp/install_22642/jre1.5.0_01/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xaa2e77d8]
#8 [0xb2b65b8b]
#9 [0xb2b5fa7b]
#10 [0xb2b5fa7b]
#11 [0xb2b5d157]
#12 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so [0xb7840c1c]
#13 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so [0xb792c668]
#14 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so [0xb7840a4f]
#15 /var/tmp/install_22642/jre1.5.0_01/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb789682b]
#16 /var/tmp/install_22642/jre1.5.0_01/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb76532cd]
#17 [0xb2b6543b]
#18 [0xb2b5f9a4]
#19 [0xb2b5d157]


My computer is stuck here. I have this installation window open but it won't ask me for anything. its all grayish as in hung up. It won't go any further. any idea whats wrong ?

---

### Post by minhaaj on 2008-07-17
ok by the way, it worked. it just took forever to load. took literally about 30 mins to start. done.

---

