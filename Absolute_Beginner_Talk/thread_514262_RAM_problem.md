---
title: "RAM problem"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-07-31
I bought a 256mb ram card for my older laptop running xubuntu.  I'm only getting 192mb of RAM.  Below is the terminal screenshot.  Can someone interpret this for me?  Does this mean that there is something wrong with the RAM?  If not, what does it indicate as the reason why I would only be getting 192mb?  Thanks.

---

### Post by Warren Watts on 2007-07-31
Depending on how old the laptop is, it may not support memory with densities above 128MB...

---

### Post by sagesparrow on 2007-07-31
I"m not sure what that means.   Why would I get 192mb?  The specs for the computer (Compaq 1800T) say it can support up to 320mb RAM.

---

### Post by Warren Watts on 2007-07-31
The Laptop has 64 MB internal, right?

If the computer is only recognizing 128 of the 256 you put in, that would be 192.

Does the computer have two slots for additional memory or one?

If it has two, then if you put 128MB in each one, that would be 64(Internal)128+128(external)=320

---

### Post by sagesparrow on 2007-07-31
If I use the system monitor, with the original 128mb RAM I see that it is using a few megs under 128.  If I do the same with the new 256mb RAM, then I see just under 192mb.  Obviously the 64mb of internal memory are not included in that.

Regarding the screenshot, I see that the first RAM of 64mb is the internal RAM as that is listed with both the 128 and 256 RAM.  The 128 RAM screenshot shows dble sided 64mb and the 256mb show dbl sided 128mb as seen in the sceenshot on the early message.

So the question remains, why I would only be able to use 192mb out of a 256mb card?

---

### Post by wpshooter on 2007-07-31
I think Warren is saying the the 2 additional on board slots on your machine will only except 128 ram modules and not anything above that.  And I agree.

Send the 256 module back and get two 128mb modules.

---

### Post by raijinsetsu on 2007-07-31
Like above, I agree that your system appears to only support 128mb chips and below. The proof: if the specs state it supports 320mb, that would be 128mb + 128mb + 64mb, not 258mb + 256mb + 64mb.
My suggestion: if it's that old, plunk $300 on a low-end laptop/desktop to replace it. It's probably cheaper than buying new obselete ram.

---

### Post by sagesparrow on 2007-07-31
there's only one slot for RAM.

---

### Post by sagesparrow on 2007-07-31
i originally had a 128 card in the one slot and the system monitor indicated that i was using 128.  when i installed the 256mb card, the system monitor said i was using 192mb.  i don't believe that the computer is limited to only 192mb.

---

### Post by wpshooter on 2007-08-01
> **raijinsetsu said:**
> Like above, I agree that your system appears to only support 128mb chips and below. The proof: if the specs state it supports 320mb, that would be 128mb + 128mb + 64mb, not 258mb + 256mb + 64mb.
My suggestion: if it's that old, plunk $300 on a low-end laptop/desktop to replace it. It's probably cheaper than buying new obselete ram.

I agree, you will probably spend more in money and time than you would by just buy a good e-machine or similar.

Good luck.

---

### Post by thefoolisme on 2007-08-01
My sister's old Compaq laptop came with 256 MB installed.  However, it sucked up 64MB for the internal video.  I don't know whether that's your issue or not, but it might be.

---

### Post by Paulmd on 2007-08-01
> **Warren Watts said:**
> Depending on how old the laptop is, it may not support memory with densities above 128MB...

Classic high density issue.

If you get a 256mb module with more chips on it, it may work. Also, make sure you have the latest BIOS from Compaq. I've seen one other laptop with that exact issue, that was cured with a bios update. FWIW, it was also a compaq.

---

### Post by Paulmd on 2007-08-01
> **wpshooter said:**
> I agree, you will probably spend more in money and time than you would by just buy a good e-machine or similar.

Good luck.

There is no such thing as a good e-machine. They work right up until the power supply goes and takes out the motherboard with it.

---

### Post by arochester on 2007-08-01
I have found this problem too in a desktop. It could be the difference between high density ram and low density ram. High density ram is cheaper but in some machines it will only be half the shown value. High density 256 could show as 128.

---

### Post by wpshooter on 2007-08-01
> **Paulmd said:**
> There is no such thing as a good e-machine. They work right up until the power supply goes and takes out the motherboard with it.

Probably more a problem of people running the machine without good surge protection and/or UPS.

---

### Post by Paulmd on 2007-08-01
> **wpshooter said:**
> Probably more a problem of people running the machine without good surge protection and/or UPS.

Not for that machine. I've seen it. Usually what happens is the power supply goes. On most machines, it ends there, but with emachines, it takes out the motherboard too.  if you REALLY must get an emachine, first thing to do is to void the warranty and install a good quality PSU, instead of the el-cheapo Bestec one that's in there. Then the machine stands a chance of living 5 years. Else they're dead in under 3.  Most other machines physically survive beyond a decade.

---

