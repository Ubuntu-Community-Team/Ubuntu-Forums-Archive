---
title: "Internet Connection"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by AKPAKP on 2008-03-29
Please help me configure my internet on Ubuntu ...
I'm using it now thru my XP now

---

### Post by alexforcefive on 2008-03-29
I think you're probably going to have to be more specific. What kind of connection is it? What does it go through? What doesn't work?

---

### Post by AKPAKP on 2008-03-29
It is a broadband connection connected via modem.....
I dont kno much more.....
Plzz...ask anything more specific i'll try to give you in detail....

Am a newbie so sorry for the trouble

---

### Post by ghost_ryder35 on 2008-03-29
wired or wireless?
What kind of computer (Desktop, Laptop)
Make and Model please (HP 540N?  Dell Latitude 6000?)
Then type this and post the output on to the forum
```
ls pci
```

---

### Post by TeoBigusGeekus on 2008-03-29
Is it a USB modem?
If so type 
```
lsusb
```
in a terminal and post us the output.

---

### Post by AKPAKP on 2008-03-29
Wired connection...
a desktop.....
custom built or assembled comp...
Now i'm using my laptop to connect post u the details from terminal in a short while

---

### Post by Hutom on 2008-03-29
You have dual boot in your desktop?

---

### Post by AKPAKP on 2008-03-29
00:00.0
Host Bridge:ATI Technologies Inc radeon Xpress 200 host Bridge(rev 01)
PCI Bridge:ATI Technologies Inc RS480 PCI Bridge
IDE Interface:ATI Technologies Inc 437A SATA Controller(rev 80)
IDE Interface:ATI Technologies Inc 4379 SATA Controller(rev 80)
{
3 USB controller
}
SMBus:ATI Technologies Inc IXB SB400 SMBus Controller(rev 82)
{
IDE Interface:
Audio device
}
ISA Bridge:ATI Technologies Inc IXB SB400 PCI-ISA Bridge(rev 82)
PCI Bridge:ATI Technologies Inc IXB SB400 PCI-PCI Bridge(rev 82)troller
{
VGA controller
}
Ethrernet Controller: Realtek Semiconductor Co. RTL-8139/8139C/8139C+(rev 10)

---

### Post by AKPAKP on 2008-03-29
no only ubuntu....After installing Ubuntu...I installed Windows but the bios or the Os list is not showing windows

---

### Post by AKPAKP on 2008-03-29
:confused:

---

### Post by TeoBigusGeekus on 2008-03-29
What about
```
lsusb
```

---

### Post by Hutom on 2008-03-29
To have a dual boot you need to install windows first, then Ubuntu and then install Grub boot loader (which is a part of Ubuntu installation). then you will see the list of other OS. 

I am not an expert in network configuration.

Anyway, if you are plugging in and out the same wire(internet) alternatively in your laptop and desktop, then in your Windows-laptop check the values under - IP Adress, DNS servers, netmask. You can see them in Control panel > network connection > propreties.  Put the same values in your Ubuntu-desktop (System > Administration > Network). 

I hope this will work.

Good luck.

---

### Post by AKPAKP on 2008-03-29
I dont use anything other than my mouse & webcam thru my USB

well the result
BUS 003 Device 001: ID 0000:0000
BUS 002 Device 001: ID 045e:0084 Microsoft Corp.
BUS 002 Device 001: ID 0000:0000
BUS 001 Device 001: ID 0c45:607c Microdia
BUS 001 Device 001: ID 0000:0000

---

### Post by AKPAKP on 2008-03-29
i did all that u said earlier itself but the problem is that i have two icons under connections 
\1.Wire conn
2. Modem connection

In modem connection it is asking me Internet service provider data(Phone no. & prefix) is this the normal phone no or some special internet no...

---

### Post by AKPAKP on 2008-03-29
Anyone here

---

### Post by kwacka on 2008-03-29
Open system --> administration  --> network

Highlight the wired connection & click on properties. Click on roaming mode to remove the tick, and select DHCP. Close

Are you now able to connect?

---

