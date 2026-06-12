---
title: "Booting install CD from firewire CD drive"
date: 2006-12-17
forum: Apple PPC Users
---

### Post by stella on 2006-12-17
Hi everyone. I'm trying to install Ubuntu on my eMac using an external firewire CD drive (internal one is broken), but I can't boot from the CD. Neither holding down c or holding down option and selecting the CD works. I know I *can* boot from this drive because I've used it with OS X install CDs, so I don't understand why it won't work with Ubuntu? Does anyone know how I can get this working? Thanks!

---

### Post by stella on 2006-12-18
Okay, so I've been looking around some more and it appears that I'll have to do this netboot thing, but I'm completely confused about it. I'm very willing to learn how to do this stuff, but there doesn't seem to be a good starting point. My only other computer is a WinXP PC, and I can't find any info about netbooting between a Mac and XP. Isn't there some site that just explains how to netboot? I really want to get this running, and I appreciate *any* help!

---

### Post by Tait on 2006-12-19
It's possible, thats how I installed it on my box.  It's all thanks to the magic of open firmware.

FIrst, boot into open firmware by holding down comand-option-o-f while booting.  you'll get a small font console.  That's the open firmware console.  then find the firewire drive.  you can type 'dev / ls' to see a list of all of the devices, but it should be aliased as fw, so you can just type 'dev fw ls'.    you'll get something like this:

ff9dc350:   /node@00063a2751
ff9dc548:      /sbp-2@4008
ff9dc790:         /disk@0

this is the path to the disk.  you only need the @number if there are more than one devices with that name.  you can boot by typing the path to the disk, followed by a ':', followed by the partition number (which you leave blank in this case) followed by a ',', and followed by the path to the boot image using backslash \ as the divider.  To boot on my box, I used:

boot fw/node/sbp-2/disk:,\install\yaboot

and that brought it right up.  

Good luck and happy geeking.

---

### Post by stella on 2006-12-19
You are my new hero. ;) Thanks so much!

I've run into another problem though. It looked like the installer would start, but there was an X server error, here's what it said: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" I copied down that output too if anyone needs to see it. Then it said: "The X server is now disabled. Restart GDM when it is configured correctly."

I don't know what GDM is, but after I hit enter, it took me back to a black screen with a blinking cursor. I had to quit there because I didn't know what to type to install Ubuntu. Anyone who can help me out (again)?

---

### Post by stella on 2006-12-19
There might be something wrong with the CD I use trying to use, because I burnt the alternate version at a slower speed (4x) and I got past that issue. And yes, now I've run into something else.

I got as far as the keyboard configuration with no problems. Then I got this error message about my CD-ROM not being able to be mounted, but it gave me the option to continue anyway, it takes me to an Ubuntu installation menu and I went through a few more steps with that CD-ROM mount thing happening between each step. Then my last option on the menu, before aborting the installation, is "Execute a shell", so that's what I did. It took me to this "ash" shell, and now I have no idea where to go from there.

(Should I just start a new, generic installations problem thread? :???: )

Edit: It says if I abort the installation now, my computer could be left in an unusable state, so I'd really appreciate any help to take my computer out of installation limbo :)

---

### Post by Tait on 2006-12-20
Next time try booting 'linux video=ofonly'.  This uses the most basic  drivers available.  

gdm stands for gnome display manager, and runs things like logging in and choosing the session you use.  It's also how X is started and stopped.  To start gdm, type /etc/init.d/gdm start.  That might get you an X environment.

---

### Post by stella on 2006-12-20
Well, that got me a little farther. After the Ubuntu loading screen, where I'd normally get the X server error, I heard what I assume is Ubuntu's start-up sound; drum music and a few bird chirps. After that...nothing, just a black screen with nothing on it, not even a blinking cursor. ](*,) So, again, if anyone has any ideas, I'd be glad to hear them...

Thanks for your help so far.

---

### Post by stream303 on 2006-12-20
A little bit further each time....  it looks like you'll have to modify your /etc/X11/xorg.conf file on that eMac.

Try this thread, or search for more eMac related threads:

[http://www.ubuntuforums.com/showthread.php?t=246129&highlight=emac](http://www.ubuntuforums.com/showthread.php?t=246129&highlight=emac)

---

### Post by stella on 2006-12-20
Thanks to stream303's link, I got the Live CD to run, and I started the installation. I'm at the partitioning my hard drive part (changed the partitions manually with the utility on the Live CD) and got this message after I finished changing the partitions:

"No NewWorld boot partition was found. The yaboot loader requires an Apple_Bootstrap partition of at least 819200 bytes in size, using the HFS Mactintosh file system."

I did a quick search, and from what I found, I have to use the alternate install CD to make this Apple_Bootstrap partition? Except...as I posted above...trying to use *that* CD gave me a whole new problem that I couldn't seem to get past. Am I really stuck again?? I was so close. :(

---

### Post by stella on 2006-12-21
Update: I just went ahead with the first option on the installer, to erase the entire disk, and let the installer figure out whatever it needed to do. So now I'm on Ubuntu! :D Thanks so much to Tait and stream303 for your help. :)

---

### Post by stream303 on 2006-12-21
You just exposed a really cool workaround for getting an external firewire to boot!

While you can install Ubuntu / Debian etc onto an external firewire drive, yaboot has problems making the firewire drive bootable and seems to only pick up the openfirmware paths of the internal drive.

But now with your internal drive not working, of course yaboot has no problem. :)

I had to go to some length to get my external firewire drive bootable by hand-editing the yaboot.conf file, moving it to the internal drive, running ybin from the internally-booted system - what a pita - but it worked.

Far simpler would have been to temporarily disconnect the internal drive, run the installer as normal for the firewire drive, and then reconnect the internal hd.

Cool - thanks for *your* help!  That's a quick fix for those with dead internal hd's.

---

### Post by stella on 2006-12-21
But...my internal drive *does* work? It was my internal CD drive that didn't work. But if I did somehow expose a helpful workaround, then you're quite welcome. :p

---

### Post by stream303 on 2006-12-22
Um, too much caffeine to start my day. :)

So what do you have running on your internal hd - OSX?  Reason I ask is that I could not get Ubuntu nor Debian make my firewire bootable even though they would finish the install. (until I manually found out the openfirmware paths and rewrote the yaboot.conf file myself)

(Ubuntu would notify me, whereas Debian would just blast through to the end without writing yaboot.conf properly.)

I'm puzzled (but glad) as to why it doesn't work for me, but it did for you..

---

### Post by stella on 2006-12-22
I think we're mixed up again. :p I didn't use a firewire hard drive, I used a firewire CD drive to install Ubuntu. I had OS X running on my HD, but I was having partition problems so I just wiped the drive and installed Ubuntu, so for now Ubuntu is the only OS installed on my HD. :)

---

### Post by stream303 on 2006-12-22
You're good, it's me thats all confused.  Wow.  Where's the decaf?  :)

---

