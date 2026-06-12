---
title: "boots to black screen"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by maverick23r on 2007-01-31
So I decided to change from Fedora to Ubuntu and after wrestling with the installation I finally installed ubuntu 6.10 with the alternate CD. Everything seems fine (grub works and everything) until the Ubuntu splash screen and then it just goes blank. I have an ATI Radeon 9200SE video card and I think that its the problem but I can't figure out how to fix it. If I try to configure with  "sudo dpkg-reconfigure xserver-xorg" the ATI driver is not listed (just some generic Intel driver). Any help would be appreciated.

---

### Post by Brunellus on 2007-01-31
> **maverick23r said:**
> So I decided to change from Fedora to Ubuntu and after wrestling with the installation I finally installed ubuntu 6.10 with the alternate CD. Everything seems fine (grub works and everything) until the Ubuntu splash screen and then it just goes blank. I have an ATI Radeon 9200SE video card and I think that its the problem but I can't figure out how to fix it. If I try to configure with  "sudo dpkg-reconfigure xserver-xorg" the ATI driver is not listed (just some generic Intel driver). Any help would be appreciated.
choose 'vesa' first.  that should get you a minimal x session.  worry about the ATI driver later...

---

### Post by maverick23r on 2007-01-31
I'll try that but does it matter which input my monitor is plugged into (I have one for the video card that doesn't seem to work and one directly into the computer that I don't use).

---

### Post by Brunellus on 2007-01-31
> **maverick23r said:**
> I'll try that but does it matter which input my monitor is plugged into (I have one for the video card that doesn't seem to work and one directly into the computer that I don't use).
say again:  by "black screen" do you mean a text mode console or simply no screen at all?

---

### Post by maverick23r on 2007-01-31
it shows a black screen (monitor is turned on so not a 'blank' screen) with no cursor, no prompt, nothing. Everything before that shows up though (ie. splash screen)

---

### Post by maverick23r on 2007-02-01
so I figured out the solution and I though I'd post it. For whatever reason Ubuntu couldn't find a driver for my Radeon 9200 SE video card and could only detect the native card that came with my computer. All I had to do was read the output that came up when the xserver didn't work on boot and find out the PCI bus address of my Radeon card. Then I went and used 'sudo dpkg-reconfigure xserver-xorg' to change the driver company to "ATI", write in the driver as "fglrx" and then copy in the correct PCI address. After that it booted right up and everything seems fine. Anyways I hope this helps someone who had a similar problem to me.

---

