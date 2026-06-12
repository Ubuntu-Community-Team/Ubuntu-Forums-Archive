---
title: "please help me get online"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by ryanav on 2007-08-12
Hi
I'm very new to Ubuntu and need some help.

Yesterday I made the switch from Windows to Ubuntu.
I got "the official ubuntu book" and installed with the disk from the book.  Everything seems to be up and running okay, but I'm having trouble connecting to my wireless internet.

I'm in Edmonton, Canada and my service provider is Telus (high speed over the phone line).  I have a linksys modem and a smc router.  I have a cheap Acer laptop that I bought at the beginning of the year.  

According to the book, there is a "network-manager" which will help me get connected by just pressing icon.  However, I cannot find this icon - am I missing something?

I have called Telus and they do not seen too eager to help me because I'm not using a MS or Apple opperating system.  They suggested I call linksys.  I called linksys, and explained the problem, but they have yet to call me back.

Should I keep looking for the network-manager?  Should I contact Telus or Linksys again?
Can anybody help me?

Thanks,
Ryan

---

### Post by skymera on 2007-08-12
open the teminal and type

```
 sudo network-manager 
```

that will bring up the network admin.
click thr wireless box and select DHCP or static. which ever is used.
click ok.
then tick the box.

it should configure the interface and then u should be online,
maybe do  resytart if it dosen work

---

### Post by shearn89 on 2007-08-12
Is your wireless card made by linksys? Can you open a terminal (applications -> accesories -> terminal), type "lspci" and post the output here.

EDIT: @skymera - the card may not be natively supported.

---

### Post by ryanav on 2007-08-12
When I type in "sudo network-manager " it says "sudo: network-manager: command not found" 
:confused:

---

### Post by lee292 on 2007-08-12
Try clicking on System, select Administration, then select Networking.  That should take you there, also.

---

### Post by skymera on 2007-08-12
> **shearn89 said:**
> Is your wireless card made by linksys? Can you open a terminal (applications -> accesories -> terminal), type "lspci" and post the output here.

EDIT: @skymera - the card may not be natively supported.

indeed i didnt think of that
luckily mine worked out of the box so i dont know how to make ones work,

if it isnt supported.
maybe nDisrapper could help...

---

### Post by AlexenderReez on 2007-08-12
check network system..

> sudo lshw -C network


you should have **network-manager-gnome** package installed to display network manager icons in notification area ....


restart networking..see is there any respon...

> sudo /etc/init.d/networking restart

---

### Post by shearn89 on 2007-08-12
I still think we need to find out what chipset the card is:
"lspci" in terminal, and post here.

---

### Post by ryanav on 2007-08-12
I'm on-line with a different computer, so I'm not sure how to get you the results from my laptop.  Is there anything in particular you want to see and I can type that info out manually?

---

### Post by por100pre1 on 2007-08-12
> **shearn89 said:**
> I still think we need to find out what chipset the card is:
"lspci" in terminal, and post here.

Agree. Ryanav, please type "lspci" (with lowercase L) in terminal and post the results.

---

### Post by shearn89 on 2007-08-12
> **ryanav said:**
> I'm on-line with a different computer, so I'm not sure how to get you the results from my laptop.  Is there anything in particular you want to see and I can type that info out manually?

yes, when you put in "lspci" it will give a whole load of output about cards connected to your computer. Copy out anything that says something about ethernet stuff. One should be your wireless card, another might be your LAN card if you have one.

On second thoughts, you could type in "iwconfig" first to see if the laptop picks up your wireless card.

---

### Post by ryanav on 2007-08-12
> On second thoughts, you could type in "iwconfig" first to see if the laptop picks up your wireless card.

here goes: 

lo   no wireless extensions.

eht0   no wireless extensions.

eth1   IEEE 802.11b/g    ESSID: "linksys"   Nickname: "Broadcom 4318"
Mode:Managed   Access point: invalid   Bit rate=1 Mb/s
RTS thr:off    Fragment thr:off
Link Quality:0    Signal lvel:0   Noise level:0
Rx invalid nwid:0    Rx invalid crypt:0    Rx invalid frag:0
Tx excessive retries: 0  Invalid misc:0  Missed becom:0

