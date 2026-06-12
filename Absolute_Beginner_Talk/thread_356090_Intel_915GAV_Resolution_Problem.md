---
title: "Intel 915GAV Resolution Problem"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-08
i am running Ubuntu 6.10 on the sustem described in the signatures,
i have 1024x768 as the highest resolution while on windows it supports much more.

i tried to follow ubuntuguide,org and here are the results:


shoaibi@saber-rider:~$ sudo apt-get install 915resolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  915resolution
0 upgraded, 1 newly installed, 0 to remove and 139 not upgraded.
Need to get 0B/15.1kB of archives.
After unpacking 131kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  915resolution
Install these packages without verification [y/N]? y
Selecting previously deselected package 915resolution.
(Reading database ... 90175 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.2-4ubuntu1_i386.deb) ...
Setting up 915resolution (0.5.2-4ubuntu1) ...
Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution or install 'vbetool'.
invoke-rc.d: initscript 915resolution, action "start" failed.

shoaibi@saber-rider:~$ 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted

---

### Post by ramjet_1953 on 2007-02-08
Enable the extra repositories in Synaptic and then use Synaptic to install 915resolution.

After it is installed, do this:

In a terminal, type in [COLOR="Red"]sudo 915resolution -l[/COLOR]

Pick a MODE which you will never use (MODE 30 is ideal)
If you want something like 1280X800 @ 24 bits/pixel type in the following:

[COLOR="Red"]sudo 915resolution 30 1280 800 24[/COLOR] (or substitute the resolution and pixel depth to suit)

It will come back and tell you that it has succuessfully patched it.

You may notice that the screen resolution that you want is already listed, but is way down the list. For some reason that I don't know, if you choose a resolution far down the list it doesn't work.

Then in a terminal edit your /etc/default/915resolution file to suit. IE

[COLOR="Red"]sudo gedit /etc/default/915resolution
[/COLOR]
[COLOR="Blue"]MODE=30
XRESO=1280
YRESO=800
BIT=24[/COLOR]

Save the changes and re-start.
It shold now be in your desired mode and will also appear as an option in the System>Preferences>Screen Resolution menu.

Regards,
Roger 8)

---

### Post by shoaibi on 2007-02-08
can't use synaptic:
[http://www.ubuntuforums.org/showthread.php?t=356066](http://www.ubuntuforums.org/showthread.php?t=356066)

[EDIT]:
this is what i get after reinstallation:

(Reading database ... 90175 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.2-4ubuntu1_i386.deb) ...
Setting up 915resolution (0.5.2-4ubuntu1) ...
Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution or install 'vbetool'.
invoke-rc.d: initscript 915resolution, action "start" failed.

---

### Post by ramjet_1953 on 2007-02-08
OK, but in your previous post you didn't put[COLOR="Red"] sudo[/COLOR] in front of the [COLOR="Blue"]915resolution -l[/COLOR] command.

You [COLOR="Red"]must[/COLOR] use 915resolution in sudo mode.

Regards,
Roger :cool:

---

### Post by shoaibi on 2007-02-08
OOOooooooppppppsssss and what about this which shows up in terminal as well as Synaptic:

Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution or install 'vbetool'.
invoke-rc.d: initscript 915resolution, action "start" failed.


and:

shoaibi@saber-rider:~$ sudo 915resolution -l
Password:
Intel 800/900 Series VBIOS Hack : version 0.5.2

Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 71908086
Please report this problem to [email]stomljen@yahoo.com[/email]

---

### Post by ramjet_1953 on 2007-02-08
I've never heard of that problem before.

Perhaps you should do as suggested and report the problem to the program's author at [email]stomljen@yahoo.com[/email]

Regards,
Roger 8)

---

