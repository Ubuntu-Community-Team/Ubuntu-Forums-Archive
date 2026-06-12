---
title: "Ubuntu will not boot"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by frogger-Lee on 2007-03-15
i have tried both ubuntu and xubuntu and niether will boot on my system.  i have another system that is currently running xubuntu the only problem i had was the graphics wich i got around and am very happy with it.  i would love to not have to use wintard on any of my pc's but what do i do. 

i have an asus A8NE-delux, Athalon 64 2.2 gig, 512 ram, EVGA with a 6600 GT gpu, 160 gig SATA hd two 40 gig part one for xp one for ubuntu 80 part for sharing files between.  

when i try to boot live cd it goes black and does nothing for safe graphics and normal both 32 and 64 bit.  i think it is a problem with the video so my next try will be with alternative install cd unless someone else has another idea.  :confused:

---

### Post by Kobalt on 2007-03-15
You can try to boot with then 'noapic nolapic' options : boot up normaly with the install CD in your drive ; when you reach the boot menu ("install/start Ubuntu, test CD, etc.") press F6 and simply add > noapic nolapic at the end of the line. Then press Enter...

---

### Post by frogger-Lee on 2007-03-15
i will try after work and get back if i get it working (hopefully from ubuntu).

---

### Post by rsambuca on 2007-03-15
You can also try adding 

ide=nodma

as a boot option.

---

### Post by frogger-Lee on 2007-03-15
i have already tried no dma it was unsuccessful but thank you for the help

---

### Post by Neobuntu on 2007-03-15
I don't know, sounds like vid card wierdness but you have the right brand, Nvidia.

Perhaps you should check the few known problems (release notes) booting that version of Live CD. 

Try the Kubuntu CD. It's best! tm 

Does the CD drive boot other stuff? Old CD drive? Slave/Master and/or cable issues?

What does a Knoppix CD say when booting that hardware? That will most likely tell you what it is.

---

### Post by frogger-Lee on 2007-03-15
ok gave no apic no lapic a try but niether worked am now posting from my xubuntu system

---

### Post by frogger-Lee on 2007-03-16
ok now i have a squashfs error what the heck is that

---

### Post by jhenager on 2007-03-16
[http://mozillaquest.com/Linux04/Asus_Sucks_Story-01.html](http://mozillaquest.com/Linux04/Asus_Sucks_Story-01.html)

I came across this article a few months ago. If you search on 'asus Linux' you will see many many articles complaining of problems with that brand under Linux.
 I am aware that Asus is preferred by some overclockers, but my first and only experience with one was pretty ugly. I gave up when I read the instructions on how to clear the BIOS. They didn't even have a jumper - you were supposed to short two solder joints with a screwdriver. It sparked. Not the best thing to see on a computer.
I would only accept one of their motherboards if it was in a sealed package - so I could sell it.

---

