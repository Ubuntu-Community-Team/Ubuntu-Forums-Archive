---
title: "Wine installation help please"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by silkstone on 2007-04-05
I've just installed Wine from Applications > Add/Remove.

Then I ran **wine config** from the terminal (because I remember someone saying that you should! And I got this....

```
silkstone@silkstone-desktop:~$ wine config
wine: creating configuration directory '/home/silkstone/.wine'...
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
Failed to open the service control manager.
wine: '/home/silkstone/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\config.exe": Module not found

```

Does that mean something's wrong?

---

### Post by plainjane on 2007-04-05
Don't know if it makes the slightest bit of difference, but I ran
                  winecfg
   in terminal instead of   wine config.   It took me two installs of wine to get it to run properly.

---

### Post by silkstone on 2007-04-05
I ran winecfg and that threw up the same errors, but also told be I needed to install libjack.so.

So.... I installed the libjack libraries from Synaptic, tried winecfg again.... and it still said I needed to install libjack.so.

So.... I decided to ignore it and try installing a Windows app. And that went OK, except that the one I tried - Faststone Image Viewer which I'm very fond of under XP - doesn't work quite as it should, because only the first page of thumbnails is displayed and everything is blank when you scroll down. Ho hum. I searched around and found that it's a known bug with running that under Wine, so maybe I'll try something else.

Or maybe I'll just stick to Linux apps. :)

---

### Post by zvacet on 2007-04-05
Did you put Wine default settings on XP?If you do and still no luck it is another proof that not every win app run under wine well.Just a fact.

---

### Post by silkstone on 2007-04-05
Thanks but yes, I did set it to XP in winecfg. I Googled 'wine faststone' and found a bug report dating back to last year, with a confirmation of the bug from someone else just a few weeks ago. So I don't think it's anything I've done wrong. Back to gThumb!

---

