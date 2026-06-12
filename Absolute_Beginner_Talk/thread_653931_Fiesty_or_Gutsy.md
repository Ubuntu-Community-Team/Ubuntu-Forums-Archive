---
title: "Fiesty or Gutsy?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by thecrimsonalchemist42 on 2007-12-30
I posted this in Installation and Upgrades too but I thought here might be more appropriate.
I am quite new to Ubuntu and was wondering, if you guys thought i should switch over from Fiesty to Gutsy or not. I would really like Compiz Fusion (also I still need to install my ATI drivers, so I am not sure if Gutsy is easier or harder to install them), but I dont know much about Gutsy and I would like to keep up to date. I'm most concerned about bugs and such in Gutsy, and am not sure if it has any or how severe they may be. And most importantly, if it doesnt have the resolution 1165x864 or 1440x900, I won't update it (Sabayon 3.4 Mini only let me use one resolution way higher than that, so that has become concerning to me when installing a new os).

---

### Post by flamelab on 2007-12-30
Gutsy of course .

You should know that in Linux every new release is better than the previous one .

In Gutsy the ATI drivers are easily installed :

1)System ->Administration ->Restricted Drivers Manager

2)You choose your graphics card 

3)It installs the driver from the internet ( the driver 8.37 though , it is a bit old )

4)You then restart X server ( ctrl+alt+backspace )

5)You enter in console

```
sudo apt-get install xserver-xgl compizconfig-settings-manager
```

and you have Fusion :guitar:

---

### Post by taurus on 2007-12-30
Double post.

[http://ubuntuforums.org/showthread.php?t=653928](http://ubuntuforums.org/showthread.php?t=653928)

---

### Post by thecrimsonalchemist42 on 2007-12-30
> **thecrimsonalchemist42 said:**
> I posted this in Installation and Upgrades too but I thought here might be more appropriate.

> **taurus said:**
> Double post.

[http://ubuntuforums.org/showthread.php?t=653928](http://ubuntuforums.org/showthread.php?t=653928)

It noted that immediately. I am sorry if I caused any trouble by trying to find answers.

---

### Post by philinux on 2007-12-30
I upgraded then found problems. I moved my home to its own partition then installed gutsy clean.

It's much better than feisty.

---

### Post by Dr Small on 2007-12-30
I've never tried Gutsy installed, but it seemed pretty good off the livecd.
I'm still running Feisty, but go ahead and try out Gutsy ;)

---

### Post by gn2 on 2007-12-30
> **thecrimsonalchemist42 said:**
>  I would really like Compiz Fusion 

Why not just install Beryl and Emerald in 7.04?

---

### Post by thecrimsonalchemist42 on 2007-12-30
> **gn2 said:**
> Why not just install Beryl and Emerald in 7.04?

Its out of date, but thats ok I guess, How do I install them? I do have an ATI card if that makes trouble...

---

### Post by gn2 on 2007-12-30
> **thecrimsonalchemist42 said:**
> Its out of date, but thats ok I guess, How do I install them? I do have an ATI card if that makes trouble...

Synaptic Package Manager. Beryl works just fine if you like that kind of thing.

No knowledge of ATI, I don't use graphics cards.

---

### Post by snakeeyes on 2007-12-30
Like some other users here said u could install Beryl or Compiz Fusion in Fiesty. I ran into some bugs with Ubuntu 7.10, but I think u should try it after backing up ur files. If u run into some problems then install Kubuntu 7.10, thats what I am using now without problems also cause I prefer KDE more or if u prefer gnome and have trouble with Ubuntu 7.10 then try Linux Mint 4.0, its based on Ubuntu 7.10 and in my opinion is a lot more stable and has more things out of the box with a way better look than Ubuntu 7.10.

You could also not upgrade at all right now and wait for Hardy.

---

