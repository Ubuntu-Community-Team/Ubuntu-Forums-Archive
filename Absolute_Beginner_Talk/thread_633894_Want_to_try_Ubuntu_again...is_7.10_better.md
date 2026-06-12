---
title: "Want to try Ubuntu again...is 7.10 better?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Satummoo on 2007-12-07
I really want to use ubuntu but trying to get everything configured felt like a nightmare.  The biggest problem was my ATI card not being able to install correctly.  I tried edge and all of the guides but after literally days of fooling around and re-installing 10x+ times, I gave up.  With the release of 7.10 I hoped that maybe some compatibilites have gotten better and ATI recently released 7.11 Drivers with specifix linux support!  Now since that the new drivers are specifically for ubuntu, will the install proccess be n00b easy?

---

### Post by kpkeerthi on 2007-12-07
This is my humble suggestion for beginners or you may even take it as a request...
If you are beginning to use ubuntu or any linux, spend some fair amount of time reading [https://help.ubuntu.com/](https://help.ubuntu.com/). This guide will help you get started and understand certain nuances of the system so you will know what exactly you are doing. I find a lot of beginners losing patience and start copy/pasting commands from the hundreds and thousands of guides scattered in the web without understanding what they do and end up with a broken system. If you do not do your home work you will only end up reinstalling not 10x+ times but 1000x + times. Again this is a request. 

Now... as for your question, its quite hard to tell how well gutsy will support your system. I think you should try it for yourself.

---

### Post by hopelessone on 2007-12-07
Envy will detect your ATI card and fetch from the net and automatically install drivers for ya...install Envy...

hope helps..

---

### Post by Rocket2DMn on 2007-12-07
Ubuntu 7.10 has a much better system for setting up video card.  If when you first install and get a command prompt like I did with my ATI card, run
```
sudo dpkg-reconfigure xserver-xorg
```
Once you get to a GUI, no matter how bad it looks, you will never need to run that command again. 7.10 has a "bulletproof" xserver for setting up your desktop by going to Administration -> Screen and Graphics.  It operates more like in windows where if you select something wrong, it has a countdown and resets the screen to the previous settings if it goes bad.

---

### Post by dptxp on 2007-12-07
Best way is to try. Then post problems if any.

---

### Post by Satummoo on 2007-12-07
> **Rocket2DMn said:**
> Ubuntu 7.10 has a much better system for setting up video card.  If when you first install and get a command prompt like I did with my ATI card, run
```
sudo dpkg-reconfigure xserver-xorg
```
Once you get to a GUI, no matter how bad it looks, you will never need to run that command again. 7.10 has a "bulletproof" xserver for setting up your desktop by going to Administration -> Screen and Graphics.  It operates more like in windows where if you select something wrong, it has a countdown and resets the screen to the previous settings if it goes bad.

ah nice :)

whenever I installed the drivers, everything worked fine, even with restarts, then when I shut down and rebooted, I had to redo the xserver which seemed like forever and had no idea what half the options were.

It's nice to know that I can do this!

also, when I tried dual booting, it always automatically went to ubuntu first.  While i'm still learning, is there any quick way to have it default start windows?

EDIT: also, is it still advisable to run x86 version vs x64?

---

### Post by Rocket2DMn on 2007-12-07
You can change the default OS to boot: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)
You CAN run the x86 version - it tends to have better support for stuff like audio codecs, and Flash i believe.  However, you won't be getting the most out of your hardware.  It's your call - if you browse around and surf a bit you can find a lot of information on this dilemma.
Good luck!

---

