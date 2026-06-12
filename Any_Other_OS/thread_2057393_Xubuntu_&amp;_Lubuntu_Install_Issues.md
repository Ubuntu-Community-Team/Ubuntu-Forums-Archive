---
title: "Xubuntu &amp; Lubuntu Install Issues"
date: 2012-09-13
forum: Any Other OS
---

### Post by robn30 on 2012-09-13
I have an old PC with a AMD Athalon 2500+ on a ECS L7VTA MB.  I am using an ATI 9600 AGP video card for output to my LCD.  I spent all day yesterday trying to get either one of the above mentioned distributions to install or run.  Each would begin the process of booting into the OS at the Splash Screen and then my monitor would go black and never return.  After 30 seconds or so the monitor would actually go to sleep.  What could be causing this to happen.  I loaded Xubuntu on a machine with a Asus MB, 2800+ AMD Athalon, and the same video card just the day before. Also I was able to install Windows XP Pro without any problems on the 2500+ machine.  I have tried using a USB with Unetbootin and from live CD and both have the same results.  What could be the matter, I am lost? BTW I am trying to install the 32 bit versions of each of these.

---

### Post by robn30 on 2012-09-13
Now I just tried Linux Mint and this time it gives me a black screen with my mouse cursor visable and movable but it will not progress past that point.  This attempt is through USB with Unetbootin. This is odd.

---

### Post by mips on 2012-09-13
try this [http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso](http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso)

---

### Post by robn30 on 2012-09-13
> **mips said:**
> try this [http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso](http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso)

Using Lubuntu with this method of choosing nomodeset just gives me a black screen with mouse but no other display. Also I was able to get Linux Mint to give me a display under Compatibility Mode but when the installer gets to the installing system part the installer closes and seems to fail.  All I am left with is the mouse indicator showing that it is doing something but it just sits there forever.  This is crazy since I just installed Xubuntu on that other machine.  Of course the MB was different but I used the same ATI 9600 Pro video card and it worked perfect.  Like I said Win XP installed without fail and is still installed on a different partition and boots fine.

---

### Post by robn30 on 2012-09-16
I appears to have been MB/Video Card Specific.  I never got it to work in the one machine.  I put the HDD in the other machine with the video card and everything went smoothly, I got Xubuntu loaded using the Athalon 2800+ & Asus MB. I then put the drive and video card back in the other machine, with Xubuntu loaded, and bam the same thing. Got to the Xubuntu Splash screen and then the screen goes black and the monitor eventually puts itself to sleep after 30 seconds or so with no video signal.  Again it was an ECS L7VTA MB with the latest BIOS, Athalon 2500+ CPU, and Radeon 9600 Pro Video Card that caused the issues attempting to load any Linux Distro.  Mint made it the furthest but the install crashed shortly after it said installing the system. BTW that was using compatibility mode in Mint, it would not show anything but a black screen with mouse cursor attempting anything else. I guess this hardware is just not usable with Linux?

---

### Post by mips on 2012-09-17
You could always try a non-ubuntu based distro and see if that helps. Maybe try crunchbang & archbang.

---

### Post by black veils on 2012-09-19
it shouldnt be the cause, but what is your ram ?  you could try **lubuntu **or** bodhi** linux instead, they based on ubuntu, so you can have the same apps, but those systems might have better driver support for the old hardware. or try something else, aimed at being minimal/light/for older computers.

---

### Post by robn30 on 2012-09-19
> **black veils said:**
> it shouldnt be the cause, but what is your ram ?  you could try **lubuntu **or** bodhi** linux instead, they based on ubuntu, so you can have the same apps, but those systems might have better driver support for the old hardware. or try something else, aimed at being minimal/light/for older computers.

I did try Lubuntu and it gave me a black screen with cursor present and never progressed past that.  Mint got the furthest but only in compatibility mode. I have 1 Gig of ram but that should be enough.  That is what is in the other machine that it loaded perfectly on. I think it has something to do with the MB and it VIA chipset or something.  I don't know, its the first setup I have had any trouble with Linux (Ubuntu flavor) loading.

---

