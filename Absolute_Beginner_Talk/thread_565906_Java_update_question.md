---
title: "Java update question"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by moose4204l on 2007-10-02
I have an older java version.  /usr/lib/j2se/1.4/bin/java

and i need the newest java version in order to compile a program i am working on. my questions are:

-is there anyway to update to the newest java version from a command line?
-does the update overwrite the existing java or does it create a new file or whatever on my system and would i have to remove the other folder?

thanks

---

### Post by tlink on 2007-10-02
you should be able to "apt-get install j2re1.4" or some variant of that.  Not sure if it would overwrite or not.

---

### Post by capitalistpiglet on 2007-10-02
to update to the latest jdk
```

sudo apt-get install sun-java6-jdk

```
I dont think it will remove the old jdk but after its installed you should be using the new jdk. To check run
```

javac -version

```
Once you have the latest jdk it should be 1.6.0 .

---

### Post by zvacet on 2007-10-02
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")


I don´t think it will overwrite it.

---

