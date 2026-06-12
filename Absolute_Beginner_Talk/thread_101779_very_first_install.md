---
title: "very first install"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Drizz on 2005-12-10
I not ashamed to say this but I am a total n00b to this. And I was pointed in this direction when I asked around about Linux.

Anyway I have an Acer Aspire 1355LC laptop and windows has been playing up so I thought why not try another OS. 

I've downloaded [this version]("http://releases.ubuntu.com/5.10/ubuntu-5.1...nstall-i386.iso") and burned the image to CD.

Now I put the CD in and rebooted, got the first screen, lovely.

> ubuntu logo

The default instillation is suitable for most desktop or laptop systems.
Press F1 for help and advanced instillation options.

To install only the base system, type 'server' then enter. for the default instillations, press enter

boot:

So I press enter and it starts to install, fantastic, but then all of a sudden my screen goes all fuzzy and I can't read anything. [Picture](http://www.dropshipinfo.co.uk/images/acer_fuzzy.jpg)

Now I fully expect to have done something wrong. Any help would be great.

Thanks.

---

### Post by kaamos on 2005-12-10
Never heard of this, but you could try defining the vga mode.. so when the cd boots enter:
```


To install only the base system, type 'server' then enter. for the default instillations, press enter

boot:**linux vga=771**

```

---

### Post by Drizz on 2005-12-10
nice one, that seems to have worked, I can actually see whats happening now :D

---

### Post by syncme on 2005-12-10
Can anyone verify this for me?

If you install with the "server" option, do you get a somewhat minimalist install? (For desktop use)

I just remember installing a server for some other distro and it didn't install any gui. Is this the same with Ubuntu?

Syncme

---

### Post by Rackerz on 2005-12-10
I doubt it. It probably optimizes for server use and installs applications for server use.

---

### Post by Estariel on 2005-12-10
"server" will not install a GUI

---

### Post by syncme on 2005-12-10
[QUOTE=Estariel]"server" will not install a GUI[/QUOTE]

That's what I thought......

Syncme

---

### Post by Gray. on 2005-12-10
once server install is done (and assuming you want a GUI) you can:
For Gnome:
```
sudo apt-get install ubuntu-desktop
```
For KDE:
```
sudo apt-get install kubuntu-desktop
```
For Xfce:
```
sudo apt-get install xubuntu-desktop
```
I think those are correct, someone feel free to correct if not.

---

### Post by aysiu on 2005-12-10
[QUOTE=Gray.]
I think those are correct, someone feel free to correct if not.[/QUOTE] Correct, but for Xubuntu, you'll need extra repositories (see first link in my sig). You'll have to ```
sudo nano /etc/apt/sources.list
```

---

