---
title: "Getting errors trying to mount"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Cubedude04 on 2007-06-26
Hey, I made a topic before asking how to mount my /home drive i can't do it and the ways i try i am getting errors and is really frustrating me oh well =D hear i go

I have set up partitions 

/=the root and is 10gb

/swap=Swap and is 2 gb

/usr=this was an accident i made but it is 5gb

/home=39gb this is where i want to store my files 

When i start up i assume it automatically is using the / root partition. I want to mount my home partition to save all my work to but i don't know how 

I tried using the df -h command which gives me 

/dev/hda1             9.9G  2.2G  7.2G  24% /
varrun                253M  116K  252M   1% /var/run
varlock               253M  4.0K  253M   1% /var/lock
procbususb            253M  108K  252M   1% /proc/bus/usb
udev                  253M  108K  252M   1% /dev
devshm                253M     0  253M   0% /dev/shm
lrm                   253M   34M  219M  14% /lib/modules/2.6.20-16-386/volatile
/dev/mapper/hda4       39G  241M   37G   1% /home
/dev/mapper/hda3      5.0G  2.0G  2.7G  43% /usr

Then i typed 

sudo mount /dev/mapper/hda4 /mnt 

from what i understand as a new user that should make the mnt folder my /home partition or drive. It appears to because when i get the properties to the file it says 39 gb. but when i try and copy files to the folder by dragging and dropping it gives me an error

Error while copying to "/mnt".
You do not have permissions to write to this folder.

What am i doing wrong?

If i am not doing this correctly can someone please give me a step by step idiot's guide to mounting the /home drive

I am still trying my 100% best to learn linux and am grateful for any assistance i might receive

Thankyou in advance :D

---

### Post by arvevans on 2007-06-26
My df -h output looks like this:
[INDENT]arv@k7hkl:~$ 
arv@k7hkl:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             5.7G  4.2G  1.2G  79% /
varrun                300M  224K  300M   1% /var/run
varlock               300M     0  300M   0% /var/lock
procbususb            300M  112K  300M   1% /proc/bus/usb
udev                  300M  112K  300M   1% /dev
devshm                300M     0  300M   0% /dev/shm
lrm                   300M   33M  267M  12% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1             958M   51M  859M   6% /boot
/dev/hda4              29G  4.4G   23G  17% /home
arv@k7hkl:~$ 
[/INDENT]

fstab looks like this:
[INDENT]arv@k7hkl:~$ 
arv@k7hkl:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a6edce3f-86cc-4791-aa87-af36103b38c2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=e95a85a6-b54c-4b8e-a7bb-2603c0c27a01 /boot           ext3    defaults        0       2
# /dev/hda4
UUID=0f38ca0f-4614-4390-90dd-57cf95cfcd77 /home           ext3    defaults        0       2
# /dev/hda5
UUID=ed07b339-7ef1-47c1-81cc-d2a491a996d4 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
arv@k7hkl:~$ [/INDENT]

Maybe that will help.
_._

---

### Post by sargeras on 2007-06-26
I think that you need to be root in order to write to /mnt

I would suggest making a directory inside /mnt (eg. /mnt/home) and the use the following command

```
$ sudo chmod -R u+wrx /mnt/home/ 
```

this will give you read, write, execute permissions on the folder /mnt/home/ directory.

Alternatively, you may be able to chmod /mnt to allow you to write there.  I don't advise that, as other things are sometimes mounted there.

Should you want to make a /home  then  use:

```
$ sudo mkdir /home/USERNAME
$ sudo chmod u+rwx /home/USERNAME
```
replace USERNAME with your name

Hope this helps

---

