---
title: "Dual Booting Linux Mint and Ubuntu... Errors"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by I_R_LEENUCKS_MAN on 2008-04-07
As it says in the title, I'm dual booting the latest version of Linux Mint, and Ubuntu Gutsy Gibbon. However, when I boot Ubuntu, I get an Error 8 at some point in the boot, and some disk check error. It enters a maintenance shell which I have to manually control+d out of the shell. How can I fix this, or uninstall LinuxMint, which also seems to have comandeered GRUB?

---

### Post by bodhi.zazen on 2008-04-07
Can you post the Ubuntu stanzas from /boot/grub/menu.lst 

ie 

title Ubuntu
root (hdx,y)
kernel 
initrd
boot

---

