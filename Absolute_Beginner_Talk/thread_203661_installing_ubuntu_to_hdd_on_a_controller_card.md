---
title: "installing ubuntu to hdd on a controller card?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by darckhart on 2006-06-25
hi all.

i want to install ubuntu to an ide hard drive that is connected to my controller card, and boot from it.

if i wanted to do this in windows land, during fresh install i would press F6 (or whatever it was) to load 3rd party driver that would install the controller card. I could then proceed with the rest of the installation process. how can i do this in ubuntu?

note: i do NOT want to do anything to ide/hda1 (ie. dual boot).

thanks

---

### Post by ZeusABJ on 2006-06-25
If its a RAID card this may help:

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

If not, sorry.

---

### Post by darckhart on 2006-06-26
hm not quite, but it gave me the idea to try to install the card's drivers ([http://www.promise.com/support/download/download2_eng.asp?productId=139&category=driver&os=3&go=GO#](http://www.promise.com/support/download/download2_eng.asp?productId=139&category=driver&os=3&go=GO#)) from the livecd session and then try to install to the hard drive after ubuntu can see the drive on the controller. But now i have now run into another problem:

to compile the drivers, it required that i install the kernel source. so i acquired the packages via synaptic: linux-headers-2.6.15-23, linux-headers-2.6.15-23-386, and linux-source-2.6.15

next i ran: make clean

but it seems unable to find the source/version?:

ubuntu@ubuntu:~/Desktop/ut_mod$ make clean
cat: /lib/modules/2.6.15-23-386/kernel/build//include/linux/version.h: No such file or directory
cd cam; make clean
make[1]: Entering directory `/home/ubuntu/Desktop/ut_mod/cam'rm -f cam_mod.o cam.o cam_ata.o cam_isr.o cam_swap.o cam_var.o cam_fm.o
make[1]: Leaving directory `/home/ubuntu/Desktop/ut_mod/cam'
rm -rf ulsata2.o pdc-ulsata2.o include

where is this version.h file located so that i can point it in the right direction? or is it not necessary and i can continue following the rest of the steps to compile the drivers?

i tried searching in /usr/src/linux-2.6.15/include/linux, and /lib/modules/2.6.15-23-386, but could not find the file there.

thanks for any help.

---

