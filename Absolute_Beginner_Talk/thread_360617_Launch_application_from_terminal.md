---
title: "Launch application from terminal?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by ChrisR on 2007-02-13
Is there a command to launch an application from the terminal?

For example if I want to open a text file in gedit, can I launch it from the terminal?

I read somewhere else that the command was "open" but it didn't seem to work for me.

Thanks.

---

### Post by 23meg on 2007-02-13
You can just type ```
gedit /path/of/file
```

---

### Post by ChrisR on 2007-02-13
ahhh!

Thank you!

---

### Post by MikeDX on 2007-02-13
> **23meg said:**
> You can just type ```
gedit /path/of/file
```

Another thing to consider is that if you want to keep your terminal unlocked, follow your command with the & symbol such as:

```
gedit /home/usr/file &
```

Which will launch gedit and still allow you to enter further commands into your terminal before gedit closes.

---

### Post by 23meg on 2007-02-13
If you'd like to open a file with its associated application from the terminal, use *gnome-open* followed by the file path.

---

