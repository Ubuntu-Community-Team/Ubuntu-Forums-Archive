---
title: "Xp Vista and Ubuntu bootloader"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by auredium on 2008-02-27
Hello,

yes i know there are a lot of questions asked already about the boot loader. But i haven seen mine so far so bare with me.

My situation is as following;

HDD1) Windows Xp
HDD2) Vista/Ubuntu

Sow, i managed to install EasyBCD and can boot Xp, Vista and Ubuntu. Fine right? I thought so.
But hold, wait on, what's this?

When i boot Ubuntu (installed from Life CD) it first asks me to insert a boot disk (after pressing a key without a disc in my computer it continues, minor glitch not really problematic. After that, grub seems to boot and I get the same choices as with easyBCD, a bit redundant I'm afraid.

Generally, can I ditch grub? If yes, how?

Any help is welcomed in advance.

---

### Post by Iam138 on 2008-02-27
Your boot order is out of whack. It's trying to boot from your optical drive first.  Just go into BIOS and change it so the Ubuntu HDD is first in the order.

---

### Post by auredium on 2008-02-29
Well, i did change the bootorder but as you can guess it's juggling with handgrenades. If the bootorder is changed, Windows will not boot but ubuntu will. I have solved it partly. The second boot menu caused by grub has been set to a 0 meening it will autoboot Ubuntu and not bother me again with a bootmenu.

I stil get a message that my bootdisc cannot be found, but once i pres a key, it simply continu's.
Yes, i know my first solve is dirty, but it is the most effective without digging deep into Windows.

---

### Post by forrestcupp on 2008-02-29
I think it's the other way around.  You didn't really need EasyBCD.

---

### Post by auredium on 2008-02-29
Without EasyBCD it got the Windows bootmenu with only XP and Vista as options. I Couldn't get grub to be booted (grub was located on HD2,1), thought it might be possible that the vista bootmenu was located on HD2,0 since HD0 didn't help to resolve the problem.

---

