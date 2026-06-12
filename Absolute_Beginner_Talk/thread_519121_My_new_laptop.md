---
title: "My new laptop"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-08-06
I recently  bought a HP laptop (it's the nx7400) ubuntu worked out of the box, except for few things:
1. sleep puts my comp into sleep, however when I wake it up the keyboard doesn't work... (it workes nicely in vista)
2. compiz causes a little bit of distortion (see included picture) it has an intel 950 graphics card and I didn\t install any drivers for it..
3. can't get wifi to work.. I use my isp's settings (static ip, custom ssid), but the interface just seems to be down.. If I try to "ifup" it it gives an error message, if I try to "ifdown" it says the interface's not configured... If I leave only wireless checked (in network preferences) and try to ping anything it says the network is down..

any help is appreciated :)

---

### Post by p_quarles on 2007-08-06
It's very common for laptops to have issues with sleep and suspend in Linux. I hear the newest kernels have better support for this, and that the October release of Ubuntu will incorporate one of the newer ones. 

As for wi-fi, you'll most likely get it to work using NDISwrapper. I've never used it, so can't give you any instructions, but I know there are tutorials and troubleshooting guides to it all over these forums.

---

### Post by motang on 2007-08-06
> **kane77 said:**
> I recently  bought a HP laptop (it's the nx7400) ubuntu worked out of the box, except for few things:
1. sleep puts my comp into sleep, however when I wake it up the keyboard doesn't work... (it workes nicely in vista)
2. compiz causes a little bit of distortion (see included picture) it has an intel 950 graphics card and I didn\t install any drivers for it..
3. can't get wifi to work.. I use my isp's settings (static ip, custom ssid), but the interface just seems to be down.. If I try to "ifup" it it gives an error message, if I try to "ifdown" it says the interface's not configured... If I leave only wireless checked (in network preferences) and try to ping anything it says the network is down..

any help is appreciated :)

Well _congrats_ on the purchase, I too have an HP laptop (1 year old) and Ubuntu works very well on it.  But I found out that sleep mode doesn't work well for me when I bring back the laptop from sleep mode there is video, so I use **hibernate** instead of sleep mode.  
For your compiz issue I would suggest that you try to install the drivers from Intel and that may fix your problem but I am not too sure as I have ATi on my laptop and I don't have compiz turned on by default.  
Getting your wifi working depends on what chipset is used for your wifi card.  First I would find out what chipset it is and lookup on how to install the drivers for it on this forum.  Mine uses *broadcom* and I found how to install *ndiswrapper* from this [forum]("http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+wifi").

---

### Post by kane77 on 2007-08-06
> **motang said:**
> Well _congrats_ on the purchase, I too have an HP laptop (1 year old) and Ubuntu works very well on it.  But I found out that sleep mode doesn't work well for me when I bring back the laptop from sleep mode there is video, so I use **hibernate** instead of sleep mode.  
For your compiz issue I would suggest that you try to install the drivers from Intel and that may fix your problem but I am not too sure as I have ATi on my laptop and I don't have compiz turned on by default.  
Getting your wifi working depends on what chipset is used for your wifi card.  First I would find out what chipset it is and lookup on how to install the drivers for it on this forum.  Mine uses *broadcom* and I found how to install *ndiswrapper* from this [forum]("http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+wifi").

thanx. hibernate works, but I find sleep a little quicker.. but nevermind..

my wireless card uses also broadcom chipset.. does it work ok after installing the ndiswrapper?

---

### Post by motang on 2007-08-06
> **kane77 said:**
> thanx. hibernate works, but I find sleep a little quicker.. but nevermind..

my wireless card uses also broadcom chipset.. does it work ok after installing the ndiswrapper?

Yes wireless works just fine after ndiswrapper!  :-D

---

### Post by kane77 on 2007-08-07
so anybody knows anything about the graphics card and compiz?

---

### Post by kane77 on 2007-08-07
okay now..

for anybody having HP nx7400 laptop, I've managed to get the wireless running using this howto: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092), however I used the drivers for nx7400 instead of the ones the howto suggested (downloaded from HP webpage and extracted using wine)..

If anybody want's the extracted files I can put them somewhere.. (is it legal??)

---

### Post by p_quarles on 2007-08-07
I haven't read the license you accepted when you dowloaded the drivers, but I doubt it allows you to redistribute them. Completely legal, though, to post a link to HP's driver download site and give instructions for how you extracted them with Wine.

---

### Post by kane77 on 2007-08-07
> **p_quarles said:**
> I haven't read the license you accepted when you dowloaded the drivers, but I doubt it allows you to redistribute them. Completely legal, though, to post a link to HP's driver download site and give instructions for how you extracted them with Wine.

I used nothing special, I just wanted to post it to folks who don't have wine.. (like I don't on my 64-bit version).. 
the link for download is: [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)  <--- those are broadcom drivers (windows professional)... they seem to work I haven't done any extensive testing but it iwlist scanning gives me list of AP's so I'd say it works...



plus when I play video when have compiz active the video doesn't play (sometimes it does, but sometimes just display whatever window used to be in front of it.. what might be the cause? what dirver package should i install? (its intel 950 card) what settings should I reconfigure?

---

