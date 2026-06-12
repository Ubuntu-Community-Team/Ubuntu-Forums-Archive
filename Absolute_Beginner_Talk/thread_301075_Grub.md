---
title: "Grub"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Desy on 2006-11-16
Can someone tell me where and how to install grub so i can chose from operating systems.  Thanks

---

### Post by taurus on 2006-11-16
Do you already have Ubuntu on your machine?  Basically, you want to install GRUB on MBR--/dev/hda--so you can boot both Windows and Ubuntu after you power up your machine.  If you haven't installed Ubuntu on your machine, there is an option to install GRUB later in the installing process.

---

### Post by Desy on 2006-11-16
Yes I have ubunto already.  I have 2 hard drives 1 with ubunto and one with xp but i dont get the option to choose the os when i boot up

---

### Post by taurus on 2006-11-16
Do you mean when you turn your machine on, you can only boot into Ubuntu and there is no entry for your XP?

---

### Post by Desy on 2006-11-16
Yep thats right

---

### Post by taurus on 2006-11-16
I guess you just need to edit your /boot/grub/menu.lst and add an entry for XP then...

Open a terminal, Applications -> Accessories -> Terminal, and do

```
sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```
Scroll down to the bottom of the file and add these lines to it.

```

title     Windows XP
root (hd0,0)
makeactive
chainloader +1

```
(Assuming your XP is on the first partition of the first drive...)

Reboot and see if there is an entry for "Windows XP" in GRUB!

---

### Post by Desy on 2006-11-16
Ive done this already and nothing happens.  When I connect the both drives together whichever is set to master is the os that loads.  Silly quiestion but how do you know that grub is loaded

---

### Post by taurus on 2006-11-16
When you boot it up, you would see a menu giving you options to which entry you want to boot:  Ubuntu, recovery mode, or memtest thing.  That's called GRUB menu...

However, if you switch harddrive to boot, then your XP would now become slave so it should have beeen "root (hd1,0)"!

---

### Post by Aranel on 2006-11-16
> **Desy said:**
> Ive done this already and nothing happens.  When I connect the both drives together whichever is set to master is the os that loads.  Silly quiestion but how do you know that grub is loaded

In the /boot/grub/menu.lst file, what does it say next to "timeout"? That's the number of seconds GRUB waits before automatically booting Ubuntu (the default is 10). GRUB is obviously installed on your machine already because Ubuntu couldn't boot without it.

Before the Ubuntu splash screen comes up, you should see a black text screen with a white-bordered box in the middle and a few options. The top one should be Ubuntu with its version and its kernel's version, followed by Ubuntu failsafe and, after that, memtest. If that doesn't come up when you first boot up your computer, and if your menu.lst file is set to wait 10 seconds, well... I dunno what the problem is. :-k

---

### Post by confused57 on 2006-11-16
> **Desy said:**
> Ive done this already and nothing happens.  When I connect the both drives together whichever is set to master is the os that loads.  Silly quiestion but how do you know that grub is loaded

You might be able to set your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

