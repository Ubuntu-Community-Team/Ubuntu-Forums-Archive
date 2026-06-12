---
title: "[SOLVED] Plz  Plz Plz help me with my wireless issues"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by theharshone on 2007-11-11
Hi
I have a Dlink DWL-G122 rev. b1 (ralink rt2570) usb wireless card. The problem is that gutsy upgraded to the new beta drivers from serial monkey and the legacy drivers will not compile in gutsy. There was an error about this code not being designed for smp in mind. Could some one maybe package an amd64 version of the legacy drivers or help me find a solution to get the beta drivers working? The beta drivers work in opensuse but are really unstable. They lock up my computer every 10 min for 2min. The only distro that has worked for me so far is Mandriva 2008 but that is no where as good as ubuntu ( for me). 
My specs are amd athlon 64 x2 3800+ with 1 gb ram and nvidia 6150 le graphics card. 

i'll try to get the outputs for iwconfig and ifconfig up. Should i post any other outputs? 

Thank You for all you help ( in advance)

---

### Post by HermanAB on 2007-11-11
Go to the ndiswrapper web site and read a bit.  You may have better luck with a Windoze driver.

Cheers,

Herman

---

### Post by theharshone on 2007-11-11
i cant find a 64 bit version of the driver for my wireless card. Also, when i use ndiswrapper, my computer randomly locks up and kernel panics.

Thanks for the speedy reply though.

---

### Post by anewguy on 2007-11-11
You may need to use the 32 bit version.  Also, when using ndiswrapper, be sure to disable any default driver that Ubuntu may have for your card or chipset, and you need to remove your current drivers first.:)

---

### Post by theharshone on 2007-11-11
Can you use a 32 bit ndiswrapper driver for and amd64 install. Last time i tried, i got an error.

---

### Post by theharshone on 2007-11-11
If ndiswrapper doesnt work, then i'll just gibe up and move back to mandriva. :frown::frown::frown::frown:

---

### Post by jingo811 on 2007-11-11
If you use Feisty you could always try this blog tutorial that someone once recommended me
[http://i-eat-noobs.blogspot.com/](http://i-eat-noobs.blogspot.com/)
I did things the hard and dirty way with NDISwrapper.  Distro independent, but I won't have time to work on the wireless tutorial until mid-December so you'll have to settle with that blog.

Or find KevDog in the **Networking & Wireless subforum** he might have the time to properly help you with NDISwrapper.
[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)


On the other hand I have some minutes to spare :-)  What does this Database say about your Wifi device?
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
And what does the NDISwrapper database have to say about your Wifi?
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)


> **theharshone said:**
> If ndiswrapper doesnt work, then i'll just gibe up and move back to mandriva. :frown::frown::frown::frown:
I thought you were saying move back to Montana 	:-D

---

### Post by theharshone on 2007-11-11
> **jingo811 said:**
> 

I thought you were saying move back to Montana 	:-D

:lolflag:

Anyway, i have new hope since i got the native beta drivers working :) but then i get riduculously slow internet speeds.legacy driver still won't compile under gutsy which compiled perfectly under fiesty.

I got the native drivers working by doing
```
ifconfig wlan0 192.168.1.x up
iwconfig wlan0 essid <myessid> key open <mykey>
dhclient wlan0

```

the 192.168.1.x was the part i was missing since i never had to do that in feisty.

Anyway this gives me hope. Also, when i used opensuse, which also uses the beta drivers, i also got really slow speeds. So i still want to get the legacy drivers working. Could someone plz package them? They take less than two minutes to compile. I'll try to compile an older version and hope it works[-o<

THanks for all your replies

---

### Post by jingo811 on 2007-11-11
Sorry I only know how to deal with non-compliant wifi hardware :) that is devices that's not Linux native.  But somebody else should know the answer to your questions.

---

### Post by theharshone on 2007-11-13
I FIXED IT!!!!!!!! Thanks for everyone who replied! I got an edited version of the rt2570 code ( i dont remember where, just google it) and it compiled! So now i can use gutsy to its full potential!

btw, how do i mark this solved?[http://e17-stuff.org/](http://e17-stuff.org/)

---

### Post by jingo811 on 2007-11-14
Edit the Title on you first post by adding [SOLVED] in front of your original title maybe.
There's a simple and advanced mode so you probably have to click the advanced button.

---

