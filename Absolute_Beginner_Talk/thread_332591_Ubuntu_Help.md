---
title: "Ubuntu Help"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by CorranSW on 2007-01-06
Hi i am new to the linux community, and most of the linux OS's i have tried i virtual machined, the one i am currently using is fedora core 6, but to be honest i only jumped into linux to work my way up to trying open gl ubuntu, so installing fedora core 6 on parrallels was a breeze. Fortunately i got a magazine with all the OS cd's inside, as for ubuntu i downloaded it off of this website, and wrote it onto a cd, but when i tried to boot it off of my new VM i made it didnt read it. I am guessing this is because i didnt use that infra thing. i downloaded it but i dont know how to install it, i looked around the folder i unzipped and it didnt have one of those easy installation things.. Can somone please help me on my quest to reach open gl linux???? :-k

---

### Post by geekygreen on 2007-01-06
When you wrote it to the CD, did you write the file directly to the CD, or did you use the option to create an ISO disk?

Generally the file is saved as an image in ISO format, and if you burn it onto a standard CD, it puts in inside another files-system "Envelope", so the system will not see it as a bootable CD.

If you save it/write it as an ISO, it doesnt repackage it, but burns the image directly on to the CD, which makes it bootable.

---

### Post by CorranSW on 2007-01-06
yeah thats the problem i cant use the infra recorder thing to burn a ISO image.. I cant install it i dont see were to i downloaded it and eveything but i dont see a setup thing or anything were i can install it.

---

### Post by PilotJLR on 2007-01-06
I have never used Parallel, but I know hardware acceleration will not work under VMware. If the same is true for parallel, which it probably is, then you can't use the fancy eye candy like XGL inside a VM...

---

