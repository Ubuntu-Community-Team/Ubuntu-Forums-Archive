---
title: "GRUB Error 22"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-09-01
I dual boot Windows XP and Ubuntu Dapper.  Recently I realized I needed more space on Ubuntu's partition so I decided to use the GPARTED LiveCD to repartition my Hard Disk.  After I completed this everything worked fine.  Here's a low tech diagram of my HDD at this point:

**Windows --- Unallocated Space --- Ubuntu**

Since GPARTED can only expand a partition to the right I had to copy the Ubuntu partition and paste it into the Unallocated Space:

**Windows --- Ubuntu copy --- Ubuntu**

Then I deleted the Original Ubuntu partition and expanded the Ubuntu copy to fill the rest of the HDD:
[B]
Windows --- Ubuntu copy[/B]

Everything appeared to be normal until I rebooted: I get a GRUB Error 22 in the boot process. ](*,)  

Any help would be greatly appreciated as I can't boot either one of my Operating System's at the moment.

---

### Post by jordanmthomas on 2006-09-01
Go back on your LiveCD.
Make a folder on the desktop and call it ubuntu or something similar.
Go to System --> Administration --> Disks
Go to the Partitions tab and find your Ubuntu partition.  Note the name of it.  (/dev/hdxy or /dev/sdxy)
Using the window you're in, mount your drive at /home/ubuntu/Desktop/*Whatever you called your folder*
Now, press ALT + F2 and type
```
gksudo nautilus /home/ubuntu/Desktop/*Whatever you called your folder*
```
Navigate (in this folder) to /boot/grub and open menu.lst
Find the part that looks something like this:
```

title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=[COLOR="Red"]/dev/sda1[/COLOR] ro quiet splash vga=$
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

```
Find which drive it's looking in (in red here) and change it to the number you noted in the Disks window earlier.
Reboot and pray.

**edit** 
This happened because your second partition was blank and your third was Ubuntu.  Now your thrid partition does not exist.

---

### Post by fatsheep on 2006-09-01
Thanks for the reply.  I went into my Ubuntu LiveCd and followed your directions.  My Ubuntu partition is located at /dev/hdc4 (instead of hdc2).  I have bolded my changes to the menu.lst file:

> 
title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/**hdc4** ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/**hdc4** ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot


When I reboot I get the exact same error: GRUB error 22.  :(   

Am I not praying hard enough? :wink:

---

### Post by jordanmthomas on 2006-09-01
hmm...do you have any other hard drives?

You could try running
```
sudo grub-setup /dev/hdc
```
after mounting the partition and see if that helps.

Once you can boot, you'll also need to update /etc/fstab to mount the correct swap partition since it's probably changed too.

I've helped about as much as I know how, so someone else may need to help.
Sorry.

---

### Post by fatsheep on 2006-09-01
Nope only one hard disk - a samsung spinpoint 40 GB. 

Here's what > sudo grub-setup /dev/hdc  returns:

> sudo: grub-setup: command not found


Same for > sudo grub-setup /dev/hdc4... :-k

---

### Post by jordanmthomas on 2006-09-01
Oops!  That should be grub-install

---

### Post by jordanmthomas on 2006-09-01
Also, you may want to try this:
[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by Stone123 on 2006-09-01
[QUOTE=jordanmthomas;1451750]Go back on your LiveCD.
Make a folder on the desktop and call it ubuntu or something similar.
Go to System --> Administration --> Disks
Go to the Partitions tab and find your Ubuntu partition.  Note the name of it.  (/dev/hdxy or /dev/sdxy)
Using the window you're in, mount your drive at /home/ubuntu/Desktop/*Whatever you called your folder*

[/code]

You need to login on that partition first.

Open terminal

Type:
sudo chroot /home/ubuntu/Desktop/*Whatever you called folder*

and then type sudo grub-install /dev/hdx

or you can type 
sudo grub 
find /boot/grub/stage1
-> you will get hd(x,y)
root (hdx,y)
setup (hdx)
quit

As a mater of fact you can do this second part without live cd , from grub on bootup.

---

### Post by fatsheep on 2006-09-01
All is good now.  Turns out I had to change the y coordinates in the boot entries to 3:

> 
title Ubuntu, kernel 2.6.15-26-amd64-generic
root **(hd0,3)**
kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hdc4 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root **(hd0,3)**
kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hdc4 ro single
initrd /boot/initrd.img-2.6.15-26-amd64-generic
boot

title Ubuntu, memtest86+
root **(hd0,3)**
kernel /boot/memtest86+.bin
boot


Thanks for the great help, all works good now.  :p

---

