---
title: "Removing Startup Items In KDE"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-09-30
I recently, put a dock in KDE Autostart and made it executable via chmod -x <name of dock> and now I want to remove it, I have deleted the file from Autostart but it still starts, how do I stop it?

Calv

---

### Post by wieman01 on 2006-09-30
Delete the file from here?
> /home/your_user/.kde/Autostart/

---

### Post by calvinthomas on 2006-09-30
I have done that but it still starts!

Calv

---

### Post by wieman01 on 2006-09-30
What program is it... KXDocker?

---

### Post by calvinthomas on 2006-09-30
Its Kooldock

---

### Post by wieman01 on 2006-09-30
Ok, wouldn't it be best if you uninstalled it? Since you don't seem to need it any longer. And if you cannot install it simply remove the program by deleting the executables & the folders.

---

### Post by jaboua on 2006-09-30
KDE might remember it being started and autostart it (session management) - close the dock, and then the session should be saved when you log out.

If you don't want KDE to autostart applications that were open last time you logged out, it can be disabled some place in kcontrol.

---

### Post by wieman01 on 2006-09-30
> **jaboua said:**
> KDE might remember it being started and autostart it (session management) - close the dock, and then the session should be saved when you log out.

If you don't want KDE to autostart applications that were open last time you logged out, it can be disabled some place in kcontrol.
Good point... Totally forgot about that. See screenshot then. That's how you disable it.

---

### Post by calvinthomas on 2006-09-30
Thankyou!

Calv

---

