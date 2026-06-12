---
title: "Ubuntu 9.10 on Macbook5,2:  no progress"
date: 2010-04-19
forum: Apple Hardware Users
---

### Post by hrsetrdr on 2010-04-19
I have a Macbook5,2 and understand that Ubuntu 9.10 is the recommended version to go with; rEFIt is already installed, free space on hdd is available.   I followed [this guide]("https://help.ubuntu.com/community/MacBook5-2/Karmic") but never get even to the live desktop, just a blank screen.  I tried "F6" after choosing language, even tried "F4" for alternate boot options, but still only get blank screen.  I've left it sitting at the blank screen for over 20 minutes but see no signs of progress.

Any/all suggestions will be welcome.

---

### Post by linuxopjemac on 2010-04-19
> Basic Installation Instructions

Booting the kernel from the (Live)CD has to be changed. Or else you get a black screen and does nothing at all after 2 seconds of kernel boot. Hit F6 to change the boot options after you selected the language. Then disable acpi enter  acpi=off  in the boot line. I also added,  noapic nolapic irqpoll vga=771 . If you don't want to loose acpi functions you can add this other option  maxcpus=1 . 

Did you do this ?

---

### Post by hrsetrdr on 2010-04-19
I choose my language, hit "F6" but get no further, there's a blinking curser then just a blank screen...forever.

---

### Post by linuxopjemac on 2010-04-20
You could try an alternate installation without GUI to start with. You then poke around to  have GRUB working. Then you just add the desktop, for GNOME:

```
sudo apt-get install ubuntu-desktop

```

Just take a mirror, go to 9.10 and download Koala's alternate installer (PC (Intel x86) alternate install CD). This will give you at least a Linux box to start with.

---

### Post by hrsetrdr on 2010-04-20
> **linuxopjemac said:**
> You could try an alternate installation without GUI to start with. You then poke around to  have GRUB working. Then you just add the desktop, for GNOME:

```
sudo apt-get install ubuntu-desktop

```

Just take a mirror, go to 9.10 and download Koala's alternate installer (PC (Intel x86) alternate install CD). This will give you at least a Linux box to start with.

That's worth a try, I had not thought of using the alternate install CD.

Thanks!  ;)

---

