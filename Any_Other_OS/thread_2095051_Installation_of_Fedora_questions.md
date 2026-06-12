---
title: "Installation of Fedora questions"
date: 2012-12-15
forum: Any Other OS
---

### Post by UltimateCat on 2012-12-15
Hi::D

I read all of the documentation on How to install Fedora 17-X86_64 XFCE.
I read the Rescue Mode documentation as well in case the install doesn't go well.
[http://docs.fedoraproject.org/en-US/Fedora/17/html/Installation_Guide/index.html](http://docs.fedoraproject.org/en-US/Fedora/17/html/Installation_Guide/index.html)

I plan to install Fedora on my Sony Vaio that has an i5 processors 6GB HDD and a Radeon 7500 graphics card with Win's 7 on it.

I'm thinking that I can allocate 20GB for the EXT3 '/' journaling file system and 4GB for the swap.  Do you think 4GB's to is much should I go with 2GB instead?

Also, do  I need to read the Red Hat documentation as well to understand Fedora?

Should I go with AMD drivers if needed since it's a brand new custom built laptop?  (if graphics is even an issue)

Any help and advise would be appreciated-
Thanks in advance;)

---

### Post by chadk5utc on 2012-12-16
> **UltimateCat said:**
> Hi::D

I read all of the documentation on How to install Fedora 17-X86_64 XFCE.
I read the Rescue Mode documentation as well in case the install doesn't go well.
[http://docs.fedoraproject.org/en-US/Fedora/17/html/Installation_Guide/index.html](http://docs.fedoraproject.org/en-US/Fedora/17/html/Installation_Guide/index.html)

I plan to install Fedora on my Sony Vaio that has an i5 processors 6GB HDD and a Radeon 7500 graphics card with Win's 7 on it.

I'm thinking that I can allocate 20GB for the EXT3 '/' journaling file system and 4GB for the swap.  Do you think 4GB's to is much should I go with 2GB instead?

Also, do  I need to read the Red Hat documentation as well to understand Fedora?

Should I go with AMD drivers if needed since it's a brand new custom built laptop?  (if graphics is even an issue)

Any help and advise would be appreciated-
Thanks in advance;)

Most would normally suggest that you Double the amount of ram you have for swap. Additional documentation is up to you. As for drivers the OS is pretty main stream and should automatically load the drivers youll need, although you may have to make a minor tweek or two.

---

### Post by UltimateCat on 2012-12-17
Thanks for the reply.

What minor tweaks are you referring to?

---

### Post by buzzingrobot on 2012-12-18
Take a look at the Fedora 17 common bugs list, just in case: [http://http://fedoraproject.org/wiki/Common_F17_bugs]("http://http://fedoraproject.org/wiki/Common_F17_bugs").

No, there's no reason to read the Red Hat documentation.  The current Red Hat release and Fedora 17 are significantly different. Red Hat's documentation is excellent, but so is Fedora's.

Research how to install AMD drivers on Fedora before beginning the install.  Fedora is adamant about not including proprietary software.

---

### Post by QIII on 2012-12-18
A swap partition double the size of your RAM is entirely too much and the 2x rule used to apply back in the days when RAM was was limited and expensive.  With 6GB of RAM you should be able to set swappiness very low and not ever get near to using all of your RAM

If you are using a laptop, you only need a swap partition large enough to contain the state of the RAM, plus a little extra, for when you hibernate.  Say 1.1x to 1.25x RAM.

I don't even use a swap partition most of the time on my desktops.

I would try the default open source Radeon driver first, but the proprietary driver will probably work better.

---

### Post by BBQdave on 2012-12-19
> **UltimateCat said:**
> I plan to install Fedora...

You make want to check out [http://rpmfusion.org/](http://rpmfusion.org/)

For example, if you want to install **VLC**, you will need to install *rpmfusion-free* :)

---

### Post by UltimateCat on 2012-12-20
> **QIII said:**
> A swap partition double the size of your RAM is entirely too much and the 2x rule used to apply back in the days when RAM was was limited and expensive.  With 6GB of RAM you should be able to set swappiness very low and not ever get near to using all of your RAM

If you are using a laptop, you only need a swap partition large enough to contain the state of the RAM, plus a little extra, for when you hibernate.  Say 1.1x to 1.25x RAM.

I don't even use a swap partition most of the time on my desktops.

I would try the default open source Radeon driver first, but the proprietary driver will probably work better.

During the install I allocated 20GB for Fedora "/"
4GB for the  swap

Amazingly I didn't even have to look for a driver.
The system booted and had the internet connection immediately-

Thanks

---

### Post by UltimateCat on 2012-12-20
> **BBQdave said:**
> You make want to check out [http://rpmfusion.org/](http://rpmfusion.org/)

For example, if you want to install **VLC**, you will need to install *rpmfusion-free* :)

Thanks for the heads up.
I appreciate that because I would like to install VLC.

BTW flash (Adobe) is a minor problem in Fedora-
Having issue's getting it working-

---

### Post by UltimateCat on 2012-12-20
> **buzzingrobot said:**
> Take a look at the Fedora 17 common bugs list, just in case: [http://http://fedoraproject.org/wiki/Common_F17_bugs](http://http://fedoraproject.org/wiki/Common_F17_bugs).

No, there's no reason to read the Red Hat documentation.  The current Red Hat release and Fedora 17 are significantly different. Red Hat's documentation is excellent, but so is Fedora's.

Research how to install AMD drivers on Fedora before beginning the install.  Fedora is adamant about not including proprietary software.


Thanks for advising not to read the RHEL documentation-
It's overwhelming!

I had great results with the install. Didn't even have to mess with the AMD drivers-
After the install; first boot was a dream!:popcorn:

---

### Post by BBQdave on 2012-12-20
> **UltimateCat said:**
> BTW flash (Adobe) is a minor problem in Fedora-
Having issue's getting it working-

I believe you will need rpmfusion *non-free*.

Though I usually just download the flash player - *.rpm* directly from Adobe Software site.

---

### Post by UltimateCat on 2012-12-22
> **BBQdave said:**
> I believe you will need rpmfusion *non-free*.

Though I usually just download the flash player - *.rpm* directly from Adobe Software site.

At first the terminal confirmed that Flash was installed. I didn't understand why it wasn't working. May have had the wrong <package_.rpm>
Finally got it working! LOL!

I opened the terminal and ran:
[CODE]Yum install flash-player
/CODE]

And that did the trick.
I'm able to watch videos now- Thanks

---

### Post by BBQdave on 2012-12-22
> **UltimateCat said:**
> I'm able to watch videos now

With a fresh Fedora install: I first update, install *rpmfusion-free*, manually install Fluendo mp3 codec pack and adobe flash player, and then finally add my favorite applications.

The Fluendo mp3 codec pack is a free download as well as the adobe flash player. Adobe Flash player, from adobe's site, gives me configuration choices for how the flash player will be used - privacy settings mainly.

I install the Fluendo mp3 codec pack for older mp3 files that I have, though I would recommend ogg-vorbis. I am in the process of ripping my CD's into ogg files, to me, it is a better sound quality.

Fedora is different than Ubuntu in that you put it together for what you need. Ubuntu has many applications and functions out of the box. But in the end, they both get you to a nice Linux distro :D

---

