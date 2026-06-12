---
title: "I think i have this right...need a quick check"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by HcoJustin on 2007-06-18
I am trying to make a .sh file to take care of my compiling, and i was just wondering if anyone could check it over for me and tell me what i did wrong, if i did anything wrong.
 Thanks,
   ~HcoJustin
```
#!/bin/sh

cd /home/justin/Desktop/winterlove
pause

javac client.java
javac Cryption.java
javac Item.java
javac misc.java
javac Player.java
javac PlayerHandler.java
javac PlayerSave.java
javac SaveGameHandler.java
javac server.java
javac stream.java
pause

```

---

### Post by sickpuppet on 2007-06-18
Hi HcoJustin - 

Can't see anything wrong with that. You don't need the 'pause' commands. Are you getting errors when you run the script?

regards
Ben

---

### Post by Gwasanaethau on 2007-06-18
That looks good though I'm not sure about the 'pause' commands (I've never heard of them myself). Other than that it looks good!

Have you tested it yourself to see if it comes up with any errors?

EDIT: Beat me to it!!

---

### Post by trak87 on 2007-06-18
pause doesn't seem to be on my Ubuntu system, but as I recall we used the 'pause' command in batch files back in the days of MS-DOS.

Here's a Linux equivalent to the old DOS pause command:

```
echo -n "Press any key to continue..." && read -n 1
```

There's also the sleep command to pause the system for a certain number of seconds, three in this case:

```
sleep 3
```

---

### Post by HcoJustin on 2007-06-18
pause is still used in windows .bat files....i just wasn't sure if i needed them or not...as i am new to Ubuntu...when it compiles them...will it make them .class?, other than that...do i need to add anything else to make it run?...because i haven't even tested yet.


EDIT: I have tested it, and it works, thank you for your help.

---

### Post by Gwasanaethau on 2007-06-18
> **HcoJustin said:**
> pause is still used in windows .bat files....i just wasn't sure if i needed them or not...as i am new to Ubuntu...when it compiles them...will it make them .class?, other than that...do i need to add anything else to make it run?...because i haven't even tested yet.

You will probably need to give your script 'executable privileges', which will allow you to execute it as well as view it. You can do this by using:
```
chmod u+x [SCRIPTNAME]
```
substituting [SCRIPTNAME] for the filename of your script. You should then be able to run it with:
```
sh [SCRIPTNAME]
```

---

### Post by HcoJustin on 2007-06-18
i have the compiler part working, it is now getting it to run...i know i need...I think
```
#!/bin/sh

cd /home/justin/Desktop/winterlove

java <I dont know what to add here>
```

---

### Post by Gwasanaethau on 2007-06-18
> **HcoJustin said:**
> i have the compiler part working, it is now getting it to run...i know i need...I think
```
#!/bin/sh

cd /home/justin/Desktop/winterlove

java <I dont know what to add here>
```

You're pretty much there. All you need to do here is add the filenames for the java files you want to run, i.e.
```
java client
java Crypton
…
```

You don't need to put the '.class' suffix on them.

Hope it all works out for you now!

---

### Post by HcoJustin on 2007-06-18
Thank you very much!
 i have been trying to figure this out for a week or so, and i just remembered the forums like an hour ago.
 Thank you everyone for your help.

EDIT: one last question...when i run it, i get exception in thread "main" which i know means i don't have my variables set i think, but i was also wondering if i could use
```
java *.class
``` instead of each individual filename

---

### Post by bvanpelt on 2007-06-18
Please consider using Eclipse. Also, if you want to scripts things, you might consider using make...

---

### Post by Gwasanaethau on 2007-06-18
> **HcoJustin said:**
> Thank you very much!
 i have been trying to figure this out for a week or so, and i just remembered the forums like an hour ago.
 Thank you everyone for your help.

EDIT: one last question...when i run it, i get exception in thread "main" which i know means i don't have my variables set i think, but i was also wondering if i could use
```
java *.class
``` instead of each individual filename

I'm not sure, but I don't think you can, because when you write something like, for example:
```
java client.class
```
it comes back with the 'exception in thread "main"' error. It has to be run without the '.class' suffix, I'm afraid.

---

### Post by HcoJustin on 2007-06-18
i have tried those....and what i am doing atm is turning my .bat files into .sh, so i can use them.

---

### Post by HcoJustin on 2007-06-18
> **Gwasanaethau said:**
> I'm not sure, but I don't think you can, because when you write something like, for example:
```
java client.class
```
it comes back with the 'exception in thread "main"' error. It has to be run without the '.class' suffix, I'm afraid.

i didn't have the .class suffix, i only needed 1 out of my 10 files to run it....

---

