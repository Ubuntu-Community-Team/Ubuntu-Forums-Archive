---
title: "[SOLVED] How do you completely COMPLETELY remove a program?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by twoseids on 2007-12-27
My VLC all of a sudden isn't opening when I try to open it. I had just given it a new skin and was trying to revert back to the original boring look when I must've offended it. Now it won't open at all, whether I try through the menu, Alt+F2 or right-clicking a video file in Nautilus and doing, "Open with VLC."

I want to uninstall it and re-install it, but when I do, it doesn't re-download it - just reinstalls. Even when I do "Complete Removal" and reinstallation, same thing. I tried -purge in the command line - same thing.

Maybe I'm missing the point here. Can someone help? I'm lost without VLC. Thanks!

---

### Post by terminal on 2007-12-27
Type vlc in a terminal it will atleast show what is causing it to crash . you can use below command to purely remove it and reinstall  . I assume u used apt-get to get it

sudo apt-get remove vlc --purge
rm -fr ~/.vlc
sudo apt-get install vlc .

---

### Post by SOULRiDER on 2007-12-27
Purge it with aptitude
```
 aptitude purge <program>
```
Theres also probably somehting left of it in your home directory, check out for a hidden folder in there. In the case of vlc it should be called .vlc, so you could do
```
rm -r ~/.vlc
```

---

### Post by twoseids on 2007-12-27
Yes! That did the trick. I've got my VLC back. Thanks terminal and SOULRiDER!

---

### Post by SOULRiDER on 2007-12-27
You should always try to use aptitude instead of apt-get, its better for handling dependencies. Also, could you please mark the thread as solved? You can do it fromt he Thread Tools meny.

Thank you!

---

