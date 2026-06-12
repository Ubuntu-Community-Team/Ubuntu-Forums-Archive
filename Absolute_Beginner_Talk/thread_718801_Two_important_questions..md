---
title: "Two important questions."
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Xplunger on 2008-03-08
1. If I post my dxdiag can you help me determine if my computer is Ubuntu compatible?

2. How much will dual booting Ubuntu slow down the performance of my xp, I tried some random distro in the past and I remember it slowing it down quite a bit and I don't feel like going down the long long path of reinstalling windows again.... I know I didn't have to but after it had already slowed down my comp. my friends wanted to try some stuff... and it didn't end well.

---

### Post by boeing777 on 2008-03-08
> **Xplunger said:**
> 1. If I post my dxdiag can you help me determine if my computer is Ubuntu compatible?

2. How much will dual booting Ubuntu slow down the performance of my xp, I tried some random distro in the past and I remember it slowing it down quite a bit and I don't feel like going down the long long path of reinstalling windows again.... I know I didn't have to but after it had already slowed down my comp. my friends wanted to try some stuff... and it didn't end well.


Answer:

1. Yes, if it shows all the specs of your system

2.  It should not and will not slow down the performance of your XP by dual booting.  If it did, then you have done something really wrong.  It's very easy to dual boot Ubuntu with XP.  and again, it should not slow down

---

### Post by crjackson on 2008-03-08
1.  It would be better if you post your computer specs. and test it out yourself using the LiveCD.

2.  It sholdn't slow your computer down at all unless there is a problem, or not enough HD space on your system.

---

### Post by Arthur Archnix on 2008-03-08
1. Yes.
2. That's literally impossible. The only distro that could possibly do that is Ubuntu, and only if you installed it with Wubi, and even then, it couldn't do much to slow down your computer.

---

### Post by OldGrey on 2008-03-08
Proabaly the easiest way to see if your pc is compatable is the burn a CD and run it as a live disk, no need to install and see if it works. If it does you can themn go on to install it. Shouldn't affect your XP installation at all if you have it (as you would have to) on a separate partition. I dual boot with no problems.

---

### Post by Xplunger on 2008-03-08
I'm downloading know and I'm going to just run of disk to test.

Also, I think I might have just realised what I did wrong. Before when I partition my hardrive, it was really freaking full, so I might have not given windows enough free harddrive space to correctly function, could that have slowed it down?

---

### Post by xc3RnbFO8P on 2008-03-08
what are the specifications of the computers you were trying to install on?

---

### Post by Tatty on 2008-03-08
> **Xplunger said:**
> Also, I think I might have just realised what I did wrong. Before when I partition my hardrive, it was really freaking full, so I might have not given windows enough free harddrive space to correctly function, could that have slowed it down?

Yes... make sure you dont fill up a partition more than 80%, otherwise it starts to fragment badly and slow down.  Especially with Windows as it stores its swap on the same partition as everything else - so when the swap starts to fragment you will really start to see a slowdown.

---

### Post by Xplunger on 2008-03-08
> **Ringi said:**
> what are the specifications of the computers you were trying to install on?

   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_qfe.070227-2300)
           Language: English (Regional Setting: English)
System Manufacturer: Dell Inc.                
       System Model: Dell DV051                   
               BIOS: Phoenix ROM BIOS PLUS Version 1.10 A04
          Processor: Intel(R) Pentium(R) 4 CPU 2.80GHz
             Memory: 1526MB RAM
          Page File: 609MB used, 2813MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

---

### Post by crjackson on 2008-03-08
> **Xplunger said:**
> I'm downloading know and I'm going to just run of disk to test.

Also, I think I might have just realised what I did wrong. Before when I partition my hardrive, it was really freaking full, so I might have not given windows enough free harddrive space to correctly function, could that have slowed it down?

You could have choked your swap file, and the drive was probably not defraged before you did the install.  This is what I suspect...

---

### Post by crjackson on 2008-03-08
> **Xplunger said:**
> Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_qfe.070227-2300)
           Language: English (Regional Setting: English)
System Manufacturer: Dell Inc.                
       System Model: Dell DV051                   
               BIOS: Phoenix ROM BIOS PLUS Version 1.10 A04
          Processor: Intel(R) Pentium(R) 4 CPU 2.80GHz
             Memory: 1526MB RAM
          Page File: 609MB used, 2813MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

Video Card?  Sound Card?  Free space on drive?

---

### Post by louieb on 2008-03-08
> **Xplunger said:**
> ... Before when I partition my hardrive, it was really freaking full, so I might have not given windows enough free harddrive space to correctly function, could that have slowed it down?

BINGO: Thats the only reason I can think of. NTFS starts to take a performance hit at about 70%  full.  It has a hard time with file fragmentation according to MS. [http://technet.microsoft.com/en-us/library/bb742585.aspx](http://technet.microsoft.com/en-us/library/bb742585.aspx)

---

### Post by crjackson on 2008-03-08
OP hasn't replied in a bit.  I suspect a new U install may be under way :)

---

### Post by xc3RnbFO8P on 2008-03-08
> **crjackson said:**
> OP hasn't replied in a bit.  I suspect a new U install may be under way :)

I dont think so.

---

### Post by Xplunger on 2008-03-08
More like the OP had to work :). But I downloaded Ubuntu and I'm going to look for a dvd to burn it on... <_<, now where did I put that old opensuse disk :lolflag:.

---

