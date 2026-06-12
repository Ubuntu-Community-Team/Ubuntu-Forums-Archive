---
title: "[SOLVED] executing a .py file?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-10-01
Hi,

I put the "rebuild_db.py" file on my iPod shuffle and it worked great for a while, but now whenever I open the .py file, in stead of giving me the option of executing it or displaying it it automatically opens with gedit. 

How do I change this so it will rebuild my directory??

sv

---

### Post by jordanmthomas on 2007-10-01
1.  make sure this is at the top of your script:
```
#!/usr/bin/python
```
2.  Ensure your script is executable.
```
chmod +x /path/to/script
```
or just right click on it and set the executable bit there.

If this doesn't work, there may be problems with how the iPod is mounted (it may not allow execution, for example)

---

### Post by staticvoid on 2007-10-01
Ok thank you, I will try that. For now I'll just use gtkPod :)

sv

---

### Post by irish_flu on 2007-10-01
You can also execute it from the command line:
```

python rebuild_db.py

```

---

### Post by staticvoid on 2007-10-03
aha! So I think I'll just set it to always open with "python" :D thanks.

sv

---

