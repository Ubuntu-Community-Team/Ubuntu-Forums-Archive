---
title: "Can't boot, can't access linux HDD to edit mistakes"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by Wolfi3 on 2006-04-08
Hallo ppl

These forums have been wonderful to me.  After 3 years of wanting I finally got a linux system installed and running with Ubuntu for a whole week!  :mrgreen: 

Installed a ton of sofware, got all kinds of p2p apps up and downloading to the linux drive, great sense of achievment!!  Even installed Nvidia drivers with no apparent change in system performance.

After editing xconfig today to setup dualview with nvidia drivers I wind up being **unable to boot**.  It hangs before desktop and at around the nvidia splash screen.
Here's the rub: if I could just access the xconfig file and revert to a backup everything would be fine, but I can't.

Setup here is XP on hda, Linux on it's own 120GB HDD (hdb), booting direct to hdb via bios selection. [see footnotes]   Lilo is there at startup but actually not actually required - just didnt' get around to removing it.

Here's what I've tried:
1. Boot in recovery mode using breezy install CD, get as far as HDD select screen, it refuses to mount the listed hdb5
2.  Boot from live cd, will not mount/enable hdb5 in disk manager - says "inaccessable"
3.  Boot from live Knoppix cd - reports hdb5 "unrecognized file system"

**Please help me get to edit my xconfig file!**

***Footnotes** *that might help you:
The dedicated linux hdb was originally formatted with qparted under an (abandoned) Mepis install.  There were at least 3 partitions, plus a swap and a  grub mbr on the xp c:/ drive. 

 When I discovered Ubuntu I decided to delete all of Mepis and install Ubuntu on a  clean drive.  Gotta admit, was totally out of my depth at the Ubuntu partion menu options.... though I understood I was doing a full disk format Ubuntu eventually appeared to be installed on hdb5 without a swap that I wanted.  At no time during running the happy Ubuntu install has disk manager ever indicated that *anything* on hdb was mountable/enableable.  Of course, the "file system" worked, programs installed and I could access any file I wanted from within Ubuntu.  I'm confident the HDD itself is still alive and working.

I got rid of the redundant hda mepis grub using xp's recovery console.
The effectively orphaned lilo sits on hdb and is just a pain in the *** doing some tedious bios check or other during bootup.  

I hope this makes sense, I seem to have  gotten rather drunk in despair :(

Thankyou.

---

### Post by htinn on 2006-04-08
I'm having trouble figuring out what you're saying. If you could describe how you installed Ubuntu and what you did specifically that caused a problem, that would be very helpful.

---

### Post by dcstar on 2006-04-08
[QUOTE=Wolfi3]Hallo ppl

These forums have been wonderful to me.  After 3 years of wanting I finally got a linux system installed and running with Ubuntu for a whole week!  :mrgreen: 

Installed a ton of sofware, got all kinds of p2p apps up and downloading to the linux drive, great sense of achievment!!  Even installed Nvidia drivers with no apparent change in system performance.

After editing xconfig today to setup dualview with nvidia drivers I wind up being **unable to boot**.  It hangs before desktop and at around the nvidia splash screen.
.....[/QUOTE]
CTRL-ALT-F1 and log in.

---

### Post by Mustard on 2006-04-08
Did you make a backup copy of your old xorg.conf?

Just a comment on the terminology you are using too.  You are saying that you can't boot, but in fact you are 'booting', because grub has come up and you have booted the kernel from your hard drive.  What you can't do is login at the gnome desktop manager because X is failing to load.  As described above, you should be able to use the ctrl + alt + f1 keys to get to a virtual terminal and from there you can login (ctrl+ alt + f1 or any function key up to f6 should work).  After you login with your user name and password, you can edit the xorg.conf file via the command line.

---

### Post by Wolfi3 on 2006-04-09
[QUOTE=Mustard]Did you make a backup copy of your old xorg.conf?

[/QUOTE]

Yes.  There are several backup versions.  If only I could reach them. ](*,)   This came about through editing xorg.conf to make TV-out  work with the official nvidia driver which had been working just fine on a single CRT monitor.

Sorry for my bad terminology.  Ctrl-Alt-F1 doesn't work.   Here is how it boots:
Lilo loads, does a lengthy Bios check
The system loads up (black screen, white text whizzing by) gets as far as "loading Gnome" then the screen goes completely white and blank (at this stage I normally get a brief Nvidia splash screen) .  There is no prompt and any combination of keys produces no result.

I've rebooted over and over and tried pressing above key combination during the bootup process hoping for a command prompt but nothing appears.

I reiterate: trying to recover using the live CD from the desktop: administration>disk util will not allow me to enable the hdb5 where all my installed files are.  It claims it is an unformatted   drive.  It will enable other disks like windows and a usb external drive.

---

### Post by aktiwers on 2006-04-09
Hi,

Not too long ago I messed up my xorg.conf.
I made a Topic here, and this helped me:

```

sudo dpkg-reconfigure -phigh xserver-xorg
```

This code reset xorg.conf if you forgot to make a backup of it.
Check my topic I made, there a some good suggestions what to do, if this doesnt work.

[http://ubuntuforums.org/showthread.php?t=153201](http://ubuntuforums.org/showthread.php?t=153201)

---

### Post by Wolfi3 on 2006-04-09
Thanks for your response.  Glad to hear it worked for you :) 

However, I still have no way of accessing the HDD that ubuntu is installed on in order to ever gain access to xorg.conf.

I just tried Knoppix live CD again.  hdb5 is there on the desktop but knoppix refuses to mount it: "I could not determine filesystem type and none is specified"

I opened up qtparted to view /dev/hbd:

/dev/hdb1  free,       hidden,  243MB       used=N/A
       hdb2  extended, --        111.52GB   used=N/A
       hdb5  unknown, active,   111.52GB  used=N/A


I totally don't understand partitions and such.  I wondered if the HDD was damaged/dead, but since Ubuntu loads up as far as Gnome it must be alive?

---

### Post by htinn on 2006-04-09
Okay, I'm going to guess that Mepis vs. Ubuntu is the real problem.

Ubuntu kinda leans toward grub, Mepis (I guess) prefers lilo. Maybe your partitions were formatted LVM (which is a bit of a pain to deal with in Ubuntu).

I really hate to say this, but maybe you should just erase the sucker and start over from scratch.

---

### Post by Wolfi3 on 2006-04-09
OK.  I guess what you're saying would explain why it was during the Ubuntu installation that the ubuntu cd's partition tool totally refused to do anything and I think I managed to bypass it in the end.  :-&

---

