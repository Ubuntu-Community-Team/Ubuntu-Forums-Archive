---
title: "Weird Mac install problem"
date: 2005-08-10
forum: Apple PPC Users
---

### Post by jaqkar on 2005-08-10
Hi

WHen trying to install Ubuntu on an oldworld mac during the setup it gives a red screen saying an installation step failed and says it could not configure timezone and it seems I cant really skip this step, any ideas?

---

### Post by leverknight1 on 2005-08-10
you should be able to it isnt realy critical to the operation of any of the processes

---

### Post by jaqkar on 2005-08-11
Yeah I know but I cant get pass it. Sad thing is I dont get this when I install with Debian, I have other issues with it but not the timezone one. I really wanna use Ubuntu.

---

### Post by Tommy on 2005-08-11
[QUOTE=jaqkar]WHen trying to install Ubuntu on an oldworld mac during the setup it gives a red screen saying an installation step failed and says it could not configure timezone and it seems I cant really skip this step, any ideas?[/QUOTE]

Yes I know exactly what you're seeing. Hoary (the latest version of Ubuntu) will NOT install successfully on a Wallstreet -- you need to download the previous release "Warty," install it, and then do a dist-upgrade to Hoary. You will have to dig around on the mirrors to find it but it's still downloadable.

For example, go to [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/) and pick your closest mirror. For me it would be the US at [http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/) so I change that URL to [http://us.releases.ubuntu.com/releases/4.10/](http://us.releases.ubuntu.com/releases/4.10/) and download the image from there.

P.S.: I haven't bothered filing a bug about the install problem because I believe Ubuntu doesn't try to support oldworlds. I suppose you or I could file one anyway. IMHO Ubuntu is much nicer than a stock Debian install on my Wallstreet. The serial ports work without fiddling so I can sync my Palm, the PCMCIA slots work -- though you can't eject the cards :-( , and after working around a small bug laptop-mode works well [https://bugzilla.ubuntu.com/show_bug.cgi?id=12701](https://bugzilla.ubuntu.com/show_bug.cgi?id=12701)  -- but OVERALL Ubuntu is VERY usable.

---

### Post by jaqkar on 2005-08-11
Hi Tommy

Great so this is a bug, thought it might be something wrong with the mac. I will look for Warty and try that, I will much rather go for Ubuntu. 

Thanks for the reply.

PS. I sent you a pm.

---

