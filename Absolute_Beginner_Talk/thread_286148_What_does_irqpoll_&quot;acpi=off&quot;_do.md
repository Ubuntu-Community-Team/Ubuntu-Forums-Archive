---
title: "What does irqpoll &quot;acpi=off&quot; do?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by ronly on 2006-10-27
I installed edgy from scratch since I was previously running breezy because I never could get dapper to run no matter what I tried and when I still had some of the same problems with edgy as I had with dapper I tried the same solutions and this time with better luck - I got it installed and everything seems to work fine. I have, however, one question: I must boot with "irqpoll acpi=off" or otherwise it will hang and would like to know what those options do? How does it affect my system, if at all? And should I at some point try booting without those options, i.e. after upgrades to some packages and which, in that case?

---

### Post by John.Michael.Kane on 2006-10-27
"irqpoll" as command line parameter. This reduces driver 97 initialization failures in second kernel due to shared interrupts.

---

