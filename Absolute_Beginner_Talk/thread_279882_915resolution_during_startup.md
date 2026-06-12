---
title: "915resolution during startup"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by levi086 on 2006-10-18
I've ended up totally depressed about making 915resolution work during bootup. :mad: 

A few weeks ago I managed to install and even change the resolution to my native one (1280x800) on my Fujitsu Pi1505 laptop by the usual command: sudo 915resolution x 1280 800 32; x being your preferred mode to be overwritten.

Now I've got frustrated typing that in terminal every time I start kubuntu. I've tried a lot of ways, mainly trying to write a script and then use the update-rc <script_name>, but to no avail. :evil: 

Can anyone help me on how to make my 915res be executed during startup ?

I apologize if there is some similar thread to this (I checked just before I created this one).

Thank you in advance. :KS

---

### Post by Kateikyoushi on 2006-10-18
Try to install this then reboot or restart the x server.

```
sudo aptitude install 915resolution
```

---

### Post by levi086 on 2006-10-19
no use :/ is there a way how i can give root priviledges for my script during runtime ?

---

### Post by Kateikyoushi on 2006-10-19
Add it to your initscripts, you can do it like [this]("http://linuxmint.com/content/view/212/52/").

---

### Post by levi086 on 2006-10-19
thanks a lot. i'll try it out and inform you as soon as i arrive home. strangely enough linux is failing to connect with my university hotspot this morning :/

---

### Post by levi086 on 2006-10-19
funny that it worked before i formatted a while ago.
now it's telling me:

```
sudo aptitude install 915resolution
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "915resolution"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

anyone knows what's the matter ?
thanks.

---

### Post by Kateikyoushi on 2006-10-19
Probably repositories.

```
kateikyoushi@X505:~/Desktop$ sudo aptitude -s install 915resolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  915resolution 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1kB of archives. After unpacking 131kB will be used.
Would download/install/remove packages.

```

This topic also start today with the same vga. [LINK]("http://ubuntuforums.org/showthread.php?t=279247")

---

### Post by levi086 on 2006-10-20
Nevermind. I installed 915resolution manually by downloading and extracting it anywhere. Then I created a small script to actually overwride one of the modes in 915resolution, gave exe permissions, and then made this script execute in the /etc/rc.local

it works :)

thx a lot

---

