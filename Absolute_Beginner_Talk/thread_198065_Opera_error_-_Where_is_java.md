---
title: "Opera error - Where is java?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-16
I get the lovely error message: 

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

when I open opera in console.  In wiki it says to go to java options and give it a path to my java program.  My question is where can I look for mine, and what kind of file/program is it?

---

### Post by bruce89 on 2006-06-16
It isn't installed, but it can be installed by doing ```
sudo aptitude install sun-java5-jre
``` in the terminal.

---

### Post by WADemosthenes on 2006-06-16
Alright, now I think I just have to give opera the path to the file/program.  Where can I find it (the default didn't work).

---

### Post by WADemosthenes on 2006-06-16
Okay found it, it was in the jvm file.

---

### Post by bruce89 on 2006-06-16
Why does Opera require Java?

---

### Post by xael on 2006-06-16
[QUOTE=bruce89]Why does Opera require Java?[/QUOTE]
Good question. They say they require Java because 

>  Some sites use Java to offer interactive content on Web pages. If you do not have Java installed, Opera will automatically offer to take you to a download site when you encounter such content. Disable Java if you do not want to run Web-page Java applets on your computer. 

---

### Post by Copter on 2006-06-27
to save some time: after installing java using Automatix valid java path :
```


/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/
```
or something very similar

copter :]

---

### Post by alingatong on 2006-07-20
IS this normal for opera to open in a separate window the java applets embedded in webpages? Because that is happening in my opera. When I use fluxbox even a separate java applet window is not opening. This really sucks.

---

### Post by Captus on 2006-07-27
I'm not sure if this is the propper way to do it BUT, this is how I made java work with Opera installed with Automatix.

```

1. Open /usr/bin/opera with your prefered editor.
2. Locate the line 'for SUNJAVA in \'. 
- For me it was on line 104 
3. Add this line AFTER 'for SUNJAVA in \'
- 'jvm/java-1.5.0-sun-1.5.0.06/jre \'
NOTE: This might be different on your system.
Use: ls /usr/lib/jvm/ to see what your version is
4. Exit and save.
5. create or open the file /etc/ld.so.conf
6. Add this line:
- /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/
NOTE: this line might be different on your sysem
7. Exit and save.
8. run: ldconfig

```

Voilla, works for me.

---

### Post by TheRingmaster on 2006-09-25
> **Captus said:**
> I'm not sure if this is the propper way to do it BUT, this is how I made java work with Opera installed with Automatix.

```

1. Open /usr/bin/opera with your prefered editor.
2. Locate the line 'for SUNJAVA in \'. 
- For me it was on line 104 
3. Add this line AFTER 'for SUNJAVA in \'
- 'jvm/java-1.5.0-sun-1.5.0.06/jre \'
NOTE: This might be different on your system.
Use: ls /usr/lib/jvm/ to see what your version is
4. Exit and save.
5. create or open the file /etc/ld.so.conf
6. Add this line:
- /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/
NOTE: this line might be different on your sysem
7. Exit and save.
8. run: ldconfig

```

Voilla, works for me.
I am scared to try this.

has anyone else had success with this?

---

### Post by Colonel Kilkenny on 2006-09-27
I have no idea what are you guys doing.
Are you trying to say to Opera where Java is by editing /usr/bin/opera?
If so, then try first ctrl+F12 -> Advanced -> Content -> Java options.

And Opera does not require Java. At least I don't think it does. It just checks whether there is plugin present for Java. In first post there is not -> it says "ignored". Completely normal.

---

### Post by dannyboy79 on 2006-09-27
what they are trying to do is enable java within opera just like I am! I am trying to play poker online at a certain website and it requires java to run. I can't get it to work?? I have xubuntu installed an when I go to tool, preferences, then content, then java blah blah blah, it asks for the location of the java install file and I can't find it?? This is all per the opera website instructions.

---

