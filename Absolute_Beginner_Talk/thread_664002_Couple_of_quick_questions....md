---
title: "Couple of quick questions..."
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by DanielJackins on 2008-01-10
So first off, for some reason I can't;

A) View any videos on the internet

or

B) View DVD's on my computer (burned ones, at least)

Any common solution to these problems I am missing?

Thanks for any help

edit: Very sorry about that

---

### Post by yabbadabbadont on 2008-01-10
```
sudo apt-get install ubuntu-restricted-extras
```
should take care of A) and B).  Discussions of piracy are not allowed on these forums, so you might want to edit your post before you receive an infraction from a moderator.

---

### Post by jan quark on 2008-01-10
try to install

flash for your browser, I assume firefox just search the forum for flash installation

the needed codecs for viewing videos, and the wright video player
I use totem gstreamer and the appropiate codec libraries
just search in the add/remove application

to watch dvd you need to read trough the restricted formats on the ubuntu wiki
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

playing
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

ripping
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)
but do not do illegal stuff and do not ask for help for illegal stuff

---

### Post by DanielJackins on 2008-01-10
I got this when I tried to do the apt-get thing, so I'm assuming it's not the problem

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.

---

### Post by oldos2er on 2008-01-10
You need to enable the Medibuntu repository before apt-getting the restricted extras. See [https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29)

---

### Post by DanielJackins on 2008-01-11
Tried the things, but still doesn't seem to work :(

---

### Post by DanielJackins on 2008-01-11
Any other suggestions?

---

### Post by Sef on 2008-01-11
I believe on the newer DVDs, there is a different lock and so they don't play on Linux.

---

### Post by DanielJackins on 2008-01-12
I'm not TOO too worried about the DVDs not playing, more movies on the internet.

---

### Post by mcduck on 2008-01-12
Make sure you have installed flash plugin, w32codecs (from medibuntu) and all gstreamer0.10-plugin packages. THen I recomend using the mplayer-plugin to show videos on websites, it's the one I've found to work best. So install that, and remove totem-plugin.

With these things installed I've been able to play every video on web that doesn't use some nasty DRM.

---

### Post by DanielJackins on 2008-01-13
So how would I go about obtaining those? Sorry, I am completely clueless as of yet when it comes to Linux. Thanks for the patience.

---

### Post by DanielJackins on 2008-01-13
Still haven't been able to find out how :(

---

### Post by mivo on 2008-01-13
> **Sef said:**
> I believe on the newer DVDs, there is a different lock and so they don't play on Linux.

Does anyone know of examples? I have a relatively large number of bought DVDs, and just got a stack of ten DVDs of relatively new US releases in the mail from a friend, and they all seem to play just fine. I'd hate to buy, especially if it is an import, a DVD and then find out it doesn't work on a Linux box. (It's certainly a good way to turn a buyer into a downloader).

---

### Post by DanielJackins on 2008-01-14
Is there some obvious step I'm missing? I still can't view any flash movies or games, or watch most videos on the internet.

---

### Post by mivo on 2008-01-14
Are you using the 64-bit version of Ubuntu?

---

### Post by quinnten83 on 2008-01-14
Hi, 
I know the installation of flash from the repos has been broken lately. something to do with the MD5checksum. I haven't figured out how to fix it yet, but I can't say I have really looked.
search google for: "install flash in ubuntu 7.10" Something will turn up.
I believe there is a bug report on launchpad, just not sure if there is a solution yet.

---

### Post by lswest on 2008-01-14
you have to install flash manually by downloading the installer off the adobe site.  There are quite a few posts on this forum of how to do that, should be easy enough to find.

---

### Post by DanielJackins on 2008-01-14
Thank you for all the replies! Things seem to be working great now, very much appreciated :)

---

