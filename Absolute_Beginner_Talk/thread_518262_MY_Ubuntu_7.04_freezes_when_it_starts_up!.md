---
title: "MY Ubuntu 7.04 freezes when it starts up!"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Elliot_M on 2007-08-05
Hi i was wondering if someone could help me out im running Ubuntu 7.04 on a DEll Inspiron E1505 (ATI Graphics card)and everything was working great i had no errors i got everything working just fine ive been using ubuntu for about 3 months now and only this morning it loads up to the orange default background and loads Nautilus and then just stops loading is frozen right in the middle of the things starting up and the mouse is frozen and i cant do anything but stare at the screen! PLEASE HELP!!

---

### Post by proalan on 2007-08-05
have you tried the boot options...

- recovery mode
- other listed kernels (if any)

---

### Post by Elliot_M on 2007-08-05
i have tried the recovery but i do not know what to type in or anything..ne ideas?

---

### Post by HereInOz on 2007-08-05
When you boot up, press ESC when GRUB starts to load, and you will get the boot menu.   You will see there options to boot from either the latest kernel, at the top, or other kernels down the list.  

It is possible that you have problems since a kernel upgrade, so try booting from one of the earlier kernels and see what happens.  If that is successful, you can then go into Synaptic and un-install the latest kernel if you wish.

---

### Post by Elliot_M on 2007-08-05
i tried that and it still isn't working..

---

### Post by louieb on 2007-08-05
When you get the grub menu highlight the ubuntu entry and press **e **to do a one time edit. Highlight the kernel line and press **e** again to edit and remove the  **quiet splash**. Then you can see where its dieing. My laptop for some reason will lock up on boot when it has a hard time making a wireless network connection.  It gives the cryptic message of bug: soft lockup on cpu0.  Once you know more then maybe someone can give you a workaround.

---

### Post by Elliot_M on 2007-08-05
ye i tried that 2 it didnt work..but what do i type in after i highlight kernal and press e then what?

---

### Post by proalan on 2007-08-06
does the recovery mode take you to a working terminal prompt?

if so do 
```
startx
```to start up the xserver i.e. the graphical interface and to log on as ROOT user.

if not then do as 'louieb' suggested
1. select the kernel and press 'e', this will allow you to edit the line.
2. remove 'quiet splash' from the end of the line. Press 'return'
3. press 'b' to boot the kernel.

This process basically outputs services being loaded etc... as ubuntu is loading.
then let us know what what service(s) are failing to load when it hangs or the line it hangs at.

Did you install any updates recently before the event, like a kernel update from the update manager.
Also could you post the options listed in grub and the kernel versions?

---

### Post by Elliot_M on 2007-08-06
k i got it to load when i went through startx then i tried to log out and it said that  the gnome display manager is not running ad that i may be running something like KDE and then it gives me an error that says "error while running Command" what do i do now?

---

### Post by Elliot_M on 2007-08-06
> **proalan said:**
> does the recovery mode take you to a working terminal prompt?

if so do 
```
startx
```to start up the xserver i.e. the graphical interface and to log on as ROOT user.

if not then do as 'louieb' suggested
1. select the kernel and press 'e', this will allow you to edit the line.
2. remove 'quiet splash' from the end of the line. Press 'return'
3. press 'b' to boot the kernel.

This process basically outputs services being loaded etc... as ubuntu is loading.
then let us know what what service(s) are failing to load when it hangs or the line it hangs at.

Did you install any updates recently before the event, like a kernel update from the update manager.
Also could you post the options listed in grub and the kernel versions?

i installed the latest update im not sure what it was and i tried to uninstall wine from my system..

---

### Post by Elliot_M on 2007-08-06
and after i log onto root what do i do now? i just want the ubuntu to start working like it was before i had no problems b4...

---

### Post by proalan on 2007-08-06
does everything work properly from when you do startx up until the point you try and log out?

you could check your systems log via the log viewer 
```
System menu > Choose Administration > System Log
```
it requires a bit of time and investigation going through as it contains every event thats taken place.

an explanation of the organization of logs located here
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer)
I suggest you start with the boot and kernel entries first.

---

### Post by proalan on 2007-08-06
A quicker solution might just be to reinstall ubuntu.

if you have your home folder on another partition your account will be preserved during the installation process. If not you could copy your home folder to an external storage device or to your windows partition if you have one, and copy it all back after the installation.

---

### Post by Elliot_M on 2007-08-06
> **proalan said:**
> does everything work properly from when you do startx up until the point you try and log out?

you could check your systems log via the log viewer 
```
System menu > Choose Administration > System Log
```
it requires a bit of time and investigation going through as it contains every event thats taken place.

an explanation of the organization of logs located here
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer)
I suggest you start with the boot and kernel entries first.

what am  looking for in the log? and if i find something bad what can i do? can i like restore ubuntu to an earlier date? like in windows?

---

### Post by louieb on 2007-08-06
> **Elliot_M said:**
> ....bad what can i do? can i like restore ubuntu to an earlier date? like in windows?
Depends do you have a backup?
> what am  looking for in the log?Your looking for a clue. If there a 50 way to leave your lover then there are at least that many things that can cause a system freeze. You say you were trying to uninstall wine. Were you deleting stuff as root or with sudo? Maybe you got carried away.
I'm with **proalan** on this one  do a reinstall. Might want to use a live CD to try and get you data copied off.

---

### Post by Elliot_M on 2007-08-06
alright if i was to do a reinstall what are the steps to get my information saved when i reinstall?

---

### Post by Elliot_M on 2007-08-06
> **proalan said:**
> A quicker solution might just be to reinstall ubuntu.

if you have your home folder on another partition your account will be preserved during the installation process. If not you could copy your home folder to an external storage device or to your windows partition if you have one, and copy it all back after the installation.
 

since im logged on as root it wont show me what external drives that are connected so i cant transfer anything ? ne ideas?

---

### Post by Elliot_M on 2007-08-07
alright well i burned alll my info on to dvd's except my bookmarks on firefox is there anyway i can retrieve them? i cnt seem to find them?

o nd when i installed the current ubuntu version i had to go through the alternate method becuase of my graphics card could u tell me where i can find a tutorial on how to reinstall ubuntu?

---

### Post by louieb on 2007-08-07
> **Elliot_M said:**
> ... bookmarks on firefox ...cnt seem to find them?

In a hidden  folder  in  your home named  .mozilla/firefox/... 

> **Elliot_M said:**
> ...tutorial on how to reinstall ubuntu?
Nice alternate CD how to at [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by proalan on 2007-08-07
Just to point out in case you don't know

your home directory contains a whole bunch of hidden folders that store program settings and preferences, like your thunderbird account, gimp panel layouts, fonts and browser bookmarks and firefox plugins. Press CTRL + H  to reveal these folders.

There are 2 programs called 'reconstructor' and 'aptoncd' which you may find useful for backup / restoration in case you have to reinstall ubuntu in the future.

The first allows you to create your own 'live cd' with packages / programs of your own choice.
The second is used primarily to back up packages / programs onto cd so you don't have to download them to restore your system.

Best of luck

---

### Post by tntwo on 2007-08-07
Hey!guys,
        I found that the "irqpoll" in the menu.lst makes this happen more often,so if you enable this option please remove that.

---

### Post by Elliot_M on 2007-08-07
thnx guys for all ur help u guys are awesome!  

couple more things..the website for the alternate installation isn't  very helpful and when i install ubuntu how can i configure my internal wireless card?

---

