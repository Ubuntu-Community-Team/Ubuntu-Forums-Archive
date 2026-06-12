---
title: "sata 150 and sata 300 compatibility"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by saltyscott on 2006-12-27
i just got a sata 300 hard drive for christmas, and i know for sure my motherboard is a sata 150. is there any way to use my new hard drive on my motherboard? i am asking because i have heard that it works but i just cant figure it out. if i can use it, is there anything special i need to have for it (like an f6 floppy with xp)?

---

### Post by pseudonym on 2006-12-27
> **saltyscott said:**
> i just got a sata 300 hard drive for christmas, and i know for sure my motherboard is a sata 150. is there any way to use my new hard drive on my motherboard? 
shouldn't be a problem, becuase the spec is supposed to be backwards compatible. I had a sata150 board and used sata300 drives on it without any issues. what i had to do was add a jumper to the drive so it only operated at sata150 speed (realistically, though, there's little difference, because '150' and '300' are just theoretical limits). I found that out by reading the documentation fro both the drive and the motherboard. This is also good advice for you ;)
> **saltyscott said:**
> if i can use it, is there anything special i need to have for it (like an f6 floppy with xp)?
for windows, most probably yes. you would need to go to your moterboard manufacturer's website and download a floppy image with driver file (or just the file). It's probably also on the board's support CD.

For Linux, though, you just plug your drive in and go ahead and install the OS, because the kernel will detect what drive you have.

HTH

---

### Post by umattu on 2006-12-27
The drive will work without having to install anything if ur using XP. The SATA 3G drive will only run at 150 because thats as fast as your board will allow it to go. But it will work just fine just by plugging it in, SATA drives are plug and play as well as hot swappable. This is the same as if you had a mobo that only supportted pata 100 and you installed a pata 133 it works just fine it just runs slower.

---

### Post by pseudonym on 2006-12-27
> **umattu said:**
> The drive will work without having to install anything if ur using XP. 
I think the OP meant the floppy you need at install time. Unless you have a *very* recent copy of XP, it's unlikely the xp installer will recognize the SATA controller. Hence the need for the driver floppy.

---

