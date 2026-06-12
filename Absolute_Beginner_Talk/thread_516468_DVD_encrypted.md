---
title: "DVD encrypted"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-08-03
I keep getting some error about not being able to play DVD because the disk is encrypted.

I've tried using Gxine, Movie Player, M Player, Xine, none of them will play the DVD.

The message says I need to install libdvdcss. I have done that. I have also uninstalled, reinstalled everything I can find that may have to do with libdvdcss more than twice (I've been working on this for a couple of days). In Synaptic I did a complete uninstall / reinstall. No joy.

In reading the forum I find reference to something called Automatix that fixed a similar problem. What / where is that?

---

### Post by tchoklat on 2007-08-03
getautomatix.com
 
but it wil provide nothing more than feisty provides itself!

---

### Post by lwalper on 2007-08-03
Well, I was looking in Synaptic and do not find libdvdcss for installation -- but do find libdvdcss3. Has libdvdcss been decremented and the application is looking for something that is just not available? Does anyone have a copy of the old libdvdcss that these apps are looking for?

Should I upgrade to version 7? Would it support this where 6.10 does not?

---

### Post by benx009 on 2007-08-03
have you installed the following:
[I]libdvdnav4
libdvdplay0
libdvdread3[/I]

---

### Post by tchoklat on 2007-08-03
Oh yeh!
If you are using 6.10, upgrade to 7.04 and the updates that you require are available there as the repo's are different!

---

### Post by benx009 on 2007-08-03
> **lwalper said:**
> Well, I was looking in Synaptic and do not find libdvdcss for installation -- but do find libdvdcss3. Has libdvdcss been decremented and the application is looking for something that is just not available? Does anyone have a copy of the old libdvdcss that these apps are looking for?

Should I upgrade to version 7? Would it support this where 6.10 does not?

you need *libdvdcss2*.  [medibuntu]("http://medibuntu.sos-sts.com/") offers the package.

to add the medibuntu repo, do this ```
echo "deb http://packages.medibuntu.org/ edgy free non-free" | sudo tee -a /etc/apt/sources.list
```

then this ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
in a terminal

---

### Post by felipe82 on 2007-08-03
I'm using Fiesty and I have installed (and reinstalled) all 4 libdvd* packages and I still get a:

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
from Totem

and an

Error opening/initializing the selected video_out (-vo) device
from Mplayer

Can play them in VLC, but I don't like this player.

Any help?
thx

---

### Post by felipe82 on 2007-08-06
> **felipe82 said:**
> I'm using Fiesty and I have installed (and reinstalled) all 4 libdvd* packages and I still get a:

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
from Totem

and an

Error opening/initializing the selected video_out (-vo) device
from Mplayer

Can play them in VLC, but I don't like this player.

Any help?
thx

Sorry, should've read the previous post, totem-xine worked perfectly.

---

### Post by asmoore82 on 2007-08-06
google for a deb package of libdvdcss for Ubuntu ...

As far as I know, the complete version of DeCSS
is not available in the official software depos.
[COLOR="White"]for legal reasons.[/COLOR]

---

