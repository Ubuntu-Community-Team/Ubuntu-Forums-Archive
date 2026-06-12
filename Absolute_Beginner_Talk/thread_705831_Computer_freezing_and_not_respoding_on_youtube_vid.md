---
title: "Computer freezing and not respoding on youtube videos"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by YaniQC on 2008-02-23
I have a new Ubuntu (7.10) installed on my second hd (sda 240 gb). Yesterday I noticed that while I'm watching youtube (or google) videos, the computer freezes and doesn't respond any more. The mouse doesn't move, ctrl+alt+bkspc doesn't work. Only reset. I checked it 3 times, and it freezed 3 times after 1 minute of video.

When I checked the same with Win Xp (on my first hd - hdb, 148 gb), nothing freezed.

A friend told me that this might be a hw problem, but he can't say which one and advised me to ask the collective mind here.

My computer:
amd athlon 64 x2 dual
core processor 3800+
2.01 Hz, 2 gb ram

Thank you in advance for considering my linux complete beginner level when trying to help me :)

---

### Post by JoshuaRL on 2008-02-23
If it doesn't freeze on XP then it's probably not a hardware issue.  Does it freeze on anything else?

---

### Post by YaniQC on 2008-02-23
For the 1st time it freezed yesterday when I was installing windows xp in virtualbox. When I rebooted the installation continued normally. Then yesterday it freezed on a youtube video. And it caused a problem in my internet connection. I don't know what was the pb, but I had to reset the router and to use another modem to get back the internet. 

And this evening the system freezed twice - on a youtube and google video. I was just surfing as usually... no other applications using (maybe skype and firestarter...)

The friend told me that it maked sense to change smth in bios (processor frequency, cash, etc), but it must be done by someone who sees into the matter.

Btw, yesterday I had pb with my 1st hd (hdb). Bios didn't see him untill I plug it off and on. Since it's my "first" disk (I think grub is on it), it's really important that it works well.

---

### Post by Black Market Baby on 2008-02-23
Do you have the proper Flash plugin installed? You have to download the tar and install it manually. The ones that appear in Synaptic Package Manager dont work (at least not for me). 

Also did you install the restricted driver for your graphics card? That might make a difference. 

(I'm a newbie too, so i may be way off in my advice)

---

### Post by YaniQC on 2008-02-23
I installed all the updates required by Ubuntu and plug-ins required during surfing internet. F.ex. flash. 

As to videocard, I remember Ubuntu proposed me to do smth to NVIDIA. I'm not sure if it's my graphic card. Where should I check it?

---

### Post by seventhc on 2008-02-23
Would using desktop effects cause this???
If you are using them, you might try disabling it, then try youtube again. If it doesn't freeze, then it would be b/c of desktop effects/compiz.

---

### Post by Black Market Baby on 2008-02-23
When Ubuntu installs it just gives you a very "general" driver that will work so you can see your windows and move the mouse, but you need to actually install the "restricted" driver to get the real performance from your graphics card. See the Video & Multimedia Forum stickies for more details.


Youtube uses flash so thats why i asked. You need to make sure you have the *right* flash plugin installed. 

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
Says:
"If you're installing Flash between January and April 2008
There is a bug with the usual installation method, so you should do a manual installation of Flash"

That site contains instructions on how to do that.

---

### Post by YaniQC on 2008-02-24
> Would using desktop effects cause this???I'm not using any desktop effects yet.

> Youtube uses flash so thats why i asked. You need to make sure you have the *right* flash plugin installed.I've just reinstalled flash according to the instruction. When I tried to check if it worked with google video, it freezed after the 1st minute.


I thought it was due to streaming video (large amount of data put in cash on computer), but I tried the same with streaming windows medis player video ([http://www.cbc.ca/video/](http://www.cbc.ca/video/)) and it worked well for an hour without freezing.

---

### Post by YaniQC on 2008-02-24
BTW, it's not only youtube and gvideo that freezes my computer, but every flash application. The same was for an on-line flash game. After 1 minute I had to reboot the computer.

---

### Post by oedha on 2008-02-24
how did you install the flash ?
what if  :==> sudo apt-get install flashplugin-nonfree

---

### Post by YaniQC on 2008-02-24
> **oedha said:**
> how did you install the flash ?
I installed the flash according to this procedure: [http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

> what if  :==> sudo apt-get install flashplugin-nonfreeShould i just type this in terminal?

---

### Post by YaniQC on 2008-02-24
As to nvidia drivers, I remember I installed them in the very beginning according to this procedure: [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia) 
So now it's checked and enabled.

---

### Post by oedha on 2008-02-24
> **YaniQC said:**
> 
Should i just type this in terminal?

yap....from terminal......( i failed when i follow your link before :) )
what about the other codecs ? have you install them ?
for codec :==> sudo apt-get install ubuntu-restricted-extras

---

