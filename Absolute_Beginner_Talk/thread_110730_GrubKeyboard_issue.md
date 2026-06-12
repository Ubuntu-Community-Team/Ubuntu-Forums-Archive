---
title: "Grub/Keyboard issue"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by TDonaghe on 2005-12-31
Hi all,

After setting up my dual boot system with WinXP and Ubuntu, I was able to easily switch between WinXP and Ubuntu during reboot when Grub was showing.  After upgrading to Kubuntu, though, the keyboard no longer responds when Grub is showing.  I can't use the down arrow keys to get to Windows XP.  

I realize that it probably has nothing to do with Kubuntu, but I'm not sure what else I've done.  The keyboard is just a normal USB keyboard.  Does anyone have any clues for me?

Thanks!

---

### Post by prizrak on 2005-12-31
Weird and shouldn't have happened. One place I can suggest looking at is your computer's BIOS and see if USB keyboards are enabled. No idea how it would possibly disable it just by installing a diff OS but hell it's an idea :)

---

### Post by kingsidy on 2006-01-01
just out of the blue try reconfiguring grub

---

### Post by TDonaghe on 2006-01-01
[QUOTE=kingsidy]just out of the blue try reconfiguring grub[/QUOTE]

I think that's what I want to do, but I'm not sure how.  How do I reconfigure grub?  I'll do some looking and update this response if I figure it out, otherwise I'd appreciate if someone could let me know.

Thanks!

---

### Post by Mustard on 2006-01-01
Whatever you do, make sure you backup your grub menu.lst first. :)

If you mess it up at least you can replace it with your old one.

-edit-

This might sound like a stupid idea, but its one of those things that has helped me fix some really strange USB problems.  Shut down the computer, remove the power cable from the back, then leave it for a while.  Plug the power cable back in, reboot and see how you go.

---

### Post by prizrak on 2006-01-01
I found this [http://geodsoft.com/howto/dualboot/grub.htm#install](http://geodsoft.com/howto/dualboot/grub.htm#install) to be a how to on reconfiguring GRUB, seems like it would take you a bit of time ;)

---

### Post by kingsidy on 2006-01-01
i am not sure but one thing you can do is pop in the install cd, navigate through the install list, go to the install grub step. after it reinstalls, exit and reboot. back up your menu list before that though just in case. 
to reocnfigure a package, type in the terminal as sudo: dpkg-reconfigure <package name>

---

### Post by kingsidy on 2006-01-01
check out this post it tell you how to restore grub if it is messed up using the install cd.
[http://ubuntuforums.org/showthread.php?t=76652]("http://ubuntuforums.org/showthread.php?t=76652")

---

### Post by TDonaghe on 2006-01-01
I have resolved my problem!  Wooo!  I tried the Grub solution shown above, and wouldn't ya know it, when the computer rebooted with the Ubuntu install disk, I couldn't press "ENTER" on the first screen when you choose if you want to install the Server version or not.  

So, in desperation, I rebooted again and just started hitting the DEL key like a madman, and the BIOS setup came up!  Wooo.  So, I started searching around in there and in one of the Advanced menus there was an option of whether you wanted the BIOS or the OS to control the USB keyboard.  It was set to OS, and so I switched it to BIOS and rebooted.  Since then I've been able to control the keyboard during bootup.  Hopefully this has completely fixed the problem.

It's still weird to me that I had previously been able to control the keyboard when Grub was up.  But I only had done it a couple of times, and maybe each time was after I had booted WinXP.  I'm not sure.

So either way, I'm not sure that Linux had anything to do directly with this problem, and I didn't have to reconfigure anything.

Thanks for all the help guys!!

---

### Post by kingsidy on 2006-01-02
glad it worked

---

### Post by Disorder on 2006-01-02
Do you happen to be using a Saitek "Eclipse" or "Gamers Keyboard". My USB Eclipse was real finicky around bootmenu's including Grub, lilo, Windows boot menu, the boards bootmenu.

---

### Post by TDonaghe on 2006-01-03
No, Disorder, but it is a Z-board which is one of those gamer type boards where you can load different key layouts onto it.  It works fine now, though, since I told the BIOS to recognize the board outside of the OS.

---

### Post by SilverWave on 2007-07-29
Thanks TDonaghe that worked for me as well !!!
I have a saitek 2 keyboard.
Hidden BIOS setting:
Pheonix Awardbios > integrated peripherals > on-chip PCI device > USB keyboard support via > set this to BIOS from the OS default.

Key words for anyone else googling for this issue: Saitek usb Ubuntu boot livecd grub bios os.


> **TDonaghe said:**
> DEL key like a madman, and the BIOS setup came up!  Wooo.  So, I started searching around in there and in one of the Advanced menus there was an option of whether you wanted the BIOS or the OS to control the USB keyboard.  It was set to OS, and so I switched it to BIOS and rebooted.

---

