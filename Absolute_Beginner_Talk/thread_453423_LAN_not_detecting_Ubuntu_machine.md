---
title: "LAN not detecting Ubuntu machine"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by rdomanski on 2007-05-24
Hi there.  I have a LAN set up in my apartment with 1 Windows desktop, 1 Windows laptop, and my Ubuntu 7.04 machine wired via an ethernet cable to a Belkin router.  On my Ubuntu machine I can see the other devices and access files on them, etc.  The router also seems to be working ok since the internet connection is being successfully shared on all devices.

So why can't any of the Windows machines detect the Ubuntu machine?  Any advice?

Thanks.

---

### Post by scrooge_74 on 2007-05-24
you need to have the SAMBA server running on your ubuntu PC, you will have to configure it in order to correctly work.  Remember windows doesnt like to play nice with other kids.

---

### Post by rdomanski on 2007-05-24
Is the SAMBA server already installed (along with the basic Ubuntu 7.04 installation), and I just need to activate it, or do I need to download it separately?

And how would I do such a thing (whether it's activating or downloading it)?

---

### Post by onbongos on 2007-05-24
samba is a nightmare, avoid at all costs. use ftp or even im if you only need to transfer files

---

### Post by wpshooter on 2007-05-24
If it works on Feisty like it does on other version, then you just click on folder sharing on the system/admin menu and it will prompt you for the installation of SAMBA.

Might have to restart your Ubuntu machine before it works correctly.

Good luck.

---

### Post by Ozeuss on 2007-05-24
i've just installed samba two days ago. wasn't difficult to set up and worked fine.
lookup howto's on this forum. there's also a wiki page in help.ubuntu.com.

---

### Post by wpshooter on 2007-05-24
> **onbongos said:**
> samba is a nightmare, avoid at all costs. use ftp or even im if you only need to transfer files

Samba works just fine for me.

---

### Post by rdomanski on 2007-05-24
thanks to all your input, i'm going to give SAMBA a shot.  what special configuration info was scrooge_74 referring to?

---

