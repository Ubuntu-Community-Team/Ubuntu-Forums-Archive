---
title: "inexpensive graphics card for Beryl."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2007-01-24
:guitar:  Howdy!

I can't seem to get my nvidia graphic card to work so under the supierior ledership of the members of our lug I am doing what I have never dared to do. BUY A NEW PIECE OF COMPUTER HARDWARE.

I don't know what I am looking for other than that it needs to be AGP what ever that means.


Any guidance for a good model is appreciated, my budget is $50 or less.

---

### Post by charles.g.moore on 2007-01-24
Thats odd because the Nvidia support is pretty good, which model is it?

---

### Post by kinematic on 2007-01-24
nvidia fx5200 with 128 or 256mb of ram.
i have one with 256mb of ram and i bought it for 35 bucks.....nothing beats it at that price.
i have beryl running all the time and it also handles games such as enemy territory,true combat elite and quake well.

---

### Post by charles.g.moore on 2007-01-24
Not to discount the work you have done so far but are you sure your card is not supported?

---

### Post by ushaba on 2007-01-24
who is the manufacturer of the card, approximately how old is it? do you know if you have agp 8X/4X or something even older? do you mainly mean that the card does not have 3d acceleration or something more severe?

---

### Post by ushaba on 2007-01-24
if it is an nvidia card, it should work pretty well... just make sure you are using the legacy drivers instead of the new ones if it is an older card. plus, how did you install the drivers? remember that the ubuntu kernel already accomodates nvidia to some extent, but you can also get the drivers from nvidia's website. what steps have you tried?

---

### Post by bichopro on 2007-01-24
I run beryl perfect with a Ati radeon 7000 64 mb.

its so old graphic card

---

### Post by Linux&amp;Lizards on 2007-01-24
WOW! thanks for all the responses!

I believe the card is a riva2 tnt2 model 64 pro?
I might be off.
I was using the legacy drivers but it still won't work

---

### Post by Linux&amp;Lizards on 2007-01-24
I got the drivers from automatix. (they are the legacy ones)

and I also had to replace nv with nvidia in one of the files if I am correct.


is there something else I should do?

I notice no change.

---

### Post by ushaba on 2007-01-25
from the sounds of it, that card might not be too successful at running beryl/compiz even with correct drivers. that said, it's worth a shot. you can follow the instructions posted on the ubuntu help documents at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
the nv driver you have working right now is the open source 3d-acceleration-less version, so that's not going to run what you want. try following the instructions in this guide first, and if that doesn't work, copy and upload your xorg.conf file from /etc/X11/xorg.conf for more info.

---

### Post by Zzl1xndd on 2007-01-25
As for a new graphics card I would also say that the FX5200 is a great card I am using the 128meg. got it for $45CND.

---

### Post by %hMa@?b&lt;C on 2007-01-25
i got a 6200LE for 30 bucks USD off of Newegg

---

### Post by Linux&amp;Lizards on 2007-01-25
kk thanks for the help.

---

### Post by letitsnow on 2007-01-25
I'm using an Nvidia MX440 64mb and it runs beryl well. It was free.:D

---

### Post by ushaba on 2007-01-25
so i guess you're giving up on the old card? i can also recommend the fx5200. i'm currently using a 7300GS myself (not a bad card, but only for light gaming, and i use fluxbox anyway...) which i think was the equivalent of about 40$ US.

---

### Post by Linux&amp;Lizards on 2007-01-25
I never give up!

I'm just considering my options and then figuring if it is worth my time and money to stick with an old card, or burning some cash to get a better one.

I'm not a gamer so If I can get this one working it would be too cool!

---

### Post by JayTee on 2007-01-26
if you look on [http://forums.beryl-project.org](http://forums.beryl-project.org) there is a link for compatible Nvidia and ATI cards. If your card is listed, I'd try the Envy script from Alberto Milone from this thread, [http://www.ubuntuforums.org/showthread.php?t=281823&highlight=Envy](http://www.ubuntuforums.org/showthread.php?t=281823&highlight=Envy). I use it to install my drivers and reinstall after a kernel update (because kernel updates break xorg with Nvidia modules. This gives you one of the latest versions which runs Beryl with fewer crashes and problems. Remember Beryl is still beta software.

---

### Post by irish_flu on 2007-01-26
I run Beryl just great on my NVidia Geforce4 Ti 4800 (AGP 8x) 128MB.  I bet you could find somebody to just give you something like that.  :)

Off-topic:
Word to my fellow Hoosier Jaytee, go Colts

---

