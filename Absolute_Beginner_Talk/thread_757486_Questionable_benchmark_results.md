---
title: "Questionable benchmark results"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by luceerose on 2008-04-17
I just ran a quick Whetstone/Dhrystone benchmark from BOINC and I'm a little concerned about the results.

PC 1) AMD 2.2Ghz Dual Core, Ubuntu Hardy 64-bit, Kernel 2.6.24-16 (generic)
Results:
Number of CPUs: 2
928 floating point MIPS (Whetstone) per CPU
2718 integer MIPS (Dhrystone) per CPU

PC 2) AMD Sempron 1.6Ghz [overclocked to 1.87Ghz], XP Pro SP2 32-bit
Results:
Number of CPUs: 1
1876 floating point MIPS (Whetstone) per CPU
3269 integer MIPS (Dhrystone) per CPU

PC1 is my pride & joy and I am concerned as to why the obviously inferior PC2 is getting better benchmarks than my Ubuntu PC1.

Can anyone explain this ?
Should I be running an optimized kernel or something ?

---

### Post by talsemgeest on 2008-04-17
It is probably the result for a single core in PC 1 so multiply your results by two to get a more accurate result.

Hope this helps :)

---

### Post by luceerose on 2008-04-17
Guess I wasn't thinking too carefully about the internal cpu architecture I was trying to compare one single core from the X2 against the sempron.

The result from both cores of the X2 combined is:
1856 Whet
5436 Dhry

That's probably a half decent Dhrystone, but the Whet still falls short of the Semprons result of
1876

Is that normal for an overclocked 1.6G Sempron to whetstone better than a 2.2Ghz X2 ?

---

### Post by talsemgeest on 2008-04-17
I am really not sure. When I benchmark I don't use numbers, I use performance. Maybe the time to rip a DVD with the same program?

---

