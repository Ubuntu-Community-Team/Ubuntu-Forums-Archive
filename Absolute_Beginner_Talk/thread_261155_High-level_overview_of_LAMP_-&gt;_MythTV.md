---
title: "High-level overview of LAMP -&gt; MythTV"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jonnythan on 2006-09-19
I want to use my Ubuntu LAMP server as my DVD player.

Could someone give me an overview of the process?

I've installed xbuntu-desktop (xfce DE?) and xine.

What else do I need to have installed? How exactly do I install the DVD playback libraries or applications? There's so much information and so many HOWTO's, none of them seem to address quite what I want and none of them seem to agree.

I have no interest in PVR functionality, just DVD playback.

---

### Post by reacocard on 2006-09-19
Mythtv is more than you'd need for this. Try a stand-alone player, like xineui. ogle, mplayer and totem-xine also play dvds.

---

### Post by jonnythan on 2006-09-19
OK.

Let's say I take a base LAMP server install, then install xbuntu-desktop.

What exactly do I need to install to do nothing more than play DVDs? Video quality and ability to adjust saturation/brightness/contrast is important if that matters.

I'll probably be using lirc for remote control.

Thanks.

---

### Post by jonnythan on 2006-09-20
Do you think it might be easier to install Xubuntu or Kubuntu, then install and configure the LAMP services?

---

### Post by reacocard on 2006-09-20
> **jonnythan said:**
> OK.

Let's say I take a base LAMP server install, then install xbuntu-desktop.

What exactly do I need to install to do nothing more than play DVDs? Video quality and ability to adjust saturation/brightness/contrast is important if that matters.

I'll probably be using lirc for remote control.

Thanks.

I think GXine can handle lirc. You'll also need to enable dvd playback.: 

In a terminal, type:
```
sudo apt-get install libdvdread3 gxine
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```

That'll get you Gxine with dvd playback. Then just install and configure lirc, and you're set!

---

### Post by jonnythan on 2006-09-21
That seems to work OK. Thanks!

---

### Post by houstonbofh on 2006-09-21
> **jonnythan said:**
> Do you think it might be easier to install Xubuntu or Kubuntu, then install and configure the LAMP services?

Even with the OP solved, this is for the searchers.  It is much harder to install and configure LAMP that to type *sudo apt-get install ubuntu-desktop* as there is no LAMP package yet.

And an easy way to get the naughty stuff is easyubuntu or automatix.  Either one will get you codecs, flash and playing DVDs in no time.

---

### Post by crouton on 2006-10-07
Huh?  Download the 6.06 Server CD and choose the LAMP install option.  Not so hard, unless you have no access to download/burn the Server CD.

---

