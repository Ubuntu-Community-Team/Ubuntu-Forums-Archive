---
title: "I want xubuntu!!"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-11-02
I want to get xubuntu, but my bios doesnt support CD boot and the Smart boot manager thing doesnt work.  I've tryed almost every thing.  Is there a way to download the image and install it right on your desktop?

---

### Post by pay on 2006-11-02
Depends on what operating system you are using. If you are using Ubuntu or kubuntu then you just need to ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```If you are on Windows then no.

---

### Post by lordvolo on 2006-11-02
I hate windows

---

### Post by TheMono on 2006-11-02
lol. You can do a network install, where you install Xubuntu on another computer, network it to the one that cannot boot from disc, and install via the network.

See [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by gn2 on 2006-11-02
> **lordvolo said:**
> I want to get xubuntu, but my bios doesnt support CD boot and the Smart boot manager thing doesnt work.  I've tryed almost every thing.  Is there a way to download the image and install it right on your desktop?

I've been told it's possible to remove drive, put it in another PC, install Xubuntu, then replace in original PC. Re-boot, at prompt type "sudo dpkg-reconfigure -phigh xserver-xorg" (without the quotes) and adjust for the different hardware.

---

### Post by skymt on 2006-11-02
> **gn2 said:**
> I've been told it's possible to remove drive, put it in another PC, install Xubuntu, then replace in original PC. Re-boot, at prompt type "sudo dpkg-reconfigure -phigh xserver-xorg" (without the quotes) and adjust for the different hardware.

That's asking for trouble. The X server is far from the only thing that would need to be reconfigured.

Anyway, see if any of [these](https://help.ubuntu.com/community/Installation) installation methods work. [WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies) and [FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) seem relevant.

---

### Post by doobit on 2006-11-02
> **lordvolo said:**
> I want to get xubuntu, but my bios doesnt support CD boot and the Smart boot manager thing doesnt work.  I've tryed almost every thing.  Is there a way to download the image and install it right on your desktop?

If you have a floppy drive, then you can boot from a boot floppy and install from the CD.

[https://help.ubuntu.com/community/SmartBootManagerHowto?highlight=%28boot%29%7C%28floppy%29](https://help.ubuntu.com/community/SmartBootManagerHowto?highlight=%28boot%29%7C%28floppy%29)

also:

[https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28floppy%29](https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28floppy%29)

---

### Post by disc on 2006-11-02
> **pay said:**
> Depends on what operating system you are using. If you are using Ubuntu or kubuntu then you just need to ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

By installing Xubuntu over Ubuntu with this command, would I keep all my applications/files?

---

### Post by doobit on 2006-11-02
Yes, because you are just installing the files needed for the XFce GUI. You will see some warnings that some packages will be uninstalled, but don't worry, they are things that will be replaced by other things that work the same way, so nothing will be disturbed. I found it was actually pretty cool to have more than one desktop window manager choice.

---

### Post by disc on 2006-11-02
Okay, I've installed Xubuntu via the terminal, is it suppose to automatically switch desktop environments, or do I have to change a setting somewhere?

---

### Post by TheMono on 2006-11-02
When you go to log in, click on Sessions, and choose XFce session.

---

### Post by disc on 2006-11-02
> **TheMono said:**
> When you go to log in, click on Sessions, and choose XFce session.

Er, it seems to have created a problem for me. I posted it here: [http://www.ubuntuforums.org/showthread.php?t=291759](http://www.ubuntuforums.org/showthread.php?t=291759)

---

### Post by Tipo on 2006-11-02
At the login screen, there should be a button called "sessions" in the bottom left corner. You can choose Xfce from there, and set it as the defaault session :)

---

