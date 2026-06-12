---
title: "TV on Ubuntu"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Olly1234 on 2006-08-26
Hey everyone, I was just wondering if there is an easy program to install to ubuntu for watching tv, without having to recompile the kernel .... also, is there any tv tuner cards that work with linux? ty :)

---

### Post by annda on 2006-08-26
for starters, see a list (short and rather old) of some tv cards tested under ubuntu:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia)

there are a few programs that will do the job once you have the right card. i can't get mine to work (AverTV PCMCIA for digital tv), but a long time ago i had a PCI Pinnacle PCTV card and it was recognized by many linux distros (i think the standard chipset is more important than the exact make and model).

---

### Post by Jerome36 on 2006-08-26
I have a TV card in my machine.  It's a Hauppauge WinTV 38101 rev. B210.  It's fairly old, but it still works fine.  I'm using a pretty simple program called "TV Time."  If you go to the "Add/Remove" Programs thing, it's listed in the Audio/Video section.  You might have to click a certain checkbox to have it show.  I can't remember, and I'm not in Linux right now

Anyway, the program worked right away, without having to mess with anything.

---

### Post by Olly1234 on 2006-08-26
thanks, been a great help :)

---

### Post by Marcelino on 2006-08-26
I have a Kworld model, based on bt878 chipset. I followed the informations from [http://www.ubuntuforums.org/showthread.php?t=32371&highlight=kworld+tv+tuner](http://www.ubuntuforums.org/showthread.php?t=32371&highlight=kworld+tv+tuner) and works fine (with tvtime).

---

### Post by Omnios on 2006-08-26
I used to use Zapping for my ati tv card but found the volume was not working with the latest 6.06 so now I am using TV time which works right out of the box.

---

### Post by Marsolin on 2006-08-26
[KDE TV]("http://linuxappfinder.com/package/kdetv") and [XawTV]("http://linuxappfinder.com/package/xawtv") are other alternatives in the Ubuntu repositories.

---

### Post by annda on 2006-08-26
BTW: are you guys using any of the cards listed on the Ubuntu Wiki? if not, please take some time time to update the list so that others can have more choice...

of course, I'm not exactly altruistic here, i'm thinking of buying something linux-friendly too.

---

### Post by Drakkor on 2006-08-26
I also have an old Hauppauge WinTV card and with TVTime it works great.
Just tell them at the store, if it doesn't work with Linux you're bringin' it back,lol ! :biggrin:

---

### Post by Marcelino on 2006-08-27
> **annda said:**
> BTW: are you guys using any of the cards listed on the Ubuntu Wiki? if not, please take some time time to update the list so that others can have more choice...

of course, I'm not exactly altruistic here, i'm thinking of buying something linux-friendly too.

If you got an eye on a card and it hasn't been listed on the Ubuntu Wiki, you could ask (or search) on the forum about that card.:)

---

### Post by Drakkor on 2006-08-27
"are you guys using any of the cards listed on the Ubuntu Wik"
Hmmm..... I can't seem to find the specific page you are referring to. 
Have a link ? Thanks :)

---

### Post by deadgobby on 2006-08-27
Myth Tv is a biggie one. 
[https://help.ubuntu.com/community/MythTV?action=show&redirect=MythTV+Guide%3A+Installing+MythTV+on+Ubuntu+6.06+LTS+amd64](https://help.ubuntu.com/community/MythTV?action=show&redirect=MythTV+Guide%3A+Installing+MythTV+on+Ubuntu+6.06+LTS+amd64)
A lot of people love it. I could not get it to work with my TV card I got. I got a cheapo Leadtek one and Kino would not even work with it. There was a couple TV programs that worked. I did mess with it soo much I srewup up the kernal to get it to work. 
Gobby

---

### Post by tzulberti on 2006-08-27
> **Drakkor said:**
> "are you guys using any of the cards listed on the Ubuntu Wik"
Hmmm..... I can't seem to find the specific page you are referring to. 
Have a link ? Thanks :)

This is the link:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia)

---

### Post by christooss on 2006-08-30
I hvae pinnacle card PCTV Rave (Bt878) but it isn't working. I posted a question on video sound forum but no anwser :(

If you think that you can help me please do

---

