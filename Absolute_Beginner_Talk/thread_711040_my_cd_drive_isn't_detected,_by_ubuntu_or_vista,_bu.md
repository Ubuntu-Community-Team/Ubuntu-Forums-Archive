---
title: "my cd drive isn't detected, by ubuntu or vista, but I can boot from it."
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by barbedsaber on 2008-02-29
I have a cd/dvd reader burner, on my computer which has vista on the hard drive it somewhere. I installed ubuntu on it a while ago, and then decided that I could speed up my boot by putting the cd to the bottom of the boot order, and then when I finnaly wanted to listen to a cd, It didn't detect, or do anything, so I tried using vista, and got nothing. I then went to my bios, and set all settings to defaults, and dugg up and ancient ubuntu 6.06 cd, and booted with that in the drive, and it booted.

I would normally think that if both os's didn't detect it that it was a hardware issue, but it booted from it, soo i dont know what to do.

I would really appreciate it if somone could get my cd drive working, without me having to buy an extarnel drive.
thanks in advance, barbedsaber.

---

### Post by krsk on 2008-02-29
I assume you installed ubuntu in dual-boot mode, so
you know your way around BIOS.
the CD/DVD drive should show up in the BIOS
list of drives on your machine.

If not, then it is very possible that the OS
(Vista and ubuntu) don't recognize the drive.

One thing puzzles me though: you mentioned putting
the CD drive at the bottom of the boot order.
But BIOS apparently boots from a (Ubuntu-)CD
prior to the hard disk drive.

Are you sure you gave the CD-drive the lowest boot priority?

---

### Post by barbedsaber on 2008-02-29
I set it to the lowest priority, and then set it back when I was tryin to figure out why it wasn't working. 

I wouldn't say that I know mmy way around a bios either,  I just know a bit.

---

### Post by krsk on 2008-02-29
Is the CD drive detected if you run Ubuntu from the Live-CD?
The live distro should mount all drives automatically.

---

### Post by muzosa on 2008-06-11
I have the same problem. My cd drive worked fine until I upgraded it to 8.04. Now my CD works fine during boot-up, but once Ubuntu loads, the drive won't even open.

At first I thought it was a power problem, but since it opens fine during boot-up, that's not it. And my machine isn't dual boot, if that matters. And the drive worked fine in Gutsy.

---

