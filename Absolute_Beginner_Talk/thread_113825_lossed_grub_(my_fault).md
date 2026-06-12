---
title: "lossed grub (my fault)"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by binks on 2006-01-07
ok so i messed up grub panicked and did a fixmbr to recover my xp as i needed some pics i have stored there 
but now how can i reinstall grub into my system without reinstalling xp or ubuntu(which i have well tweaked and running mighty fine)

cheers in hope binks

---

### Post by Azriphale on 2006-01-07
I had a similar problem when I had to reinstall winXP (you know how it stops working every now and then, i'm sure... )

Here is how I fixed it:

put your Ubuntu install disc in your drive. At the boot screen where it says ask for boot options (press Enter to go into install, type server for a server install, all of that), type "rescue" and press enter.

you need to know what device grub was previously installed on. Mine was installed on /dev/sda (first drive, containing linux and windows). yours is probably the same.

It will ask you for location, language, keyboard layout and all that stuff like in the normal install, but it is in rescue mode, as displayed in the top left corner of the screen.

once the system boots (it boots to a virtual disc mounted on /), type 
```
grub-install /dev/sda
```

that should reinstall grub to the original location on your machine. I think.

---

### Post by binks on 2006-01-07
fixed it cheers m8 another reason i love these forums :):)

---

### Post by Yvqkck on 2006-01-07
I am new with Ubuntu also, but just wanted to point out that I had to use (grub-install /dev/hda) in my case, I do not know if dev/sda is the norm for a hd in other systems.

Great post Azriphale!!

---

### Post by Azriphale on 2006-01-07
glad i could help.

---

### Post by Azriphale on 2006-01-07
I think my drive is /dev/sda because its a Serial ATA device, although my IDE hard drive in the same machine in /dev/sdb and my second SATA device is /dev/sdc

Before I used SATA (which was also before my Ubuntu days, I was with SuSE then) my devices were /dev/hdX

---

