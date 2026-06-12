---
title: "[SOLVED] Can A Linux Installed Hdd(pc1) Boot To Another Pc(pc2) With A Different Arch"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by djules26 on 2008-04-09
I have cloned the hard drive(HD1) of my PC1 with linux installed on it using clonezilla but when i installed my cloned hard drive(HD2) to my other computer(PC2) it won't load ubuntu...it only gives me a grub prompt, then nothing else(it never reached to the part where it ask for a login). My PC2 has a different architecture compared to PC1. 

Help is greatly appreciated...Thanks!
Jules

---

### Post by y-lee on 2008-04-09
simple version of the answer; that is not gonna work. To much system dependent stuff in your configuration  files. It wouldn't work with windows either.

---

### Post by maybeway36 on 2008-04-09
Worked for me on Debian (except networking and X11, but I knew how to fix those.)

---

### Post by y-lee on 2008-04-09
> **maybeway36 said:**
> Worked for me on Debian (except networking and X11, but I knew how to fix those.)

that is why i said > simple version of the answer;


you might be able to get it to work if ya correct all the relevant configuration files, I'm not sure and i think it might depend on how different the machines are and the packages installed and or compiled. far easier i would think to reinstall.

---

### Post by lackofcreativity on 2008-04-09
You're gonna need to get the architecture-specific version of Ubuntu.

---

### Post by djules26 on 2008-04-09
thanks for the answers guys...NOW just done cloning again the HD1(source drive). I removed HD1 and installed the cloned drive(HD2) on the same computer(PC1) and set it to master but still it only gives me the GRUB prompt.

---

### Post by djules26 on 2008-04-09
PROBLEM SOLVED! i just did the clone process again. Thanks All for the help...as Y-LEE stated it wont boot if different architecture...true! but it will work also in a different architecture(depending on how different the machines are) but its more complicated to do that...so i decided to make my PC2 identical to PC1...installed the HD2 on it...now it works fine.

thanks again all...

---

