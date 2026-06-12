---
title: "Isolation"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Don1500 on 2007-05-02
Hi, I'm a complete novice to Linux and Ubuntu. From what I have read and seen here I believe I have found what I need to accomplish my task.

I have a windows based laptop and want to Isolate the internal hard drive from access when I am using Ubuntu. I have used only the CD based .ISO file so far and that works good, but it is not "installed" in any hard drive so nothing is saved, ie I have to reconfigure whenever I boot.

I want to use a USB 126 gig hard drive (By wolverine). This drive is recognized by Ubuntu and works fine under this OS. 

Now my question: If I load Ubuntu on the Wolverine drive and do not mount the internal hard drive will the internal drive ever be accessed by the OS? (Part 2) Can I still boot from the CD and have my preferences (monitor resolution, favorites, etc.) recovered from the Wolverine Drive?

Thanks in advance, I hope these questions aren't too basic.

---

### Post by vedace on 2007-05-02
Welcome.

Googling "install ubuntu external hard drive" without the quotes will give you plenty of information about how to install ubuntu on an external drive.  If you do this, then, yes, you can set things up so that ubuntu never touches your internal hard drive.  If you want to simply boot from the live cd every time but be able to access your settings, you can follow the directions [here ]("https://help.ubuntu.com/community/LiveCDPersistence") for saving your settings on a USB flash drive.  To do this with an external USB drive is exactly the same thing, just a little bit slower.

---

### Post by Don1500 on 2007-05-02
Thanks, exactly what I needed.

---

### Post by orb9220 on 2007-05-02
> I have a windows based laptop and want to Isolate the internal hard drive from access when I am using Ubuntu.

I have Ubuntu installed on drive with winXP and if I don't mount the xp partition it will not be seen ot accessed by ubuntu.

If you set-up a dual boot then you don't need the usb drive except for storage of data or a liveCD to carry around. On bootup you can choose to boot to xp or ubuntu and you decide if you want either to have access to the other's filesystem.

In other words Ubuntu will not see read write to your xp unless you want it to.

---

### Post by Don1500 on 2007-05-02
Thanks, But I need it to be 100% off the windows drive. And I can not partition that dive.

---

### Post by jfinkels on 2007-05-02
> **Don1500 said:**
> Thanks, But I need it to be 100% off the windows drive. And I can not partition that dive.

As long as you don't mount it, you should be just fine.

You could always buy a write blocking hardware device :D

---

