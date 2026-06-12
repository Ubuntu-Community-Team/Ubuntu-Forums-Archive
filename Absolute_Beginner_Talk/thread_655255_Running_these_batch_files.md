---
title: "Running these batch files"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Stanyer on 2008-01-01
Hello.

I am a windows user but i am going to be purchasing a ubuntu VPS (If i am able to do the following)

I need to know if and how to run these windows batch files in ubuntu.

```

@echo off
COLOR 0c
title PKScapeX V1 Server Compiler
"C:\Program Files\Java\jdk1.6.0_02\bin\javac.exe" -cp . *java
pause

```

And

```

@echo off
color 0c
title PKScapeX V1
java -cp .;./classes; server

```

If anyone could let me know how these would be executable in an ubuntu os that would be much appreciated.

---

### Post by Xavieran on 2008-01-01
If this is in BASIC I think you might need to do a bit of tweaking to get them usable...

P.S. What do they do? I may be able to write a python script to do the same...

---

### Post by Stanyer on 2008-01-01
The first one compiles JAVA Files in the directory of the batch file into CLASS files.

The second executes the CLASS files and in turn runs the runescape private server.

---

### Post by nick_h on 2008-01-01
If you install the java packages then you will be able to run the java and javac commands.  The syntax is very similar.

---

### Post by Stanyer on 2008-01-01
Does an ubuntu server run exe files like so i can download the java jdk executable file?

---

### Post by Stanyer on 2008-01-01
Bump ^-^

---

### Post by nick_h on 2008-01-01
> Does an ubuntu server run exe files like so i can download the java jdk executable file?

You would install the packages sun-java6-jre and sun-java6-sdk.  This would give you the java and javac executables.

---

### Post by Stanyer on 2008-01-01
And in turn the files i posted in the first post would run perfectly?

Would the file extension still be .bat?

---

### Post by Stanyer on 2008-01-01
And in turn the files i posted in the first post would run perfectly?

Would the file extension still be .bat?

---

### Post by .nedberg on 2008-01-01
> **Stanyer said:**
> And in turn the files i posted in the first post would run perfectly?

Would the file extension still be .bat?

No, they would not run. But you could very easily write bash-scripts that would do the same. .bat and .exe are Windows only (sort of), in Linux you have different files that do the same

---

### Post by Stanyer on 2008-01-01
Thats the whole point of this thread, how would i run them. :D

---

### Post by Stanyer on 2008-01-01
Bump. Threads go down quickly here =/

---

### Post by Xavieran on 2008-01-01
Can you please explain to me what and why the batch file does what it does?

What do you actually want done,there could be another solution not involving batch files...

---

### Post by Stanyer on 2008-01-01
The first one compiles JAVA Files in the directory of the batch file into CLASS files.

The second executes the CLASS files and in turn runs the runescape private server.

---

### Post by nick_h on 2008-01-01
Your shell scripts will be very simple:
```
#!/bin/bash
/usr/bin/javac -cp . *java

```
and
```
#!/bin/bash
/usr/bin/java -cp .:./classes server

```

The commands title and color in the Windows batch file just set the title of the window and colour of the text and background.

You could set these in Ubuntu by running the script in an xterm.
```
xterm -title "PKScapeX V1" -fg red -bg black -e /home/user/script.sh
```

Without knowing exactly what your java programs do it would be impossible to say if they would work perfectly.  The best way would be to just try them.

---

### Post by linux noooob on 2008-02-04
I am guessing this is to run moparscape? if so could you please tell me if it works! 

(note: maybe if i am right you should stick with the problem with the .sh file that is given for linux but doesn't work)

---

