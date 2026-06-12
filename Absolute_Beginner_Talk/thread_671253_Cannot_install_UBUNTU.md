---
title: "Cannot install UBUNTU"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by HRaouda on 2008-01-18
Hi everyone,

I have been trying to install UBUNTU on my HP laptop but I am not getting any results. I managed to burn the ISO image of UBUNTU into a CD. However, when I double click on the same icon from my desktop: I get a pop up for Sonic registration, which basically wants to record the ISO image into a CD. I read somewhere that when you install the ISO image, you should have multiple files inside it but as I mentioned I can not even open it because when I do, it just lunches a recording software.

I took the CD and put it in my XP and I changed the BIOS settings to start from CD and when I reboot, it just starts up windows like nothing is going on. The CD has the ISO image and the size is 695 MB, which is what the actual size is. I tried downloading the ISO on many other CDs and I get the same problem… 

I got so fed up of XP, and I formatted my laptop because I don’t even want to partition anymore, I’ll be happy with only UBUNTU running on my machine but I just can not manage to start the installation.

I would appreciate any help on that.

thanks

---

### Post by KMW on 2008-01-18
What did you burn it with and how did you burnit?

I think you burned it as a wrong file type.

---

### Post by hyper_ch on 2008-01-18
you need to burn it as image file.
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by HRaouda on 2008-01-18
You guys are righat... I gave the task of burning the Image file to my employee at work and she said she did but today i went and sat next to her and asked her to show me what she did, she obviously copied it as a data cd.

Now my next question. 
If I burn it properly and go home and install it with no WINDOWS at all. Is it easy to get connected to the internet afterwards? Or do I need to have some sort of setups and setting changes involved. 


Guys you rock with these helpful and fast responses.

Screw gates and his crappy windows! :)

---

### Post by FuturePilot on 2008-01-18
The beauty of the live CD is that you can test most things out, right on the Live CD including your internet connection.

---

### Post by HRaouda on 2008-01-18
Thanks man. 

How about anti-viruses? Do I need to download any in particular?
Cuz after this point if I get any more viruses, I will throw my laptop in some river, quit work and become a farmer so that i don't have to ever deal with viruses! lol

---

### Post by FuturePilot on 2008-01-18
No, Linux does not need Antivirus
See here for an overview of security
[http://www.psychocats.net/ubuntu/security#firewallantivirus]("http://www.psychocats.net/ubuntu/security#firewallantivirus")

---

### Post by lswest on 2008-01-18
one word of warning though, HP is incredibly fond of broadcom, which might leave you with a few issues, but ethernet should work if you need it

---

### Post by KMW on 2008-01-18
Well done and best of luck with it.

Most Linux users do not use AV as most feel it unneeded, unless it is with a dual boot with Windows.

---

### Post by FuturePilot on 2008-01-18
> **lswest said:**
> one word of warning though, HP is incredibly fond of broadcom, which might leave you with a few issues, but ethernet should work if you need it

My HP has an Intel wireless card.

---

### Post by HRaouda on 2008-01-18
I am planning to connect wirelessly through my wireless card to a network that originates from a windows XP pc. Not sure if this will create any troubles, I just got my router yesterday and today is the big day.

any tips? 

I have an HP ZD7040 model btw.

---

### Post by asmiller-ke6seh on 2008-01-18
> **lswest said:**
> one word of warning though, HP is incredibly fond of broadcom, which might leave you with a few issues, but ethernet should work if you need it

Just to make this clear: if you are going to use a wireless Internet card, you might find that the laptop you have uses a BROADCOM chip set - Ubuntu does not natively support most (if not all) BROADCOM wireless chip sets ... it requires the installation of NDISWrapper to support the Windows driver for that wireless card.

However, if you use a hard-wire Internet cabled connection, it should work faultlessy without any messing around.

I hope that gives you confidence to try running Ubuntu off of the LiveCD before deciding to make the commitment to an installation to your HP laptop.

There is little to no evidence that anyone has ectually experienced a viral infection on a Linux system that has cuased any kind of significant damage. However, you might want to use CLAMAV as an antivirus measure to clean your emails of (Window$) viruses so that you do not send them on to your friends and aquaintances who are unfortunate enough to still be using Windoze.

---

### Post by sowelie on 2008-01-18
I have an HP laptop with broadcom wireless. In gutsy it works flawlessly, I just had to install the restricted driver.  You can do this by going to restricted driver management, system -> administration  -> restricted drivers manager.

---

### Post by hyper_ch on 2008-01-18
why not dualboot first?

---

### Post by HRaouda on 2008-01-18
I guess I would need to be connected to install the restricted drivers don't I? :)

---

### Post by antisocialist on 2008-01-18
> **hyper_ch said:**
> why not dualboot first?
i didnt dual boot at first and i am glad i didnt i would still be learning slowly about linux, if you completely get rid of windoze then you learn linux much quicker, as a result i have already written a beginners guide to the terminal (see my sig) after just 4 months of linux
> **HRaouda said:**
> I guess I would need to be connected to install the restricted drivers don't I? :)

yes you would, connect your laptop via a cord to your router, then run the restricted driver manager get your restricted drivers and you will be good to go

---

### Post by huntis619 on 2008-01-18
Well I have a hp laptop also. It took me 5 days to get everything installed. If you go to the search this forum and type in my name you may find some info for you. I have a windows xp disk so I did a clean install of ubuntu. I downloaded the iso from the ubuntu and burned it using nero 6. Then I burned 2 additional copies just in case. Again search under huntis619. I had problems with my wireless connection and drivers for my nvidia.

---

