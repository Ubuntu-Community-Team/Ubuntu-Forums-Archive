---
title: "Still can't play dvd"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by stoli150 on 2007-12-23
Is there a how 2 on getting DVD's to play for ver 7.10 ? I have installed restricted drivers. gxine totem  movie player and it still wont play a dvd. Every time I upgrade the OS It takes me hours to get the dvd player to work and it drives me batty.

---

### Post by PeterJS on 2007-12-23
The element that you're missing is a rather interesting one, the dvd decrypter itself, libdvdcss2. Ubuntu can't directly distribute or support libdvdcss because it's illegal in the States. How ever the medibuntu group has done a good job of being off US soil and not having any official ties to Canonical. 
Check this out:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by thecure on 2007-12-23
> **stoli150 said:**
> Is there a how 2 on getting DVD's to play for ver 7.10 ? I have installed restricted drivers. gxine totem  movie player and it still wont play a dvd. Every time I upgrade the OS It takes me hours to get the dvd player to work and it drives me batty.

If you don't want to mess with getting dvd decryption just download another player like VLC and it'll play DVD's without a problem. [http://www.videolan.org/vlc/]("http://www.videolan.org/vlc/")

---

### Post by PeterJS on 2007-12-23
> **thecure said:**
> If you don't want to mess with getting dvd decryption just download another player like VLC and it'll play DVD's without a problem. [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)


I knew Video Lan built, developed, and hosted libdvdcss, but didn't know that it was statically built in to VLC. I don't mean to insult, but do you have a source for that, that seems like kind of a big deal.

---

### Post by stoli150 on 2007-12-23
> **PeterJS said:**
> The element that you're missing is a rather interesting one, the dvd decrypter itself, libdvdcss2. Ubuntu can't directly distribute or support libdvdcss because it's illegal in the States. How ever the medibuntu group has done a good job of being off US soil and not having any official ties to Canonical. 
Check this out:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[I]synaptic says I have libdvdcss2 installed
[/I]

---

### Post by stoli150 on 2007-12-23
> **thecure said:**
> If you don't want to mess with getting dvd decryption just download another player like VLC and it'll play DVD's without a problem. [http://www.videolan.org/vlc/]("http://www.videolan.org/vlc/")

I installed VLC and it starts when I try to the open the DVD a menu opens up I choose the dvd  DVD option then the program crashes...

---

### Post by Hugo.roy on 2007-12-23
I have exactly the same problem.

I've installed restricted things, libdvdread3, VLC, I even tried to change the region (with regionset). There are a lot of movies that i can read, but there are a lot that i can't read : Barry Lindon and A Fistful of Dollars don't work !

When I try to open directly the folder and play the .vob files one by one, the files don't wan't to get started.

I have to boot on Windows XP for that (!!!! argh!!!!)

For info I have Ubuntu 710 64 bits on a Toshiba tecra M9 Laptop with Intel GM...chipset.

---

