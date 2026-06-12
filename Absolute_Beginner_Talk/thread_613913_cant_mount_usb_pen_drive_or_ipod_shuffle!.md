---
title: "cant mount usb pen drive or ipod shuffle!"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by badgerboyx on 2007-11-15
Hi guys, just installed ubuntu gutsy and loving, loving loving it. One slight problem though, when I plug in my ipod shuffle the ipod icon does not appear on the desktop. Try loading up gtkpod also and no luck in mounting from there. How do I go about getting this to work? Also have a the same deal with my usb pendrive, no icon! Please help a neeewwb!

---

### Post by DrBeaverhausen on 2008-01-24
Ya, I'm having the same problem.  They both mounted on the live CD without problem.

---

### Post by Fleece Flamingo on 2008-01-24
try ```
sudo mount media/name of your ipod
```
or just remove the sudo from the command.

---

### Post by miqie on 2008-01-24
I've gotten my USB flashdrive to mount by:

```
sudo modprobe -r ehci_hcd
```

It still won't mount automatically, but this is better than nothing.

---

### Post by rod40cool on 2008-02-10
> **miqie said:**
> I've gotten my USB flashdrive to mount by:

```
sudo modprobe -r ehci_hcd
```

It still won't mount automatically, but this is better than nothing.

Thank you, thank you. 
I have been using Gutsy 386 version on my old PC without problems mounting my ipods but when I set up my new PC with Gutsy AMD64 version I couldn't mount my ipod colour photo, but strangely the shuffle would mount ok.

I have been searching through this forum and launchpad for an answer but nothing was working.

I was in the process of starting up a new post when one of the suggested posts took me here.

I just tried this code and BINGO my ipod colour is now mounted but syncing transfer rate is 12Mb/sec though.

I have been reading about problems with the 2.6.22-14 kernel and mounting some devices (ipods one of them), does anyone know if the problem has been confirmed?


Rod
Gutsy 64bit, GA-M61SME-S2 4200+ 1GB (Fresh install - no windows whatsoever)

---

