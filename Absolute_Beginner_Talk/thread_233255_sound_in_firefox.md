---
title: "sound in firefox?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by detoj on 2006-08-09
Hi, I'm new to ubuntu and linux, and I'm still trying to configure and set everything up.  One problem I'm having is that if I try to play a video through firefox, such as one from a site like youtube.com, I get the video but no sound.  Is anyone else having this problem? Do I need a plugin or a program or something?  Thanks!!

---

### Post by GuitarHero on 2006-08-09
I've had problems with that too.  Try this:
```

sudo apt-get install alsa-oss

sudo kate /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"
```

---

### Post by detoj on 2006-08-09
thanks for the response!
I tried what you said, but I got this message after the second line:

sudo: kate: command not found

help?

---

### Post by Sanjay on 2006-08-09
```
sudo apt-get install alsa-oss

sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP="aoss" 
```

kate is the equivalent editor for "Kubuntu" the KDE version of ubuntu, Gedit is the standard Ubuntu equivalent and will work in place of kate.

Hope That Helps, SanJ

---

### Post by GuitarHero on 2006-08-09
Oops sorry my bad, yes replace kate with gedit and it should work.

---

### Post by detoj on 2006-08-09
well, I edited the file like you suggested, but still no sound.  I am able to hear sounds in other programs, like rhythmbox, but not through the browser.

---

### Post by Dr. Nick on 2006-08-09
thier is another possible solution here

[http://ubuntuforums.org/showthread.php?t=204022](http://ubuntuforums.org/showthread.php?t=204022)

seems to be a very common issue

---

### Post by detoj on 2006-08-10
okay, so I redid the FIREFOX_DSP="aoss" and this time it worked for some reason, so thanks!!  However, now the sound is out of sync and gets more out of sync the longer the video runs.  I tried the suggestion [here]("http://ubuntuforums.org/showthread.php?t=186594"), but that did not work.... any ideas?

also, I have seen some people mention that using aoss will cause firefox to crash.  Is this true and if so is there a way to prevent it?

Thanks!

---

### Post by indrajeetak on 2006-08-15
```

sudo apt-get install alsa-oss

sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP="aoss" 

```


Thanks a lot. I tried the above and it worked. I was so pissed off and now I am back on UBUNTU.

---

