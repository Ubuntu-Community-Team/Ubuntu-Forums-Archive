---
title: "Booting with 'noapic' option....what does it do?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by esayex on 2006-08-03
Ok, my Gateway laptop  (With AMD Turion 64 processor) was getting the error that the APIC timer wasn't connected (MP-BIOS bug I believe) That was easily fixed by using the 'noapic' option. 

however, I was wondering...what does 'noapic' do? Or alternatively, what **does** APIC do that I'm missing out on?

---

### Post by T700 on 2006-08-03
> **esayex said:**
> Ok, my Gateway laptop  (With AMD Turion 64 processor) was getting the error that the APIC timer wasn't connected (MP-BIOS bug I believe) That was easily fixed by using the 'noapic' option. 

however, I was wondering...what does 'noapic' do? Or alternatively, what **does** APIC do that I'm missing out on?

APIC stands for **A**dvanced **P**rogrammable **I**nterrupt **C**ontroller.  It was a chip designed to use the timing circut from the computer's silicon quartz clock to coordinate multiple (up to 60, as I recall) processors.  It never worked very well and many modern computers don't implement it, so it is not generally accessed by default in Linux.

All that to say, you're not missing much!

Paul

---

