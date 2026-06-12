---
title: "Installing jdk"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-08-17
I've decided I want to learn Java 2  programming and I d/l'ed the linux version of it but it's a bin file.  I tried doing this:

 chmod a+x jdk-1_5_0_07-linux-i586.bin
 sudo jdk-1_5_0_07-linux-i586.bin

and get this:

sudo: jdk-1_5_0_07-linux-i586.bin: command not found

So I looked around a little more and found this:

 sudo aptitude install jdk-1_5_0_07-linux-i586.bin

which gives me this:

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "jdk-1_5_0_07-linux-i586.bin"


I can get it working in Winders (the windows version), but I want to be able to do it in Ubuntu...

Also, I'm gonna need a little help too once I get it installed to put it in my path...So maybe we could kinda kill two birds with one stone here so to speak and someone could kinda help me out with both questions?

Thanks in advance.

~* Ash

---

### Post by taurus on 2006-08-17
```

sudo ./jdk-1_5_0_07-linux-i586.bin

```

---

### Post by magnoliablossom on 2006-08-17
thanks for the help. :)

---

### Post by magnoliablossom on 2006-08-17
I believe I've installed the JDK in Ubuntu but when I do "java -version" it gives me the version of the JRE I have.  Now I found this telling me how to set my path:

[http://www.ubuntuforums.org/showthread.php?t=63893&highlight=jdk+path](http://www.ubuntuforums.org/showthread.php?t=63893&highlight=jdk+path)

However, those directories that it points to are not there.  So, how do I find where the jdk is on my computer and the right path to set it to?

---

### Post by wvslkr on 2006-08-18
I'm guessing here, but if it is not in the default system path and is installed, probably in your home folder.  

I may me totally off but at least this will bump and someone may know for sure:)

---

### Post by magnoliablossom on 2006-08-18
thanks...but i checked there already....np...i'll just use it in windows.

---

