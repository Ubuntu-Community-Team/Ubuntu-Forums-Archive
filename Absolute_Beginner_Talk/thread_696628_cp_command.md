---
title: "cp command"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by zoomiest on 2008-02-14
I was just stretching my (very small) Linux muscles, at the command line, and found that I could, very quickly, search my entire system for a specific file type with the find command: ```
 find -name *.jpg
```

Which is very useful. **Is there a way to use the cp command to now copy all file of a certain type OUT of an entire directory tree?** I tried a few things, but didn't work. For example, copy all .png files out of my system to a particular directory?

cp *.png /home/allan/PNG didn't work.

Thanks in advance.

---

### Post by jan quark on 2008-02-14
```
cp /path/to/cd-drive/* /path/to/new/location/
```

try this it is just an 
example

and in the signature there is a begginer command tutorial
 in which I collect useful terminal commands I find in this forum

---

### Post by kpkeerthi on 2008-02-14
```

find /path/to/search -name *.png -exec cp '{}' /home/alan/PNG ';'

```

---

### Post by jan quark on 2008-02-14
that's another one which goes into the repository :)

---

### Post by kpkeerthi on 2008-02-14
repository?

---

### Post by emarkd on 2008-02-14
Maybe using xargs:

```
find -name *.png | xargs -i cp { } /home/me/PNGS
```

Disclaimer:  NOT TESTED ;)

---

### Post by jan quark on 2008-02-14
> repository? 

just joking 
I meant my small [repository]("http://laiconic.quotaless.com/commandtut.html")

---

### Post by zoomiest on 2008-02-14
> **kpkeerthi said:**
> ```

find /path/to/search -name *.png -exec cp '{}' /home/alan/PNG ';'

```

Awesome. One last question... is that "{}" literal or is that a blank that I should fill in?

---

### Post by Cypher on 2008-02-14
The {} is indeed literal, the "find" command will fill it in for you. This syntax has always been a little confusing to me (i.e., I can never remember is properly) so I'm always prone to using 'xargs' as previously mentioned..
```

find . -type f -name "*.jpg" | xargs cp /home/alan/PNG

```

---

### Post by kpkeerthi on 2008-02-14
Its a literal and is part of the **find** command. It will be replaced by the 'file' that the find command finds.

---

### Post by zoomiest on 2008-02-15
```
find /path/to/search -name *.png -exec cp '{}' /home/alan/PNG ';'
```
This one worked seemlessly. I think I don't understand the xargs well enough.

Thanks!

---

