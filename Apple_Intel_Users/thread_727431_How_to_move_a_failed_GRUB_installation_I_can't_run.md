---
title: "How to move a failed GRUB installation? I can't run windows now."
date: 2008-03-17
forum: Apple Intel Users
---

### Post by acentrado on 2008-03-17
Hi all.

I just installed UBUNTU 7 in my MacBook. First I installed Leopard, then rEFIt, then WindowsXP and Finally I tried to install UBUNTU.

All was going well but I think I made a mistake in the last windows of the process. In the ADVANCED option I allow the installer to place GRUB in the HD0. According to a tutorial I was following this is something you shouldn't do. 

Anyway, I did it. Now when I try to enter in my Windows partition I come back to the rEFIt screen selector.

Can I change GRUB to the Linux partition again? 

Sorry is this question is to simple, I am really new in Linux, and this is my first installation.

Thanks a lot for the help!

-j-

---

### Post by logos34 on 2008-03-17
Allowing Grub to install to hd0, the default location, is usually fine unless you want to use another bootloader. 

You can easily reinstall grub to the linux root partition from the ubuntu Live CD, just choose (hd0,x) instead of (hd0), where x=root partition # as reported by **find** command:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-144e274a5aeaa50ba6c93dcc4cc233626caf8ef0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-144e274a5aeaa50ba6c93dcc4cc233626caf8ef0)

Then restore your previous bootloader to the MBR, and insert an entry pointing to ubuntu.

---

### Post by cyberdork33 on 2008-03-17
you can see the multiboot guide in my signature to see how to fix it. You are still getting odd behaviour though. Things should still work with grub on hd0, you just have to go through grub to get to windows (which you really don't need to do).

---

### Post by acentrado on 2008-03-18
Hey!

Thanks for the guide! It seems very clear. I'll try it and I'll write back here later with the results.

Again thanks!

-j-

---

