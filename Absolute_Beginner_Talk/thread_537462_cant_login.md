---
title: "cant login"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-08-28
fiesty fawn
get a massege gdm could not write to your authorizion file this could mean your out of space?  i just installed this? should have plenty of space, also grub show ubuntu kernel 2.6.20 16 and 15 2 places to start up ubuntu is this right i think i only installed it 1 time or at least thats all i wanted to do. any ideas as to whats going on here

---

### Post by jamvegan on 2007-08-29
If you can boot into recovery mode (which will cause a bunch of text to scroll up the screen, ending with a boot prompt), then type:
```
df
```
and look for the line in the output that has "/" in the "Mounted on" column.  What does it say in the "Use%" column?

As for the two kernels: yes, it is normal for Ubuntu to install both of them.

---

### Post by sumguy231 on 2007-08-29
> also grub show ubuntu kernel 2.6.20 16 and 15 2 places to start up ubuntu is this right i think i only installed it 1 time or at least thats all i wanted to do. any ideas as to whats going on here
This just means you have two versions of the Linux kernel installed. This is normal and all you really need to know is to not worry about it and choose the latest/first one.

If you want to double-check how much space you have, hit ctrl+alt+f1 to get to a terminal, log in, and type 'df -h'. This will tell you how much of the hard disk you're using. When you're done you can type 'exit' and press Ctrl+Alt+F7.

Edit: Beaten! Argh!

---

### Post by trucker33377 on 2007-08-29
wow looks like im out of space on that.

---

### Post by feistyfirsttimer on 2007-08-29
Your Ubuntu installation used up all your hard drive?  How big is your hard disk?  Are you dual-booting?  If so, how big is your Ubuntu partition?

---

### Post by trucker33377 on 2007-08-30
it was set at 4 gigs. I had no idea that if i used it up I wouldnt be able to even log in. there was plenty of room on the HD 120gigs. so i reinstalled ubuntu and gave it alot more space this time.

---

