---
title: "Ubuntu feisty installed with no sound"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Hackza on 2007-04-25
Hey,

I've been a windows user for years so bear with my lack of linux knowledge. I've downloaded the iso and ran the install of ubuntu feisty desktop, done as a dual boot with windows. everything seems to work, I've got hold of my windows ntfs I think it is partitions data, I've got beryl working with my nvidia geforce 6200 LE card, codecs and installing things like wine seems great and easy. 

I'm just lacking sound. Now I may be a complete beginner at linux and havnt had problems with sound as its all so plug and play but I have had a good poke about sites but I guess I just dont know what I'm looking for or how to word it. I've ran this in terminal:-

sudo asoundconf list
Password:
Names of available sound cards:
Intel

I dont know my sound card to be honest, not exactly a tech genius. if theres an easy way to see in windows then that would help I presume. this is also presuming intel is wrong... but I know no better so that could be good? In totem and in the volume control on the panel in gnome, they are set to max and I have speakers I normally keep in windows on quiet and maxed them but nothing other than hiss so not that I have it on mute or the speakers. Sound works in windows.

I dont know if it is installed, wether its an option or what. sorry for the big post of rubbishness but thought I'd just speak and give detail where I can. install seems fine other than this, any help? I need a driver that I dont know/ havnt found? any help would be apreciated

---

### Post by annda on 2007-04-25
if you get a hiss, something is working. type alsamixer in the terminal. make sure master and pcm are NOT muted, use 'M' key to change that.

---

### Post by saurio33 on 2007-04-25
follow this post:
[http://ubuntuforums.org/showthread.php?t=239995&page=2](http://ubuntuforums.org/showthread.php?t=239995&page=2)

---

### Post by Hackza on 2007-04-25
Thanks a lot guys! I read about that other post that I didn't see before and found someone saying about surround sound acting like master volume so I headed into alsamixer remembering seeing surround in there. unmuted and turned it up and now I'm all good to go.

again thanks for the help and it may be a hack of a fix? does surround being used matter at all? I've only got stereo speakers really but it seems like it works fine with no sound missing so cheers for pointing me in the right direction.

---

### Post by Panzor on 2007-04-25
Yeah, alsamixer has saved my a** many a time. :)

---

