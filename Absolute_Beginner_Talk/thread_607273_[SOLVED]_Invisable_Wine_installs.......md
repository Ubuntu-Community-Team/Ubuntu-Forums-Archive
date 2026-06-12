---
title: "[SOLVED] Invisable Wine installs......?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by spideygal on 2007-11-08
My installs are invisible from terminal, says there is no such directory and this happens if I run from shell or desktop. However if I use alt + F2 and run the exact command. It will open up my wine installs.

 /home/sg/.wine/drive_c/Program Files/Macromedia/Fireworks 8/

Why can I not find them in terminal?

---

### Post by pissedoffdude on 2007-11-08
> **spideygal said:**
> My installs are invisible from terminal, says there is no such directory and this happens if I run from shell or desktop. However if I use alt + F2 and run the exact command. It will open up my wine installs.

 /home/sg/.wine/drive_c/Program Files/Macromedia/Fireworks 8/

Why can I not find them in terminal?

You need to put it in quotations so your command would be something like ```
wine "/home/sg/.wine/drive_c/Program Files/Macromedia/Fireworks 8/fireworks.exe"
```

---

### Post by spideygal on 2007-11-08
> **pissedoffdude said:**
> You need to put it in quotations so your command would be something like ```
wine "/home/sg/.wine/drive_c/Program Files/Macromedia/Fireworks 8/fireworks.exe"
```

Worked like magic!

Thanks and marked solved.

---

