---
title: "Need Help with Mine and Playing Music"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Afteraffekt on 2006-12-03
Well, I don't know what to say but this is confusing, and I would really appreciate any help I can get. Just I cant get Wine to work...

I'm a gamer, but was tired of Windows always giving me trouble, not to mention I'm taking computer classes and I wanted to know more, and this is how I learn. So I got a copy of Ubuntu from my teacher, was 5.10, and worked, but I had errors while trying to install Wine. First I installed my C Compilers, still got a few errors but not as many, then I actually downloaded 6.10 and clean installed it. I'm still getting the error, so then i go into Add/Remove programs and search for Wine, and I find it, I hit apply it starts to download and its at 11/18 files downloaded, and guess what? I remember the repository has been acting up, and sure enough it stops at 11 and says Failed for the remaining 7 files. I close out of it to try again, now I cant install anything from Add/Remove Programs and here is the error that wine gives me when I do ./tools/wineinstall:

C Compiler cant create executables.

The error I get when I use Add/Remove is:

Wine Windows Emulator cannot be installed on your computer type (i386)
  Either the application requires special hardware features or the vendor decided to not support your computer type.

I get that for any, and all programs I try to install through Add/Remove.

What route should I take to fix this?

My Computer is:
Amd Athlon 64 3700+
OCZ 1Gb Ram 2-2-2-5
ATI X300/X550
MSI Neo4 K8N Platinum SLI Motherboard

Now how do I play mp3s? Thanks

---

### Post by Afteraffekt on 2006-12-03
Was pushed to 2nd page so felt it needed a bump.

---

### Post by Azakus on 2006-12-03
Why bother with Windows software and WINE to play music? Try Audacious Media Player (my favorite) or the built-in Rythembox player. Audacious is like WinAmp and Rythembox like iTunes.
If you want Audacious, run this code in the terminal
```
sudo gedit /etc/apt/sources.list
```
and add these lines to the bottom
```
##Audacious Media Player
deb http://static.audacious-media-player.org/ubuntu edgy main
deb-src http://static.audacious-media-player.org/ubuntu edgy main

```
Save the file, exit Gedit, and in a terminal type ```
sudo aptitude install audacious audacious-plugins audacious-plugins-extra
```
You'll have all the plugins to play every music file I know of.

---

### Post by Afteraffekt on 2006-12-03
With that I try and I get an error stating it couldn't find anything?

---

### Post by CatKiller on 2006-12-03
There isn't a 64-bit version of Wine. So you'd have to (I'd imagine) compile your own. For that you'll need to install **build-essential**. There are instructions at winehq.com. You might also find [this page]("http://monkeyblog.org/ubuntu/installing/") useful.

There are a number of programs that do not necessarily have optimal 64-bit versions. For that reason, it is generally recommended that new users first use the generic 32-bit version until they have more of an understanding of the processes involved.

Your other mp3 question is answered [here]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by Afteraffekt on 2006-12-03
I just want to play World of Warcraft, Fear, Ventrilo, and HL2/CSS And that will be fine, and in that sense why do I need a 64bit wine? 32bit works fine.

---

### Post by Afteraffekt on 2006-12-04
WoW With tinker Iv gotten my mp3s and wine to work, and have successly installed Ventrilo, but when i go to run World of Warcraft it acts lik it want to launch then freezes...i know directx isnt supported, so how do i get it to run in opengl?

---

