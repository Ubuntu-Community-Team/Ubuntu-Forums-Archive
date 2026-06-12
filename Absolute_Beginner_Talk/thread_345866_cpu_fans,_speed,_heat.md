---
title: "cpu fans, speed, heat"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by jmrichky on 2007-01-24
First of all I am running 64-bit Edgy with kernel 2.6.19.2 and I have gotten everything working (wireless, 3d, flash, etc..).  I do notice that my laptop is not nearly as loud as it once was.  How can I verify that my fans are quiet because they don't need to be running fast or that there is a problem with fan control?  How can I see the temperature of my processor?  Also, my processor is clocked @ 1ghz in cpuinfo.  Does this have to do with cool n quiet?  How can I be sure that my processor is detected with its proper capabilities (AMD64 Athlon 3200+)?

---

### Post by Pathos_ on 2007-01-25
Your processor will be running below its max speed due to automatic processor scaling to reduce heat and increase battery life. It will go full speed when necessary. It is probably is using Cool and Quiet technology to do this.

lm-sensors is responsible for getting chipset monitoring information. Try right clicking on a panel Add to Panel->Hardware Sensors Panel.

also research other peoples experience with your model of laptop to see how they fared.

---

### Post by housam on 2007-01-25
Type this code to see your cpu infos
```
cat /proc/cpuinfo
```
Also right clicking on the top bar of the screen, then clicking on the Add to Panel..., and then scrolling down to find the cpu monitor ..., which will give you an instance % of the cpu capasity.

---

