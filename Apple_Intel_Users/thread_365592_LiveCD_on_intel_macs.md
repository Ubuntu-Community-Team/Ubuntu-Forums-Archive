---
title: "LiveCD on intel macs?"
date: 2007-02-19
forum: Apple Intel Users
---

### Post by Tadpole on 2007-02-19
I see that people have managed to get K/Ubuntu dual-booting on intel macs, but what about the LiveCDs? Would the i386 LiveCDs work properly on my mac mini core solo?

Thanks.

---

### Post by Tadpole on 2007-02-19
Oh, I just found a thread where someone says that this is possible:

> **handylinux said:**
> For your MacBook you need the CD for the Intel processor -- the same CD I believe you would use for any x86 PC.

---

### Post by Tadpole on 2007-02-20
Okay I successfully ran Kubuntu on my mac mini via a LiveCD. However, I can't connect to my WPA-encrypted wireless, even though the "wpasupplicant" is installed. It is able to *detect* my router, though, so I don't think it's a hardware driver issue. If anyone has tips, please let me know.

Thanks!

---

### Post by Gen2ly on 2007-02-21
if its a new mac mini it uses anew airport which isn't supported yet.  you'll need to use an NDIS wrapper.

[https://help.ubuntu.com/community/MacBook?highlight=%28macbook%29](https://help.ubuntu.com/community/MacBook?highlight=%28macbook%29)
[http://wiki.debian.org/MacBook](http://wiki.debian.org/MacBook)

---

### Post by Tadpole on 2007-02-22
> **Dirk.R.Gently said:**
> if its a new mac mini it uses anew airport which isn't supported yet.  you'll need to use an NDIS wrapper.

[https://help.ubuntu.com/community/MacBook?highlight=%28macbook%29](https://help.ubuntu.com/community/MacBook?highlight=%28macbook%29)
[http://wiki.debian.org/MacBook](http://wiki.debian.org/MacBook)

By "new," do you mean any intel mac mini? I got mine in March of last year, right when the intel mac mini was first announced, so it's almost a year old.

---

### Post by Tadpole on 2007-02-22
I just downloaded Ubuntu Edgy Eft and my WPA2 wireless doesn't work with that either. Is there something special I have to do to get it to work?

---

### Post by Gen2ly on 2007-02-24
> **Tadpole said:**
> I just downloaded Ubuntu Edgy Eft and my WPA2 wireless doesn't work with that either. Is there something special I have to do to get it to work?

Thats Strange.  If your Mac was rolled off the line in March you should have no problem with the wireless.  I'm assuming you're using your airport?  Is WPA2 your router?  You'll need to be more specific.

---

### Post by cbrain on 2007-02-24
I believe WPA2 is a type of network encryption, like WEP.

---

### Post by dominik.margraf on 2007-02-24
Have you tried the Feisty LiveCD (Herd-4 onwards)?  It is the first Ubuntu release which has automated GUI support for WPA2 and detection / choosing of wireless network.

---

