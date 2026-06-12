---
title: "synaptic"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by moheganer2 on 2007-07-25
recently while using synaptic I received a message dpkg was interrupted you must run dpkg-configure -a to correct.when i run this is comes back command not found.i have rebooted but symantic always starts with same message and is useless unless fixed.Anyone with similar problem with advice or solution?

---

### Post by meierfra on 2007-07-25
The correct command is

```
dpkg --configure -a
```

dpkg is followed by a space and two dashes.

---

### Post by trak87 on 2007-07-25
> dpkg-configure -a

There isn't a dpkg-configure command, so maybe you meant "dpkg --configure -a" ??

---

### Post by Bozodog on 2007-07-25
I have the same problem.
I type dpkg --configure -a in the Konsole, and the message that is returned is
dpkg: requested operation requires superuser privilege

How do I become a 'Superuser'!

---

### Post by overdrank on 2007-07-25
> **Bozodog said:**
> I have the same problem.
I type dpkg --configure -a in the Konsole, and the message that is returned is
dpkg: requested operation requires superuser privilege

How do I become a 'Superuser'!

The command is 
```
sudo dpkg --configure -a
```

---

### Post by moheganer2 on 2007-07-25
I think you have to type sudo in front of the command to be superuser- it will then ask for your password and you can proceed.

---

### Post by Bozodog on 2007-07-25
Thank you very much.

Tried this and it worked.  It's just as you suggested.

[http://ubuntuforums.org/showthread.php?t=509167](http://ubuntuforums.org/showthread.php?t=509167)

Thank you again.  Now I understand why.

---

