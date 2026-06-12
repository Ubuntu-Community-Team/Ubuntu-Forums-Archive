---
title: "[SOLVED] conky problem"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by rob1984 on 2007-12-23
ive just installed conky and got a nice ~/.conkyrc from the forums but i have a problem:

if i start conky from the terminal, it closes when i close the terminal.
if i set it as a startup program, it loads before my desktop and then closes when the desktop loads.

ideally i would like conky to startup automatically and stay up.

can anyone help me?

---

### Post by jonward690 on 2007-12-23
Well I don't really use conky but I no if you run it from the terminal it will close when you close the terminal so you have to go to run and run it.Oh yea and how loads before your desktop I donno how you do this but you have to set a delay on when it runs.I would google it and see if you find some help there.

---

### Post by ÜbuntuMensch on 2007-12-23
You need to write a small script and have that run in your Startup Programs. This I am getting from some threads here...such as [http://ubuntuforums.org/showthread.php?t=205865&highlight=conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky) which is all things conky.

so...in terminal:

[INDENT]sudo gedit .conkyon.sh[/INDENT]

or whatever you want to call it. the . before keeps it hidden and the .sh is the extension for a shell script.

then enter this text to the document you have just created:
[INDENT]
#!/bin/bash
sleep 40 && conky;[/INDENT]

sleep causes a delay, allowing the window dressings to load first.
save and close.

make this an executable file by in terminal:

[INDENT]chmod a+x .conkyon.sh[/INDENT]

now to System>Preferences>Sessions

to Add a new Startup Progarm

Name: Conky
Command: /home/yournamehere/.conkyon.sh
Comment: gets my Conky on


easy as pie.

---

### Post by rob1984 on 2007-12-24
cheers, that works a treat!

---

### Post by Abu_Dayya on 2007-12-24
> **ÜbuntuMensch said:**
> 
to Add a new Startup Progarm

Name: Conky
Command: /home/yournamehere/.conkyon.sh
Comment: gets my Conky on


easy as pie.

So, should I add this command instead of just 'conky'"

Thanks

---

### Post by rob1984 on 2007-12-24
yea, you wanna put the path to the shell script you just created instead of the path to conky.

---

### Post by Abu_Dayya on 2007-12-24
> **rob1984 said:**
> yea, you wanna put the path to the shell script you just created instead of the path to conky.

Gotcha !

---

### Post by Dr Small on 2007-12-24
Starting conky from the following command, would have worked, when you close the terminal:
```
conky&
```

---

### Post by rob1984 on 2007-12-27
oh yeah, cheers.

i had forgotten about the '&'

---

