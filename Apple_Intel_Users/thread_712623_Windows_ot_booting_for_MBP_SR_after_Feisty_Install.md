---
title: "Windows ot booting for MBP SR after Feisty Install"
date: 2008-03-01
forum: Apple Intel Users
---

### Post by vegeto626 on 2008-03-01
Hey guys, I currently leopard installed. From there I made another partition for bootcamp (through diskutility). Then I installed Windows XP. Once done I was able to boot into leopard just fine. After that, I went and installed Feisty 7.10 onto a third partition but cutting off a piece off the end of the windows partition. Now I can boot into only into leopard and feisty, while windows throws a error about a corrupt or missing hall.dll file. 

Here is what I have tried so far to remedy the problem.

1. Repair the windows install, installation doesnt even start - hall.dll file still missing, will try another right now after modifying the boot.ini, but please assume that that has failed too

2. fixboot, chkdsk, fixmbr - hall.dll still missing

3. edit the boot.ini and change the partition # (made a option for every partition). Able to see the windows loading screen, but BSOD flash and restart happened. 

4. after fixboot chkdsk and fixmbr, expanded the hal.dll file from the windows disk to the system32 folder - now loading screen loads longer, but eventually a BSOD of UNMOUNTABLE_BOOT_VOLUME error or something like that shows up, but does restart, it stays this way. 

5. create a leopard, windows and ubuntu partition right from the beginning and installed that way - same results as if I did it by cutting off a section of windows partition

6. Installed feisty without the bootloader - hall file still missing, and rEFIt does not show the feisty in the bootable list. 

Oh yea, I followed the instructions in the ubuntu wiki provided and installed the boot loader to hd(0,3) as my partition map is as follows:

1.efi
2.leopard
3.windows
4.feisty

Although i did follow the instructions on the wiki (which seems to have worked for quite a few people) could it be because I'm trying to use XP instead of vista? and how can i get this to work, because I triple booted on my sisters Macbook (not SR) just fine. I have no idea why installing ubuntu would mess with my windows.

Thank you for your help.

---

### Post by cyberdork33 on 2008-03-01
Make windows after Ubuntu.

---

### Post by vegeto626 on 2008-03-01
That actually was the very first way my partitions were set up. I had leopard then a empty partition for storage and a windows partition at the end. When I installed ubuntu the hal.dll problem came up, so not sure if i try that again if anything would be different. Ill give it a try though.

---

### Post by cyberdork33 on 2008-03-01
> **vegeto626 said:**
> That actually was the very first way my partitions were set up. I had leopard then a empty partition for storage and a windows partition at the end. When I installed ubuntu the hal.dll problem came up, so not sure if i try that again if anything would be different. Ill give it a try though.
For some reason, Windows wants to be last (as far as it can tell which means #4).

---

### Post by vegeto626 on 2008-03-02
Im in the middle of the windows install right now. so im installing it on the 4th partition, then ill install ubuntu and the boot loader to (hd0,2). Hopefully this'll work.

---

### Post by vegeto626 on 2008-03-02
Thanks man it worked!

---

