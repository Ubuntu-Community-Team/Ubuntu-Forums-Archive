---
title: "Ubuntu problems on Macbook"
date: 2012-12-02
forum: Apple Hardware Users
---

### Post by Barter00 on 2012-12-02
So, yesterday I installed ubuntu on my Macbook, I removed all the partitions and made only one for Ubuntu, so I don't have OSX installed anymore.

I used it for a while and noticed the battery doesn't last as long as on OSX, so I tried some fixes from askubuntu.com and now it's kinda ****** up and I just wanted to reinstall ubuntu, or install OSX or lubuntu.

The problem is I can't access rEFIt anymore, if I create a bootable USB it just won't boot from it, and inserting the OSX install DVD does nothing, it won't boot from it. Sometimes grub bootmenu shows up but I can only boot ubuntu from there. I tried the command+option+O+F shortcut after turning the macbook on but it does nothing.

What can I do? I probably just want OSX back :(

---

### Post by LuisGMarine on 2012-12-02
Boot the Ubuntu LiveCD yet again, and run the partition editor.  Then delete all the partition (including ubuntu) and reformat them to something like +HFS.

After that and you shutdown and run the OSX live cd, and press and hold the letter key c.

Hope this helps.

**Keep in mind that this will remove all operating systems on the computer.  This is exactly what I do on my macbook pro when I decide to remove ubuntu and install OSX again for a bit.  I can't gurantee it will work for you, so please try on your own risk and only do if you do not care that it will get rid of any working operating system.

---

### Post by alexmurray on 2012-12-02
Try booting up and holding down option / alt with the livecd and you should be able to select to boot from it.

---

### Post by Barter00 on 2012-12-03
I tried creating a bootable USB again following this guide [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)
and it just boots the installed ubuntu when I restart, not the USB, even when holding option/alt or C.

---

### Post by LuisGMarine on 2012-12-04
I'm not sure what the problem could be ... I could be related to the USB install or not.  

Is it possible that you can try a CD instead?  How about crating a bootable rEFIt disc to re-install REFIt.  However if this works I would read on what you would have to do to reinstall the proper things.

That's all I can think of for now, sorry :\

---

### Post by trogdor1138 on 2012-12-05
OK, this is a long shot, especially if your MacBook is exactly as you've described, but this may work:

- Image your USB drive from your OS X install DVD (Clonezilla does a good job of copying drives exactly: [http://clonezilla.org/](http://clonezilla.org/))

- Insert both the OS X install DVD and the USB drive, then reboot until you get a GRUB menu

- At the menu, quickly press 'c' to bring up a GRUB console

- First, search for the OS X boot files: search --file --set=root /System/Library/CoreServices/boot.efi

- The above command sets the first device with that file found as root. If it's found, then enter: chainloader (${root})/System/Library/CoreServices/boot.efi

- If the above doesn't work, you'll need to play around with trying to use 'chainloader' with manually-specified boot paths. For example: chainloader (hd1,1)/System/Library/CoreServices/boot.efi

- The boot files I've named are for recent versions of OS X. I don't know which version of the DVD you have, but older boot files may instead be at: /usr/standalone/i386/boot.efi

- If you need some help with GRUB, this part of the manual shows how to reference different devices and files: [http://www.gnu.org/software/grub/manual/grub.html#Device-syntax](http://www.gnu.org/software/grub/manual/grub.html#Device-syntax)

- Once you're in to OS X setup, use Disk Utility to wipe the hard drive and run the verify and repair utilities

- Follow the OS X install process

This will, if it works, wipe your hard drive clean and set you up with a new install of OS X. GRUB can chain-load OS X from a different partition, but I've never explicitly tried loading the installer from GRUB off of a DVD or USB drive. Theoretically, it shouldn't be that different from simply selecting a Linux kernel in GRUB and booting that, but with Apple's system who knows.

---

### Post by asifnaz on 2012-12-13
you should have keep OS X on one partition

---

### Post by TBABill on 2012-12-13
> **asifnaz said:**
> you should have keep OS X on one partition
 Without question. Once you've paid for an OS, why delete it unless it becomes corrupt or space on the HDD is an issue?

---

### Post by Fet600 on 2012-12-17
Hi,

I've been through the exact same issue as you on a couple of MacBooks (3,1 and 7,1 versions) and I found that in both cases I was able to install anything I wanted by using an external DVD drive plugged into the USB port and then booting with the option key held down.

I've no idea of the reason behind it but the internal drive just stopped behaving but returned to normal once I'd re-installed OS X.  I've also never been able to get the bootable USB stick versions of Ubuntu to work on my MacBooks.

Not sure if this will work for you but this was my experience.

Hope this helps.

---

### Post by Maxadax on 2012-12-17
What do you mean exactly when you say it doesn't boot into the DVD? Does it not detect it?

If you get the DVD working, here's what you do:

If you can, copy all your files over to an external Hard Drive.

1. Pop in your OS X DVD which came in the box and boot into that by holding C on startup
2. Go into disk utility from the top menu bar (ignore the Mac OS X installation window for now)
3. Reformat ("erase") the drive by selecting the "erase" tab.
4. Then,  you restart into the DVD (hold C) again and install as usual.
5. If you backed up, copy all the files back over.

I've done this before but it's been a while. Also I'm going by what it's like on Snow Leopard, it's probably the same on all OS X versions though.

Also, as pointed out above me, for some reason Mac's tend to boot into external drives better. With my experiences I can tell you that you can create 2 partitions on the external drive, one for the Mac OS (Or probably Ubuntu) DVD and the second partition to be used for your file backups. They say this is dangerous though, so beware.

So I would try to burn your Mac OS install DVD to your hard drive, if you can't use your MacBook then use another computer. If you want to back up on the same drive you can partition it so that you can also have a backup. Then, hold down "option" on boot up and it should show you the drive.

If all fails then I would just take it to an Apple store. Those people are hugely underrated, in my experience.

Good luck!

---

