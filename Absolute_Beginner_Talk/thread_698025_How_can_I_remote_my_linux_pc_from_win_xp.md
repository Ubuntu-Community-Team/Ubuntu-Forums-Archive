---
title: "How can I remote my linux pc from win xp?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Usta_AsH on 2008-02-15
Hello I am not looking for only ssh I want desktop remote.I tried RealVNC, Tightvnc and NX.I think I am unsuccessful to install these 3 softwares so will you prefer me such a program?

---

### Post by fatality_uk on 2008-02-15
> **Usta_AsH said:**
> Hello I am not looking for only ssh I want desktop remote.I tried RealVNC, Tightvnc and NX.I think I am unsuccessful to install these 3 softwares so will you prefer me such a program?

Did you enable remote access on your Linux desktop?
Enter this into a terminal and then setup from there if you didn't

> vino-preferences

VNC should work well then

---

### Post by Usta_AsH on 2008-02-15
> **fatality_uk said:**
> Did you enable remote access on your Linux desktop?
Enter this into a terminal and then setup from there if you didn't



VNC should work well then

bash: vino-prefences: command not found

---

### Post by Prospero2006 on 2008-02-15
apt-get install vino

---

### Post by Usta_AsH on 2008-02-15
ok I have spelling mistake I opened that screen and configured. I could conect it unless I reset my linux it is in login page right now(looked at screen) but I cannot log in. I want to login from startup.

---

### Post by Usta_AsH on 2008-02-15
is there any way to put it startup?

---

### Post by HermanAB on 2008-02-15
Likely the best way to access Linux from Windoze is with Xming and PuTTY:
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by Usta_AsH on 2008-02-15
> **HermanAB said:**
> Likely the best way to access Linux from Windoze is with Xming and PuTTY:
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

I said I don't want ssh programs.

---

### Post by FreakTech on 2008-02-15
All you need to do is go to System->Preferences-> Remote Desktop.  Set your preferred setting.  On the XP box install tightVNC and then you should be able to connect.

---

