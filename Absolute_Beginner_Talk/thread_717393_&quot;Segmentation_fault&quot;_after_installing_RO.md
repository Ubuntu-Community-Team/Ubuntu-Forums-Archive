---
title: "&quot;Segmentation fault&quot; after installing ROM"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Julita on 2008-03-07
Hello everyone! My ROM is just 192 MB SDRAM (PC133), and I have installed additional 128 MB of this type. When I turned on my PC, BIOS recognized memory (320 MB), but, since I do not have splash image, I could see that the system hangs at preparing restricted drivers, and then comes many lines with "segmentation fault," and nothing happens. I have tried to use several Linux CDs to boot from, but the result was the same. When I tried to go into Acronis Disk Director Suite, I found out that my mouse is not working (I have tried both - USB and "usual"), but the keyboard worked fine. Now I have removed ROM that I have installed, and everything boots well. Can someone suggest what can I do? Maybe I have to change something in my BIOS?

---

### Post by amingv on 2008-03-07
You might like to check that memory module. (The liveCD has a tool to do that, in the boot menu). Make sure it is firmly inserted into its slot.

Also, I believe you're refering to "RAM"; not "ROM", they're quite different.

---

### Post by Julita on 2008-03-07
Thank you very much! RAM, of course. How can it be that BIOS recognizes correctly the memory if there is something wrong with it?

---

### Post by amingv on 2008-03-07
> **Julita said:**
> Thank you very much! RAM, of course. How can it be that BIOS recognizes correctly the memory if there is something wrong with it?

The BIOS just accounts for the memory you have available and checks that it's all there and that it is completely empty, then places some data needed to boot; but it does not check it for defects (if it did this every time, you'd grow a beard by the time it's done booting.). The memory test tool in the liveCD (for example) writes to and reads from every block of the memory to make sure it's usable.

---

### Post by Julita on 2008-03-07
I have done the memory test.  There were many errors... I have not even finished the test... However, is it possible that the problem is in the slot? I got this computer from other people, and from three available slots there were used two. Those people know computers quite well and they can afford to buy another RAM. I mean, why they have left the slot empty?... Maybe because it is unusable?...

---

### Post by mcduck on 2008-03-07
> **Julita said:**
> I have done the memory test.  There were many errors... I have not even finished the test... However, is it possible that the problem is in the slot? I got this computer from other people, and from three available slots there were used two. Those people know computers quite well and they can afford to buy another RAM. I mean, why they have left the slot empty?... Maybe because it is unusable?...

Try it on a different slot, then. Move one of the old RAM sticks to the free slot and run memtest again to see if the slot is fine. Or replace one of the old sticks with the new one and test if it works.

I'd say it's most likely that the RAM stick is faulty, 

Anyway, memory test should always be run for long time, at least overnight. And even a single error means that there is something wrong.. (well, of course when you get the first error there's no need to run the test any longer)

---

### Post by Julita on 2008-03-08
Thank you very much guys! I shall try another stick; if something goes wrong, I shall think further on ))

---

