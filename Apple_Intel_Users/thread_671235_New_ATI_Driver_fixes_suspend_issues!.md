---
title: "New ATI Driver fixes suspend issues!"
date: 2008-01-18
forum: Apple Intel Users
---

### Post by cyberdork33 on 2008-01-18
> [FONT=Verdana][COLOR=#003c28]**Resolved Issues** [/COLOR][/FONT]

   [FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2]   [FONT=Verdana][SIZE=2]The following section provide a brief description of resolved issues with the latest version of the ATI Catalyst™ Linux software suite. These include:[/SIZE][/FONT] [/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][LIST]
[*][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2]
[*] [FONT=Verdana][SIZE=2]Corruption will no longer be noticed in the lower right corner of the display or on the mouse pointer after the system is running for a long period of time [/SIZE][/FONT]
[*] [FONT=Verdana][SIZE=2]Connecting a display device that supports 1680x1050 to a system running Linux will no longer result in a maximum display resolution of 1280x1024 only being available [/SIZE][/FONT]
[*] [FONT=Verdana][SIZE=2]Custom mode lines in xorg.conf will no longer be ignored by the fglrx driver [/SIZE][/FONT]
[*] [FONT=Verdana][SIZE=2][COLOR=Red]Suspending to RAM or DISK on kernel version 2.6.23 or later no longer fails[/COLOR][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/LIST]Get them here:
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run")

You can follow the directions for installing here:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

[SIZE=4]**Bonus!**[SIZE=2] [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") now installs the latest ATI drivers.[/SIZE][/SIZE]

---

### Post by ward83 on 2008-01-18
Sweet! I've been having trouble with the garbage in the bottom right for a while now. Hopefully this will fix it.

---

### Post by cyberdork33 on 2008-01-18
Well it did install on my machine and compositing is working and everything. It is acting a little strange on the remote access side though...

---

### Post by inportb on 2008-01-18
Absolutely. I just installed it on my Toshiba and it works perfectly! The last time it worked was when I had Edgy...

Thanks, AMD =p

### EDIT ###

Hmmmmmmmmmmm... minor issue (or major issue): CTRL+ALT+BKSP freezes the graphical system instead of restarting it. When I try to kill X, everything dies except the background image. From there, I have to either hit the power button or enter the SYSRQ sequence for clean reboot.

An alternative way to restart the graphical system works:

sudo /etc/init.d/kdm stop     [COLOR="#ff0000"](this stops kdm. then you have to switch to a TTY and login)[/COLOR]
sudo /etc/init.d/kdm start     [COLOR="#ff0000"](this starts kdm again)[/COLOR]

obviously, type gdm instead of kdm if you use gdm.

Has anyone else got this issue? Is there a fix?  :x

---

### Post by cyberdork33 on 2008-01-18
> **inportb said:**
> Has anyone else got this issue? Is there a fix?  :xI think that is the problem with my remote machine. I have to wait until I get home to check it though. I tried to reboot, and I think the thing has frozen.

---

### Post by cyberdork33 on 2008-01-18
> **inportb said:**
>  Hmmmmmmmmmmm... minor issue (or major issue): CTRL+ALT+BKSP freezes the graphical system instead of restarting it. When I try to kill X, everything dies except the background image. From there, I have to either hit the power button or enter the SYSRQ sequence for clean reboot.Well, I guess thge problem was something different. I am getting the same problem with CTRL+ALT+BKSP. It is a pretty bad freeze too, I couldn't even CTRL+ALT+F2 to get to a terminal. The weird thing is that I could still ssh into the machine and use it like that, but trying to reboot from the command line took a long time to actually reboot the machine.

---

### Post by antoniogartime on 2008-01-19
Works really fine in my Imac 20'!! Thank you!

---

### Post by ne0genius on 2008-01-19
hi guys

need a little help here. just got ubuntu 7.10 x64 installed on a second hard drive on my new mac pro. i have been struggling all morning trying to get the ati 2600 hd card to work. i went through one wiki but once i got the drivers installed, started up and now have black screen :-(

can someone point me into the direction of a good wiki for the ati drivers and this card. i want to have a better resolution and hopefully 3d support. it seems every wiki lists 100 steps to get it to work, is there any way i can just install the ati binary?? TIA.

-
aj

---

### Post by echo6 on 2008-01-20
> **inportb said:**
> Hmmmmmmmmmmm... minor issue (or major issue): CTRL+ALT+BKSP freezes the graphical systemFor me it is a major issue, I get the same even when logging out cleanly.

Oh! and I am still unable to get 1680x1050,  still stuck at 1440x900 :-(

This after a complete fresh install of Gutsy and these drivers.  I'll be reverting back to my old install from a backup until ATI can resolve the locking up issue!

---

### Post by handy on 2008-01-20
> **ne0genius said:**
> hi guys

need a little help here. just got ubuntu 7.10 x64 installed on a second hard drive on my new mac pro. i have been struggling all morning trying to get the ati 2600 hd card to work. i went through one wiki but once i got the drivers installed, started up and now have black screen :-(

can someone point me into the direction of a good wiki for the ati drivers and this card. i want to have a better resolution and hopefully 3d support. it seems every wiki lists 100 steps to get it to work, is there any way i can just install the ati binary?? TIA.

-
aj

[***_Envy_***]("http://www.albertomilone.com/nvidia_scripts1.html") worked beautifully for me on a current 24" iMac.

---

### Post by cyberdork33 on 2008-01-20
> **handy said:**
> [***_Envy_***]("http://www.albertomilone.com/nvidia_scripts1.html") worked beautifully for me on a current 24" iMac.Is it getting the latest release now? It was still getting 7.12 last time I checked. I still get some strange issues. I seems to crash to a blank screen if you leave it sitting...

---

### Post by handy on 2008-01-20
> **cyberdork33 said:**
> Is it getting the latest release now? It was still getting 7.12 last time I checked. I still get some strange issues. I seems to crash to a blank screen if you leave it sitting...

I don't know if it is using the latest release.

I would think that Alberto may watch the forum & elsewhere for a few days to see if a new driver has any problems before he updates Envy to use it.  I know I would.

My 24" iMac has no problems with the previous driver, so I'm in no rush to update it.

---

### Post by macaholic on 2008-01-22
Im still getting the x session freeze issue, there has been talk on the ohronix forums about it. [http://www.phoronix.com/forums/showthread.php?t=7448](http://www.phoronix.com/forums/showthread.php?t=7448). And susoend still doesn't work for me :(. Plz post if you find a wroking fix/workaround for the freezing of the X session on logout.

---

### Post by cyberdork33 on 2008-01-22
> **macaholic said:**
> Im still getting the x session freeze issue, there has been talk on the ohronix forums about it. [http://www.phoronix.com/forums/showthread.php?t=7448](http://www.phoronix.com/forums/showthread.php?t=7448). And susoend still doesn't work for me :(. Plz post if you find a wroking fix/workaround for the freezing of the X session on logout.
It works great on some other hardware I have... Try some of the suggestions in the ATI wiki:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by legzelda on 2008-01-25
While it is true my suspend seems to work without any problems with 8.1, X freezes on restart (ctrl + alt + backspace) and on logout in Gnome.  This also happens in Xfce4.  I cannot switch to another terminal and issue /etc/init.d/gdm restart, either.  This is a rather annoying bug, and I hope a fix is released or a workaround can be found!

This happens for me in both Gutsy and Hardy using kernels 2.6.24-5 and 2.6.22-14.

---

### Post by cyberdork33 on 2008-01-25
It seems that people are tracing the problem to atieventsd. This is automatically run when Xorg is started. 

[COLOR=Red]_** Be aware that I am not completely sure what all this daemon does. **_[/COLOR]

You can prevent it from starting automatically by removing it's symlinks from your rc scripts by using this command:
```
sudo update-rc.d -f atieventsd remove
```You can read more in this thread:
[http://www.phoronix.com/forums/showthread.php?t=7448](http://www.phoronix.com/forums/showthread.php?t=7448)

---

### Post by WaySensei on 2008-01-25
The new 8.01 driver still does not fix allow a Macbook Pro Core Duo with a ATI Radeon x1600 running Gutsy to wake from suspend :(

---

### Post by legzelda on 2008-01-25
After reading through that forum's thread, disabling atieventsd worked for me, too.  I can now logout, restart X, and suspend/resume.  I still have no compiz, and video still seems to tear.

> **cyberdork33 said:**
> It seems that people are tracing the problem to atieventsd. This is automatically run when Xorg is started. 

[COLOR=Red]_** Be aware that I am not completely sure what all this daemon does. **_[/COLOR]

You can prevent it from starting automatically by removing it's symlinks from your rc scripts by using this command:
```
sudo update-rc.d -f atieventsd remove
```You can read more in this thread:
[http://www.phoronix.com/forums/showthread.php?t=7448](http://www.phoronix.com/forums/showthread.php?t=7448)

---

### Post by legzelda on 2008-01-25
The computer still "freezes" after removing atieventsd when logging out a user while multiple users are logged-in at the same time.  The only way around this, evidently, is to keep both users logged-in and switch between/among them.  Any thoughts as to why this happens?

---

### Post by cyberdork33 on 2008-01-25
> **WaySensei said:**
> The new 8.01 driver still does not fix allow a Macbook Pro Core Duo with a ATI Radeon x1600 running Gutsy to wake from suspend :(
Try these suggestions. It did not work for me without changing these options.
 [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Suspend.2FHibernation_work_with_7.12](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Suspend.2FHibernation_work_with_7.12)

> **legzelda said:**
> After reading through that forum's thread, disabling atieventsd worked for me, too.  I can now logout, restart X, and suspend/resume.  I still have no compiz, and video still seems to tear.The video tearing is listed as a "known issue"
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_81_linux.html#183417](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_81_linux.html#183417)
Compiz works for me on my Compaq. There is a section about whitelisting the ATI hardware in the above link in my reply to WaySensei as well. You might try that.

> **legzelda said:**
> The computer still "freezes" after removing atieventsd when logging out a user while multiple users are logged-in at the same time.  The only way around this, evidently, is to keep both users logged-in and switch between/among them.  Any thoughts as to why this happens?No, that is new... especially since they are all thinking it has to do with changing powerstates and such.

---

### Post by inportb on 2008-01-28
> **cyberdork33 said:**
> It seems that people are tracing the problem to atieventsd. This is automatically run when Xorg is started. 

[COLOR=Red]_** Be aware that I am not completely sure what all this daemon does. **_[/COLOR]

You can prevent it from starting automatically by removing it's symlinks from your rc scripts by using this command:
```
sudo update-rc.d -f atieventsd remove
```You can read more in this thread:
[http://www.phoronix.com/forums/showthread.php?t=7448](http://www.phoronix.com/forums/showthread.php?t=7448)

That's probably the process that doesn't terminate correctly. I cannot shutdown properly either -- the screen goes black, but I have to press the power button again sometime to send another shutdown signal. When I power on, I see that my KDE session wasn't saved.

I'll do some research about this atieventsd =p

---

### Post by sjatkins on 2008-02-02
> **cyberdork33 said:**
> [FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/LIST]Get them here:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run)


How did you install this driver.  I installed on automatic everything.  It seems to work except that its tools from the ATI Catalyst Control Center insist something is wrong or there is no driver.  WTF?  There were no errors seen in the install.   SIGH.  Any help?

---

### Post by sjatkins on 2008-02-02
> **inportb said:**
> That's probably the process that doesn't terminate correctly. I cannot shutdown properly either -- the screen goes black, but I have to press the power button again sometime to send another shutdown signal. When I power on, I see that my KDE session wasn't saved.

I'll do some research about this atieventsd =p

I`ll be darned.  I uninstalled and reinstalled the latest drivers.  I made sure atieventsd was not running.  Then I closed the lid.  It went to sleep.   I reopened the lid.  It woke up!   I think we are on to something here. 

Oops.  Not quite.  It went to this funny console level (black screen) with a fast blinking _ cursor.  I have noticed this cursor when booting also.  Anyone know what causes this?  Seems to be in the way here.

---

### Post by sjatkins on 2008-02-02
It worked once.  But the ATI latest driver never showed as properly installed as mentioned.  On subsequent reboots it fails.  However after removing the driver and not installing the normal proprietary driver either the system does sleep.  So the ati proprietary drivers are definitely the right area to track this down in from what I see.   Very discouraging.   OS X is looking good, real good, about now.  You know, if we can't get Ubuntu happy on popular laptops then we will never ever win the battle for the desktop or even be taken seriously there.   Sad but true.

---

### Post by prana on 2008-02-02
> **sjatkins said:**
> It worked once.  But the ATI latest driver never showed as properly installed as mentioned.  On subsequent reboots it fails.  However after removing the driver and not installing the normal proprietary driver either the system does sleep.  So the ati proprietary drivers are definitely the right area to track this down in from what I see.   Very discouraging.   OS X is looking good, real good, about now.  You know, if we can't get Ubuntu happy on popular laptops then we will never ever win the battle for the desktop or even be taken seriously there.   Sad but true.

OSX was made for Mac hardware so to compare it to Linux is disingenuous. It is proprietary  hardware so unless Apple releases their specific ACPI implementation, suspend will always be a bit of guesswork.

I have a Macbook Pro Core 2 Duo and I purchased the machine to run OS X. OSX is a pretty good OS for a number of things but I wanted more flexibility so I started looking at Ubuntu. In fact, I had Leopard on my machine exclusively a few days ago. Initial reports confirmed that Ubuntu was very hit or miss on my machine so I waited for the kernel developers and ATI to make progress since I didn't have time to test it. 

Thanks to various people that have tested it since, support on Macs has been improving a lot. I took the plunge and it wasn't easy but now I have working suspend on my machine.

Running Ubuntu on a Mac requires some patience and if you are feeling frustrated I completely sympathize and my suggestion is to go back to OS X and try it again when Hardy is in a more stable state.

---

### Post by cyberdork33 on 2008-02-03
> **prana said:**
> Thanks to various people that have tested it since, support on Macs has been improving a lot. I took the plunge and it wasn't easy but now I have working suspend on my machine.Did you have to edit anything in /etc/default/acpi-support?

---

### Post by sjatkins on 2008-02-03
> **cyberdork33 said:**
> [FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/LIST]Get them here:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run)

Got this to work with a build and install of a 2.6.24 kernel.  Alas I lost sound in the process.  Anyone know if there is a problem on Macbook Pro Core Duo with regard to this kernel and sound?  A day and a half and still not a fully useable laptop.  Sigh.

---

### Post by cyberdork33 on 2008-02-03
> **sjatkins said:**
> Got this to work with a build and install of a 2.6.24 kernel.  Alas I lost sound in the process.  Anyone know if there is a problem on Macbook Pro Core Duo with regard to this kernel and sound?  A day and a half and still not a fully useable laptop.  Sigh.Try compiling ALSA from source. I don't know why it would break sound unless there are some specific patches that have not been added to your kernel, but as far as I knew, your machine should work fine.

---

### Post by prana on 2008-02-03
> **cyberdork33 said:**
> Did you have to edit anything in /etc/default/acpi-support?


Yeah.

SAVE_VBE_STATE=false

POST_VIDEO=false

---

### Post by prana on 2008-02-03
> **sjatkins said:**
> Got this to work with a build and install of a 2.6.24 kernel.  Alas I lost sound in the process.  Anyone know if there is a problem on Macbook Pro Core Duo with regard to this kernel and sound?  A day and a half and still not a fully useable laptop.  Sigh.

I didn't compile my own 2.6.24. I just got the pre-built Hardy kernel for Gutsy and sound worked.

You can find out how I went about changing to Ubuntu from Leopard in this post:

[http://ubuntuforums.org/showpost.php?p=4252788&postcount=5]("http://ubuntuforums.org/showpost.php?p=4252788&postcount=5")

---

### Post by grahams on 2008-02-05
With the latest ati driver and the "sudo update-rc.d -f atieventsd remove" work around for logging out I have nearly everything working perfectly. Suspend/resume, no hangs, good performance, Compiz (1 screen only) and dual screen with Metacity.

On dual screen with compiz the screen gets corrupted and breaks up. Maybe I'm going beyond the resolution limits for this. Has anyone got this to work?

---

### Post by cyberdork33 on 2008-02-05
> **grahams said:**
> On dual screen with compiz the screen gets corrupted and breaks up. Maybe I'm going beyond the resolution limits for this. Has anyone got this to work?I have a feeling that is a driver bug. Especially since on the last release they were getting a lot of screen corruption problems with compositing.

[B]Everyone
[/B][Envy]("http://www.albertomilone.com/nvidia_scripts1.html") now installs the latest ATI drivers, which is a _much_ easier way to install them.

I backported the Hardy kernel to my iMac, and made the changes to /etc/default/acpi-support as noted above, and suspend works great.

---

### Post by prana on 2008-02-05
> **grahams said:**
> With the latest ati driver and the "sudo update-rc.d -f atieventsd remove" work around for logging out I have nearly everything working perfectly. Suspend/resume, no hangs, good performance, Compiz (1 screen only) and dual screen with Metacity.

On dual screen with compiz the screen gets corrupted and breaks up. Maybe I'm going beyond the resolution limits for this. Has anyone got this to work?

Dual head is a problem for me too with Compiz so I just gave up. I will try it again with the next version of the driver.

This is what I used as my guide:

[http://hamzakc.wordpress.com/2006/10/16/dual-monitor-setup-ubuntu-ati/]("http://hamzakc.wordpress.com/2006/10/16/dual-monitor-setup-ubuntu-ati/")

---

### Post by Ebuntor on 2008-02-06
Hi everyone,

I installed the [https://a248.e.akamai.net/f/674/9206...x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run") file.
It did fix my suspend problem but made my system very slow. I'd like to remove it but I don't know what packages it installed. If I enable the standard Ubuntu driver my system won't even start the X server.

How do I remove it? What packages are involved?

EDIT: Using Envy and installing the driver did work. However I'd still like to know how to remove the packages that .run file installed. I don't have clue how to find out what that thing changed to my system, very frustrating.

EDIT2: Oh and making the changes in acpi-support worked perfectly. :) Thanks **prana**

---

### Post by cyberdork33 on 2008-02-06
> **Ebuntor said:**
> EDIT: Using Envy and installing the driver did work. However I'd still like to know how to remove the packages that .run file installed. I don't have clue how to find out what that thing changed to my system, very frustrating.How did you use it? what directions did you follow?

---

### Post by Ebuntor on 2008-02-06
> **cyberdork33 said:**
> How did you use it? what directions did you follow?

How did I use it? Are you referring to Envy or that .run file you gave in at the beginning of the thread?

Envy fixed my problem luckily. I simply installed the .deb from [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

The .run file, as I mentioned in my previous post, created all the problems. I simply ran it, I didn't follow any directions since it was perfectly clear what I was supposed to do. Although that driver did slow my system for some reason so perhaps I did do something wrong.

---

### Post by cyberdork33 on 2008-02-06
> **Ebuntor said:**
> The .run file, as I mentioned in my previous post, created all the problems. I simply ran it, I didn't follow any directions since it was perfectly clear what I was supposed to do. Although that driver did slow my system for some reason so perhaps I did do something wrong.Those are just the official ATI drivers. You can go to ATI.com and get the same ones. while you can just run the script directly, that is not the preferred method. Ideally, you should generate the deb packages from it, and install those (basically what envy does).

---

### Post by inportb on 2008-02-07
> **prana said:**
> Yeah.

SAVE_VBE_STATE=false

POST_VIDEO=false

Interesting; that fixed my shutdown issues completely. Thanks for the tip!

---

### Post by Ebuntor on 2008-02-07
> **cyberdork33 said:**
> Those are just the official ATI drivers. You can go to ATI.com and get the same ones. while you can just run the script directly, that is not the preferred method. Ideally, you should generate the deb packages from it, and install those (basically what envy does).

Yeah I ran the script directly, that's probably what screwed up my system so much.

---

### Post by cyberdork33 on 2008-02-07
> **Ebuntor said:**
> Yeah I ran the script directly, that's probably what screwed up my system so much.
Well, glad you got it working. I will edit the original post to give better direction.

---

