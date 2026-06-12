---
title: "Getting mp3 and avi files to work in 7.10?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by AggieTwist on 2007-11-29
hey, i have Gutsy loaded as a dual boot on my laptop and am new to Ubuntu but was wondering what the simplest way to get my .mp3 and .avi files to play is.  I read something about EasyUbuntu but after downloading it and installing the package it said I needed to enter another line in the terminal that is as follows:
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```
But when I did this it does nothing in the terminal and my files still don't play...I'm going to try it again this evening but was wondering if there are other solutions.  I would primarily just like to be able to play my mp3's avi files and the occasional dvd.  Thanks!

---

### Post by RomeReactor on 2007-11-29
Hi. The easiest way to enable most multimedia functionality in Ubuntu is to install **ubuntu-restricted-extras**; however, since you're in Texas, due to some licensing issues only you can decide whether to install this package or not. This is the package description Synaptic gives about it:

> Commonly used restricted packages
This package depends on some commonly used packages in the Ubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (gstreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio files),
and DVD playback.

Please note that packages from multiverse are restricted by copyright
or legal issues in some countries. See
[http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)
for more information.

So visit that link to get more information about it. If you *do* decide to install it, open a terminal and enter:
```
sudo apt-get install ubuntu-restricted-extras
```

Hope this helps

---

### Post by Inxsible on 2007-11-29
Try this method which is from the Ubuntu Guide link in my signature

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Updates_and_Upgrades_and_Installing_Software](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Updates_and_Upgrades_and_Installing_Software)

---

### Post by fineas on 2007-11-29
First, enable extra repositories: System>Administration>  Synaptic package manager.Then, from menu bar, settings>repositories.Check main,universe,restricted and multiverse.In the second tab,check them all.Close and click the update button.
Now, double left click a mp3 file.You should be asked if you want to install the apropriate codecs or something like this.Say yes and things will get automatically.
Tell us for the result
Also check this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and note that easyubuntu is not recommended by Ubuntu

---

### Post by maybeway36 on 2007-11-29
[http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues]("http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues")

---

### Post by AggieTwist on 2007-11-29
thanks guys, that was fast...i'll try your suggestions the next time I get on my laptop...

---

### Post by Delkster on 2007-11-29
> **RomeReactor said:**
> however, since you're in Texas, due to some licensing issues only you can decide whether to install this package or not.
There should be no problem in using mp3 decoders for personal use. I don't suppose things are different in Texas.

Encoders do pose a problem, and yes, there are also patent issues with decoders, which is why Ubuntu doesn't ship with one by default, but as far as I know, the patent holders do not require royalties for non-commercial use of mp3 decoders. I'm not a lawyer, of course.

Anyway, you can find various codecs in Add/Remove Applications by searching with the word "codec". Generally, if you want to play stuff in Rhythmbox or the default Totem Media Player, install GStreamer plugins for the formats you need. Installing "Ubuntu restricted extras" will bundle some of the most common codecs as well as Flash and Java support.

---

### Post by Henry Rayker on 2007-11-29
The patent issue is stupid and I refuse to pay it any mind. It is unclear exactly who has what rights concerning the MP3 format.

Three groups claim to have control over licensing of the mp3 format...and they can't decide exactly what anyone is allowed to do...I tend to go with the least strict of any of their claims. (For example, Thomson claims individuals are allowed to use free encoders without fear of repercussion).

When it's all said and done, .ogg is nicer...if only my Creative Zen played it...

---

### Post by AggieTwist on 2007-11-29
put it this way, i'm already in trouble if anyone ever checks my computer for patents or copyright law infringement...i have about 10,000 songs...enough said...

---

### Post by AggieTwist on 2007-11-29
when i entered the code provided this is what i got...
```
jared@jared-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for jared:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

```

what do i do from there? i will try enabling more repositories and the like...

EDIT: I got it all to play by adding the repositories and stuff. Only question now is how come my speakers won't play real loud (like 1/5 the volume of windows) and there is static or fuzz sound in the background.

---

