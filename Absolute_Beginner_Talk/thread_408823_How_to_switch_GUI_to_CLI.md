---
title: "How to switch GUI to CLI ?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by henry0712 on 2007-04-13
I want to switch GUI to CLI in the process of initiating or using. Should I change the init level?
thanks.

---

### Post by Seisen on 2007-04-13
Are you trying to say that you just want use a CL and get rid of gui or use the CL w/ the GUI?

---

### Post by sonny on 2007-04-13
I don't think I get the question, but if you are already in a sesion you have to press "Ctrl"+"Alt"+"F1" to get to a real terminal, go that way through out "F6", then "F7" would leave you back in the GUI session.

If you want to change the way your session starts you have to do it in the options button at the GDM (the login screen).

---

### Post by henry0712 on 2007-04-13
Thank you.

I want to use the CLI at the beginning of starting ubuntu Desktop instead of GUI. How can I configure it.

---

### Post by Falados on 2007-04-13
I don't know if there is an easy way to do that. However you can change your default runlevel to 3 instead of 5.  This run level traditionally doesn't start X.  If there is no way to do this in a GUI tool, you can edit /etc/inittab and change the runlevel from 5 to 3

---

### Post by Sef on 2007-04-13
> I want to use the CLI at the beginning of starting ubuntu Desktop instead of GUI. How can I configure it.

At the log in screen, you can change it.  It is under the options menu.

---

### Post by ncappel1 on 2007-06-19
> **Falados said:**
> I don't know if there is an easy way to do that. However you can change your default runlevel to 3 instead of 5.  This run level traditionally doesn't start X.  If there is no way to do this in a GUI tool, you can edit /etc/inittab and change the runlevel from 5 to 3

I think that in feisty the 2-5 runlevels are all the same by default, aren't they?

---

### Post by Znupi on 2007-06-19
At the login screen hit Ctrl+Alt+F2, login, and type
```

sudo /etc/init.d/gdm stop

```
to stop the graphical UI.
Hope that helps :).

---

