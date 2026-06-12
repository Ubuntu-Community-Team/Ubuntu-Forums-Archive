---
title: "Problems getting sound to work in Kubuntu 7.04 (Creative XMod)"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by gamerguy on 2007-06-29
Hi,
Just install Kubuntu 7.04 and couldn't get sound to work. And I'm using the Creative XMod (external USB sound card) by the way.
Thing is, my Xmod shows up in Kmixer. however, there's no sound at all, be it on startup, in firefox or XMMS.
can someone help me solve this problem?

---

### Post by perimere on 2007-08-08
Hi matey,

Have you tried, the troubleshooting guide?
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I'm still in the process of getting mine to work with my laptop (only got the Xmod today). For starters try:
```
cat /proc/asound/cards
```

Presuming you can see an Xmod device in that list?

To get sound working in Amarok for example, you go into: Settings | Configure Amarok, click on the Engine button on the left and enter the following line into the ALSA device configuration section

```
plughw:Xmod,0
```

After a restart of Amarok, this gave me sound!

If you need more, I'll post when I've finished working out the details ;)

Cheers

Adam

---

### Post by perimere on 2007-08-08
Ok, got it sorted now.

Make sure you have the ALSA packages as mentioned int he troubleshooting guide, and then run:
```
asoundconf list
```

This lists the cards available under ALSA. Xmod was listed for me.

Next, type:
```
asoundconf set-default-card Xmod
```

**Reboot**

Everything now works for me, including the volume/mute control from the HW device :)

HTH

Cheers

Adam

---

### Post by galloper on 2007-10-19
The above listed solution did not work for me, I guess it was because I do not use X Windows. But I did manage to make the volume knob work without X. I have posted my solution in another thread: [http://ubuntuforums.org/showthread.php?t=442474](http://ubuntuforums.org/showthread.php?t=442474), if you are interested. I would say it's a more generic and robust solution, should work for every one.

---

