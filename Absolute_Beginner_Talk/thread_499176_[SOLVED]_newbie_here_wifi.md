---
title: "[SOLVED] newbie here wifi??"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-07-12
frist of all im really liking this OS so far. :) 
my machine has a linksys  wireless-G model WMP54GS ver 1.4
linksys says it wont work with ubuntu, ok what will? i went to frys computer store and was told they had nothing out of the box for linux.

---

### Post by randytuggle on 2007-07-12
there is an app called ndiswrapper which will allow you to install the windows drivers for the wi-fi card. I don't know the exact driver you need - but someone here is going to know this info. Hang on and someone will come to your rescue on this.

---

### Post by deadgobby on 2007-07-12
Most of the time Fry's people do not know what they are talking about. Most wifi's will work with Ubie 7.04 right out of the box. Some you do need to do some mojo. I have a Blanc bw-54u11 and worked right off the bat with Edgy. The cost was really cheap.
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
 You may need to install ndiswrapper to get your wifi working. Check out the link and carry on.
Gobby

---

### Post by Ek0nomik on 2007-07-12
Well, I on the other hand would tell you that most wireless cards probably won't work out of the box, or at least most wireless cards that people use in their computers with Linux don't work out of the box.

Your wireless card, from my very short period of research, seems to be a rather picky little guy.

[http://dossy.org/archives/000110.html](http://dossy.org/archives/000110.html)

This link is a guide on how someone got his WMP54GS working.  The individual uses Debian, so the commands should work for Ubuntu.  However, the tutorial is a bit outdated, in regards to the version of ndiswrapper and the kernel.

It may or may not work for you, but it is worth a shot.  You can grab a newer version of ndiswrapper from [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net).

Otherwise you could buy a wireless card which has been shown to work with Ubuntu, but you still will probably end up using ndiswrapper.

I would give this a shot though first, might save you a couple bucks.

---

### Post by Espreon on 2007-07-12
Here is my way of getting ndiswrapper up the easy way!

```
sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```

Once you find the driver (google it) extract the .exe/.zip/.cab or whatever the file is

Somewhere in the extractions you should find an .ini or .inf (forgot which one) file once you found it goto System>Administartion (or System [I am not on an Ubuntu  comp right now])>Windows Wireless Drivers

Now Select Add or New and find the .ini or .inf file that is your driver and select OK, reboot and it may (should) work and enjoy!

---

### Post by jrandolph on 2007-07-12
I have a Linksys WMP54G and I use

wlassistant

try it -- works for me

---

