---
title: "managed to install dual-boot with Vista already installed"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Nathan_M on 2007-04-28
From one Linux newbie to many others:

I've seen a few topics about installing a dual-boot with Vista, and all of them looked really complicated. I tried a few methods and messed up my Vista boot loader a couple of times, but eventually found a method which I believe is quite easy, and so I thought I'd share it here. I don't think anyone else has posted this method before... sorry if I missed something.

First of all, my computer came with Vista pre-installed, and I've been using it like that for a few weeks, so I didn't want to have to uninstall Vista.

1. Log in to Vista as an administrator. Go to the Control Panel and type "partition" in the search box. Click the "Create and format hard disk partitions" link.

2. Choose the drive you want to install Ubuntu on (it can be the same drive as your OS), and choose a large partition to shrink. Right click on the partition and shrink it by however much space you want to reserve for the Ubuntu partition (minimum 2 GB).

3. Restart the computer with the Ubuntu installation CD in the drive, and wait for Ubuntu to start.

4. Double-click the install icon on the desktop, and follow the instructions.

5. When you get to the part asking what disk to install it on, you can choose Guided - larges continuous free space, or Manual. If you choose manual, select the free space you just cleared in Windows, and use it to create a new partition, with the format set to us3. If you like, you can create two partitions, one of which is to be used as swap-space. Set the file system for this one to swap.

6. Follow the rest of the installation process and you're done. Now, each time you start up your computer, you'll get a menu asking what you want. Either select the first Ubuntu option, or the "Windows Vista / Longhorn" option.

I might post more later as a reply to this, about how to configure the start-up menu (GRUB) to act how you want. For example, mine starts up Windows by default, and only stays for 3 seconds, not the default of 10. Depends if anyone asks for it, I suppose.

Hope this has helped someone.
-Nathan

---

### Post by Mazza558 on 2007-04-28
Does Vista allow you to resize thing even whilst it's running, or does it apply them before restarting?

---

### Post by Nathan_M on 2007-04-28
It just resizes them there and then. Pretty clever, methinks.

---

### Post by Arken on 2007-04-28
If I partition my hard drive, will I lose all my data?

---

### Post by ucsdrake on 2007-04-28
i wouldnt think so, however make sure you defrag your hard drive at least once if not twice just to make sure

and if you want to really make sure not to lose any information, back it up on an external hard drive :D

---

### Post by gzone on 2007-04-28
This is a good post...I'd like to find a method of dual booting an Winblows XP system with Ubuntu. Nice job on the instructions.

---

### Post by Arken on 2007-04-28
> **ucsdrake said:**
> i wouldnt think so, however make sure you defrag your hard drive at least once if not twice just to make sure

and if you want to really make sure not to lose any information, back it up on an external hard drive :D

If i had an ex. hard drive, i wouldn't have asked

---

### Post by seetho on 2007-04-28
External HDs are cheap and very useful for quick backups.  You can use regular IDE HD with one of those IDE to USB converters.  I bought one for about $7. It even comes with a power adapter.  You don't have to buy expensive external HD enclosures.

---

### Post by sailor2001 on 2007-04-28
> **Nathan_M said:**
> From one Linux newbie to many others:

I've seen a few topics about installing a dual-boot with Vista, and all of them looked really complicated. I tried a few methods and messed up my Vista boot loader a couple of times, but eventually found a method which I believe is quite easy, and so I thought I'd share it here. I don't think anyone else has posted this method before... sorry if I missed something.

First of all, my computer came with Vista pre-installed, and I've been using it like that for a few weeks, so I didn't want to have to uninstall Vista.

1. Log in to Vista as an administrator. Go to the Control Panel and type "partition" in the search box. Click the "Create and format hard disk partitions" link.

2. Choose the drive you want to install Ubuntu on (it can be the same drive as your OS), and choose a large partition to shrink. Right click on the partition and shrink it by however much space you want to reserve for the Ubuntu partition (minimum 2 GB).

3. Restart the computer with the Ubuntu installation CD in the drive, and wait for Ubuntu to start.

4. Double-click the install icon on the desktop, and follow the instructions.

5. When you get to the part asking what disk to install it on, you can choose Guided - larges continuous free space, or Manual. If you choose manual, select the free space you just cleared in Windows, and use it to create a new partition, with the format set to us3. If you like, you can create two partitions, one of which is to be used as swap-space. Set the file system for this one to swap.

6. Follow the rest of the installation process and you're done. Now, each time you start up your computer, you'll get a menu asking what you want. Either select the first Ubuntu option, or the "Windows Vista / Longhorn" option.

I might post more later as a reply to this, about how to configure the start-up menu (GRUB) to act how you want. For example, mine starts up Windows by default, and only stays for 3 seconds, not the default of 10. Depends if anyone asks for it, I suppose.



  starting with the #0 (inyour case windows) count down to the ubuntu kernal and remember that #.  In the terminal type: sudo gedit /boot/grub/menu.lst   
Edit the default start-up to the new # you wanted. also a little further down you can change the start-up time to more seconds if you wish

Reply With Quote
-Nathan
starting with the #0 (inyour case windows) count down to the ubuntu kernal and remember that #.  In the terminal type: sudo gedit /boot/grub/menu.lst   
Edit the default start-up to the new # you wanted. also a little further down you can change the start-up time to more seconds if you wish

---

### Post by Nathan_M on 2007-04-28
> **Arken said:**
> If I partition my hard drive, will I lose all my data?

There's probably a risk, but I lived dangerously and didn't. It used to be the case that partitioning your hard drive meant formatting it, but not anymore. As ucsdrake pointed out, defragging minimizes the risk further.

---

