---
title: "Spooky Ethernet issue"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by woofjack on 2007-08-07
Hi

I am a complete ubuntu newbie. Last week I installed Ubuntu Fiesty Fawn on a second hand Aopen MX46 U2 micro ATX computer. It has ethernet on the motherboard and I was able to connect to the internet via ethernet to my adsl modem/router without having to do anything but plug the cable in at either end.

After a week of fun with my little fiesty fawn box, I decided I really did need to install XP so I could use Itunes and WOW and felt I did not have the skills to use WINE. I felt like I was betraying myself by installing XP but I went ahead and did, totaly wiping Ubuntu from the HDD. XP took hours to install and patch and so did WoW. The plan was to make the system dual boot.

I gave up in the end and reinstalled Fiesty Fawn and now the ethernet connection to the ADSL does not work - the leds on both ends are not coming on.

I am a complete newbie, havent quite got my head around using terminal yet. Any suggestions for me on what might be wrong and how to fix it?

Jack

---

### Post by xopher_mc on 2007-08-07
Two questions,

Have you tried a different Ethernet cable (and double check there plugged in fully)

Did it work in live Cd?

---

### Post by diablo75 on 2007-08-07
If you are using some kind of on-board Ethernet port (one that is buitl into the motherboard, and is not a separate PCI card) then make sure it is still enabled inside your BIOS.

Also, make sure the Ethernet device is enabled.  If you are in Windows, go to the Control Panel>System>Device Manager and make sure it's not disabled.  In Ubuntu, go to System>Administration>Network and make sure there is a check box next to the Ethernet adapter to enable it.

---

### Post by p_quarles on 2007-08-07
There's one thing I'm not completely clear on from your post . . . when you say you gave up and reinstalled Ubuntu, do you mean that you wiped XP entirely off the drive? Or did you make it into a dual-boot system like you had intended? 

The difference it makes is that sometimes Windows will do funny things with an Ethernet NIC. Like disable it during the shutdown process, so as to prevent waking-on-LAN. 

You should try this, though, and post any error messages you get:
```
sudo ifup -v eth0
```

If that doesn't work, I second the suggestion, though, to try another cable. You might also wish to open up the box and make sure the NIC is securely plugged into the PCI slot. I've dealt with one coming *slightly* loose before, and then refusing to work.

---

### Post by woofjack on 2007-08-09
Thankyou to everybody who responed with helpful information.

I had reinstalled Fiesty Fawn completely wiping away Xp.

I followed the suggestions, checked the cable on another machine, checked the bios, checked
that eth0 was up using sudo as suggested etc.

I then put in a spare pci network card and after disabling the on motherboard  ethernet, I am now connected to the internet. I think the connection is stuffed on the on board internet,

---

### Post by tgalati4 on 2007-08-09
Sometimes the on-board ethernet needs to be reset.  Unplug the computer for an hour.

---

