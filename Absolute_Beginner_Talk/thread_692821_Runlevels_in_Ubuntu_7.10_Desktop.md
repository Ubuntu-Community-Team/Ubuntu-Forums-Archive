---
title: "Runlevels in Ubuntu 7.10 Desktop"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by descent89 on 2008-02-10
Please....how to change them?
I would like to boot straight into BASH SHELL but I dont know how....i read a lot of stuff about editing inittab to change default runleveles, but there is no inittab in my Ubuntu.....and I really don't understand that Upstart stuff :confused:

Would you be so kind a post here a noob-friendly guide how can I make my own Runlevel without GUI? thx a lot:-)

---

### Post by jeffus_il on 2008-02-10
There are lots of ways to do what you want. The quickest would be to remove the gdm link to the gdm startup script in /etc/rc2.d.

Then if  you want to run the gui type > sudo /etc/init.d/gdm startup

---

### Post by The Cog on 2008-02-10
Ububtu normally uses runlevel 2, and levels 3, 4, 5 are configured pretty-much identically. 

Runlevel 1 on all Linuxes that I know of is "single user mode" where only the essential things are started - no GUI, no networking, no other consoles, print spoooler etc - it is intended as a kind of maintenance mode I guess.

As jeffus_il says, if you never want the GUI on startup, the easiest thing to do is to delete the link  /etc/rc2.d/S30gdm and then you have a custom level 2 which doesn't start the GUI (levels 3, 4, 5 still do). You can then switch between runlevels if you like with 
**sudo init 3**
and back to 2 with sudo init 2.

Red Hat et al use runlevel 5 for default and runlevel 3 for everything except the GUI. Sometimes you see instructions saying to switch to runlevel 3 to kill the GUI. We sometimes get posts here asking why that doesn't work in Ubuntu.

FYI, init 0 powers off and init 6 reboots.

P.S:
It's **sudo /etc/init.d/gdm start** (not startup)

PPS:
I can't figure out yet what replaces the old inittab fie that used to say which runlevel to use. It must be documented somewhere (you'd think). So as of now, I don't know how to select the runlevel at boot.

---

### Post by descent89 on 2008-02-10
thanks a lot :)

please, how can i make a different runlevel default? i tried ```
sudo telinit 3
``` but it only switched runlevels, i would like to have it permanent ;)

please tell me if there is a difference between
```
sudo /etc/init.d/gdm start
```
and
```
startx
```

---

### Post by K.Mandla on 2008-02-10
You could always rip out GDM; that would leave you at a login prompt each time you start the computer, but still give you a GUI when you enter startx at the terminal.

---

### Post by jeffus_il on 2008-02-10
Ah! To make it permanent, you need to edit the Grub Menu and modify the parameters that the boot loader Grub passes to the kernel when it loads it.

Edit the Grub menu:
```
sudo nano /boot/grub/menu.lst
```change the line that looks something like this (the "kernel" line):
```
## ## End Default Options ##

title           Ubuntu hardy (development branch), kernel 2.6.24-7-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-7-generic root=UUID=287b3dcf-9adb-45ff-963-b699af1733c4 ro vga=normal

```Add 3 to the end of the "kernel" line.

But this won't work in Ubuntu, It works in other Linuces but Ubuntu has peculiar behavior. Search the forum and you will find many references to this. I will look for a workaround, in the meantime, and post back here!

There is a bug open on Launchpad about this:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014)

---

### Post by jeffus_il on 2008-02-10
```
sudo /etc/init.d/gdm start
```
Runs the Gnome Display Manager which logs you in using a gui and gives you some options to choose from for running your session.

```
startx
``` is run after login to a console and runs the X Server directly

---

