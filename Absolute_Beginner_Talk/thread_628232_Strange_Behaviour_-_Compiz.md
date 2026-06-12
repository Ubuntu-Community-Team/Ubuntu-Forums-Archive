---
title: "Strange Behaviour - Compiz"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by AnandKM on 2007-12-01
Hi Friends,

I have enabled compfiz on my computer and it is wonderful.

I have 2 users on my desktop, myself and my wife.  I have the administrator rights and the compiz works perfectly for me.

However, when I tried to enable compiz for my wife in System >> Preferences >> Appearance - the machine says unable to activate.

Please help!

---

### Post by Martje_001 on 2007-12-01
If you do
```
compiz --replace
```
in a terminal, what do you see? Any errors?

---

### Post by AnandKM on 2007-12-02
Here is the result:

divya@anand-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

divya@anand-desktop:~$ 

I had to Ctrl-C to break out of the loop.

---

### Post by santiagoward2000 on 2007-12-02
> **AnandKM said:**
> Here is the result:

divya@anand-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

divya@anand-desktop:~$ 

I had to Ctrl-C to break out of the loop.

Hi!
If you're using an ATI card and the drivers in Ubuntu's repository, you'll need to install **xserver-xgl** to get Compiz working.

---

### Post by Gone fishing on 2007-12-02
If you reboot and go to your wifes account BEFORE you go to your account and enable compizfusion does it work?

I found this post and it looks possibly relevant [http://ubuntuforums.org/showthread.php?t=211029](http://ubuntuforums.org/showthread.php?t=211029)

---

