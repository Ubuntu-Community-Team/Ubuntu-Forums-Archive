---
title: "Java 1.4 on PPC?"
date: 2004-11-02
forum: Apple PPC Users
---

### Post by thalavoy on 2004-11-02
Hello,

Is Java 1.4 (JRE/JDK) available on PPC yet? Thanks

Siva

---

### Post by berndtj on 2004-11-02
Well, sun doens't make it but IBM does.  Check out the IBM developer site for their java SDK.  I just got it installed about an hour ago, and so far, so good.  I downloaded the rpm version and used alien to install the package.  Once installed you will have to update your $PATH, but that's about it.

Now, if I could only get eclipse installed!!!

Here's the info:

[http://publib.boulder.ibm.com/infocenter/db2help/index.jsp?topic=/com.ibm.db2.udb.doc/start/c0010331.htm](http://publib.boulder.ibm.com/infocenter/db2help/index.jsp?topic=/com.ibm.db2.udb.doc/start/c0010331.htm)

---

### Post by stereo on 2004-11-03
hi,

are you running java1.4 with JIT enabled?
with the "processor-setting to typ 6" java is running with jit on my debian. but X is crashing. perhaps it'll work on ubuntu.
any luck to build eclipse?

---

### Post by berndtj on 2004-11-03
Well, I just lost my eth0 adapter, so I've got other issues to deal with before eclipse.  I'm running a laptop, so I plug in where ever, or wirelessly.  It seems that if I get my ibook configured for one, it breaks the other.

Oh well, this is my linux crash course.

I have instructions on recompiling the x86 build for ppc, so we'll see if it works out.

Berndt

---

### Post by stereo on 2004-11-04
hi,
do you have a link to your recompile instructions?

---

### Post by SyL on 2004-11-04
Hi,
I tried to install the IBMJava2-ppc-142 for running eclipse. 
java version "1.4.2"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2)
Classic VM (build 1.4.2, J2RE 1.4.2 IBM build cxppc32142-20040917 (JIT enabled: jitc))

But I can't do anythink whitout the JVM make a core file :
 javac /home/syl/tmp/OrderStateAction.java
JVMDG217: Dump Handler is Processing Signal 4 - Please Wait.
JVMDG303: JVM Requesting Java core file
JVMDG304: Java core file written to /opt/IBMJava2-ppc-142/javacore.20041104.141619.11926.txt
JVMDG215: Dump Handler has Processed Exception Signal 4.
Instruction illégale

Anybody have an idea ?? :D

---

### Post by Viro on 2004-11-05
That's a problem with IBM's JVM. It seems to run fine in text mode, but anything GUI related causes a crash.

Sorry, I have no idea how you'd solve it.

---

### Post by SyL on 2004-11-09
[QUOTE=Viro]That's a problem with IBM's JVM. It seems to run fine in text mode, but anything GUI related causes a crash.
 [/QUOTE] 
 The JVM 1.4 crash also when I do a simple compilation in text mode

---

### Post by SyL on 2004-11-09
The only SDK which run on my powerbook g4 12" is the IBMJava2-ppc-131. All version of the 1.4 crash
   
   grrrrr
    
    ](*,)
  
  a know problem with the PB G4 12" 1,33 GHz?

---

### Post by SyL on 2004-11-09
You can bypass the problem by forcing the JVM to use code for a specific CPU model, like this :
   
    ```
export JITC_PROCESSOR_TYPE=6
``` 
   
   
   thank to Michael Rex
   [http://www.rexi.org/linux/eclipse-ppc.html]("http://www.rexi.org/linux/eclipse-ppc.html")
  
  
  :mrgreen:

---

### Post by Viro on 2004-11-14
Finally got Java working by following the instructions laid out in the wiki. thanks guys.

---

