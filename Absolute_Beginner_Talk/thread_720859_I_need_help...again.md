---
title: "I need help...again"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Miss Karen on 2008-03-10
Okay guys, please help again, I'm really sorry I keep asking...

I've checked out the multimedia threads but I can't seem to find anything that helps. I've downloaded/installed all the codecs for my multimedia but it still won't play DVDs. I get sound but no picture.

Bear in mind my Ubuntu is not connected to teh net.

Thankyou...

---

### Post by taurus on 2008-03-10
What did you download and install so far for codecs?

---

### Post by Miss Karen on 2008-03-10
Umm...it's a very long huge list, all the gstreamer ones, plus supporting codecs all starting with "lib"

It wouldn't let me install libdvdcss2, it said there was a later version installed.

---

### Post by taurus on 2008-03-10
Did you get all the info from this link, [https://help.ubuntu.com/community/Medibuntu?](https://help.ubuntu.com/community/Medibuntu?)

---

### Post by Miss Karen on 2008-03-10
I had a look, and downloaded more of the libdvdcss2 bitsies, but I feel rather lost, and I'm not sure it will work given that it already said I had a later version of libdvdcss2 onboard...

---

### Post by fdesign on 2008-03-10
if you installed libdvdread3.....try this

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by ubuntu-freak on 2008-03-11
Or this;

**sudo /usr/share/doc/libdvdread3/install-css.sh**

 
You may need build-essential, debhelper and fakeroot for the above command though, see part 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833). Use VLC to watch DVDs, it's the best and has superb menu support.
 
Nathan

---

### Post by crjackson on 2008-03-11
> **Miss Karen said:**
> Okay guys, please help again, I'm really sorry I keep asking...

I've checked out the multimedia threads but I can't seem to find anything that helps. I've downloaded/installed all the codecs for my multimedia but it still won't play DVDs. I get sound but no picture.

Bear in mind my Ubuntu is not connected to teh net.

Thankyou...


Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

### Post by ubuntu-freak on 2008-03-11
What is it with telling newbies to change the backend of Totem to Xine? It affects more than just DVD playback, and is completely unnecessary. VLC works just fine and is the best DVD player by far. 
 
Nathan

---

### Post by Miss Karen on 2008-03-11
Umm, thanks guys, but I'm not connected to the net...therefore I'm not sure those commands will work...

---

### Post by DUDE_2000 on 2008-03-11
Why aren't you connected to the net?

---

### Post by Miss Karen on 2008-03-12
...because I have no real need to be?

---

### Post by ubuntu-freak on 2008-03-12
> **Miss Karen said:**
> ...because I have no real need to be?

 
It's quite tricky if you're not connected though, as packages rely on other packages being present (dependencies), some will already be installed, but others will not be.
 
Nathan

---

