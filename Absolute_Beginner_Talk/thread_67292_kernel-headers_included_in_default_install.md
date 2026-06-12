---
title: "kernel-headers included in default install?"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by ryneezy on 2005-09-19
Hi,

I'm a long time Debian user going to make the switch to Ubuntu.

I have some pretty old hardware so I know most of my stuff should be supported, but I'm concerned about my wireless card. Since most Linux distributions do not support wireless cards, I'm assuming Ubuntu does not either.

This is not a problem because I can compile the driver from source. My only concern is if the Ubuntu default install includes the kernel-headers. My only form of internet connection is wireless so I will not be able to use apt-get to get the headers through ethernet.

Please let me know if they are included or if there is another way to get them.

Thanks a lot,
Ryan

---

### Post by mlomker on 2005-09-19
I guess you'll have to download them through packages.ubuntu.com using another machine and burn it to a CD or something.  Flash Drive, maybe?

---

### Post by ddemers on 2005-09-19
Its possible that it will support your card, try the Preview and fine out.  It supports both my cards.

---

### Post by ryneezy on 2005-09-19
Ok. Cool. I didn't know Ubuntu included wireless drivers. Hopefully it supports mine (Linksys WMP54G).

If not I'll get the kernel-headers and put them on a USB drive.

Thanks a lot for the quick replies,
Ry

---

### Post by mlomker on 2005-09-20
>  (Linksys WMP54G).


Most of the Linksys cards use the madwifi/Atheros driver and that's included.

---

### Post by ryneezy on 2005-09-20
[QUOTE=mlomker]Most of the Linksys cards use the madwifi/Atheros driver and that's included.[/QUOTE]

It didn't detect my card on setup. My card uses the RaLink RT2500 chipset.

I found a better solution than compiling the drivers from source, however. I was originally going to compile the driver either through the ndiswrapper project or official Linux drivers from RaLink, but I found an ndiswrapper debian package for Ubuntu.

I simply installed the package and it worked.

Now that I have everything working and updated, I'll admit that I'm very impressed with Ubuntu. It really lives up to what everyone is saying.

---

