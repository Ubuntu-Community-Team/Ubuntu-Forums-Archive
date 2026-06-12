---
title: "A Number of MacBookPro3,1 Hardware Issues. And a software issue."
date: 2009-04-08
forum: Apple Hardware Users
---

### Post by aptenodytes on 2009-04-08
Hey all,

I'm experiencing some hardware problems with my MacBookPro3,1 and Ubuntu 8.10.

Specifically...

1. To double click, I have to hit fn+ctrl+f10. How can I get the mouse to double click?

2. The brightness control keys are working, but only to a certain point. As in, when I turn the brightness up about 1/3 of the way, if I hit again, it goes back to the beginning (dark), rather than all the way through.

3. The backlit keys are not working.

4. It is running very hot. I've been solving this by using the terminal to run some program (apologies on being unspecific and a noob) to set the minimum temp to 4000 RPM rather than 2000 RPM. Is there a graphical interface program to solve this, or at least something like FanControl for Leopard where I can set the threshold level for the fan to kick in as well as the base speed, etc?

5. I have partitioned a part of my Leopard HD (500GB) to be used for Ubuntu (100GB). Is there a way I can use one of the Ubuntu Music Players (amarok?) and access my music library on the Leopard part of my HD and use that folder as the default library where music is stored so I can listen to it in Ubuntu? Also ... can I make that folder writeable so I can import CDs / MP3s / whatever in Ubuntu and have them stored where they would be on Leopard? Right now I can't do this because it says I do not have permission to open the folder on my OS X HD.

6. Can I expand the Ubuntu partion further? If so, how? As in, further into the OS X space.

7. Having some problems with 'Suspend.' The computer will 'Suspend' (I think) but it does not wake up from Suspend. I have to hold the power button until it turns off (I hear a click), and then turn the computer back on.

Thanks very much in advance, I know it's a lot, and I appreciate any help I can get!

aptenodytes

---

### Post by hajk on 2009-04-08
Of course you should first check the Ubuntu community wiki page for the MBP 3,1 and the version of Ubuntu you're running. Just follow the link in the sticky at the top of this forum.

Now, that having been said, I want to tell you that I'm running a related OS on my MBP 4,1 with a 2.6.29 kernel, and I find that all those hardware problems have gone away: fn-key works out-of-the-box, Apple F1/2 keys adjust screen brightness, F10-12 adjust sound volume, F7-9 work in Totem, the Eject button works, F3/4 are not assigned (of course), and F5/6 should work (xev shows the proper key assignments, but I'm still trying to figure out the required settings in /sys/devices/platform/applesmc.768/leds/). Further, my BT mighty mouse can just be paired without having to worry about resetting hci_usb mode. All of this should also work on the 3,1.

So, even if you get stuck for now doing it the Ubuntu way, remember that the 2.6.29 (or later) kernel will be part of Ubuntu 9.10...):P

---

### Post by aptenodytes on 2009-04-08
I have checked that, it is helping but not very much. Thanks for your reply.

---

### Post by cyberdork33 on 2009-04-08
> **aptenodytes said:**
> 1. To double click, I have to hit fn+ctrl+f10. How can I get the mouse to double click?
To double-click? You can't just click twice with a mouse? that seems like a strange issue. Try removing the mouseemu package.

> **aptenodytes said:**
> 2. The brightness control keys are working, but only to a certain point. As in, when I turn the brightness up about 1/3 of the way, if I hit again, it goes back to the beginning (dark), rather than all the way through.

3. The backlit keys are not working.

4. It is running very hot. I've been solving this by using the terminal to run some program (apologies on being unspecific and a noob) to set the minimum temp to 4000 RPM rather than 2000 RPM. Is there a graphical interface program to solve this, or at least something like FanControl for Leopard where I can set the threshold level for the fan to kick in as well as the base speed, etc?
You need to make sure that applesmc is loading. That would be a big step in the right direction for all of these. There is no GUI for this (yet), but someone had been working on one at one time here in the forum, and there are also some scripts posted that can automatically change fan speed.

> **aptenodytes said:**
> 5. I have partitioned a part of my Leopard HD (500GB) to be used for Ubuntu (100GB). Is there a way I can use one of the Ubuntu Music Players (amarok?) and access my music library on the Leopard part of my HD and use that folder as the default library where music is stored so I can listen to it in Ubuntu? Also ... can I make that folder writeable so I can import CDs / MP3s / whatever in Ubuntu and have them stored where they would be on Leopard? Right now I can't do this because it says I do not have permission to open the folder on my OS X HD.
Linux respects the file permissions set on file by OS X. Your OS X user and your Ubuntu user are not the same person (as the system sees it), and thus your Ubuntu user does not "own" those files and access is denied. You can either modify your user account to match the uid of your OS X user (uid is your userid number, not your username), or you can edit the permissions on the files to allow access to all other users.

You cannot write to an HFS+ filesystem unless you disable journaling (and I wouldn't recommend doing that).

> **aptenodytes said:**
> 6. Can I expand the Ubuntu partion further? If so, how? As in, further into the OS X space. You can use gparted / disk utility to shrink your OSX partition, and gparted should be able to extend your linux partition.

> **aptenodytes said:**
> 7. Having some problems with 'Suspend.' The computer will 'Suspend' (I think) but it does not wake up from Suspend. I have to hold the power button until it turns off (I hear a click), and then turn the computer back on.probably need to file a bug / find a bug about that...

Can you tell us what version of Ubuntu you are using? Have you tried the Jaunty Beta?

---

### Post by aptenodytes on 2009-04-08
Thank you very much for all your help, cyberdork33. I am running 8.10. I have not tried the Beta yet, I plan on updating in a couple weeks when it comes out though.

The only serious issues right now are

1. Suspend is not working
2. I can't right click unless I use the command fn+ctrl+f10.

---

