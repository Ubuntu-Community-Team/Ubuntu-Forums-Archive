---
title: "Delete Locked Root file"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by chip_123 on 2008-02-09
Hi I have two locked root owned folders on my desktop that were created by Sbackup and can;t remove them. I have tried rm command from root with no sucess . Help !

---

### Post by Faud on 2008-02-09
Have you tried
```

gksudo nautilus

```
and then just manaully deleting them ?

---

### Post by chip_123 on 2008-02-09
I am new so could you tell me the command to manually delete them after gksudo?

---

### Post by Faud on 2008-02-09
Actually that should allow to browse your files as root so you would just go to your desktop or wherever they are and just hit delete

---

### Post by vinutux on 2008-02-09
1.Alt+F2  and tuype gksu nautilus

2.give root password

3.navigate /home/[COLOR="Red"]urusername[/COLOR]/.Trash

4. shift+delete everything


............Done.............

:guitar:

---

### Post by chip_123 on 2008-02-09
I will try it , Thank You !

---

### Post by crushtastic on 2008-05-17
Thank you, this helped me as well.:KS

---

### Post by buzznot1012 on 2008-05-26
> **Faud said:**
> Have you tried
```

gksudo nautilus

```
and then just manaully deleting them ?

I have the same problem, but it's a folder in my Video directory (under Places).  I tried modifying the code you provided to delete this folder, but I can't seem to get it.  Would you have a sec to share the secret?  Thanks!

---

