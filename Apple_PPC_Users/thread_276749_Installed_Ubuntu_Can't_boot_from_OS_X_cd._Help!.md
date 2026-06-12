---
title: "Installed Ubuntu: Can't boot from OS X cd. Help!"
date: 2006-10-13
forum: Apple PPC Users
---

### Post by mph66 on 2006-10-13
Hi All,

I've been seeking an answer for days, and I'm coming up with bubkes.  Hoping someone can help.  Here's the situation: I backed up all files, wiped the hard drive on my eMac (was running 10.3- 40 gb hd, 1 Ghz, PPC, 512 RAM) and installed Ubuntu from the Live cd for PPC.  It's great.  I want to keep it, but I still need a Mac partition soooo...

I'm trying to create a Mac HFS+ partition, but when I boot from the live CD, It won't allow me to create an HFS+ parition in the "unallocated" space.  (I right-click->New->Primary->HFS+ is grayed-out).  If I choose "Extended" it defaults to "extended".  When I try to boot from the OS X cd, it balks.  Do I have to edit something in the boot file?  How? Do I have to create an HFS+ boot partition?  How do I get the comp to decide which (Linux or Mac) to boot into? All I want to do is install OS X on its own partition.  I know there has got to be a way, but I'm a newbie and I'm lost, sadly.  

Please help.  I've been beating my head against this wall for four days.  And it hurts.  ](*,) 

-Marc

---

### Post by Jose R on 2006-10-13
From my understanding, you can not do what it is you want to do.

If I'm reading you right, you have Ubuntu on the HD with some unallocated space, and then you want to install osx.

OSX needs to be installed first, and occupy the first portion of the HD.  You will need to insert the OSX cd and wipe the HD using disk utility and create a HFS+ partition for osx and leave the remainder of the HD as free space.

Then insert the live cd.  Ubuntu will see the HFS+ partition and istall itself on the "free space" creating the yaboot partition on its own.  So, at startup you will have th option of booting into osx or ubuntu.

---

### Post by mph66 on 2006-10-13
> **Jose R said:**
> From my understanding, you can not do what it is you want to do.

If I'm reading you right, you have Ubuntu on the HD with some unallocated space, and then you want to install osx.

OSX needs to be installed first, and occupy the first portion of the HD.  You will need to insert the OSX cd and wipe the HD using disk utility and create a HFS+ partition for osx and leave the remainder of the HD as free space.

Then insert the live cd.  Ubuntu will see the HFS+ partition and istall itself on the "free space" creating the yaboot partition on its own.  So, at startup you will have th option of booting into osx or ubuntu.

So if I'm reading you right, I'm stuck with a single-boot system and can never again boot from OS X?  Somehow I can't believe that's entirely correct.  There must be a way to get this eMac to boot from the OS X system disk.

-Marc

---

### Post by Jose R on 2006-10-13
No, you can do a dual-boot, but you need to install osx first on the hd.

yaboot gives you the option of booting into osx or ubuntu.  If I were home I would post a screenshot.

The fact that you cannot boot from the osx cd is problematic. I'm assuming you are pressing down on the "c" key when you restart after the OSx cd is inserted?

---

### Post by mph66 on 2006-10-13
> **Jose R said:**
> 
The fact that you cannot boot from the osx cd is problematic. I'm assuming you are pressing down on the "c" key when you restart after the OSx cd is inserted?

Oops.  Sorry.  Yes, I'm definitely holding down the "C" key.  That's how this whole mess got started in the first place.  I held down the "c" key and booted the Live CD and said, "Aww, what the heck?"  So, yes, I know how to boot from a cd, whether it's Mac or Ubuntu. :)

When I try to boot from the Mac CD, I get the black screen with the choices:
l to boot Linux
c to boot from cd.

I get "..." (wait) and then it never acknowledges the Mac OS X cd and boots (after a wait) into Ubuntu. 

-Marc

---

### Post by Jose R on 2006-10-13
Well, to trouble-shoot, maybe because you are not holding the key down long enough?  that's the only thing that comes to mind?

When starting from the osx cd, you shouldn't even see the linux intro screen - it should go direct to the start-up disc.

Try again - restart ubuntu with the cd inserted, press the c key after the screen goes black, and keep holding it down until you hear the cd-rom drive start reading the cd and you see the apple welcome screen.

---

### Post by mph66 on 2006-10-16
> **Jose R said:**
> Well, to trouble-shoot, maybe because you are not holding the key down long enough?  that's the only thing that comes to mind?

mph66:  Definitely not the problem.  I've held the "c" key down through 3 reboot attempts.  Each  time, the loader can't find the OS X cd.

When starting from the osx cd, you shouldn't even see the linux intro screen - it should go direct to the start-up disc.

mph66:  It doesn't do that.

Try again - restart ubuntu with the cd inserted, press the c key after the screen goes black, and keep holding it down until you hear the cd-rom drive start reading the cd and you see the apple welcome screen.

I've tried this on several occasions.  Still doesn't work.  Anyone out there have any idea what might be wrong?

-mph66

---

### Post by notimpressed on 2006-10-16
I have same problem. I hold the c key down and the apple logo appears and then a graphical glitch (a coloured line) appears and nothing else. Does anyone know of a mac bootable cd util that format the drive and re-partition?

---

### Post by oswaldkelso on 2006-10-16
If you have a friend with a mac connect your macs with a firewire cable and clone his mac to yours with "carboncopycloner" or "superduper" if you have a firewire ipod you can use that.(its lighter than carrying a mac on the bus). ie clone a mac to an ipod then back to your mac then use disk utility to partition your HD and start again. any version of osx will do to get you up an running. Once running see if osx can read your disk and reinstall your data.

---

