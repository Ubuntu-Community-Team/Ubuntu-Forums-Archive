---
title: "Adept"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by cyberlite on 2006-10-28
Hi all

Every time I try to upgrade a progam with adept I get this
"Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one"

I have tried to restart my computer but it did not help, and I cant see a other adept progam running , any help???????

thx

---

### Post by justaguynpc on 2006-10-28
In a case like this, I would uninstall your current adept, ensuring it was a complete removal, then reinstall. 

 I never use adept in KDE, I quickly install synaptic (gnome package with dependencies).  I find it faster and more "stable" than adept.

Cheers

---

### Post by Jucato on 2006-10-28
> **cyberlite said:**
> Hi all

Every time I try to upgrade a progam with adept I get this
"Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one"

I have tried to restart my computer but it did not help, and I cant see a other adept progam running , any help???????

thx

Type in this command in Konsole:

```
sudo dpkg --configure -a
```

Then try again.

---

