---
title: "iMac G3 Breezy SDRAM detection"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by jtxdriggers on 2006-06-07
I recently bought a 512mb PC100 168-pin SDRAM DIMM for my old G3 iMac because I was sick of only having 64mb to try and run Apache on (my research concluded that G3 iMacs could support up to 1 gig of ram). I installed the chip in the 1st port, but when I boot into Ubuntu, it doesn't seem to detect it. Everything runs at the same speed as before. When I run lshw, it shows that it does detect the chip, but all the information it gives (with the 512mb in the first slot) is:

*-memory
     description: System memory
     physical id: 1
     size: 64MB
  *-bank:0
          description: Memory bank
          product: SDRAM PC100-222S
          physical id: 0
          slot: DIMM0/J13
  *-bank:1
          description: Memory bank
          product: SDRAM PC100-322S
          physical id:1
          version: 5343,05 01,01
          serial: M366S0924CTS-C75
          slot: DIMM1/J14
          size: 64MB

Any help is greatly appreciated.

EDIT: Umm, a little news. I tried taking the 64 meg out and just leaving the 512 in, and when I try to turn on the computer, it beeps (not the normal startup sound for an old mac) and won't do anything. It's as if there is no RAM in it at all. I believe the 512 is defective and I'm going to try to exchange it for a new one.

---

