---
title: "Help fixing Ubuntu OS"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by ACF1 on 2007-11-26
Well, I was trying to change something on my Ubuntu system, and I wrecked something pretty good.  What can I do to either, get back to a working system, or at least save my files and do a fresh install?  If more information is needed, let me know.  Thanks.

---

### Post by PeterJS on 2007-11-26
What were you trying to change? and what if anything is working right now?

---

### Post by rabid9797 on 2007-11-26
without more specific information, there is really nothing we can do to help you fix your system. could you please provide any error messeges or what happened to your system?

if you can't, the best thing you can do is boot into a live cd(ubuntu live), and transfer all the data you need over to a flashdrive or another partition on your hardrive, or burn it to a CD/DVD and then to a complete reinstall of ubuntu.

---

### Post by ACF1 on 2007-11-26
> **rabid9797 said:**
> without more specific information, there is really nothing we can do to help you fix your system. could you please provide any error messeges or what happened to your system?

if you can't, the best thing you can do is boot into a live cd(ubuntu live), and transfer all the data you need over to a flashdrive or another partition on your hardrive, or burn it to a CD/DVD and then to a complete reinstall of ubuntu.

How do I back up my files to a flash drive using the live cd?  I think that may be my best option.  Thanks.

---

### Post by ACF1 on 2007-11-27
Here is what my screen looks like when it starts up. [ LINK]("http://img107.imageshack.us/img107/201/1001502ob7.jpg")

What do you think I should do?  Thanks.

---

### Post by PeterJS on 2007-11-27
Oh that's not so bad, the system boots up just fine, it just doesn't load the graphical interface. Press ctrl+alt+F1 to get to the first physical terminal, and login. Then try:
```

sudo dpkg-reconfigure xserver-xorg

```
This should try and reconfigure your graphics drivers for you. After that try:
```

startx

```
if that loads up you can then reboot and everything should be fine.

If that doesn't work tell us what your graphics card is and we'll see what we can do for you.

---

### Post by ACF1 on 2007-11-27
Here is what comes up now.  [LINK]("http://img153.imageshack.us/my.php?image=100150301ky0.jpg")

As far as I know, I entered every thing correctly.  Also, that is where I originally messed it up.  What else should I do/ what am I doing wrong?

---

### Post by PeterJS on 2007-11-28
> **ACF1 said:**
> Here is what comes up now.  [LINK]("http://img153.imageshack.us/my.php?image=100150301ky0.jpg")

As far as I know, I entered every thing correctly.  Also, that is where I originally messed it up.  What else should I do/ what am I doing wrong?

Sad :(
That is most certainly a broken X server. What graphics card do you have?

---

### Post by ACF1 on 2007-11-28
I have an ATI Radeon 7500, I believe.  I have been using Ubuntu for about the past year, and I like it a lot.

---

### Post by jfinkels on 2007-11-28
Can you post the output of the following command:```
cat /etc/X11/xorg.conf
```

If we find out whether you're using 'ati' or 'fglrx' driver, maybe we can try to reinstall your driver.

---

### Post by PeterJS on 2007-11-28
> **ACF1 said:**
> I have been using Ubuntu for about the past year, and I like it a lot.

Ok, well what were you changing when everything broke?

---

### Post by ACF1 on 2007-11-28
> **PeterJS said:**
> Ok, well what were you changing when everything broke?

I updated it to the newest version (of Ubuntu), and then it didn't have the screen resolution I have been using (1024x768).  So I tried to change it through the terminal....  Basically, I think I did the same thing you had me do to try and fix it, and that is how I broke it.

---

### Post by ACF1 on 2007-11-28
> **jfinkels said:**
> Can you post the output of the following command:```
cat /etc/X11/xorg.conf
```

If we find out whether you're using 'ati' or 'fglrx' driver, maybe we can try to reinstall your driver.

OK, here is what it did.  [LINK]("http://img504.imageshack.us/my.php?image=1001504te5.jpg")

---

### Post by jfinkels on 2007-11-28
Err, my bad. Forgot you can't post/see the entire output. Do the following:```
cat /etc/X11/xorg.conf | grep Driver
```You will see a line that says either "ati" or "fglrx". All we need to know is which one it is.

---

### Post by ACF1 on 2007-11-28
It says ati.

---

### Post by jfinkels on 2007-11-29
Try to reinstall the ati driver:```
sudo aptitude reinstall xserver-xorg-video-ati
```

Then do this:```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by ACF1 on 2007-11-29
> **jfinkels said:**
> Try to reinstall the ati driver:```
sudo aptitude reinstall xserver-xorg-video-ati
```

Then do this:```
sudo dpkg-reconfigure xserver-xorg -phigh
```

OK, I did that and it still doesn't work.  Any other ideas?

---

### Post by jfinkels on 2007-11-29
My only idea is to flat out remove xserver-xorg-core to remove all xserver dependencies/files, and then reinstall them. So if you're willing to give this a shot (it may just be easier for you to reinstall, if you were able to install in the past with video working correctly) do:```
sudo aptitude remove xserver-xorg-core
```And type "Y" when it prompts you to remove a bunch of other stuff. This will take a while. Then do ```
sudo aptitude install xorg xserver-xorg xserver-xorg-input-all xserver-xorg-video-ati[code] and [code]sudo dpkg-reconfigure xserver-xorg -phigh
```

This whole process will uninstall and reinstall a LOT of files. If you are willing to do this, then be patient. If it doesn't work or you aren't comfortable with all this reinstalling, you may just want to do a full reinstall of Ubuntu.

---

### Post by ACF1 on 2008-06-05
I decided to do the whole remove and reinstall a whole lot of stuff process.  And.... It didn't work!  LOL, I must have really wrecked it.  It said fatal error and then something about a battery.  I don't know if there is anything that can be done, but thanks guys.

---

### Post by ACF1 on 2008-06-07
I know I took forever to do the whole remove/install thing, but does anyone have any thoughts on why I can't get graphics?  Thanks.

---

