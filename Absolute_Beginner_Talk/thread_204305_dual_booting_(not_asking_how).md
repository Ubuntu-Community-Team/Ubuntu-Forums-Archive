---
title: "dual booting (not asking how)"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by recke on 2006-06-26
i am dual booting and when i turn on my computer it asks me what i want to boot to, ubuntu as first choice and at the bottom there is windows.  it boots to the first selection if i dont do anything for 10 seconds.  how do i get it to either dont boot to the first thing in 10 seconds or put windows as #1?

---

### Post by bruenig on 2006-06-26
```
sudo gedit /boot/grub/menu.lst
```
When you get in here, line 19 gives you the time out option, it should say 
```
timeout		10
```
You can change that number to something really high.

The easiest way is probably just to make windows the first selection on the list and all you have to do to do that is cut all of the windows information, probably looks something like this and is at the bottom of the file
```
title		Windows 95/98/NT/2000/XP
root		(hd0,0)
makeactive
chainloader	+1
```

And paste it at the top of all of the other boot options, my top boot option looks like this
```
title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot
```
may look different in yours but you get the idea, paste it above the highest thing that looks like that in the file that doesn't have #'s in front of it. Save changes.

---

### Post by recke on 2006-06-26
wow, thanks.  gotta boot to ubuntu now.  i use windows for gaming and thats usualy what i do.  if i know im just surfing or something i will use ubuntu.  if some one wants to use my computer they use ubuntu.

---

### Post by aysiu on 2006-06-26
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by confused57 on 2006-06-26
You could copy and paste your grub menu.lst Windows entry above the line
###Begin Automagic Kernal List

Keep the default 0, that way if the kernel is updated, your Windows entry would still be the first option to boot.

---

### Post by recke on 2006-06-26
i now have xp set to default and a timeout of 60 seconds.  i have been using ubuntu since hoary and haven't needed to ask any questions but this just had me stumped.  i googled but i didn't really know what to look for. thanks.

one more question.  is it possible to triple boot?  i want to have xp, ubuntu and a third os for testing and fiddling with.

---

### Post by aysiu on 2006-06-26
Yes. I've quintuple-booted before.

---

### Post by catlett on 2006-06-26
Grub can do anything. To get a sense of grub's power check out this "infamous" grub example. [http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973) It is the thread about the 100+ OS booting system using grub.

The best way to add a third or fourth etc. Is to not let the new OS install a bootloader or it's own grub. Just add an entry to your current menu list to boot to the new OS after you install it.

---

