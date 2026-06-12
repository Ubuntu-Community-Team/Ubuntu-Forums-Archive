---
title: "blank screen boot from cd Macbook Pro 13 inch Mid 2012"
date: 2012-12-19
forum: Apple Hardware Users
---

### Post by luckyisdog on 2012-12-19
there's a blinking cursor whenever I insert the ubuntu 12.04 cd in. I've also tried the ubuntu 12.04 precise pangolin amd64 for mac. it showed the same thing. 

I have made 50gb of free space for it using Mac's disk utility.

I've read I had to set nomodeset noapic or something but I can't access that menu. it's just the blinking cursor. 

any clues on how to fix this?

---

### Post by skimmilk on 2012-12-19
Did you get rEFIt before trying to boot? rEFIt will show you your boot options when starting up and from there you can select boot from cd

---

### Post by luckyisdog on 2012-12-20
yes I have installed rEFit, and I can boot from cd. I just don't know how to set boot options on that? Let me look it up

---

### Post by skimmilk on 2012-12-21
Hmmm I had a similar problem when booting it showed a blinking cursor and said Missing Operating System. Check to make sure that your disk partition is listed in the MBR partition table

---

### Post by luckyisdog on 2012-12-22
Made a bootable usb ubuntu AMD64, booted from it and it worked! That's all that it needed

---