### Post by unclernie on 2008-02-14
Wow.  upstart has been here for a year, and we're still trying to find basic compatibility documentation.
  I did some poking around last night.  `man init` told me about /etc/event.d, and I went browsing there.  I found a bunch of scripts named rcN, where N is a number between 0 and 6, and one suspiciously named rc-default, so I browsed that one.  The comment at the top leads me to believe it sets the default runlevel, and the 'else' clause of all the tests is `telinit 2`.  Coincidence?

  So I would think that you could change the default runlevel by changing that default call to telinit in this script...
  But if you look in /etc/rc2.d thru /etc/rc5.d, you will find that every one of them contains links named S10xserver-xorg-input-wacom and S50gdm.  And rc1.d and rc6.d contain links named K01gdm.  So changing the runlevel alone won't give you a console-only machine.  You have to create a console-only runlevel.

  So if this really is compatible with the old sysVinit stuff, all you would have to do is:
  sudo rm /etc/rc3.d/S10xserver*
  sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K01gdm
  
I tried that, then rebooted.  At the grub menu, I hit 'e', which brought up a screen with the menu.lst entries for the first kernel in my list.  I hit the down-arrow until the 'kernel' line was hilited, and hit 'e' again to edit it.  I appended a '3' to the end of the line, hit enter, then escape, which took me back to the menu, and I let it boot.  But it booted into gdm anyway.

  I then logged in, opened a terminal, and issued the command 'sudo telinit 3'.  My gnome session immediately dissapeared, and I got an extremely ugly hash-filled screen with some barely-readable messages in a HUGE font reminiscent of my old VIC-20.  But I hit enter, and I got a barely - readable login: prompt amid the hash.  UGLY!

  I then triggered a reboot with the three-finger salute, and this time, instead of logging in with gdm, I simply hit ctrl-alt-F2, which gave me a clean, readable console login, although it was in the VIC-20 font, which looked like it would give me about 10 lines of 40 characters on my WXGA screen!

  I decided to take a risk, and edited /etc/event.d/rc-default, changing 'telinit 2' to 'telinit 3 on two lines near the end.  Then reboot.   SCARY!  the system appeared to boot, but the screen was totally black.  After a few minutes, I ventured a finger towards the keyboard, and touched the 'alt' key.  I got a screenful of huge characters.  Now I can see better the dimensions: 22 lines by 40 characters. It had booted with the screensaver already triggered.

Several errors. 

[ (some numbers)] PCI: Cannot allocate re
source region 0 of device 0000:00:00.0
Loading, please wait...

