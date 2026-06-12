---
title: "[SOLVED] Too much GRUB."
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by DaraJava on 2007-11-18
Hello I've been having some problems as of yesterday. My brother was messing on my laptop just doing normal stuff y'know internet etc. And i think he restarted it or something.

He gave it back to me and the screen was dim. When I try to make it bright again (using fn + up arrow) It doesn't work. please help. :confused:

Now the worst thing is that GRUB takes so long to load. 2-3 mins on average. This only started happening when I got my laptop back from my brother. 

I have another problem with my internet that happened a while before this. It actually started happening since I upgraded to Gutsy I think not 100% sure though. Anyway the problem is this: sometimes when I turn on my laptop the internet doesnt work. It says I have full signal and that I'm connected to my router but there is nothing that I can do to make it work except restarting it. 

If I could get any help at all with any of these problems it would be great,

Thanks,

DaraJava

---

### Post by staticvoid on 2007-11-18
List specific info on your wireless card and what kind of internet you have and stuff :)

check "System>Perefrences>Keyboard Shortcuts" to get your dimmness and lightness keys working again. Although... it might be a hardware problem...? 

sv

---

### Post by MegaJim on 2007-11-18
Grub slow booting happend to my laptop after the last set of 7.10 updates rolled out about a week ago, the problem was I had updated ubuntu and rebooted to windows, but one of these updates did something to the journalling I think, because when I next logged in the filesystem was not clean, despite clean shutdows and windows not having access to the Linux partition.

After one clean boot and shutdown grub has gone back to being fast as greased lighting, so I would try just doing a clean startup/shutdown and maybe a diskcheck.

---

### Post by DaraJava on 2007-11-18
I am using a netopia router and my wireless card is a dell a/b/c or something.

I looked in keyboard shortcuts and i couldnt find a shortcut for brigtness. :confused:

I will do a clean shutdown and restart and let you know how it goes. 

Thanks all!

Dara

---

### Post by DaraJava on 2007-11-20
Anyone?

---

### Post by DaraJava on 2007-11-21
I solved my slow GRUB problem. I had a windows vista install disc in my CD drive and that was making it slow. If I put in any other disc it works just fine.

---

