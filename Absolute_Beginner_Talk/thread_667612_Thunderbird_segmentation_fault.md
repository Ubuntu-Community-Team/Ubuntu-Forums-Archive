---
title: "Thunderbird segmentation fault"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Gifty85 on 2008-01-14
I installed yesterday Ubuntu 7.10 again, but I didn't format my home directory. Then, when I installed thunderbird I had all my stuff there, accounts, e-mails, extensions, etc just like I wanted. But, the second time i ran thunderbird the program exit by itself. I try to ran it from console and the output was Segmentation Fault.

Can you help me? :s

Thanks in advance!

---

### Post by ajmorris on 2008-01-14
hi there,
could you please do the following:
```
cd ~
mv .thunderbird .thunderbird.old

```
Then re-run thunderbird, you will not have all your emails etc there, because you just moved your .thunderbird folder, this is to see if the problem is something in your .thunderbird folder, or if there is a problem with thunderbird itself.

---

### Post by Gifty85 on 2008-01-14
It worked. So, this is a problem with my thunderbird config files... :/

---

### Post by ajmorris on 2008-01-14
> **Gifty85 said:**
> It worked. So, this is a problem with my thunderbird config files... :/

That is a pain :(
You could try making a new profile, and copying over ~/.thunderbird/<profile>/Mail to the new profile, so you can still keep all your mail.

---

### Post by Gifty85 on 2008-01-14
Ok, thanks. I'll try to do that.

---

