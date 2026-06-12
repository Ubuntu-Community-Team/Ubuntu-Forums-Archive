---
title: "Grub menu messed up"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-06-27
Windows decided to eat itself (literally! I ran disk cleaner and it wiped ALL files LOL!!) so I reinstalled it, knowing that the grub menu would be overwritten.

I was following [this guide](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub) and all was working fine until I got to this step:

```
grub> root (<tab>
```

When I hit tab, nothing gets listed!

How can I fix my grub so I can boot into Ubuntu and not just XP?

Cheers:popcorn:

---

### Post by spamzilla on 2007-06-27
My Ubuntu partition is (hd0,1) but when I enter

```
root (hd0,1)
```

at the step stated above, I get

```
unrecognised command
```

How can I fix this?

---

### Post by Seisen on 2007-06-27
Try this guide 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub")

---

### Post by spamzilla on 2007-06-27
Hey I did this

```
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,1)".

6. Type "setup (hd0,1)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".
```

but when I restarted, I got the following error message:

```
no bootable devices-- strike f1 to retry boot, f2 for setup utility
```

So I booted back into the livecd having made the problem worse, as I cannot boot into windows :(

---

### Post by Seisen on 2007-06-27
Follow the second option in that link and see if it works.

---

### Post by logos34 on 2007-06-27
The second option on that link uses the 'grub-install' method, but that's more complicated (you have to mount root first)...You could just try what you did before except put grub on the MBR instead of the root partition:

sudo grub
>root (hd0,1)
>setup (hd0)
>quit

---

### Post by spamzilla on 2007-06-27
> **logos34 said:**
> The second option on that link uses the 'grub-install' method, but that's more complicated (you have to mount root first)...You could just try what you did before except put grub on the MBR instead of the root partition:

sudo grub
>root (hd0,1)
>setup (hd0)
>quit

Woot that worked, thanks :KS

---

### Post by ryanVickers on 2007-06-27
I would recommend Super Grub Tool (I think it's called).  You can restore grub to the master Boot Record and/or the ubuntu partition, and if it still doesn't work, boot from a live cd and look in your HD's linux /boot/grub/menu.lst and make sure it's looking in the correct partition for ubuntu

Edit: too slow! :(

---

