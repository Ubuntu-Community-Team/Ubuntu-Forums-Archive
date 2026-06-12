---
title: "Some /usr/include files missing?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by rashby on 2007-01-11
I am starting to port an application from AIX to Xubuntu.

The makefiles I am porting have a number of header file dependencies that I am having problems with. Here are a few of them:

/usr/include/va_list.h
/usr/include/sys/m_types.h
/usr/include/stdarg.h

None of these files are in my /usr/include.

NOTE: I did run "apt-get install build-essential", which (I think) populated my /usr/include with a lot of the standard include files.

What I am wondering is: Is there something else I need to do to get these include files, OR are they not needed in Xubuntu, OR are they someplace else (other than /usr/include)?

Thanks very much.

---

### Post by Bachstelze on 2007-01-11
Have you installed the headers matching you current running kernel ?

```
sudo apt-get install linux-headers-$(uname -r)
```

---

