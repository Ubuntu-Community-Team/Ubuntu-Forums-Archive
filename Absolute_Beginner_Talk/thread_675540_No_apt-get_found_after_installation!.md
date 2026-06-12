---
title: "No apt-get found after installation!"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by sonyisme on 2008-01-22
7.1.0 Desktop i386. I installed this on my vista via Virtual PC 2007.

After installation, I'm able to get online. But cannot use apt-get command.

-bash-3.00$ sudo apt-get
sudo: apt-get: command not found
-bash-3.00$ which apt-get
/usr/bin/which: no apt-get in (/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/usr/X11R6/bin:/usr/NX/bin)
-bash-3.00$ sudo apt
sudo: apt: command not found
-bash-3.00$

---

### Post by PurposeOfReason on 2008-01-22
While I doubt this, try typing 'gksudo synaptic' and looking for apt-get and install it or use sudo appitude install apt-get.

---

### Post by ajmorris on 2008-01-22
> **sonyisme said:**
> 7.1.0 Desktop i386. I installed this on my vista via Virtual PC 2007.

After installation, I'm able to get online. But cannot use apt-get command.

-bash-3.00$ sudo apt-get
sudo: apt-get: command not found
-bash-3.00$ which apt-get
/usr/bin/which: no apt-get in (/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/usr/X11R6/bin:/usr/NX/bin)
-bash-3.00$ sudo apt
sudo: apt: command not found
-bash-3.00$

hi there, can you please go into Synaptic Package Manager and see if it works to download packages from there.
You could also try using aptitude install as opposed to apt-get

---

### Post by ajmorris on 2008-01-22
> **PurposeOfReason said:**
> While I doubt this, try typing 'gksudo synaptic' and looking for apt-get and install it or use sudo appitude install apt-get.

beat me to it :P

---

