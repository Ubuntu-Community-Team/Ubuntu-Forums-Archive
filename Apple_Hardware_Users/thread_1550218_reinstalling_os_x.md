---
title: "reinstalling os x"
date: 2010-08-10
forum: Apple Hardware Users
---

### Post by bob1222333333333333333 on 2010-08-10
I installed linux on my imac G5(i did not dual boot) and now i want to install os x again on my mac but when i try to boot the installation cd it doesnt work. Help me please.

---

### Post by GregBrannon on 2010-08-10
Why is it marked 'solved?'

---

### Post by Macskeeball on 2010-08-11
To boot from the install DVD, hold down the C key as you start your computer. If that doesn't work, you might not be holding the C key down long enough, or the disk could be damaged (check it for fingerprints or scratches).

---

### Post by bob1222333333333333333 on 2010-08-11
Ive tried that but it doesnt work i just get some error screen telling me to restart. The installation disk is clean,

---

### Post by conundrumx on 2010-08-11
Try holding down the Option key as the computer starts, you should be able to select the CD drive as a boot device.

---

### Post by bob1222333333333333333 on 2010-08-11
Ive tried that to but i get no different result.

---

### Post by conundrumx on 2010-08-11
> **bob1222333333333333333 said:**
> Ive tried that to but i get no different result.

Try clearing PRAM, and/or Command Option, Shift and Delete while booting.

---

### Post by bob1222333333333333333 on 2010-08-11
I still get the error message. 
The message:unable to find driver for this platform: powermac 12,1 and no debugger configurated- dumping debug information. also on the grey screen it said panic: we are hanging in here. Also a box in the middle of the grey screen telling me to restart and a little more

---

### Post by bastones on 2010-08-11
It could be that when you installed Linux, Linux wiped your HDD clean deleting the hidden partition allowing you to install OS X from your recovery media that came with your Mac. You may need to buy a retail disc from an eBay seller for OS X Leopard. Make sure, if you do this, to buy only from a reputable seller with good trader feedback. By the way I could be wrong here (because, normally Ubuntu install doesn't delete hidden partitions AFAIK) but this is what happened on my Intel Mac mini (but could of been down to something I did).

---

### Post by Macskeeball on 2010-08-11
> **bastones said:**
> It could be that when you installed Linux, Linux wiped your HDD clean deleting the hidden partition allowing you to install OS X from your recovery media that came with your Mac. You may need to buy a retail disc from an eBay seller for OS X Leopard. Make sure, if you do this, to buy only from a reputable seller with good trader feedback.

The OP is using an iMac G5. Do PowerPC Macs use a hidden partition? I thought that was just Intel Macs (the EFI partition).

---

### Post by bastones on 2010-08-11
> **Macskeeball said:**
> The OP is using an iMac G5. Do PowerPC Macs use a hidden partition? I thought that was just Intel Macs (the EFI partition).

Yeah, I could be wrong but this is what happened for me (on an Intel Mac mini) so I've modified my post to state this - don't want the OP buying a disc when not required - but just posted to reference because I initially thought that *may be* the case

---

### Post by Macskeeball on 2010-08-11
I did some Googling, and it looks like the problem may be that you're using the wrong OS X install disk. Where did you get your OS X Leopard disk?

You might be using a model-specific OEM disk that's for a different Mac than what you have. You say you're using an iMac G5, but the error message mentions "powermac." Retail versions of OS X are not model specific, but the restore disks that come in the box with the computers are. Maybe you got the disk secondhand from eBay, etc. and it's for a different Mac model.

Again, the question is: where did you get your OS X Leopard disk? Has that particular disk ever worked in that computer before?

---

### Post by bob1222333333333333333 on 2010-08-11
I have os x tiger 10.4 we have one intel and one power pc. The cds are the ones that came with the macs and it has worked on the computer before. Does it make an difference if the disk is for the intel or powerpc? i might have mixed them up then, but ive tried both before. the computer i use is an powerpc.

---

### Post by bob1222333333333333333 on 2010-08-11
I only remebered getting 2 install cds, but one was for the applications and one is the one i am using now.

---

### Post by Macskeeball on 2010-08-11
> **bob1222333333333333333 said:**
> I have os x tiger 10.4 we have one intel and one power pc. The cds are the ones that came with the macs and it has worked on the computer before. Does it make an difference if the disk is for the intel or powerpc? i might have mixed them up then, but ive tried both before. the computer i use is an powerpc.

Yes, for a PowerPC Mac you need to use the PowerPC disk. You say it came with the computer and that the computer is an iMac G5, so does the disk say iMac G5 on it?

---

### Post by bob1222333333333333333 on 2010-08-11
The cds for both computers are identical. os x install disk is said on it. But if that is the case i will try to the ppc cd.

---

### Post by bob1222333333333333333 on 2010-08-13
I  found the cd and put it in the computer and the install starts but it wont find a volume to install it on.

---

### Post by conundrumx on 2010-08-13
> **bob1222333333333333333 said:**
> I  found the cd and put it in the computer and the install starts but it wont find a volume to install it on.

Open Disk Utility from the Utilities menu and wipe the disk.

---

