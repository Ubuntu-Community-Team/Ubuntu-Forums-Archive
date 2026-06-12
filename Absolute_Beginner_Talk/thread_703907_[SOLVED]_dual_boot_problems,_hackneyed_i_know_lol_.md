---
title: "[SOLVED] dual boot problems, hackneyed i know lol but please help"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2008-02-21
i just got a new computer (hp) and the first thing i did when i got it was whipe vista and pop ubuntu on, then i realized i had a few programs i wanted to run with vista so i tried to reinstall vista but i had this problem and i looked it up in some forums and in order to fix the problem i had to boot knoppix and change the active partition from the linux partiton to the one i needed to install windows on so i did that. then after vista was installedand i rebooted the GRUB menu never came up; vista just booted up. so i switched the active partition back to linux and now when i restart nothing happens i just get a blank screen, and no GRUB menu. any ideas on how to get GRUB to show up so i can choose between windows and linux? or why nothing is happening when i start my computer? lol thanks in advance :)

---

### Post by kbless7 on 2008-02-21
There are many threads on this. When you install windows it overwrites the MBR, so grub gets cleared out. Pop in the live cd, open a terminal and type

```
sudo grub
root (hd0,<tab>
```

this is assuming its on your first hard drive. look for the partition number of ubuntu. it will be type 83 ext2f or something like that. then run the root command again with the correct partition number

```
root (hd0,1)
setup (hd0)
quit
```

This will install grub. after that just change the /boot/grub/menu.lst when you get back into ubuntu.

---

### Post by onearmedpanda on 2008-02-21
thank you very much
i did that and grub shows up but windows isn't listed : /
any idea on why and/or how to fix it?

---

### Post by onearmedpanda on 2008-02-21
nevermind
figured it out :)

---

