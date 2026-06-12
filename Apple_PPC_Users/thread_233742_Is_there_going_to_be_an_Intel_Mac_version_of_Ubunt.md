---
title: "Is there going to be an Intel Mac version of Ubuntu?"
date: 2006-08-10
forum: Apple PPC Users
---

### Post by cobbweb on 2006-08-10
Hi, 
  I was wondering if anyone here knows if there is going to be a Intel Mac version of Ubuntu? I use a MacBook and the only way I can get Ubuntu to work on my machine is to use Parallels. The only thing is Parallels still isn't like having Ubuntu dual booted. Some features are subject to my OSX. Thanks, 

 Cobbweb

---

### Post by jedsen on 2006-08-10
The PPC version of Ubuntu is not Apple-specific, so there won't be a Apple-specific Intel version. There are, however, several Mactel specific kernel patches to get (almost) everything working.

---

### Post by cobbweb on 2006-08-10
cn i get a version of ubuntu that default installs the kernals with installation? 

 Cobbweb

---

### Post by Tofu on 2006-08-10
It seems to be taking a long time to get an official Linux distro that installs itself onto an Intel Mac.

I don't mean to sound pushy, but I'm curious to know why it takes so long.

When I Google the topic, I just find news articles from Jan/Feb 2006, with Red Hat announcing its plans.

There are other threads in this forum where clever people have got Ubuntu going on an Intel Mac, but it is too hard for beginners and Linux novices.

I haven't heard how the progress is going for Linux on Intel Macs. I wonder what the ETA is?

---

### Post by jedsen on 2006-08-11
> **Tofu said:**
> It seems to be taking a long time to get an official Linux distro that installs itself onto an Intel Mac.

I don't mean to sound pushy, but I'm curious to know why it takes so long.

When I Google the topic, I just find news articles from Jan/Feb 2006, with Red Hat announcing its plans.

There are other threads in this forum where clever people have got Ubuntu going on an Intel Mac, but it is too hard for beginners and Linux novices.

I haven't heard how the progress is going for Linux on Intel Macs. I wonder what the ETA is?
The Ubuntu alternate install CD does everything you need done (eg, lilo), besides xgl. Most of the work for the Intel macs needs to be done at the kernel level, and it won't be until 2.6.18 that we see suspend working without a patch, and who knows how long until the remote and camera patches are included, if ever. The great thing about ubuntu is it will probably have all these patches by edgy eft in a few months.

---

### Post by hajk on 2006-08-11
> **cobbweb said:**
> Hi, 
  I was wondering if anyone here knows if there is going to be a Intel Mac version of Ubuntu? I use a MacBook and the only way I can get Ubuntu to work on my machine is to use Parallels. The only thing is Parallels still isn't like having Ubuntu dual booted. Some features are subject to my OSX. Thanks, 

 Cobbweb

It is not difficult to install Ubuntu on the HD of a MacBook in a dual-boot setup with the rEFIt bootmanager. I have just done this myself, pulling a lot of info together from various threads on this forum, see my detailed installation report (PDF) on [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk").

Not everything works perfectly with the current 2.6.15-26 kernel, such as the wireless connection that needs a bit of manual tweaking everytime you 
boot. But most of these little annoyances are only a kernel update or two away, in my opinion. Try the install, you won't regret it.

---

