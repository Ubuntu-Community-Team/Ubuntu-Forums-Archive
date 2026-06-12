---
title: "sound issues with 5,3 MBP"
date: 2009-12-17
forum: Apple Hardware Users
---

### Post by cmojallali on 2009-12-17
i have a MBP 5,3 Unibody.

I can't get the sound to work even after doing this:
[https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Sound](https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Sound)

The alsamixer shows up but is totally blank. also i dont know if this helps at all but when i hit edit>sound card properties the program closes and displays this in the terminal: 

```
(gnome-alsamixer:2130): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
```Also i tried installing pommed but my backlight and keylight keys still don't work.

---

### Post by cmojallali on 2009-12-17
Bump. This is the most annoying issue. I have tried everything humanly possible. But being a noob i'm husre i've just made a dumb mistake

---

### Post by linuxopjemac on 2009-12-18
did your installation of alsa-driver really work ?

just fiddle a bit around how to find the alsa-driver version number, something like

```
apt-cache showpkg alsa-driver
```

more info [here]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html")

---

### Post by cmojallali on 2009-12-19
> **linuxopjemac said:**
> did your installation of alsa-driver really work ?

just fiddle a bit around how to find the alsa-driver version number, something like

```
apt-cache showpkg alsa-driver
```more info [here]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html")

I did this and it displayed this:

```
W: Unable to locate package alsa-driver_
```___

---

### Post by cmojallali on 2009-12-19
My Issue is solved.

---

### Post by piniculis on 2009-12-25
I have the same issue with my macbook 5,3.

Would you be so kind as to share how you resolved it?

---

### Post by fargusmax on 2009-12-27
> **cmojallali said:**
> My Issue is solved.

I am also having this problem.  My sound worked fine, but I needed to reinstall and the tried and true way mentioned earlier in the thread is not working.

PLEASE write up what you did to fix!

Thanks,

Rob

---

### Post by sml on 2009-12-29
> **cmojallali said:**
> My Issue is solved.

Thanks but share with others .. assistance shouldn't be one way :(

---

### Post by cmojallali on 2009-12-31
Ok, I'm not exactly sure what my issue was but I just had to keep trying to use the instructions here:[ https://help.ubuntu.com/community/Ma...3/Karmic#Sound]("https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Sound") 

After failing about 30 times eventually it worked. Really odd. And the time that it did work I typed directly into the console. Maybe try that.

Good luck

---

### Post by dogturd on 2010-01-05
Ive followed the instructions but for some reason the drivers aren't installing?

W: Unable to locate package alsa-driver

I have a MBP 15" 5,3 Ubuntu 9.10 64Bit

I have everything working with the exception of sound?

Thanks

---

### Post by linuxopjemac on 2010-01-06
According to the wiki you have to download and compile alsa-driver yourself. It's not in the repository. Maybe you can find it in the backport repository.

```
aptitude install linux-backports-modules-alsa-karmic-generic
```

You might also want to follow this thread:
[http://ubuntuforums.org/showthread.php?t=1370252](http://ubuntuforums.org/showthread.php?t=1370252)

---

### Post by dogturd on 2010-01-06
That worked many thanks :)

---

