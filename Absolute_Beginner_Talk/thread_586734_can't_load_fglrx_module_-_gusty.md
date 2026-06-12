---
title: "can't load fglrx module - gusty"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by danm-koder on 2007-10-22
Hi everyone.

I was running feisty on my laptop wich has an ATI Radeon Xpress 200M (I know, not very friendly to Linux :P ) but after some days of work, I got the 3D workin fine with the fglrx driver... And then, yesterday I upgraded to gusty from the Internet... Everything went fine until I rebooted... then I just got a terminal and a message that said something like this :

"Xorg failure, can't load module fglrx, device not present" or something like that... 
Anyway, I changed the xorg.conf and now I am using the "radeon" driver... which works fine... but I'd really like to get the fglrx driver to work...

So, at the moment I'm at work but if anyone has some ideas, they are very welcome, anyhow I hope I'll get it to work within the week, and I'll let you know how I did it...

Thanks.

---

### Post by jimerickso on 2007-10-22
if you are using gnome try system >administration > restricted drivers manager and enable it from there.

---

### Post by danm-koder on 2007-10-23
I solved It! It turns out that the version of the fglrx driver in the repo is 8.33 which needs Xorg 7.1, and since Gusty runs Xorg 7.2 it crashes... So I downloaded de the lastest version of the fglrx from the ATI website and voilá!!!! There you go... 3D compatibility and everything...

---

