---
title: "Ubuntu doesnt boot"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by hardikorama on 2007-08-19
I have an HP pavillion dv6000 laptop with the troublesom broadcom wireless card. Due to that, I wasnt able to run the live cd. I used the alternate cd to do the installation. But now, it doesnt seem to hav worked as ubuntu doesnt load. At the boot screen, the bar below the text, 'ubuntu', freezes halfway. It just doest progress. Please help.

---

### Post by Arthur Archnix on 2007-08-19
In your bios, check to see if you have something called "high precision timer", if so disable it.

If that doesn't work, reset to defaults, reboot and go into grub. Chose your current linux kernel but choose 'e' to edit. Add the option "noapic" and then 'b' to boot. If that works you can add it permanently by editing your /boot/grub/menu.lst

---

### Post by hardikorama on 2007-08-19
I checked the bios and there is nothing like "high precision timer" present. When i use noapic and boot, the screen gets stuck at "Loading hardware drivers".

---

### Post by Arthur Archnix on 2007-08-19
Edit: Ignore: Does [this]("http://ubuntuforums.org/showthread.php?t=282094") thread help?

Try this link:[ hp dv6000 ubuntu wiki]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by hardikorama on 2007-08-19
Thanks for the Link. I am trying it out currently.

---

