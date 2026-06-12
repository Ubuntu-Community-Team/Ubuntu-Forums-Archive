---
title: "dual boot- xp &amp; ubuntu 7.10- installing ubuntu problem"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by beginner wan on 2008-03-08
good day...

i just installed a fresh Xp in a partitioned HD w/ a capacity of 60GB. i do have 100GB more left.. i plan to use it on ubuntu. i made a partition 99GB(ext3) so i can install ubuntu and 1GB for swap.. the problem is that i cant finish the installation. i cant go farther than typing the computer name and the password (6th step).. it always detect crash report.. it always say that "An application has crashed on your system(now or in the past). and i dont know what to do in order to resolve that problem...:confused:

also, my prolink 9000 usb network adapter cant be detected, that is why i cant connect to the internet using ubuntu... 

i hope someone can help me resolve my problems.. thank you guys!! :):)

-beginner wan

---

### Post by alphaniner on 2008-03-08
I got that same error during an install once, but it was on a 'single boot' system.  Also, I'm pretty sure it happened after step 7, when the installer was setting up the partitions/filesystems.  That said, it turned out to be a memory issue.  I ran the memory tester from the install CD and it picked up quite a few errors.  If you haven't tested your memory and install CD, try that.  I'd recommend testing the CD first, if only because it should take less time.

a9

---

### Post by Duck2006 on 2008-03-08
If it's not your memory you could try a text base install.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by spiderbatdad on 2008-03-08
I think this is a problem with the cd itself. I seem  to remember a similar circumstance on a machine. I got that message and after numerous attempts to resolve, I started getting a "bad sector on disk" message. I thought the hard disk was toast and gave up for awhile. 
Anyway recently I decided to try again. Made a new download and disk...and it worked.

You should verify the md5sum of your .iso, and then after the cd is burned, verify the md5sum of the cd. Doing that is like 98% guaranteed the cd and image are good.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This guide is for an older version, but works fine. Just replace 6.10.iso (whatever) with the name of your download.iso. Remember case matters in linux file names.

---

### Post by beginner wan on 2008-03-08
ok.. thanks for the immediate response.. im going to try it now and update you afterwards.. thanks!!:):)

---

### Post by beginner wan on 2008-03-08
i already installed ubuntu after doing the memory test.. 

the next problem i getting is that i cant connect to the internet.. im using prolink 9000 usb network adapter.. how can i make it work?

---

### Post by alphaniner on 2008-03-08
> **beginner wan said:**
> i already installed ubuntu after doing the memory test.. 

the next problem i getting is that i cant connect to the internet.. im using prolink 9000 usb network adapter.. how can i make it work?

I'm confused.  The memory test shouldn't have 'fixed' anything, just... told you if it was broken.  Well, it's good that it is working nonetheless.

I don't know if usb networking works like ethernet networking.  Try

```
ifconfig -a
```

and post the output.

---

### Post by beginner wan on 2008-03-09
sorry sir, i dont know where i can type ifconfig.. i just installed ubuntu and have n't explored it yet.. i really just want my Usb adapter to work so i can browse and explore the OS and the same time conneting to the internet so i can learn lots of things w/ ubuntu w/ the help of the world wide web....:)

---

### Post by alphaniner on 2008-03-09
Yeah, sorry about that.  On the panel at the top of the screen, go to 'Applications'. then 'Accessories', then 'Terminal'.  Once it is up, type

```
ifconfig -a
```

and post results.  Seeing as how you have no internet on that PC, I'll post mine to give you an idea of what it should look like:

```

[COLOR="DarkOrange"]eth0[/COLOR]      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          **inet addr:192.168.1.151  Bcast:192.168.1.255  Mask:255.255.255.0**
          inet6 addr: fe80::203:47ff:fec8:2f4e/64 Scope:Link
          **UP BROADCAST RUNNING MULTICAST**  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8457 (8.2 KB)  TX bytes:8964 (8.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

```

The most important bits are those I put in bold.  As I said, I don't know much about USB networking.  I found a thread on the forums ([usb network hotplug]("http://ubuntuforums.org/showthread.php?t=2038")) which suggests that instead of [COLOR="DarkOrange"]eth0[/COLOR] you should see usb0, but otherwise things should be similar.  If it sees an interface we can move on to the next step, for which we'll need to know if you use dhcp (automatic configuration) or a static IP address.  In windows-speak, that means did you have your network set to "Obtain an IP address automatically" or "Use the following IP address:".  But we'll get to that after we make sure your device is being seen.

---

### Post by beginner wan on 2008-03-09
hello sir... after typing ifconfig -a.. this are the things that showed up...

[IMG]http://img511.imageshack.us/img511/60/41843180yy4.jpg[/IMG]

what am i going to do next?:confused::confused:

---

### Post by lswest on 2008-03-09
eth0 is your ethernet card, which should work fine.  However, for the USB hub, can you post the output of ```
lsusb
```?

---

### Post by beginner wan on 2008-03-09
sir, here is the code..

[IMG]http://img160.imageshack.us/img160/5820/27197450ai5.jpg[/IMG]

---

### Post by beginner wan on 2008-03-09
what am i going to do next? i really want to use ubuntu.. but it will not be complete w/o internet connection.. :(

---

### Post by lswest on 2008-03-09
just googled the card, and i came up with this:
[http://www.fida.com/download-dc.htm](http://www.fida.com/download-dc.htm)

try the Linux driver, might get it sorted for ya

---

### Post by beginner wan on 2008-03-09
sir, actually it is not a for wireless connection.. the modem has 2 options for connecting to the net. via LAN card and USB.. my NIC seems to have a problem thats why i use usb for my ADSL modem.. but, i'll still try the link that you gave me.. thank you sir for the help.. :)

---

### Post by lswest on 2008-03-09
haha no problem, and you can drop the "sir" i'm only 16 :P

---

### Post by beginner wan on 2008-03-09
ok.. it seems installing some thing in ubuntu takes a lot of time.. its very hard to try something and if it does n't work, reboot... im getting frustrated.. i dont know what am i going to do.. im sorry, i just installed ubuntu yesterday and i have n't explored it yet.. also, i use windows since i learned how to use computer, that's why im having a hard time working on ubuntu.. :(

---

### Post by lswest on 2008-03-09
Well, generally installing stuff is easy, just drivers and such can be rather difficult to install.  So, i just looked at the archive, what you wanna do is extract it to whatever folder you feel like using, then go to the docs folder, and open the en_install.html file in firefox.  That gives you step-by-step instructions on how to install it.  If you have specific questions, feel free to ask

---

### Post by airfire on 2008-03-30
lz help!
I ve followed the rules, ubuntu 7.10 works fine!
but when i try to enter windows a message appears: starting up!!
but nothing happens!? what's wrong? plz help me!!!:mad:

---

