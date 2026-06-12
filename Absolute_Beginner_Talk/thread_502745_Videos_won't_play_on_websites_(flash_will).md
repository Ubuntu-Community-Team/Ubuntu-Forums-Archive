---
title: "Videos won't play on websites (flash will)"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-07-17
All of my flash movies play on the net, but it seems that the movies that are using Totem aren't playing at all.  I'm assuming it's due to the w32codecs.  

I'm trying to install w32codecs and I'm getting an error:

> Reading package lists...
Building dependency tree...
Reading state information...
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Any clue what this is, or what I'm doing wrong??

---

### Post by crispy_420 on 2007-07-17
Did you add the correct repos?

[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by Al3xK3aton on 2007-07-17
If it's missing, you probably have to re-download it.

---

### Post by digital_sabotage on 2007-07-17
i personally use mplayer ...mozilla-mplayer and w32 codecs ...all installed through synaptics ...not a single problem since:-)

---

### Post by dmorand on 2007-07-17
> **digital_sabotage said:**
> i personally use mplayer ...mozilla-mplayer and w32 codecs ...all installed through synaptics ...not a single problem since:-)

I downloaded mozilla-mplayer but when I open vids in firefox Totem is still being used.  How do I change it to use mozilla-mplayer?

Also, when I search for w32 in Synaptic I don't see the codecs listed.  Where can I find them?  

.....What repos am I supposed to have for this?

---

### Post by digital_sabotage on 2007-07-17
...sorry ...missed a step or two

[http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

mplayerplug-in ...this is what got my streaming vid to play through mplayer in firefox

...and for w32codecs ...i think you need to make sure you have "main, universe, restricted and multiverse" enabled in the repositories ...but i could be wrong 

if that doesn't work for your codecs try this page...
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28w32codec%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28w32codec%29)

...i don't know where i got my codecs for sure but i see i have a deb file i saved in a personal folder with the same codecs version as is offered in the link above and is what i have installed

worst case go to mplayerhq and download codecs from there  ...just they aren't in debian which i think is way easier


...hope this helps

---

### Post by dmorand on 2007-07-17
Cool, I'll give that a shot when I get home from work.  I have to reload my backup of x11.conf cause I screwed it up messing with something.

---

### Post by digital_sabotage on 2007-07-17
...found this link to download w32codecs ...the deb file ...then you can save for next time you might need them

[http://sft.if.usp.br/debian-marillat/pool/main/w/w32codecs/](http://sft.if.usp.br/debian-marillat/pool/main/w/w32codecs/)

...download and save the debian file that is 13.6 M ...date last modified June 24 2007

...that is the latest version available to my knowledge ...one version up from mine

...once you have the file downloaded just double click on it ...it will check that dependencies are satisfied and if not will tell you what you need (should be able to get dependencies through synaptic)

i would personally try repos first and if no go ...try download next

...good luck:-)

---

### Post by dmorand on 2007-07-18
I can't seem to find this in any repo yet, and it's not in my synaptic when I search for w32.  I'll keep digging.

---

### Post by testube_babies on 2007-07-18
This will add the proper repository and install it for you.

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install w32codecs
```

---

### Post by dmorand on 2007-07-18
> **testube_babies said:**
> This will add the proper repository and install it for you.

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install w32codecs
```

Thanks I'll give that a shot when I get home.

---

