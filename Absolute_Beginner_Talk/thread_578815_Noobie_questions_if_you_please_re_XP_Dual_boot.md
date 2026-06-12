---
title: "Noobie questions if you please re XP Dual boot"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by chrisfoster1971 on 2007-10-17
I've installed Feisty Fawn and now I am unable to boot into windows....which I know is wonderful etc etc, but I need it for work so could really do with a little help.

I trialled with the liveCD and thought it was worth a bash, but I am not presented with a boot loader screen, after installing to the same disk as XP is installed to. I chose guided "Use largest continous space" and now XP doesn't boot although the system files are still there.

I've checked the grub is installed which it looks like it is but I must admit I am lost, any help appreciated.

---

### Post by bodhi.zazen on 2007-10-17
post the output of :```
sudo fdisk -l
```

and the BOTTOM of /boot/grub/menu.lst (the part where you see entries of booting)

title ubuntu
root ...
initrd ....

title Windows XP
root ...

---

### Post by logos34 on 2007-10-17
What error message are you getting?

Did you shrink windows partition before ubuntu install (maybe with Partition Magic or Acronis)?

---

