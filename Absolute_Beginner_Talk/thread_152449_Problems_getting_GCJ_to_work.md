---
title: "Problems getting GCJ to work"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by janki on 2006-03-29
I just installed the Java compiler GCJ using the Synaptic Package Manager. The problem is that when I try to compile a Java-file I get the following message:
**gcj: libgcj.spec: No such file or directory**

I tried to find a solution to my problem through a Google-search, but the closest I came up with is:
[http://cvs.savannah.nongnu.org/viewcvs/gcc/wwwdocs/htdocs/java/faq.html?rev=1.29#4_7]("http://cvs.savannah.nongnu.org/viewcvs/gcc/wwwdocs/htdocs/java/faq.html?rev=1.29#4_7")

Unfortunately I don't even know how to begin to "*configure both libgcj and gcj with the same "--prefix" directory*".

Does anybody have a simple recipe?

---

### Post by HokeyFry on 2006-03-29
I never could get gcj to work, though i never tried very hard. I just installed the JDK for linux and it works fine. If you dont know how to install it, PM me and I will give you detailed instructions.

---

### Post by kuppas on 2006-03-30
step 1:
Install gcj  to compile/executable from java source file
```
sudo apt-get install gcj
```

step 2:
Install development package
```
sudo apt-get install libgcj6-dev
```

step 3:
Install Just in Compile time, if you want to compile java into class file (byte code) and run
```
sudo apt-get install gij
```

step 4:
Now, write a small Java program HelloWorld.java 
```

public class HelloWorld {
  public static void main(String args[]) {
   System.out.println("Hello Ubuntu");
  }
}

```

step 5:
Compile the java file into class file (byte code)
```
gcj -C HelloWorld.java
```

step 6:
Run the compiled java file 
```
gij HelloWorld
```


-Kuppa

---

### Post by jacquesb on 2006-04-12
I have just started looking at it, and also ran into 
gcj: libgcj.spec: No such file or directory

The nice thing about gcj that it can compile to executable files. The executables can berun from a terminal comand line. Actually, there is a gnome-extension to create execuatbles that have a GUI.

The work around through gij does not deliver an executable but a class file. gij is a java virtual machine, similar to the onces provided by sun, in which class files can be runned.

I will try to install gcj following directions from 
[http://gcc.gnu.org/java/](http://gcc.gnu.org/java/)

and let you know if it works.

---

### Post by jacquesb on 2006-04-13
To avoid the error:
libgcj.spec: No such file or directory

install (with synaptic): 
libgcj6-dev

(tested -> worked)
see the thread on: 
Java problem (gcj-4.0)

---

