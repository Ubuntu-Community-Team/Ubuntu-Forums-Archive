---
title: "How do I remove Windows?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by patience on 2007-02-10
Happily, I have Ubuntu Edgy running great on my laptop.  I have it set up as a dual boot machine, but I no longer need Windows on this machine.  

Is there an easy way to dump windows and reclaim that partition, without having to reinstall Edgy?  I've spent blood, sweat & tears getting wireless and other things set up; I really don't want to go through that again if it can be avoided.

---

### Post by aidanr on 2007-02-10
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

download, burn, boot, delete windows partition, resize ubuntu partition

---

### Post by patience on 2007-02-10
That's it?  Boy that is easy.  Thanks for the quick reply.

---

### Post by jordanmthomas on 2007-02-10
Also, if you have your windows partition mounting automatically on boot, you will need to remove any references to it in /etc/fstab

If your Windows installation is on....say /dev/sda1 and your Ubuntu is on /dev/sda2 you will need to do more work than just deleting the Windows partition and resizing your Ubuntu one.  (You'll just need to update /boot/grub/menu.lst to reflect the new locations of your kernel and /etc/fstab as well)

---

### Post by confused57 on 2007-02-10
Easiest way would probably be to use the gparted live cd & just reformat the Windows partition as ext3(primary partition) & use it as a data partition for Ubuntu...least you have several choices.

---

### Post by jordanmthomas on 2007-02-10
I agree with confused57, that would be the easiest in the case your windows was installed before Ubuntu
If you're confused about partitioning at all I'd suggest you do that instead of what I suggested.

---

### Post by patience on 2007-02-10
> **jordanmthomas said:**
> Also, if you have your windows partition mounting automatically on boot, you will need to remove any references to it in /etc/fstab

Ah, it did seem a little too good to be true.  The windows partition is indeed mounting on boot. 

> **jordanmthomas said:**
> If your Windows installation is on....say /dev/sda1 and your Ubuntu is on /dev/sda2 you will need to do more work than just deleting the Windows partition and resizing your Ubuntu one.  (You'll just need to update /boot/grub/menu.lst to reflect the new locations of your kernel and /etc/fstab as well)

Is this the proper order for this operation?

1. edit /etc/fstab to remove any references to mounting the windows partition
2. edit /boot/grub/menu.lst to remove references to windows
3. run the liveCD to delete the windows partition and resize my linux partition.

Do I get it?

---

### Post by jordanmthomas on 2007-02-10
You get it for the most part, but you will also need to edit the numbers for your Ubuntu kernel
For example, my menu.lst modified to match yours a little bit.
```

# (0) Arch Linux
title  Arch Linux
root   (hd0,[COLOR="Red"]1[/COLOR])
kernel /boot/vmlinuz26 root=/dev/sda[COLOR="Red"]2[/COLOR] ro vga=792
initrd /boot/kernel26.img

```

Since you are removing /dev/sda1 your linux will become /dev/sda1 so the red values above would need to be changed to 0 and 1, respectively.

You will need to do similar editing in /etc/fstab
Fixing your Linux stuff is critical, while you will just get annoying messages if you don't take out references to Windows.

---

### Post by patience on 2007-02-10
That makes sense.  The other solution is tempting too.  

One last question.  If I manage to screw up the configuration, I assume that I can run Ubuntu from the CD and correct the files, then reboot to get back to normal.  Is that a correct statement?

---

### Post by jordanmthomas on 2007-02-10
Yes, that is correct.
Unless, of course, you format the wrong partition.  Then you're in trouble.  :)

---

### Post by patience on 2007-02-10
LOL!  Trust me, I won't even admit it if I do that! :)

---

