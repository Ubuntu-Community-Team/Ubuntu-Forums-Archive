---
title: "ASUS P8Z68-V LE freezing upon installation"
date: 2012-06-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Leyzr on 2012-06-14
Alright, I've been wanting to update to Ubuntu for quite a while and every time I've tried it freezes right after I selection the option from the boot screen.
The 5 options, try without installing, install ubuntu, ect...
Everyone freezes and hangs at a black screen after. My disk drive attempts to read it then basically gives up after a few seconds. I have burned it at the slowest speed, and tried 4 different disks and got the same results. I also tried using a friends second DVD-ROM drive and once again the same result.

Specs:
ASUS P8Z68-V LE
4GB DDR3 1600
i5-2500K
GeForce 460v2

I'm basically stumped and i have absolutely no clue what to do -.-

---

### Post by Smerpette on 2012-06-15
If Ubuntu is not booting up after the reboot on the install you should follow these commands. I had the same issue and this link[ http://askubuntu.com/questions/139121/grub-rescue-after-install-of-ubuntu-12-04-dual-boot]("http://askubuntu.com/questions/139121/grub-rescue-after-install-of-ubuntu-12-04-dual-boot")   I found to be very  helpful and useful. If you having a different issues maybe you could be more specific.

---

### Post by Leyzr on 2012-06-15
It is freezing right after hitting the install button. It doesn't go any further. I can't install it at all. I'll make a video later showing.

---

### Post by Leyzr on 2012-06-16
ok, so im unable to get a video, but can someone please help? right after the disk boot screen, i hit the install button to install, but after that just black screen. why? :( (bump)

---

### Post by Leyzr on 2012-06-19
[http://www.youtube.com/watch?v=hQaF89V_QcQ](http://www.youtube.com/watch?v=hQaF89V_QcQ)
That is the video i recorded to show. can i please get some help? I see a thread with over 100 pages, i could maybe get a productive reply?
i did set my bios to defaults and that didnt help either.

---

### Post by GeneralCody on 2012-08-29
I actually had the exact same problem with this Motherboard.
Haven't figured it out yet, I'm sorry.

I installed ArchLinux instead on this machine and somehow it worked out fine.
I also tried other distros on the same MB with same result. Black screen with a blinking bean upper left corner after selecting install from the DVD, USB, CD's I've tried...

Crazy basically.

---

### Post by GeneralCody on 2012-08-30
I've finally SOLVED this problem I had with installing Ubuntu on this hardware.
I really needed to install Ubuntu Studio 12, because the AUR packages for Archlinux I was using was kinda rotten and would not compile dbus-c++ which I needed to install FFADO for my FireWire soundcard. Anyway...

It was kinda embarrasing that I hadn't tried this before, but here it goes:

If you choose F6 i believe under install options when you boot the DVD/USB/CD whatever, you can check for NOAPIC, NOAHCI and NOMODESET or something like that. I just chose all starting with "NO" I think it was 3 options to disable, and it booted fine.
Guess this is a case of buggy BIOS or something.

Now I have Ubuntu Studio 12 running dandy on my monster machine.

Nice indeed.

---

