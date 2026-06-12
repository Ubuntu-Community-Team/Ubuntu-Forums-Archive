---
title: "setting the default jre"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by No_Germs on 2005-11-08
my breezy has several jres on it. currently the default one is 1.4, while i would like it to be the 1.5 jre that's also installed. i've managed to configure several applications to use the 1.5 jre, but still when i try to open a JAR, it uses the 1.4.
how do i set the default JRE? I know that in windows you do it by setting the java path system variable...

---

### Post by Xian on 2005-11-08
Like this & select from list:

```
$ sudo update-alternatives --config java
```

---

### Post by No_Germs on 2005-11-08
the three options i get are all for 1.4 jre's...
i'm sure i also have the 1.5 jre... i've double checked it to be sure...

---

### Post by Xian on 2005-11-08
How did you install jre1.5? 
Was it from source, an official Ubuntu package or other?

There's a how-to at the wiki: [Installing Sun Java](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

---

### Post by No_Germs on 2005-11-08
i've installed the 1.5 jre this way:
i've downloaded it from sun's website and followed the instructions there (on sun's website)... what can i do to correct this problem?

---

### Post by manicka on 2005-11-08
I installed 1.5 through  these repos

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by No_Germs on 2005-11-08
ok, it worked out... thanks :)
one thing- firefox still uses the 1.4 version (i know that because i get a major-minor exception)... how do i change that?

---

### Post by jeremy on 2005-11-08
sudo update-alternatives --config java

---

### Post by sunshineboy on 2008-07-03
good guy .Awesome!

---

