---
title: "[SOLVED] Unable to launch a program from Applications menu"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by VON_CAPO on 2007-12-21
I downloaded "HJSplit GUI for Java" and I can run it double clicking on it, but not from the Applications menu.

I set it to open with Java Sun 6 Runtime  from the Properties menu.

If I click on the file, it starts perfectly, but the problem is that I am unable to launch it from the launcher  I just created --->

[[IMG]http://img412.imageshack.us/img412/9361/screenshot1zq9.th.png[/IMG]](http://img412.imageshack.us/my.php?image=screenshot1zq9.png)

Any idea about what I am doing wrong? :confused:

---

### Post by PeterJS on 2007-12-21
> **VON_CAPO said:**
> I downloaded "HJSplit GUI for Java" and I can run it double clicking on it, but not from the Applications menu.

I set it to open with Java Sun 6 Runtime  from the Properties menu.

If I click on the file, it starts perfectly, but the problem is that I am unable to launch it from the launcher  I just created --->

[[IMG]http://img412.imageshack.us/img412/9361/screenshot1zq9.th.png[/IMG]]("http://img412.imageshack.us/my.php?image=screenshot1zq9.png")

Any idea about what I am doing wrong? :confused:

Yeah, nautilus is doing some MIME magic behind your back. For the launcher try:
```

java -jar "/home/fab/.HJSplit GUI for Java/hjsplit_g.jar"

```

---

### Post by VON_CAPO on 2007-12-21
> **PeterJS said:**
> Yeah, nautilus is doing some MIME magic behind your back. For the launcher try:
```

java -jar "/home/fab/.HJSplit GUI for Java/hjsplit_g.jar"

```
Success!!!
Thank you so much. :):):)

By the way, about the MIME magic (bug or feature?)... it is intriguing, where can I learn more about it?

---

### Post by PeterJS on 2007-12-21
It's a feature. MIME stands for **Multipurpose Internet Mail Extensions, **which is where the idea started but since then has been expanded to cover any system of describing the contents of a file.  Every file has a mime type that describes what it is, for some MIME Types it's pretty easy to correctly guess what they are. In this case nautilus is able to correctly recognize that the file is a Java jar, and then sets the default action when you double click on it to open it with java. This is the same mechanism it uses to know to open pictures in and image view, etc.

---

