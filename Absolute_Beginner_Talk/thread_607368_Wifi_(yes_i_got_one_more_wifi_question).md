---
title: "Wifi (yes i got one more wifi question)"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by COLiNx86 on 2007-11-08
So a couple days ago I installed the bcm43xx-fwcutter driver and my wifi didn't work. Then two days ago it started working perfectly. And then on Wednesday  it stopped working. and by today i had to reinstall feisty  and I have everything I want working, except wifi.

so my computer is [Compaq Presario V6205NR]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00846886&lc=en&cc=us&dlc=&product=3340116") but my wireless card is a Dell Wireless 1390 WLAN Mini-PCI Card. So which driver do I install? The bcm43xx-fwcutter or do I have to use a Ndiswrapper thing?

Also when I had the Bcm43xx-fwcutter I heard that it was better to turn roaming off, But when I would do that it wouldn't even try to connect.

---

### Post by ByteJuggler on 2007-11-08
I don't know if you've got the same broadcom chipset as me, but I'm still using the Windows driver with NDiswrapper with mostly no problems.  I also tried the native driver, but it's not quite complete, and is (so I gather) lacking code dealing with weak signal situations and interference situations.  The net result is that with the native driver it works really well when it works (when close-ish to the access point) and doesn't work at all when the signal is weak.  My laptop won't work in the lounge with the native driver, can't hold the connection, while it does work fine with NDiswrapper (as it did previously with Windows.)  

So moral is, you might want to try the Ndiswrapper route as well.  Make sure you try to get the correct Windows driver for your chipset.

---

### Post by flyingpengwin on 2007-11-08
If it is a hardware issue, then most likely you have what I have.
Your wifi card is going bad and is only working when it wants too. 
Your going to have to replace the wifi card.
Then again I am only a noob and that is only if you are having the exact same problem.
I hope I helped, atleast a little :mrgreen: 

(Edit: I have a HP Pavilion dv6000 notebook, and I am not sure if we have the same wifi card. I'm just trying to help :D )

---

### Post by COLiNx86 on 2007-11-08
Ok thanks both of you. 
Also I doubt it's going bad cause I just got it in April.
should I use [This]("http://ubuntuforums.org/showthread.php?t=297092") guide? even though it's not for my computer but it is for the same card.

---

### Post by flyingpengwin on 2007-11-08
> **COLiNx86 said:**
> Ok thanks both of you. 
Also I doubt it's going bad cause I just got it in April.
should I use [This]("http://ubuntuforums.org/showthread.php?t=297092") guide? even though it's not for my computer but it is for the same card.

I'm sorry i can't help you with the guide, but just to let you know I got my entire laptop in May (2007) and about a week ago the wifi card went bad. But hopefully its a software issue so that it wont cost anything. :D 
(unless you can get another bc of the warranty :mrgreen: )

---

### Post by COLiNx86 on 2007-11-08
Oh ok, wow. it didn't last long (your wifi card I mean) I bet it is just a software thing though.

---

### Post by COLiNx86 on 2007-11-08
Ok so I tried that link I posted but no Luck.
So does ANYBODY have any suggestions on what I should do?

---

