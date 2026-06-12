---
title: "what version kernal am i using?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-08
im running dapper. how can i tell what my version of the linux kernal is and if it contains the the hidp.ko kernel module necessary for supporting the bluetooth HID profile.

thanks

---

### Post by el_itur on 2006-09-08
try running "uname -a"  on your terminal, that will tell you the kernel version you are using.
About the other thread I cant help you since I have no blue tooth. you can try "ls hidp.ko", but I dont remember the way to show the kernel module.
Have luke.

---

### Post by Miademora on 2006-09-08
To find your kernel version type

```
uname -a
```

To test if the module can be loaded try

```
modprobe hidp
```

and to see if it is successfully loaded use

```
lsmod | grep hidp
```

At least modprobe might require the use of sudo.

---

### Post by jinxjinx on 2006-09-08
ok i did what you said:

freeth@nephroid:~$ uname -a
Linux nephroid 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
freeth@nephroid:~$ modprobe hdip
FATAL: Module hdip not found.
freeth@nephroid:~$ 

do you know how i can install the module? 

when i do a locate i find something...

freeth@nephroid:~$ locate hidp.ko
/lib/modules/2.6.15-23-386/kernel/net/bluetooth/hidp/hidp.ko
/lib/modules/2.6.15-26-386/kernel/net/bluetooth/hidp/hidp.ko

thanks

---

### Post by Miademora on 2006-09-08
Think i wrote it wrong then.

```
sudo modprobe hidp
```

or maybe

```
sudo insmod /lib/modules/2.6.15-26-386/kernel/net/bluetooth/hidp/hidp.ko
```

---

### Post by jinxjinx on 2006-09-08
ok i ran those commands.

[email]freeth@nephroid:~/.cair[/email]o-dock$ sudo modprobe hidp
[email]freeth@nephroid:~/.cair[/email]o-dock$ lsmod | grep hdip
[email]freeth@nephroid:~/.cair[/email]o-dock$ sudo insmod /lib/modules/2.6.15-26-386/kernel/net/bluetooth/hidp/hidp.ko
insmod: error inserting '/lib/modules/2.6.15-26-386/kernel/net/bluetooth/hidp/hidp.ko': -1 File exists
[email]freeth@nephroid:~/.cair[/email]o-dock$ 


im not sure what that means though. nothing seemed to happen after modprobe hidp or lsmod |grep hdip

do i have the mod installed and working?
thanks! = )

---

### Post by Miademora on 2006-09-08
it is 

```
lsmod | grep **hidp**
```

not

```
lsmod | grep **hdip**
```

---

### Post by jinxjinx on 2006-09-08
i guess this means its here...

[email]freeth@nephroid:~/.cair[/email]o-dock$ lsmod | grep hidp
hidp                   31744  2 
l2cap                  26244  10 rfcomm,hidp
bluetooth              49892  6 rfcomm,hidp,l2cap,hci_usb


now i just need to figure out how to get my bluetooth keyboard to work  : (

---

