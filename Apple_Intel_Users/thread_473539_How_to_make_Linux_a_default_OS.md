---
title: "How to make Linux a default OS?"
date: 2007-06-14
forum: Apple Intel Users
---

### Post by Ubivetz on 2007-06-14
Hi All!

I have RefIt! installed and I want to know how to make Ubuntu default OS?

---

### Post by kzm. on 2007-06-14
me too! and less seconds.. is there a how-to for this?

---

### Post by eldepeche on 2007-06-14
I don't know about a how-to, but you can configure rEFIt under OS X by editing the file /efi/refit/refit.conf . Look for the "legacyfirst" option.

---

### Post by Ubivetz on 2007-06-14
I tried, but it doesn't work.
Run /efi/refit/enable.sh is also required.

---

### Post by eldepeche on 2007-06-14
So in your refit.conf file, you have "legacyfirst" (without quotation marks) on a line by itself, then you ran enable.sh, and it still doesn't boot into Ubuntu by default?

---

### Post by yanaventer on 2007-06-14
I just tried the legacyfirst option, worked fine for me. I didn't do ./enable.sh or anything afterwards, just modified that one line (removed the #).

---

### Post by Ubivetz on 2007-06-14
> **eldepeche said:**
> So in your refit.conf file, you have "legacyfirst" (without quotation marks) on a line by itself, then you ran enable.sh, and it still doesn't boot into Ubuntu by default?
No. I tried to uncomment "legacyfirst" and then reboot. Refit! boot menu disappeared and Mac OS started booting.
Then I tried to comment it out. Reboot. Menu appeared, but, of course OS X was default OS.
Then I tried to uncomment "legacyfirst" and run enable.sh. All became Ok!

---

