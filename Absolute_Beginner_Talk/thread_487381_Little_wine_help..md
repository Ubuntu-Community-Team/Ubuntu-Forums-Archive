---
title: "Little wine help."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-06-29
Ok, I got wine from getdeb.net and installedit.

I downloaded NittoLegends from nittolegends.com and placed it on my desktop.

I opened terminal cd Desktop and got:
```

root@admin:/home/admin/Desktop# wine NittoLegendsBet00930.exe
wine: could not load L"c:\\windows\\system32\\NittoLegendsBet00930.exe": Module not found

```

---

### Post by cogadh on 2007-06-29
That error indicates that Wine could not find the .exe in the directory you were trying to launch it from and therefore assumed it must be in Wine's fake "system32" directory. Of course, it also didn't find it there.

Is the username you used when you downloaded the .exe really "admin"? If it isn't then you were in the wrong desktop folder and that is what caused the error. Also, did you run "winecfg" after you installed Wine? If not then you need to in order to set up your drives, sound and graphics correctly.

---

### Post by Canis familiaris on 2007-06-29
> **phizikal said:**
> Ok, I got wine from getdeb.net and installedit.

I downloaded NittoLegends from nittolegends.com and placed it on my desktop.

I opened terminal cd Desktop and got:
```

root@admin:/home/admin/Desktop# wine NittoLegendsBet00930.exe
wine: could not load L"c:\\windows\\system32\\NittoLegendsBet00930.exe": Module not found

```
Try 
```
wine ./NittoLegendsBet00930.exe
```

---

### Post by Canis familiaris on 2007-06-29
> **phizikal said:**
> Ok, I got wine from getdeb.net and installedit.

You installed from getdeb? 
If nothing even works now I thing you should remove wine and install wine by Add/Remove. Just search for it in Add/Remove, check it and apply. It will not only install wine but also many wine tools which are pretty useful.

---

### Post by bodhi.zazen on 2007-06-29
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

That *might* be too much help :twisted:

---

