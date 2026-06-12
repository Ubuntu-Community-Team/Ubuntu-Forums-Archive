---
title: "Finding the desktop"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by peterstone on 2007-02-27
Hello all.
I know I'm a newbie wimp, but I've just installed 6.08 server version and the command line stuff looks all ok (if baffling!) but I can't work out how to get to my desktop. Any lifelines, please.
Cheers
Peter

---

### Post by Kateikyoushi on 2007-02-27
The server install does not come with a desktop.
You have to choose a desktop environment for yourself and install it.
The following should install gnome the buntu dekstop.

```
sudo aptitude install ubuntu-desktop
```

kubuntu-desktop will install kde and xubuntu xfce.

---

### Post by erkki70 on 2007-02-27
hi,
You probably need to install a gui to get to a desktop with the server edition.
For Gnome try:
```
sudo aptitude install ubuntu-desktop
```Hope it helps...

Oooohhh! I was slow ;-)

Extra link: [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Maelgwyn on 2007-02-27
better yet - install Fluxbox! ;)

[www.fluxbox.org](www.fluxbox.org)

```
sudo apt-get install xorg fluxbox fluxconf
``` will see you right :)

---

### Post by peterstone on 2007-02-27
> **Maelgwyn said:**
> better yet - install Fluxbox! ;)

[www.fluxbox.org](www.fluxbox.org)

```
sudo apt-get install xorg fluxbox fluxconf
``` will see you right :)
Thanks guys, I think I've made some progress.
I followed your advice but the first problem I encountered was that during the install, unbuntu wanted to access a file on my cdrom by reference to the disc label, but as a home burned disc, of course there wasn't one.
Bit of head scratching then tried using the internet. Followed a 25 minute download on broadband and a very long install process of some well known packages including Open Office and Gnome. Then I got a message that 'a package failed to install......assertion 'dependtry <=4' failed.
At least there was a bit of colour on my screen by then!!
I tried "sudo aptitude install ubuntu-desktop" whiich appeared to work  but at the end when I tried to start Gnome, I simply ended up with a garbled screen consisting of multiple coloured blobs!
I've a feeling that it may be best for me to get the 'official' instal cd rather than my own iso download version, but I'll press on for a while yet.
Thanks again - I'll let you know if I succeed.
Cheers
Peter

---

### Post by russell.h on 2007-02-27
Not sure exactly what you mean by your own iso download version, but what I would recommend is getting the Ubuntu Desktop install CD. Downloading and burning will land you with the exact same CD as ordering or whatever you have in mind.

Go to [http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease) and find a Mirror you like, then click on "CD Image for desktop and laptop PCs". Download the iso, burn it, and stick it in your drive. Reboot. Make sure you are set to boot from the CD in your BIOS (you probably are if you managed to do the server install), then boot up.

It should boot to an Ubuntu Desktop which is running live from the CD, and hence everything will be a little slow (or a lot slow). Right on the desktop is a nice GUI installer, just double click that and follow the prompts. The next time you reboot you will have your very own desktop.

---

### Post by peterstone on 2007-02-27
> **russell.h said:**
> Not sure exactly what you mean by your own iso download version, but what I would recommend is getting the Ubuntu Desktop install CD. Downloading and burning will land you with the exact same CD as ordering or whatever you have in mind.

Go to [http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease) and find a Mirror you like, then click on "CD Image for desktop and laptop PCs". Download the iso, burn it, and stick it in your drive. Reboot. Make sure you are set to boot from the CD in your BIOS (you probably are if you managed to do the server install), then boot up.

It should boot to an Ubuntu Desktop which is running live from the CD, and hence everything will be a little slow (or a lot slow). Right on the desktop is a nice GUI installer, just double click that and follow the prompts. The next time you reboot you will have your very own desktop.
Second reply to Kateikyoushi, erkki70 andMaelgwyn:

Belay all that boloney I just wrote. I just tried my third re-start of ubuntu and bingo, gnome came up no problem and has done so twice since!!

And to Russel.h
You are quite right, I did mean the instal CD, but the ready burned one that is available. Hopefully now I won't need to, but if there are more crashes, I'll probably try it your way.

Thanks again to all
Peter

---

