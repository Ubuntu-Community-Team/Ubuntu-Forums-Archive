---
title: "Gusty Still Freezing!!!"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by championboxes on 2007-11-29
I am still having trouble with gusty freezing... someone told me earlier to disable desktop effects... I did that and it seemed to work for a lil while... but now it is freezing very often... ABOUT 5 TIMES TODAY!!! does anybody know how to fix this? i never had a problem with it in fiesty and i really dont want to go back to fiesty... everything else works very well... heck even my bluetooth is showing up now...

---

### Post by Nano Geek on 2007-11-29
Do you have a Nvidia card and are you using the Restricted Nvidia Driver?

---

### Post by Loki1989 on 2007-11-29
About a week back I was using gutsy and it would lock now I am trying again with another card hoping it goes better this time around with my new card. both are nVidias one a 7300GS the new one a 8600GT.

---

### Post by championboxes on 2007-11-29
Actually yes i am using the nvidia restricted driver... which is weird b/c to get fiesty to work i had to download the binary driver from the nvidia website and install it in the command line just to get the x server to work... but i found another fix that works in gusty but i cant install the nvidia driver that i used for fiesty... btw i have an alienware m9700 laptop with dual 7900 gs's

---

### Post by Nano Geek on 2007-11-30
Yes, unfortunately the Restricted Nvidia drivers that come with Gutsy have a bug that causes them to freeze with certain 7 and 6 series Nvidia cards. 

To fix the problem, uninstall the driver with the Restricted Drivers Manager, and type this into the command-line.```
sudo apt-get install nvidia-glx
```This command installs an older version of the driver that has worked fine for me and should work for you. After that then just reboot and you should be in business.

---

### Post by DensetsuV on 2007-11-30
I found reconfiguring xorg to use the driver rather than trusting synaptic to do the driver install properly fixed the problem for my machine. The nvidia-glx-new driver does work if you configure it yourself.

---

### Post by championboxes on 2007-11-30
Ok I installed the nvidia driver like what was said and i have not had any problems out of it... i will post in a couple days to confirm it...

---

### Post by championboxes on 2007-11-30
Well I just had my computer freeze up again and I had to do a hard reboot... so sudo apt-get install nvidia-glx did not work... does anybody else have any other ideas? I dont really want to go back to fiesty....

---

### Post by Nano Geek on 2007-11-30
That's really strange. I havn't heard of the older Nvidia driver causing computer crashes. Are you running Compiz?

---

### Post by eolson on 2007-11-30
You might try running memtest (think it's option 6 on the grub menu) you may just coincidently have a memory stick that went bad.  Happened to me.

---

### Post by cmileto on 2007-12-01
Its def. the nvidia driver. Im getting same thing, and there are posts about it on nvidia's forums as well.
[http://www.nvnews.net/vbulletin/showthread.php?t=103434]("http://www.nvnews.net/vbulletin/showthread.php?t=103434")

---

### Post by championboxes on 2007-12-01
Um i disabled desktop effects but I did some searching and found out that firefox could be the problem... i have installed seamonkey and i have not had any problems so far... it kinda sucks b/c i really like firefox... ill post a reply in a couple days to confirm....

---

### Post by Nano Geek on 2007-12-01
I have also heard that [this new beta driver]("http://www.nvidia.com/object/linux_display_ia32_169.04.html") has fixed the problem. 
If you need help installing it then just let me know.

---

### Post by championboxes on 2007-12-01
Where my computer is a laptop doesnt that mean I need the geforce go driver? (1.0-9755)

---

### Post by Grafster on 2007-12-01
If this didn't happen to you before (i.e. in Fiesty) then you should consider just installing back to Fiesty and waiting for Hardy.

A Gutsy's introduced a lot of non-solvable issues.
No point in beating yourself up if it's not going to work.

---

### Post by Nano Geek on 2007-12-01
> **championboxes said:**
> Where my computer is a laptop doesnt that mean I need the geforce go driver? (1.0-9755)Yes, it looks like you would. If that's the card you have.

> **Grafster said:**
> If this didn't happen to you before (i.e. in Fiesty) then you should consider just installing back to Fiesty and waiting for Hardy.

A Gutsy's introduced a lot of non-solvable issues.
No point in beating yourself up if it's not going to work.But it can work. I'm using Gutsy just fine with a card that causes crashes. It's best to try to fix problems than to give up when something doesn't work.

---

### Post by championboxes on 2007-12-01
Yeah I really like gusty seeing that most of my hardware works now... with gusty i had all kinds of problems reading and writing to NTFS but gusty solved that for me.... but so far since i have been using Seamonkey i havent had any freezes... but i dont know how firefox could be the problem? i believe that the only thing that doesnt work now hardware wise is my built in webcam... i havent tried very hard to get it to work... and i dont know if dueling monitors works either... but that is for a different day ;)

---

### Post by championboxes on 2007-12-02
Well i am still having problems with gusty... it still freezes... but i think it is due to programs i run... it seems that it will freeze when i use firefox... and also when i use azureus... im really have no clue how i would be able to fix this problem.... other than that gusty seems to run smoothly...

---