### Post by Drakkor on 2006-08-30
What TV progams have you used ? eg;xawtv,tvtime ?
Also this may help: [http://www.nikosoft.net/howtos/pinnacle.php](http://www.nikosoft.net/howtos/pinnacle.php)

---

### Post by christooss on 2006-08-30
Forgot to write more :)

When dmesg | grep bttv i get a not of Unknown genreic card then I do

modprobe bttv card=39 and than started tvtime. Tvtime started to crash I don't know. I will try thing on your howto. For now thanks

P.S is /etc/modules.conf in ubuntu etc/modules?

---

### Post by christooss on 2006-08-30
[17179606.872000] bttv: driver version 0.9.16 loaded
[17179606.872000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179606.872000] bttv: Bt8xx card found (0).
[17179606.872000] bttv0: Bt848 (rev 18) at 0000:02:02.0, irq: 201, latency: 32, mmio: 0xe6100000
[17179606.872000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179606.876000] bttv0: gpio: en=00000000, out=00000000 in=00e707df [init]
[17179606.880000] bttv0: using tuner=-1
[17179606.880000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[17179607.308000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179607.312000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179607.316000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179607.316000] bttv0: registered device video0
[17179607.316000] bttv0: registered device vbi0

---

### Post by Drakkor on 2006-08-30
Yeah,unfortunately, I don't think the bt848 chipset is supported (though I could be wrong) as seen in in even a Haupaugge card here: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia)
My card's a bt878
[4294692.518000] bttv: driver version 0.9.16 loaded
[4294692.518000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294692.518000] bttv: Bt8xx card found (0).
[4294692.518000] bttv0: Bt878 (rev 17) at 0000:02:0b.0, irq: 185, latency: 32, mmio: 0xee800000
[4294692.518000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb

---

### Post by btdown on 2006-08-30
Good luck trying to get TV working...I've tried with numerous cards, using various tutorials and could never get any of them to work...

---

### Post by Drakkor on 2006-08-30
I would be patient,a lot of people here (like me) have TV cards that work perfectly with little or no setup required.Maybe someone can answer your question better than I can.Though it could be as I said the bt848 chipset is not supported,but I know there are others out there !

---

### Post by Marcelino on 2006-08-31
> **Marsolin said:**
> [KDE TV]("http://linuxappfinder.com/package/kdetv") and [XawTV]("http://linuxappfinder.com/package/xawtv") are other alternatives in the Ubuntu repositories.

To christooss :
Have you tried those alternatives? If neither those won't work, then... I don't know.
You should double check the bttv module. And try to specify the tuner parameter. Refer to [http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm) for more details.

---

### Post by christooss on 2006-08-31
I tried Xawtv but scantv doesnt find chanells

---

### Post by Marcelino on 2006-09-05
Make sure your Frequency Table is set to your zone. As I see, your zone is... Europe (as mine :) ).

---

### Post by christooss on 2006-09-05
Frequency is set to europe and pal. So there shouldn't be a problem there :)

if noticed that tvtime always freezes the whole system. Hard reset is needed. Same with kdetv

---

### Post by Deker on 2006-09-06
Hi all, I too have a slight problem with TV in Kubuntu.  First off, tvtime works great right out of the box, however, when I enable the ATI 3D driver, tvtime stops working.

ATI X800GT 256 meg
tv card = SAA7133 Phillips Semiconductors.

I have been pretty lucky with Ubuntu/Kubuntu over the past year since I began using it, and have usually been able to figure stuff out, but alas, Im stumped.  Any ideas? 

Thanks.
D

---

### Post by confusimo on 2006-10-01
I also need a new tuner.  I have DD 6.06 64bit Ubuntu.

So like the hauppauge 33801 mentioned here if I got that like of ebay of course or what have you. Would that work without recompling the kernal or adding any files right out of the box.

Or I found a kworld pci based on 878 (KW-TV878RF) on ebay.  But I've rad here more files need to be added.  Seems like a lot of work just to watch tv.

Thanks,
Confusimo

---

### Post by petri on 2006-10-01
When tv is causing problems you sometimes have to add these lines to xorg.conf
```
Option          "VideoOverlay"  "on"
Option          "OpenGLOverlay" "off"

```
or was it first "off" and the second "on" :rolleyes:

---

### Post by confusimo on 2006-10-01
I don't even have a card yet.  That's why I'm trying to determine the better buy.  The hauppauge or the kworld.

---

