---
title: "Multimedia codecs"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by SalsaShark on 2008-02-21
Hey guys,

I've looked all over the boards to see if there are any answers to my problems, but I haven't found any.

Basically, I cannot get MP3s, videos, cds, or videos in mozilla to play.  It always says that either I need more files that I don't already have, or I the new software conflicts with software I already have.  What can I do to listen to CDs, mp3s and watch dvds and videos in mozilla (I got flash working, but I'm talking about .wmv files and .movs and avis and what not)?

---

### Post by ImThatNerd on 2008-02-21
This should help you:

[http://getautomatix.com/](http://getautomatix.com/)

Not sure if my link works, but it is called automatix.

---

### Post by SalsaShark on 2008-02-21
Thanks for that, I seem to have gotten a little progress... but I still have a problem:

 sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  automatix2: Depends: tango-icon-theme-common but it is not installable
              Depends: tango-icon-theme but it is not installable
E: Broken packages



That happens after the last step in terminal.  What do I do about that?

---

### Post by ImThatNerd on 2008-02-21
I'm sorry, I just got Ubuntu so I am unsure as to what you do when you get that since it installed fine for me.

---

### Post by confused57 on 2008-02-21
Maybe this will help:
[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

---

### Post by jan quark on 2008-02-21
please

**do not use automatix and do not recommend it further it is known to cause severe compatibility problems**

do you have installed 

ubuntu-restricted-extras

```
sudo apt-get install ubuntu-restricted-extras
```

this should help

---

### Post by hyper_ch on 2008-02-21
AUTOMATIX IS NOT RECOMMENDED!

the proper way is how jan quark said. I'm not sure if libdvdcss2 is also included there. That one is needed for playing DVDs. If you can't add the medibuntu repositories ([http://www.medibuntu.org](http://www.medibuntu.org))

---

### Post by billgoldberg on 2008-02-21
For dvd playback, java and flash I always reccomend this program:

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

It will install all those things for you.

It's easier than the command line and adding repo's.

---

### Post by billgoldberg on 2008-02-21
For mp3 playback -> install the gstreamer codec from synaptic.

Also install totem-mozilla from synaptic to be able to play non-flash videos on the web.

---

### Post by Funky91 on 2008-02-21
Ubuntu-restricted-extras should do it fine. Its in Synaptic so its easy to find.

---

