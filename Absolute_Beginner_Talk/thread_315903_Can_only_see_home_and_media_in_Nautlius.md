---
title: "Can only see home and media in Nautlius?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by SZorg on 2006-12-09
So I installed the Kubuntu-desktop package to try out KDE. I love GNome but I hate to be closed-minded, there *may* be better things out there.

Regardless, after installing the kubuntu-desktop, I can only see, when I got o "filesystem" in nautilus, 'home' and 'media'. Even when I do 'sudo nautilus'. What can I change to see everything again? :/

---

### Post by dbbolton on 2006-12-10
are you running nautilus from a gnome session or a kde session ?

---

### Post by msak007 on 2006-12-10
There is a file called ".hidden" in the / (root) directory. Edit it and either delete (from the file) the folders you want to see, or just comment them out with a #. Needless to say this "feature" annoyed everyone and will be removed in Feisty :).

---

### Post by SZorg on 2006-12-11
I was running from GNome.


Thanks, I deleted .hidden and it works perfectly. :]

---

### Post by msak007 on 2006-12-11
> **SZorg said:**
> I was running from GNome.


Thanks, I deleted .hidden and it works perfectly. :]
...or you could just delete the file completely :).

---

### Post by SZorg on 2006-12-12
o_O. I did delete the .hidden file completely. The solution works perfectly. <3 :)

---

