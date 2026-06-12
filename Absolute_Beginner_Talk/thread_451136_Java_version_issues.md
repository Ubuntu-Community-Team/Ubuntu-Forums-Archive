---
title: "Java version issues"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by trenog on 2007-05-22
Hello. I was trying to compile a simple Hello.java program however it doesn't work and gives me the following error:

```
Exception in thread "main" java.lang.NoClassDefFoundError: Hello
```

I was checking the versions when I found something that was out of place

```

trenog@trenog-desktop:~/workspace/helloworld$ java -version
java version "1.5.0_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_10-b03)
Java HotSpot(TM) Client VM (build 1.5.0_10-b03, mixed mode)
trenog@trenog-desktop:~/workspace/helloworld$ javac -version
javac 1.6.0

```

The weird part with all of this is that is used to run when I tried it out in Eclipse some time ago but now even then it doesn't work. Perhaps I touched something as Eclipse talks about Java version 1.5.0_06.

Also, in case this helps, this is the config I've got

```
trenog@trenog-desktop:~/workspace/helloworld$ sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
      4        /usr/lib/j2re1.5-sun/bin/java
*     5        /usr/lib/jvm/java-6-sun/jre/bin/java

```

```
trenog@trenog-desktop:~/workspace/helloworld$ sudo update-alternatives --config javac


There are 2 alternatives which provide `javac'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/lib/jvm/java-6-sun/bin/javac
      2        /usr/lib/jvm/java-1.5.0-sun/bin/javac

```

Can anyone figure out my Java woes?

---

### Post by deadgobby on 2007-05-22
I am going through Java right now. I been using Text Editor to able to edit with.
 Then I save it has myworld.html and open it with FF. If you type it in and want to learn the code. Too many spaces can cause nothing.

---

### Post by trenog on 2007-05-22
Okay then, did a little reading and fiddling and figured out that the reason for the different versions is because of the links within the usr/bin directory so I changed them around to my 1.5.0_06 version but I'm still getting the same problem.

Also, I tried installing 1.6.0_01 but when I linked the java and javac files I got an error that said that the object class couldn't be found or something...huh?

EDIT:

The error is specifically (when I set the links in the bin directory to point to the 1.6.0_01 versions:

```

trenog@trenog-desktop:~/workspace/helloworld$ java -version
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
trenog@trenog-desktop:~/workspace/helloworld$ javac -version
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

```

---

### Post by h0ax on 2007-05-22
based on the fact you're writing a hello world program, I'm assuming this is your first Java program.
Could you post it? -- Perhaps there is an error there?

---

### Post by h0ax on 2007-05-22
Well I wanted to help you but I am falling fast asleep, so sorry.

Make sure you have named your files right.  If you have
public class Name{ } - your filename should be Name.java [it is case sensitive]
then javac filename.java
java filename.java

sorry I couldn't stay up longer!

---

### Post by trenog on 2007-05-22
```
public class Hello {
	
	public Hello() {
		int i = 0;
	}
	
	public static void main(String[] args) {
		
		System.out.println("The message has changed");
		//Hello welcome = new Hello();
	}
	
}
```

It's very simple and it worked at one point...I just am not sure what's wrong now

---

### Post by trenog on 2007-05-22
Or can anyone direct me in how to get Java 6 or Java 5 working normally? I guess I would need the jdk and jre because I'm going to be doing some programming on my box. Perhaps a new attempt at installing the products would fix whatever problems exist right now.

---

