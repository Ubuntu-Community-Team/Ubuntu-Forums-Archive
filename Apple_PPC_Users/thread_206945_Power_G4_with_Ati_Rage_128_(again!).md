---
title: "Power G4 with Ati Rage 128 (again!)"
date: 2006-06-30
forum: Apple PPC Users
---

### Post by ZekeG4 on 2006-06-30
I know this problem has been here before, but all the threads that talk about this issue are incomplete and don't post any solution. I have a powerG4 400 MHz with an Ati Rage 128... this computer:

[http://www.lowendmac.com/ppc/g4.shtml]("http://www.lowendmac.com/ppc/g4.shtml")

My problem, and one that has been here forever, is I can't manage to load X. I've tried editing the xorg.conf file (changing the refresh rate, I have a 17inch Apple Studio Display, turning on/off dri, and a couple of other solutions posted online), but I can't manage to fix the problem.

I load the live cd, and and can only load up with "live video=ofonly" option, then ubuntu starts loading. I get the splash screen and the loading but after a while an x error.

I was wondering what to do to fix this problem.

Thanks!

---

### Post by trash on 2006-07-05
nightmare indeed! I have finally replaced my 16" studio display(fixed resolution 832x624) with a nice 17"@view... G4, 466 here but I am sorry I don't have a concrete solution for you. I was never able to get a livecd to work with the studio display, i did report it as a bug a while back but nothing came of it.
From what i remember, video=atyfb:vmode:13,cmode:16 3 was a boot option I used. xorg had to have the horiz and vert refresh rates and depth had to be 16 not 24.
As nice as studio display is i am so happy to be rid of it!

---

### Post by ZekeG4 on 2006-07-05
Well, discarding the live cd, did you manage to install it?

---

### Post by trash on 2006-07-05
yup. what errors are you getting?

---

### Post by ZekeG4 on 2006-07-05
I see the splash screen and it starts loading stuff, but then crashes to a blue screen with a XServer error. Do you want the error?

Another thing, do you think I would have the problem if I just went ahear and installed it? (I would have to go ahead and download an install cd, wouldn't I?)

---

### Post by trash on 2006-07-05
nope go for it, the card itself is well detected, i think it is that screen that is giving you troubles... is it a fixed resolusion? Though you may want/need to install in text mode.

---

### Post by ZekeG4 on 2006-07-05
Thanks! I'll give it a try and let you know. ;) 

Though it'll have to be tomorrow. (it's 2:20am over here)

---

### Post by trash on 2006-07-05
cool, btw you may prefer running Xubuntu it's a bit peppier on my G4 than Gnome. I did a quick check for your monitor but didn't find it.. check here to make sure your refresh rates are good... [http://monitorworld.com/Monitors/apple/](http://monitorworld.com/Monitors/apple/)

good luck:)

---

### Post by Jason C. on 2006-07-05
Hi Zeke,

I have a Mac G4 Cube at home with the Rage128 card and an Apple Studio Display.  I ran into the same problems you are hitting when trying the liveCD and the installation (these are documented at cubuntu.blogspot.com).

To begin, by passing in the "video=ofonly" argument, you will use only the open firmware video output (this is my very basic understanding of this argument); importantly, this means that X will not work.  Try passing "live video=aty128fb" to the liveCD bootloader.  If this doesn't work, then the only course I know of is to install using the "video=ofonly" argument and then adjust your yaboot configuration after the installation (I discuss these at cubuntu.blogspot.com).

Good luck.

P.S. Please post if the video=aty128fb argument works with the liveCD.

---

### Post by ZekeG4 on 2006-07-05
Ok, I tried the boot option on the live cd and it didn't work. I just installed Xubuntu with the hope that I could fix the problem by defining the refreash rate but it didn't work.

Did you try the boot option on the live cd or on your install? This is my first Linux install, I've played with solaris and linux but only as a user. How do you edit the boot options on the installation?

Thanks for your help, this is pretty fun. :)

---

### Post by ZekeG4 on 2006-07-06
Ok, here's the latest update. I tried the "procedure" on your page, about changing video=ofonly to video=aty128fb in the yaboof.conf file. I then ran ybin and rebooted. Doom! Now I cant see a thing! And to make matters worse, I have a blank screen and have no idea how to fix yaboot to return to "normal". 

