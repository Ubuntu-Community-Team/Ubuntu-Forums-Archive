---
title: "Open, darn you, open!"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-10-07
Ok, so I download Frostwire from their website.  It opens with an installer and instals just fine, but when I go to click on it, nothing happens.  What did I do? Download the icon?

---

### Post by Anonii on 2006-10-07
Open the terminal and execute : **frostwire**

Post the output here; thanks!
[SIZE="1"]
Edit: Take that Matt.H :P[/SIZE]

---

### Post by Old Pink on 2006-10-07
Run it in terminal and paste me the output. :)

**EDIT: **Beat me, Anonii. ;)

---

### Post by picpak on 2006-10-07
Java isn't correctly configured. This guide will help you out:

[http://www.ubuntuforums.org/showthread.php?t=176442](http://www.ubuntuforums.org/showthread.php?t=176442)

(Note: After Step 2.1, make sure you run *sudo apt-get update* .)

---

### Post by OptimusPrime on 2006-10-07
bash: /usr/share/applications/frostwire.desktop: Permission denied

---

### Post by Frak on 2006-10-07
> **OptimusPrime said:**
> Ok, so I download Frostwire from their website.  It opens with an installer and instals just fine, but when I go to click on it, nothing happens.  What did I do? Download the icon?
Oh, please listen I HAD THE EXACT SAME PROBLEM, go to Add/remove, Internet, show unsupported/commercial(both) and get BLACKDOWN JAVA and JAVA RUNTIME ENVIROMENT. When that works post a reply to this one please.

---

### Post by ian.l on 2006-10-07
Try launching it from the terminal. Try typing "Frost" then hit tab to see if it autocompletes the command for you. Try it lower-case: "frost" or even just "Fro" and "fro".

In Linux most user installed program executables reside in /usr/bin but you should be able to launch it without having to use the absolute path. Also, check the permissions on the executable to make sure execute permissions are enabled. If not, you might have to sudo chmod +rwx <filename> before you can execute it.

---

### Post by Anonii on 2006-10-07
> **ian.l said:**
> Try launching it from the terminal. Try typing "Frost" then hit tab to see if it autocompletes the command for you. Try it lower-case: "frost" or even just "Fro" and "fro".

In Linux most user installed program executables reside in /usr/bin but you should be able to launch it without having to use the absolute path. Also, check the permissions on the executable to make sure execute permissions are enabled. If not, you might have to sudo chmod +rwx <filename> before you can execute it.

[I]Try launching it from the terminal. Try typing "Frost" then hit tab to see if it autocompletes the command for you. Try it lower-case: "frost" or even just "Fro" and "fro".
[/I]

Wouldnt it be easier to just say "Try launching it from the terminal with the command "frostwire" ? 
Minimalism helps, to avoid confusion.

---

### Post by OptimusPrime on 2006-10-07
I'm getting the same problem, it just doesn't open.

---

### Post by OptimusPrime on 2006-10-07
wesley@wesley-laptop:~$ frostwire
: command not found:
: No such file or directory
: command not found1:
: command not found5:
'unFrost.sh: line 26: syntax error near unexpected token `{
'unFrost.sh: line 26: `look_for_java() {
wesley@wesley-laptop:~$

---

### Post by Frak on 2006-10-07
> **OptimusPrime said:**
> wesley@wesley-laptop:~$ frostwire
: command not found:
: No such file or directory
: command not found1:
: command not found5:
'unFrost.sh: line 26: syntax error near unexpected token `{
'unFrost.sh: line 26: `look_for_java() {
wesley@wesley-laptop:~$
You have to change the file from using sh to use bash.
When I remember how to do that I will post back.

---

### Post by Anonii on 2006-10-07
[U]sudo nano /usr/bin/frostwire
[/U]
Change the #!/bin/sh to */bin/bash*

[U]sudo nano /usr/lib/FrostWire/runFrost.sh
[/U]
Change the #!/bin/sh to */bin/bash*


I may have messed up the directories. If they are not the right ones, please post back.

---

### Post by warjowuch on 2006-10-12
This all sucks, I can't still open this thing. Can't find java, and bin/bash does also not work. By the way, should it also be uncommented, so:

# !/bin/sh, goes to
/bin/bash, or does it go to
# !/bin/bash, or to:
# /bin bash ??

---

### Post by Arby on 2006-10-12
#!/bin/sh goes to #!/bin/bash. That isn't a comment symbol it's a special case called a shebang line (from hash bang). You will see it a the top of scripts in many languages such as perl/python etc. It tells the system where the language (in this case bash) interpreter is located. If you want to check the location of your bash interpreter type 'which bash'. It should return the path to bash.

Before you start changing that though: leave the first line as #!/bin/sh and try this. If you are trying to run a file called runFrost.sh, cd into the directory that contains that file and type 'sh runFrost.sh' The sh tells bash to behave as if it were sh, this is how I usually run files with .sh extensions. If that doesn't work you can try changing that first line.

Although the behaviour you are observing is quite strange. I am however quite confused by this thread, lots happening at once. Could you summarise where you have got to and what you have tried so far.

Also, if you are having issues with java there is a good guide here [https://help.ubuntu.com/community/Java?highlight=%28java%29]("https://help.ubuntu.com/community/Java?highlight=%28java%29")

---

### Post by RanDinCarolina on 2006-10-12
You also need to check to see if the correct java runtime envirionment is being used. I think the command is

```
java
```

in a terminal. I am at work so this is probably not right.

But that's how I got mine to work after I changed the bin/bash thingie.

---

### Post by Ben Sprinkle on 2006-10-12
```

ls

```
Find it then.
Then type:
```

sudo frostwirename
```

---

