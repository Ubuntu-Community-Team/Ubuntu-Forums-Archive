---
title: "I hate Microsoft help me plz"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Vodkayum on 2007-06-23
This is going to be a little long but please read and help.

First off I want free from Windows buggy P.O.S. OS. I used Xandros for a while and liked it but it was still lacking. Then I used Suse and loved it and had no real issues with it but now that they've partnered with Satan I want a new one. Sooo I am on Ubuntu now. I still have XP on another drive and I'd love to never touch that drive again. I went out and bought a new 160 Gig hard drive just for Ubuntu and all the stuff I plan on doing and am ready to put forth the effort of learning. Soo now to my issues...

Issue one I have no sound. I'm using an Asus A8V deluxe Mobo and using the onboard sound. Of course Asus has no Linux support. This is a serious issue and all my other problems are minor annoyances that I can over look but this is a must. Please help me.

I'll post my other minor grievences later they are all easy things that I will try to research on my own and will probably ask for some help here and there but I need my music.

---

### Post by Vodkayum on 2007-06-23
oh and sorry I got latest Ubuntu Feisty 7.04 i think it is.

---

### Post by HotShotDJ on 2007-06-23
[http://seehuhn.de/pages/asus](http://seehuhn.de/pages/asus) was my first hit using asus a8v sound linux on google.  Hope it helps.

---

### Post by Vodkayum on 2007-06-23
OK I read it and it says that my /proc/asound/cards should read 

0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC850 at 0x1000, irq 21

How do I make it do that while not logged on as root?

---

### Post by HotShotDJ on 2007-06-23
Ok... lets see what you've got right now.  Please open a terminal and type: ```
cat /proc/asound/cards
```Post the results here.  I'm heading off to work right now, but will check back in the morning.  Perhaps somebody will happen along to help you out while I'm gone.

---

### Post by Tyke91 on 2007-06-23
to use root permissions, type sudo in front of whatever you need in a command line

---

### Post by Vodkayum on 2007-06-23
I typed your instructions and I have this

0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xfac00000/0xfab00000, irq 18
 1 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC850 at 0x1000, irq 22

---

### Post by Vodkayum on 2007-06-23
Why are there two devices listed?

---

### Post by BobCFC on 2007-06-23
I think that file is output from hardware detection for you to read not a configuration file to edit.   Config files are usually stored in /etc


What happens when you type **alsamixer** can you change the volume?  ALC850 is the name of your Realtek onboard sound chip which you have listed as second device.

---

### Post by DBStevens on 2007-06-23
Vodkayum,

It appears you have two sound cards on your system.   One is on the board and the other is on an add on card.

Which one has speakers attached and which one is selected for output? 

I could attach a couple more to my beast but I'd get confused at my advanced age, I have the same issue (sort of, the wrong one is hooked up when I grab the other) with my two tv cards ;-).

---

