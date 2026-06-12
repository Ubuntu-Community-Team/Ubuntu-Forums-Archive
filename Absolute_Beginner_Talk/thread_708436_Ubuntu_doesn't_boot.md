---
title: "Ubuntu doesn't boot"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by mason215 on 2008-02-26
After i restarted my computer, and went run ubuntu. But after a quarter of a way booting it just goes to a black screen, i didnt install anything recently so i dont what the problem is.

is there any commands i can run in recovery mode

---

### Post by airbornemist6 on 2008-02-26
Have you updated recently? If so, the update may have broken the kernel, if so, try choosing a different kernel version from the grub list.

---

### Post by mason215 on 2008-02-26
> **airbornemist6 said:**
> Have you updated recently? If so, the update may have broken the kernel, if so, try choosing a different kernel version from the grub list.

ok i did this, but know it takes a long time to boot, is there any way to make it go faster

---

### Post by matey3 on 2008-02-26
I've seen one particular case more than once.. and that happened after I instaled Xen on Ubuntu... (oh I didnt see Mason's reply,, he is right too)
Any ways can you hit the Escape key and see the menu?

It defaults to like 2 or 4 seconds so you have to be fast.

once you get in the menu use the e key to edit the line.
it usually has the problem with pointing to the wrong partition. like (hda 0,0) and it should be some thing like (hda 0,2) so play around with the 0s (both of them if u saw 2) and change them (one at the time) and then hit the b key to boot...if no boot go back e-diting...b-ooting

If one works remember which one so you can go into /boot/grub and edit (pico nano vi) the menu.lst file. (sometimes u can cheat and lookup at the menu.lst~ or old or something...
good luck..

If that is not the case then sorry for giving u the wrong info...but please do give us more detail  as to what was the last thing installed etc...

---

### Post by sayakb on 2008-02-26
> **mason215 said:**
> ok i did this, but know it takes a long time to boot, is there any way to make it go faster

Already discussed in another post.
Open a terminal and type 

```
sudo gedit /boot/grub/menu.lst
```

There, scroll down to the appropriate kernel option you are booting to. Replace a string which says "quiet splash" to "quiet nosplash"

---