kinit: name_to_dev_t(/dev/disk/by-uuid........
kinit: trying to resume...
kinit: no resume image, doing normal boot

Ubuntu 7.10 studio tty1

studio login:


Huge font, but no hash.  I login, and quickly discover that the 'virtual' screen is much larger than my physical one.  My shell prompt is well below the bottom of my display, and I have to hit repeated carriage returns in order to see the results of any commands I type, but `ps aux | grep xorg` tells me that no X server is running, so I guess I was successful, sorta.

Well, enough experimenting for one session.  I run `startx`, and I get my desktop, where I can open a usable terminal and clean up my edits to /etc/event.d/rc-default.

So what did I accomplish?  I learned a bit about upstart's config, I managed to create a runlevel 3 which is console-only, although it looks like it needs some vgamode love to make it usable.  For that matter, the virtual ttys available on ctrl-alt-F2 thru -F6 from a normal X session need that vga mode love as well.
  What's left to learn?
  How can I specify a runlevel in the grub editor, that will be effective for only the current boot?  Lilo was so easy!  'linux 3' did it!

---

### Post by macogw on 2008-02-14
> **unclernie said:**
> Wow.  upstart has been here for a year, and we're still trying to find basic compatibility documentation.
You can still use update-rc.d like you would on any Debian system.  It's roughly equivalent to chkconfig on Red Hat.

> 
  So I would think that you could change the default runlevel by changing that default call to telinit in this script...
  But if you look in /etc/rc2.d thru /etc/rc5.d, you will find that every one of them contains links named S10xserver-xorg-input-wacom and S50gdm.  And rc1.d and rc6.d contain links named K01gdm.  So changing the runlevel alone won't give you a console-only machine.  You have to create a console-only runlevel.

Yep, just like Debian.  On Debian, 0 is halt, 6 is reboot, 1 is single-user, and everything else is multi-user with X.  Having 3 be multi-user no X and 5 be multi-user with X is a Red Hat convention.

---

### Post by aBitLater on 2008-02-16
my noob curiosity here has left me corn-fused...

If I'm studying a linux admin book, I'm lost because I can't see an /etc/inittab file and then I have no option for init 3 to console at boot?

What is the purpose of making ubuntu non-standard in this respect?  What's wrong with having init 3 boot to a console - with out a GUI.

---

### Post by PeterJS on 2008-02-16
It's a matter of moving forward, SysV init is over 25 years old at this point, ubuntu has moved to upstart, Fedora* and Gentoo are using init-ng, OSX is using launchd. It's going to take a while for people to shake out which of these SysV replacements is the best, and as long as that's happening there won't be any universal standard, and even when a replacement is chosen historical SysV documentation probably won't correctly describe it, paraphrasing LnW, it's hard to improve something if you clone it exactly.

*FC9 will be using upstart.

Also as for breaking standards with what the run levels do, Ubuntu most certainly does no such thing, it adheres to the Debian standard. If you're expecting a Debian derivative to follow Red Hat standards that is kinda silly, I can see being annoyed at a RH derivate varying from the Red Hat standard, by Ubuntu has no Red Hat lineage.
[http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)

---

### Post by aBitLater on 2008-02-17
Hi PeterJS,

My frustration here (and not that 'runlevels' are the only point) is that Ubuntu is *REALLY* nice for noobs like me, because it just plain WORKS... but at the same time, as I want to learn more about linux administration, I often can't find the directories or files that are mentioned in several linux admin. books.

You and others mentioned "upstart", can you show some links that give a good explanation (user oriented, not developer oriented).

Thanks & Cheers

EDIT:  I also would like to boot by default to a console - I think this will help force me to learn 'command line' administration.

---

### Post by aBitLater on 2008-02-17
> **K.Mandla said:**
> You could always rip out GDM; that would leave you at a login prompt each time you start the computer, but still give you a GUI when you enter startx at the terminal.

so, how do you do this?

Do I go to /etc/rc3.d and remove the gdm link and all links that follow it (since they may or may not be dependent on gdm)?

```

root@mycomputer:/etc/rc3.d# ls -al
<snip>
lrwxrwxrwx   1 root root    13 2008-02-02 00:18 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    17 2008-02-02 00:18 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root    13 2008-02-02 00:18 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root    14 2008-02-02 00:18 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root    17 2008-02-02 00:18 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root    22 2008-02-02 00:18 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    21 2008-02-02 00:18 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root    18 2008-02-02 00:18 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root    19 2008-02-02 00:18 S99rmnologin -> ../init.d/rmnologin


```

---

### Post by The Cog on 2008-02-17
Here is an interesting article on upstart:
[http://lwn.net/Articles/202779/](http://lwn.net/Articles/202779/)
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by PeterJS on 2008-02-17
> **aBitLater said:**
> Hi PeterJS,

My frustration here (and not that 'runlevels' are the only point) is that Ubuntu is *REALLY* nice for noobs like me, because it just plain WORKS... but at the same time, as I want to learn more about linux administration, I often can't find the directories or files that are mentioned in several linux admin. books.

You and others mentioned "upstart", can you show some links that give a good explanation (user oriented, not developer oriented).

Thanks & Cheers

EDIT:  I also would like to boot by default to a console - I think this will help force me to learn 'command line' administration.

Firstly more launchpad fodder:
[http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart)
Wikipedia usually has enough to give you a boot in the right direction.

As of the books and documentation, you're probably not going to find as much stuff on the Debian family in professionally published media, you're far more likely to find commercial documentation and publication on the much more commercial Red Hat family, Debian being much more community driven tends to have it's lore tied up in wiki's and community based sites.
A good starting point for stuff to read is: [http://debianadmin.com/](http://debianadmin.com/)
For command line fu the Linux Documentation Project's Bash programming guide is a great resource for knowing how to do things, it won't give you the want, but once you know what you want to do it's a great guide/reference for the mechanics of how to get it done.
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by PeterJS on 2008-02-17
> **aBitLater said:**
> so, how do you do this?

Do I go to /etc/rc3.d and remove the gdm link and all links that follow it (since they may or may not be dependent on gdm)?

```

root@mycomputer:/etc/rc3.d# ls -al
<snip>
lrwxrwxrwx   1 root root    13 2008-02-02 00:18 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    17 2008-02-02 00:18 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root    13 2008-02-02 00:18 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root    14 2008-02-02 00:18 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root    17 2008-02-02 00:18 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root    22 2008-02-02 00:18 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    21 2008-02-02 00:18 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root    18 2008-02-02 00:18 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root    19 2008-02-02 00:18 S99rmnologin -> ../init.d/rmnologin


```

You'll want to leave the scripts in /etc/init.d alone as they're common to all run levels.

First remove the launcher for GDM from runlevel 3:
```

sudo unlink /etc/rc3.d/S30gdm

```
Then relink it back in tell it to stop on runlevel 3
```

sudo ln -s /etc/init.d/gdm /etc/rc3.d/K30gdm

```
That's S for start, and K for kill.
As for changing the default run level, I don't know I never tried.

There should be a more elegant and "correct" way of doing this with update-rc.d, but at the end of the day that linking and unlinking is what actually happens on disk. So that's not the conceptually correct way of doing it, but it works, hurray for pragmatism.

---

### Post by C. Wizard on 2008-02-17
> **aBitLater said:**
> my noob curiosity here has left me corn-fused...

If I'm studying a linux admin book, I'm lost because I can't see an /etc/inittab file and then I have no option for init 3 to console at boot?

What is the purpose of making ubuntu non-standard in this respect?  What's wrong with having init 3 boot to a console - with out a GUI.

If you want to learn Linux you might consider running Slackware.  It does almost everything the "old fashion" way. Actually, I prefer being able to configure everything, but just grew tired of it and decided to try U/Kubuntu since it does much of the "work" for you, but you do pay a price for that convenience.
Slackware 12 is the current stable release and the best to date, IMHO.
:)
Oh, btw, Slackware uses the inittab file as follows:
0 = halt.
1 = single user mode.
2 = unused, but configured the same as runlevel 3.
3 = multiuser mode (boots you to the command prompt and is the Slackware default).
4 = X11 with KDM/GDM/XDM ( your desktop, KDE, whatever).
5 = unused, but configured the same as runlevel 3.
6 = reboot.

You would never want set it to 0 or 6.
:)

---

### Post by aBitLater on 2008-02-17
Thanks for the links, they look like they'll be useful.

I haven't found anything yet about default boot to init 3, though the unlink may work.

I was wondering about ubuntu as a server  ... do people who use ubuntu server boot into the gui consistently?  I mean, isn't a server better off not running a GUI?  If so, maybe an ubuntu server admin can shed more light on that.

I might try out the slackware on another computer, C. Wizard.  How would you say slackware compares to opensuse?  Opensuse is the only other distro I've tried (except for Red Hat, eons ago)


Disclaimer: I'm still thrilled with Ubuntu!  I could set up my mother's computer on Ubuntu, that's how friendly it is, IMO.

---

### Post by oldos2er on 2008-02-17
Ubuntu server comes without a GUI.

---

### Post by C. Wizard on 2008-02-18
> **aBitLater said:**
> ...I might try out the Slackware on another computer, C. Wizard.  How would you say slackware compares to opensuse?  Opensuse is the only other distro I've tried (except for Red Hat, eons ago)...
I've not used OpenSUSE, but from what I've read and heard, it must be more like U/Kubuntu than Slackware.  

Slackware is fast, rock solid, and very secure, but it is not for the faint of heart.  You have to set up almost every aspect of the system by hand.  Until Slackware 12 was released last July you still had to mount and umount CDs, etc. 

First thing I do once the installation is complete and I have signed in at a command prompt, is configure the sound card, then xorg, etc., etc., etc.  

There are several Slackware sites, in addition to the Project site, and a great community of users that are happy to answer questions. 

There are many binary packages available on various sites, BUT, you are usually on your own to find the dependencies and install them one by one. 

The big advantages are, Slackware doesn't stamp their name all over the system. You can configure it anyway you want. You can install upgraded packages anytime you feel like it, not when they are "approved." Between Slackware as the OS and KDE as the desktop you are really able to customize and fine tune a system to run and look the way you want.

However, one of the draw back I found was, one, I got tired of doing all the configuration. Two, not everything I would install would work or work the way I thought it should, and I'm not geekie enough to be able to figure fix all those things. Sometimes I can figure it out and sometimes not. For example, there is a plug-in for The GImp called "refocus."   I could never get that to work in Slackware, but in Kubuntu, apt-get installed it and it worked.
Amazed me. 
:)

