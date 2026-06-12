---
title: "how do I make .sh files executable?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Baelari on 2008-03-04
What does sh stand for, and how do I make it executable?

---

### Post by jan quark on 2008-03-04
make it executable with
```

sudo chmod a+x /path/to/sh.script
```


> Shell Script Installer (.sh, .bash, ...)
    You can run the shell script inside a terminal with the command sh. If the script is called test.sh and is on the desktop of user carl, you can install it with sh /home/carl/Desktop/test.sh. Keep in mind that the script might not have permission to execute in your file-system. monkeyblog.org

---

### Post by Baelari on 2008-03-04
It doesn't give me any response. What does that mean?

---

### Post by lemmer on 2008-03-04
you can click with the right button of the mouse upon the file, go on properties and give the permissions (another sorry for my english....)

---

### Post by Chemroydal Tissue on 2008-03-04
I think this is what you want, but you weren't very specific:```
chmod +x /path/to/file.sh
```
Look [here]("http://en.wikipedia.org/wiki/Bash") and [here]("http://www.gnu.org/software/bash/manual/bashref.html") for information on Bash shell.

---

### Post by Oldsoldier2003 on 2008-03-04
> **jan quark said:**
> make it executable with
```

sudo chmod a+x /path/to/sh.script
```


 monkeyblog.org
or if you prefer the octal values (its good to know both because you often see the octal values used in tutorials)
```

sudo chmod 755 /path/to/sh.script
```

---

### Post by Baelari on 2008-03-04
Nothing I'm doing is working. It doesn't say it did something wrong, or successfully,or that it did anything at all... If I misspell it, it says no such directory.

```

angie@angie-laptop:~$ sudo chmod a+x /home/angie/Desktop/jarnal/jarnalannotate.sh
angie@angie-laptop:~$ sudo chmod 755 /home/angie/Desktop/jarnal/jarnalannotate.sh

```


also, what's the command to run stuff from the terminal?

---

### Post by teamkiller87 on 2008-03-04
That's it. You made it executable... Now to run it, navigate to the folder your file is in and run.

```
angie@angie-laptop:~$./name-of-file
```

---

### Post by Baelari on 2008-03-04
putting .script at the end makes it say no such directory...

---

### Post by Oldsoldier2003 on 2008-03-04
> **Baelari said:**
> Nothing I'm doing is working. It doesn't say it did something wrong, or successfully,or that it did anything at all... If I misspell it, it says no such directory.

```

angie@angie-laptop:~$ sudo chmod a+x /home/angie/Desktop/jarnal/jarnalannotate.sh
angie@angie-laptop:~$ sudo chmod 755 /home/angie/Desktop/jarnal/jarnalannotate.sh

```


also, what's the command to run stuff from the terminal?
If there is no input then you successfully completed the command
in order to run the script you mentioned above:
```

cd /home/angie/Desktop/jarnal
./jarnalannotate.sh
```

---

### Post by Baelari on 2008-03-04
```

./jarnalannotate.sh: line 14: 11828 Aborted                 (core dumped) java -Xmx192m -jar jarnal.jar -t templates/annotate.jaj -b "$1" "$2" "$3" "$4" "$5"
angie@angie-laptop:~/Desktop/jarnal$ 
```

time to find a different file?

what does $ signify?

---

### Post by Oldsoldier2003 on 2008-03-04
> **Baelari said:**
> ```

./jarnalannotate.sh: line 14: 11828 Aborted                 (core dumped) java -Xmx192m -jar jarnal.jar -t templates/annotate.jaj -b "$1" "$2" "$3" "$4" "$5"
angie@angie-laptop:~/Desktop/jarnal$ 
```

time to find a different file?

what does $ signify?
yes theres something wrong in the actual script.

the $ tells you you are a normal user, a # would mean you are root.

try this make a text file with this :
```
#!/bin/bash
# My first script

echo "Hello World!"
```
save it in your home directory as  "angie_first_script". No quotes,no extensions and use the underscores instead of spaces

then inn a terminal:
```
chmod 755 angie_first_script
```
you don't need sudo because the script was created by you and will belong to you

next make sure you are in the right place
```

ls -l
```

if you see your file you know you are right :) then

```
./angie_first_script
```

you should see Hello World! print out in your terminal

---

