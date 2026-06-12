---
title: "Nitto1320 on wine."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-06-29
Ok, I have downloaded and fully installed wine on my Dapper. I downloaded the zip  files onto my desktop and extracted it there.

I have a 1320c152S.exe file on my desktop

I used terminal with root and got.

```

root@admin:/home/admin/Desktop# wine 1320c152S.exe
wine: could not load L"c:\\windows\\system32\\1320c152S.exe": Module not found

```

I am sure this isn't hard to fix, please and thank yous.

---

### Post by phizikal on 2007-06-29
no help?

---

### Post by Seisen on 2007-06-29
Perhaps this might explain it.

[http://www.winehq.org/pipermail/wine-users/2006-April/021266.html]("http://www.winehq.org/pipermail/wine-users/2006-April/021266.html")

---

### Post by reset3x on 2007-06-29
> **phizikal said:**
> no help?

You have to set the path to your desktop... Or you can open winefile and navigate to it if you'd like to point and click....

---

### Post by phizikal on 2007-06-29
I did cd my desktop. look at the code.

---

### Post by phizikal on 2007-06-29
I found the problem, 
```

$ chmod +x 1320v152S.exe

```

---

