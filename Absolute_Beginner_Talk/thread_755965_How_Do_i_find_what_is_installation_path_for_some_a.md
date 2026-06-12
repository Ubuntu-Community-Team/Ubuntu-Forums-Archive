---
title: "How Do i find what is installation path for some application binary(executable) files"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-04-15
Hi
I installed some packages from the internet and now I want to find out what is the path that the files are installed, for example where does it binaries are located, is there any way to do this?
I remember that there was a way to find out how much JDK are installed and also that way we could see the path for each installation, also we could add our own item to those installation.

I am looking for similar command for other Linux applications.

Thanks.

---

### Post by Jesuses Left Leg on 2008-04-15
If I understand what you mean you can use which to locate binaries.

For example 
```

matt@matt-laptop:~$ which firefox
/usr/bin/firefox

```

---

### Post by Biggy on 2008-04-15
/home/biggy  ( View > check Show Hiden Files )

---

### Post by Inxsible on 2008-04-15
most of the binaries for any software go into /usr/bin.

Again, the which command is great to find out the exact path, as already mentioned.

---

### Post by xeth_delta on 2008-04-15
Another option:
```
whereis application_name
```

---

