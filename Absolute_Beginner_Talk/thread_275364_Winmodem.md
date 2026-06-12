---
title: "Winmodem"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by madhu.rox on 2006-10-11
I own a Compaq Presario M2013AP.  I am dual booting WinXP home and Dapper drake. I have access only for a dail up connection. i downloaded the scanModem tool from linmodem.org and did as per instruction and tried to e mail them with the modem.txt file thru connecting to the web using XP but the email Id of theirs:discuss@linmodem.org doesn't seem to work.What should i do to insatll driver for my modem?what is the better way?Thanx](*,)

---

### Post by kevinlyfellow on 2006-10-11
Can you specify which modem you have?  If its a Lucent winmodem, I can help

---

### Post by Sef on 2006-10-11
dupicating what was already posted.

---

### Post by kevinlyfellow on 2006-10-11
This is the absolute beginner talk forum, this person is probably new and isn't familiar with the common threads in these forums.  Besides, a direct instruction of how to install a winmodem often does not work.  I spent a few  years following different sets of instructions before I got mine to work.  So, having installed a lucent linmodem successfully, I think that this method of figuring out how to install it is probably better than following sets of instructions.

---

### Post by az on 2006-10-11
Start here:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by madhu.rox on 2006-10-11
ok..i have a Conexant modem ...well im a compelete newbie to linux ..jus two days...then please tell me all the instruction u encountered b4 u actually won.

---

### Post by Josey on 2006-10-11
If your new to linux like I was when trying to install my winmodem in Dapper the way I got mine to work was with a .deb package for my modem. I would focus on finding one of those instead of trying to install it yourself.

---

### Post by Josey on 2006-10-11
[ftp://ftp.wizzy.com/pub/wizzy/conexant/](ftp://ftp.wizzy.com/pub/wizzy/conexant/)

I would try the larger .deb here and hope I get lucky :)

After installing the package the "detect modem" feature should work.

Someone with more experience with winmodems may have better advice though.


As I said before though. To save yourself hours of frustration as a newb to ubuntu go for the .deb version :)

---

### Post by az on 2006-10-11
> **madhu.rox said:**
> ok..i have a Conexant modem ...

Bummer.  All of the other modem chipsets have freeware drivers.  They are not free-libre open source so they are not distributable by Ubuntu, but they are available.  Conexant charge money for their linux driver.  It would be cheaper for you to go out and buy a modem with another chipset.

---

### Post by madhu.rox on 2006-10-12
Azz..u r absolutely right..my  conexant has no free driver ,however i found one for free in linuxant.com ,but the speed is limited to 14kbps..so u c im typing this post thru ubuntu.and linuxant asks for 19$ for the full version of 56k driver.is there any r option:-| .atleast i am happy that within two days installation of ubunt i got it connected n did not take years.Im totally new as i said first time, im starting to see a working Linux just from 2 days ago.Because here in India and that too my place i don't see any Linux ..there r only Windows not even a single Mac or Linux i have seen.

---

### Post by honda on 2006-10-12
I got my conexant HSF modem to work at full speed (on Dapper) by following 'method A' in this howto:
[http://www.ubuntuforums.org/showthread.php?t=190728&highlight=conexant](http://www.ubuntuforums.org/showthread.php?t=190728&highlight=conexant)
'method B' seemed simpler but it didn't work for me (as I remember, it might actually have been the opposite way, anyway it didn't hurt to try both). And as the howto involves compiling, you have to install the build-essential package (I think it's on the install cd). A reply to the howto also mentions these packages: linux-headers-ARCH, debhelper and fakeroot. I don't actually remember installing those. Or if I did, are they on the cd or not... Anyway they could be downloaded using the linuxant 14.4 kbit driver.

---

### Post by Robfuscate on 2007-03-25
> **Sef said:**
> dupicating what was already posted.

This, I find, is typical of so many 'expert' user's approach to answering questions from 'absolute beginners' .  It's a form of power and control to belittle those with less knowledge. As a first timer on this forum I must say I have seen very little that makes me want to go beyond absolute beginner to basic user - right now I feel like going into 'Sod it who cares, I'll pay to have something that actually works.

See, here's the problem

1/. My modem doesn't work with Ubuntu 6.1.
2/. The only way to fix it is to go online to a forum, or to download a program to check out what sort of modem I have, or to find a link to learn how to install it. I have driven 20 miles to access the 'net in a library to find out how to fix this.

Am I the only person who sees the flaw here? Why isn't the information on how to set up a modem on the CD? It is such an absolutely basic requirement that I can't believe it isn't (cue whiney expert comments about the difficulties of setting up a modem, different makes , types, hardware modems software modems blah, blah, blah!) . This page [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) should not be online, but on the desktop on first install! Along with all its linked pages

This is what the blurb for Ubuntu says:

> " Ubuntu 'Just Works'

We've done all the hard work for you. Once Ubuntu installed, all the basics are in place so that your system will be immediately usable." 

What absolute tosh, those things that actually work - Open Office etc are those which stand alone, anything requiring 'net access doesn't work - that's email/browser/mp3 player (can't download the plug in can I? ) up dates ... oops, I guess that includes open office too - need I go on?

Yours in absolute frustration

---

