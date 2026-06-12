---
title: "Firefox is Slower? Half Open TCP IP?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Literati on 2008-03-16
Two quick questions

I just switched to Ubuntu a few days ago, and I installed Firefox 3 Beta 4 on both my XP and Ubuntu computers. 

My question is, how come, say I'm trying to watch the Diggnation Podcast on my computer, it'll stream SLOWER on Ubuntu than it does on XP? The video is choppier. It's not a question of it not loading (Although YouTube videos load slower) but it's already loaded, but it's just choppy...

Secondly, I know on XP you need to tweak your max half open TCP IP settings for use with Torrent clients. Do I need to do anything like that on Ubuntu? Or is Deluge just all set to go?

---

### Post by handydan918 on 2008-03-16
What kind of video card do you have? 
Post the output of ```
lspci | grep vga
```

---

### Post by Literati on 2008-03-17
> **handydan918 said:**
> What kind of video card do you have? 
Post the output of ```
lspci | grep vga
```


01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]

---

### Post by billgoldberg on 2008-03-17
Remember that you are using beta software.

That means it's not ready for the masses to use.

But I also use it and have no such problems.

Could be compiz fusion related, try turning compiz off and see if that helps.

I believe the command is:

```
compiz --reconfigure
```

or you could use a little program called [compiz switch]("http://blogage.de/files/1393/download?compiz-switch_0.2.0~ubuntu_i386.deb"). After installing the .deb (just doulble click it) it will be in "applications -> accessories", you could right click it and add it to the panel for quicker usage.

---

### Post by handydan918 on 2008-03-18
> **Literati said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]

Don't have an ATI card, so I'm blind here, but using synaptic, enable the restricted driver section and look for an ATI driver for your 9600. I bet that will help.

---

