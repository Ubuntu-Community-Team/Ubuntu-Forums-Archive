---
title: "get rid of windows"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-14
i spent one night with ubuntu and i am ready to delete windows.. 
i have the LInux and the WIndows partition on the same hard disk.
Can i erase windows and keep my Ubuntu settings and stuff?
if i can't , can i add a "default OS" to load when the computer starts, so i don't have to choose ubuntu everytime?

---

### Post by atihimself on 2007-02-14
I just reformated my windoze partition and made it a storage catalog, didn't know then how to merge it with linux partition

---

### Post by aysiu on 2007-02-14
First of all, I think you should wait a few weeks before deleting your Windows partition. It's always best to take things slow, just in case. One night of Ubuntu may seem like bliss at first, but you may find yourself wanting to boot into Windows tomorrow. You never know.

That said, if you went with the default installation options, you can very well just delete the Windows partition, format it as Ext3, and then mount it somewhere, and everything should be fine. More details here:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

*But* I have the feeling that you *didn't* do a default installation (which installs Grub to the MBR); otherwise, you would already have Ubuntu as the default OS. Are you doing some kind of awkward dual boot that involved the *dd* command and modifying the boot.ini file in Windows? Did you choose not to install Grub to the MBR?

---

### Post by panti19 on 2007-02-14
how do i check if i have Grub?

---

### Post by housam on 2007-02-14
> **panti19 said:**
> how do i check if i have Grub?

If you have not , you'll not be able to boot ubuntu.

---

### Post by to4i on 2007-02-14
Just use dual boot. That's what I'm using. May be later you can format Win partition.

---

