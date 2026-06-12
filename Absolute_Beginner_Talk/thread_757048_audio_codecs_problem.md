---
title: "audio codecs problem"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by aimpau on 2008-04-16
I really don't understand the "codec" system of Linux thus I'm here asking the ff question w/ regards to my situation

Situation: I'm a xubuntu user.

1. After googling around, I stumble upon the website of Mplayer. In their website, a file, which allegedly contains codecs, is present for download. I downloaded and followed all instructions. Those files are now residing at
```
~/win32
```
with a "755" permission.

2. Next, I download totem-xcine through synaptic.

3. I also download Banshee 'coz it features iTunes management.

Now here's what went wierd:

I tried to play mp3 in banshee, but it doesn't run and promptly suggests that a codec be searched. However, playing the same file in totem, it plays well.

So my question is, how does codecs work in xubuntu? aren't they "centralized" like in windows? Can you recommend some other alternative to iTunes which can also encode/decode .aac and .mp4? Or will I have to go with wine?

4.Since this is a codec problem (coder/decoder), I also tried:
```
sudo apt-get install nautilus-script-audio-convert
```
This "program" supposedly can convert various songs including .m4a/.mp4 and .aac to any format. How can this work? It says something about typing in the terminal but can't quite understand it. Please download this too and check it out for yourself.

5. I also download faac and faad. However, I tried it on a .wav and it didn't support it. Will it support mp3 as well?

I hope my questions get answered 'coz I do want to learn things but in some cases, I just have to ask. Better ask and be a fool for a moment, than never to ask and be a fool forever.

Thank you and keep up the good work in our Linux Crusade!

---

### Post by Claus7 on 2008-04-16
Hello,

giving a quich reply to your question I would suggest you to go to synaptic package manager and there to try and find win32 codecs or simply codecs. That way every program that you will use will be supported. Also I would propose you to install automatix and install from there the audio codecs that is has.

Regards!

---

### Post by PeterJS on 2008-04-16
W32 codecs and other overtly non-free/illegal stuff is kept in medibuntu to provide Canonical with legal deniablity. Medibuntu is neither , blessed, sanctioned or associated with Ubuntu... but every body will tell you to use it unofficially.

Directions for setting up medibuntu can be found here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

As for automatix, it's a terrible technical pox and shouldn't ever be used:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by owenll on 2008-04-21
> **PeterJS said:**
> 
As for automatix, it's a terrible technical pox and shouldn't ever be used:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
And there will be no automatix for Ubuntu 8.04 anyway  - it has been discontinued: 
[http://www.getautomatix.com/forum/index.php?showtopic=2424](http://www.getautomatix.com/forum/index.php?showtopic=2424)

---

### Post by Claus7 on 2008-04-25
Hello,

I didn't know about automatix. As long as I have it in dapper, I haven't faced any problem. I had made the setup long time ago and back then it was an easy and helpful application. Yet, this now is not the case.

Regards!

---

