---
title: "Adding Windows to GRUB"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by rmx.dave on 2007-01-24
I just installed Windows XP onto a small 20 gb partition of my 100gb laptop drive. I was able to get grub back to access Ubuntu again, but now I am having troubles adding Windows back to the bootloader. I did some Googling and searching on these forums and tried to resolve this issue myself, but I could not find anything. I do know that all I have to do is edit that menu.lst file and it should work, but I don't have the slightest idea what to put there.

```
title Microsoft Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1
```
I already added this segment to the menu.lst file, but it is incorrect. I get error # 13 when I try selecting that. I know that the Windows OS is located at SDA3 on my hard drive. I'm assuming all I have to do is change the root (hd0,1) value, but I don't know what to. 

Can anyone assist me?

Thanks a bunch in advance.

//rmx.dave

---

### Post by rabid emu on 2007-01-24
If it's on sda3, you want it to say hd(0,2) since it starts counting from 0.

---

### Post by rmx.dave on 2007-01-24
oh, duh. Thanks for your help, I'm sure that'll do it.

---

