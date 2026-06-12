---
title: "I want a big screen!!!"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by rift400 on 2008-03-05
Hi all
I'm new to Ubuntu/Linux and am basically struggling through a bunch of problems setting up my shiny new ubuntu machine. My newest question is this... is there a 'how to' running through how to set up an extended desktop. I've got a bog standard dell laptop (intel standard integrated graphics card) with a tiny screen and I'd like to connect up a benq FP92W and use both screens. The problems began to arise when I was playing with the Screens and Graphics section. There doesn't appear to be a driver for this monitor in there and when I told it to use a generic plug and play setting it dumped me into ascii text mode when I rebooted. The end result was that I had to reinstall ubuntu coz I couldn't figure out how to get into the GUI again. I'm not a linux wiz but I do have a little technical know how... and I'm trying to learn how to do stuff. Any suggestions or guidance would be much appreciated.

Cheers

---

### Post by overdrank on 2008-03-05
> **rift400 said:**
> Hi all
I'm new to Ubuntu/Linux and am basically struggling through a bunch of problems setting up my shiny new ubuntu machine. My newest question is this... is there a 'how to' running through how to set up an extended desktop. I've got a bog standard dell laptop (intel standard integrated graphics card) with a tiny screen and I'd like to connect up a benq FP92W and use both screens. The problems began to arise when I was playing with the Screens and Graphics section. There doesn't appear to be a driver for this monitor in there and when I told it to use a generic plug and play setting it dumped me into ascii text mode when I rebooted. The end result was that I had to reinstall ubuntu coz I couldn't figure out how to get into the GUI again. I'm not a linux wiz but I do have a little technical know how... and I'm trying to learn how to do stuff. Any suggestions or guidance would be much appreciated.

Cheers

Hi and I have not tried to use a external monitor with my laptop but if you lose the GUI again there is no need for reinstall you can reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by rift400 on 2008-03-05
Awesome. Thanks for the advice.

---

