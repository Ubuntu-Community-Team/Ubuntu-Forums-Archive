---
title: "Unpack jar files"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by matemargo on 2007-03-09
Which repository I have to add to be able to install the jar tool?
I've tried with **apt-get install jar** but I get this error:

```

E: Couldn't find package jar

```

Thanks.

---

### Post by Perfect Storm on 2007-03-09
Jar is part of Java, so you need to install Sun Java 1.5 or 1.6

---

### Post by Songwind on 2007-03-09
Can't Ark or the gnome archive manager open jar files?  They're just renamed .zip files.

---

### Post by Perfect Storm on 2007-03-09
Yes, but I'm not quite sure what he wants and what it is. If it's just to extract and nothing else file-roller that is installed by default should do it.

---

### Post by matemargo on 2007-03-09
I'm accessin through SSH, so I need a CLI tool to unpack the files.
I have installed JDK 1.5 but the jar command isn't recognized.

---

### Post by Perfect Storm on 2007-03-09
```
java [-options] -jar jarfile [args...]
```

---

### Post by matemargo on 2007-03-09
I don't want to run a jar, I want to unpack it.
I need to edit some text files inside a jar... so I want to unpack, modify and pack again.

---

### Post by Perfect Storm on 2007-03-09
Well;
The one that works for me is;
jar -xvf *.jar

But you said jar isn't working?

What does 
```
java -version
```
say?

---

