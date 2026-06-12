---
title: "Damnit, Windows!"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by PietreWitobi on 2006-09-19
So I installed Windows Vista to my Windows partition.  Went Swimmingly.  Installed, it's very pretty, but not very effective.  So I say "Hey, Why don't I switch to Ubuntu, and check to see if it still mounts the drive alright?"  Then I restart the computer, and wait for the menu to come up so I can choose - Boot to Ubuntu...

BUT IT NEVER COMES!!!

I have completely reversed the boot order, and it still boots to Windows.  WTF?  I'm so damn confused.  Any help?

---

### Post by Sonic Alpha on 2006-09-19
You installed Vista after you installed Ubuntu, right?

That was the wrong thing to do, it's always best to install Ubuntu after Windows if you plan to dual boot.

However, I believe you may be able to restore the grub loader.  I just don't know how :/

---

### Post by D10 on 2006-09-19
Windows will rewrite the MBR when you install it. You will have to reinstall GRUB.

See if this will help.

[http://www.ubuntuforums.org/archive/index.php/t-22537.html](http://www.ubuntuforums.org/archive/index.php/t-22537.html)

---

### Post by skymt on 2006-09-19
Windows overwrites your MBR. You need to [reinstall grub](http://www.ubuntuforums.org/showthread.php?t=224351).

---

### Post by ignorance on 2006-09-19
Simpel rule first install linux than windows, just for the simpel reason that if when you install windows after linux i would mess up the boot-loader of linux and making it impossible to boot linux.

Btw this is what i heard, never tried it. Installed linux last year and 3 months later windows was switched by debian.

Don't know any other solution than to make back-ups and install ubuntu again.

---

### Post by Brunellus on 2006-09-19
> **ignorance said:**
> Simpel rule first install linux than windows, just for the simpel reason that if when you install windows after linux i would mess up the boot-loader of linux and making it impossible to boot linux.

Btw this is what i heard, never tried it. Installed linux last year and 3 months later windows was switched by debian.

Don't know any other solution than to make back-ups and install ubuntu again.
reversed.  Install WINDOWS FIRST, and then linux:  that enables you to use the superior GRUB bootloader without worrying that it will be trashed by windows.

---

### Post by Sef on 2006-09-19
[Restoring GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") from Ubuntu Documentation.

---

### Post by arkangel on 2006-09-19
I really hate  this Microsoft policy.  I wish you good luck
that happened to me 3 times. twice i could re-install grub  the last time after asking support from microsoft (just spam and stupid  replies  that repeated my email just to confirm and a 30-min useless phone call)and reading all what my God Google told me to do , I just  gave up and erased  Windows forever.

Grub  can boot almost all OS known  by the Human being  and they have to do it    in the  hard  way  
I share your  sorrow

Edit: I was reading the link posted by Sef and there are some things  I didnt try ,  It would be worth to give it a shot before thinking in reinstalling again ,  I like ubuntu for its community :KS

---

### Post by Mime on 2006-09-19
Been there... had windows munge my MBR... said a few words I'd rather not repeat here(ok, maybe more than a few), then got out my LiveCD I keep around just for times like this and started fixing things.

Didn't know for a fact that Vista did this as well, but I can't say that I'm surprised.:neutral:

---

### Post by Frak on 2006-09-19
I've heard, DON'T SLEEP ON IT, that Vista has a bug that "supposedly" keeps all other OS's from booting, not just linux.

---

### Post by jISh on 2006-09-19
> **Frak said:**
> I've heard, DON'T SLEEP ON IT, that Vista has a bug that "supposedly" keeps all other OS's from booting, not just linux.
That's nonsense. If your MBR is controlled by anything other than Windows then there is nothing Windows can do about it.

---

### Post by xpod on 2006-09-19
Extra sensory powers.....that "vista" sounds powerful:razz:

---

### Post by Drakkor on 2006-09-19
Fastest way to reinstall grub to the mbr of windows to dual boot
OK,boot to the live Ubuntu CD
Open terminal type
Code:

sudo grub

At the grub>prompt enter these commands
Code:

find /boot/grub/stage1

This will return a location like (hd0,1)
still in terminal type
Code:

root (hd?,?)

use the values from the find command
Next enter the command to install grub to the mbr
Code:

setup (hd0)

Enter
Code:

quit

reboot to the hard drive,and you will be given the grub menu to select what you want to boot Ubuntu is default and XP would be at the bottom,just hold down the down arrow key !

---

### Post by xpod on 2006-09-19
LOL...well seeing you`ve had plenty practise drakkor...[-X :D

---

### Post by Drakkor on 2006-09-19
Yep, I like to break things and then fix them,lol :p 
I alway say: "If it ain't broke...fix it till it is,lol

---

### Post by xpod on 2006-09-19
I prefer.."if it aint broken then im determined to fix it"!!:D

---

### Post by PietreWitobi on 2006-09-20
Haha,

Thanks all, the unofficial "Super Grub Disc" worked beautifully.

And Windows Vista is mostly eyecandy, for the record.

---

