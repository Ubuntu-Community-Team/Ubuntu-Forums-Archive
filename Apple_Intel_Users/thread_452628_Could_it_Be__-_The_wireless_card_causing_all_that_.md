---
title: "Could it Be ?? - The wireless card causing all that extra heat"
date: 2007-05-23
forum: Apple Intel Users
---

### Post by anujseth on 2007-05-23
After you've installed ubuntu on the MacBook ([http://ubuntuforums.org/showthread.php?t=452262]("http://ubuntuforums.org/showthread.php?t=452262")) 

and you use the wireless alot like me ... you might have experienced awesome amounts of heat as comapred to Mac OS X. 

The hot spots(quite literally) for me are in the top left and center parts of the mac book. A look on the inside 
([http://www.powermax.com/articles_reviews/article.php?id=26]("http://www.powermax.com/articles_reviews/article.php?id=26")) 
does show thats where the Wifi is. Madwifi does not have a Power On/Off option, so i went back to OS X 
and ran with the wireless switched off. Behold! the operating temperature in OS X also dropped. 


Comments!!

---

### Post by Seamyst on 2007-05-23
That could be it... although I've noticed that OS X runs cooler in general than Ubuntu.  It also has a much better power-management system, running down the battery a lot less.  This suggests to me that Ubuntu has power-usage issues, either across the board or on Mactel.

---

### Post by anujseth on 2007-05-23
It does seem like it ... another reason could be no option to slow down disks in Ubuntu, as in the System Preferences in Mac OS X have an option to put hard disks to sleep when possible. Mac OS X is significantly cooler in general and the battery back up is also more than double. Seems like this fix will need some indepth kick *** study.

---

### Post by Ilove2023 on 2007-05-23
I think that if you remove the modules ath_pci and/or wlan the wifi card will be disabled... (sudo rmmod ath_pci)... (i think it should be the same for bluetooth and so on)

Concerning the speed of the hdd, maybe hdparm or sdparm could do that... it's maybe worthy to take a look ;).
For example, to suspend my usbdisk i do : "sdparm --command=stop /dev/sdb" and the disk stop ;)

---

### Post by ronocdh on 2007-05-23
> **Seamyst said:**
> That could be it... although I've noticed that OS X runs cooler in general than Ubuntu.  It also has a much better power-management system, running down the battery a lot less.  This suggests to me that Ubuntu has power-usage issues, either across the board or on Mactel.
Ubuntu definitely has power management issues! My battery life is lucky to be half in Ubuntu what it is in OS X. You can compensate for this a little by disabling certain Services you don't often use, such as bluetooth (System>Admin>Services). This has helped me out a bit.

The complicating factor for us is that Apple isn't disclosing how the system interacts with the battery; this is evident in the numerous stories about how Vista's battery life, while abhorrent across the board, is even worse on the MacBooks and MBPs. Try with XP; you'll get significantly less time than you would on a comparable machine by Dell or HP.

=/ This is an obstacle for the moment, yes, but I find it fascinating the the wireless card might be causing heat. Good catch! Out of curiosity, are you guys running 64-bit? I've recently installed 32-bit Feisty on my C2D MBP, because I was walking a friend through the process, and wanted to use the same physical CD-R I was giving them, and I think it runs hotter than 64-bit did. Just a thought.

---

### Post by ronocdh on 2007-05-23
> **Ilove2023 said:**
> I think that if you remove the modules ath_pci and/or wlan the wifi card will be disabled... (sudo rmmod ath_pci)...
Agreed, but... then he wouldn't have wireless. ;) It's a very rough fix, but I understand your willingness to address the symptom rather than the cause, especially in this case: sometimes by machine gets so hot I shut down, worrying I'm going to damage something! Or I reboot into OS X, and the fan spins up immediately to full blast; after about 3 minutes, it can shut off because the temperature has been brought down a lot. (I use iStat Pro to monitor temps.)

---

### Post by Ilove2023 on 2007-05-23
Yeah... for sure,  but I said that because anujseth said madwifi hasn't power off option ;) ... clearly it's not a good solution to have internet access ;) ...

Maybe you should report a bug... this branche of madwifi is in development...


by the way, that corner is quite hot on my mac too (i'll try to desactivate the module...)

---

### Post by anujseth on 2007-05-23
Disabling the Bluetooth service is alright for decreasing battery consumption but it makes no impact on the heat. Infact less battery life I can live with a hot system I can't. I used to keep my Dell Latitude machine plugged in for 3 days straight and nothing happened to it (but then again i didn't have a wireless thingy on it). 


@llove2023
Those fixes you suggest I know of, these will massively impact functionality and thats not neat. We
need to do better. I remember seeing this C program on a Math students website which added a power 
on/off option to the madwifi settings. I cant find the damn link now.

