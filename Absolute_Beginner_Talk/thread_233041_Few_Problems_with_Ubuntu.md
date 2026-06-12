---
title: "Few Problems with Ubuntu"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by RaCeR123 on 2006-08-09
Alright here it goes.
I have used Windows for over 7 years... and now just wanted to have some fun with linux/ubuntu. I downloaded the 64bit version of ubuntu and tried installing it... My First question... I can't see my cursor... i can click and stuff but my cursor is just not there... I can live with it but it is really annoying and take 3 minutes to open 1 window as you could imagine... Secondly I am running 2 Seagate 320 GB Drives in raid0. I made a 20GB partition that i Want to install Ubuntu on... but as soon as I get to where I choose to where to install Ubunutu... I see both my hard-drives with 300gb... but it says its allocated space? how can that be? how come it doesn't recignize my hdd partitions??? thanks

---

### Post by RaCeR123 on 2006-08-09
bump?

---

### Post by GuitarHero on 2006-08-09
The installer should allow you to partition in it.  Also the 64 bit version can be buggy, i would stick to the 32bit.

---

### Post by RaCeR123 on 2006-08-09
yeah i tried that and it still doesn't let me choose... it says i have 2 drives at 320 gb but all allocated space... i can't just erase 1 hard-drive cuz they are in raid0... :(

---

### Post by nalmeth on 2006-08-09
Since you made the partition, that is probably why it sees it as allocated space.

Weird about the mouse.. What kind of video card do you have? If you have Nvidia or ATI, installing their proprietary drivers may solve the problem. I can probably link you to a solution, just post what type of vid card you have. 

Ya, that must be annoying.

---

### Post by RaCeR123 on 2006-08-09
i have a 6800GS video card from Nvidia.. i am on windows right now....

---

### Post by RaCeR123 on 2006-08-09
i also tried to just erase the whole hard-drive with 20 gb... so keep it as allocated space and then just let ubuntu do its thing... but it doesn't want to recignze my the space.... it tells me that i have 2 320 gb hdd's which is correct... after i click let me do it manualy, i get to choose ... then i can actually find the 20 gb patition that i made but i get the error  No Root System Error or w/e when i try to instal it and it cancels the instalation

---

### Post by RaCeR123 on 2006-08-10
i am back on ubuntu so if anyone can help me i'll greatly appreciate it :)

---

### Post by nalmeth on 2006-08-10
I know you've already burned 2 discs, but I've heard so much about partitioning problems on the liveCD, I usually always recommend the alternate install disc, even for new users.

I have to go do a flood right now, I will be back in 15 to try to help you out if you don't want to burn another disc.

---

### Post by RaCeR123 on 2006-08-10
whats the alternate instal disc? nvmd i found it... guess im going back to windows now haha... you'll think it'll work? also i can still have my dual boot with that instal rite?

---

### Post by TheEmb3rEgg on 2006-08-10
You might try downloading GPartEd from sourceforge.net. Boot from the live CD. Make a root partition of about 5gb (I use 10gb) using the ext3 file system. Make a 1gb linux-swap partition and allocate the rest of the space for your files (ext3).

I used the short video clips at linux.com as my reference

[http://tips.linux.com/article.pl?sid=06/07/20/1654251&tid=129&tid=50&tid=131](http://tips.linux.com/article.pl?sid=06/07/20/1654251&tid=129&tid=50&tid=131)

(They could have used another less boring voice to orate that >.<)

---

### Post by RaCeR123 on 2006-08-10
thanks i will try that asap

---

### Post by nalmeth on 2006-08-10
whoops, I took a little longer that I expected, sorry

Gparted is a good idea, I just thought you might want to reduce how many CD's you burn. Gparted is useful though, and is beneficial to have around.

I think the alternate install CD would resolve your problems, if after using gparted, the liveCD still isn't working. 

BTW, do you have another OS on the HD you're trying to install Ubuntu on?

You seem to have great patience with this, it will pay off when you get up and running.

---

### Post by RaCeR123 on 2006-08-10
alright so tried to do the live cd from the program you suggested to make my partitions... well i tried to run it and uhmm after i click 24 bit and 1024X768 i get some really messed up colors and nothing works... its hard to describe what it looked like... u know when you put in a nintendo game the wrong way you get weird colors... well thats wat it looks like...so what can i do... i tried all kind of resolutions and different kind of bits... anyone??? starting to get frustrated with ubuntu and i haven;t even installed it yet [-X

---

### Post by RaCeR123 on 2006-08-10
> **nalmeth said:**
> whoops, I took a little longer that I expected, sorry

Gparted is a good idea, I just thought you might want to reduce how many CD's you burn. Gparted is useful though, and is beneficial to have around.

I think the alternate install CD would resolve your problems, if after using gparted, the liveCD still isn't working. 

BTW, do you have another OS on the HD you're trying to install Ubuntu on?

You seem to have great patience with this, it will pay off when you get up and running.well i have windows xp installed but thats it... thats why i can't format the whole drive... i just want to play around with ubuntu and have some fun :) well I hope i can get this running rather sooner than later :)

---

### Post by nalmeth on 2006-08-10
Ok, so you have 2 HD's, one of them has windows installed, and on the windows drive you are trying to install ubuntu alongside it.

What is on the other drive?

Although it is usually quite safe practice, I personally don't like telling people to resize their windows partition unless their data is backed up, so if it is possible, perhaps it would be best to install on the other HD, with the alternate install disk. 

I would just feel bad if someone lost all their data following my instructions, even if it wasn't directly my instructions at fault.

About the graphical issues, it has something to do with your Nvidia card. I don't know much about them, perhaps it is really new, or really old (unlikely, as support should be better). 

If you manage to get Ubuntu installed, here's a guide for installing the Nvidia drivers (easier than using a script like automatix to do it, hope you aren't adverse to the command line)
Open a terminal (Applications - Accessories - Terminal)
Copy this command, and paste it in the terminal:[FONT=Verdana]
[/FONT]```
sudo apt-get install nvidia-glx linux-restricted-modules-$(uname -r)
```[FONT=Verdana]
then copy and paste this command into the terminal:
[/FONT]```
sudo nvidia-glx-config enable
```
Then reboot

---

### Post by RaCeR123 on 2006-08-10
thanks... for the advise... well see about the 2 HDD... i am running them in raid0 which means they are becomig 1 huge hard-drive which has double the speed of a single drive... if that makes any sense... now i am made some different primary partitions... 1 for windows 2 other for stuff and i made 1 more for linux/ubuntu... so i don't know if i will lose all my data... but i like to take risks... haha... i am gonna try the alternate cd's... if not... then i don't know haha... my graphics card is about 1 year old so not new but also not very old... :/... well i'll try my best :)

---

### Post by nalmeth on 2006-08-10
I see, that's a cool feature, I might look into that.

To be honest, I don't know much about raid0, that's why I was a little hesitant to suggest anything too forward. 

Sometimes windows can be corrupted if it is heavily fragmented when you shrink it. If you want to reduce some of the risk of damage, defrag it a couple of times, and naturally, tread carefully and slowly through the partitioning process.

All that said, it is your computer and data, I hope you are able to install without any damage done :)

---

### Post by RaCeR123 on 2006-08-10
Hey well I tried the alternate disc... and I have the same problem... It just doesn't want to take my raid0. It recognized both Hard-Drives but not the 4 Partitions... I made all Logical Partitions with ext3, swap, and ext3 again. But it can't find it anywhere. It wants to completely reformat 1 of my HDD which I am not willing to do, seeing that it would completely destroy my raid and windows :). I guess I will just have to wait for a later version of ubuntu... :) But thanks for trying to help me anyways :)

---

