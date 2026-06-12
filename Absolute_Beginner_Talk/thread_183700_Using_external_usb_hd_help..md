---
title: "Using external usb hd help."
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-05-28
Ok i have an external maxtor usb hd. It was set up on a windows machine and stores my entire music collection.

Now i want to transfer some music from it to my linux box.

Can i even do this?

Not knowing where to start, I just plugged it in :)

All the correct options are checked in preferences>removable media.


i plug this code:     cat /proc/bus/usb/devices

and get(among others,but this is the HD)

```
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0d49 ProdID=7110 Rev= 2.03
S:  Manufacturer=Maxtor
S:  Product=OneTouch II
S:  SerialNumber=L40D7NGG
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=32ms

```

so how can i browse and copy stuff to and from my hd????

---

### Post by catlett on 2006-05-28
Does nothing happen when you power on your external drive? I ask because all I ever did was power on and my drive is recognised and has an icon on my desktop. Same thing with usb flash drives, for me.
Is it recognised when you power on and then give this command ```
sudo lsh -C disk
``` See if it is being recognised by your system.

---

### Post by CloudyHaze on 2006-05-28
Nope. Nothing happens when i turn it on.

That code you posted does nothing. (sudo: lsh: command not found)

---

### Post by catlett on 2006-05-28
Is the drive turned on while you boot into ubuntu? Try these 2 and see what they say ```
sudo fdisk -l
``` and then ```
cat /etc/fstab
``` The first is the partitions your computer sees but I don't think it lists externals. That's why I posted the sudo lsh -C disk that one lists all drives it sees, at least for me. The second one is the file the computer uses  at startup. That is the listing of partitions and drives Ubuntu mounts on starttup. 
At least we'll see what it does detect. But if you haven't booted with thewm on, do that first.

---

### Post by CloudyHaze on 2006-05-30
yes the drive is turned on during boot up.

 im not sure it will be viewed as a drive in those contexts? but i will try those codes when i get home tonight.

is there any other general USB commands i should know about?

```
cat /proc/bus/usb/devices
```

the drive is there(see first post)

---

### Post by Jussi Kukkonen on 2006-05-30
[QUOTE=CloudyHaze]Nope. Nothing happens when i turn it on.

That code you posted does nothing. (sudo: lsh: command not found)[/QUOTE]

Should probably be lshw, not lsh.

> is there any other general USB commands i should know about?

sudo lsusb (try with -v and -vv if you want more info )

---

### Post by patrick295767 on 2006-05-30
1/Unplug ur usb device 
2/RePlug ur USB device 
3/type : 
```
sudo bash
dmesg & 
# (read where is ur hdd example : /dev/sdb1)
apt-get -f -y install qtparted
qtparted &
# (read where is ur hdd example : /dev/sdb1)
  
#Then, u'll see where is ur hdd, then
#example :  /dev/sdb1
mkdir /mnt/sdb1 
 
#then, you can mount it /dev/sdb1 to /mnt/sdb1  :-)
# cd /mnt/sdb1 ; ls

```
  
Greetings !

---

