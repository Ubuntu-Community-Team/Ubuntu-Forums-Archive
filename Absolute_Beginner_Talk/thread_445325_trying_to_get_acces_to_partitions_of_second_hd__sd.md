---
title: "trying to get acces to partitions of second hd/  sdb 1,2,3"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-05-15
Hi , parted my second hdd in three sdb1,2,3 

but still don't have acces to them , i read a little about it 

when i run 'df -h'

this is my output :
fayaman@takhai-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  3.5G   30G  11% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  112K  506M   1% /proc/bus/usb
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb2              16G  168M   15G   2% /media/disk-1
/dev/sdb1              12G   30M   11G   1% /media/disk-2
/dev/sdb3             9.8G  151M  9.2G   2% /media/disk


so i try fayaman@takhai-desktop:~$ sudo chown -R fayaman:takhai /media/sdb2
(bit confused here) i want to change the owner of the partitions 

but it says chown: cannot access `/media/sdb2': No such file or directory

what am i doing wrong , i want to make sure two other accounts can acces these partitions 

they are all three primary one ext2 , other ext3 
should it be extented and logical instead before being able to acces and change 'owner' of the partitons #-o

---

### Post by firedancer on 2007-05-15
Is there anybody out there , 
i have been reading about similar cases in the forum but i'm having problems 

can anybody rescue me !

Hymnoflife ! or Taurus ! or anybody ?

tried some of the codes but now cat/etc/fstab  and won't even see my second hdb WHY NOT ?

do i need to make them extended and then partition them and not all three primary

is that the reason why the hdb can't be found now ?](*,) #-o

---

### Post by firedancer on 2007-05-16
loosing bit of hope here , just want my three partitions on hdb to be accessible for storing data , etc

two days busy and reading , need to work actually, but i don't want a second hd which i can't acces and store stuff on , tried ohter forums and sites , i know how to partition them , filesystem ,

trying to make them accessible with 'chown'


:-\"  anyone , i'll go ahead already got smarter

---

### Post by lazyart on 2007-05-16
Hmmm... I'm stretching here and not on my ubuntu box but:

> /dev/sdb2 16G 168M 15G 2% /media/disk-1

It's not listed as /media/sdb2, so why try to access it that way?

---

### Post by firedancer on 2007-05-16
how can i copy a file and save it there or work in open office and save it there !

give me a clue ?

---

