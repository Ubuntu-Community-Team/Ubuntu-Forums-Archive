---
title: "Another audio question"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Beastofomous on 2007-06-05
I know you guys are probably tired of listening to n00bs like me with audio problems but heres another one for you.

When I ran ubuntu LiveCD (64bit) everything was fine, the resolution was off a bit but I figured it was because I could'nt save any drivers and whatnot. My sound was working and everything though. So I decided to go ahead with the install, purchased a new hard drive to put it on so as not to worry about messing up my xp install. Since I've installed it there has been no sound, i have tried everything i can find on this forum and it still does not work.  I'm at a complete loss and was hoping someone could have me post with some of my settings or something and make some sense of it. 

If i cant get anything working is there a possibility that its because of the 64bit? and if so can someone point me in the direction of a easy tutorial for switching to 32bit? 

Hope someone can help. thanks in advance!

---

### Post by starcraft.man on 2007-06-05
Uh, if you want help from some of the 64 bit experts might want to add a bit more detail. Whats the motherboard? Integrated? If its external sound whats the card? Anything else useful is also good to add. I've never used 64 so all I know is that it breaks things when people use it (no offence to it, its just still a 32 bit world)... >.>.

There aren't any quick switches to 32 bit, its a completely different system. You have to do a complete reinstall (lucky Ubuntu is a fast install compared to others like openSuSE, just sat through that one...). Heres a link to download a new ISO, just check the sum as always, burn, recheck sum and off you go with install :).
[URL="http://releases.ubuntu.com/7.04/"]
Link[/URL] (x86 version).
Just pick whatever installer you used before Desktop for Live and the other option is of course Alternate, torrent links at the bottom if thats your preferred means. MD5 sums in a small text at bottom of the page too.

Personally, I don't think 64 is ready just yet. The speed boost doesn't seem to outweigh the difficulty and problems...

---

### Post by Beastofomous on 2007-06-05
uninstalling ubuntu isn't going to be a problem is it? I used the default install method and put it on my new hard drive. I've heard that uninstalling can wipe your MBR?

---

### Post by bren on 2007-06-05
no MBR will be fine....

when you install 32 bit version choose manual at the partition stage and you can format/wipe the 64 version 

by the way i agree 32 bit is the one to install right now..

the resolution works on 32 for me!   (didnt in 64!)

bren

---

### Post by starcraft.man on 2007-06-05
> **Beastofomous said:**
> uninstalling ubuntu isn't going to be a problem is it? I used the default install method and put it on my new hard drive. I've heard that uninstalling can wipe your MBR?

There is no problem. When you get to the partitioner (live or alternate) pick manual, carefully look at the partitions and you can just format and remount them as they are. That will just erase everything in them and retain them as divisions. As for the MBR, it will only be wiped if you uninstall Ubuntu after having installed GRUB to your MBR of the main booting disk. In such cases, you'd have to restore it with the ntloader (windows boot loader) or a replacement. Your overwriting, so you will be fine. GRUB will reinstall itself automatically like before.

I'm sure it will be fine, best wishes :).

Edit: [This link]("http://www.psychocats.net/ubuntu/installing#partitioning") will show you about partitions if your worried, don't be :).

---

### Post by Beastofomous on 2007-06-05
Wow. Now i know what people are talking about when they say the Linux community is unlike any other. Not only was that almost as fast as talking to any of you on an IM program but you are all so polite, even to a Linux noob like myself. Thanks alot guys hopefully i can get this working properly and stick around this community

---

### Post by starcraft.man on 2007-06-05
Oi! Course I am, Canadian if ya didn't see, aye? :p.

Naw, just messing... its not just a forum filled with Canadians (trust me, thats a really **REALLY** bad thing, been in one) we just all get along (99% of time) and are happy to lend a hand. It doesn't hurt any, and I got plenty of time. :)

---

### Post by Beastofomous on 2007-06-05
Alright guys so I've re installed with x86 instead of the 64bit iso and when I booted everything up im still not getting any sound.

now last time when I first booted it up I quickly installed those restricted nvidia drivers, is that a no no? should i be installing something else possibly?

the drivers that are running that they are calling restricted are Atheros Hardware Access Layer and Nvidia accelerated graphics driver.

Should I disable these and find better replacements?

You dont think these are related to my no sound issue do you?

---

### Post by starcraft.man on 2007-06-05
Nothing in the graphics department should interfere with Audio, don't disable anything there. Kinda odd, Audio was the thing I always thought worked out of the box... Whats the mobo model and sound card please. I'm not really an audio expert, might have to find someone else to help ya if this isn't something super common I've seen...

Do feel free to install nvidia drivers again by whatever means you did last time.

---

### Post by Beastofomous on 2007-06-05
well i used belarc to try and figure out what mobo i have, and it came back with AsusTek Computer Diablo 1.xx but when i search for an asus of the "diablo" model i get nothing

the sound card is onboard and it should be Realtek AC'97... at least thats the conclusion I've come to after all of this audio work I've been doing today

---

### Post by Beastofomous on 2007-06-05
actually just double checked it is diablo its a HP motherboard and the audio is integrated AC'97

---

### Post by Beastofomous on 2007-06-06
Sorry for bumping my own thread but im really hoping someone can help me figure out whats gone wrong

---

