---
title: "Disappointed =("
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by XeroCurve on 2006-07-26
I dont know about any of you but I have been reading for about a week straight now and still cant get what should be a small thing to work right. I dont understand how this support section to be named Absolute Beginner when I am far from a beginner but these issues are making me feel really stupid. I guess I need to read the "The absolute infant beginner" support threads if there are any. Is there a good place for a real beginner to get help? I started out just trying to get an embeded midi file to play in Firefox and I cant get it to work. I am frustrated and I dont know where to get help. I have had many replies to my questions and all of them assume that I know what im doing, which i guess I dont! Like many people I hate Windows, but I can get anything I need done there.

Sincerly, Wits End.

---

### Post by pbaehr on 2006-07-26
Many of the posts in the "Absolute Beginner" section are anything but. I have often thought that many new users may have been scared off by posts like, "Cannot access /dev/ttyS1 via eth0 with root access over SSH" (yes, I know that doesn't make sense).

There are, scattered about, many posts by true beginners, though. If people are responding to your posts with the assumption that you know more than you do, ask them to slow down. Explain that you are an ACTUAL beginner and you need things explained a little clearer. While that should be redundant in this section, often it is not.

There are plenty of people here willing to spend some time to help you get started learning, even if they just point you in the right direction. Good luck!

---

### Post by jordilin on 2006-07-26
Well you can always ask, ask and ask. I have several years of experience in Linux with several distros, and I'm always learning new things and sometimes asking things that only a newbie would ask. Linux is like the universe, its possibilities are endless. So, don't worry, this is a great community. I would go to [www.tldp.org](www.tldp.org) the linux documentation project for general Linux info. There you will find incredible manuals and howto's. Obviously, ubuntuforums website is one of the most awesome out there in order to look for info. As Ubuntu is Debian based, you can always look for Debian tutorials as Debian has more years of experience under the belt. Just my two cents. :D

---

### Post by annda on 2006-07-26
hi!

don't get discouraged too soon. many people (including myself) have posted questions about "simple" things here and almost always there is someone who knows the answer.

i must admit that i can't help you, but if you don't get any help here , try reposting with a clear topic (like "how to play midi in firefox").

also, you might try Automatix for installing multimedia support automatically. look here:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

anyway, don't be afraid to ask questions. (of course, it's always a good idea to search the forums for your problem first)

---

### Post by avtolle on 2006-07-26
Not trying to start a flame war or anything, but as I recall from memory, the OP has tried to install various apps w/Automatix, and it didn't seem to help. Perhaps it would be beneficial for him to restate the issue, from his beginning post it appears he is trying to install a plugin in Firefox to play a midi file.

---

### Post by XeroCurve on 2006-07-26
I apreciate what you guys are saying and if I had more time I wouldnt care so much. The situation is that I work in the IT dept of a small business and I convinced them to let me set up an Ubuntu BOX for them to try out in the office but, lucky me, the only thing I cant get to work is essential.They have an older online help program that has an embeded midi file that plays and alert when someone requests assistance and if I cant get this to work soon then they will only be reassured that windows is where they should stay, and in essence ive defeated my purpose.

---

### Post by GuitarHero on 2006-07-26
I think Easy Ubuntu can install midi support.  Try it.

---

### Post by XeroCurve on 2006-07-26
Oh and yes what im trying to get to work is an embeded midi file to play in a Firefox browser. Ive tried the Automatix install and it didnt work. The correct plugins seem to be in one directory but not another. Ive done the about: plugins in Firefox and it doesnt list the mplayer plugins even though I can find them in certain directories. I had a suggestion to do the sym link and followed it (I thought) and still nothing. I tried installed Media Connectivity but I cant get that to work right either. The only item that I could find to play midi files is something called "Timidity" but even that wont work right in the Media Connectivity program. Ive even tried changing the HTML code to use <object> tags instead of the <embed> and no difference. I suspect there is something simple im not doing but I have no idea what.

---

### Post by kayoti on 2006-07-26
EasyUbuntu worked for me, it got things rolling in firefox and hopefully (and painlessly) it will do the same for you.  Here's the link: [http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")
Check the download section and it has step by step instructions for you to get it installed.  

For the window to type the install code into, use the Terminal.

**[EDIT] Now that I read your previous post, I am wondering if you are running the 64bit Ubuntu?  If so, check out this forum:
[http://www.ubuntuforums.org/showthread.php?p=1174435]("http://www.ubuntuforums.org/showthread.php?p=1174435")

Kyle

---

### Post by XeroCurve on 2006-07-26
I dont think I am running the 64 bit version but, how would i check. I did the upgrade from Breezy.

---

### Post by XeroCurve on 2006-07-26
I just tried to do Easy Ubuntu and it said that it could not apply changes and that I needed to fix broken packages? huh?

---

### Post by wog on 2006-07-26
Oh my god, something I might actually know???

If you have broken packages in your system, try this in a terminal:

```
sudo apt-get -f install
```

That should fix the broken stuff if there is any.

After that, this couldn't hurt:
```
sudo apt-get update
sudo apt-get upgrade
```

See what that does.

---

### Post by JoWilly on 2006-07-26
> **wog said:**
> Oh my god, something I might actually know???

If you have broken packages in your system, try this in a terminal:

```
sudo apt-get -f install
```

That should fix the broken stuff if there is any.



Wait wait wait !

Not good to try to force an install with broken packages. Fix the broken packages first.

Start synaptic in system/admin/synaptic , click custom filters, and broken , to see the broken packages, then click apply to fix them.

---

### Post by wog on 2006-07-26
Dunno. When I run that command string and nothing else, it seems to go through my package tree and repair everything that is incomplete, including installing deps that are not installed and fixing things that are not set up properly. Automagically.

I say 'seems' because I don't know what it really does in the background. While I assume '-f' means to force installation, I do note the lack of a named package in the command string to force installation of.

---

### Post by JoWilly on 2006-07-26
> **wog said:**
> 

I say 'seems' because I don't know what it really does in the background. While I assume '-f' means to force installation, I do note the lack of a named package in the command string to force installation of.

Aha you put no package ? Ok, so in that case it means it tries to fix itself. 

Thats good then :)

---

### Post by wog on 2006-07-26
> **JoWilly said:**
> Aha you put no package ? Ok, so in that case it means it tries to fix itself. 

Thats good then :)

Oh good. I got it right after all. :)

---

