---
title: "Reinstalation of windows for duel boot"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-06-07
Dont know why but my instalation of windows did not go as well as planned. I am runing a duel boot of XP Home and Feisty fawn. It has been a month sence I have used windows do to some problems from reinstalling it. 

SO here is what I want to do. Leave Feisty intact and just reinstall windows into the partition I have it in now.

My question is, will this mess up my installation of Ubuntu? What about the Grub? any ideas or suggestions? 

Thanks 
Sabar

---

### Post by p_quarles on 2007-06-07
Everything I've heard says you should install Windows prior to Linux if you want to dual-boot. If you do it the other way around, it can cause problems. If you can manage it (and I know how complicated this can get), backup all your data and setings in Ubuntu, install Windows (umm, if you need to), and then let gparted carve out a space for Ubuntu. 

Hopefully someone else will have a better solution, but that's what I've come to understand.

---

### Post by durrell on 2007-06-07
Yeah, you shouldn't have any problem installing Windows onto a clean NTFS partition as long as it's the same partition that GRUB is seeing now. If you were to change the partition then GRUB might not see it, I'm not all too familiar with GRUB yet.

---

### Post by icechen1 on 2007-06-07
Reinstall Windows will not remove Ubuntu but it will mess up your GRUB.You have to reinstall GRUB(search the forum for how to do it)

---

### Post by logos34 on 2007-06-07
Since a fresh Windows install will replace grub bootloader with its own, you will have restore grub (using the Ubuntu desktop live cd) to be able to get back into feisty.

After installing windows, simply boot from the ubuntu live cd, load the desktop, opem a terminal and type these commands:

sudo grub

find /boot/grub/stage1

This will output '(hd0,x)'  where x is the root partition # 
Enter this output in the next command

root (hd0,x)
setup (hd0)
quit

Reboot to the hard drive and you should get grub menu and be able to go into windows or linux. 

You shouldn't have any trouble as long as you don't alter the ntfs partition.  Just let windows do a full format of it before install.  I've reinstalled many times and never a jad a problem.

---

