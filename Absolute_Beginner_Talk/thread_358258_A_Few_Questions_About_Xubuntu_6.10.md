---
title: "A Few Questions About Xubuntu 6.10"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by jzke on 2007-02-10
Hi all,

I was just wondering a few things about my new Xubuntu (6.10) system;

1. Fonts- in Firefox many websites look much worse (compared to Windows) and it's basically just ugly fonts. Where can I install all the MS fonts or equivalent to make my websites look nicer?

2. In the new version of XFCE, it is often claimed to have compositing built-in and the likes. How can I have the simple window transparencies and drop-shadows (built-in ones, not Beryl) turned on?   (BTW I'm using a Fujitsu Lifebook with Intel graphics)

3. I understand I'm only using XFCE 4.4 RC1, how can I update to the latest version?

Thanks in advance :)

---

### Post by Happy_Man on 2007-02-10
1. Go to a terminal and type:

```

sudo apt-get install msttcorefonts

```

2. I'm afraid I don't know, as I don't use XFCE.

3. My advice: don't. The guys up at Ubuntu know what they're doing, and a basic rule of thumb is that if it came with a fresh install and is essential (like XFCE), wait for the repos to  update. What the guys stocking the repos do is tweak it (or keep it tweaked) to best suit the Xubuntu theme, and preference settings. If you install the new version from the site, yo u may lose a preference and not know how to get it back, or (worst case) mess up your entire existing XFCE installation. So wait. Patience is a virtue.

---

### Post by jzke on 2007-02-10
Thank you for the quick reply, unfortunately I get the following error;

> jake@jake-laptop:~$ sudo apt-get msttcorefonts
Password:
E: Invalid operation msttcorefonts

It appears as though there isn't a package, which repo is it in? (I probably haven't enabled it)

That leave's question 2. for any other XFCE users out there... :)

---

### Post by risbac on 2007-02-10
My XFCE computer is not here now, can't remember where it is... But this may help:

[http://ubuntuforums.org/showthread.php?t=343488](http://ubuntuforums.org/showthread.php?t=343488)

---

### Post by Happy_Man on 2007-02-10
Go to Applications --> Add/Remove, and click Preferences. Check the main, universe, restricted, and mutiverse options, and apply changes. When it asks if you want to reload, do so. After that, you can either install msttcorefonts straight from add/remove, or go back to the terminal and do it from there.

---

### Post by borris.morris on 2007-02-10
> **jzke said:**
> Thank you for the quick reply, unfortunately I get the following error;



It appears as though there isn't a package, which repo is it in? (I probably haven't enabled it)

That leave's question 2. for any other XFCE users out there... :)

you messed up. it's sudo apt-get install msttcorefonts
you put sudo apt-get msttcorefonts
you didn't tell it what to do.

---

### Post by Fundi on 2007-02-10
> **jzke said:**
> Thank you for the quick reply, unfortunately I get the following error;

```
jake@jake-laptop:~$ sudo apt-get msttcorefonts
Password:
E: Invalid operation msttcorefonts
```

It appears as though there isn't a package, which repo is it in? (I probably haven't enabled it)

That leave's question 2. for any other XFCE users out there... :)

Try this:

```
sudo apt-get install msttcorefonts
```

---

