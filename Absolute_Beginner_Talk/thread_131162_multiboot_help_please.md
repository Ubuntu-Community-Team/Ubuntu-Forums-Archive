---
title: "multiboot help please"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by blackhawkpowers on 2006-02-15
well just so everyone knows I have been using ubuntu now for about 6 months and absolutely love it. Now to my problem, I have recently reformated one of my computers that was dual booting XP and Ubuntu. This weekend I was forced to reformat the windows bit. (imagine that) after this was done grub was erased I know the linux partition is still there and I believe my information still is but I cannot boot into ubuntu. At this point I would probably just wipe windows off but I do have 2 apps that need windows to run on. So my question is basically how to I just install grub on the computer without reformating and loosing my info on the linux partition?

---

### Post by zxee on 2006-02-15
To boot into your ubuntu install, boot from the install or live cd and type boot/kernel*  (*that would be the actual kernel you have installed) or you could opt for rescue mode. Once you are in linux, and you could do this from the live cd too-open a terminal and type 'grub' or 'sudo grub' if necessary. When you get the grub prompt i.e. grub> then type 'find /boot/grub/stage1' The output from that should be where grub is installed. Say you get (hd0,0) You would then type 'root (hd0,0)' and finally 'setup (hd0,0)' Adjust the actual (hdX,X) for where you want to install grub to.  The setup command should tell you if it successfully setup grub. Hope that helps.

---