U/Kubuntu on the other hand is, as we know, very easy to install and it is even easier to add packages to it.

I'm running the same hardware, video drivers, and version of KDE on Kubuntu that was running with Slackware, yet KDE in Kubuntu has a more "polished" look to it and in generally more pleasing to the eye.  

So far it has been stable, but it is not as secure as Slackware.  I found and made the changes to the Grub menu to password protect the system and did save the changes and tested it. It worked.
A few days later I tried it and there was no password protection. Looked at the file and the changes I made were gone.  There are a couple of other things which don't come to mind at the moment, but they have concerned me enough to consider going back to Slackware.  Perhaps, when they release a 64 bit version of Slackware I'll take another look.

---

### Post by aBitLater on 2008-02-18
Thanks for the input.

With what you said, I think I'll stay away from slackware for the moment - my extra computer needs to be usable by my wife, and she'll knock me around like a little girl if I keep the computer down for a day or two trying to configure it! :)

But it sounds like the perfect system to use for learning more about linux when I get another computer.

---

### Post by freakalad on 2008-02-27
I've set up a server with 7.10, and added gdm after ("sudo apt-get install ubuntu-desktop").

Great! Now it keeps on booting into the GUI.

Absolutely NOTHING happens when I do: "sudo telinit 3" (or 1 or anything else for that matter)
Just keeps on reloading the GUI.

