---
title: "Nooby Totem Question"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by warhell on 2006-02-10
First of all I want to say hi to the Ubuntu community, I just took windows off my box and put Ubuntu, I'm a computer science major, so they strongly recommend using Linux. I'm going to try really try hard to fully switch to Ubuntu, which brings up my question.

In Ubuntu there is totem and there is that other program.... rythmbox, since I come from the windows world, I have a lot of mp3s that are stored on my mp3 player. When I transfered over to my box, totem and rythmbox could not play them. Now I looked online and try to download the decoder and whatnot, but every time i tried to dl, there is no .exe file, so i'm kinda stuck. If anyone can give me some really detailed instruction on how to fix this I would appreciate it.

In advance, Thanks.

---

### Post by warhell on 2006-02-10
bump

---

### Post by GreyFox503 on 2006-02-10
Welcome to Ubuntu forums.  If you're new to Ubuntu, I would suggest browsing these forums and the wiki site, wiki.ubuntu.com.  You can find many HOWTOs for lots of common tasks, like this:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

Ubuntu does not ship with any proprietary codecs (to my knowledge), so you cannot play MP3s, DVDs, etc. on a default installation.

You may also want to download [Automatix]("http://ubuntuforums.org/showthread.php?t=66563").  It is a small program that downloads and install many common programs/drivers/codecs for you.  I don't use it personally, but it looks useful.

---

### Post by jpkotta on 2006-02-10
The [wiki]("https://wiki.ubuntu.com/RestrictedFormats") has info about stuff like this, and most other common questions.

There is no such thing as a ".exe" in Unix.  Unix generally doesn't look at filename extensions when trying to execute a file.  Instead, each file has an execute bit (actually three), which causes the OS to try to run the file if it is set.  You can change this and other bits with the chmod command (or a right click in Nautilus).

[Here]("http://www.ubuntuguide.org/") is another beginners' resource.

BTW, if you want to start programming, you want to install the build-essential package

---

### Post by 3rdalbum on 2006-02-10
Quick 'n simple instructions: Open Synaptic Package Manager, go to the Edit menu and come down to Search. Do a search for "gstreamer", and install all of the plugins that look promising.

---

