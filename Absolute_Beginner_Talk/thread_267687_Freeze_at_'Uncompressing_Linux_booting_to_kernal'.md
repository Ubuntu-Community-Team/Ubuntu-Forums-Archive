---
title: "Freeze at 'Uncompressing Linux booting to kernal'"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by snowsqwert on 2006-09-29
I have been trying to installfrom a CD (CD works fine. Uncompressing starts then after some time I get a blank screen with 'Uncompressing Linux... OK, booting the kernal' and thats it the process frezzes right there. Any advice on what I'm doing wrong etc would be appreciated.
Thanks.

---

### Post by po0f on 2006-09-29
snowsqwert,

Do you have any weird/exotic hardware?

---

### Post by Drakkor on 2006-09-29
Check the md5sums or "Check CD for defects" ?

---

### Post by snowsqwert on 2006-09-29
No weird hardware its a standard Pent 3 800 mghz.
Will check the cd for errors - thanks

---

### Post by snowsqwert on 2006-09-29
how would I check the md5sums? 
Thanks for replying

---

### Post by Drakkor on 2006-09-29
To save a possible step,when you boot the CD there is option #2 "Check CD for defects" try this first,then if that fails type```
md5sum
``` into the terminal and then just drag the .iso into the terminal,and you'll have to wait a bit but it should match whatever one you dowloaded.  :)
The sums are here:
b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso

---

### Post by po0f on 2006-09-29
snowsqwert,

So when the computer freezes, there is no activity whatsoever (CD spinning, hard drive indicator flashing)?

If you know your computer has a fairly buggy BIOS, try booting with these kernel parameters:
```
linux acpi=off noapic nolapic
```

These are the arguments I have to pass to the kernel to get my computer to boot the live CD.

---

### Post by snowsqwert on 2006-09-29
thankyou will try

---

### Post by snowsqwert on 2006-09-29
How & where do I put in the code please?

---

### Post by po0f on 2006-09-29
snowsqwert,

Boot the live CD.  When it comes to the part when it asks you to press enter to start the graphical install, just type in the above, and press enter.

---

