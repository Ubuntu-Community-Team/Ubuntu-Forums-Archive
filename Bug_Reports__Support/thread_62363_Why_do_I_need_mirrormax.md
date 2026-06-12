---
title: "Why do I need mirrormax ?"
date: 2005-09-04
forum: Bug Reports / Support
---

### Post by d2_racing on 2005-09-04
Hello, I'm new with Ubuntu but not with Debian...

So, I have a special question regarding the backports.

Since I installed, I had some problems with the backports :

This is my /etc/apt/sources.list
```

#Les serveurs de l'Université de Sherbrooke
# Ubuntu CD-ROM (Hoary)
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Marillat (Vidéo)
#deb ftp://ftp.nerim.net/debian-marillat/ testing main

# Ubuntu binaire (Hoary)
deb http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary main restricted universe multiverse
deb http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary-security main restricted universe multiverse
deb http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary-updates main restricted universe multiverse

# Ubuntu sources (Hoary)
deb-src http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary main restricted universe multiverse
deb-src http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary-security main restricted universe multiverse
deb-src http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary-updates main restricted universe multiverse

#Ubuntu Backports (Hoary) Official
deb http://ca.archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
#deb-src http://ca.archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

# Ubuntu Backports (Hoary) avant que ca change pour ca.archive.ubuntu.com
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted


```

So since I wanted to install, Java,Azureus,Amule,Acroread....everythings was not found .
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

So, what is official with that deposite :

#Ubuntu Backports (Hoary) Official
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

To make sure that I can install what I wanted, I changed my sources.list with that :

```

#Les serveurs de l'Université de Sherbrooke
# Ubuntu CD-ROM (Hoary)
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Marillat (Vidéo)
#deb ftp://ftp.nerim.net/debian-marillat/ testing main

# Ubuntu binaire (Hoary)
deb http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary main restricted universe multiverse
deb http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary-security main restricted universe multiverse
deb http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary-updates main restricted universe multiverse

# Ubuntu sources (Hoary)
deb-src http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary main restricted universe multiverse
deb-src http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary-security main restricted universe multiverse
deb-src http://gulus.usherbrooke.ca/pub/distro/ubuntu/ hoary-updates main restricted universe multiverse

#Ubuntu Backports (Hoary) Official
#deb http://ca.archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
#deb-src http://ca.archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

# Ubuntu Backports (Hoary) avant que ca change pour ca.archive.ubuntu.com
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted


```

