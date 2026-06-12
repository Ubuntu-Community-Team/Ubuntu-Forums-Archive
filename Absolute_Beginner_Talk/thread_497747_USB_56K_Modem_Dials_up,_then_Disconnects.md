---
title: "USB 56K Modem Dials up, then Disconnects"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by SanjoEel on 2007-07-10
Hi Guys. I have feisty installed on an old Gateway and I am trying to get dial up working.  I am not really sure what to do from here. I have a Zoom 56k USB (external) modem, Gnome PPP detects the modem and dials up, then says it's connected, then disconnects after 4 seconds. I'm stumped on this, any help is greatly appreciated! I know it's something simple but I can't figure out WHAT!

---

### Post by Rotaj on 2007-07-10
Hopefully, this thread will help.

[http://ubuntuforums.org/showthread.php?t=427979]("http://ubuntuforums.org/showthread.php?t=427979")

---

### Post by SanjoEel on 2007-07-10
Thanks, not a lot of pertinent info for my modem on those links unfortunately. I have googled my brains out and tried everything I know how to do.
It is a Zoom 2985c 56k USB modem, and all the info I found says it should work just fine.I have tried every setting combo I can. I'm at a loss. It dials up, connects then disconnects after 4 seconds. :frown: Anyone have any suggestions?

---

### Post by Bartender on 2007-07-10
It's a USB modem?  Most of them are not full-hardware.  But you indicate it's dialing, which sure sounds like it is working.  Is it one of those modems with both USB and serial outs?
EDIT:  It doesn't look like a full-hardware modem to me.
[http://www.zoomtel.com/products/alliance_hp_win_ce.html](http://www.zoomtel.com/products/alliance_hp_win_ce.html)
The 2985 data specifically says Agere or Conexant chipset, and says it''ll run Windows but nothing about Linux.  You might be able to get the Agere or Conexant chipset going but that's beyond me...

---

### Post by sailor2001 on 2007-07-10
I would think it's the same as in windows.....go to your mail reader whatever it is and in accounts (I believe that's where it is) is a line with tick box "hang-up after receiving mail"

---

### Post by SanjoEel on 2007-07-10
Got it!
I knew it was something stupid. I ran pppconfig, and chose PAP for the auth. protocol, then I made sure to add @copper.net to my username and now it dials up. Thanks guys, I gathered some info from both of your post to get this working. :guitar:

---

### Post by Bartender on 2007-07-10
Sanjo -
I'm happily surprised to hear you got it working.  I'm trying to maintain a list of modems that do work, especially the ones that exceeded expectations!
Can you give any more details about what you had to do?  
For instance, where did wvdial or gnome-ppp find the modem?  Was it something like ttyUSB0?
Did you have to download drivers?
That would be great if you didn't have to do any really weird stuff that new Linux users would find difficult.

Copper.net seems like a pretty good ISP, glad to hear they're working out for you.

---

### Post by SanjoEel on 2007-07-10
Bartender,
It was auto detected as an analog modem at /dev/ttyACM0 by gnome-ppp. I didn't have to install any drivers. I just plugged it in to a random usb slot and let gnome-ppp autodetect it.Then as I stated before I ran pppconfig, and selected PAP.  In Network Settings the Modem settings are at port /dev/ttyS0 and dial type is set to pulses (for whatever reason). It is set as the default connection. The computer is a Gateway Select 1200. Would any other info be helpful?

---

### Post by Bartender on 2007-07-11
> **SanjoEel said:**
>  In Network Settings the Modem settings are at port /dev/ttyS0 and dial type is set to pulses (for whatever reason). It is set as the default connection. 

Yeah, the Network GUI has been broken since Edgy.  Gnome-ppp is a good replacement.  
Thanks for the reply, I'll make a note of it.  The Zoom is awful expensive, so maybe it is full hardware?  Anyway, glad to hear you're online.

---

### Post by SanjoEel on 2007-07-11
Cool, thanks for your help. BTW I got the Zoom at a thrift store for $3. :lolflag:

---

### Post by Bartender on 2007-07-14
$3!!
Good job.  Dial-up on Linux sucks but at least you didn't have to pay a bunch to get there!

---

