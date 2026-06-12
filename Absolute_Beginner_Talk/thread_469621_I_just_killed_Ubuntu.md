---
title: "I just killed Ubuntu"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by R00tBreaker on 2007-06-10
I have Ubuntu 7.04 and I think I just killed it. I was attempting to update my ATI drivers. This is what I did:

```
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
```

ATI said that after I reboot, I should be good to go. However, when I reboot and select Ubuntu from the GRUB menu, it never boots. The Ubuntu logo comes up, the loading bar fills up, and then I get a blank screen.

---

### Post by loathsome on 2007-06-10
Are you able to get into **tty1?**

---

### Post by R00tBreaker on 2007-06-10
> **loathsome said:**
> Are you able to get into **tty1?**

Sorry, I'm a complete noob and don't know what that means. Not a single thing, no text at all, comes up.

---

### Post by Najand on 2007-06-10
Push ALT+CTRL+F1. Do you see the console?

---

### Post by R00tBreaker on 2007-06-10
Ok, sorry guys. I became impatient. I booted into the live CD and replaced xorg.conf with a backup/original that I had created before and this appears to have fixed it. What in the world did I do to screw up? Should I just avoid trying to install the drivers?

---

### Post by Najand on 2007-06-10
If you still have both xorg.conf files and post them here, we can find out why it happened.

---

### Post by Dokatz on 2007-06-10
In 7.04 theres a way to install the ATI drivers via the System menu.

System>Administration>Restricted Drivers Manager>

This has worked for me, Saved me some time.

---

### Post by R00tBreaker on 2007-06-10
> **Najand said:**
> If you still have both xorg.conf files and post them here, we can find out why it happened.
Sorry, I deleted the one created by the driver installation process. 

Thanks for the info Dokatz. I'll definitely be using this method until I learn some more about Ubuntu/Linux. Thanks for the help guys.

---

### Post by loathsome on 2007-06-10
You could've also done something like **[COLOR="DarkSlateGray"]$ sudo dpkg-reconfigure xserver-xorg[/COLOR]** from a console.

Glad you solved things out.

---

