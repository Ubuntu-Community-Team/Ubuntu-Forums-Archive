---
title: "New MP3 player... what do I do?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Corfy on 2007-04-09
It is times like this I am glad there is an "Absolute Beginner Talk" thread on this forum. I'd feel embarrased asking this question anywhere else.

Ok, I got a (new to me) MP3 player as an early birthday present.

I have never owned an MP3 player before. I have never even made an MP3 (not in Windows, Linus, or Mac).  My MP3 collection is about a dozen, all downloaded off the web. I do have plenty of CDs, however, and I probably won't be downloading too much music, so that portion of it won't be a problem.

Anyway, I got a gently used Samsung YH-920 player (which will supposedly also play ogg files). If I plug it in to the USB port, it shows up on my desktop as a mounted external USB drive. I have read some other threads on the forum that say that other Samsung players worked well with Ubuntu, so I am hoping that this player will do the same for me. But as I said, I don't know what to do or what programs to use or anything. I have the software CD that came with the player, but it is Windows only.

I am running Kubuntu 6.10 (although I have both Gnome and KDE installed).

So... what do I do?

Thanks for your help.

---

### Post by RomeReactor on 2007-04-09
Hi. If Kubuntu does recognize it as a storage device, I'd say it's a pretty good bet you can just drag and drop MP3's to it (and from it) using Konqueror; I have a Creative Zen Nano Plus which is also recognized as a storage device, and that's what I do.

---

### Post by Corfy on 2007-04-11
I have been running into all sorts of problems with this player.

I copied several .ogg files onto the player, but the player didn't seem to recognize them. After further research, I discovered that the U.S. version of the YH-920 doesn't play ogg files, but players released in some other countries do. Oookay.

So I made MP3s instead. However, for some reason, I couldn't copy the MP3s onto the player with Kubuntu. It kept telling me I didn't have permission or the drive was full. I could copy any other files I wanted to, but not MP3s.

So I booted up a Windows computer and installed all of the software and tried from that end. From Windows, I can copy over all the MP3s I want, but the player doesn't see them to play. ](*,) 

I tried several different locations on the player, but nothing seems to work.

The only thing that does work in Windows is pulling up the Napster program that came with the player and using that to transfer the files from CD to the player. That works great (except that it is through Windows). But I can't figure out how to import any of my MP3s. I can't seem to get Napster or the player to recognize them. And I would really like to be able to do this through Linux rather than Windows. Is there a Napster-like program for Linux? I'm not interested in the downloading and purchasing of music, I just want to get my music from my CDs onto the player so I can listen to it. But since MP3s are officially supported, but I can't get them recognized by the player, I am wondering if maybe ogg files might be supported as well if I can just get them recognized. At the moment, though, I just want to get this working.

---

### Post by lamalex on 2007-04-11
try using amarok, I've had good luck with it.

---

### Post by sailor2001 on 2007-04-11
[http://www.tropicalglen.com/](http://www.tropicalglen.com/)    if you are into music for the computer....have no idea where I got this one

---

### Post by Corfy on 2007-04-11
> **Iamalex said:**
> try using amarok, I've had good luck with it.

Well, after fighting with Amarok for nearly an hour, I was finally able to transfer some MP3 files over to the player.

Unfortunately, the player still won't play them.

There appears to be some type of database or file listing on the player itself for audio files. I discovered that because I deleted a file off the player yesterday and saw that the song was still listed as a playable track, even though there was nothing there to play. I think that is the problem, the MP3 files aren't in the database, and apparently, it doesn't appear in the database automatically.

---

### Post by Corfy on 2007-04-12
I thought I would bring you up to speed on what I have worked out so far (in case someone else stumbles across this thread).

I stumbled across the PMPLib project at [http://pmplib.sourceforge.net/](http://pmplib.sourceforge.net/) and realized that this was my problem. Typically, the software on the computer would re-write the song list database on the player, but when I copy the files over myself, the player ignores them. The PMPLib project is supposed to set it up so that it will rewrite the database on the player once the music files are on there. I can then use my own software (whatever software I want) to rip the songs and put the songs on the player.

Unfortunately, I had all sorts of problems with getting it installed. It isn't in the Ubuntu repositories, so I followed the directions found at [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) for "How to Install Anything in Ubuntu. I first used alien and tried to install the RPM. Well, it seemed to work, no errors, no messages, but when I went to run the program, I was told the command didn't exist.

So then I tried installing it via the source code. I downloaded the code, ran ./configure on it (which seemed to go OK), but then, when I tried to run make, I was told the makefile didn't exist, so it stopped.

I finally found a script online at [http://martin.ellis.name/pmplib/](http://martin.ellis.name/pmplib/) that will install it on Ubuntu, and it seemed to go successfully, but it didn't recognize that I had a player installed, even though my player is listed in the supported list.

By then, it was getting late, and I just left it. I will try again tonight. I may just have needed to unplug and replug the player back into the computer (which I didn't try). Or maybe my computer just needed restarting with all of the trials and errors I made (I know, that is a Windows thing, not a LInux thing, but still). Or maybe I will be stuck needing Windows (there is a Windows version of the software, maybe I can use Ubuntu to rip the songs and transfer them, and then use Windows to rebuild the database). In any case, I will keep you posted.

BTW, I did figure out why I couldn't copy the MP3s over onto the player. The file names had quotes in them. The Samsung player didn't like that.

---