sit0 no wioreless extensions.

---

### Post by ryanav on 2007-08-12
lspci results:

0000:08:02.0 Ethernet controller: Realtek Semicinductor Co., Ltd.  RTL-8139/8139C/8139C+ (rev 10)
000:08:04.0 Network Controler:  Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by shearn89 on 2007-08-12
given that it picks up the card in iwconfig, it should let you connect to an access point: go to System -> Administration -> Networking (i think thats it). If you can't find that, open a terminal and type "gksudo network-manager"

EDIT: you can do a final to check to make sure it really is working (if you want) by trying to run a program called "wavemon". Open terminal -> wavemon and see what happens.

---

### Post by ryanav on 2007-08-12
okay - i typed in "gksudo network-manager" 
it then asked form my password and when i typed it in, it brough me back to terminal
when i type it in again, it says command not found

---

### Post by shearn89 on 2007-08-12
can you not get to network-manager at all? In my experience, ISPs aren't helpful at all with regards to Linux.

---

### Post by ryanav on 2007-08-12
nope - can't get to network manager at all

---

### Post by ryanav on 2007-08-12
> **shearn89 said:**
> 

EDIT: you can do a final to check to make sure it really is working (if you want) by trying to run a program called "wavemon". Open terminal -> wavemon and see what happens.

command not found

---

### Post by askantik on 2007-08-12
Hey guys,

I have the exact same card and the exact same problem.  Just know that if you find the solution, you'll help two people :D

BTW, I've tried Wicd and installing Windows drivers (.inf file).  I still couldn't get it to work.  Lookin forward to more help from you nice people :)

---

### Post by shearn89 on 2007-08-12
Hmmm... Trying to install stuff without a direct internet connection is quite tricky. 
Look at this page:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
which is a very good wireless network tool.

You can ignore most of it apart from the "In GNOME, to get the tray icon to automatically appear..." bit, and just download the file here:
[http://wicd.longren.org/pool/feisty/extras/wicd_1.3.1-all.deb](http://wicd.longren.org/pool/feisty/extras/wicd_1.3.1-all.deb)

You may have to install some other stuff if all the dependencies aren't met. To do this, go to google, and type:
```

<packagename> site:http://archive.ubuntu.com/ubuntu/pool/universe/

```
in the search box, substituting "packagename" for the keyword in the packages title (ie libc6 or something)

EDIT: dammit, just looked up. Askantik, did you use Ndiswrapper for the drivers? And blacklist the Broadcom native drivers?

---

### Post by askantik on 2007-08-12
I tried to use ndiswrapper but ended up feeling pretty stupid, so I did a fresh install.  Now I'm at a clean slate.  And I'm not sure how to blacklist...

And my direct ethernet connection IS working, just for the record..

---

### Post by askantik on 2007-08-12
WOOT!  I GOT IT TO WORK!

Trouble is, my home network is WPA-enabled.  It won't connect unless I turn WPA off.  With WPA on, it hangs at "Obtaining IP address" on Wicd.  Here's how I got it to work, and even though I'm an Acer user, I didn't follow the Acer instructions:

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

Start where it says "Dapper and Edgy (and Feisty/Gutsy with ndiswrapper)"

Any ideas why my WPA won't work?

---

### Post by askantik on 2007-08-12
I'm real happy right now.  If you have this card and need to do WPA, follow the first link in my other post, then make sure you can connect to an unsecured network.  If you can, but not connect to a WPA network, go here: [http://ubuntuforums.org/printthread.php?t=197102&pp=75](http://ubuntuforums.org/printthread.php?t=197102&pp=75) and follow magomago's instructions (further down... press CTRL+F and type in magomago)

Hope this helps someone.  After MANY days of screwing with it, it finally works!!!!  BTW, I removed Wicd and using Network Manager now.

---

### Post by shearn89 on 2007-08-13
Glad to know your up and running! It took me ages to get my wireless to work, in part because the techy who set up our AP made it soooo ridiculously secure.... My card should be allowed on it, but it won't let me connect.

---

