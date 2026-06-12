---
title: "Windows bootloader dual boot: mkdir question"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by zmike1 on 2007-05-08
I've been continuing trying to get windows bootloader to work:

[http://ubuntuforums.org/showthread.php?t=435072](http://ubuntuforums.org/showthread.php?t=435072)

following the directions in :
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

After thinking about the command:
mkdir /mnt/osshare (which I try while using the linux rescue CD)

I wonder, "how does linux know where I am trying to mount the partition or from where I am getting the original file?"  gparted calls the partition "/dev/sda6" and not "osshare" even though I made its mountpoint /osshare when I ran the ubuntu installer

Then, mount the partition:
mount -t msdos /dev/sda6 /mnt/osshare 

so when I use this command:
dd if=/dev/hda5 of=/mnt/osshare/ubuntu.bin bs=512 count=1
I do get a file, but how do I know it's right?

---

### Post by starcraft.man on 2007-05-08
Ummm, this may be a really stupid question... but is there a reason for not using GRUB?

If you want a really easy bootloader, look at [GAG.]("http://gag.sourceforge.net/") I don't really know of any benefit of trying to get windows bootloader... You can just pop it in and it will recognize partitions.

---

### Post by zmike1 on 2007-05-08
The reason is to keep from over-writing the windows MBR (to keep the rest of the system accessible to the people who share the computer.  There is a "quick load" button on the computer to load "media Direct" without having to boot any OS.  Just a nice feature.  Plus I thought I'd learn something about how this linux stuff works.

---

### Post by starcraft.man on 2007-05-08
> **zmike1 said:**
> The reason is to keep from over-writing the windows MBR (to keep the rest of the system accessible to the people who share the computer.  

I don't really understand this... you can always restore the MBR pretty easily with any restore disk or Windows install disk, just pop it in and use the fixmbr command. I don't get how using GRUB "prevents" people from accessing the system, its a simple straightforward selector that lists Ubuntu and XP/Vista at the bottom if detected...

> **zmike1 said:**
> There is a "quick load" button on the computer to load "media Direct" without having to boot any OS. 

Ummmm.... I don't know what this feature is or the benefit... Ubuntu boots in 20-30 (I boot under 20) seconds on most PCs, and if your going to sit down to watch a "media" I assume movie... you have hours.

> **zmike1 said:**
> Plus I thought I'd learn something about how this linux stuff works.

Far as I know, no Linux developper ever coded anything in the windows bootloader. Nor is there any connection with Ubuntu/Linux.

---

### Post by zmike1 on 2007-05-08
> **starcraft.man said:**
> I

Ummmm.... I don't know what this feature is or the benefit... Ubuntu boots in 20-30 (I boot under 20) seconds on most PCs, and if your going to sit down to watch a "media" I assume movie... you have hours.

Far as I know, no Linux developper ever coded anything in the windows bootloader. Nor is there any connection with Ubuntu/Linux.

I appreciate your POV; however, I'm not the only one who uses the computer.  There is another user who "must" have the button.  It's not for speed, rather convenience.  You're right to say it's only 20 seconds, but I have yet been able to make a convincing case that life isn't really more difficult to look at the screen and make a selection.  but that's not a software issue - it's a user issue.

Also, my reasoning is more a matter of My understanding and the principle:   If I can't go online and find a well written "How To" guide (which i did) and follow the instructions (which I did) and get the desired result (nope), maybe Unbuntu just isn't for me.

I don't blame the ubuntu/linux developers, actually I admire their ability to use creative solutions and community efforts to develop what sounds like a good piece(s) of software.  I merely want to get this to work in a way I understand.  
GAG may be an option, so, thank you for the suggestion.  

I don't want to give up yet.  I'd like to understand how dd works and how mkdir works...

---

### Post by starcraft.man on 2007-05-08
> **zmike1 said:**
> 
Also, my reasoning is more a matter of My understanding and the principle:   If I can't go online and find a well written "How To" guide (which i did) and follow the instructions (which I did) and get the desired result (nope), maybe Unbuntu just isn't for me.

Just to point out... Ubuntu is designed to boot with GRUB and LILO. All the other Bootloaders are designed like GAG to detect and boot any existing OS. As far as I know, Microsoft has made no attempts to smooth dualbooting with Ubuntu or any other OS, ever... I also assume your using the XP bootloader, which for all intents and purpose is a really dumb one. Thus, I really don't see how Ubuntu can be responsible  in any way for you following a guide to "hack" the windows MBR to work with Ubuntu. Thats microsoft's product and its in their interest to make it as hard as possible (if not impossible) to lock you into Windows.

> **zmike1 said:**
> 
I don't blame the ubuntu/linux developers, actually I admire their ability to use creative solutions and community efforts to develop what sounds like a good piece(s) of software.  I merely want to get this to work in a way I understand.  
GAG may be an option, so, thank you for the suggestion.  

I don't want to give up yet.  I'd like to understand how dd works and how mkdir works...

I don't really see how using GRUB prvents you from understanding how you got this to work... [heres]("http://www.gnu.org/software/grub/manual/grub.html") the grub manual if you really wanna learn.

Anyway, knock yourself out with GAG... I just don't seem to understand why one would actively avoid GRUB, its a good bootloader.

---

### Post by zmike1 on 2007-05-08
> **starcraft.man said:**
> Just to point out... Ubuntu is designed to boot with GRUB and LILO.
...I also assume your using the XP bootloader, which for all intents and purpose is a really dumb one. Thus, I really don't see how Ubuntu can be responsible  in any way for you following a guide to "hack" the windows MBR to work with Ubuntu. Thats microsoft's product and its in their interest to make it as hard as possible (if not impossible) to lock you into Windows.
Anyway, knock yourself out with GAG... I just don't seem to understand why one would actively avoid GRUB, its a good bootloader.

Thanks again for the reply.  I understand that ubuntu is supposed to boot with a linux bootloader; and I understand that the XP bootloader is "dumb"  (maybe that's why I can understand it...) :-)
I'm not trying to avoid GRUB necessarily, I was just trying to get Ubuntu to load without overwriting my existing MBR.  I thought I'd found a way... it seems that someone else did.

I guess things aren't as flexible and configurable as I hoped.  Maybe I just need to climb further up the learning curve.

---

### Post by starcraft.man on 2007-05-08
> **zmike1 said:**
> Thanks again for the reply.  I understand that ubuntu is supposed to boot with a linux bootloader; and I understand that the XP bootloader is "dumb"  (maybe that's why I can understand it...) :-)
I'm not trying to avoid GRUB necessarily, I was just trying to get Ubuntu to load without overwriting my existing MBR.  I thought I'd found a way... it seems that someone else did.

I guess things aren't as flexible and configurable as I hoped.  Maybe I just need to climb further up the learning curve.

Just a note, but I do want to make sure ya know, I wasn't inferring you were dumb, its a fact that the XP bootloader is well stupid... can't find XP if its not on c for instance >.> Comparing that to GAG which can practically detect any OS anywhere on drive...

Just a thought, but if you want to make sure you never lose your MBR forever... you can always use a disk imager, they usually let ya back up the MBR with any partition. Free ones, [here.]("http://linuxappfinder.com/backupandrecovery/driveimaging")  

Anyway, have fun, I'm off for the night.

---

### Post by zmike1 on 2007-05-08
> **starcraft.man said:**
> Just a note, but I do want to make sure ya know, I wasn't inferring you were dumb, its a fact that the XP bootloader is well stupid... can't find XP if its not on c for instance >.> Comparing that to GAG which can practically detect any OS anywhere on drive...

Just a thought, but if you want to make sure you never lose your MBR forever... you can always use a disk imager, they usually let ya back up the MBR with any partition. Free ones, [here.]("http://linuxappfinder.com/backupandrecovery/driveimaging")  

Anyway, have fun, I'm off for the night.

Thanks.  No offense taken.  I didn't think you were implying that I was dumb (though perhaps banging my head against this "problem" may not have been the best use of my time).

When you said that I was really trying to "hack" the windows bootloader and make it do something it doesn't (necessarily) want to do, the light came on.  
I'll try GAG... or I'll just use GRUB 'cuz I know that will work if I'm willing to sacrifice the dubious convenience button and deal with the disgruntled user (aka, "wife").

---

