---
title: "Forced Dual Boot"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by Mikey_MW on 2006-06-09
Ok, I just installed Ubuntu after trialing many LiveCD / friends Linux computers and its all going good. But I still need Windows XP (so my mum can use it) on my computer. Is dual booting the way to go and how might I go about it? Any recomendations on the programs I should use?

Note - This PC has two physical hard drives, 80Gb and 20Gb. Does this have any effect on the dual boot? I would like WinXP to have the 20.

Thanks

---

### Post by kb3hkg on 2006-06-09
To dual boot, have windows already installed on the 20GB and then install ubuntu on the other drive, with the bootloader Grub you may want to set Windows as the default so that your mother doesn't have to select it. You can select ubuntu when you want to use it though.

It sounds like dual boot is definitely the way for you to go. Having 2 drives doesn't affect ability to dual boot at all, Grub just has to know where each OS is on which drive, it does that on its own mostly so you should be fine.

---

### Post by cotcot on 2006-06-09
I would go for dual boot. If you google on 'ubuntu XP dual boot  tutorial' you can easily find information.
Here are a couple of links : [http://www.hezardastan.org/breezy_xp_dualboot/en/]("http://www.hezardastan.org/breezy_xp_dualboot/en/") ; 
[URL="http://users.bigpond.net.au/hermanzone/[/URL]

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

It is good to read a lot of information before you sta
rt.

You can choose on what hard disk you put XP. Important is that you install XP first and ubuntu afterwards. 

It is easier to have XP on the 'master' hard disk (hda) and ubuntu on the 'slave' (hdb). So if the 20 GB drive is 'master' that would be easier. Although the opposite is also possible.

---

### Post by Luke771 on 2006-06-09
Dual boot: Windows on the master drive, Linux on the slave drive, Grub on MBR

---

### Post by Luke771 on 2006-06-09
Partition both the drives leaving 10 GB for each OS, NTFS for Win on one drive (master) and Ext2 for Linux on the other one (slave), plus the swap space, and format the rest of the drives as FAT32: that way the space will be accessible and writeable by both OSes: if you only use NTFS for win and ext2 ext3 or whatever for Linux, then windows won't read the files you saved under Linux, and linux will read the windows drive but you wont be able to write on it (you don't wont to write on a NTFS partition using linux) so the best choice is to make one relatively small partition for each OS and some bigger FAT32 partitions for file storage, which will 100% accessible by both.

---

### Post by aktiwers on 2006-06-09
You could also install it in Vmware. For me XP is just as fast ontop of Ubuntu, as if its not.

Check this guide.
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

Then you could simply power op Vmware, when your mother needs to use the PC. :)

---

### Post by Greevous on 2006-06-09
[QUOTE=kb3hkg]To dual boot, have windows already installed on the 20GB and then install ubuntu on the other drive, with the bootloader Grub you may want to set Windows as the default so that your mother doesn't have to select it. You can select ubuntu when you want to use it though.[/QUOTE]

I tried reading a little bit about the bootloader Grub, but it isn't making very much sense. How would I set Windows to be the default operating system when the computer boots?

---

### Post by sailor2001 on 2006-06-09
at boot-up, count the options, starting with zero.....then sudo gedit /boot/grub/menu.lst   and set the order there for boot up.

---

### Post by anaconda on 2006-06-09
[QUOTE=Luke771]Dual boot: Windows on the master drive, Linux on the slave drive, Grub on MBR[/QUOTE]

I would do it the opposite way...

eg. Windows on the SLAVE drive (=20GB) and linux on the master. This way you would get (the  whole) grub and ubuntu in the linux drive, and windows to its own drive (with its own boot loader).

Then if you ever have any problems booting you could just unplug the linux-drive, and windows would still boot normally. eg. you wouldn't "mess" with windows-drives boot sector... 

If you install grub to mbr of the windows-drive, and something happens to your linux-installation you wouldn't be able to boot to windows.. You would have to boot with windows install CD and go to rescue, and overwrite the mbr... This happens because the whole grub-boot loader doesn't fit to MBR. Parts of it is in /boot folder of your linux-drive..

When installing grubyou would have to remap the windows drive to think it is the master drive to make booting to windows to work. this is easy in grub. just edit the menu.lst and add
          map (hd0) (hd1)
          map (hd1) (hd0)
to where windows is loaded..

---

### Post by Greevous on 2006-06-09
[QUOTE=sailor2001]at boot-up, count the options, starting with zero.....then sudo gedit /boot/grub/menu.lst and set the order there for boot up.[/quote]

[QUOTE=anaconda]
When installing grubyou would have to remap the windows drive to think it is the master drive to make booting to windows to work. this is easy in grub. just edit the menu.lst and add
          map (hd0) (hd1)
          map (hd1) (hd0)
to where windows is loaded..[/QUOTE]

I tried that but I guess I don't have permission to edit the (read-only) menu.lst. (?)

---

### Post by confused57 on 2006-06-09
```
sudo gedit /boot/grub/menu.lst
```

In the menu.lst, the lst is short for list, not first...if that may be what you're doing, in other words it's a lowercase "L".

gedit only works in the GUI terminal,  

nano is used as the text editor in the console,  eg  sudo nano....

---

### Post by Greevous on 2006-06-18
```
sudo gedit /boot/grub/menu.lst
```

Whenever I try this, I get a password prompt in the terminal, but it won't allow me to type anything for the password. It's as if the keyboard has frozen or the computer has stopped responding, but the rest of the interface responds perfectly.

---

### Post by Dancingwllamas on 2006-06-18
The stars do not show up in the console, but it is accepting input. Type your password in and press enter and it will work.

---

