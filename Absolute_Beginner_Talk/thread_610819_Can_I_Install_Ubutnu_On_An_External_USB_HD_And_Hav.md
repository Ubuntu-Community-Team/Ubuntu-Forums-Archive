---
title: "Can I Install Ubutnu On An External USB HD And Have Network?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Minker17 on 2007-11-12
If I install Ubuntu on an external USB HD, can I use the network connection on my desktop? I don't want to partition my current Vista machine, but I want to use Ubuntu. If I can in fact use the network connection on my desktop, is there any way to boot to it if my BIOS doesn't have a boot to USB option?

Does any of that make sense? Thanks!:)

---

### Post by spideygal on 2007-11-12
Makes a lot of sense. Just install Ubuntu to your USB hard drive and set bios to boot from it.

---

### Post by Minker17 on 2007-11-12
Is there any way to determine if my BIOS will boot from USB without restarting my pc?

---

### Post by gheorghe_pop on 2007-11-12
Yes. juts go to boot devices and check if you have USB HDD as an option. The menu diferes from bios to bios. You can also try a minimalistic distribution,like [http://featherlinux.berlios.de/]("http://featherlinux.berlios.de/").

---

### Post by shad0w_walker on 2007-11-12
Most motherboard manuals should say something about USB boot, though with anything in the last 2-3 years its a fairly safe bet it will support USB booting.

---

### Post by houstonbofh on 2007-11-12
> **Minker17 said:**
> Is there any way to determine if my BIOS will boot from USB without restarting my pc?
No.  However, if you can not (or don;t want to) you could try this. [https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)  You know you can boot off a CD, and this allows you to save changes to a USB stick.

---

### Post by Minker17 on 2007-11-12
Well I decided to just try it and see. I unplugged my local HD and booted from the CD. I partitioned my USB HDD and installed Xubuntu on it. I did have the option to boot from USB and did that. I got network and everything (having issues setting up my work mail), installed updates and shut down. Reconnected everything and booted up and had the option to boot to either OS.

So everything seems to be working well. In my Ubuntu folder, I have an uninstall ubuntu option. If I ever want to get rid of it, do I just select that and then reformat my partition? Basically, if I ever want to get rid of Xubuntu and revery my external drive back to how it was an hour ago, what do I do?

---

### Post by Minker17 on 2007-11-12
Oh, and is there any way to boot up xubuntu within XP, or will I have to boot into Xubuntu every time I want to run it?

---

### Post by Minker17 on 2007-11-12
I meant to say Vista instead of XP and my buddy said he thinks there is something, but a guy I work with says it's not possible.

---

### Post by houstonbofh on 2007-11-12
> **Minker17 said:**
> Oh, and is there any way to boot up xubuntu within XP, or will I have to boot into Xubuntu every time I want to run it?
The only way is with a Virtual Machine.  This is VMware, parralells, Microsoft Virtual PC, or Qemu.  Qemu is free and portable.  You might even be able to install and run it from your USB stick.

---

