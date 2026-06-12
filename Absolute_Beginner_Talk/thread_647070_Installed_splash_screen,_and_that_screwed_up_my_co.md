---
title: "Installed splash screen, and that screwed up my computer!"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-12-21
Well, I installed [this]("http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468") splash image into my computer, but all that shows is a black screen, while my caps lock and scroll lock LEDs go on and off repetitably. Luchily, I have other Ubuntu partition on my computer, so is therea ny way to restore the splash screen to the default?

---

### Post by spiderbatdad on 2007-12-21
what do you have in /etc/usplash.conf  ?

and could you post /boot/grub/menu.lst ?

---

### Post by Fixman on 2007-12-21
> **spiderbatdad said:**
> what do you have in /etc/usplash.conf  ?

```
# Usplash configuration file
xres=1280
yres=1024
```

Just that.

---

### Post by spiderbatdad on 2007-12-21
ok xres and yres need to be 1024, 768 

and in /boot/grub/menu.lst the block of text that lists you current kernel should have the line vga=791

also do you have usplash installed?

---

### Post by spiderbatdad on 2007-12-21
[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

---

### Post by Fixman on 2007-12-21
> **spiderbatdad said:**
> ok xres and yres need to be 1024, 768 

and in /boot/grub/menu.lst the block of text that lists you current kernel should have the line vga=791

also do you have usplash installed?

Well, yes, I tried what you told me and, when I booted it told me an error about "kernel panic", and I had to reboot. Yes, I have uSplash installed.

---

### Post by spiderbatdad on 2007-12-21
```
cd
cd Desktop
sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so

```
And choose the right value (write the number displayed near the file called 'usplash-theme-fingerprint.so' then press Return to confirm)
```

    sudo update-initramfs -u
```

---

### Post by Fixman on 2007-12-21
> **spiderbatdad said:**
> ```
cd
cd Desktop
sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so

```

```

    sudo update-initramfs -u
```

How do I run all this if I can't access the terminal of that partition? Anyway, what I wanted as not to install the theme, but to restore the original splash theme

---

### Post by spiderbatdad on 2007-12-21
sorry thought you had accessed the terminal with ctrl-alt-f1 from boot screen...if you can then you can reinstall usplash usplash-theme-ubuntu

---

### Post by Fixman on 2007-12-21
help!

---

### Post by Fixman on 2007-12-21
seriously, help me please!

---

### Post by Fixman on 2007-12-22
I can't even use my computer!

---

### Post by Fixman on 2007-12-22
Just think about how horrible it is!

---

### Post by Fixman on 2007-12-22
Only you can help me get out this pain!

---

### Post by Fixman on 2007-12-22
I need help!

---

### Post by spiderbatdad on 2007-12-22
i was able to mount a file system, with dapper on it, to my desktop then navigate through the various directories using the terminal and finally gedit whatever files i needed to change on the "/media/disk" (which was actually the mounted file system).

have you tried ctrl-alt-f1 during the boot process when your 7.10 freezes?

---

