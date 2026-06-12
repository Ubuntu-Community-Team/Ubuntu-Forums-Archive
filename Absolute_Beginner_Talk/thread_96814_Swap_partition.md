---
title: "Swap partition?"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by Yes_It's_Me on 2005-11-29
Hello, I am new to these great forums and linux and have just recently installed Ubuntu (RULZ!) on my poopy old laptop along with win xp pro (I know that it is deppressing that i have it but i need it for games and if something goes wrong) anyhoo, i am getting a new comp just after christmas and wondering how big i should make the swap space (i will have an amd 3700+ with 2gig ram and 200g hdd and sapphire 256mb x800gto).

PS. what is a swap space?

Thank you for your help.

---

### Post by linbetwin on 2005-11-29
A swap partition is a portion of the hard disk that your computer uses as virtual memory when it runs out of "real" memory (RAM) With 2 GB of RAM I don't think you need to worry about swap. Let Ubuntu partition your hdd automatically and it will determine the swap partition size.

---

### Post by Yes_It's_Me on 2005-11-29
ah, thankyou

---

### Post by erikpiper on 2005-11-29
I think you should at least make a small swap- I have a IBM T23 with 756 MB Ram- I had a bit of swap usage with a 80% ram use. Weird. I have a 150 MB swap- mabe you should make a 100MB. No real reson not to. Especially with a 200 Gig HD!

---

### Post by LuxoDave on 2005-11-29
I have a system with 2 gigs of RAM as well. During the install I trusted Ubuntu to choose the size of the swap partition. My swap is 118 MB. I have not had any trouble, although it has only been about 3 weeks and I am still learning.

---

### Post by Yes_It's_Me on 2005-11-29
Ok, cool, i guess i can just trust ubuntu to do the dirty work for me.

---

### Post by Qrk on 2005-11-29
I think the rule of thumb is swap should be twice your ram. But if you have a ton of ram it becomes less needed.

---

### Post by detyabozhye on 2005-11-30
[QUOTE=Qrk]I think the rule of thumb is swap should be twice your ram. But if you have a ton of ram it becomes less needed.[/QUOTE]
Yes, that way your computer runs somewhat faster, I did that on Linux and on Windoze, but if you have 2 GB, you can make the swap same size as you RAM too, it should work as good as 2x your RAM.

---

### Post by az on 2005-11-30
If you have a tiny hard drive, the installer will not create as big a swap.  Your swap needs to be bigger than your ram by about 25 per cent for hibernation (suspend-to-disk) to work.  

When you go into hibernation, the contents of your ram get written to the swap partition.

If you do not use hibernation, then it does not matter.  I hibernate on a desktop machine and it boots in about 25 seconds.

---

