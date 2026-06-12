---
title: "problem with the latest 8.04 install"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by larrinski on 2008-04-25
I may just be having a brain fart...but here we go.

I have installed Linux(ubuntu,kubuntu, and fedora core) dual boot on my Macbook using refit about a dozen times with no hitch, but this time I have come across a problem. I am not an advanced user by any stretch, but can follow directions just fine, and am not scared of the Terminal...

I installed Refit, and rebooted from both the ubuntu 8.04, and kubuntu 8.04 disks and did the install. I say this as I have tried both versions with the exact result. I partitioned disk0s3 into disk0s3 as / and disk0s4 as swap. my disk0s3 is 21000mb, and my swap is 4041mb. The installs went just fine and I rebooted. After the reboot and selected Linux on HD, it can't find a bootable disk. I think that I just need to point refit to disk0s3, but don't know what command I need to enter to make that happen. If I need to make a /boot in the front of the install partition, let me know, but I haven't had to do that before.

Thanks in advance...:)

---

### Post by cyberdork33 on 2008-04-25
> **larrinski said:**
> I may just be having a brain fart...but here we go.

I have installed Linux(ubuntu,kubuntu, and fedora core) dual boot on my Macbook using refit about a dozen times with no hitch, but this time I have come across a problem. I am not an advanced user by any stretch, but can follow directions just fine, and am not scared of the Terminal...

I installed Refit, and rebooted from both the ubuntu 8.04, and kubuntu 8.04 disks and did the install. I say this as I have tried both versions with the exact result. I partitioned disk0s3 into disk0s3 as / and disk0s4 as swap. my disk0s3 is 21000mb, and my swap is 4041mb. The installs went just fine and I rebooted. After the reboot and selected Linux on HD, it can't find a bootable disk. I think that I just need to point refit to disk0s3, but don't know what command I need to enter to make that happen. If I need to make a /boot in the front of the install partition, let me know, but I haven't had to do that before.

Thanks in advance...:)
there is a bug in the Ubuntu installer. Reboot, and in the rEFIt menu, select the partition tool and sync your partition tables, then things should work properly.

---

### Post by larrinski on 2008-04-25
> **cyberdork33 said:**
> there is a bug in the Ubuntu installer. Reboot, and in the rEFIt menu, select the partition tool and sync your partition tables, then things should work properly.

I did that and it takes me to the white screen with Tux, and stays there...What next?
Cheers,
Larrinski.

---

### Post by luisbg on 2008-04-25
same here. need some help.

---

### Post by louelou21 on 2008-04-25
I am also having the same problem. get the Tux screen and it just stays there..

---

### Post by cyberdork33 on 2008-04-25
This is a different error. I don't know what might be causing that. You might check with the rEFIt devs.

Can you boot into OSX? Try disbling rFEIt and using the Option key to select the OS.

---

### Post by louelou21 on 2008-04-25
> **cyberdork33 said:**
> This is a different error. I don't know what might be causing that. You might check with the rEFIt devs.

Can you boot into OSX? Try disbling rFEIt and using the Option key to select the OS.

Yes this worked for me. Deleted 'efi' folder from my hard drive ( '/' ) held option at restart and successfully booted into Ubunto 8.04 from there. I believe you have to sync partition table with rEFIt first as linux partition did not show up when i help the option key at start up. (anybody correct me if I'm mistaken. This is the first time I run any sort of linux OS so I don't know much.)

excited looking forward to messing with Ubunto some more later.
 hope this works for others having similar problem.

---

### Post by larrinski on 2008-04-25
> **cyberdork33 said:**
> This is a different error. I don't know what might be causing that. You might check with the rEFIt devs.

Can you boot into OSX? Try disbling rFEIt and using the Option key to select the OS.

BINGO!!!
I can boot into OSX no problem with rEFIt. I will disable it and go in via the option key for now! Thanks for the great assistance!

---

### Post by crhis on 2008-04-25
I had the same problem, and what I did was install 7.10 and then just upgrade from that. It takes a while, but it is mostly just downloading everything again.

---

### Post by cyberdork33 on 2008-04-25
can someone file a bug with refit?

you have to use refit to sync the partition tables because of a bug in the Ubuntu installer, and apparently there is an additional bug in refit.

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by cyberdork33 on 2008-04-25
ok i got this issue with an install tonight as well. Can you guys say what options you chose during install? I used the amd64 disc and chose to install to the free space.

---

### Post by mabovo on 2008-07-30
I got this issue again with Hardy 8.0.4.1 and latest kernels updates.

rEFIT is installed in the OSX partition and GRUB doesn't start anyway. 

I have tried to reinstall GRUB and also installed LILO but seems that Ubuntu doesn't recognize "sda" partitions and it shows a message "Error parsing number".

All temptatives to recover GRUB failed. At last, tried to boot live CD and install GRUB and got the same error after reboot.
At the moment I have one OSX logo and two Tuxes in rEFIT menu.
Could be possible that I have two GRUB's installed in the same Hardy partition ?

---

### Post by cyberdork33 on 2008-07-30
> **mabovo said:**
> I got this issue again with Hardy 8.0.4.1 and latest kernels updates.

rEFIT is installed in the OSX partition and GRUB doesn't start anyway. 

I have tried to reinstall GRUB and also installed LILO but seems that Ubuntu doesn't recognize "sda" partitions and it shows a message "Error parsing number".

All temptatives to recover GRUB failed. At last, tried to boot live CD and install GRUB and got the same error after reboot.
At the moment I have one OSX logo and two Tuxes in rEFIT menu.
Could be possible that I have two GRUB's installed in the same Hardy partition ?
What error number? 23?

Please show how you installed GRUB manually. grub notation always uses (_h_dX,Y) format so if you try to use (_s_dX,Y) it will give this error.

---

### Post by mabovo on 2008-07-30
> **cyberdork33 said:**
> What error number? 23?

Please show how you installed GRUB manually. grub notation always uses (_h_dX,Y) format so if you try to use (_s_dX,Y) it will give this error.

Yeah ! Error 23.   I solved reinstalling Hardy again. Fortunately I had a separeted /home partition.  Now it is downloading 225 updates .... and I  still have two tuxes on rEFIT menu.

---

