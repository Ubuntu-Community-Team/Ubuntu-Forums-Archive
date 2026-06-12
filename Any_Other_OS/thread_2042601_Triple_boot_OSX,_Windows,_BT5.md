---
title: "Triple boot OSX, Windows, BT5?"
date: 2012-08-15
forum: Any Other OS
---

### Post by theone419 on 2012-08-15
Hi, I am looking into getting the new Macbook pro because of the hardware to price ratio compared to the ultrabooks which use the low ULV processors and cost about 1.5k, so I figured for a couple extra hundred a retina macbook would be the way to go. My question is are there any ways to triple boot OSX. Windows 7/8 & Backtrack 5 with all encrypted partitions? I know you can use bootcamp for win/osx but I wouldn't want to separately encrypt each partition within each OS. There is a nice guide I followed not too long ago for BT5/WIN boot using luks encrypted ext4/swap and truecrypt for windows. It involved chainloading and using Grub for the main loader, the tutorial is below

[HTML]http://www.mathyvanhoef.com/2011/08/backtrack-5-and-windows-dual-boot-with.html[/HTML]So in short Triple boot OSX, BT5, WIN7 on a macbook with everything encrypted except the boot partition ofcourse, is it possible or even practical?

---

### Post by oldfred on 2012-08-15
I do not know Macs, but saw this:

2012 MacBook Air Isn't Trouble-Free On Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTE1ODA](http://www.phoronix.com/scan.php?page=news_item&px=MTE1ODA)


Linux Display Switching Support For Apple MacBooks
[http://www.phoronix.com/scan.php?page=news_item&px=MTE2MDM](http://www.phoronix.com/scan.php?page=news_item&px=MTE2MDM)

---

### Post by theone419 on 2012-08-15
> **oldfred said:**
> I do not know Macs, but saw this:

2012 MacBook Air Isn't Trouble-Free On Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTE1ODA](http://www.phoronix.com/scan.php?page=news_item&px=MTE1ODA)


Linux Display Switching Support For Apple MacBooks
[http://www.phoronix.com/scan.php?page=news_item&px=MTE2MDM](http://www.phoronix.com/scan.php?page=news_item&px=MTE2MDM)

Nice, thanks for the reply. That phoronix one was freshly from today. So by the way it sounds there would be too many problems with the retina. Should I revert to the original macbook pro would I still have these display problems? Also I was strongly looking into the 2012 Sony V3 but once I found out about the RAID0 I was and still am hesitant, looks like we killed two birds with one stone one that one. My third and final choice was the X1 carbon, I wouldent need to worry about the triple boot but driver wise and problems similar to the Vaio Z is something I would need to look out for, Does anyone know if the hardware used in the X1C; fingerprint reader, Wifi, Bluetooth etc... would work with Backtrack 5? If not what patches / drivers would I need to install. Thanks...

---

### Post by oldfred on 2012-08-15
Another link I just saw on Groklaw.

[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

---

### Post by theone419 on 2012-08-17
> **oldfred said:**
> Another link I just saw on Groklaw.

[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

Thank you very much, I bookmarked those tutorials. Looks like linux/osx is very do-able but with the new kernal and hardware from the 2012 mac there are things that need to get sorted out. Does Michael Larabel have a blog or something where I can keep up with him? If you see any triple boot configs with encryption tuts let me know please, Im sure I can figure it out but its nice to have help.

---

### Post by sffvba[e0rt on 2012-08-17
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by BrianBlaze on 2012-08-17
IMHO I would buy a sweet laptop with all intel parts and make a hackintosh... I am currently playign with OSX on vm's and going to work my way to a full triple boot PC haha

---

### Post by theone419 on 2012-08-18
> **BrianBlaze said:**
> IMHO I would buy a sweet laptop with all intel parts and make a hackintosh... I am currently playign with OSX on vm's and going to work my way to a full triple boot PC haha

Nice let me know how it works out or if u need help. What linux distro are you going with? and why go with all intel parts?

---

### Post by ac1d3 on 2012-08-27
> **theone419 said:**
> 

[snip/]

So in short Triple boot OSX, BT5, WIN7 on a macbook with everything encrypted except the boot partition ofcourse, is it possible or even practical?


I managed to do a triple boot of Mac OSX, Windows 8 and a Scientific Linux (should be easier with any other distribution as this one uses quite an old 2.6.32 kernel...). I don't see why you would not be able to follow same guides to encrypt your partition on each OS independently.

I described my experience [here]("http://att.macrumors.com/showpost.php?p=15537212&postcount=752") if it's of any help.

Cheers,
Quentin Casasnovas

---

### Post by pbhound on 2012-08-28
Here is the tutorial that i followed for my MAcbook Pro 5,3 [LifeHacker Triple boot]("http://tinyurl.com/2be5lz9")

I am running win 7, Mac OSX 10.6 (snow leopard), and Ubuntu 10.4 LTS.

no issues what so ever!

---

### Post by theone419 on 2012-08-31
> **pbhound said:**
> Here is the tutorial that i followed for my MAcbook Pro 5,3 [LifeHacker Triple boot]("http://tinyurl.com/2be5lz9")

I am running win 7, Mac OSX 10.6 (snow leopard), and Ubuntu 10.4 LTS.

no issues what so ever!

Thanks for that!, looks like I can combine that with some other tuts and achive what im looking for, Any problems compatibility wise?

---

