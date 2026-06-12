---
title: "Copy DVD Gnome Baker?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-04-04
Hi,
I am getting there with all this linux stuff but am a bit stuck with tis problem.

I have a DVD of a wedding and someone wants a copy. Easy I thought.
But in Gnome Baker there is no copy dvd option.
So I thought I'd be clever and just create a Data DVD and copy the _TS folders.
However it fails to play, so a Video  DVD must have something else on the disk.

I know I could bring u pa command line and do a makeisofs first to get an iso then make a DVD from ISO but its a bit naff having this extra unnecessary (well necessary I suppose...) step.

So finally my question, can I find a graphical diskcopy facility that will work on dvd's ?

Ta

Jeff

---

### Post by dcstar on 2006-04-04
[QUOTE=jethro10]Hi,
I am getting there with all this linux stuff but am a bit stuck with tis problem.
......
So finally my question, can I find a graphical diskcopy facility that will work on dvd's ?

Ta

Jeff[/QUOTE]
Try k3b

---

### Post by jethro10 on 2006-04-04
Thanks for the reply.
I'm gonna show my ignorance again. That is a KDE app, can I install it on Gnome? and will it be reliable enough running it in an alien desktop?

Ta
J

---

### Post by meborc on 2006-04-04
it can install just fine... although it will need a bunch of stuff, which it will also install... but most of kde apps run just fine under gnome

---

### Post by slazh on 2006-04-04
[quote=jethro10]Thanks for the reply.
I'm gonna show my ignorance again. That is a KDE app, can I install it on Gnome? and will it be reliable enough running it in an alien desktop?
[/quote] 
Yes you can install it on Gnome. But it will install some KDE packages (not the entire KDE package) so K3B can run. And yes, it will be stable :)

Edit; meborc was first ;P

---

### Post by taurus on 2006-04-04
Hey, I use k3b to do all the burning even though I use fluxbox so it doesn't matter whether it's Gnome or KDE's apps.  They will run just fine in whatever window manager you use.

---

### Post by meborc on 2006-04-04
[QUOTE=taurus]Hey, I use k3b to do all the burning even though I use fluxbox so it doesn't matter whether it's Gnome or KDE's apps.  They will run just fine in whatever window manager you use.[/QUOTE]
yes, that is true, they run, but since they are not native apps, they will recuire (they depend on) a lot of libraries which will be also installed and which will be initiated when running this non-native-program... this means space lost in HD and higher RAM usage... but with todays machines it really doesn't matter ;)

---

### Post by trent dillman on 2006-04-04
You could make a Video DVD and copy the folders.

Or, you could go terminal:

```

mkisofs -dvd-video -o ~/wedding.img /media/cdrom/

```
writes an img file to your home directory, copying from your cdrom drive, then write to disk with
```

dvdrecord speed=4 -dao dev=0,0,0 ~/wedding.img

```

where dev=0,0,0 is the device displayed by

```
dvdrecord -scanbus
```

---

### Post by meborc on 2006-04-04
[QUOTE=jethro10]...I know I could bring u pa command line and do a makeisofs first to get an iso then make a DVD from ISO but its a bit naff...[/QUOTE]

[QUOTE=trent dillman]...writes an img file to your home directory, copying from your cdrom drive...[/QUOTE]

i guess that doesn't solve the problem ;)

---

### Post by jethro10 on 2006-04-04
[QUOTE=meborc]i guess that doesn't solve the problem ;)[/QUOTE]

No, it doesn't.  However I tried all these command line options and am reasonably happy with them.

I'm just trying to make all this Wife proof in a quest to dispose of the Windows PC.

Getting closer.
J

---

### Post by trent dillman on 2006-04-04
Haha, I haven't slept. Give a guy a break for trying.

Besides, I mentioned making a Video DVD first.

:-?

---

