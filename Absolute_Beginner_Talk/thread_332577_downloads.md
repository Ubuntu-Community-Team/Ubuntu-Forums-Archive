---
title: "downloads"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by RHS on 2007-01-06
Help!
My firefox will not save any downloads from the internet.  The window hangs up for about 30 seconds, then clears but the download manager never appears and then the file is not saved.  what is wrong??
Thanks!

---

### Post by Vorian on 2007-01-06
It may be the source, or does this happen on all downloads from different sources?

---

### Post by RHS on 2007-01-06
all downloads all sources--i just tried it in several places

---

### Post by taurus on 2007-01-06
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by RHS on 2007-01-06
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              91G  3.5G   83G   5% /
varrun                236M   88K  236M   1% /var/run
varlock               236M  4.0K  236M   1% /var/lock
udev                  236M  100K  236M   1% /dev
devshm                236M     0  236M   0% /dev/shm
lrm                   236M   19M  218M   8% /lib/modules/2.6.15-26-386/volatile

---

### Post by Pixilarion on 2007-01-06
> **RHS said:**
> all downloads all sources--i just tried it in several places

I guess you're internet connection is in trouble. Make sure you're internet connection is fully up and running and try to download something from an FTP server. If the speeds is really slow, maybe you're connection is failing. Downloading through Firefox (i.e. HTTP traffic) has more difficulty with these slowdowns...

---

### Post by taurus on 2007-01-06
What exactly are you trying to download?  You can download it from a terminal with wget...

---

### Post by RHS on 2007-01-06
I just downloaded firefox broser latest version and it worked.  it is a exe file on my desktop--but i cannot save pictures from the web.  now what?

---

### Post by taurus on 2007-01-06
Were you downloading the latest version of firefox for your Windows because .exe is the wrong file for Linux...

What site did you try to save those pictures because some sites won't allow you to save those pictures to your computer?

---

### Post by RHS on 2007-01-06
Sorry, it is a bin file.  I cannot save Any image for any web site!  help!!

---

### Post by taurus on 2007-01-06
Can you give one example (site) so I can if I can save the image to my machine?

---

### Post by obsidion on 2007-01-06
> ]Sorry, it is a bin file.  I cannot save Any image for any web site!  help!!
> I just downloaded firefox broser latest version and it worked. it is a exe file on my desktop--but i cannot save  > pictures from the web. now what?

  It could be me but I have never seen a bin version of Firefox tar.gzs yes exe yes deb and rpm yes but never a bin file. Not for linux anyway where did you get it from and are you sure it is for your system. Why do you want to save images for websites, are you wanting to steal them and pass them off as your own, what are you actually trying to achieve ?

---

