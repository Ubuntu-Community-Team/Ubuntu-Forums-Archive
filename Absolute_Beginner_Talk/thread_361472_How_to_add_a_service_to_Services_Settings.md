---
title: "How to add a service to Services Settings"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-02-14
Hi

Anyone know how to add a service to the System/Admin/Services tool

I run a media service wizd and would really like it to start with the OS.

Unfortunately the Help file that comes with System/Admin/Services has nothing to do with it's current incarnation Dapper.

I have tried all the obvious things like right click, searched for anything like an associated menu, no joy, you can turn a predefined list of services on or off, you cannot add a new service. very odd indeed.

Another reason why Linux is not ready for prime time yet, Aunt Mable ain't never going to be web surfing with Ubuntu without her own personal Tech Support Team on standby.

However, I enjoy a challenge and would really like to make this work.

Thanks
M

---

### Post by rverrips on 2007-02-14
> **Busta999 said:**
> Hi
Anyone know how to add a service to the System/Admin/Services tool

I run a media service wizd and would really like it to start with the OS.


Hi, 

I'm going out on a limb here, and guessing that you only want to startup the Media Service Wizard once you've started Gnome, and it's not really a service but a command?  If that's the case, [FONT=Verdana, Arial, Helvetica][SIZE=2][FONT=Verdana, Arial, Helvetica][SIZE=2]go to the Preferences section of the Desktop menu, then select Sessions. Click on the Startup Programs tab, then type in the command you want to run when Gnome starts.[/SIZE][/FONT][/SIZE][/FONT]

Otherwise, open a terminal and run:
> sudo gedit /etc/rc.local
... and add the command you want to run at the end of that file.  (rc.local is the autoexec.bat of linux)

The reason I'm saying this is if your Media Services Wizard were indeed a service, it would've installed itself as such in /etc/init.d

Hope that helps

---

### Post by Busta999 on 2007-02-15
rveripps thanks for the response

It is in the init.d dir, it installed in there but it doesn't load it I always have to login open a terminal and run sudo wizd start and off it goes.

I really want it running whenever the machine is on.

While rebooting it dropped Gnome again (for no apparent reason), this time I was better prepared and used the magic CTRL ALT BSPC to get away from the mouse pointer on an otherwise empty desktop. Then I was able to install the KDE desktop and switch to that. 

I will try removing gnome and reinstalling it see if that fixes it.

---

### Post by Busta999 on 2007-02-15
rveripps thanks for the response

It is in the init.d dir, it installed in there but it doesn't load it I always have to login open a terminal and run sudo wizd start and off it goes.

I really want it running whenever the machine is on.

While rebooting it dropped Gnome again (for no apparent reason), this time I was better prepared and used the magic CTRL ALT BSPC to get away from the mouse pointer on an otherwise empty desktop. Then I was able to install the KDE desktop and switch to that. 

I will try removing gnome and reinstalling it see if that fixes it.

---

