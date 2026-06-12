---
title: "Can no longer boot Gutsy after upgrading to new kernel"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Angus77 on 2007-12-19
The update manager told me there was a new version of the kernel today. I accepted it, and then it told me I had to reboot. I rebooted, and now I can no longer use Gutsy---all I get is the ash shell, and I can't boot into Gnome or access anything under /home.

It's a good thing I still have Feisty on another partition!

How can I fix this?

---

### Post by Joeb454 on 2007-12-19
what happens if you type ```
start x
```

Can you access that /home partition from Fiesty?

---

### Post by spiderbatdad on 2007-12-19
try booting into failsafe..it may take several minutes. From there if you can access a terminal, it may just be usplash that is messed up.```
gksu gedit /etc/usplash.conf
```
and check xres and yres. set to 1024, 768, if that is your normal screen res. then run:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by Angus77 on 2007-12-21
I tried these commands, and just got told that they couldn't be found. Something like:

```
sudo: could not be found
```

(I'd love to cut and paste what it said exactly. Should've written it down!)

---

### Post by philinux on 2007-12-21
For some reason some people are getting a grub error after the kernel update. It did not affect me.

It seems to change the pointer to root in grub.

[http://ubuntuforums.org/showthread.php?t=645116](http://ubuntuforums.org/showthread.php?t=645116)

---

### Post by Angus77 on 2007-12-22
Well, Gutsy actually boots, but it boots into the ash (not bash) shell.  I don't get an Error 17.

---

