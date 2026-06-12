---
title: "Lost internet"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-09-11
I'm a complete newb to ubuntu, first time using it, first time loading it on a brand new PC.  I installed it, as a dual boot with the windows XP that came with thte system.

When I boot into ubuntu and click firefox, there is no connection.  When I goto system-->network (there is no networking) it only shows an inactive dial-up connection.

Do I need to create a network connection or something?  When I boot into windows it connects fine.

---

### Post by Jamie Jackson on 2007-09-11
Which version of Ubuntu, and are you trying to connect via wireless or wired network?

---

### Post by waste301 on 2007-09-11
Brand new dell desktop. Dual-core, 80 gig hard drive I just repartitioned using the Ubuntu installation software. Connecting with Comcast, no network - I'm plugging the modem into my PC. When I boot into Ubuntu it doesn't see the network.

I'm getting help in the other thread I submitted.  No one was answering this one.

---

### Post by Maestro23 on 2007-09-11
> **waste301 said:**
> Brand new dell desktop. Dual-core, 80 gig hard drive I just repartitioned using the Ubuntu installation software. Connecting with Comcast, no network - I'm plugging the modem into my PC. When I boot into Ubuntu it doesn't see the network.

I'm getting help in the other thread I submitted.  No one was answering this one.

No need to make multiple threads asking the same thing.  Just FYI since you are new on the forums.

---

### Post by waste301 on 2007-09-13
Yesterday, you guys helped me get ubuntu up and running stably on its own partition.  There remains only one more problem - No internet.

When I installed, a warning came up telling me that the installer could detect no network devices on my computer.   

This is a brand new Dell PC specs:

1 223-1769 Vostro 400, Intel Core2 Duo CPU E6550 (2.33GHz, 1333FSB 4MB L2)
1 311-7366 2GB DDR2 SDRAM 800MHz, Dual Channel DT
1 310-9322 Dell USB Keyboard
1 320-5667 Dell 22 inch Wide E228WFP Analog Flat Panel Monitor
1 320-5760 256MB NVIDIA GeForce 8600GT 2DVI
1 341-4988 80GB Serial ATA Hard Drive 7200RPM, 8MB Cache
1 341-4742 No Floppy Drive Requested
1 420-7369 Genuine Windows XP Home
1 420-7243 CyberLink PowerDVD 7.0 DVD Playback
1 310-9440 Windows XP Home backup CD
1 420-7180 Dell Support 3.4
1 420-7286 GOOGLE SEARCH PORTAL ON
1 313-5798 Dell Resource CD, Vostro 400
1 310-9326 Dell Scroll Mouse
1 430-2501 Integrated 10/100 Ethernet
1 313-5469 No Modem Requested
1 420-7275 Adobe Acrobat Reader
1 313-5456 16X DVD+/-RW Drive
1 420-7241 Roxio Creator
1 313-5672 Integrated 7.1 Channel Audio
1 313-5461 No speakers
1 420-7189 DellNetwork Assistant 1.7
1 420-7262 No Pre-installed Security Software
1 420-7280 No Internet Service Provider Requested
1 420-7281 No Pre-installed Productivity Software
1 412-0359 Soft Contracts - Qualxserve
1 983-4250 Warranty Support,Initial Year
1 987-6849 No Warranty, Year 2 and 3
1 983-8540 Type 3 Contract - Next Business Day Parts and Labor On-Site Response, Initial Year
1 988-0387 Dell Hardware Warranty PlusOnsite Service, Initial Year
1 987-7479 VOSTRO,Datasafe 10GB,1YR(Incl w/price)
1 420-7368 Dell DataSafe 2.0 Online, 10GBfor 1 Year Free (for ABU only)
1 960-8851 1YR AUT. PC TUNE UP,VOSTRO, Included in Price
1 420-7367 PC Tune-up, 1 Year (For English OS only)
1 462-4506 Purchase is NOT intended for resell
1 310-8591 You have chosen a Windows XP System
1 310-8977 S and P Drop-in-Box Marcom forBSD Systems Box

Device manager list my network card as Intel(R) 82562V-2 10/100 Network Connection.

It appears to be integrated into the motherboard.  Please help me get online with Ubuntu.

---

### Post by waste301 on 2007-09-13
Bump.  Please help.

---

### Post by w4ett on 2007-09-13
try this solution:

[http://ubuntuforums.org/showpost.php?p=3050436&postcount=4](http://ubuntuforums.org/showpost.php?p=3050436&postcount=4)

12 minutes for a bump?...lol you ARE desperate. :)

---

### Post by mikeyphi on 2007-09-13
Is the network card listed under Preferences/Hardware Information in ubuntu?

---

### Post by waste301 on 2007-09-13
I followed the instructions you linked.

matt@mattspc:~/Desktop$ cd e1000-7.6.5/src
matt@mattspc:~/Desktop/e1000-7.6.5/src$ sudo make install
Password:
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/matt/Desktop/e1000-7.6.5/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_main.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_82540.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_82542.o
s  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_82571.o
u  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_82541.o
do  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_82543.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_ich8lan.o
   CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_80003es2lan.o
m  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_mac.o
od  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_nvm.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_phy.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_manage.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_param.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_ethtool.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/kcompat.o
  CC [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000_api.o
  LD [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/matt/Desktop/e1000-7.6.5/src/e1000.mod.o
  LD [M]  /home/matt/Desktop/e1000-7.6.5/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
gzip -c ../e1000.7 > e1000.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.20-15-generic -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.20-15-generic -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man: 
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.
matt@mattspc:~/Desktop/e1000-7.6.5/src$ sudo modprobe e1000
matt@mattspc:~/Desktop/e1000-7.6.5/src$ 

I tried to open firefox nest.

Still no connection

---

### Post by waste301 on 2007-09-28
Hi - I installed updates as requested, and lost my internet.  What should I do to resolve this?

---

### Post by bruce89 on 2007-09-28
[LIST=1]
[*]Which version of Ubuntu?
[*]Which updates?
[*]How do you connect to the internet?
[/LIST]

---

### Post by Malibu Illusion on 2007-09-28
Which updates?  To what?  Do you have network connectivity?  How are you trying to access the internet?  What is the output of:

```
sudo ifconfig -a
```

Can you ping out to other sites?

```
ping -c3 google.com
```

Which browser are you using?

Providing information is good.

---

### Post by waste301 on 2007-09-28
7.04

a bubble apeared asking to install updates, I did so.  My network card was not originally detected

comcast cable

---

### Post by waste301 on 2007-09-28
> **Malibu Illusion said:**
> Which updates?  To what?  Do you have network connectivity?  How are you trying to access the internet?  What is the output of:

```
sudo ifconfig -a
```

Can you ping out to other sites?

```
ping -c3 google.com
```

Which browser are you using?

Providing information is good.

firefox

---

### Post by bruce89 on 2007-09-28
> **waste301 said:**
> firefox

And the other things that were requested?

---

### Post by waste301 on 2007-09-28
Sorry - I'll have to reboot into ubuntu, which has no internet access.  Are there specific commands I should run from the terminal, and copy to a thumb drive, to give you the answers you need?  I know nothing, noob.

---

### Post by waste301 on 2007-09-28
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

matt@mattspc:~$

---

