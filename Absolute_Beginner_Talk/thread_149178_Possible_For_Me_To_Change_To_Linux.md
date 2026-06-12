---
title: "Possible For Me To Change To Linux?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Throne777 on 2006-03-23
I really hate Windows and really want to change to Linux, however, I have a wireless internet and am wondering whether I will be able to change to Linux, i.e. will I be able to install the wireless USB adapter without any knowledge of coding etc?
I'm running a 1.1 ghz processor (it's very painful I assure you), 256MB RAM, 40 gig ish of hard drive space. The adapter is;
802.11g 54MBps USB adapter (US Robotics), model: USR805422
Do I have any hope of being able to get it working without being a computing genius? I.e. I don't know any coding or programming script.
Thanks for any help.

Throne777

---

### Post by pope on 2006-03-23
[QUOTE=Throne777]
I have a wireless internet & wondering whether I will be able to change to Linux...
Will I be able to install the wireless USB adapter without any knowledge of coding?

Do I have any hope of being able to get it working without being a computing genius?
I.e. I don't know any coding or programming script. [/QUOTE]

Dear Beloved son of god "Throne777",

I read your concerns & I want to ask you:

Do you believe in God my Son?

If you believe in God, you can believe in Linux too!!!

There is only one way to find my son, ...just install Ubuntu!

Bless YOU & Ubuntu, 

The Pope.

P.S. > You should not have any problems... if you do, write back... we will help you out!

---

### Post by christhemonkey on 2006-03-23
According to [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"):
> USB: US ROBOTICS USR805422 802.11g Wireless USB Adapter 
Chipset:Unknown 
usbid: 0baf:0118 
Driver: Official U.S. Robotics [http://www.usr.com/support/5422/5422-files/USR5422-v1.0.1.18.exe](http://www.usr.com/support/5422/5422-files/USR5422-v1.0.1.18.exe) rename the archive with a .zip extension, extract the files, then rename all of them to lower-case. 
Other: Works perfect, also the radio, tested on Ubuntu 5.10 kernel 2.6.12, ndiswrapper 1.1-4ubuntu. 
Bug: If the usb adapter is disconnected before the system shutdown the computer freeze, probably kernel panic
So you will need to install ndiswrapper, fairly simple with a little help.

---

### Post by TeeAhr1 on 2006-03-23
Chris, you beat me to it...for the record, Throne777, the page he's referencing is [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29").  Also, here is the [wiki]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto") page on setting up ndiswrapper.  Sorry I'm not more help, but I don't really have any experience with ndiswrapper.  Hopefully someone a little more knowledgeable can jump in here with some pointers...

Pope: Dude, you're real weird.

---

### Post by OBnascar on 2006-03-23
[QUOTE=Throne777]I really hate Windows and really want to change to Linux, however, I have a wireless internet and am wondering whether I will be able to change to Linux, i.e. will I be able to install the wireless USB adapter without any knowledge of coding etc?[/QUOTE]

I love Linux and ubuntu, but if I was you I would wait for the final ubuntu Dapper in June. Of course some people do have sucess with wireless in Breezy and some do not. Some have sucess with using ndiswrapper and some do not. My point is I think ubuntu is the greatess, but for wireless it hasn't in the past "always" worked. It does detect the Ethernet interface right out of the box. I am also running Dapper flight4 and the wireless has really been inproved in that.

Just something to think about....I hope you do try a Linux distro, you will enjoy it Throne777, but don't forget about the effort learning Linux, and again, that is worth it also.

---

### Post by kadymae on 2006-03-23
Wireless support for G standard has gotten much better.

You shouldn't have too many problems, but, if you can wait until June, Dapper should be the most polished Ubuntu yet.

---

In the mean time, if you're really *dying* to start the switch, there are software packages that will allow you to repartition your current Windows XP drive.  If you search the wiki, there are straightforward instructions about how to set up your machine to dual boot.

(I can't be more specific, because I have Apples at my house and my knowledge of the exact programs/techniques is all based on that.)

---

### Post by elmore on 2006-03-23
I'm not sure, but it is possible that Linspire might support your card.  Linspire cost 50.00 us $ to download, but there is usually a coupon floating around that allows you to get it for free(just google it),
if you can try the live cd, go for it.

---

### Post by nalmeth on 2006-03-23
Might work, might not. I'm slightly pessimistic, because I couldn't AT ALL setup a wireless USB. It came down to paying linuxant (a driver company) $20 to get the thing going, and didn't like the idea of paying again for drivers that were already paid for.
Maybe you will have a different experience?
Good luck!

---

### Post by user1397 on 2006-03-23
[QUOTE=Throne777]I really hate Windows and really want to change to Linux, however, I have a wireless internet and am wondering whether I will be able to change to Linux, i.e. will I be able to install the wireless USB adapter without any knowledge of coding etc?
I'm running a 1.1 ghz processor (it's very painful I assure you), 256MB RAM, 40 gig ish of hard drive space. The adapter is;
802.11g 54MBps USB adapter (US Robotics), model: USR805422
Do I have any hope of being able to get it working without being a computing genius? I.e. I don't know any coding or programming script.
Thanks for any help.

Throne777[/QUOTE]
Before trying the install/dualboot, TRY the ubuntu breezy 5.10 live cd and see if your wireless thing works.  Then maybe install it.  No offence but I can't believe someone has not posted this comment yet.

---

### Post by JimS on 2006-03-23
...

I didn't see anyone mention trying the live CD.

If the live CD works, generally Ubuntu will install alright.

If you try it and something doesn't work, ask us.

[COLOR="Red"]JimS[/COLOR]
[COLOR="Blue"]Prostate Cancer Aware[/COLOR]

,,,

---

### Post by Brunellus on 2006-03-23
[QUOTE=JimS]...

I didn't see anyone mention trying the live CD.

If the live CD works, generally Ubuntu will install alright.

If you try it and something doesn't work, ask us.

[COLOR="Red"]JimS[/COLOR]
[COLOR="Blue"]Prostate Cancer Aware[/COLOR]

,,,[/QUOTE]
OP has a USB wlan adaptor that will likely only work with ndiswrapper; his concerns will not be fully addressed by merely using the livecd.

The Livecd will give a fair idea as to other device compatibility, and will be great for learning the interface, but wireless on a livecd is...well...tough.

---