Any ideas? I wouldn't mind a reintall that much, since I havn't done anything yet, so it wouldn't be the end of the world. But that wouldn't fix the overall problem. I beginning to think that OS X is the only solution :(  ...

Thanks for all your help guys.

---

### Post by Jason C. on 2006-07-06
Hi Zeke,

Well that is disappointing.  I am now at home, working on my Cube so perhaps I can be of more assistance.  You should not need to reinstall.  If you have the liveCD available, you can boot from that passing the "video=ofonly" argument and then edit yaboot.conf and run ybin.  You will probably have to mount the root partition of your hard drive once the cd boots up.  I think this should work, I will try it right now with my Cube.

I also had a look at my yaboot.conf file; here it is:

## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda9
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=11
root=/dev/hda11
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda16

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash video=aty128fb:1280X1024-24@60"

image=/boot/vmlinux
        label=old
        read-only
        initrd=/boot/initrd.img
        append="quiet splash video=ofonly"


Note that the video=aty128fb also has the screen resolution (1280x1024) the color bit level (24) and the refresh rate included (60).  Perhaps these will make the difference; I apologize as I clearly forgot that these need(?) to be included.  The second entry, and I should have mentioned this earlier as well, boots with the "video=ofonly" argument (everything else but the label is the same).  That way if something goes wrong, I can always boot into the ofonly video by using the "old" command at startup.

---

### Post by Jason C. on 2006-07-06
Update:

I was able to successfully boot the liveCD using the "video=ofonly" option.  Once at the CLI, I mounted the hard drive using the mount command, and then was able to edit yaboot.conf.  I then tried running the ybin command (in this case you will have to give the full path, i.e. /directoryWhereYouMountedTheHardDrive/usr/sbin/ybin and you will have to pass the location of the yaboot.conf file) and it went through the motions of working (I did not use sudo, so it did not actually do anything to my bootloader).

I should also mention that in the above post, I gave the specs for my 15" studio display.  Your 17" will be different.  You should be able to find this info on Apple's website.

Good Luck and I will keep my eye on this thread should you need more help.

---

### Post by Jason C. on 2006-07-06
Okay, another update.

This thread inspired me to begin playing around with my yaboot file a bit (probably not the smartest thing to do, but hey its fun).  So I just went into yaboot.conf and set up a third label; in this case I completely deleted the video argument (it looks like this):

image=/boot/vmlinux
        label=test
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

I ran ybin -v and rebooted.  After telling the bootloader that I want linux (my first screen is to choose between linux, macosx and a cd boot so I type "l"), i then typed "test" to test this new configuration.  I am now writing this message from Firefox after booting (i.e. X works after removing the video= option).  This now leads me to believe that the kernel on the liveCD is missing the appropriate driver to run the Rage 128 Pro Card with the Studio Display, but this driver is included upon installation(? just a guess).  Thus, I would suggest giving this a shot before you try the aty128fb argument again.

---

### Post by avtolle on 2006-07-06
I have a cube also with the same video card and 15" display. I did a dist-upgrade from Breezy and not a clean install of Dapper, thus not exposing mself to the "live CD". I did not have the problems of the OP, and video has run (and contines to run) "fine". This leads me to support Jason's hypothesis concerning the kernel; I seem to recall some early discussion that the kernel on the live cd had been upgraded on the install cd. Clearly, the kernel that was installed by the dist-upgrade had the appropriate driver. A long winded way to say, do an install; I think it will resolve the video issues for you.:)

---

### Post by ZekeG4 on 2006-07-06
Okay! I will try it without the video= option. First step though, is to get th CLI so I can see it.

I'll let you know how it went. :)

Thanks!

---

### Post by Jason C. on 2006-07-06
Good luck Zeke.  Hopefully you won't have to do a clean install, but this may be the best option if trying to edit yaboot.conf gets too hairy.

Interesting idea about the kernel, although I am still a bit dumbfounded as to why the liveCD would not include this driver; the Rage 128 card is found in plenty of Macs.

I will again mention that I booted the installer with the "video=ofonly" option and this was added to my yaboot.conf by the installer (also not clear why this is done).  So after installation, you will likely have to remove this from the yaboot.conf if you install in the same manner (it took me two days to realize this).

---

### Post by ZekeG4 on 2006-07-06
Ok... the update.

I learned to fix the yaboot.conf. Pretty simple. Just boot the live cd, mount the ubuntu partition, edit the yaboot.conf file and run ybin -v -C yaboot.conf (-v for verbose, -C to use a conf file made by me).

After the happiness that learing to use mount, ybin and the yaboot.conf fiile gives you, I started trying different boot options. Up til no I've tried:

  booting with no "video= " option ... [fail]

  booting with the "video=aty128fb:1024x768-24@60" ...[fail]
  booting with the "video=aty128fb:1024x768-16@60" ...[fail]

these settings (for the monitor) are suppossed to be correct acording to the users manual.
[http://manuals.info.apple.com/en/StudioDisplay_17inchCRTUserManual.PDF]("http://manuals.info.apple.com/en/StudioDisplay_17inchCRTUserManual.PDF").

Anyway, I'll keep at it tomorrow. By the way, I AM working off of an install CD, the xubuntu install cd, not off a LiveCD. I'm only using the live cd to fix stuff when all hell breaks loose. :)

Is their a posibility that the xubuntu install cd is bad? That I would have to install ubuntu from an ubuntu install cd and then xfce? I really doubt it, but who knows. Maybe as a last resort.

---

### Post by Jason C. on 2006-07-07
Well, again, that sucks.  :confused: 

Glad you have become comfortable with booting off the liveCD and editing the yaboot.conf file, etc.

I just measured my monitor and apparently it is 17" (ah, the details are killing me here; sorry, this is the first time I have tried to help someone debug, so I am learning plenty).  You could try the specs I originally proposed, but if those were going to work I would expect the no video option to work.  I am using the standard Ubuntu distro, not the xfce distro.  So maybe that may be the difference, but now I am just guessing.

I just followed the link you posted and that is for the 17" CRT.  Do you have a CRT or the flat panel LCD (I have the flat panel LCD)?  If you have the flat panel, the specs I posted are probably more accurate.

I think the next step is to check your xorg.0.log file.  This is in the /var/log directory.  I would suggest you look it over and also possibly post it here.  Another file to check would be the kern.log (also in the /var/log directory); this (the kern.log) will verify that when you boot appropriate options are being passed in.

---

### Post by ZekeG4 on 2006-07-27
Ok guys. Sorry for disapearing but I had a few family things that I had to go to.

I think I have narrowed my problem to ubuntu hating my monitor. I think the problem has to be somewhere in the xorg.conf file. Why?, you ask.

Today I finally had the idea to hook up another monitor to my computer (stupidly I hadn't done this earlier). I conected my PCs standard vga computer. Of course at first I had no problem but after a nice "dpkg-reconfigure xserver-xorg" I had xubuntu running on my powerg4 on the vga monitor. Excelent! 

So I started editing the xconf file... of course nothing happend, BUT (!) I just noticed something. I started un my computer with no fancy "video=" and my screen went blank. 

The strange and posibly good news is that I left it running like that for a while (I could hear activity in my hard drive) and I got the little xubuntu startup sound. So xubuntu loaded but is giving me a blankk screen. I'm gonna continue playing with the xorg.conf file and see if I can get it to run, but at least the OS is loading up. If you have any ideas I would love to hear them. I've foud a couple of people online who have the same problem, but have yet to find a simple solution.

Thanks, guys, for all your help.

---

### Post by ZekeG4 on 2006-07-28
Things are looking grim. I suspect the problem to be the ADC conection on my monitor, but am not sure. Looking around I'm seeing that a lot of people have this problem... :(

---

### Post by ZekeG4 on 2006-08-01
Final Update!

Recently this was posted on the forum. Aparently the specs we had were wrong (a slight difference in the model number).

[http://www.ubuntuforums.org/showthread.php?t=225897](http://www.ubuntuforums.org/showthread.php?t=225897)

So I finally got Xubuntu to run. Thanks for all your help.

The End.

---

