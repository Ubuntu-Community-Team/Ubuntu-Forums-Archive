---
title: "oops wiped out OS"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Diamyst on 2007-08-25
This is a perfect example of not paying attention to what you are doing.
I wanted to run LiveCd on the Kids Computer to try Freespire.  It doesn't have the same front page as Ubunto so I hit the wrong button and it wiped out my XP and installed itself onto the puter.  I hated it so put Ubunto on instead figuring I'd test drive Ubuntu before I put it on the laptop.  Anway I did put it on the laptop so now want to put XP back on the other computer except the computer will not pick it up.   It is set to boot from CD but since Ubuntu is on it now it won't pick up the windows disk.   How would I get it to read the CD drive...  actually, when the computer boots the lights flash on the CD before it goes to the hard drive but it isn't picking up the CD.   

Normally I would just say oh well and use Ubuntu but this is the computer that I tutor kids on and I have 120 educational programs that I need to have on it before the 8th of Sept.   

Sorry this is so long.  You guys have been so helpful with other problems I'm hoping someone can tell me what to do with this one.

The computer is an IBM P3 with 512 meg of ram.

---

### Post by Steve1961 on 2007-08-25
You might find that you need to use the live cd to delete your ubuntu partition before the windows installation disk will work.  Can you still boot from the live cd, or is your cd drive refusing to boot full stop?

---

### Post by asmoore82 on 2007-08-25
> **Diamyst said:**
> This is a perfect example of not paying attention to what you are doing.
I wanted to run LiveCd on the Kids Computer to try Freespire.  It doesn't have the same front page as Ubunto so I hit the wrong button and it wiped out my XP and installed itself onto the puter.  I hated it so put Ubunto on instead figuring I'd test drive Ubuntu before I put it on the laptop.  Anway I did put it on the laptop so now want to put XP back on the other computer except the computer will not pick it up.   **It is set to boot from CD but since Ubuntu is on it now it won't pick up the windows disk.**  ...

this is not really possible ...
do you have a windows installation disk or is it just a vendor specific "backup" disc?

---

### Post by southernman on 2007-08-25
> **Diamyst said:**
> This is a perfect example of not paying attention to what you are doing.
I wanted to run LiveCd on the Kids Computer to try Freespire.  It doesn't have the same front page as Ubunto so I hit the wrong button and it wiped out my XP and installed itself onto the puter.  I hated it so put Ubunto on instead figuring I'd test drive Ubuntu before I put it on the laptop.  Anway I did put it on the laptop so now want to put XP back on the other computer except the computer will not pick it up.   It is set to boot from CD but since Ubuntu is on it now it won't pick up the windows disk.   How would I get it to read the CD drive...  actually, when the computer boots the lights flash on the CD before it goes to the hard drive but it isn't picking up the CD.   

Normally I would just say oh well and use Ubuntu but this is the computer that I tutor kids on and I have 120 educational programs that I need to have on it before the 8th of Sept.   

Sorry this is so long.  You guys have been so helpful with other problems I'm hoping someone can tell me what to do with this one.

The computer is an IBM P3 with 512 meg of ram.*stupid humor* It'll take until the 7th of september to get the updates done on XP! ;)

*seriously* Ubuntu wouldn't have modified your bios boot order... not unless you got a bogus disk somehow. Anyway... try these things:

1- boot up the computer and begin punching the delete key (could be F10 - F12 - ESC) to get into the bios. Once in double check the boot order to make sure it's set right. Regardless of the OS you installed if the boot order is set to boot from CD first, then it will boot from the CD. Providing of course you have a windows installation cd in the tray... YOU DO have the cd in the tray, right? ;)

2- double check your ide and power cable to the cd drive. won't hurt to unplug them and reseat them again. also do this for the plugin on the motherboard itself. If you have a spare ide cable may want to replace the old one. If it's bad, the led would still work.

3- double check the windows cd for defects.

---

### Post by kwilliam on 2007-08-25
First of all, did Freespire really wipe out your entire Windows partition with one click?  Ubuntu has an installation wizard that makes you pick your timezone, username, etc, before it actually installs.  You could use the Gnome Partition Manager to see if maybe the Windows partition is still there.

If it really is gone and you need to reinstall XP:  I can't imagine why the Windows disk doesn't boot unless A) the bios actually *isn't* set to boot from CD, B) the CD drive suddenly broke, or C) the Windows CD is bad.  The first two are easy enough to test: put in a LiveCD and see if that boots.  If so, you know the bios andn CD drive must be good.  You could try cleaning the Windows CD and retrying it - I know I have to clean my DVD's occasionally.  If that doesn't work, I guess you could try borrowing another Windows CD from a friend and see if that works.

I guess what Steve mentioned is also a possibility.  The Windows CD might fail somehow if the only partition is a large Ubuntu (ext3) partition, or something equally stupid.  In that case, boot the Ubuntu LiveCD and use the Gnome Partition Manager to completely wipe the hard drive and reformat it as FAT if necessary.  I don't have much expertise installing Windows.

Hope you get everything working again by Sep. 8!

---

### Post by Diamyst on 2007-08-25
First off it wasn't Freespires fault entirely.  I hit the wrong button.  Ubuntu installs from the Live CD after it is loaded.  I thought Freespire would do the same.  Unfortunately when you say install it installs.   I walked away and left it run thinking it would be up and running when I came back.  It was up and running and I set the date and time and clicked okay.   Went away again and let it run.   When I came back I had a clean install of freespire on the computer.  Obviously I should have sat there and paid more attention.  But hindsight is 20/20.

When I put the CD in again to see what I had done wrong I saw that the first choice was to use the entire drive and install Freespire.  Second choice was to run from CD.    I hit first choice..  wrong one.

The computer is definately reading and booting from the CD.   I have a full version of XP albeit an old one.     I tried cleaning it but it didn't seem to help.  My daughter just informed me that she had trouble with the last install of XP as well.  So there is a good chance it is something wrong with the disk.

Is there a windows emulator or something that would allow windows programs.. small ones... to run in Ubuntu Feisty Fawn.   I may just have to keep Ubuntu on it.

Thanks for all help guys.  I sure hope that I can learn all the stuff I need to to keep my 4 computers happy.  It seems to be a pretty steep learning curve and I am an old dog not used to new tricks.

Thanks

---

### Post by pgar23 on 2007-08-25
If your running 120 programs (ones that used to work on WIndoze) you will want to stick with windoze, just for the simple fact that you know they work on their OS. The programs may work on Ubuntu, but it may taake you a while to figure out how to get 120 programs to work with Ubuntu...
My suggestion is (Dual BOOT), 
1. If you know a friend or anyone who will let you borrow their XP install cd, borrow it and install XP back on the comp.

2. Install Ubuntu...hey at least you know your hardware and everything is compatible and that you dont have any problems installing Ubuntu.

Watch the VIDEO TUTORIAL from my signature...



GOOD LUCK, (if you need more help, you know where to find us.)
|
|
|
V

---

### Post by kwilliam on 2007-08-28
> **Diamyst said:**
> Is there a windows emulator or something that would allow windows programs.. small ones... to run in Ubuntu Feisty Fawn.   I may just have to keep Ubuntu on it.

Well, I certainly hope that you can get XP reinstalled.  But yes, there are several operating system emulators that can let you run Windows in Linux.  [VMware]("https://help.ubuntu.com/community/VMware/Server") and [VirtualBox]("https://help.ubuntu.com/community/VirtualBox") are two such programs.  They let you install [virtual machines]("http://en.wikipedia.org/wiki/Virtual_machine").  The Windows programs will run significantly slower, however.  Look up VMware or VirtualBox

---

