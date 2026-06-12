---
title: "ubuntu gui will not load...HELP"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by windowszombie on 2007-05-07
I downloaded the newest version of Ubuntu for my system booted the disk to the splash screen where I am asked how I would like to proceeded. I choose to not install Ubuntu just yet but check it out with out installing it. Then the loading screen comes up and it starts doing its thing. Until I receive an error message telling me that the GUI cannot be loaded then I am dumped to what I assume is the Ubuntu command prompt. Anyone have any ideas why this would be happening and what I need to do to fix it?

---

### Post by Ianman on 2007-05-07
You will need to provide a bit more information I think.

What type of video card do you have? Does this happen every time? Do you have another system you can try the live CD on? What about the rest of you system....whats the spec?

Thanks.

---

### Post by windowszombie on 2007-05-09
The video card is an 8800gts, in a gigabyte ga-965p-ds3 mobo. Sorry about not giving a bit more info in the first post.

---

### Post by zvacet on 2007-05-10
```
 sudo dpkg-reconfigure xserver-xorg
```

Replace **nvidia** with **nv**.After that you can go and search for proper drivers for your card.

---

