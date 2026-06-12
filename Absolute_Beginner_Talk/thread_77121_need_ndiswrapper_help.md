---
title: "need ndiswrapper help"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-10-16
my problem: my only possible internet connection is with a USB wireless adapter (netgear WG111 v.2). if it's not connected, i can't be online. (it's a combination of numerous hurdles that make it so.)

if i can't be connected, then using synaptic is out, right?

if so, i have to install ndiswrapper via CD (i'd actually use my camera to transfer any files i need, saving me the time in burning the CD). i tried a dry run of this on the live CD and i guess that just doesn't work. i'd get stuck at the dpkg commands. i'm guessing these commands don't work on the live CD?

as i will be loading any files i need to get my wireless working, with ndiswrapper, all offline, what exactly do i need for the procedure (i've heard mention of some 'gcc thing', etc. what is that?)? once i've got ubuntu installed, it will be difficult for me to download additional files unless i reinstall windows ME (now you understand the urgency, although i don't think ME is as bad as people say).

---

### Post by fuscia on 2005-10-16
i just found this - [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

do i need to be online to use synaptic?

---

### Post by kvidell on 2005-10-16
Yes, unless ndiswrapper is on your Ubuntu CD, which I don't think it is.

Synaptic is a front-end to aptitude/apt, which uses online repositories of software maintained by developers to download and install applications on the fly without much user intervention.
- Kev

---

### Post by fuscia on 2005-10-16
[QUOTE=kvidell]Yes, unless ndiswrapper is on your Ubuntu CD, which I don't think it is.

Synaptic is a front-end to aptitude/apt, which uses online repositories of software maintained by developers to download and install applications on the fly without much user intervention.
- Kev[/QUOTE]

so, can i install it off a cd? and what else would i need?

---

### Post by JazzCrazed on 2005-10-16
If it's a Debian package (*.deb file), you can install it in terminal via:

```
sudo dpkg -i [package filename].deb
```

If it's source code that needs to be compiled, then I can't help you. :-/

---

### Post by fuscia on 2005-10-16
[QUOTE=JazzCrazed]If it's a Debian package (*.deb file), you can install it in terminal via:

```
sudo dpkg -i [package filename].deb
```

If it's source code that needs to be compiled, then I can't help you. :-/[/QUOTE]

i have it as both a .deb file and a tar.gz file.

---

### Post by JazzCrazed on 2005-10-16
Did it work when you ran dpkg -i on the deb file?

---

### Post by az on 2005-10-16
[QUOTE=fuscia]my problem: my only possible internet connection is with a USB wireless adapter (netgear WG111 v.2). if it's not connected, i can't be online. (it's a combination of numerous hurdles that make it so.)

if i can't be connected, then using synaptic is out, right?

if so, i have to install ndiswrapper via CD (i'd actually use my camera to transfer any files i need, saving me the time in burning the CD). i tried a dry run of this on the live CD and i guess that just doesn't work. i'd get stuck at the dpkg commands. i'm guessing these commands don't work on the live CD?

as i will be loading any files i need to get my wireless working, with ndiswrapper, all offline, what exactly do i need for the procedure (i've heard mention of some 'gcc thing', etc. what is that?)? once i've got ubuntu installed, it will be difficult for me to download additional files unless i reinstall windows ME (now you understand the urgency, although i don't think ME is as bad as people say).[/QUOTE]


read this:
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

Everything you need is on your cd.  Use synaptic.  Install ndiswrapper-utils and then set it up.

---

### Post by fuscia on 2005-10-16
thanks, azz. i've gotten as far as "sudo modprobe ndiswrapper", but i got this response: "FATAL: error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): operation not permitted". i tried it in root terminal as well.

---

### Post by fuscia on 2005-10-16
i just did  ndiswrapper -l  and it listed "netwg111   invalid driver. i used the .inf file that i found on my windows ME when i had my wireless instlled on it.

*edit: i have verified i have the correct driver from two other sources (netgear site and installation CD).

---

### Post by fuscia on 2005-10-16
so close, yet so far away...

---

### Post by az on 2005-10-16
remove the driver and reinstall it

sudo nautilus /etc/ndiswrapper
and delete the entry(s)

sudo ndiswrapper -i ...again.

---

### Post by fuscia on 2005-10-16
[QUOTE=azz]remove the driver and reinstall it

sudo nautilus /etc/ndiswrapper
and delete the entry(s)

sudo ndiswrapper -i ...again.[/QUOTE]

ok, i got a little further this time.  'sudo modprobe ndiswrapper'  seemed to work (no error message, at least). but, when i ran  'ndiswrapper -l'  it listed the driver and said 'invalid driver'. i've checked a variety of sources for this driver and it appears to be most correct.

thanks for your help, btw.

---

### Post by az on 2005-10-17
[QUOTE=fuscia]ok, i got a little further this time.  'sudo modprobe ndiswrapper'  seemed to work (no error message, at least). but, when i ran  'ndiswrapper -l'  it listed the driver and said 'invalid driver'. i've checked a variety of sources for this driver and it appears to be most correct.

thanks for your help, btw.[/QUOTE]
Does this card work in windows and are you using that same driver?

---

### Post by fuscia on 2005-10-17
[QUOTE=azz]Does this card work in windows and are you using that same driver?[/QUOTE]

yes, it worked fine in windows. i saw another thread in which someone mentioned an additional .inf file, so i will try that one later on. btw, i found an old linksys 802.11b that i'm using now. would there be much of a speed difference between a 'b' working out of the box vs. a 'g' working on ndiswrapper?

---

