---
title: "Reboot ubuntu"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by renesis317 on 2008-04-01
i am a complete ubuntu noob. i installed ubuntu on my system and found that my xfi creative music extreeme card didnt work. So i went ahead and customized the kernel without backing anything up (as i was told to do by a post) and now i cant acess the drivers that came with ubuntu. is there a quick and easy way to restore ubuntu to the settings on the live cd?

---

### Post by shadowtroopers on 2008-04-01
can you boot up your system normally without using live cd?

---

### Post by renesis317 on 2008-04-01
yes, but wireless, video, sound drivers are all gone

---

### Post by kpkeerthi on 2008-04-01
> **renesis317 said:**
> i am a complete ubuntu noob. i installed ubuntu on my system and found that my xfi creative music extreeme card didnt work. So i went ahead and customized the kernel without backing anything up (as i was told to do by a post) and now i cant acess the drivers that came with ubuntu. is there a quick and easy way to restore ubuntu to the settings on the live cd?

Mind posting a link to the HOW-TO you followed so I can see if it can be reversed?

EDIT: Also change the post's title to something relevant to your problem

---

### Post by riven0 on 2008-04-01
> **renesis317 said:**
> yes, but wireless, video, sound drivers are all gone

I'm guessing you don't have an older kernel version on your grub screen. So, when you boot up, do you get to the terminal. If so, log in and try re-installing the kernel. For example, if you're using Feisty: > sudo apt-get install linux-image-2.6.20-16-generic . Unfortunately, I've forgotten what kernel numbers the newer 7.10 and 8.04 uses. :(

---

### Post by thisiam on 2008-04-01
I haven't screwed up Ubuntu bad enough to use recovery mode yet, never used it or even booted to it. perhaps i should to take a look at to see what its all about, but if this happened to me i would look into recovery mode.

---

### Post by renesis317 on 2008-04-01
thanks guys...

these are the directions i followed...method 2
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

i got the old kernel to boot. i cant get to my 1680 1050 resolution anymore....is there any way i can quickly start from scratch? if not, how do i set the old kernel as default?

---

### Post by renesis317 on 2008-04-01
i cant get the live cd to boot either...it says that my drive is not ready.

---

