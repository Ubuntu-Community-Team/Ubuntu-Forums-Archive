---
title: "Sound iMac 24&quot;"
date: 2010-03-31
forum: Apple Hardware Users
---

### Post by jaco223 on 2010-03-31
Does anyone know how i would be able to activate the internal sub-woofer  on a Mac.
I have sound, but no bass response. I'm trying to achieve the same  sound quality
as when I'm in OSX.

The iMAC&#8217;s sound card is built on top of the [Realtek  ALC885]("http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=138") chipset driven by the Intel ICH8 HD  Audio controller.

Any help would be greatly appreciated. Thanks.

Jaco

---

### Post by linuxopjemac on 2010-04-01
I see two configurations for 
```
/etc/modprobe.d/alsa-base.conf
```

one is
```
options snd-hda-intel model=lenovo-sky
```
(reported to be tinny)

the other is
```
options snd-hda-intel model=mbp3
```
(some say it works great, don't know what that means though)

---

### Post by NightwishFan on 2010-04-01
I read this in the Ubuntu Community Doc:
[https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound)

Edit: This page is linked way down, however you might find the other sections useful as well.

---

### Post by linuxopjemac on 2010-04-01
I am curious which of the ones work best.

---

### Post by jaco223 on 2010-04-01
> **NightwishFan said:**
> I read this in the Ubuntu Community Doc:
[https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound)

Edit: This page is linked way down, however you might find the other sections useful as well.

NightwishFan, I'm able to get sound both imac24 and mbp3 work equally well, my question is how to get Linux to activate the internal sub-woofer on the iMac. This is what is eluding me. I love Linux and especially Ubuntu, but the lack of bass response is what I'm disappointed in. I've googled the question, but in the end I come up empty.

@linuxopjemac, both options produce that tinny sound. It's sad because in OSX the internal speaker and sub-woofer give great audio playback.

---

### Post by linuxopjemac on 2010-04-01
I am afraid that this feature is missing in the ALSA driver. If I were you, I would report it as a bug to the ALSA developers and tell them that this has been lacking for a long time already...

---

### Post by ErsinG on 2010-04-02
[http://ubuntuforums.org/showthread.php?t=1443020](http://ubuntuforums.org/showthread.php?t=1443020)

have you checked this out?

---

