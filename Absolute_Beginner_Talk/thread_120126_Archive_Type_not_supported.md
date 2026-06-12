---
title: "Archive Type not supported?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by ve6hba on 2006-01-20
I was trying to install "fp-linux-ws.rpm"
I got this message: "Archive Type not supported"

What does this mean?
Thanks VE6HBA

---

### Post by dueY on 2006-01-20
You have to use ALIEN to convert .rpm to .deb

I believe the command is ```
sudo alien -k [name of file.rpm]
```

---

### Post by ve6hba on 2006-01-20
I get the sam eresult if I try and install the converted *.rpm file.
The new file now is "fp-linux-ws.deb"
The error is the same: "Archive Type not supported"

Thanks VE6HBA

---

### Post by cwaldbieser on 2006-01-21
[QUOTE=ve6hba]I get the sam eresult if I try and install the converted *.rpm file.
The new file now is "fp-linux-ws.deb"
The error is the same: "Archive Type not supported"

Thanks VE6HBA[/QUOTE]
If you type:
```

$ file fp-linux-ws.deb

```
What type of file does the system think it is?

---

