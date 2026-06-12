---
title: "how to add xp in grub ?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by nypdz on 2007-06-23
hello , i've seen the already posted threads , but my case is a special one,
my "df" in terminal says this 

Filesystem                                          1K-blocks      Used Available Use% Mounted on
/dev/sda6                                           13092812   2952692   9475032  24% /
varrun                                                1033412        84   1033328   1% /var/run
varlock                                                1033412         0   1033412   0% /var/lock
procbususb                                        1033412       112   1033300   1% /proc/bus/usb
udev                                                    1033412       112   1033300   1% /dev
devshm                                                1033412         0   1033412   0% /dev/shm
lrm                                                       1033412     33788    999624   4% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1                                             96154      7982     88172   9% /media/sda1
/dev/disk/by-uuid/8C38FE3C38FE24BC
                                                             48235160  21799740  26435420  46% /media/sda2
/dev/disk/by-uuid/64707E07707DDFEA
                      14466500   6132228   8334272  43% /media/sda5


my disk system is different from others. but please i would not like to format anything.
 linux apart, i have 3 partitions , sda 1, sda 2 , and sda 5 
xp is loaded in sda5 but after installing linux it says " ntldr missing ",although i "DO" find ntldr on my sda5 partition..

this is my menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0cca4221-c6e5-4d56-8c2c-21e6ce3249e2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault




# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda5
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1



dell inspiron 6400 ; 1.8ghz centrino duo, 2gb ram, 80 gb sata hard disk
please help !

---

### Post by Inxsible on 2007-06-23
Post the output of this command

```
sudo fdisk -l
``` -l is lowercase L

---

### Post by logos34 on 2007-06-23
> # This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda5
title Windows XP Media Center Edition
root (hd0,[COLOR="Red"]**1**[/COLOR]) ------> [COLOR="DarkOrange"]wrong.  change to[/COLOR]** (hd0,[COLOR="Blue"]4[/COLOR])**
savedefault
makeactive
chainloader +1

Try this: 
reboot to the grub menu.  Hit 'e' on the windows line, 'e' again on the 'root' line and change to the above.
Hit enter and 'b' to boot.  If it works edit the windows entry in menu.lst as described above

---

