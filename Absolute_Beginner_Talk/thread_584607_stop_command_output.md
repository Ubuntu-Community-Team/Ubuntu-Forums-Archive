---
title: "stop command output"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-21
basically I want a way of running any command without the command outputting anything in the terminal. for example I could run wget something.xml and not have it give all the details as to what it is doing but still save the xml file

thanks :)

saamon

---

### Post by sintoris on 2007-10-21
You can run wget with the option -o /dev/null

---

### Post by ssaamon on 2007-10-21
thanks :)

---

### Post by ssaamon on 2007-10-21
just wondering what is /dev/null ?

is it just an empty file? or is there something special about it?

---

### Post by Vixis on 2007-10-21
In Unix-like operating systems, /dev/null or the null device is a special file that discards all data written to it (but reports that the write operation succeeded), and provides no data to any process that reads from it (it returns EOF). In Unix programmer jargon, it may also be called the bit bucket or black hole.

---

