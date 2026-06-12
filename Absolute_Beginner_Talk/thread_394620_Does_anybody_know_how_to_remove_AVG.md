---
title: "Does anybody know how to remove AVG?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-03-27
I downloaded and installed a deb file of AVG for Linux from the Grisoft website.  I'm on a dual boot with XP and a network with XP and Vista so I thought I would need it.  The problem is I could never get it to schedule a scan or, more importantly, get it to update either scheduled or manually.  I kept getting "Permission Denied" ,  So I went to AVAST and got it working just fine.  Now, I would like to get AVG 7.5 off my computer entirely but whenever I try to remove it I get this:

jtx472@Northgate:~$ sudo dpkg --remove avg75fld
(Reading database ... 131758 files and directories currently installed.)
Removing avg75fld ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 4183: bad variable name
( not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75fld (--remove):
 subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg75fld
jtx472@Northgate:~$ 

Which I don't completely understand.  Any help would be greatly appreciated.

---

### Post by zvacet on 2007-03-27
Try with 
```
sudo aptitude remove package_name
```

---

### Post by jtx472 on 2007-03-27
I did as you suggested and got:

jtx472@Northgate:~$ sudo aptitude remove package_avg75fld
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "package_avg75fld"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jtx472@Northgate:~$ 

But when I run the query I get:

jtx472@Northgate:~$ dpkg-query -l '*avg*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
un avg71fld <none> (no description available)
ii avg75fld 7.5.45_a0973 Free edition of antivirus solution with GUI.
un avggui <none> (no description available)
un avglinux <none> (no description available)
un wmavgload <none> (no description available)
jtx472@Northgate:~$

I don't understand.

---

### Post by mikewhatever on 2007-03-27
I don't think the word 'package' should be included, unless it is part of the name. Try sudo aptitude remove avg75fld (assuming avg75fld is the name).

---

### Post by jtx472 on 2007-03-27
Yes, it tells me in the query that avg75fld is the package name but when I ran sudo aptitude remove avg75fld I got:

Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  avg75fld 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 131758 files and directories currently installed.)
Removing avg75fld ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 4183: bad variable name
( not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75fld (--remove):
 subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg75fld
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
jtx472@Northgate:~$

---

### Post by mikewhatever on 2007-03-27
Suspected it would not work, since your first option (sudo dpkg --remove avg75fld) should have been the way to go. There are good guides on how to install AVG, but none I've seen tell you how to uninstall it.

---

### Post by jtx472 on 2007-03-27
Well thanks anyway for tryin'.

---

### Post by msak007 on 2007-03-27
I can't find anything either, and unless you compiled it from source using "make install" you won't be able to uninstall using something like "make uninstall". I would suggest trying to reinstall that .deb, then trying to uninstall it. When you do though, if you get it to uninstall, I would suggest using
```
sudo apt-get remove --purge <package name>
``` or ```
sudo aptitude purge <package name>
``` as either of those will also remove config files left behind from a previous installation of an app.

EDIT: Looking at your output from the error, it looks like it's trying to stop the process "avgdkill" but it doesn't seem to be running. This normally wouldn't stop an app from uninstalling, it would just skip to the uninstall part. If you try a reinstall / uninstall and that doesn't work, can you post the output of

```
ls /etc/init.d | grep avg*
```

---

### Post by jtx472 on 2007-03-27
jtx472@Northgate:~$ ls /etc/init.d | grep avg*
jtx472@Northgate:~$ 

And  when I  tried to  reinstall:  

[http://www.postyourimage.com/view_image.php?img_id=5ty2smoAdCfNUYV1175040907]("http://www.postyourimage.com/view_image.php?img_id=5ty2smoAdCfNUYV1175040907")

I've been going back and forth on Launchpad and the forums for about a week now and it seems nobody can figure out how to remove this bugger.  My real problem with it is that I cannot update it.  Maybe somebody can figure out how to update it so I don't have to remove it.

[http://www.picsoup.com/images/84799Screenshot.png]("http://www.picsoup.com/images/84799Screenshot.png")

---

### Post by snick on 2007-03-29
I also can't update AVG virus data files from GUI window --
  but I was able to update manually from terminal command line:

   sudo  avgupdate -o

--------------------------------------------------- 

{  " -o  "  switch downloads virus data file from online }
--------------------------------------------------------------------------------------------
Question:  
I can't achieve real time scanning of evolution email incoming,
  or files downloaded -- tested using EICAR  test virus file - no detection
 unles running manual scanning of file or system. 

avg manual mentions entering Dazuko into Linux Kernel --
 -- any experience of this venture out there ?

Thanks

---

### Post by jtx472 on 2007-03-29
After going back and forth with Launchpad, many times each day, for over a week and trying everything they suggested without any success, I finally got so frustrated I just un-installed Ubuntu and re-inmstalled.  I wanted that thing off my computer.  I'm now using Avast and it works perfect...updating manually or auto, running several different kinds of selective scans, etc.  I used AVG for years with Windows but I would never advise anyone to use AVG for Linux.  It's got too many bugs.

---

### Post by msak007 on 2007-03-29
Sorry I had no other suggestions on how to get rid of it. My next suggestion was going to be to just wait for Feisty to be released in a couple weeks and then format and reinstall.

---

### Post by kittyhawk63 on 2007-03-29
> **jtx472 said:**
> After going back and forth with Launchpad, many times each day, for over a week and trying everything they suggested without any success, I finally got so frustrated I just un-installed Ubuntu and re-inmstalled.  I wanted that thing off my computer.  I'm now using Avast and it works perfect...updating manually or auto, running several different kinds of selective scans, etc.  I used AVG for years with Windows but I would never advise anyone to use AVG for Linux.  It's got too many bugs.

hjtx472,
what commands did you use to install Avast?

---

### Post by jtx472 on 2007-03-29
Avast for Linux go to:
[http://www.avast.com/eng/download-avast-for-linux-edition.html]("http://www.avast.com/eng/download-avast-for-linux-edition.html")
Download the deb file.  Get the free registration code.  Install.
Go to:    /usr/bin/avast.gui  and click.  That'll start it up.  Paste in your registration code and your in business.  You can also drag /usr/bin/avast.gui to your panel for easy access.
Works great!

---

### Post by kittyhawk63 on 2007-03-29
> **jtx472 said:**
> Avast for Linux go to:
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)
Download the deb file.  Get the free registration code.  Install.
Go to:    /usr/bin/avast.gui  and click.  That'll start it up.  Paste in your registration code and your in business.  You can also drag /usr/bin/avast.gui to your panel for easy access.
Works great!


You can also drag /usr/bin/avast.gui to your panel for easy access. What does this mean? I know about placing program icons on the panel.
Thanks
kh

---

### Post by jtx472 on 2007-03-30
Just go to /usr/bin/avast.gui, hold down on your left mouse button, and drag it to the panel.

---

### Post by kittyhawk63 on 2007-03-30
> **jtx472 said:**
> Just go to /usr/bin/avast.gui, hold down on your left mouse button, and drag it to the panel.

I keep seeing this  /usr/bin/whateverhere (in this case: avast.gui)  but I don't know how to get to /usr/bin/avast.gui.  Can you give step by step instructions to a noob?
Thanks 
kh

---

### Post by jtx472 on 2007-03-30
Hey, I'm a newbie myself but I'll try.  

On your desktop click "Places" (should be on your panel).
Click "Home Folder".
On the left double click "File System".
Scroll down to "usr" and click.
Click "bin".
Scroll down to "avast.gui".  That's the baby.
If you double click that it should bring up Avast.  Give it a few seconds.
If you hold down on your mouse, you can drag it to your panel for easy access.

Hope that helps, but if not give me a holler, although I will be away from my computer for a while.

---

### Post by kittyhawk63 on 2007-03-30
> **jtx472 said:**
> Hey, I'm a newbie myself but I'll try.  
On your desktop click "Places" (should be on your panel).
Click "Home Folder".
On the left double click "File System".
Scroll down to "usr" and click.
Click "bin".
Scroll down to "avast.gui".  That's the baby.
If you double click that it should bring up Avast.  Give it a few seconds.
If you hold down on your mouse, you can drag it to your panel for easy access.
Hope that helps, but if not give me a holler, although I will be away from my computer for a while.

Well, that got me to where I wanted. I drug the avastgui icon to the panel and clicked on it. It came up with the right screen but also an error screen popped up. See attachment. I recognize you're a noob like me, but maybe you have already run into this and know how to fix it. Thanks.
Edit: I got it to work. I right clicked on the panel icon and went into Properites and changed to sudo avastgui instead of the default /usr/bin/avastgui.
kh

---

### Post by jtx472 on 2007-03-30
All...right!  Good for you.  I think you're really gonna like it once you get used to it.  You can set it (Preferences) for auto-update.  I like the manual update cause I just like to watch it update.:guitar:

---

### Post by kittyhawk63 on 2007-03-30
[quote=jtx472;2377724]All...right!  Good for you.  I think you're really gonna like it once you get used to it.  You can set it (Preferences) for auto-update.

Yes, I checked that already. Thanks. And, thank you again for your help.
kh

---

### Post by mikewhatever on 2007-04-03
> **jtx472 said:**
> I downloaded and installed a deb file of AVG for Linux from the Grisoft website.  I'm on a dual boot with XP and a network with XP and Vista so I thought I would need it.  The problem is I could never get it to schedule a scan or, more importantly, get it to update either scheduled or manually.  I kept getting "Permission Denied" ,  So I went to AVAST and got it working just fine.  Now, I would like to get AVG 7.5 off my computer entirely but whenever I try to remove it I get this:

jtx472@Northgate:~$ sudo dpkg --remove avg75fld
(Reading database ... 131758 files and directories currently installed.)
Removing avg75fld ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 4183: bad variable name
( not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75fld (--remove):
 subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg75fld
jtx472@Northgate:~$ 

Which I don't completely understand.  Any help would be greatly appreciated.
Just for the record, I was able to completely remove avg75fld from the recovery console and by manually deleting leftovers. The following command in the recovery mode removed the package, but left behind /opt/grisoft directory with files.> sudo dpkg -r avg75fld  Those where removed after booting into Ubuntu proper by > sudo rm -r /opt/grisoft
The launcher in the System was removed by > sudo rm -r /usr/share/applications/avg*
and the .avg7 folder by > sudo rm -r /home/your_username/.avg7
That was really geeky, but didn't work the other way. There seems to be a problem with the 7.5  deb version. It would not update saying 'error while processing package', and would not uninstall either. Hope Avast works fine. :)


Edit: As time goes by, we learn some new things, so here is an easier way to do it:
> sudo dpkg -R -P avg75fld
Then remove the leftovers
> sudo rm -r /opt/grisoft

There is no need to boot into recovery mode.

---

### Post by josebita on 2007-04-10
For the records. this same thing was happening to me under Feisty. Then I realized this might be due to Ubuntu changing from bash to dash.
Edit /etc/init.d/avgd and change #!/bin/sh to #!/bin/bash
This worked for me, at least.

---

### Post by rlozano on 2007-07-18
> **jtx472 said:**
> I downloaded and installed a deb file of AVG for Linux from the Grisoft website.  I'm on a dual boot with XP and a network with XP and Vista so I thought I would need it.  The problem is I could never get it to schedule a scan or, more importantly, get it to update either scheduled or manually.  I kept getting "Permission Denied" ,  So I went to AVAST and got it working just fine.  Now, I would like to get AVG 7.5 off my computer entirely but whenever I try to remove it I get this:

jtx472@Northgate:~$ sudo dpkg --remove avg75fld
(Reading database ... 131758 files and directories currently installed.)
Removing avg75fld ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 4183: bad variable name
( not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75fld (--remove):
 subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg75fld
jtx472@Northgate:~$ 

Which I don't completely understand.  Any help would be greatly appreciated.

there's suppose to be an uninstal.sh in the /opt/grisoft directory, right?

---

### Post by jtx472 on 2007-07-18
I just reinstalled Ubuntu.  It only takes a few minutes.  And I'm not running any virus scanner.  Viruses are not much of a threat anyway in Ubuntu.  The only thing I was concerned about was an Ubuntu virus infecting my XP but I have good virus protection there so not to worry.  Thanks anyway for all the replies.  That's what I really like about Ubuntu...got a problem...submit it to the forum.  You'll get almost immediate responses and usually a solution.  Try that with Microsoft.  They run you through so many hoops you finally just say, "Forget it".

---

### Post by Gotblade on 2007-09-02
"apt-get remove --purge avggui"  is what worked for me.
Wasn't the name of the deb file I installed from but the command used to launch the program.
Hope this helps!

---

### Post by paper-sith2 on 2007-09-02
Here is an email from Radek V., the .deb maintainer:

[I]1)
To perform update, user must be a member of group avg created
automatically during installation of avg. When adding an user
to the group, it is necessary to log out and on again so that the
changes take effect.


>> Problem 2) Will not reinstall.
>> Problem 3) Will not un install
>> There seems to be no way to uninstall by convetional means.
>> sudo dpkg -r avg75fld >returns whats in attached files


2) 3)
To reinstall or uninstall avg, running avg daemons must be stopped.
This should be done automatically, but there is an issue with
Ubuntu 6.10 which is using dash instead of bash as a default
/bin/sh shell and as a consequence the initscripts which are used to
stop the daemons during the process of package removing
don't work correctly. This should be fixed in next .deb package.
As a workaround, you can either stop the daemons manually (A),
or modify the initscript files to work correctly(B).

(A)
To stop the daemons, you can kill the daemons and remove their
lockfile by running commands

$ sudo killall avgscan
$ sudo rm /var/lock/avgd

Then the reinstall or uninstall by dpkg should work.

(B)
To modify the initscripts to work correctly, change the first line
of the file /opt/grisoft/avg7/etc/init.d/avgd.all

from:

#!/bin/sh

to:

#!/bin/bash

(If you want to use email scanning connected with sendmail
via milter daemon, change also the file
/opt/grisoft/avg7/etc/init.s/avgdmilter.all
in the same way)

After this change, initscripts will use bash and work correctly,
and re/uninstall with dpkg should also work without problems.


Radek V.[/I]

Hope this helps all..............

---

