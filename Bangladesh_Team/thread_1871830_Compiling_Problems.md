---
title: "Compiling Problems"
date: 2011-10-29
forum: Bangladesh Team
---

### Post by arif.cse28 on 2011-10-29
I've recently installed Ubuntu 11.10 64-bit.

I'M FACING SOME PROBLEMS....!!!....

1.
  After installing Geany my *.cpp/*.c (which is in other drives ) are not running, but it's compiling.

the terminal is showing
 "./geany_run_script.sh: 5: ./ ( name of program ) : Permission denied "

but the program which is saved in home directory is running.

but the .java files are running from any drive in geany.

2.  
  i could not make compile any .java file from Terminal
by giving the command
"javac *.java"

how could i solve the  problems.

Give me some suggestions soon.
PLZ

---

### Post by ashickur.noor on 2011-10-29
For Java please check have you install sun-jdk,sun-jre correctly?
For C do you have write permission on those drive?

---

### Post by arif.cse28 on 2011-10-29
how can i see whether i've permission for write or not in a drive?

---

### Post by ashickur.noor on 2011-10-29
> **arif.cse28 said:**
> how can i see whether i've permission for write or not in a drive?
Can you create a new file or folder on that drive?

---

### Post by forhan on 2011-11-02
1.Make sure your source code (*.cpp or *.c file) is in a directory where you have write permission.For example you can copy your file and paste it in home folder or desktop .

Now open the file using geany.compile it.then build it.Now execute it.It will definitely run.

2.Make sure you have jdk installed.To do so,run in the termin:
javac
If jdk is installed,it will show you instructions to compile source code.If not,it will show "The program 'javac' can be found in the following packages:"
*some package names,etc

If not installed,you can follow this installation guide:
[http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/](http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/)

Hope that helps.

---