Latter versions of Ubuntu does not utilise the /etc/inittab file, as so much forums & documentation details. Everything I've found on google & this forum only details other people's hassles in trying to get the machine to boot up in a non-GUI environment. 
Altering the /boot/grub/menu.lst does nothing except corrupt start-up's.

It's really a very simple issue: start up in runlevel 3 in stead of runlevel 5. How hard should it be?

Has anyone found a reliable (preferably simple) way of modifying start-up scripts to boot properly? 
Should be an addition or substitution of a single character: 5 to 3

Please help. Some clarity would be appreciated

---

### Post by PeterJS on 2008-02-27
It's actually booting to runlevel 2, Debian derviates and Red Hat derivaties handle run levels differently.
[http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)
To stop gdm from running on all run levels you can run:
```

sudo update-rc.d -f gdm remove

```
And if you read the manual for update-rc.d it will give examples of selectively re-adding gdm to certian run levels.

---

### Post by The Cog on 2008-02-27
> **freakalad said:**
> I've set up a server with 7.10, and added gdm after ("sudo apt-get install ubuntu-desktop").

Great! Now it keeps on booting into the GUI.

Absolutely NOTHING happens when I do: "sudo telinit 3" (or 1 or anything else for that matter)
Just keeps on reloading the GUI.

Latter versions of Ubuntu does not utilise the /etc/inittab file, as so much forums & documentation details. Everything I've found on google & this forum only details other people's hassles in trying to get the machine to boot up in a non-GUI environment. 
Altering the /boot/grub/menu.lst does nothing except corrupt start-up's.

It's really a very simple issue: start up in runlevel 3 in stead of runlevel 5. How hard should it be?

Has anyone found a reliable (preferably simple) way of modifying start-up scripts to boot properly? 
Should be an addition or substitution of a single character: 5 to 3

Please help. Some clarity would be appreciated

I guess you didn't read the rest of this thread. Try reading post #3.

If you want a non-GUI startup, use this command:
**sudo rm /etc/rc2.d/S30gdm**
and then use **startx** when you want a GUI

---

### Post by macogw on 2008-02-27
Most Linux admin books are written for Red Hat.  If you want to learn Red Hat, use Fedora.  If you want to learn Debian, Ubuntu is fine, but you should be reading a Debian administration book.  Red Hat and Debian are often very different.

---

