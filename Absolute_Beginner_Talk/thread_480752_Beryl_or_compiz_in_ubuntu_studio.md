---
title: "Beryl or compiz in ubuntu studio"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by LostArt on 2007-06-21
How can I install Beryl or Compiz in Ubuntu studio. I have an Intel 900 Graphics accelerator, and Compiz worked when I had feisty installed. but sadly when I installed Ubuntu studio, and tried to get Compiz or Beryl working I just get the white screen of death, which sucks. A lot :(

---

### Post by mengfei on 2007-06-22
Honestly, if I were you I would just stay away from either Compiz or Beryl. I mean, really, just how useful is it to have wobbly windows? Maybe when they're more stable I'll look to use them.

But if you must... well, I've never used Ubuntu Studio before..., but have you tried out [http://ubuntuguide.org?](http://ubuntuguide.org?)

Give that a shot, you might find something helpful there.

One more thing, I know that the Intel GMA 950 requires a package to be installed to work correctly... don't remember the exact package name, 915resolution?

Well, anyhow, just saying that perhaps you need a similar package for your Intel 900.

So roll up your sleeves, research your problem, and give it a go!

---

### Post by Clay_Banger on 2007-06-22
install the drivers for your card:
open the terminal and type this in:
```
sudo apt-get install xserver-xorg-video-intel
```
restart you computer.

then try installing compiz/beryl

---

