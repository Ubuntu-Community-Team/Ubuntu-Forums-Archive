---
title: "Java Problem ~~~~~Help ~Urgent"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by 008325 on 2006-02-11
hello everyone

i can compile the java file by javac ( XXX.java )

but i can not run the file by java and it display the Exception

[COLOR="Red"]Exception in thread "main" java.lang.NoClassDefFoundError:[/COLOR]

i remember in the windows , that have something call classpath 

but i dont know how to set it in the Linux 

thx

---

### Post by Estariel on 2006-02-11
This probably  really dumb suggestion, but how do you try to run the program?
Do you type

java myprogram.java

or

java myprogram

?

The first one will deliver the error you just quoted...

---

### Post by 008325 on 2006-02-12
i type java program 

not java program.java 

i got the same problem in the windows

but i can set the classpath 

however , i don't  how to do that in the linux

---

### Post by Arktis on 2006-02-12
if it's a jar, try ```
java -jar filename.jar
```

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=008325]i type java program 

not java program.java 

i got the same problem in the windows

but i can set the classpath 

however , i don't  how to do that in the linux[/QUOTE]
```

$ export CLASSPATH=/path/to/classes

```
Also, I think there is a "--classpath" option on "java" program.
```

$ java --classpath /path/to/class program

```

---

### Post by bbqbaker on 2006-02-12
help me also!!!!!.


ive installed jdk, but now how do i use the javac command? when i type locate javac, this is what i get...

/usr/share/vim/vim63/syntax/javacc.vim
/usr/share/vim/vim63/compiler/javac.vim

now is this what i put in my bash? and after i save my bash file, how do i execute it? must i log out log in again?

---

### Post by bbqbaker on 2006-02-12
in addition to, i dont see java where i think it should be...alll i see is


/usr/lib/j2re1.5-sun/bin/java
/usr/lib/j2re1.5-sun/bin/java_vm
/usr/lib/j2re1.5-sun/bin/javaws


shouldnt there also be a /usr/lib/j2re1.5-sun/bin/javac ???????

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=bbqbaker]in addition to, i dont see java where i think it should be...alll i see is


/usr/lib/j2re1.5-sun/bin/java
/usr/lib/j2re1.5-sun/bin/java_vm
/usr/lib/j2re1.5-sun/bin/javaws


shouldnt there also be a /usr/lib/j2re1.5-sun/bin/javac ???????[/QUOTE]
Yeah, it looks like you are missing javac.  I don't think I installed Sun's, but I my javac is /usr/bin/javac.

---

### Post by bbqbaker on 2006-02-12
do you know if apt-get can install javac? if not, what did you d/l?


thanks

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=bbqbaker]do you know if apt-get can install javac? if not, what did you d/l?


thanks[/QUOTE]
It's been a while, but dpkg tells me I got it as part of the "sun-j2sdk1.5" package.  Not sure if I needed to enable extra repositories to get it, but it was definitely apt-able.

---

### Post by kaamos on 2006-02-12
Add the repo
> deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
and then just install sun-j2sdk1.5

---

### Post by bbqbaker on 2006-02-12
once again....THANKS A MILL!!!


now my next task....tomcat. lol

---

