---
title: "GUI Will Not Load"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by TGuitar on 2007-09-16
I'm at ropes end.  I wanted to be free of Windows and I can't even get LINUX to work.  I mean it works, but GUI doesn't load so that's as good as dead to me.  I am a complete newbie, so complete that I ask you be patient with me like you would be explaining LINUX to your grandfather. 

I installed UBUNTU STUDIO unto my Gateway MX6629 Laptop.  
I couldn't configure the wireless so updating is out of the question. 

I get the error: NO SCREENS DETECTED, the blue screen comes up and says there was a problem loading the GUI.  

I need step by step very thorough instructions not only on how to get the GUI to work on my system, but even on how to give you guys the info you need to help me get this running.  Like what chipset I have and all that stuff, I just can't understand.  I need someone to treat me like a manequin and tell me exactly what to type and when and where.  

Please I beg you someone help me.  

The GUI is what I want. I don't even care about the wireless, I'll fight with the OS later, when I get the GUI working. 

PS Forgive me if this post is in the wrong section or if this has been addressed already a thousand times somewhere else, I really don't know ANYTHING.  Forgive me and help me, I beg you. Incase I can't find this thread again, my email is [email]Raza_Sogekihei@hotmail.com[/email].

---

### Post by overdrank on 2007-09-16
> **TGuitar said:**
> I'm at ropes end.  I wanted to be free of Windows and I can't even get LINUX to work.  I mean it works, but GUI doesn't load so that's as good as dead to me.  I am a complete newbie, so complete that I ask you be patient with me like you would be explaining LINUX to your grandfather. 

I installed UBUNTU STUDIO unto my Gateway MX6629 Laptop.  
I couldn't configure the wireless so updating is out of the question. 

I get the error: NO SCREENS DETECTED, the blue screen comes up and says there was a problem loading the GUI.  

I need step by step very thorough instructions not only on how to get the GUI to work on my system, but even on how to give you guys the info you need to help me get this running.  Like what chipset I have and all that stuff, I just can't understand.  I need someone to treat me like a manequin and tell me exactly what to type and when and where.  

Please I beg you someone help me.  

The GUI is what I want. I don't even care about the wireless, I'll fight with the OS later, when I get the GUI working. 

PS Forgive me if this post is in the wrong section or if this has been addressed already a thousand times somewhere else, I really don't know ANYTHING.  Forgive me and help me, I beg you. Incase I can't find this thread again, my email is [email]Raza_Sogekihei@hotmail.com[/email].

Hi and welcome, can you tell us some specs on your system like, cpu, memory, video card and such. Also when you get the blue screen that tell you that your xorg is not configured click ok and then it should return you to the command prompt with a login screen. Login with user name and password then you can use this command 
```
sudo dpkg-reconfigure xserver-xorg
```
And if you do not know the answer then leave as the default answer that is given. Then when completed, you will be given the command prompt again and then use the command for reboot
```
sudo shutdown -r now
```
This will reboot your system and hopefully get you to the GUI  good luck!

---

### Post by TGuitar on 2007-09-16
No, it didn't work.  I tried using all the defaults but it still wouldn't load.  
Here are my system specs, the best I can tell you because like I said, I know nothing.  This is what it says on the box:

Gateway MX6629 Notebook

Processor: Intel Pentium M Processor 750 Operates at 1.86 Ghz, 2mb L2 Cache and 533 MHz FSB

Screen:  15.4 Widescreen UltraBrightr WXGA TIFT

Memory: 1024 MB DDR2 Dual Channel Memory

Video:  Intel Graphics Media Accelerator 900

HDD:  100GB , 4200 RPM

Optical Drives:  Multi-Format Double Layer DVD+RW Drive

Memory Card Reader:  4-in-1 Secure Digital (SD) Memory Stick Memory Strick Pro Multimedia Card

Network/Modem:  Intel PRO/Wireless LAN 802.11g , 10/100 built in Ethernet, 56k ITU V.92-Ready Fax Modem

And well, all the ports I'm sure you know already, are standard ports with any laptop.  

That's all I know.

---

### Post by overdrank on 2007-09-16
Ok that is strange, intel graphics are usually pretty good. Were you able to run the live cd at all? And you may try that command again and select intel as your driver or maybe vesa.

---

### Post by TGuitar on 2007-09-16
I already tried vesa.  There was no live CD option. I'd reinstall but my drive is already partitioned up the wing-wang and I have no idea what craziness it would incurr open my already savaged computer.

---

### Post by overdrank on 2007-09-16
> **TGuitar said:**
> I already tried vesa.  There was no live CD option. I'd reinstall but my drive is already partitioned up the wing-wang and I have no idea what craziness it would incurr open my already savaged computer.

Ok well you could download and try the live cd without effecting your system. As for the partitions, when using the live cd you could just install over the top of your existing ubuntu partition. Good luck and sorry to hear of your troubles.

---

### Post by nonewmsgs on 2007-09-16
this was definitely something i didn't care for in ubuntu studio.  i was running ubuntu for months on this computer and then i upgraded to studio and it gave me that error

well good sir.  this is your solution.  the problem sounds like you aren't sure of some of the answers, and i can understand that.  if you can please write down any question to which you aren't sure and we can help you.

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by duhsutter on 2007-09-18
I am having the same problem... I may have access to more video cards, should I try and swap? (I'm dealing with salvaged cpu's so none of them are very good...)

NVIDIA Vanta

---

### Post by overdrank on 2007-09-18
> **duhsutter said:**
> I am having the same problem... I may have access to more video cards, should I try and swap? (I'm dealing with salvaged cpu's so none of them are very good...)

Hi what video card are you using now? Have you used the aforementioned commands and selct vesa as the driver?

---

### Post by duhsutter on 2007-09-18
I think I have a NVIDIA Vanta. (Again, salvaged computer, not really sure... can I find out some how?) I ran through the process, and set it to vesa, rebooted and all. But when I rebooted it gave me the xorg error again. Another thing, When it's loading GRUB (it counts down normally) it just shows 2... I have to hit escape to get a boot menu.

---

