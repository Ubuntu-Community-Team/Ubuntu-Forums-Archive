---
title: "Cannot Play DVDs - I want AUTOMATIX BACK!!!!!"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-10-15
Well after all my experience with UBUNTU, I finally decided to put Gutsy on a second computer. I used Automatix2 on my first ione and all sound and video worked. On the new box I downloaded everything I could think of the Ubuntu-restricted-packages, the libfmpeg2, gstreamer, mplayer, etc. but alas... my firefox streams videos beautifully, but no DVDs in Totem.

Can anyone please help??:-({|=

---

### Post by Lord Illidan on 2007-10-15
You need the libdvdcss2 package and preferably totem xine.

So let's install libdvdcss2 first. Close apt-get/synaptic and type this in a terminal.

```
 sudo sh /usr/share/doc/libdvdread3/install-css.sh
```

And then, install totem-xine

```
sudo apt-get install totem-xine
```

---

### Post by santy_kushwaha on 2007-10-15
probebly need to install some other packages in order to run dvd

---

### Post by bodhi.zazen on 2007-10-15
See if this helps :

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

Also, FYI, you might want to look at Mint : [http://linuxmint.com/](http://linuxmint.com/)

Mint is Ubuntu + a number of extras ;)

---

### Post by devilears on 2007-10-15
download & install AUTOMATIX from here: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
This makes it EASY to install all CODECS etc

---

### Post by anaconda on 2007-10-15
Or use Linux Mint, which is ubuntu with all codecs etc. preinstalled.

---

### Post by FuturePilot on 2007-10-15
Wow! I had no clue such a thing existed. I'll have to remember this.
```
sudo sh /usr/share/doc/libdvdread3/install-css.sh
```
I learn something new everyday!:lolflag:

---

### Post by k3lt01 on 2007-10-15
I had similar trouble the other day, but today I put Gladiator into my laptop, Totem asked to download Codecs, it did and now my laptop plays DVDs.

Reboot your machine and try again, thats what I did and it works now:)

---

### Post by hyper_ch on 2007-10-15
Automatix is not recommended for installation and it's not needed for installation of other software.

---

### Post by scwinn on 2007-10-15
So many answers and things to read. I love this community!

As for Linux Mint.... I wanted to like it, it seemed like a good idea, BUT I could never get my network working. I did things that on any other distribution I have tried even UBUNTU that worked out of the box, but not on Mint, like configure my network. So Mint is a pass for me.

As for Automatix, I have deep respect for anyone who has mastered the command line, and understands how and where to find CODECS etc. Unfortunately, I do not have the desire to do anything else but click a button and have some intelligent tool do all of the hard stuff for me. Automatix was great for a Newbie making a transition away from Microsoft and heading into new territory! I hope it returns. I find myself preaching LINUX, especially UBUNTU to friends, family, and coworkers all of the time. Part of the allure of computing today is that computers have become appliances. I know that it sucks, but that is what they are.

For LINUX to become mainstream, it has to deliver on being simple. And then a user like me, can slowly build on it over time. It is only when you look under the covers a bit, you start to realize how powerful and infinite Linux really is. But in the spirit of Open Source, we need the freedom to also have the environment be simple to install, to use, and to enjoy!

I will try the solutions posted here. And hopefully we can encourage the filk at the automatix to keep expending their efforts not only to UBUNTU going forward, but also other distros. This tool really made LINUX easy to configure and actually use. I am sorry it has changed course so much.

---

### Post by FredB on 2007-10-15
Just use the libdvdcss code. You can find a mirror on medibuntu. No need of the *crappy* automatix script.

[http://medibuntu.sos-sts.com/repository-old.php](http://medibuntu.sos-sts.com/repository-old.php)

Well, for now, no gutsy repository, but soon I think. And no need of totem-xine either.

---

### Post by mc4man on 2007-10-15
you can get it at
[http://bapoumba.wordpress.com/2007/10/02/medibuntu-non-free-codecs-for-gutsy/](http://bapoumba.wordpress.com/2007/10/02/medibuntu-non-free-codecs-for-gutsy/)

---

### Post by FredB on 2007-10-15
> **mc4man said:**
> you can get it at
[http://bapoumba.wordpress.com/2007/10/02/medibuntu-non-free-codecs-for-gutsy/](http://bapoumba.wordpress.com/2007/10/02/medibuntu-non-free-codecs-for-gutsy/)

Thanks for the info.

---

