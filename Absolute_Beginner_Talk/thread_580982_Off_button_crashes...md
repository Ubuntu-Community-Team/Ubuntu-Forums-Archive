---
title: "Off button crashes.."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-19
when i click the off buttom in the corner,
everything freezes!

i have to do ctrl+alt+backspace to gt out of it and shutdown
or shutdown vias terminal.

anyone else having this problem?

---

### Post by serif on 2007-10-19
Yes, I get something similar. If I click the Quit 'running man' icon then there is a delay of a minute or more before the dialogue box with the log off / shutdown / restart options appears. During that time I can usually launch another application and use it -- but that app will eventually freeze and I have to patiently wait for the Quit dialogue box to appear. Or, if not feeling patient, I press the power-off key on my laptop to force a shutdown!

I thought at first it was connected to using the restricted driver for my Nvidia graphics card (which, by the way, produced the full range of video effects: wobbly windows and so on.) But after re-installing Ubuntu from scratch and **not** installing the new graphics card driver I find the shutdown problem persists. Shame, everything else is so good with this version of Ubuntu - I have been using openSUSE 10.3 till yesterday. My solution is to delete the Quit button and use the hardware power-off key on my laptop instead.

---

### Post by skymera on 2007-10-19
hmm, when i click mine, i cant do anything :(
no menus, no apps

i got the nvidia driver, like most people nowadays.
im stuck on what it is.

it annoys me when i forget and click it, and have to restart X

---

### Post by Sendervictorius on 2007-10-19
I have the same issue. For me, the shutdown button freezes X forever. ctl-alt-backspace is the only way out. I have an Nvidia graphics card too - mine is a 4 year old GeForce4 MX 440. I tried both the restricted and open drivers as well.

My workaround solution is to edit the menu and add a custom launcher that runs "shutdown -h now"

I have noticed a few funnies with X on login as well. The login music completes then there is a long wait (maybe 30 seconds to a minute) before the desktop appears. Sometimes the desktop paints, then disappears, before re-painting. All a bit unstable really.

But other than that, I'm very happy with 7.10

---

### Post by skymera on 2007-10-19
yeah that works, but not convcenient, the button is there for a reason.

whats the difference between shutdown -h and -P?

---

### Post by Sendervictorius on 2007-10-19
Don't know. I always use -h. According to "man" -h is "Halt or poweroff after shutdown.", while -P is "Halt action is to turn off the power", so I guess they are the same.

---

### Post by serif on 2007-10-19
Update, some hours later. After using Ubuntu for a couple of hours, mainly browsing the Web, I suddenly discovered that the Quit command worked - up popped the dialogue box without any delay. A pleasant surprise. So, in the interest of greater knowledge, I took a deep breath and installed the Nvidia restricted driver. After the required reboot I found (as I feared) that Quit reverted to its long delay. Resigned to reinstalling Ubuntu, I carried on browsing. A mere 10 minutes later, I discovered that the Quit command now worked immediately. :confused:

Its puzzling, and unsettling, to have a bug come and go like this. But I am enjoying Ubuntu 7.10 too much to shift back to openSUSE (which refuses to let me have wobbly windows and takes ages to install new software).

---

### Post by mjziegle on 2007-10-19
I have the same problem.  After a reboot or fresh login when I hit the power button the system stalls for about 5 minutes.  After that the button performs normally.

I went from Feisty -> Gutsy RC.  I'm thinking this is a problem with dbus.

---

### Post by skymera on 2007-10-19
ok mine doasent crash, its just hangs.

still bloody annoying!!!!

---

### Post by Sendervictorius on 2007-10-20
Update - After further checking - mine hangs for 3 minutes, freezing X and everything. Finally after 3 minutes the shutdown dialog appears.

Cancelling out from the dialog box, and then selecting System>Quit again, I find that It works with a jump of the display (mode change?) - but there is no delay - then OK for the rest of the session.

---

### Post by danik on 2007-10-20
Maybe for the first time I can help you. I had the same problem, but I found the solution: the gnome-power-manager has to be enable for every session, you can do it by System -> Session.
I had this service off because I don't need it, but in this case I'd say that it's necessary !

You can find more at:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/138811](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/138811)

---

### Post by serif on 2007-10-20
Danik - thanks for your comments and the link. On my setup, the Gnome Power Manager is set as a Startup program but the icon isn't displayed when Ubuntu starts. Also, in the Sessions dialogue box, on the Current Session tab, gnome-power-manager was in style 'settings'. But after clicking Quit command and waiting a minute or more for dialogue box to appear so I could cancel, I found gnome-power-manager was in style 'normal' -- and the icon appeared in the tray. Quit then displayed its options at once.

I found a similar bug with latest openSUSE (10.3) -- the power manager icon did not appear until I selected it as an application. But there I had no problem with Quit (and also no chance to use a new Nvidia driver).

Maybe a bug with the new Gnome 2.2?

P.S. More good news with Ubuntu 7.10 -- first time ever with Linux I have got my Linksys Broadcom wireless network card working. Oh bliss!!

---

### Post by theh0g on 2007-10-20
> **danik said:**
> Maybe for the first time I can help you. I had the same problem, but I found the solution: the gnome-power-manager has to be enable for every session, you can do it by System -> Session.
I had this service off because I don't need it, but in this case I'd say that it's necessary !

You can find more at:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/138811](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/138811)

It works! Thanks dude! I just enabled Power Manager in session and logout window pops up instantly (ok, the fade could be smoother, but it'll do for now).

---

### Post by Sendervictorius on 2007-10-21
Works great. Thanks.

---

### Post by skymera on 2007-10-23
yep
gnome-power-manager 

:D

---

### Post by radovan01 on 2007-10-23
works! :)

---

### Post by ktulu1115 on 2007-10-25
Unfortunately for me that doesn't solve the problem.  gnome-power-manager is indeed running but hitting the Logout button locks X most of the time.  The only thing I found to fix it is disable compiz.  I'm running dual LCDs on an nvidia card if that makes any difference.

---

### Post by serif on 2007-10-25
On my system (Sony VAIO laptop with nvidia card), the Session dialogue box shows gnome-power-manager installed and running - though no icon is visible in the notification area. But if I launch the Power Manager app from the system menu then the icon appears and Quit works fine.

In case the new restricted driver for nvidia was causing the problem, I reinstalled Ubuntu and did not install the new driver. But the Quit problem still occurred. 

There also seems to be a common fault with Power Manager in both Ubuntu 7.10 and openSUSE 10.3. When I open the Power Manager dialogue, the control at the bottom for screen brightness is missing. Usually it appears when Power Manager is run again some time later. Seems to be a bug in the new version of Gnome which is used by both distros.

---

### Post by skymera on 2007-10-27
i have no icon?

isit defo on?

---

### Post by serif on 2007-11-23
Hurrah! Latest Ubuntu update to Gnome has fixed the problem with Quit. I can now click the Quit button right after logging in and get the dialogue box. Also, the Power Manager icon now displays too without needing a manual launch. Hope same good news applies to others too!

---

### Post by skymera on 2007-11-23
ahh thats good to hear! :)

---

### Post by sawback on 2007-12-03
I'm glad to hear that the update has fixed this problem for some people, but it's not fixed for me yet on my AD users using Edubuntu. 

Local/system users have no problem accessing the log off dialogue but AD users have to wait a minute or two before the dialogue appears.

Any ideas?

---

