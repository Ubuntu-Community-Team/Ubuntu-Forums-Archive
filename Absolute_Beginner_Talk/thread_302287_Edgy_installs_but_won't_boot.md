---
title: "Edgy installs but won't boot"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by stoiss on 2006-11-18
Hi,

I have been trying to install Ubuntu 6.10 (Edgy) for a couple of days now.

The install itself completes without errors. Once I try to restart the system to boot Ubuntu it just enters an endless restart cycle. Grub tells me it's about to boot up on hda0,0 and then the system restarts.

I read somewhere that the partition tool in the installer doesn't always handle already partitioned hard drives well so I went in an created my partitions manually on my 60GB hard drive (50MB on "/boot", 58.5GB on "/" and 1.5GB as swap).

It still enters an endless restart cycle.

I have had Ubuntu 5.10 (Breezy) installed on the system earlier and it installed and booted without a hitch.

What changed in the way Ubuntu is installed and booted between 5.10 and 6.10 and how can I fix it?

/stoiss

---

### Post by K.Mandla on 2006-11-18
Can you tell us more about your computer? The only time I've ever seen behavior like that was when I had installed the wrong kernel for the processor I was using. I doubt that's your problem though, if you're still on your initial boot. Let us know what kind of hardware you're using, and no doubt someone will have an idea for you.

---

### Post by stoiss on 2006-11-18
It's a VIA Epia VE5000 motherboard and the iso I downloaded, burned and installed is "ubuntu-6.10-server-i386.iso".

---

### Post by stoiss on 2006-11-18
The main menu in Grub looks like this:

```
Ubuntu, kernel 2.6.17-10-server
Ubuntu, kernel 2.6.17-10-server (recovery mode)
Ubuntu, memtest86+
```

If I choose to edit the first option I get:

```
root (hd0,0)
kernel /vmlinuz-2.6.17-10-server root=/dev/hda5 ro quiet splash
initrd /initrd.img-2.6.17-10-server
quiet
savedefault
boot
```

---

### Post by stoiss on 2006-11-18
I just find it very odd that "Breezy" installs (server option) and boots fine while "Edgy" that seems to have an almost identical installation procedure, fails to boot.

Someone must have an idea of what could be wrong - what changed? :confused:

---

### Post by stoiss on 2006-11-18
I have done a bit more research on the subject.

This thread [Kubuntu 6.10rc Installation - "No root filesystem"](http://ubuntuforums.org/showthread.php?t=282898) describes symptoms similar to the ones I have seen.

The install and boot of Ubuntu works now. All I had to do was download and install the "alternative" version of Edge and configure it the same way I did the server version.

Before that I tried both the server version of Edgy and Dapper Drake. Both failed. I don't understand the difference between the normal and the alternative version, but it works now. :-D

---

