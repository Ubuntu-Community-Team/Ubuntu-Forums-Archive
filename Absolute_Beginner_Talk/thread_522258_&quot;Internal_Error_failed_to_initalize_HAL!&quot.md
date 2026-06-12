---
title: "&quot;Internal Error: failed to initalize HAL!&quot; Help please."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-08-10
That message pops up when I booted my computer on the desktop. I have already read a few other threads about this problem. Trying both:
Sudo /etc/init.d/dbus restart
That didn't work so I then tried:
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12
Neither worked. 
Prior to this I had a problem with GDM. "The GDM group 'gdm' does not exist. Please correct GDM configuration and restart again." I fixed that by doing sudo apt-get remove gdm and then sudo apt-get install gdm. But now I got this HAL error. Any idea to help this problem? It isn't allowing me to connect online.

---

### Post by CapitanYochua on 2007-08-10
I think the problem arrives from typing the commands in terminal. Even though I am using sudo it is as if "it doesn't listen or respond" in a way, because I'm not root user. How can I make myself root user or make it "listen" as if I was root user?

---

### Post by SOULRiDER on 2007-08-10
sudo will run commands as if you were roo, but if you *REALLY* need to become root you can do
```
sudo -i
```

Try reinstalling HAL and see what happens:
```
sudo aptitude purge hal
sudo aptitude install hal
```

---

### Post by CapitanYochua on 2007-08-10
I know..it's weird. But I'll boot up some recovery mode and it will make me root. When I run the commands there I actually get positive output. any explanation?

---

### Post by CapitanYochua on 2007-08-10
sudo -i didn't do anything for me. I think I might have some problems with /etc/groups

---

### Post by CapitanYochua on 2007-08-10
okay. Great! Now I have larger problems. After doing the "try reinstalling hal" I rebooted. Once I get past the login screen the whole screen just stays black. Nothing. Can't see desktop. Helppp. Involving becoming the root user I got:
chown:'root:utmp:' invalid group
chown:'root:tty:' invalid group
chgrp: invalid group 'adm'

PLLLEASE HELP!!

---

### Post by SOULRiDER on 2007-08-10
Right now i wish i had my ubuntu installation here with me...

In a recovery console try to (re)start HAL and DBUS with
```
sudo /etc/init.d/hal restart
sudo /etc/init.d/dbus restart
```

Once thats done, try to start GDM or Xorg
```
sudo /etc/init.d/gdm start

or

sudo startx
``` (im not sure if these two commands will work correctly though.

If that still fails try reinstalling dbus and hal.. im out of ideas for now... =/

Good luck!

---

### Post by CapitanYochua on 2007-08-10
okay for the first command. 
I got...
sudo: /etc/init.d/hal: command not found
For the second command  got the following output...
*Stopping System Tools Backends system-tools-backends    [ok]
*Stopping Avahi /mDNS/DNS-SD Daemon: avahi-daemon     [fail]
*Stopping DHCP D-Bus daemon dhcdbd                                 [ok]
*Stopping system message bus dbus                                     [ok]
chgrp: invalid group 'messagebus'


The third command didn't help. Just took me to the log in screen to experience the same problem afterI log in.

sudo startx took me to some weird black and white checkered looking screen or something. And just stayed there. So not much help; more worry.

---

### Post by ashishgoel on 2007-08-10
if u able to start workin in Ubuntu and again gets a HAL error after update, solution for u-

Re: Recent HAL update caused frequently failure for "suspend when lid closes"

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...
__________________

---

