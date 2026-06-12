---
title: "Ubuntu Server Edition"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Snitz on 2007-07-16
I downloaded the Ubuntu Server Edition and I'm wondering, does it com with a user friendly interface like the personal edition? And can I download drivers and applications through it?

---

### Post by Motoxrdude on 2007-07-16
> **Snitz said:**
> I downloaded the Ubuntu Server Edition and I'm wondering, does it com with a user friendly interface like the personal edition? And can I download drivers and applications through it?

If you want to use synaptic but don't want to install tons of packages, run
```
sudo apt-get update
sudo apt-get install fluxbox synaptic
```
then when you want to install applications from synaptic, enter
```
startx
```
RIght click and select "Apps>>System Tools>>Synaptic"

That should do the trick. 
O yeah, you can also just do
```
sudo apt-get install (name of program)
```

---

### Post by Soarer on 2007-07-16
> **Snitz said:**
> I downloaded the Ubuntu Server Edition and I'm wondering, does it com with a user friendly interface like the personal edition? And can I download drivers and applications through it?

Hi,
I guess the whole point of the server edition is that it doesn't come with a GUI - on a server a GUI would be a  waste of resources.
Having said that, you can easily install a desktop onto it if you like.
```
sudo apt-get install ubuntu-desktop
```
will do the trick. Then you have Gnome desktop on a server installation.

Alternatively, you could install [Webmin]("http://www.webmin.com") which is a web front end for server applications. This is not as friendly as Gnome desktop, but should use fewer resources.

You can download drivers and applications with any version of Ubuntu (from the repositories at least, for free).

---

### Post by Snitz on 2007-07-16
I will go for it then, thanks alot. But now I'm having a problem burning the files to the CD making it a bootable CD using NERO. Can anyone help me?
Whenever I choose "Make bootable CD" I get an error saying "wrong path for the image" or something like that.

---

### Post by davidjmayo on 2007-07-16
Try burning with Infrarecorder
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Snitz on 2007-07-16
Ah, thanks. I got it working. I will be installing the server edition in few hours and then I will install the gnome-desktop and other applications.

Just few questions, how do I connect to the internet from the server edition and from where will I be able to download my laptop's drivers?

---

### Post by Soarer on 2007-07-16
It depends on how you normally connect. If using a wired connection, Feisty (I think) will detect & configure for you. If using a modem or wireless, some more configuration may be necessary. A search on here should find the answers quickly for you. 

The same is true of the drivers - Feisty should detect your hardware and install where it can. If anything is still not working, do a search or post on here.

Have you run the Live CD? It will show you if anything is not detected properly (as that function - sound, wireless, screen etc.. won't work)  before you install.

Good luck.

---

### Post by Snitz on 2007-07-16
When I installed Fedora, it detected the network card and nothing more though I couldn't connect via broadband pppoe. And when I reinstalled WinXP, it didn't detected any of my drivers, not even the network card. I had to download all the drivers. So, I'm afraid that Ubuntu wouldn't detected my drivers and I wouldn't know where to download them from.

When I'm home, I connect via Broadband pppoe and now when I'm at work, I connect normaly via a UTP with automatic configuration.

---

### Post by Snitz on 2007-07-16
I installed the server edition of Ubuntu and when I type:

> sudo apt-get install ubuntu-desktop

it tends to download around 400MB, is this right?

---

### Post by Soarer on 2007-07-16
> **Snitz said:**
> I installed the server edition of Ubuntu and when I type:



it tends to download around 400MB, is this right?

Probably. GUIs are big :)

---

### Post by Snitz on 2007-07-16
So if I installed the ubuntu desktop, I'll be like I'm on the normal edition? And isn't there another smaller desktop?

---

### Post by meborc on 2007-07-16
you could just install fluxbox, or xfce... if you are going to set up a server, then you will probably not use the interface much... so you don't need all the programs and eyecandy in ubuntu-desktop... installing ubuntu-desktop will give you EXACTLY the same result as to install a normal ubuntu edition and then install some server applications :)

use fluxbox or xfce4.4.1 ... or even openbox... or icewm

then you will use less disk space and bootup speed triples

EDIT: strongly suggest some reading here - [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) use the guides to get a small setup with incredible speed...

---

### Post by Snitz on 2007-07-16
I'm gonna try: sudo apt-get install fluxbox
And see what it is about. This is my second time using Ubuntu.

---

### Post by meborc on 2007-07-16
don't forget to install xorg package! :D

also install lynx, so you can browse internet in cli/terminal mode... so you don't need to swich between ubuntu/win to read this!

good luck!

EDIT: and don't forget to read about fluxbox setup here - [https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

---

### Post by Motoxrdude on 2007-07-16
> **Snitz said:**
> So if I installed the ubuntu desktop, I'll be like I'm on the normal edition? And isn't there another smaller desktop?

Yes! Ready my post!

---

