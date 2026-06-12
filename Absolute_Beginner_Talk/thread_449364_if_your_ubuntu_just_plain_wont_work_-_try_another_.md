---
title: "if your ubuntu just plain wont work - try another distro"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by daverich on 2007-05-20
heya.

Ubuntu works great on my laptop but my desktop just wouldn't have it - an incompatibility with my video i think.

After a day of wrangling i was about to install xp when i figured i might as well try another distro first.

Opensuse worked right off the bat.

I'm a linux newbie and im sure the nvidia Geforce2 MX 440 probably could be made to work in ubuntu - but if you're like me and just want linux to work then give another distro a go.

I'll certainly be keeping ubuntu on my laptop though :)

Kind regards

Dave Rich

---

### Post by saphil on 2007-05-20
excellent advice!

An expert (for instance the experts who reverse-engineet video drivers to work on SuSE) might be able to get your video working, but there is certainly no reason to moan that you aren't that expert (yet).  Like Torvalds says in his biography _Do it for fun._ 

Happy Sunday!

Wolf

---

### Post by Borzo on 2007-05-20
Have you tried the nvidia drivers... i have GeForce2 MX working on ubuntu 6.10 on an old system like a charm.

---

### Post by Kobalt on 2007-05-20
Very constructive thread indeed... 
FYI : the GeForce2 MX cards work with the [nvidia-glx-legacy]("http://www.nvidia.com/object/IO_32667.html") drivers, which is in the repos of course.

---

### Post by daverich on 2007-05-20
> **Kobalt said:**
> Very constructive thread indeed... 
FYI : the GeForce2 MX cards work with the [nvidia-glx-legacy]("http://www.nvidia.com/object/IO_32667.html") drivers, which is in the repos of course.

not for me they didn't

trust me i tried the nvidia drivers many times - did all the xorg hoop jumping - no luck.

I'll try ubuntu again when i get another video card - but seriously, it's not worth that much hassle when another distro will work no problem and ubuntu wouldn't even boot half the time. like i said before it's great on this laptop, just not my desktop.

-edit- interestingly suse said it wanted the nvidia drivers to enable desktop effects, but when i said ok to that it then told me that 3d acceleration wouldn't work on my video card. Maybe this is the problem? - could I suppose be the 3d part of my video is faulty?

Kind regards

Dave Rich

---

### Post by Simran on 2007-05-20
> I'm a linux newbie and im sure the nvidia Geforce2 MX 440 probably could be made to work in ubuntu 

I have a desktop with this video card and it worked no problems, got beryl running smooth as a whistle. The restricted drivers manager thing in 7.04 sorted it all out :)

Simran

---

### Post by Kobalt on 2007-05-20
I doubt the 3D of your video card is the guilty part... 
There are actually two legacy drivers : the 1.0-96xx and the 1.0-71xx one. The legacy drivers proposed in Feisty have no proper acceleration. One possible solution then would be to compile the 8776 drivers for Feisty manually. Check [this]("http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/") out for more info.

---

### Post by daverich on 2007-05-21
> **Simran said:**
> I have a desktop with this video card and it worked no problems, got beryl running smooth as a whistle. The restricted drivers manager thing in 7.04 sorted it all out :)

Simran

Tried that today - no luck - well, i did have luck when i loaded in rescue mode, loaded those drivers in, rebooted - then it worked great, until i rebooted again when ubuntu just wouldn't load the gui.

suse is great, but it's a bit too complicated for me on the networking side (I just want to copy some files from one computer to another - sheesh)

hopefully ubuntu/nvidia will sort out this driver situation - it's a real pain. Am i correct in thinking that if suse can manage it well, then because it's all open ubuntu could take the bits that make suse work right off the bat with my video card?

Kind regards

Dave Rich

---

