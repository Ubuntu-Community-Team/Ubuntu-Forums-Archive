---
title: "No Boot! No Apps! Please Help!"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by pushprocess on 2007-01-14
Installed ubuntu 6.10 ok! But can only boot from cd! I have ubuntu intailed it  on a slave hard drive & when the computer trys to boot it says No operating system installed! At the setup it ask me if i want to have a boot manager i think it grubI have to keep win XP on the main hard drive for the family, But i hate it & real want to use ubuntu! I boot it up from the cd & try and get to my boot manager and other apps but cant! Have tried everything! But cant seem to get anywhere! Have tried to change files! Have tried to run them but no good! If i could get things to run i think i will be fine! It says i am the admin but there is no system tools or boot manager or anything! I am new at Linux but know windows! Please someone help as i am at a point were i will have to go back to working with Bill!

---

### Post by rai4shu2 on 2007-01-14
When you have multiple hard drives, it's can difficult for the installer to know which one to put grub onto. For now, you might try switching which drive gets booted by the BIOS if you can find a BIOS boot menu or a BIOS setup option for that.

---

### Post by Sef on 2007-01-14
Can you boot into Windows?

---

### Post by pushprocess on 2007-01-14
Someone Please Help!

Please!

---

### Post by pushprocess on 2007-01-14
> **rai4shu2 said:**
> When you have multiple hard drives, it's can difficult for the installer to know which one to put grub onto. For now, you might try switching which drive gets booted by the BIOS if you can find a BIOS boot menu or a BIOS setup option for that.

I have done that! No Good!

Tryed Them All!

---

### Post by pushprocess on 2007-01-14
> **Sef said:**
> Can you boot into Windows?

Only If i put the ubuntu cd in and go to Boot from first hard drive!

---

### Post by rai4shu2 on 2007-01-14
Are you absolutely positive you are setting up your BIOS correctly? This sounds to me like you're leaving the CD and/or the floppy first in the boot order.

---

### Post by pushprocess on 2007-01-14
> **rai4shu2 said:**
> Are you absolutely positive you are setting up your BIOS correctly? This sounds to me like you're leaving the CD and/or the floppy first in the boot order.

No! I am taking the cd out!!! I Am getting into the Bios And changeling thing ! I know how to do that!!! Still no boot!

But how do i get into the Apps? Like Boot Manager and Grub? I Evan tried to get Lilo! I downloaded it but how can i find it! Have tried to run them all! HELP!!!

---

### Post by Sef on 2007-01-14
Sounds like a bad install, so a few questions for you:

1) Did you md5sum the download?

2) Did you burn it at 4x or less?

3) Are there any problems running the live cd?

---

### Post by ajgreeny on 2007-01-14
Boot into the ubuntu live CD and then run gparted (Gnome partition manager).  Let us know what partitions the program finds and on which disk(s).  We may then be able to help out.

You could also try the following, but if you get any error messages come back and ask again:-

Boot into the ubuntu live CD
open a terminal and run :
*sudo grub*
This gets you to a simple grub command line.
Then:
*find /boot/grub/stage1*
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu.  Replace the question marks in the following command with the output of the this last command :
*root (hd?,?)*
[like : *root (hdo,1)* ,probably]
then:
[I]setup (hd0)
[/I]This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate.  It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
*quit*
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by pushprocess on 2007-01-14
> **Sef said:**
> Sounds like a bad install, so a few questions for you:

1) Did you md5sum the download?

2) Did you burn it at 4x or less?

3) Are there any problems running the live cd?

1/ DoNot Know What This Is! (Sorry Real n00b)

2/ I Burnt The Cd At The Slowest Speed I Could! Which I Think Was 8x! Could Not Get It Slow With Nero!

3/No! I have No Probs With Live cd!

Thanks For Your Help! Hope I Get Somewhere! Bill Sucks!

---

### Post by pushprocess on 2007-01-14
> **ajgreeny said:**
> Boot into the ubuntu live CD and then run gparted (Gnome partition manager).  Let us know what partitions the program finds and on which disk(s).  We may then be able to help out.

You could also try the following, but if you get any error messages come back and ask again:-

Boot into the ubuntu live CD
open a terminal and run :
*sudo grub*
This gets you to a simple grub command line.
Then:
*find /boot/grub/stage1*
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu.  Replace the question marks in the following command with the output of the this last command :
*root (hd?,?)*
[like : *root (hdo,1)* ,probably]
then:
[I]setup (hd0)
[/I]This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate.  It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
*quit*
Finally reboot, and hopefully you will now have a working grub bootloader.

Oooo! Heavy! I Will Try!

Will Get Back To You A Little Later! Working On DIYing The Bathroom At Moment!

Please Stick By This One! Really Want This To Work!

Many Thanks!

Push (-_-)

---

