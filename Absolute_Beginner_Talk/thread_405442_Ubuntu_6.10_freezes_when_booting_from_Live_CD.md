---
title: "Ubuntu 6.10 freezes when booting from Live CD"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Silvo on 2007-04-09
G'day!

I just downloaded the Ubuntu 6.10 Edgy Desktop ISO, and successfully burned it to a CD (the ISO's md5 thing matched and when booting I ran the "check CD for errors" thing, which said there was nothing wrong with it). I boot from the live CD, and it has the loading bar, then it loads three things (there are three icons on a bar in the meddle of the screen). A background is displayed, I can move the mouse, but that is all. It is just that it sits there forever (well, it might eventually do something, but I don't think any booting sequence should take longer than 15min). There are no icons, just the background and the cursor, and the hard drive and CD LEDs on my computer don't flash. 

What is wrong? How do I fix this?

Oh, I tried switching to the text interface and typing: "live noapic nolapic", but this doesn't work either.

---

### Post by overdrank on 2007-04-09
> **Silvo said:**
> G'day!

I just downloaded the Ubuntu 6.10 Edgy Desktop ISO, and successfully burned it to a CD (the ISO's md5 thing matched and when booting I ran the "check CD for errors" thing, which said there was nothing wrong with it). I boot from the live CD, and it has the loading bar, then it loads three things (there are three icons on a bar in the meddle of the screen). A background is displayed, I can move the mouse, but that is all. It is just that it sits there forever (well, it might eventually do something, but I don't think any booting sequence should take longer than 15min). There are no icons, just the background and the cursor, and the hard drive and CD LEDs on my computer don't flash. 

What is wrong? How do I fix this?

Oh, I tried switching to the text interface and typing: "live noapic nolapic", but this doesn't work either.

Hi could you tell us the type of video card you use and any specs on your system will help. Also did you burn the cd as slowly as possible? and just have to ask if you have enough ram 256 mb is the min.

---

### Post by Silvo on 2007-04-09
OK, my system is a Toshiba Satellite A30 laptop. The specs are:

Pentium 4 3.06 Ghz
ATI Mobility Radeon 9000
512MB RAM

the disc was burnt at 8x speed using very good CD-R media. I suppose could have done it slower,  but wouldn't the "check CD for errors" utility have picked up any errors caused by a fast write speed?

Anyway, I hope this helps you.

---

### Post by overdrank on 2007-04-09
> **Silvo said:**
> OK, my system is a Toshiba Satellite A30 laptop. The specs are:

Pentium 4 3.06 Ghz
ATI Mobility Radeon 9000
512MB RAM

the disc was burnt at 8x speed using very good CD-R media. I suppose could have done it slower,  but wouldn't the "check CD for errors" utility have picked up any errors caused by a fast write speed?

Anyway, I hope this helps you.

Ok I had to ask because sometimes the video card may pose a problem but that should not be the case with yours. Have you tried the safe graphics mode on the cd you burned?
If you have or do and it does not work _*I am assuming that you dont want to install and just want to use the live cd.*_ 
I would suggest to try and burn the disc following this how to 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
at the slowest speed you can.
If that still does not work then I am sure that someone can offer better advice!
:popcorn:

---

### Post by Silvo on 2007-04-09
Hmmmm, i did follow that guide, and i remember seeing that the magic number for buning was 8x, which is what i used.

I dont recall having chosen that option, so i will reboot and try it now. If it fails, I dont now what I'll do. 

I did do some mroe tests, and I am able to restart it with ctrl-alt-backspace, which gives me an orange background, and eventually a white box appears in the top left corner. Putting the cursor over it gives the "I" shape cursor (like you are hovering over text), but there is no text in it. 

I am stumped.

---

### Post by Silvo on 2007-04-09
Safe graphics mode doesnt work either.

---