---

### Post by Ilove2023 on 2007-05-23
Yes, it's not neat  ... just to test or the time to have a fix ;).

Is it as hot with OSX when the card is working?

---

### Post by ronocdh on 2007-05-23
> **ronocdh said:**
> Out of curiosity, are you guys running 64-bit? I've recently installed 32-bit Feisty on my C2D MBP, because I was walking a friend through the process, and wanted to use the same physical CD-R I was giving them, and I think it runs hotter than 64-bit did. Just a thought.
*Bump...* ;)

---

### Post by Seamyst on 2007-05-23
> **ronocdh said:**
> *Bump...* ;)

Errmmm..... not sure, actually.  How do I find out?  :-k

I know that sometimes the fans will run at full force for several minutes, even when I'm not using it and nothing's running.  Kinda startled me the first couple of times, until I figured out what was causing it.  This never happens to me in OS X.

---

### Post by ronocdh on 2007-05-23
> **Seamyst said:**
> Errmmm..... not sure, actually.  How do I find out?  :-k

I know that sometimes the fans will run at full force for several minutes, even when I'm not using it and nothing's running.  Kinda startled me the first couple of times, until I figured out what was causing it.  This never happens to me in OS X.
Oh, well, it's just about which ISO you installed from! If you aren't sure, try typing **arch** in the terminal, I think that displays it.

---

### Post by Seamyst on 2007-05-23
> **ronocdh said:**
> Oh, well, it's just about which ISO you installed from! If you aren't sure, try typing **arch** in the terminal, I think that displays it.

Yeah, that's what I figured.  It says i686, so that's 64-bit, right?  I just checked the Ubuntu download page and it lists 64-bit AMD and Intel computers, and since mine's a Mactel...

---

### Post by ronocdh on 2007-05-23
> **Seamyst said:**
> Yeah, that's what I figured.  It says i686, so that's 64-bit, right?  I just checked the Ubuntu download page and it lists 64-bit AMD and Intel computers, and since mine's a Mactel...
[Actually...]("http://en.wikipedia.org/wiki/I686") I think it means you're using 32-bit. I've really suspect I got a cooler machine when I was using 64-bit, but I'll have to test in the coming weeks. I have a friend with a MBP 17" who wants Ubuntu, and we set a date next week sometime to do it. I'll give him 64-bit, of course, but that's hardly valid because the hardware and even the case are different. Bah.

Well, just something to keep in mind. Thanks for replying.

---

### Post by anujseth on 2007-05-24
its the 32 bit one ... last time i tried the 64 bit, it had major issues

---

### Post by ivesjd on 2007-05-24
Just an idea. If you thinking that the left side is warmer then the right side, thats because the right side has the dvd drive, the left half of the case is the mobo and such. Not saying that you guys are wrong about the heat ;)

---

### Post by anujseth on 2007-05-24
@ivesjd

Yeah I guess thats another thing, since in my case the DVD is virutally never used. But the cause for concern is the amount of heat when compared to the Mac OS X. The Mac OS X runs a lot cooler and longer.

---

### Post by anujseth on 2007-05-24
You know I guess the whole power thingy here is wrong ... the WiFi specifcally (its getting more than needed) ... I guess apple does not release specs and things are running in a heuristic sort of way. Power management is the issue here.

---

### Post by ivesjd on 2007-05-24
Or ubuntu has decided to overclock you wifi card. lol

---

### Post by anujseth on 2007-05-24
lol .... yeah i'm not so sure ... i don't know much about hardware and HAL ... but this is getting way out of hand ... i mean the heat has forced me back to OS X ... this sucks ...

---

### Post by ivesjd on 2007-05-24
That sucks, maybe it has something to do with the newer wireless n capable card. My macbook is the cd with a/b/g and it is a little bit warmer then OS X, but not unbearable so. And I have it on my lap wearing shorts!  Also, what wifi drivers are you using? madwifi isnt working yet correct?

---

### Post by anujseth on 2007-05-24
no madwifi is working ... thats what i'm using

---

### Post by ivesjd on 2007-05-24
Im so confused about madwifi and the atheros cards, From what I know, the C2D have the atheros chipset. And madwifi works? So what is in the origanal macbooks? Mine has atheros which seems strange to some people. So is it my computer is weird or do all the  macbooks have some form of the atheros chipset?

---

### Post by anujseth on 2007-05-24
no idea ... why dont you open yours and let us all know :)

---

### Post by Ilove2023 on 2007-05-24
Hep, just to say that there is a interesting bug report [there]("http://madwifi.org/ticket/447") about the power management of atheros wifi card

---

