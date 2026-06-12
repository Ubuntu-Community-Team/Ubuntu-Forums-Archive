---
title: "Elementary OS Luna, wireless keyboard needs unplug, replug for detection"
date: 2014-04-07
forum: Any Other OS
---

### Post by jbaerboc on 2014-04-07
Title says it all. I've had random strange detection issues on all distros based on Ubuntu I have tried. For example with Mint it would only detect my wireless keyboard after hitting 5 keys for example. In ElementaryOS Luna I have to unplug and replug the usb unifying thinggi for it to detect it. Once it re-detects it then everything works fine. And so far it seems when I replug it I have to do so into a different usb port than what it was in before.

My keyboard is a Logitech K350. Any advise or thoughts?

---

### Post by Stinger on 2014-04-07
What are the hardware specs of your computer and how new is it ?

---

### Post by jbaerboc on 2014-04-07
Stinger, I have a custom computer, insides are about a year old. There were some other things I couldn't get working and I just got annoyed enough I re-installed Linux Mint (KDE Flavor this time around).

I'm guessing it had to do with Luna using an older ubuntu repo and older software lists. I think when the OS matures more it could be a serious contender for the top of the list though. Mint better watch out!

---

### Post by Stinger on 2014-04-07
You can get eOS working with new hardware too using the LTS Enablement stack from Precise.

To install the Saucy hardware enablement packages in eOS Luna or Precise , please run the following command:

```
sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy
```
Remember to reboot to activate the new kernel and x-server.
[LTS Enablement Stack page]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

I wrote about it earlier on this thread:
[ [elementaryOS] 5 Myths About elementary]("http://ubuntuforums.org/showthread.php?t=2214635") 
( Bottom half )

noxit2 had almost the same problem on this thread:
[ elementaryOS won't let me use my external keyboard]("http://ubuntuforums.org/showthread.php?t=2213023")

---

### Post by jbaerboc on 2014-04-12
Interestingly Ubuntu 14.04 Beta 2 notices my keyboard right away no problems. Even in Mint [based on 13.10] I had to tap a few keys before it said ,"oh yeah there's something there".

---

### Post by Stinger on 2014-04-13
Well it seems like you would need the LTS enablement stack from Trusty, but Trusty hasn't been released yet so thats unfortunately not available  (  But will be soon )

You could consider trying the [unstable ElementaryOS build from 2014-04-01]("http://sourceforge.net/projects/elementaryos/files/unstable/"), it has the Saucy LTS Enablement Stack build in.
It has "kernel 3.11.0-19-generic" and "OpenGL version string: 3.0 Mesa 9.2.1, OpenGL shading language version string: 1.30"

Officially I can't recommend that you install it ( have only tried it live myself ) but what you do is completely up to you ;)
Try it live first to see if it works.

---

### Post by jbaerboc on 2014-04-13
Hmm good to know Stinger, I may give it another shot in the future. Right now I'm surprized and amazed I'm enjoying using Unity. Have always been against it but with this 14.04 Beta 2 I actually almost *gasp* like it. But I have a certifiable case of the distro jumps so I'll circle back around to ElementaryOS at some point for sure. I did like the overall design concept.

---

