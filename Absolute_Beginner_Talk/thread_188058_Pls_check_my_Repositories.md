---
title: "Pls check my Repositories"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-06-03
Can someone check my repos and tell me if they're looking optimal. Having trouble running DVD players and trying to ensure i got it all right. Everything was smooth and working in Breezy, and still tweaking here in Dapper

[http://paste.ubuntu-nl.org/15033](http://paste.ubuntu-nl.org/15033)

Thank you

---

### Post by bluevoodoo1 on 2006-06-03
Nothing seems glaring to me.

Have you seen this link? 
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by sophtpaw on 2006-06-03
[QUOTE=bluevoodoo1]Nothing seems glaring to me.

Have you seen this link? 
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)[/QUOTE]
 
Yes, i have actually, but did it via syanptic the way the wikis show. Is the result the same?

Edit:

This is what it would look like if i used source-o-matic:
[http://paste.ubuntu-nl.org/15034](http://paste.ubuntu-nl.org/15034)

which is better?

---

### Post by bluevoodoo1 on 2006-06-03
[QUOTE=sophtpaw]which is better?[/QUOTE]

It really just depends what packages you're looking for. IF you won't need anything in Cipherfunk or Seveas' repo, then you don't need it in your sources list. Here's mine, the essentials are near the top, while the bottom aren't necessarily for everyone.  I can pretty much get everything I need with the top half of my sources, the bottom half are newer/beta/might-not-be-entirely-stable. You're more likely to have things get broken if you stray from the "official" repos.

```

deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb-src http://archive.ubuntu.com/ubuntu/ dapper universe

deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ dapper-security main restricted

deb http://security.ubuntu.com/ubuntu/ dapper-security universe
deb-src http://security.ubuntu.com/ubuntu/ dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper multiverse

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse



#Wine
#deb http://wine.sourceforge.net/apt/ binary/

#Xgl and Compiz
deb http://www.beerorkid.com/compiz dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://www.beerorkid.com/compiz dapper main

# Engage panel
#deb http://soulmachine.net/breezy/ unstable/

#amarok 1.4+
deb http://kubuntu.org/packages/amarok-latest dapper main
deb-src http://kubuntu.org/packages/amarok-latest dapper main

```

---

### Post by sophtpaw on 2006-06-03
[QUOTE=bluevoodoo1]It really just depends what packages you're looking for. IF you won't need anything in Cipherfunk or Seveas' repo, then you don't need it in your sources list. Here's mine, the essentials are near the top, while the bottom aren't necessarily for everyone.  I can pretty much get everything I need with the top half of my sources, the bottom half are newer/beta/might-not-be-entirely-stable. You're more likely to have things get broken if you stray from the "official" repos.

[/code][/QUOTE]

Yea, aguess, i don't see any harm in having the repos maxed so that if and when i do need something i don't need to figure out in what repos they are and where to get them. So, i just like to have it from the outset.

An aside: how does XGL work? and what are the prerequisites if you don't mind me asking?

---

### Post by bluevoodoo1 on 2006-06-03
[QUOTE=sophtpaw]
Yea, aguess, i don't see any harm in having the repos maxed so that if and when i do need something i don't need to figure out in what repos they are and where to get them. So, i just like to have it from the outset.[/quote]

You can always comment out repos that you only use once in a while (like wine or xgl), so you don't have to wait so long when you're updating your list, via 'sudo apt-get update' or through the "reload" button in synaptic. Again, untrusted repos can be a security risk, so watchout for any that seem suspicious.

> An aside: how does XGL work? and what are the prerequisites if you don't mind me asking?

[http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl) A nvidia video card might give you fewer troubles, and of course, fast hardware is a plus. I have a Nvidia fx5500--which is getting old-- and Xgl/compiz works fine.

---

### Post by sophtpaw on 2006-06-03
[QUOTE=bluevoodoo1]You can always comment out repos that you only use once in a while (like wine or xgl), so you don't have to wait so long when you're updating your list, via 'sudo apt-get update' or through the "reload" button in synaptic. Again, untrusted repos can be a security risk, so watchout for any that seem suspicious.



[http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl) A nvidia video card might give you fewer troubles, and of course, fast hardware is a plus. I have a Nvidia fx5500--which is getting old-- and Xgl/compiz works fine.[/QUOTE]

Thx for that. I have integrated graphics onboard motherboard, which isn't good enough. So, i need to get a nice nvidia pci graphics card

---

