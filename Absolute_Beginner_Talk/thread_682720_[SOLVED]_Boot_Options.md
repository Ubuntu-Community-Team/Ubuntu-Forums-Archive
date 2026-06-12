---
title: "[SOLVED] Boot Options"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-30
Hello!
I have 7 options in my boot screen which is really a lot! Two are "other operating system" and "windows" and one is "cpu test" but my problem is on other 4 options. Two are for recovery and two for kernal. Two are for 2.6.24.-3 and two for 2.6.24.-5 Can I delete those which are for 2.6.24.-3 because I never used them and I don't know what are them. And how can I delete them?
+++
Why are there 2.6.24.-3 and 2.6.24.-5?
Thank you.

---

### Post by seventhc on 2008-01-30
I am not saying that this is safe or ok to do but
if you really want to edit it, open a terminal and put this in
```
sudo gedit /boot/grub/menu.lst
```first back it up, and instead of deleting it entirely you might just comment them out by putting # in the beginning of each line you don't want.
why do you have so many?? Is this a multi boot system??
after you open it, could you pls paste it here.

---

### Post by aeiah on 2008-01-30
you can delete the entries, yes. you can modify the entry names too. the file you'll need to edit is /boot/grub/menu.lst

you're best commenting out the entries for the kernel you dont want showing rather than deleting them. you never know when you might need them. this wont delete the kernels however, but you shouldnt need to do that anyway.

note however that your grub default boot may change if you comment out an entry that's at the top. so if you usually booted windows by default (which is at the bottom) by using the number 5, then it will now be number 3. this probably wont affect you since im guessing your newer kernel is the one you default to, and its number 0 anyway

---

### Post by Hoom@n on 2008-01-30
Thank you. I edited it. I check the result after restart.

---

### Post by dstew on 2008-01-30
If you remove the old kernels using Synaptic, the grub menu entries will be removed automatically.

---

### Post by Hoom@n on 2008-01-30
Yea thank you. But I just put # and I think it'll work. As I said I'll check it.

---

### Post by dstew on 2008-01-30
Yes, the only downside is that you have the old unused kernels taking up hard drive space.

---

### Post by Hoom@n on 2008-01-31
So, how can I remove that old kernals from hard too?
Thanks.

---

### Post by dstew on 2008-01-31
Uninstall the kernel packages using Synaptic.

---

### Post by Hoom@n on 2008-01-31
Sorry, please explain how can I do that.
Thanks,

---

### Post by dstew on 2008-01-31
Go to System --> Administration --> Synaptic package manager. In the lefthand window of the Synaptic screen, choose Base System. In the right hand window, you should see the installed kernel images marked with the green squares. The older ones have the lower numbers. You click the green square, choose Mark for Removal. It then shows you all the packages it will remove. Click Mark. Then, after you have marked all the old kernel images you want to remove, click the green check Apply menu button. Just don't delete *all* your kernel images, or you won't be able to run your computer!

---

### Post by Hoom@n on 2008-02-01
Thank you. I installed gutsy again and those packages removed automaticaly.

---