### Post by omegamormegil on 2008-02-27
The file /etc/rc2.d/README says:  

   "The scripts in this directory are executed each time the system enters
   this runlevel.

   The scripts are all symbolic links whose targets are located in
   /etc/init.d/ .

   To disable a service in this runlevel, rename its script in this directory
   so that the new name begins with a 'K' and a two-digit number, where the
   number is the difference between the two-digit number following the 'S'
   in its current name, and 100.  To re-enable the service, rename the script
   back to its original name beginning with 'S'.

   For a more information see /etc/init.d/README."

Following these instructions I executed:

```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm
```

After a reboot, I was presented with the bash login prompt and no GUI!  After logging in, typing "startx" successfully launched the GUI.  I find this preferable to deleting the S30gdm file, because to reverse the modifications, you can just rename the file again with: ```
sudo mv /etc/rc2.d/K70gdm /etc/rc2.d/S30gdm
```

---

### Post by freakalad on 2008-02-28
Thanks, guys.

Does make sense. I just expected a more elegant solution, but this will do nicely.

Just a bit peculiar that there is not better & more concise documentation on the subject, especially since it deviated from the norm (inittab)

---

### Post by The Cog on 2008-02-28
Most of them, you can adjust with Syatem->Administration->Services. But you can't adjust gdm that way because as soon as you un-check the gdm checkbox the GUI gets killed off and it never gets the chance to save the change to the filesystem.

---

### Post by PeterJS on 2008-02-28
> **freakalad said:**
> Thanks, guys.

Does make sense. I just expected a more elegant solution, but this will do nicely.

Just a bit peculiar that there is not better & more concise documentation on the subject, especially since it deviated from the norm (inittab)

Inittab was the norm for 25 years, things are changing, see the top of page two:
[http://ubuntuforums.org/showpost.php?p=4345063](http://ubuntuforums.org/showpost.php?p=4345063)

---

### Post by Robert Citek on 2008-02-28
> **unclernie said:**
> Wow.  upstart has been here for a year, and we're still trying to find basic compatibility documentation.

Ditto.  Along the same lines, I'm looking for answers to these questions:

1) How does one change the default runlevel?  When Ubuntu boots, it boots into runlevel 2.  I'd like it to boot into runlevel 5.  With /etc/inittab I would modify the "id:" line.

2) How does one re-read the /etc/event.d files?  With inittab, I would type 'init -q'.  In upstart I modified the /etc/event.d/rc-default file, changing 2 to 5.  However, if I type "init 1" and then exit from runlevel 1, Ubuntu still goes into runlevel 2.  According to the docs, any changes in events should be automatic:

 [http://upstart.ubuntu.com/faq.html#reload](http://upstart.ubuntu.com/faq.html#reload)

3) How does one specify a different runlevel at boot time?  With init I would simply specify the run level at the end of the kernel line. That doesn't work in Ubuntu.

4) How does one enter Emergency mode?  Before upstart one could specify -b and only a minimal number of drivers were installed, e.g. no networking.

I've been googling and searching the forums, but nothing yet.

Any pointers appreciated.

Regards,
- Robert

---

### Post by Robert Citek on 2008-02-28
> **omegamormegil said:**
> For a more information see /etc/init.d/README."

Following these instructions I executed:

```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm
```


An alternative solution, especially familiar for those who have used chkconfig on fedora:

```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf --list
sudo sysv-rc-conf --level 2 gdm off

```

Regards,
- Robert

---

### Post by Robert Citek on 2008-02-28
> **Robert Citek said:**
> 1) How does one change the default runlevel?  When Ubuntu boots, it boots into runlevel 2.  I'd like it to boot into runlevel 5.  With /etc/inittab I would modify the "id:" line.


One does it by editing /etc/event.d/rc-default.  Here's what mine looks like now:

```

# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
       def_RL=5
       runlevel --reboot || true

       if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
           telinit S
       elif [ -r /etc/inittab ]; then
           RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
           if [ -n "$RL" ]; then
               telinit $RL
           else
               telinit $def_RL
           fi
       else
           telinit $def_RL
       fi
end script

```

To change the default runlevel, change the value of def_RL.

Regards,
- Robert

---

### Post by Robert Citek on 2008-02-29
> **Robert Citek said:**
> 3) How does one specify a different runlevel at boot time?

