---
title: "Install Xubuntu from Ubuntu ??"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-02-25
I'm quite happy with using Ubuntu v6.10 but realise I could get more performance from Xubuntu.

From the homepage:

*Xubuntu is a complete GNU/Linux based operating system with an Ubuntu base. It is lighter on system requirements and tends to be more efficient than Ubuntu with GNOME or KDE, since it uses the Xfce Desktop environment, which makes it ideal for old or low-end machines, thin-client networks, or for those who would like to get more performance out of their hardware.*

I found these instructions:

**Install Xubuntu from Ubuntu**

*If you have an existing Ubuntu, Kubuntu, or Edubuntu installation, it is possible to install Xubuntu and retain your current installation. To do so, just go into Synaptic (or Adept if you use Kubuntu) and install the xubuntu-desktop package. There you are! Next time you login, you can choose Xubuntu from the Session menu on the login screen.*

I was wondering if I would be better off with a clean installation using the AlternateCD ISO or using the above method ??

The PC is low end and I had considered using this solely as a router with IPCOP
[I]
P3(Katmai) 500Mhz
196MB SDRAM
10GB HDD
SB Live Soundcard
USB 1.0
LiteON 32123S CDRW[/I]

So was pleasantly surprised it could actually run an OS with various applications.

Finally by moving to Xubuntu am I losing anything that I have been accustomed to within Ubuntu ??

Thanks

---

### Post by raja on 2007-02-25
Xubuntu would surely be snappier on your system. However, the XFCE interface would be different. So I would think that the best thing would be to just install 'xubuntu-desktop' with aptitude or synaptic. That will allow you top try it without losing gnome.

---

### Post by chrome307 on 2007-02-25
[COLOR="Red"][B]
@raja[/B][/COLOR]

Thanks for getting back to me :)

Do I simply do enter this at the Terminal Window ??

```


sudo aptitude install xubuntu-desktop


```

---

### Post by Maestro23 on 2007-02-25
> **chrome307 said:**
> [COLOR="Red"][B]
@raja[/B][/COLOR]

Thanks for getting back to me :)

Do I simply do enter this at the Terminal Window ??

```


sudo aptitude install xubuntu-desktop


```

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by mcduck on 2007-02-25
Yes, that command is to be run in a terminal. You can also just install the 'xubuntu-desktop' package using Synaptic.

Then you can choose XFCE from the login screen. The result is exactly the same desktop you would get by installing from Xubuntu CD. The operating system is the same, only difference between Ubuntu, Xubuntu and Kubuntu is the desktop environment installed by default, but you can turn one into any of the others or install all desktop environments if you want :D

---

### Post by chrome307 on 2007-02-25
Thanks guys for the advice :)

I did forget one important question ............ can I reverse this at any point ??

---

### Post by Maestro23 on 2007-02-25
> **chrome307 said:**
> Thanks guys for the advice :)

I did forget one important question ............ can I reverse this at any point ??

Yes, read the link I provided. There are other topics on the right side of the screen.  Toward the bottom it talks about the different desktops.

---

### Post by chrome307 on 2007-02-25
[B]
@Maestro23[/B]

Thanks for that ............ just finished downloading and then installed the updates .... worked perfectly :)

---

### Post by RuarriS on 2007-02-25
i recently did this myself, and installed the xdm. I would like to uninstall the gnome things (to save drive space). I tried to uninstall gdm but then it wants to uninstall my xubuntu-desktop?!
What packages are safe for me to uninstall from the gnome side?

---

### Post by Rui Pais on 2007-02-25
> **RuarriS said:**
> i recently did this myself, and installed the xdm. I would like to uninstall the gnome things (to save drive space). I tried to uninstall gdm but then it wants to uninstall my xubuntu-desktop?!
What packages are safe for me to uninstall from the gnome side?

gdm is the login manager, common to gnome and xfce. 

Check psychocats.net, there are an article on xfce only, [here]("http://www.psychocats.net/ubuntu/purexfce").

---

