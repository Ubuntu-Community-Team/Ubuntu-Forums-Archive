---
title: "iBook G3 - Pink Display"
date: 2010-05-08
forum: Apple Hardware Users
---

### Post by ajkwright on 2010-05-08
I have an iBook G3 and about 4 months ago after Mac OSX was corrupted I installed Ubuntu 9.10 on it. During the install the screen was divided and partly blacked out but when I installed it, the resolution was fine and the OS encompassed the whole screen.

After a few weeks everything on the screen started to turn pink until all the colours on the whole screen were a shade of pink! I decided that I would abandon my laptop as I had a fully functioning Ubuntu desktop which was my preferable computer to use anyway.

Following the release of Ubuntu 10.04 I decided that I would try a fresh install on my laptop. When I started the install I was disappointed to find that the screen was divided and everything was shaded pink. I went ahead with the install regardless hoping that everything would be fine once I installed Ubuntu. Once again I was let down, the screen was still divided and pink. I have included some pictures for you to have a look at. I would really appreciate some help. Thank you, ajkwright.

---

### Post by linuxopjemac on 2010-05-09
You need a good xorg.conf file.
Read a bot how to change the xorg.conf file: [http://mac.linux.be/content/black-screen-or-missing-gui](http://mac.linux.be/content/black-screen-or-missing-gui)

Then choose on of these files to try:
[http://mac.linux.be/content/xorgconf-ibook-g3-500-dual-usb-0](http://mac.linux.be/content/xorgconf-ibook-g3-500-dual-usb-0)
[http://mac.linux.be/content/xorgconf-file-g3-karmic-koala](http://mac.linux.be/content/xorgconf-file-g3-karmic-koala)

or ask someone else with the same type of iBook as you for an xorg.conf file.

---

### Post by ajkwright on 2010-05-09
Thank you very much for your help. It has gotten me closer to fixing the problem. I will tell you what I did so you can help:


[LIST]
[*]Firstly I created a new xorg.conf as it is not automatically created in Ubuntu 10.04
[*]I then pasted the contents from the first link you sent me (Dual USB) into my xorg,conf file.
[*]I restarted to find that my resolution had been fixed but before I could log on I was greeted with a message telling me that "Ubuntu was running in low graphics mode". It told me that I had a problem with my configuration file. I then went ahead and logged in. The pinkness was still there.
[*]I decided to change the contents of my xorg.conf file to the second link you sent me.
[*]Then when I booted the computer was back to the way it was. The screen was split and was still pink.
[*]I then combined the two files together by replacing the section of the first link with the section from the second one.
[*]Then when I booted I was greeted with the same message and this time I decided to select the option restore settings. This changed nothing. The resolution was fine but the computer is still pink.
[/LIST]
This is where I am up to now. I am posting from the laptop so there is definitely an improvement. Thank you so much for your help, ajkwright.

---

### Post by linuxopjemac on 2010-05-09
Try the following xorg.conf file.

```
Section &#8220;Device&#8221;
Identifier    &#8220;Video&#8221;
Driver        &#8220;ati&#8243;
BusID        &#8220;PCI:0:16:0&#8243;
Option        &#8220;UseFBDev&#8221;    &#8220;true&#8221;
Option        &#8220;NoInt10&#8243;    &#8220;true&#8221;
EndSection


Section &#8220;Monitor&#8221;
Identifier    &#8220;LCD&#8221;
HorizSync    58-62
VertRefresh    43-117
EndSection

Section &#8220;Screen&#8221;
Identifier    &#8220;Default Screen&#8221;
Monitor        &#8220;LCD&#8221;
Device        &#8220;Video&#8221;
DefaultDepth    24
SubSection &#8220;Display&#8221;
Depth    24
Modes    &#8220;1024×768&#8243;
EndSubSection
EndSection

Section &#8220;DRI&#8221;
Mode    0666
EndSection

```

After trying this file, give me the output:
```
cat /var/log/Xorg.0.log
```

If it's fine, let it be as it is, if it is not ok try switching to a lower color depth:

```
Section &#8220;Device&#8221;
Identifier    &#8220;Video&#8221;
Driver        &#8220;ati&#8243;
BusID        &#8220;PCI:0:16:0&#8243;
Option        &#8220;UseFBDev&#8221;    &#8220;true&#8221;
Option        &#8220;NoInt10&#8243;    &#8220;true&#8221;
EndSection


Section &#8220;Monitor&#8221;
Identifier    &#8220;LCD&#8221;
HorizSync    58-62
VertRefresh    43-117
EndSection

Section &#8220;Screen&#8221;
Identifier    &#8220;Default Screen&#8221;
Monitor        &#8220;LCD&#8221;
Device        &#8220;Video&#8221;
DefaultDepth    16
SubSection &#8220;Display&#8221;
Depth    16
Modes    &#8220;1024×768&#8243;
EndSubSection
EndSection

Section &#8220;DRI&#8221;
Mode    0666
EndSection

```

And give the log output for this config file as well.

---

### Post by ajkwright on 2010-05-09
Here is the output after the first xorg.conf file:

```
wombat@wombat-laptop:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-20-powerpc64-smp ppc Ubuntu
Current Operating System: Linux wombat-laptop 2.6.32-21-powerpc #32-Ubuntu Fri Apr 16 08:10:47 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash 
Build Date: 23 April 2010  05:11:55PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 10 07:08:52 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Parse error on line 1 of section InputClass in file /etc/X11/xorg.conf
    The Section keyword requires a quoted string to follow it.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
wombat@wombat-laptop:~$ 

```

Thank you for your help. This xorg.conf file reset my computer to like the pictures I sent you to start off with, I will try the second file when I get home from school today. Thank you very much, you have been ever so helpful.

---

### Post by ajkwright on 2010-05-10
Hello, I just tried the second file. This one worked slightly better than the first. In this one the screen was still pink but not split unlike the first one in which the screen was split and was pink. Here is the code after changing the xorg.conf file to the second:

```
wombat@wombat-laptop:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-20-powerpc64-smp ppc Ubuntu
Current Operating System: Linux wombat-laptop 2.6.32-21-powerpc #32-Ubuntu Fri Apr 16 08:10:47 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash 
Build Date: 23 April 2010  05:11:55PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 10 16:27:44 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Parse error on line 1 of section InputClass in file /etc/X11/xorg.conf
    The Section keyword requires a quoted string to follow it.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
wombat@wombat-laptop:~$ 

```

With both of the xorg.conf files I was greeted with the message telling me that Ubuntu was running in low graphics mode. I chose to run Ubuntu in low graphics mode for one session. Thank you very much. My computer screen is now not split which was the main thing that was bothering me. If it comes down to it I will be able to cope with the pinkness. Thank you very much, :)

---

### Post by linuxopjemac on 2010-05-10
You might want to find out the right modelines:
[http://mac.linux.be/content/setting-xorgconf-manually-xrandr](http://mac.linux.be/content/setting-xorgconf-manually-xrandr)


Reading your story again it seems that your display is not working properly anymore. If it worked ok in the beginning and you did not change settings and you see something like this, it has to be the screen itself.

---

### Post by linuxopjemac on 2010-05-11
I installed Lucid myself on my old PowerBook. I found something out about low graphics mode, read the post [here]("http://ubuntuforums.org/showthread.php?t=1479469").

---