One modifies the code in /etc/event.d/rc-default to processes the boot command line (/proc/cmdline) :
```

# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
        def_RL=5
        runlevel --reboot || true

        RL="$(< /proc/cmdline tr ' ' '\n' | grep -v '[^0-9]' | tail -1 || true)"
        if [ -n "$RL" ] ; then
            RL=$RL
        elif grep -q -w -- "-s\|single\|S" /proc/cmdline; then
            RL=S
        elif [ -r /etc/inittab ]; then
            RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
            if [ -n "$RL" ]; then
                RL=$RL
            else
                RL=$def_RL
            fi
        else
            RL=$def_RL
        fi
        telinit $RL
end script

```

The logic's a bit convoluted, but it works.

Regards,
- Robert

---

### Post by Robert Citek on 2008-02-29
> **Robert Citek said:**
> One modifies the code in /etc/event.d/rc-default to processes the boot command line (/proc/cmdline) :
```

# rc - runlevel compatibility
...

```

Slightly easier to read code:

```

# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
        default_runlevel=5
        runlevel --reboot || true

        # check the boot command line for runlevel
        RL="$(< /proc/cmdline tr ' ' '\n' | grep -v '[^0-9]' | tail -1 || true )"
        grep -q -w -- "-s\|single\|S" /proc/cmdline &&
            RL=S

        # check the inittab for a runlevel
        [ -z "$RL" -a -r /etc/inittab ] &&
            RL="$( < /etc/inittab grep ^id:[0-9sS]: | cut -d: -f2 || true)"

        # if no runlevel specified, use the default
        [ -z "$RL" ] &&
            RL=$default_runlevel

        telinit $RL
end script

```

---

### Post by Robynsveil on 2008-03-26
I'm trying to upgrade my NVidia driver, which requires me to run as root at runlevel 3 *without* X up at all. In the instructions to upgrade the driver, I was told that I was running in runlevel 1 and needed to issue a **telinit 3** -- this, however, launched the gui.

> **The Cog said:**
> Ubuntu normally uses runlevel 2, and levels 3, 4, 5 are configured pretty-much identically. 
As jeffus_il says, if you never want the GUI on startup, the easiest thing to do is to delete the link  /etc/rc2.d/S30gdm and then you have a custom level 2 which doesn't start the GUI (levels 3, 4, 5 still do). You can then switch between runlevels if you like with 
**sudo init 3**
and back to 2 with sudo init 2.

When I logged in as root in recovery mode, I was logged in at runlevel 1, according to the NVidia Driver installer. In an effort to follow the above instructions, I discovered my Ubuntu Gutsy Gibbons install doesn't **_have_** a S30gdm file in the /etc/rc2.d/ folder. It has a S13gdm file, but no S30"anything". Deleting this didn't affect my runlevels any.

I've gone back and forth on this thread, and I'm more confused than ever. I don't want to permanently boot to VGA console, just temporarily whilst getting this driver installed. Are there some simple instructions for noobs like me on how to keep the GUI from loading automatically when I issue a telinit 3?

---

### Post by Robert Citek on 2008-03-26
> **Robynsveil said:**
> I've gone back and forth on this thread, and I'm more confused than ever. I don't want to permanently boot to VGA console, just temporarily whilst getting this driver installed. Are there some simple instructions for noobs like me on how to keep the GUI from loading automatically when I issue a telinit 3?

Do you have a link to the installation instructions you are following?

From what you describe it sounds like the installation instructions are for a Red Hat-based distro.

I suspect that all you need to do is the following:

1) logout from your X11 session
2) switch to a virtual terminal (Ctrl+Alt+F1)
3) login
4) run "sudo /etc/init.d/gdm stop", instead of "telinit 3", to stop your X11 server
5) install your drivers
6) run "sudo /etc/init.d/gdm start", instead of "telinit 5", to restart your X11 server

As for documents on runlevels, I have not found any place that does a really good job of explaining them, although Wikipedia is as good a place as any to start:

[http://en.wikipedia.org/wiki/Init](http://en.wikipedia.org/wiki/Init)

Be sure to let us know how things go.

Regards,
- Robert

---

