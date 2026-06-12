---
title: "Why Is My Boot Screen Blank?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-02-27
Hello all.  I've gotten to the point in my Gutsy install that I'm trying to dress things up a bit.  I've gotten a grub screen showing with an image, and I've changed the splash screen to one that I like.

My problem is that after the splash screen when the progress bar goes away, there is just nothing but a plain screen, color of like a light tan.  That blank screen just stays blank until about 10-15 secs later when the desktop shows up.

Is there something I can do to dress that blank screen up some?  It's very boring, not to mention that people who come over to look at my new OS ask me if something has gone wrong...  

I don't get the login screen, because I'm the only one using this computer, and thus have bypassed it.   So, I guess I'm asking if I can replace the blank login screen??

Thanks!

FwF

---

### Post by kool_kat_os on 2008-02-27
do you have xgl thing running?

---

### Post by FreewareFan on 2008-02-27
Yes, compiz-fusion is running on my desktop.  I don't see how that would affect boot up screens.  Does it?

---

### Post by glennric on 2008-02-27
Compiz shouldn't affect the boot splash screen.  Try doing 
```
sudo update-initramfs -u
```

---

### Post by FreewareFan on 2008-02-27
What does that command do?  I like to learn along the way.  And, my splash screen with the progress bar works fine, but then when it's time for the system to switch to the login screen, that's when I get the plain tan screen until my desktop shows up...

---

### Post by Zorael on 2008-03-08
Wait, so, this is after X boots up (cursor shows), but before your desktop is drawn?

Then the light tan would be the default background color for Ubuntu, which is changeable someplace, possibly through the administrative options, or through the gconf tool.

---

### Post by FreewareFan on 2008-03-08
> **Zorael said:**
> Wait, so, this is after X boots up (cursor shows), but before your desktop is drawn?

Yes, that is correct.

> 
Then the light tan would be the default background color for Ubuntu, which is changeable someplace, possibly through the administrative options, or through the gconf tool.

You are also correct, in that to change the background color one would edit the file /etc/gdm/PreSession/Default .   This is how I got the tan color.

Now my question still is this:::  Is there a way to display a graphic, photo, or whatever, instead of that plain tan screen, just before the desktop appears?

Thanks!

FwF

---

### Post by nevlis on 2008-03-08
I think that's just what gets drawn first... Maybe if you had a wicked fast computer and it all got drawn at the same time?

---

### Post by st33med on 2008-03-08
> **nevlis said:**
> I think that's just what gets drawn first... Maybe if you had a wicked fast computer and it all got drawn at the same time?

Yeah, if he had a hard drive going 20,000 RPMs and a modified Upstart ;).

---

### Post by Zorael on 2008-03-08
In KDE there are three wallpapers; one displayed at the actual login screen, one that's displayed during the splash screen duration, and then lastly your own wallpaper. I'm not sure if gdm allows for wallpapers during the splash, but kdm sure does.

---

### Post by FreewareFan on 2008-03-08
> **Zorael said:**
> In KDE there are three wallpapers; one displayed at the actual login screen, one that's displayed during the splash screen duration, and then lastly your own wallpaper. I'm not sure if gdm allows for wallpapers during the splash, but kdm sure does.


Really?  So at no time during boot up do you see any blank screen?  That would be nice to figure out how to do on Ubuntu.

---

