---
title: "Ubuntu recognizes my printer, but printer not printing"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-18
I use Ubuntu 7.04, and have an HP Laserjet 1018. I hooked up the printer via USB, and opened up the "add printer" dialague box in Ubuntu. Ubuntu identified the printer perfectly and added it. When I give the order to print, Ubuntu opens up the print dialogue box and appropriately says it is sending the order to the printer to print. But the printer doesn't give any sign that it got any order at all. It just sits there, and doesn't print. And I know the printer is working fine, because I tried hooking it up to another computer and it prints fine. So what do I do to get the printer to print?

---

### Post by swarup on 2007-06-18
I've been researching the matter on the linux printer database, and came up with the following instructions (for my specific printer -- HP Laserjet 1018) which seem quite good and clear. Just due to my lack of knowledge of terminal, I am not sure how to execute it. Can someone kindly read the below and tell me how to follow it? --i.e. how do I enter the command in a "root shell". Does that mean I first type "sudo bash"? And then is the next item typed separately "getweb 1018"? Or does it get typed in the same command line as what comes after it below? And the ">" sign, is that whole thing which comes before and after it one single command? Thanks!!
 

17 May 2007 - On Ubuntu Feisty, you do not need to download foo2zjs from it's homepage (and recompile it) anymore. Only the firmware is missing in the distribution; to get it just enter this in a root shell (sudo bash): 
getweb 1018 ; arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl
Then power off and on the printer and do the printer setup as usual.

---

### Post by swarup on 2007-06-18
> **swarup said:**
> I've been researching the matter on the linux printer database, and came up with the following instructions (for my specific printer -- HP Laserjet 1018) which seem quite good and clear. Just due to my lack of knowledge of terminal, I am not sure how to execute it. Can someone kindly read the below and tell me how to follow it? --i.e. how do I enter the command in a "root shell". Does that mean I first type "sudo bash"? And then is the next item typed separately "getweb 1018"? Or does it get typed in the same command line as what comes after it below? And the ">" sign, is that whole thing which comes before and after it one single command? Thanks!!
 

17 May 2007 - On Ubuntu Feisty, you do not need to download foo2zjs from it's homepage (and recompile it) anymore. Only the firmware is missing in the distribution; to get it just enter this in a root shell (sudo bash): 
getweb 1018 ; arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl
Then power off and on the printer and do the printer setup as usual.

I tried it, and here below is what happened. Did I do it right?

swarup@swarup-laptop:~$ sudo bash
Password:
root@swarup-laptop:~# getweb 1018 ; arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl
--11:50:54--  [http://foo2zjs.rkkda.com/sihp1018.tar.gz](http://foo2zjs.rkkda.com/sihp1018.tar.gz)
           => `sihp1018.tar.gz'
Resolving foo2zjs.rkkda.com... 82.165.129.11
Connecting to foo2zjs.rkkda.com|82.165.129.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 70,547 (69K) [application/x-tar]

100%[====================================>] 70,547        57.85K/s             

11:50:56 (57.75 KB/s) - `sihp1018.tar.gz' saved [70547/70547]

sihp1018.img
root@swarup-laptop:~#

---

### Post by swarup on 2007-06-18
It's fine. The printer is working perfectly now.

---

### Post by LowSky on 2007-09-12
figured i Would clean up the code

```
 sudo bash 
```

```
 getweb 1018 ; arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl 
```

---

### Post by jperode on 2007-11-03
Thanks a bunch. 
It was a tad dissappointing to know that Gusty could do some great things automatically but couldn't print to a regular HP Laserjet.
Absolutely trouble free now.

Jp

---

### Post by ynef on 2007-11-04
If you get a 404 when you try to use the getweb command now, it's because the author has changed the directory structure on his site. The firmware for the HP 1018 has been moved to [this location]("http://foo2zjs.rkkda.com/firmware/sihp1018.tar.gz") (visited 4th November 2007). The change is that he's moved firmware into a folder called "firmware", as you can see in the URL, if you compare it to what getweb attempts to download.

---

### Post by guga31bb on 2007-11-06
so...what command do we need now?

---

### Post by warjowuch on 2007-11-10
Yeah, i'd like to know either. I am on the edge of buying this printer:)

---

### Post by natehatewindows on 2007-11-10
there are thing all over the forums about it....you just need to search. 

i just got mine to work. cheack out.

[http://ubuntuforums.org/showthread.php?t=602378&highlight=laserjet+1018](http://ubuntuforums.org/showthread.php?t=602378&highlight=laserjet+1018)

[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)


just search this topic, it was the easiest topic i have ever searched to find great info on....the search function is a great tool....use it.

no offense or anything....this topic is just here hundreds of times.

---

