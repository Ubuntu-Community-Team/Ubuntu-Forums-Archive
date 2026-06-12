---
title: "Can't play DVD's"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by SPQQKY on 2007-07-20
What do I need to play DVD's? I thought Movie Player would handle it but all I get is garble on the screen. Kaffeine and Ogle don't work either. Ogle crashes and Kaffeine says it couldn't find demux.

---

### Post by p_quarles on 2007-07-20
> **SPQQKY said:**
> What do I need to play DVD's? I thought Movie Player would handle it but all I get is garble on the screen. Kaffeine and Ogle don't work either. Ogle crashes and Kaffeine says it couldn't find demux.
Have you installed the codecs? Here's a how-to:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by nichipet on 2007-07-20
Try the instructions from here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by citadelgrad on 2007-07-20
Automatix is really the easiest way to setup DVD support. It also gives you the option to add many other useful restricted apps.
[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by p_quarles on 2007-07-20
> **citadelgrad said:**
> Automatix is really the easiest way to setup DVD support. It also gives you the option to add many other useful restricted apps.
[http://www.getautomatix.com/]("http://www.getautomatix.com/")
Automatix is also the easiest way to kill your OS. 

Use the link that nichipet and I gave you first.

---

### Post by ilowtf on 2007-07-20
> **p_quarles said:**
> Automatix is also the easiest way to kill your OS. 

Use the link that nichipet and I gave you first.


Why is it the easiest way to kill your OS?

---

### Post by citadelgrad on 2007-07-21
p_quarles: Why does Automatix kill Ubuntu?

---

### Post by SPQQKY on 2007-07-21
I've already done all of this, which is why I don't understand why it's not working.

---

### Post by nichipet on 2007-07-21
Okay. You used Add/Remove for Ubuntu restricted extras, then added the Medibuntu repository to your sources.list, then added libdvdcss2 to your system? Did any of these give any output at all, whether an error or a confirmation? What happens when you try this in the command line:

```
kaffeine -d /path/to/your/dvd/drive
```

The path may be /dev/dvd

---

### Post by SPQQKY on 2007-07-21
> **nichipet said:**
> Okay. You used Add/Remove for Ubuntu restricted extras, then added the Medibuntu repository to your sources.list, then added libdvdcss2 to your system? Did any of these give any output at all, whether an error or a confirmation? What happens when you try this in the command line:

```
kaffeine -d /path/to/your/dvd/drive
```

The path may be /dev/dvd
I used Add/Remove for ubuntu restricted extras, but I can't for the life of me figure out how to add medibuntu. I don't see it anywhere. How do I get the libdvdcss2?

---

### Post by SPQQKY on 2007-07-21
```
dominic@dominic-desktop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
dominic@dominic-desktop:~$ 

```

I get this error and I have gone through all the steps in the guide verbatum.

---

### Post by lemonseed on 2007-07-21
go to [http://packages.medibuntu.org/pool/](http://packages.medibuntu.org/pool/)

go to free/

then libd/

then libdvdcss2/

then choose the file for whatever system you're using
   such as libdvdcss2_1.2.9-lplf3_i386.deb if your computer is a non-mac or non-64bit machine

---

### Post by SPQQKY on 2007-07-21
> **lemonseed said:**
> go to [http://packages.medibuntu.org/pool/](http://packages.medibuntu.org/pool/)

go to free/

then libd/

then libdvdcss2/

then choose the file for whatever system you're using
   such as libdvdcss2_1.2.9-lplf3_i386.deb if your computer is a non-mac or non-64bit machine
That does me no good. It says this version is already installed, as I thought it was but I still cannot play a DVD.

---

### Post by lemonseed on 2007-07-21
I stumbled across this thread as I was trying to get my DVDs to play also. So far, I can play them but it says I'm watching cdrom1. I have a cdrom and a dvdrom on this machine but the movie is in the dvd drive. If I select Movie -> Play Disc"BIG_TROUBLE_IN_LITTLE_CHINA" it tells me it cannot play the media(DVD) because I don't have the appropriate plug-ins to handle. Well obviously I do since it sees and plays it as cdrom1. It is the legit store-bought dvd. I mean it plays and all but it bugs me to not have something work like it should. Maybe Totem Movie Player is a sub-par player? Any recommendations on a better one?

---

### Post by lemonseed on 2007-07-21
> **SPQQKY said:**
> That does me no good.

Why doesn't it do any good? It worked for me in that I can display the DVD now.

---

### Post by SPQQKY on 2007-07-21
> **lemonseed said:**
> Why doesn't it do any good? It worked for me in that I can display the DVD now.
Because like I said, it says it's already installed like I thought it was. I uninstalled Kaffeine, I put the DVD in one more time and Movie Player decided to start playing the disk. Ogle never would open it up, so I uninstalled that too. From now on, as long as it keeps working, I'll use Movie Player for DVD's and VLC for my .avi files. 

BTW, lemonseed, Big Trouble In Little China rocks. :guitar:

---

### Post by lemonseed on 2007-07-21
You're now able to watch the DVD using Totem Movie Player?

---

### Post by pyros on 2007-07-21
I've tried quite a few dvds in ubuntu, and I've learned two things:
1. totem (movie player) will only play dvds (for me) when they are inserted into the drive and autorun. 
2. when totem fails try vlc
3. when both fail... rip it to ogg.
but this of course a ymmv situation.

---

### Post by lemonseed on 2007-07-21
I installed VLC and it will play the DVD but if I try to skip to the next chapter it just goes back to the beginning.

---

### Post by SPQQKY on 2007-07-21
Okay, this is truly annoying. As pyros stated, totem is only working when I install the disc and autoruns and I don't get any menu, it just starts playing the first track and I cannot skip to the next track.
I cannot open a disk in VLC, it keeps directing me to all the VOB's and will only play a split second and then close.
Cripes, I just wanna watch a DVD. It's not like it's an illegal copy or anything.

---

### Post by pyros on 2007-07-21
> **SPQQKY said:**
> Okay, this is truly annoying. As pyros stated, totem is only working when I install the disc and autoruns and I don't get any menu, it just starts playing the first track and I cannot skip to the next track.
I cannot open a disk in VLC, it keeps directing me to all the VOB's and will only play a split second and then close.
Cripes, I just wanna watch a DVD. It's not like it's an illegal copy or anything.

In vlc, go to file>open disc, not open file, that should help.

---

### Post by pyros on 2007-07-21
(and the autorun only, no menus support in totem is a known issue(tm)

---

