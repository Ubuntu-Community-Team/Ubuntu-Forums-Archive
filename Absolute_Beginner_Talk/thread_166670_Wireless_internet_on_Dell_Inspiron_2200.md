---
title: "Wireless internet on Dell Inspiron 2200"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by darkbullet87 on 2006-04-26
Let me just start out by saying, I currently use Ubuntu on my desktop (dual boot ubuntu/windows) and LOVE it, I haven't booted into windows on it in months. Up until this point I've had Windows on my laptop simply becuase I've heard it's a pain to install Ubuntu on laptops. However, recently Windows on my laptop hase been giving me MAJOR poblems, and I can't even login anymore. So I've been seriously considering installing Ubuntu on my laptop as well. I've been searching around the forum, as well as the Ubuntu Wiki, and have gotten a lot of good info. Specificly from [here]("http://ubuntuforums.org/showthread.php?t=165646&highlight=Inspiron+2200+wireless") and [here]("http://www.ubuntuforums.org/showthread.php?t=25683") However, I'm still unclear about some things. 

1) Seeing as I cannot boot into windows to get the bcmwl5.inf or bcmwl5a.inf files, where can I obtain them from. (as you may or may not know, inspiron 2200's have a "recovery partition" instead of the usual boot disks, so I do not have a boot disk to take the files from) 

2) I've heard that Ubuntu does not support Inspiron 2200's video card. Is this true? And if so, how am i supposed to troubleshoot it if I can't see my screen? LOL

Thanks for any info :)

---

### Post by macdo on 2006-04-26
To address your concerns about display, try a live CD - that should give you a pretty quick answer :-)
As for the wireless card drivers, check out the relevant product website [here]("http://support.dell.com/support/downloads/devices.aspx?c=us&cs=04&l=en&s=bsd&SystemID=INSPIRON%202200&os=WW1&osl=EN")

Let us know how you get on!

---

### Post by darkbullet87 on 2006-04-27
I got the live CD and am running it now. It works fine for my display. So that means it'll be ok when it installs too? 

Also, Is there a way for me to test getting wifi from the live CD? 

oh, and I checked out the website you posted, but all the file formats are .exe

---

### Post by macdo on 2006-04-27
If the display works with the live cd, I see no reason why it should not Just Work (TM) when you install Ubuntu. 

As for the wireless ssue, you can probably make it work with the live CD - just bear in mind that changes only last until the next boot. 
If you're running a broadcom chip (cleverly disguised as a Dell something or other, maybe), then perhaps you can get the drivers you need from another manufacturer who uses the same chip. Google is your friend :-) (I just don't have time).

---

### Post by plexi50 on 2006-04-27
Try entering your wireless connection key and info in the network settings, if the wireless connection shows there, it may have detected the card OK with the kernel drivers and no .inf files will be needed. The WIFI config tools through automatix are a big help, too if you need them.

---

### Post by Papa-san on 2006-04-27
My Dell took a long time to configure for Ubuntu, but this was because of a serious defect in my setup! (The organic link between the keyboard and chair!) Try the links I have in my signature. I am still trying to Get these particular driver files on my site for people to download without the hassles. My endaround was getting the .exe file downloaded to my desktop and using 'file-roller' to open them. This process wasn't seamless, though, and the one time I got it to happen, the drivers were corrupt! I don't know if you can hook your Dell up via a cat-5 wire to your router, but if you can, and install Automatix, the file roller there worked. I got the .exe file from manufacturer site, and worked it that way... 
Good Luck!:D

---

