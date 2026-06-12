---
title: "K3b Problem"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Darth_Maul on 2007-06-08
I opened it up and got this message

Mp3 Audio Decoder plugin not found.
K3b could not load or find the Mp3 decoder plugin. This means that you will not be able to create Audio CDs from Mp3 files. Many Linux distributions do not include Mp3 support for legal reasons.
Solution: To enable Mp3 support, please install the MAD Mp3 decoding library as well as the K3b MAD Mp3 decoder plugin (the latter may already be installed but not functional due to the missing libmad). Some distributions allow installation of Mp3 support via an online update tool (i.e. SuSE's YOU).

---

### Post by starcraft.man on 2007-06-08
Open up a terminal (Applications Accessories > Terminal) and paste this in:

```
sudo aptitude install libk3b2-mp3  
```

Problem solved. You have to specify to install it yourself. It will then let you make audio cds with MP3.

Have fun Mr. Sith :D.

---

### Post by Darth_Maul on 2007-06-08
Hey thanks

---

### Post by starcraft.man on 2007-06-08
> **Darth_Maul said:**
> Hey thanks

No problem. Jedi or Sith, we are friendly with all and give help to any :D.

---

### Post by daschmidty on 2007-06-08
I have a somewhat related question. How do I go about ripping a cd to mp3 files? Everyone always posts "just install lame" but installing lame does not install any corresponding plugin for k3b, and there is still never a menu entry in the rip dialog to encode as mp3. Just wondering on this one, in the meatime i will use kaudiocreator.

---

### Post by forestpixie on 2007-06-08
you can look in add/remove and search for rip

I have grip but haven't used it yet in anger.

---

### Post by Quinn The Eskimo on 2007-07-01
> **starcraft.man said:**
> Open up a terminal (Applications Accessories > Terminal) and paste this in:

```
sudo aptitude install libk3b2-mp3  
```

Problem solved. You have to specify to install it yourself. It will then let you make audio cds with MP3.

Have fun Mr. Sith :D.


thanks... saved me from starting a thread:p

---

### Post by Swampfox on 2007-07-02
Thank you.  Just ran into this problem with a fresh install of Ubuntu Studio.

---

### Post by mneisen on 2007-07-03
Unfortunately, this:

```
sudo aptitude install libk3b2-mp3  
```

did not solve the problem in my case. I run Kubuntu Feisty Fawn and had already installed libk3b2-mp3. Juts to be on the safe side, I removed the package and re-installed it. Nada.

In K3b, I can rip an Audio CD without problems, but I can only encode the files as wave or OGG - which will not play on an iPod.

So, what did I do wrong? Are there any other packages I might lack?

Thanks for your help!

Regards
Martin

---

### Post by Slammer64 on 2007-07-03
Try installing the version of k3b from [www.getdeb.net](www.getdeb.net) download and install k3b libk3b2 and libk3b2-mp3, it's version 1.0.2 and it solved my problems with burning to mp3.

---

### Post by starcraft.man on 2007-07-03
> **mneisen said:**
> Unfortunately, this:

```
sudo aptitude install libk3b2-mp3  
```

did not solve the problem in my case. I run Kubuntu Feisty Fawn and had already installed libk3b2-mp3. Juts to be on the safe side, I removed the package and re-installed it. Nada.

In K3b, I can rip an Audio CD without problems, but I can only encode the files as wave or OGG - which will not play on an iPod.

So, what did I do wrong? Are there any other packages I might lack?

Thanks for your help!

Regards
Martin
[URL="http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs"]
Did you install the MP3 codecs themselves?[/URL]

MP3 support isn't included by default, ogg and wave are. Please follow that and ensure its done. If its still not there might have to edit it in manually.

Glad to see people using search feature and getting help.

---

### Post by mneisen on 2007-07-03
> **Slammer64 said:**
> Try installing the version of k3b from [www.getdeb.net](www.getdeb.net) download and install k3b libk3b2 and libk3b2-mp3, it's version 1.0.2 and it solved my problems with burning to mp3.

That solved my problem, thank you very much!

---

### Post by mneisen on 2007-07-03
> **starcraft.man said:**
> Did you install the MP3 codecs themselves?

Yes, I did. I have lame installed on my machine.

> 
MP3 support isn't included by default, ogg and wave are. Please follow that and ensure its done. If its still not there might have to edit it in manually.

I guess the real problem is that there was no lame config for the external encoder plugin in K3B. In the *deb package from getdeb, there is such a configuration.

Is this a slight glitch in the K3B package for Feisty?

> Glad to see people using search feature and getting help.

Well, part of my research activities are in the field of information retrieval - it would be very ironic if I did not use the search functionality. :-D

Regards, and thanks for all the help!
Martin

---

