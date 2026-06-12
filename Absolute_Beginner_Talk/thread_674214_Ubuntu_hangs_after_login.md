---
title: "Ubuntu hangs after login"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by -=Zoro=- on 2008-01-21
Hi

Newbie to buntu - Gusty Gibbon... 

Dual boot Vista and Ubuntu 

NVidia Graphics card..

Installation was without fault and installed NVIDIA drivers via Envy... all was working OK until a re-boot last night when I got as far as the login page and entered details.

I was then presented with a fawn background with mouse cursor...

This stayed there for around 2 minutes before continuing through the boot up process..

I guess this is OK if you have time to kill but after enjoying a fast login what has gone wrong

Any ideas in simple laymans terms would be appreciated

Cheers

BP

---

### Post by fatality_uk on 2008-01-21
If you have got past the login stage, fsck will have run by then so I guess it wont be that. Can you give some more details on what driver envy installed and what card you are using please?

---

### Post by -=Zoro=- on 2008-01-21
NVIDIA GeForce 7600 GT

I just selected the Install NVIDIA Drivers automatically option..

Worked fine until the last couple of logins :(

---

### Post by jd65pl on 2008-01-21
Its probably a coincidence but I also have a 7900 GT, when I log in the system hangs for around 20 seconds before it becomes responsive. There are no errors in the logs as far as I can see.

Is this happening on a fresh install or have you installed any apps?

J

---

### Post by Frem on 2008-01-21
Could one of you install fluxbox or something similar, and log in to see if the problem persists?

Also, look in Gnome's "session" control panel and post a list of everything there.

---

### Post by -=Zoro=- on 2008-01-21
OK... struggling at this point

What is Fluxbox, where do I get it, what does it do... as for session panel.. that's really got me

---

### Post by jd65pl on 2008-01-22
Fluxbox is a desktop environment like gnome, installing it seems a prettty long winded way of finding out if there is a problem with gnome which may not be that apparent unless you remove all the gnome packages from the system i.e. have pure fluxbox.

To find sessions:
SYSTEM>PREFERENCES>SESSIONS

This is a gui to control what is started at start-up however I don't use it I always add apps that I need once I've logged in to ~/.profile (mythbackend, lirc, irexec are the apps I start in this way)

Have you selected the "Automatically remember running apps when logging out" on the "Session Options" Tab of the sessions gui?

J

---

### Post by -=Zoro=- on 2008-01-22
OK... it was a clean install using a download off the site....

Yes I have selected the "Automatically remember running apps when logging out" on the "Session Options"


Sessions =

[COLOR="Blue"][COLOR="Blue"]Beagle Search Daemon
Beryl
Bluetooth Manager
DeskLets
Network Manager
No name !!!
Power Manager
Print Queue Applet
Restricted Drivers Manager
Tracker
Update Notifier
User folders update
Visual
Volum[/COLOR]e Manager[/COLOR]

I hope that this helps

Cheers

BP

---

### Post by dstew on 2008-01-22
For slow booting that eventually works, it seems to be network problems, like the IPv6 protocol. You can use [bootchart]("http://packages.ubuntu.com/dapper/admin/bootchart") to get a graphical display of your processes at boot time, and usually you can figure out where the blockage is. You can probably install bootchart from Synaptic.

---

### Post by rosegarden78 on 2008-01-22
I'm surprised!  The kernel loads a little slow getting up to login screen.  Blackbox and Fluxbox are window managers.  You get them by using Synaptic to install them.  You use then by selecting Session Type when you login.  To use Blackbox effectively right click Xterm and type nautilus.  Then open a Konsole or Terminal and type kicker.  You'll probably want to install kde and xfce to satisfy the dependencies.

---

### Post by -=Zoro=- on 2008-01-22
Hi Thanks for that bit of advice

I have installed bootchart and after that on reboot the system did not close down at all..

Now it will not boot into even to the login screen

I get an error saying unable to mount root 0.0 !!

Is there a check disk / repair function that I can run in Ubuntu?

If so how do I get to a screen from here to be able to run it..

Vista is still running fine but not what I really want :(

---

### Post by -=Zoro=- on 2008-01-22
Anyone there?

---

### Post by philinux on 2008-01-22
Can you post the exact error messages.
The worst that can happen is that you might have to reinstall Grub (not the whole system) from the live cd.

---

### Post by -=Zoro=- on 2008-01-25
Sorry for the delay in getting back to you..

Here is the error message on screen at boot up or recovery:

[COLOR="Blue"][B]RAMDISK: ran out of compressed data - Invalid compressed format (err=1)

Kernel Panic:  not syncing: VFS 

Unable to mount root fs on

Unknown Block (0,0)[/B][/COLOR]

---

### Post by -=Zoro=- on 2008-01-26
Thanks for the suggestions

I eventually gave up on trying to fix the issue and started again from a fresh install and all seems to be OK now

When will a stable version be released?

---

### Post by coonj on 2008-01-29
I've been having what sounds like the same problem.
This has been going on since I first installed Feisty, and still after Gutsy upgrade.

I login, and the disk-access light will completely stop blinking during the hang.
The hang usually lasts about 30 sec, but it does vary on a range of no hang-time to over a minute. 

I looked in /var/log/auth.log, and noticed that hang occurs at the CRON session open:

Jan 29 10:16:42 gdm[4669]: pam_unix(gdm:session): session opened for user jay by (uid=0)
Jan 29 10:16:42 gdm[4669]: gkr-pam: unlocked 'login' keyring
Jan 29 10:17:07 CRON[5224]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 29 10:17:58 CRON[5224]: pam_unix(cron:session): session closed for user root

Not sure where to look from here. I'm not too familiar with the log files, so any guidance on how to narrow down the issue would be appreciated. Thanks!

---

### Post by corkyt on 2008-05-16
Finally.  I found the problem:

[http://ubuntuforums.org/showthread.php?t=585545](http://ubuntuforums.org/showthread.php?t=585545)

Pretty ridiculous that some buried file somewhere caused this issue.

~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml

---

