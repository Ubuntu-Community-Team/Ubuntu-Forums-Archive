---
title: "Couple of Clam AV questions"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-02-04
If someone downloaded a virus/trojan/worm using GTK-Gnutella (which I did), and immediatly scanned the file with ClamAV (which I did), and it identified it (which it did),and I deleted the file; could the trojan have infected the XP OS on the second HD in my system?
From reading other posts, it doesn't seem that it would but I just wondered..
Also, should I have quarantined it instead of deleting it?
Another question: Does Clam get updates automatically, or is that a manual process?
Thanks-Milt

---

### Post by irish_flu on 2007-02-04
I don't know how the updates work, but I can tell you that you need not worry; your XP install would not be affected in such a circumstance.

---

### Post by Gerard Barberi on 2007-02-04
Updates should be automatic.
Type 'ps -e' in the terminal.  It will output all proccesses on your system.  You should see clamd and freshclam listed.  Clamd is the server and freshclam is the updater.

---

### Post by kpatz on 2007-02-04
99.99999% of all malware is written for, and only runs on, Windows.  Therefore, if you download a virus in Linux, you wouldn't be able to run it anyway, so it can't spread or do any damage.

---

### Post by Milt888 on 2007-02-04
> **irish_flu said:**
> I don't know how the updates work, but I can tell you that you need not worry; your XP install would not be affected in such a circumstance.

Thanks. I thought that was the case.

---

### Post by Milt888 on 2007-02-04
Yeah, now I see from the help section that it updated "signatures" yesterday.
I guess that's an automatic deal.

---

### Post by Milt888 on 2007-02-04
> **Gerard Barberi said:**
> Updates should be automatic.
Type 'ps -e' in the terminal.  It will output all proccesses on your system.  You should see clamd and freshclam listed.  Clamd is the server and freshclam is the updater.

Hey, thanks. clamd and freshclam are both there.
Good info.

---

