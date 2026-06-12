---
title: "Quad core proccesor cores slower then should be."
date: 2012-06-14
forum: Any Other OS
---

### Post by Phil The Newb on 2012-06-14
Hello, i'm using Linux Mint 13 and I think i've messed something up but i'm not sure. I have an amd athlon II quad core 3.0 Ghz processor and it's only showing one core as 3000 mhz right now and the others keep changing from 800 mhz to 3000 and under. at one point they were all 800 mhz. here's what I think I did wrong: during the computers boot on the BIOs screen (when it shows the american megatrends sign or whatever it was) it said something about pressing f3 and f4 to unlock the third and fourth cores and I stupidly pressed both of them without knowing what would happen. Now i'm not sure if this is what messed it up but if anyone can help me figure out this problem (or at least explain why it's changing speeds like this)I would be VERY, very grateful. I'm not sure if this would help but my motherboard is a BIOSTAR A780L3L. thanks in advance,  Phil The Newb.  [edit] this is what it shows right now in the system information under proccesors. -Processors- AMD Athlon(tm) II X4 640 Processor		: 800.00MHz AMD Athlon(tm) II X4 640 Processor		: 800.00MHz AMD Athlon(tm) II X4 640 Processor		: 3000.00MHz AMD Athlon(tm) II X4 640 Processor		: 800.00MHz

---

### Post by Phil The Newb on 2012-06-14
for some reason it's not letting me put spaces between my paragraphs, i'm sorry for the jumbled mess...

---

### Post by Perfect Storm on 2012-06-15
Moved to Other OS/Distro Talk.

---

### Post by QIII on 2012-06-15
That is normal behavior.  The core speed is throttled when there is no load (800MHz is common with AMD processors) and increased to match load up to the nominal design frequency of 3.0GHz.

Each core may be under different loads at different times, so any moment you check you might find the cores running at different speeds.

You have done nothing wrong and there is nothing to worry about.  Your processor is behaving as intended.

---

### Post by joe4ska on 2012-06-15
You can test this by opening several applications. running a youtube video palying music playing a DVD or otherwise watching video. I'm using an Intel i5 processor and it drops down to half speed to save energy when there is no demand for the extra resources.

You can also install jupiterapplet [http://www.jupiterapplet.org/]("http://www.jupiterapplet.org/")

reboot or logout and run it to set the performance manually to the highest setting and it should stay there. However, as stated above it's normal to save resources under lighter loads. It keeps temperatures down and saves power.

---

### Post by Dlambert on 2012-06-15
If all cores ran at 3000MHz say hello to your energy bill!

---

