---
title: "2 HD, 2 OS thru bios boot sequence not &quot;traditional dual boot&quot;"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by FunWithSoil on 2006-10-08
I have 1 internal and 1 external hard drive. I want to just keep windows on the internal, but I want to plug in the external and start linux when i want.  
The bios boot sequence is 

1. cd
2. usb
3. internal hd

Ubuntu was installed on the external drive when it was the internal drive with no windows present, not as a dual boot set up. 
Then it was put in an enclosure and windows was installed on the current internal hd.

Either drive alone as the internal drive boots fine.

When the external (linux) is plugged in, I get a grub error.

Is it possible to do this? The bios tells it which drive to go to, then why should the mbr of the linux drive care if there is another drive that wasn't there during install of ubuntu?

---

### Post by Bigbluecat on 2006-10-08
HI FunWithSoil,<br><br>I suspect that you menu.lst has been written as if Ubunutu is on the internal drive (I assume hd0). Now when you move the drive to paths are pointing to the wrong place for you linux kernal and grub boot stages. <br><br>We need to edit your menu.lst to get everything pointing in the right direction.<br><br>Some people use the Live CD to bring Ubuntu up then mount the drive to edit the menu.lst file.<br><br>Personally I have manually booted my kernel twice from the grub comman line (press c during grub boot). There is an excellent guide here:<br><br>http://users.bigpond.net.au/hermanzone/p15.htm<br><br>Scroll down to&nbsp; the commnad line interface section and there are very good step by step instructions.<br><br>We will certainly need to do some interrogation of your system to find out the how grub names your external disk (hd?) and which /dev/sd? it is.<br><br>Hope this helps.<br><br>

---

### Post by Bigbluecat on 2006-10-08
Hmmm,

Really not sure what happened to the formatting of that reply. Must preview post in future.

I'll re-write as it looks completely unreadable.

---

### Post by Kateikyoushi on 2006-10-08
I think it is possible.
You have to boot the livedisc then check your partitions and edit the grub menu accordingly.

This lists your partitions after you boot the live disc.

```
sudo fdisk -l
```

Possibly you have to mount the usb drive in case ubuntu does not do it automatically.

Then edit /boot/grub/menu.lst

---

### Post by Bigbluecat on 2006-10-08
HI FunWithSoil,

I suspect that you menu.lst has been written as if Ubunutu is on the internal drive (I assume hd0). Now when you move the drive the  paths are pointing to the wrong place for you linux kernal and grub boot stages.
 
We need to edit your menu.lst to get everything pointing in the right direction.

Some people use the Live CD to bring Ubuntu up then mount the drive to edit the menu.lst file.

Personally I have manually booted my kernel twice from the grub comman line (press c during grub boot). There is an excellent guide here:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Scroll down to the commnad line interface section and there are very good step by step instructions.

We will certainly need to do some interrogation of your system to find out the how grub names your external disk (hd?) and which /dev/sd? it is.

Hope this helps. 

Better format:mrgreen:

---

### Post by FunWithSoil on 2006-10-08
Thanks alot guys for the info and link.  I'm hopefull. I just wanted to make sure it was possible.  Have some project deadlines now, but I'll get to that next week hopefully. This sure is a great community and I am gratefull for your time.

---

### Post by CatKiller on 2006-10-08
It may just be a case of changing each instance of hd0 in your /boot/grub/menu.lst to sd0.

---

### Post by gn2 on 2006-10-08
The Linux on USB hard drive is an excellent option, and I hope that the option to install direct to USB is incorporated into Ubuntu with the next release.

There's no reason why it shouldn't be available, PCLinuxOS has exactly this option on install with it's excellent Draklive Installer.

---

