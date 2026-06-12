---
title: "Removing previous Ubuntu from Grub"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-09-26
When I updated Ubuntu for the first time, two new OS choices appeared in GRUB, just another Ubuntu.  To delete the old (unupdated) Ubuntu from GRUB, I think I can become a superuser, open the /boot/grub/menu.lst and delete the two older ones.

My question is, is it a good idea to remove these two?  Would I ever need to use them?  Is there another, better fix for this problem?

---

### Post by whizbaby on 2006-09-26
Just
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
and do what you said.(so you can get back to your old grub menu by simply switching the files in the cp command above if you feel like it)

---

### Post by think13 on 2006-09-26
Ok Thank you.

---

### Post by bodhi.zazen on 2006-09-26
Or comment out the lines in menu.lst

# Add a hash mark at the start of the line

---

### Post by lapsey on 2006-09-26
if ubuntu can add new lines to grub, why can't it remove them

---

### Post by whizbaby on 2006-09-26
> **lapsey said:**
> if ubuntu can add new lines to grub, why can't it remove them
If you install a kernel grub guesses that you want to boot it. (that's why it adds).
What would you say if every other grub entry is removed at the same time? You'd say **huh?**, especially when the new kernel doesn't work and you want to boot into one of your old systems.(that's why ubuntu can't remove automatically - how should it know which entry you want to stay and which not, that's personal preference)

---

### Post by az on 2006-09-26
You need not edit the menu list by hand - just remove the corresponding package.

Use synaptic and see what linux-image-xxxxxx packages you have installed.  Remove the older ones.

In future releases, this sort of thing will be taken care of automatically for you.  Once you install a new linux-image package and boot into the new kernel, the old one will be removed.

---

### Post by mitch.c on 2006-09-26
> **think13 said:**
> When I updated Ubuntu for the first time, two new OS choices appeared in GRUB, just another Ubuntu.  To delete the old (unupdated) Ubuntu from GRUB, I think I can become a superuser, open the /boot/grub/menu.lst and delete the two older ones.

My question is, is it a good idea to remove these two?  Would I ever need to use them?  Is there another, better fix for this problem?

I usually remove the previous kernel image after I'm sure the latest is stable on my system. From the terminal:
```
sudo aptitude purge linux-image-2.6.15-26-686 linux-restricted-modules-2.6.15-26-686
```
Using this method calls update-grub which modifies menu.lst automatically, removing the older kernel references.

---

### Post by whizbaby on 2006-09-26
> **azz said:**
> Once you install a new linux-image package and boot into the new kernel, the old one will be removed.
So that you are left with only the new kernel to boot, removing all other installations (some people have more than one system, e.g. FreeBSD, debian, edgy) without being asked? Can't believe that, this would be a big step back in userfriendlyness and a big step towards M$ way of doing it...

---

### Post by az on 2006-09-27
> **whizbaby said:**
> removing all other installations (some people have more than one system, e.g. FreeBSD, debian, edgy) without being asked? 

No.  Not removing all other installations!  Just removing the older versions of the same kernel package on your Ubuntu partition.

---

