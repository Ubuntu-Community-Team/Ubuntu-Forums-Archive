---
title: "Microcode &quot;bcm43xx_microcode4.fw&quot; Error"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by jb6000 on 2007-05-04
Hello,

I have a bad wireless card before I installed ubuntu so I know it's not going to work.

Now that I have ubuntu running on my laptop every now and then I get the following error:

bcm43xx: Error: Microcode "bcm433xx_microcode4.fw" not available or load failed.

I know how to disable this message by doing the command:

sudo modprobe -r bcm43xx  

BUT it returns every time I boot up.

What boot file do I need to edit so this does not get loaded again?

TIA

---

### Post by davahmet on 2007-05-04
Try running in your terminal:
sudo echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist

to add it to your blacklist so the kernel isn't trying to load it during boot.

---

### Post by jb6000 on 2007-05-04
I get a Permission Denied.

I made sure I typed sudo but it did not help.

---

### Post by davahmet on 2007-05-04
Hmmm...OK, in that case,
sudo gedit /etc/modeprobe.d/blacklist

and then add the line at the bottom
"blacklist bcm43xx"

---

### Post by jb6000 on 2007-05-08
I get the following:

Cannot ope display:
Run 'gedt --help' to see a list of available commands.

---

