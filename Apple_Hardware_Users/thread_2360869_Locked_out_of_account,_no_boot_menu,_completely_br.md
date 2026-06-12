---
title: "Locked out of account, no boot menu, completely bricked?"
date: 2017-05-09
forum: Apple Hardware Users
---

### Post by architecteight on 2017-05-09
Hello Ubuntu community, 

I've run into a bit of a problem after installing Ubuntu, the password created at start for the admin/root password is incorrect and not knowing the password of the user account has me locked out of changing anything on the computer completely (keeps asking to authenticate things with the password I don't know). I also can't access bios/boot menu or anything like that. 

Ubuntu is installed on a slightly older MacBook Pro 2002 era and none of the boot up commands work for either Ubuntu or the Mac OS. At start up there is a flash of the Grey Macbook Pro OS then immediately the Ubuntu purple, there is no logo, and then it is loaded up completely with the default user account. 

Is my computer completely bricked? I'd like to reinstall with a different username/password or none at all if possible, because this is really nuts. I've never not been able to just wipe a computer clean with a new OS until I put Ubuntu on here, send help!

---

### Post by RobGoss on 2017-05-09
What brand of computer is this is it a Mac?

---

### Post by architecteight on 2017-05-09
Yes sir, MacBook.

---

### Post by oldfred on 2017-05-09
You have to type the password in twice when you install.
So it cannot be incorrect.

       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

And you need sudo with password to do anything administrative.

       
 Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by slickymaster on 2017-05-09
*Thread moved to **Apple Hardware Users**.*

---

### Post by architecteight on 2017-05-09
Yes, but none of this will work because - I can't boot! There is no way to access boot menu or bios or this issue would've been easily solvable. I shut down and restart and the screen is purple for a moment, no logo or anything, none of the boot keys work, holding/pressing does nothing - then we are at the desktop. There are no prompts, no grub, nothing.

---

### Post by RobGoss on 2017-05-09
If this is a new installation it's kind of hard to not be able to access the desktop, if the passwords were incorrect it would have told you before the installation started

---

### Post by architecteight on 2017-05-09
I can get to the desktop fine, i just can't do anything else - I need the password to do any admin things and I just want to reinstall but I can't access the bios or the boot menu. Idk what the passwords could be because none of them work. There is also no way to find them out and no way to reset them without the bios or boot (according to the internets) so I am stuck? Bricked macbook?

---

### Post by RobGoss on 2017-05-09
I don't know much about Mac but I do know the password you create for your installation has nothing to do with accessing your BIOS

---

### Post by architecteight on 2017-05-09
Okay, I just can't figure out any of the passwords for anything and I can't access the bios, its just a Ubuntu computer with a few apps on it right now.

---

### Post by RobGoss on 2017-05-09
Did you try reinstalling Ubuntu and start fresh? At this point that would be a better option

---

### Post by architecteight on 2017-05-09
That is exactly what I want to do, I can't! I can't get it to boot up on USB or disc, i can't access the boot menu or the bios, there is no way to reinstall and start fresh. It just starts up and goes immediately to the desktop - that is the entire problem I'm having right now and it is driving me nuts haha.

---

### Post by oldfred on 2017-05-09
Do not know Mac.
But how did you get into its EFI originally. 
Did you install in UEFI or BIOS boot mode?

Often if system has issues getting into BIOS/UEFI, you can cold boot, not warm reboot. Or fully power down, if laptop remove battery and remove power cord and hold power switch to drain all residual power. Then boot and press correct key(s) for UEFI/BIOS.

Some systems have jumpers on motherboard to totally reset. That will also reset any changes you made to UEFI/BIOS back to defaults, so you have to reset them. And then you should be able to cold boot.

---

### Post by RobGoss on 2017-05-09
>  Some systems have jumpers on motherboard to totally reset. That will also reset any changes you made to UEFI/BIOS back to defaults, so you have to reset them. And then you should be able to cold boo 

Oldfred is correct, I just had this issue a few days ago I just removed battery from one of my Dells and bingo, easy access. Some machine as Fred stated have jumpers and need to be removed

---