With mirrormax, I installed everythings...so is that because the soft are from hoary-extras....and if so, is there any official backports like deb [http://ca.archive.ubuntu.com/](http://ca.archive.ubuntu.com/) that I can use.

Thanks you in Advance.

Sorry for my bad English, but I understand 90% of that language....I read English, but my writting is very limited.

---

### Post by SilvioTO on 2005-09-11
Good question. In official hoary backports I don't find java, for example. I don't understand what's difference is between official backports and mirrormax...  :? 

Thanks for any explanation.

---

### Post by Spikey on 2005-10-04
Can anyone answer these questions? I think its safe to say alot of us are wondering why the Ubuntu developers would shutdown the mirrormax backports and cause all the grief that the Ubuntu community has seen lately. Half the packages arn't available in the "offical" backports and because of this move the ubuntuguide located at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) is no longer a valid / trusted resourse that can be used. I love ubuntu and i will continue to keep using it but the devs working on Ubuntu took a serious step backwords in the developmet of this piece of sofware. 

If i am mistaken and i seriously HOPE I AM. Please post all the repositories that are needed to replace the mirrormax backports. Bare in mind that i, as well as many other individuals have already added  "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse" to our sources.list file.



Thanks in advance

Spikey

---

### Post by mr_pouit on 2005-10-05
[QUOTE=SilvioTO]Good question. In official hoary backports I don't find java, for example. I don't understand what's difference is between official backports and mirrormax...  :? 
Thanks for any explanation.[/QUOTE]

i think they removed some packages like libdvdcss because they are not legal in some countries. For java, perhaps Sun doesn't want a *.deb to be redistributed, or Ubuntu devs want people to use gcj instead of sun ? :confused:

---

### Post by zee on 2005-10-05
OK, sure, but some of us would still like to use apps like RealPlayer, watch movies (w32codecs package)...

Where are those packages?

zee

PS: though I think it's just a temporary thing since the Breezy Badger release is coming.

---

### Post by Jenda on 2005-10-05
There was indeed legal trouble with Java. You have to DL and install it manually.

---

### Post by bluhound on 2005-10-08
Jenda is right.  Not only Java but many more due to legal issues.  Looks like we have to make full use of Google and start downloading manually..... :P BTW, can anyody explain to me why w32codecs is illegal??  Isn't it something like K-Lite Codec Pack?? :S

---

### Post by GeneralZod on 2005-10-08
[QUOTE=bluhound]Jenda is right.  Not only Java but many more due to legal issues.  Looks like we have to make full use of Google and start downloading manually..... :P BTW, can anyody explain to me why w32codecs is illegal??  Isn't it something like K-Lite Codec Pack?? :S[/QUOTE]

I'd imagine it's because it contains codecs for WMV, Microsoft's proprietary media format.  Microsoft are not keen on having their codecs distributed to Linux users, as you can probably imagine! :)

---

### Post by Segovia on 2005-10-08
[QUOTE=GeneralZod]Microsoft are not keen on having their codecs distributed to Linux users, as you can probably imagine! :)[/QUOTE]
They're just creating more bad blood between "us and them" when they play hardball like this.  I'm sick of this crap.  DOWN WITH MS!  DOWN WITH SUN!

---

### Post by nix4me on 2005-10-14
[QUOTE=mr_pouit]i think they removed some packages like libdvdcss because they are not legal in some countries. For java, perhaps Sun doesn't want a *.deb to be redistributed, or Ubuntu devs want people to use gcj instead of sun ? :confused:[/QUOTE]

gcj sux.  It doesn't satisfy the requirements for most java apps.

---

### Post by mr_pouit on 2005-10-15
[QUOTE=nix4me]gcj sux.  It doesn't satisfy the requirements for most java apps.[/QUOTE]
yes, but you can install blackdown j2re1.4 and java-common, and it works out of the box :D

---

### Post by tomski on 2005-10-31
it is exactly this problem that forces us all to continue to use ms windows so we will continue to line billys pockets.
unless there is a worldwide loby to force ms to stop using the line that this software is restricted because of piracy issue's then the transition from windows to linux will never get smoother.
so upshot is dual boot to get around it or create your own packages that contain the software you need just learn a shed load of coding skills and take what you need from that old copy of xp you stoped using(but still own) and as long as you dont re-distribute then your ok, but hey thats just a dream eh.....

if you have fun running into walls dont forget, bill gates has the windows to smash!!!

---

### Post by The Warlock on 2005-11-07
[QUOTE=mr_pouit]yes, but you can install blackdown j2re1.4 and java-common, and it works out of the box :D[/QUOTE]

Sure you can, until you need Java 1.5. I need to program in 1.5 for school.

---

### Post by mr_pouit on 2005-11-08
[QUOTE=The Warlock]Sure you can, until you need Java 1.5. I need to program in 1.5 for school.[/QUOTE]

that's strange, because at school, when i needed to program in java, they said "do not use sun 1.5... stay in 1.4" :D 

But if you need sun jre/jdk 1.5, you can use plf repositories ;) => [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by macleod199 on 2005-11-11
> **mr_pouit]that's strange, because at school, when i needed to program in java, they said "do not use sun 1.5... stay in 1.4" :D 

But if you need sun jre/jdk 1.5, you can use plf repositories  said:**
> http://wiki.ubuntu-fr.org/doc/plf[/url]

Probably because they don't want to roll it out on all the lab computers yet. I had one kid e-mail me about using generics last year because it was in his textbook, and I told him I'd be marking on the lab computers and it wouldn't work, so don't worry about learning it. :)

---

