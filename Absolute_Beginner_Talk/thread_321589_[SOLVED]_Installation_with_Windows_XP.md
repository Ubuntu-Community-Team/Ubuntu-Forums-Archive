---
title: "[SOLVED] Installation with Windows XP"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Hopalong on 2006-12-19
I've now got Ubuntu Edgy Eft installed, in company with Windows XP, SP2. It was installed from a downloaded and burned live disk, which worked O.K. I have the boot options, and can select Windows. Windows makes its appearance, but then says 'autochk program not found - skipping autochk', shuts down, and reboots.  Where did 'autochk' go? and how do I get it back?

---

### Post by LookTJ on 2006-12-19
Hmm, I'm confused, what is this program "autochk"?

EDIT: I googled your words.

found [this](http://www.techspot.com/vb/all/windows/t-7746-autochkexe-not-found.html) with the exact same problem.

---

### Post by LookTJ on 2006-12-19
is your partition(ntfs) hidden?

---

### Post by whoismilan on 2006-12-19
I would like to add to the previous reply that if you can boot into Ubuntu, open the terminal (Applications > Accessories > Terminal) and type: "sudo fdisl -l". This will print a list of your partitions, and will show you wether the NFTS partition is hidden on not (Id 17 = hidden, Id 7 = not hidden).

I haven't tried, but if this is caused by the NTFS partition being hidden, you would most probably be able to change it in a partition editor in Ubuntu. Either use the live CD, or install gparted, to make this easy.

---

### Post by LookTJ on 2006-12-19
> **whoismilan said:**
> I would like to add to the previous reply that if you can boot into Ubuntu, open the terminal (Applications > Accessories > Terminal) and type: "sudo **fdisk** -l". This will print a list of your partitions, and will show you wether the NFTS partition is hidden on not (Id 17 = hidden, Id 7 = not hidden).

I haven't tried, but if this is caused by the NTFS partition being hidden, you would most probably be able to change it in a partition editor in Ubuntu. Either use the live CD, or install gparted, to make this easy.just some corrections.

---

### Post by Hopalong on 2006-12-20
Yes, it was. I'm glad to say that I found that gparted was installed, and with this I changed the flags. Now everything works (Hopalong is sprinting!).  My thanks to all who contributed, particularly Taylor
  (Meanwhile the next job has screwed up in the same area, Heigh-ho! . . . )

---

