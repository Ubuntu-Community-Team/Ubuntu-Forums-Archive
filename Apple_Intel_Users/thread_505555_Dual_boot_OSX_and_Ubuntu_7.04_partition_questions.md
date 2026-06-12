---
title: "Dual boot OSX and Ubuntu 7.04 partition questions"
date: 2007-07-20
forum: Apple Intel Users
---

### Post by mshale on 2007-07-20
So I was reading the posts about dual booting (I have a 2.16 GHz C2D macbook), and I have some questions.


Will the mac ship with 2 partitions, one for EFI and one for OSX? Don't remember where I read that info.

I want one partition for OSX and VM windows, one for Ubuntu, and one large partition for all of my multimedia files.  Where (if i even need one) does the SWAP partition come in to play?  I read a post once about not using a swap.  With 2 Gigs of ram, who needs one?

I have done searches for the wiki on dual booting with OSX and Ubuntu using rEFIt, but i seem to not be able to find it anymore.

Thanks everyone!

---

### Post by cyberdork33 on 2007-07-20
> **mshale said:**
> Will the mac ship with 2 partitions, one for EFI and one for OSX? Don't remember where I read that info.
yes, the EFI partition is hidden.

> I want one partition for OSX and VM windows, one for Ubuntu, and one large partition for all of my multimedia files.  Where (if i even need one) does the SWAP partition come in to play?  I read a post once about not using a swap.  With 2 Gigs of ram, who needs one?
you should have a swap space. you can put it after partition 4 though since it is not bootable.

Suggestion:
1. EFI
2. OSX
3. Shared Partition
4. Ubuntu Root
5. Swap

you can switch 3 and 4 if you want and there are plenty of other combos you could use. you can even delete the EFI partition altogether since it isn't used (although who knows if it will be in the future.)

> I have done searches for the wiki on dual booting with OSX and Ubuntu using rEFIt, but i seem to not be able to find it anymore.
There are many how-tos for this in this forum. Search here.

---

### Post by mshale on 2007-07-20
> **cyberdork33 said:**
> yes, the EFI partition is hidden.


you should have a swap space. you can put it after partition 4 though since it is not bootable.

Suggestion:
1. EFI
2. OSX
3. Shared Partition
4. Ubuntu Root
5. Swap

you can switch 3 and 4 if you want and there are plenty of other combos you could use. you can even delete the EFI partition altogether since it isn't used (although who knows if it will be in the future.)
.

ok, what i was reading was saying that it is not possible to have more than 4 partitions.  I guess that you could create a primary partition with some secondary parts in it?  or was it meaning that you can only have 4 BOOTABLE partitions?

---

### Post by cyberdork33 on 2007-07-20
> **mshale said:**
> ok, what i was reading was saying that it is not possible to have more than 4 partitions.  I guess that you could create a primary partition with some secondary parts in it?  or was it meaning that you can only have 4 BOOTABLE partitions?

you can have up to 128 partitions on a disk with GPT (this is the default mac partition type). The problem is that the emulated BIOS MBR can only use 4 primary partitions. Extended or logical partitions were a hack / workaround to utilize more partitions, but it is not possible to make an extended partition on a GPT disk (because they are not needed). So... you are limited to 4 partitions.

BUT...

Ubuntu can see the other GPT partitions after it has booted. so it is ok to put partitions after number 4 (like swap), you just won't be able to boot from them. That is, unless you can boot directly from EFI. ( On a side note, for this reason, OSX doesn't have to be one of the first 4 partitions ;) )

---

### Post by mshale on 2007-07-22
Thank you very much!  So if i wanted to, i could theroeticaly put 3 dif operating systems on the thing and have a shared partition that is after one of the first four?  Would OSX be able to see that shared partition?  I'm sorry that i'm asking so many questions, it's just that i find all of this quite interresting :)

---

### Post by cyberdork33 on 2007-07-23
> **mshale said:**
> Thank you very much!  So if i wanted to, i could theroeticaly put 3 dif operating systems on the thing and have a shared partition that is after one of the first four?  Would OSX be able to see that shared partition?  I'm sorry that i'm asking so many questions, it's just that i find all of this quite interresting :)

Windows would not, but linux / OS should, yes

---

### Post by mshale on 2007-07-23
Great!  But this all seems quite difficult to get what is in essence just two different flavors of the UNIX platform onto one laptop... lol.  I mat just end up snagging the Parallels program and running windows and Ubuntu as an emulation... I may just be too lazy to get it done... lol

Thanks for your input!

---

### Post by cyberdork33 on 2007-07-23
well if you are going to use a VM, then checkout Vmware Fusion first.

---

