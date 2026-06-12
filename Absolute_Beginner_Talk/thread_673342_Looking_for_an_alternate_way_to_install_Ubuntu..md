---
title: "Looking for an alternate way to install Ubuntu."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-01-20
I have this older computer I am trying to set up for my 29 year old autistic brother. Now please do not get offended by my next sentence as it actually is one of the major reasons I am trying to install Ubuntu Gutsy Gibbon. The only things he would use the computer for would be to look up old places he used to live, check his email, research game shows, listen to game show music, watch game show videos on youtube, and pornography. As I'm sure most of us know, even those who do not look at pornography, Windows and porn do not mix with out constant work being done to the machine. Well, I eventually got sick of fixing his crashing computers and have been using Ubuntu now for a couple of weeks, so I figured hey I'll put Ubuntu on his computer and never worry about it again! Well, he has an HP Pavilon 7845 which has the following stats:


[HTML]Processor:
AMD Duron 850 MHz

Chipset:
VIA KM 133

Bus frequency:
200 MHz

Total cache:
192 KB

Memory:
128 MB SDRAM

Storage:

    *
      20 GB Ultra DMA Hard Drive
    *
      DVD-ROM 16x
    *
      CD-RW 8x4x32 rewriteable drive

Communication

    *
      Modem / Fax 56Kbps, V.90
    *
      10/100BT network interface
    *
      ADSL connection

Video

    *
      Nvidia GeForce2 MX TM
    *
      32MB dedicated video memory

Sound

    *
      Integrated AC&#8217;97 sound solution
    *
      2 Polk Audio premium stereo speakers

Accessories

    *
      HP Internet Keyboard
    *
      PS/2 Scrolling Mouse

Ports and expandability

    *
      5 expansion bays (1-3.5&#8221; internal)
    *
      1 AGP
    *
      3 PCI ( 2 PCI free)
    *
      4 USB Ports (2 in Front)
    *
      1 parallel port
    *
      2 serial ports (1 in front)
    *
      TV out[/HTML]

Now, that's from the HP website says for the stats. However, I know for a fact that it has a Pentium 3 processor in it as the sticker right on the outside states that, and I am using a 40gb hard drive. I'm thinking that perhaps since he recieved this computer in the mail from my father that perhaps he purchased it refurbished at a discount or something. Anyway, it has a VERY slow CD Rom drive and when I boot the live CD it runs the live Ubuntu very slow and keeps freezing before I have a chance to install Ubuntu on it. Being as it is a 40gb hard drive I've installed Tiny XP as a 10 gb partition with no sweat. Being as the installer is text based and I don't have to worry about the slow CD-ROM drive loading all that graphic stuff. Basically what I'm looking for is a text based installer for Ubuntu that will allow me to install Ubuntu on the rest of the hard drive. By the way, Tiny XP: Beast Edition runs fine on it as it, so far, is only running on 50MB of system memory right now. Does anyone have an recommendations? I recently decided that it would probably be best to run Xubuntu: Gutsy on it instead. As far as I know its the lowest system resources using version out. If someone knows a better one please let me know. I should also mention that when I tried using the Ubuntu CD it loads up to the desktop then freezes before it loads any icons. If I try safe graphics mode it freezes before it even loads the desktop. With Xubuntu, it loads the desktop and icons and can sit as long as I want it to. But as soon as I double click on install it freezes. If I try to run it in Safe Graphics mode it freezes before it gets to the desktop, much like it did with Ubuntu. I've tried the OEM install, but I don't much understand it nor has it ever worked on any computer I've ever tried to run it on. I know that once Xubuntu is installed on the hard drive it will run fine. I'm sure of this as Tiny XP runs fine on it. Basically, I'm sure that if I had a text based installer, much like windows has, then it will work fine. I'm at my wits end here, because I'm not going to keep fixin' his computer if I know he's just going to break it again soon in the future. Thanks alot.

Edit: Well, I feel like a complete jack*ss now as I've discovered the "Alternate Install CD" after 5 seconds of google. I promise that from now on out I will research my questions a little longer before i post a thread. Thank you. I was even able to find out why. If anyone is interested. 128mb is enough to support the desktop, but you need 192mb  to run the install. The alternate install CD only requires 64mb.

My aplogies again, hopefully this post though can help someone else with the same situation.

---

### Post by mnemosyne on 2008-01-20
Try the Xubuntu 7.10 alternate cd. It installed fine on my old 650MHz Pentium III box. Make sure you burn the install cd at low speeds too.

---

### Post by Ludford on 2008-01-20
you could try wubi..

It installs ubuntu onto your machine as a dual boot from inside windows. You simply select how much space you want it to take up and the desktop envoronment you want (I recomend Xbuntu becuase it's an old PC) and then it installs it without causing harm to The windwos MBR.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by kwacka on 2008-01-20
Either download the Xubuntu CD, or the Ubuntu server CD. 

The server CD is a text install, at the command after installation install xubuntu using apt-get install xubuntu-desktop

---

### Post by Tyke91 on 2008-01-20
Use the alternate install CD (when you go to the "get ubuntu" page, you will see a box for *alternate installer* . check it and download the ISO to burn.

it is just a text based installer.

---

### Post by whoscheesemine on 2008-01-20
> **whoscheesemine said:**
> 

Edit: Well, I feel like a complete jack*ss now as I've discovered the "Alternate Install CD" after 5 seconds of google. I promise that from now on out I will research my questions a little longer before i post a thread. Thank you. I was even able to find out why. If anyone is interested. 128mb is enough to support the desktop, but you need 192mb  to run the install. The alternate install CD only requires 64mb.

My aplogies again, hopefully this post though can help someone else with the same situation.

Perhaps you didn't see my edit. Thanks anyway for all the support. That's why I love this community so much.

Edit: I am still glad those who responded did respond as I did learn some extra things I did not know about. Thanks alot.

---

