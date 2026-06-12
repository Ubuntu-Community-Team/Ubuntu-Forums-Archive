---
title: "Playing a DVD"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by piromedic on 2008-04-13
I can not play a DVD in Totem.  I gives me an error message stating that Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.  Can anyone point me in the right direction?

---

### Post by t1n0m3n on 2008-04-13
What version of Ubuntu do you have?

---

### Post by Glaxed on 2008-04-13
Perhaps you need more Gstreamer plugins.
Open synaptic, search for 'gstreaner', and install what you need.
Look into w32codecs as well.

---

### Post by sayakb on 2008-04-13
> **piromedic said:**
> I can not play a DVD in Totem.  I gives me an error message stating that Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.  Can anyone point me in the right direction?

As far as I remember, Totem offers you to download the plugins by pressing some Yes button. Otherwise, open synaptic package manager and install all gstreamer plugins.
You might also try VLC media player:
```
sudo apt-get install vlc
```

---

### Post by russo.mic on 2008-04-13
If your using Gusty, w32codecs package is no more.

Install Totem-xine in Synaptics.  OR, get VLC cause it's awesome.  Search in synaptics for VLC if you'd like.  it'll play almost anything.

Russo

---

### Post by t1n0m3n on 2008-04-13
What do you mean by "w32codecs package is no more" ?

---

### Post by ubuntu27 on 2008-04-13
In Order to be able to play DVD in Ubuntu, you have to add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository, and then install the DVD codecs. Follow these instructions: [Note: All the comands have to be entered in the terminal. **The terminal can be found at Applications menu/Accesories/Terminal **in Ubuntu or GNOME]

If you are using **Ubuntu 7.10 "Gutsy Gibbon":**

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

If you are using **Ubuntu 8.04 "Hardy Heron":**

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```



INSTALL The DVD codec:

```
sudo apt-get install libdvdcss2
```

Install the rest of the codecs:

If you are using UBuntu  32bits (also known as !386)
```
sudo apt-get install w32codecs

```

If you are using Ubuntu 64bit
```
sudo apt-get install w64codecs
```


SOURCE: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by X_CheshireCat_x on 2008-04-13
i am also having trouble playing DVD's i have tried all of the above, including downloading the VLC player.
Totem says Totem it "cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc".
VLC player does absolutely nothing when i open the disc...

---

### Post by hurtstotalktoyou on 2008-04-13
I actually just had this problem, and the fix was quite simple.

1.  Open terminal (applications > accessories > terminal)
2.  Type in the following commands:
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot

sudo /usr/share/doc/libdvdread3/install-css.sh

That should do it.

---

### Post by X_CheshireCat_x on 2008-04-13
i have done as you said... now totem wont even open and VLC plays white noise with no video.... any other suggestions?




(no sarcasm intended)

---

### Post by hurtstotalktoyou on 2008-04-13
> **X_CheshireCat_x said:**
> i have done as you said... now totem wont even open and VLC plays white noise with no video.... any other suggestions?




(no sarcasm intended)

You are in 7.10, right?

---

