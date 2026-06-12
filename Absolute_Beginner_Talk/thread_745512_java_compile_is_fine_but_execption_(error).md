---
title: "java: compile is fine but execption (error?)"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by christinak on 2008-04-04
Heyhey!

I should be programming java for next week, but somehow, I am not sure my java is working ok (or maybe I just need another package...?)

The tutor sent us a certain program as an example and even this is not working: it compiles fine, but then when i try to execute it, this error comes 

Exception in thread "main" java.lang.NoClassDefFoundError: java.util.Scanner
   at BasicIO.main(BasicIO.java:7)

 and the first 7 lines of the program are



import java.util.Scanner;

public class BasicIO{

	public static void main(String[] args){
		
		Scanner sc = new Scanner(System.in);
		
		int x;
		
		System.out.println("please type variable 'x': ");
		
		x = sc.nextInt();



what am i doing wrong? (and where can i download new packages for java or whatever the problem may be?)

many many thanks!
christina

---

### Post by neurostu on 2008-04-04
Scanner was introduced in Java 5. What version of java are you using?

---

### Post by neurostu on 2008-04-04
In the future you should probably refer questions of this sort to your TA, as this forum is mainly for linux support.

---

### Post by christinak on 2008-04-04
well, I thought i had java 5 - seeing that I followed the download instructions on the course homepage - or do i not?

when i type java -version, this comes:

java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

thanks so much for your help.

---

### Post by neurostu on 2008-04-04
can you post the entire error message and all of the code you are tyring to run but do it insidet code and /code tags so it gets formated correctly,

Example  [-code-]  word [-/code-] -->
```

word

```   (but without the hyphens)

---

### Post by christinak on 2008-04-04
you mean like this? (i had been wondering how to do that but never gotten around to finding out)

```

java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by Crafty Kisses on 2008-04-04
You can download more packages from Synaptic, but are you using Jedit still? I remember your old post about Jedit, did you ever get that working?

---

### Post by christinak on 2008-04-04
No. :( I'm really at loss because i don't even know where to look for the error. (but as I said before, there are alternatives that do work, so it's ok - ... one day, i will work that out as well, though.)

---

### Post by neurostu on 2008-04-04
Yep exactly like that.
Can you post the entire error message?

Can you post all of the code in the .java file?

---

### Post by christinak on 2008-04-04
is there a difference between synaptic and adept manager?

---

### Post by christinak on 2008-04-04
so the .java code is this (with comments in german)

```


import java.util.Scanner;

public class BasicIO{

	public static void main(String[] args){
		
		Scanner sc = new Scanner(System.in);
		
		// ----------- HIER DEN PROGRAMMCODE EINGEBEN ----------
		
		int x;
		
		System.out.println("Bitte geben sie einen Wert fuer 'x' ein:");
		
		x = sc.nextInt(); // Programm blockiert u. wartet auf Eingabe
		
		System.out.print("Sie haben fuer x den Wert '");
		System.out.print(x);
		System.out.println("' eingegeben");
		
		
	}
}


```

and then i just type javac BasicIO.java, which worked fine, however, after i type java BasicIO
 this comes 
```
 

$ java BasicIO
Exception in thread "main" java.lang.NoClassDefFoundError: java.util.Scanner
   at BasicIO.main(BasicIO.java:7)

```

---

### Post by Crafty Kisses on 2008-04-04
> **christinak said:**
> No. :( I'm really at loss because i don't even know where to look for the error. (but as I said before, there are alternatives that do work, so it's ok - ... one day, i will work that out as well, though.)

I'm not sure what you're trying to do with Java, like making apps or what not, but you may want to look into Eclipse.

---

### Post by neurostu on 2008-04-04
So I tried the following:
```

slayton@stockton-mini:~/java$ javac BasicIO.java
slayton@stockton-mini:~/java$ java BasicIO 
Bitte geben sie einen Wert fuer 'x' ein:
2
Sie haben fuer x den Wert '2' eingegeben
slayton@stockton-mini:~/java$ 

```
and it worked fine. So the code is fine. 

are you sure you are typing:
```

javac BasicIO.java
java BasicIO

```
correctly?

If you are then you have a libraries problem...

---

### Post by neurostu on 2008-04-04
If you don't have the scanner class present then it shouldn't compile...

this is a weird error....

But I'm sure it has a very simple solution ;-)

---

### Post by christinak on 2008-04-04
yeah, that's what I thought, sort of. (I'm typing everything correctly.)

how do you solve a libraries problem? I had initiallly installed version 6, then, as I was having problems with jedit, removed it and installed version 5 - I hope that went fine - in any case, i have not a clue as to where to start looking even. :(

---

### Post by christinak on 2008-04-04
it is bizarre, really.

i don't know enough about java to be able to say if this means anything but if i read input with 
```

Integer.parseInt(args[0]);

```

it does work - but then maybe that the version before scanner came out? *confused* :)

---

### Post by christinak on 2008-04-04
.... and i just wrote a longer program - that again compiles and that'S it - with a longer error: the code of the program being (sorry if the programming is bad - i'va avoided it for way too long)

```


import java.util.Scanner;

// ---- Klassennamen aendern und Datei unter dem gleichen Namen abspeichern ---
public class Quotient{

	public static void main(String[] args){
		
		Scanner sc = new Scanner(System.in);
		
		int x;
		int i;
		i= 0;
		x= -3;

		while (x<=0 && i<4) 
		{
		System.out.println("Bitte geben Sie einen positiven Wert fuer x ein ");
		x = sc.nextInt();	
		i=i++;
		}

		if (i<4)
		{
		x=x/10;
		System.out.print("'x' durch 10 ist ");
		System.out.println(x);
		}
		else
		{
		System.out.print("'x' muss positiv sein");
		}		
	}
}



```

and then the error is 

```


$ java Quotient.java
Exception in thread "main" java.lang.NoClassDefFoundError: Quotient.java
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: Quotient.java not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)


```

---

### Post by christinak on 2008-04-05
sorry about the code above, typed Quotient.java (thats what happens when you don't stop when you're too tired.)

anyway, found a solution under 

[http://blog.csmonkey.com/2007/06/how-to-make-sun-java-5-default-java.html](http://blog.csmonkey.com/2007/06/how-to-make-sun-java-5-default-java.html)


thanks again for all your help!

---

### Post by forrestcupp on 2008-04-05
So it compiles *and* runs correctly now?

---

### Post by christinak on 2008-04-12
(sorry the late answer - problem solved so i didn't check any more)

anyway - YES! it compiles, the program works afterwards and as a plus jedit started working as well. *very very happy with all that*

---

