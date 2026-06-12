---
title: "How to search for a file"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by havedampton on 2007-04-10
How can I search my entire system for the location of a particular file?  Search seems to just search the current directory.

thanks

---

### Post by mand0 on 2007-04-10
One way would be to type in the Terminal:

```
find
```

Take a look [here]("http://www.pixelbeat.org/cmdline.html") under file searching.

---

### Post by Obor on 2007-04-10
Places menu - Search for files - and in "look in folder" choose File System or any mounted drive etc.

---

### Post by taurus on 2007-04-10
Applications -> Accessories -> Terminal
```
sudo find / -name **filename** -print
```

---

### Post by lamalex on 2007-04-10
or ```
sudo updatedb
sudo locate filename

```

---

### Post by TwoBit on 2007-04-12
>> Places menu - Search for files - and in "look in folder" 
    >> choose File System or any mounted drive etc.

That doesn't work. When you choose File System, it never finds anything. Not on my Nautilus 2.16.1 at least. It only finds anything when you give it a subdirectory such as /bin or /usr.

Once again, please, is there any way with the Nautilus GUI to search everything beneath root? If not then is there an alternative to Nautilus that does this? 

Thanks a bunch.

---

