---
title: "Cant get a .sh file to run"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by Yautja_Ender on 2006-02-17
So like the post says, cant get the .sh file to run... ive typed 

sh filename.sh 

in the command prompt and it comes up with no such file or directory... i have the file on my desktop... is that a problem.... then i tried 

sudo sh filename.sh but that did nothing.... help me please ... lol sorry im a newb

---

### Post by austin on 2006-02-17
seems you did not make sure you are in the directory where the .sh file is!?

If it is on your desktop try to cd to ~/.Desktop or similar. Use your tab-key in order to make the shell complete the path- and filenames you type, e. g. .De and than tab. So you know if you are going in the right direction.

---

### Post by heimo on 2006-02-17
This is how I'm used to run shell scripts.

Make sure it's executable.
```
chmod u+x filename.sh
```

Run it.
```
./filename.sh
```

---

### Post by patrick295767 on 2006-02-17
[QUOTE=Yautja_Ender]So like the post says, cant get the .sh file to run... ive typed 

sh filename.sh 

in the command prompt and it comes up with no such file or directory... i have the file on my desktop... is that a problem.... then i tried 

sudo sh filename.sh but that did nothing.... help me please ... lol sorry im a newb[/QUOTE]
You may:
```
chmod +x script.sh              # to make it executable
./script.sh                                   # to run it 
```


script.sh content:
```
#!/bin/bash
echo "Hello, this is my first script"
```
  
Check the permissiosn too

Kind regards, 

Pat'

---

### Post by Yautja_Ender on 2006-02-17
Ok, thanks.... i just moved it to my home folder and it worked fine like that... for some reason it wouldt work off my desktop... i cd'd to it but it still wouldnt find it

---

### Post by kvorion on 2006-02-17
[QUOTE=Yautja_Ender]Ok, thanks.... i just moved it to my home folder and it worked fine like that... for some reason it wouldt work off my desktop... i cd'd to it but it still wouldnt find it[/QUOTE]


Make sure that you are working from the same directory where you have the .sh file. Make sure that it is executable, and it will definitely work. Like everybody else said, do the chmod first. There are two ways to execute a shell script...

either add the sha-bang and the beginning of your file
```
#!/bin/bash
your code
```

and just type at your prompt 

```
./script.sh
```

Here is where you have to make sure that you are in the correct directory

else just say

```
bash script.sh
```

---

