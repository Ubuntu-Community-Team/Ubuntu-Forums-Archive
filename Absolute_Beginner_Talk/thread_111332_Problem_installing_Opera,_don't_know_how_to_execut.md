---
title: "Problem installing Opera, don't know how to execute"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by cafevincent on 2006-01-02
So far all software I've needed were available in apt-get but it doesn't seem to have opera in there so I downloaded the archive from opera.com and extracted it. Now I don't know how to launch it. There is a file bin/opera that is marked executable but doubleclicking it does nothing. Help! Also where should I copy the contents of the archive? I mean where does ubuntu usually store installed programs?

---

### Post by Perfect Storm on 2006-01-02
Add:

[b]# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free[/b]

to your sourcelist.

Then

```

sudo apt-get install opera

```

Now you can start opera with writting **opera** in the terminal or making an application launcher.

---

### Post by cafevincent on 2006-01-02
Thanks!

---

### Post by Madpilot on 2006-01-02
Just for future reference:

[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

:p

---

