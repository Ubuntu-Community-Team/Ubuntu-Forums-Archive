---
title: "LimeWireLinux installation"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by lauzsta on 2006-07-26
Im sorry for all these noobie questions but I havent a clue how to install this. I have downloaded it and its in .bin form. But I dont know where to go from here.

---

### Post by IrishGangsta on 2006-07-26
where did u get it from? 
is it the RPM package?

---

### Post by lauzsta on 2006-07-26
No its just .bin

got it from [http://www.gnutella.com/connect/java/clients/9](http://www.gnutella.com/connect/java/clients/9)

---

### Post by IrishGangsta on 2006-07-26
We are using Ubuntu Linux, which is Debian base.
I was not aware that LimeWire was available for debian based linux's
The problem is that this LimeWire may be RedHat Linux based, there fore will not work on Ubuntu.
I just downlaoded it myself and it could not detect character decoding and what not.

I hope i am wrong b/c i also would like to use LimeWire here on Ubuntu.


Otherwise use Frostwire.  
and downlaod the .deb package from  [www.frostwire.com](www.frostwire.com)
It is similiar to limewire but i like limewire better to tell u the truth

---

### Post by lauzsta on 2006-07-26
I just installed frostwire, i clicked it and it doesnt open :(

---

### Post by IrishGangsta on 2006-07-26
I just opened Frostwire and my laptop froze.
Frostwire isnt that good. But it will get you by for now

Go to your terminal 

Applications > Accessories > Terminal

and type Frostwire

hit enter

and frostwire should open

---

### Post by IrishGangsta on 2006-07-26
Actually, i have a problem as well.
It seems that everytime i open Frostwire, my laptop freezes
This just started happening out of no where 5 minutes ago

---

### Post by justinflavin on 2006-07-26
> **IrishGangsta said:**
> We are using Ubuntu Linux, which is Debian base.
I was not aware that LimeWire was available for debian based linux's
The problem is that this LimeWire may be RedHat Linux based, there fore will not work on Ubuntu.
I just downlaoded it myself and it could not detect character decoding and what not.

I hope i am wrong b/c i also would like to use LimeWire here on Ubuntu.


Otherwise use Frostwire.  
and downlaod the .deb package from  [www.frostwire.com](www.frostwire.com)
It is similiar to limewire but i like limewire better to tell u the truth

you can find Frostwire on the Ubuntu repositories. Use that version.

from the command line:

sudo apt-get install frostwire

that will install the official, tested, and approved Ubuntu package version of Frostwire.

---

### Post by Perfect Storm on 2006-07-26
Limewire:

1. Make sure you have Java sun 1.5 installed.

2. Download the .rpm file of Limewire to your Desktop.

3:
```
sudo apt-get install alien
cd Desktop
sudo alien -i LimeWireLinux.rpm

```

Note: It's not all .rpm package you can convert and use, but with Limewire there's no problem.

[quote=lauzsta]I just installed frostwire, i clicked it and it doesnt open [/quote]
You need java 1.5.

---

### Post by IrishGangsta on 2006-07-26
wow, i tried getting limewire on here a while ago, i did now  know about this alien conversion thing.

Well now i have Limewire which is way better then frostwire.
thanx

---

### Post by deadgobby on 2006-07-26
If you are looking for a easy P2P, you can install GTK Gnutella. This program all so goes into other p2p on the Gnutella.

---

### Post by adam.tropics on 2006-07-26
> **IrishGangsta said:**
> 
Well now i have Limewire which is way better then frostwire.
thanx

Except now you have 'upgrade now' reminders everytime you start it, and a pogram that may be headed down the DRM aisle. Thankfully the developers at Frostwire, which currently incedentally is almost the same as Limewire, have [sense.]("http://www.frostwire.com/?module=about")

---

### Post by IrishGangsta on 2006-07-26
i also have Apollon, but when i try to start it, it never connects. 
Someone told me that apollon is pretty good as well. But can anyone help me get it working?

---

### Post by deadgobby on 2006-07-28
This is how I got Frostwire working.
[http://ubuntuforums.org/showthread.php?t=165371](http://ubuntuforums.org/showthread.php?t=165371)

---

### Post by locoHost on 2006-08-11
Not working for me :-(

Got Java 5.0 with the update manager. That installed fine.

In terminal, I did the steps above. Alien installed fine but the LimeWire RPM aparently doesn't install correctly. It runs, the drive light goes for a bit, then the terminal line clears as if it's finished. I look in the Internet menu and see LimeWire, but clicking it does nothing. What have I missed?

---

### Post by BatteryCell on 2006-08-12
For a64 users this works:
[http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_Gnutella_Client_.28LimeWire.29](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_Gnutella_Client_.28LimeWire.29)
I tried the rpm but since it's i386 alien threw me some errors.

---

