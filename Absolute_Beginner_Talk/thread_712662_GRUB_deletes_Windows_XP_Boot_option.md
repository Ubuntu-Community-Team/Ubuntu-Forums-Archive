---
title: "GRUB deletes Windows XP Boot option"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by smartypants120 on 2008-03-01
Ok, I have a bit of a weird problem...I'm sure it's easy to fix, but I'm new when it comes to inux

I installed Ubuntu 7.10 without a hitch, and GRUb was working fine. I rearranged rhe default boot order from some instructions on the ubuntu forums, and all was good, until one day, my Windows XP option (my default) disappeared from the GRUB Booter. I thought no problem i'll just fix it, and it wored for a bt and then the smae problem with GRUB happened again. I have since reformatted my hard drive, because this put me off using Ubuntu. I have decided I really want to use it again, but the idea that the problem will happen again is really putting me off. I hope that someone can help.

Cheers guys! :KS

---

### Post by Iandefor on 2008-03-01
How did you initially fix it?

---

### Post by Omnios on 2008-03-01
Grub is loaded on the mbr but it reads from within the Ubuntu partition where all the the grub information is stored. Running the O's are stored.

---

### Post by smartypants120 on 2008-03-03
> **Iandefor said:**
> How did you initially fix it?
Well, I went into the terminal and did that fancy thing where you can edit the boot list in the grub folder as an administrator and found the thread on the forum where I found how to change the order and copied that from what I rememer seeing in my .lst file when I was editing it.

---

### Post by mikewhatever on 2008-03-03
You probably place the entry for Windows inside Linux area in menu.lst, so that every time Linux kernel is updated, the windows entry gets deleted. Move it to the very end of the file, that should fix it.

---

### Post by Iandefor on 2008-03-03
Make sure that the entry for Windows isn't in between the lines 

> ### BEGIN AUTOMAGIC KERNELS LIST
[A bunch of stuff in between the two]
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by logos34 on 2008-03-03
> **Iandefor said:**
> Make sure that the entry for Windows isn't in between the lines

I see too many people getting fouled up with this problem.  I wonder what post/howto they're reading.

Iandefor,

That avatar of yours was my desktop theme last winter!  I just loved that bluejay photo...could stare at it for hours, so impressive is the detail and resolution and color

---

### Post by smartypants120 on 2008-03-03
> **Iandefor said:**
> Make sure that the entry for Windows isn't in between the lines

I think this could be the problem, I think it might have been in what I read. Can you just please go over where I should move the windows xp entry in the list to make it the default boot option in GRUB? I just thought it saved me getting mixed up and it could help others, cause it could happen again to someone else. Thanks for your help so much everyone!

---

### Post by warbird on 2008-03-03
you can use a graphical editor to avoid problems like this. One of the best ones is here:
[http://phorolinux.com/kgrubeditor-a-grub-editor-for-kde-4.html](http://phorolinux.com/kgrubeditor-a-grub-editor-for-kde-4.html)
but its for KDE, so you need some extra packages to run it in gnome.
Theres also startup-manager, thats in the repos(gutsy only I think):
sudo aptitude install startupmanager

---

### Post by mikewhatever on 2008-03-03
> **smartypants120 said:**
> I think this could be the problem, I think it might have been in what I read. Can you just please go over where I should move the windows xp entry in the list to make it the default boot option in GRUB? I just thought it saved me getting mixed up and it could help others, cause it could happen again to someone else. Thanks for your help so much everyone!

Placing it to the very end of the file would be just fine.

---

### Post by Iandefor on 2008-03-03
> **smartypants120 said:**
> I think this could be the problem, I think it might have been in what I read. Can you just please go over where I should move the windows xp entry in the list to make it the default boot option in GRUB? I just thought it saved me getting mixed up and it could help others, cause it could happen again to someone else. Thanks for your help so much everyone! I would recommend you put it right *before* those lines, in addition to making sure the option "default" is set to "0" (zero). That way, when a kernel upgrade to Ubuntu happens, you don't have to go back and update the default option. 

There's nothing technically wrong with putting it at the end, but when the kernel is upgraded, it'll add a few menu entries before it, meaning that to keep XP as the default, you'll have to go back and update the value of the "default" option. Putting it at the top of the list, before all the automagic kernel stuff, and setting the default menu entry to the first one saves you from bothering with that.

---

### Post by smartypants120 on 2008-03-04
Ok, I will give these ideas a try, thanks very much for your help everyone! :KS

---

