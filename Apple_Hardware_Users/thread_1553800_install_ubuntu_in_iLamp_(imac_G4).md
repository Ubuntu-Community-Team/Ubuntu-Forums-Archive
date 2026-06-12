---
title: "install ubuntu in iLamp (imac G4)"
date: 2010-08-15
forum: Apple Hardware Users
---

### Post by hreggnasi on 2010-08-15
Hello everybody.
I have an older iLamp (iMac G4 1Ghz, 768RAM). It is getting quite outdated and I would like to be able to dual boot between MacOsx and Linux. I am getting more and more interested in Linux and I have used Ubuntu on an older IBM Thinkpad and older eMac. 

I have downloaded desktop editions of Ubuntu 8.04, 9.10 and 10.04. (all** PPC** versions). The problem is that my iMac wont startup from the disks, I have tried to hold down the Option key, Open Firmware and I have tried to put an iso on root on the hard disk( with appropriate files; initrd and vmlinux ) I have reformatted the drive and I have made an "free space" partition and the computer refuses to start up from Linux. So now I am stuck. ( the iMac did startup from one of the CD´s but I don´t remember which one, it froze in the startup process anyway...)

I did this the same way with the aforementioned eMac without any hiccups ( that machine is only running Linux )

Any ideas?

Thanx in advance,

---

### Post by gast0r on 2010-08-16
When it's starting up, try holding down 'c'. Thats what works for my Macbook Pro if I want to boot into a disc. However, it might be a different configuration for older Macs. I have the same Mac as yours in my attic with Ubuntu 8.04 on it, so it's definitely possible.

---

### Post by hreggnasi on 2010-08-19
Well, this doesn´t work. I have a CD that I used to install Ubuntu 10.04 LTS successfully on an eMac yesterday so the CD must be OK. The CD/DVD drive is misbehaving and doesn´t read all inserted disks. So I attached a Macbook Pro via FireWire targed mode and still no luck. I can boot yaboot if it is on the hard disk with Open Firmware. Shouldn´t it be possible to put an iso in the same place as yaboot on the root?

---

### Post by gast0r on 2010-08-19
> **hreggnasi said:**
> Well, this doesn´t work. I have a CD that I used to install Ubuntu 10.04 LTS successfully on an eMac yesterday so the CD must be OK. The CD/DVD drive is misbehaving and doesn´t read all inserted disks. So I attached a Macbook Pro via FireWire targed mode and still no luck. I can boot yaboot if it is on the hard disk with Open Firmware. Shouldn´t it be possible to put an iso in the same place as yaboot on the root?

I'm not exactly the best person to answer that question but by the sound of what your saying, it sounds pretty logical.

---

### Post by hreggnasi on 2010-08-21
After days of frustrating attempts to boot Ubuntu iso images in order to intall it I finally reset the nvram via Open-Firmware. Believe it or not: It worked. This is something I should have done the first day. First hour.

---

### Post by Azyx on 2010-12-07
> **hreggnasi said:**
> After days of frustrating attempts to boot Ubuntu iso images in order to intall it I finally reset the nvram via Open-Firmware. Believe it or not: It worked. This is something I should have done the first day. First hour.

How do you reset nvram?

/Cherrs.

PS. I have problem to boot to cd/dvd, some time it work sometime not...

---

### Post by conal on 2010-12-07
I have had to do this before:

Restart, hold down Command(Apple) + Option(alt) + O + F. as it boots. 

At the Open Firmware prompt type:

> reset-nvram
reset-all


I have also had to flash the PRAM before.

However if your cds' sometimes boot but sometimes not, then might it be the cd's at fault?

---

### Post by Azyx on 2010-12-07
> **conal said:**
> I have had to do this before:

Restart, hold down Command(Apple) + Option(alt) + O + F. as it boots. 

At the Open Firmware prompt type:



I have also had to flash the PRAM before.

However if your cds' sometimes boot but sometimes not, then might it be the cd's at fault?

Yes, It is quite possible. I will try boot from a firewire dvd nest time with
CMD-OPT-SHIFT-DELETE. DO you know what OPT and CMD is on a PC-keyboard?

---

### Post by conal on 2010-12-08
> DO you know what OPT and CMD is on a PC-keyboard? 

Do you have a PC keyboard plugged into a mac? if so I'm not sure it will be correctly detected as you switch on (though you can use it with ubuntu). You could try the windows + alt keys I suppose?

---

