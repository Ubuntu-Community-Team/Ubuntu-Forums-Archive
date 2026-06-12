---
title: "2 hard drives 2 OS's"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Whamola on 2008-02-09
I recently recieved a hard drive with some version of Windows on it and have it set as the slave on my system and I was wondering how to be able to choose which one to boot from.  I know this question has most likely been answered a million times, but I'm so lost that I'm too frustrated to find it.  I tried setting the Win OS as the only HD and got "can not find NATDR"  or something along those lines, so it might just be screwed up.

Thanks

---

### Post by ashmew2 on 2008-02-10
it would have been " NTLDR is missing"...Typical of Windows (lol)

So , Have you tried going in the BIOS and setting the Boot Priority ? Like if it is (in order , assuming you have SATA disks) :

SATA 2
SATA 1

Try changing it to 

SATA 1
SATA 2
I had the same problem , got it fixed the same way,

---

### Post by R@inm@n on 2008-02-10
What is your main OS?  Ubuntu?

 If you want the option to dual- boot and have an OS installed on each HDD, you need to set the  drive with Linux on it to Master, and the Win HDD as slave.

Boot into Ubuntu and open the Terminal. It's under Applications / Accessories.

 Type in the following:

 gksudo gedit /boot/grub/menu.lst

 You will be asked for your password.  Type it in and press ENTER.

  The config list will then appears on your desktop, so scroll to the very bottom of it.

After the line " ###END DEBIAN AUTOMAGIC KERNALS LIST"

Type in ...or copy and paste this in.


title           Windows XP
root            (hd1,0)
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

While you are in there, find Hidden and comment it out...like this .....    #Hidden

Then change the timeout to 10 seconds.


Save and exit the list.

That should let you choose which OS to boot from a menu when the computer boots up.



    HTH,



    R.

---

