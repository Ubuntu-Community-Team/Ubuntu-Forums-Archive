---
title: "[SOLVED] python trouble"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by weezy8802 on 2008-03-07
i have been in some tutorials and save the programs that it had me write the same way it told me to. Now i have tried to run the programs the exact way it said to and is always giving me "no such file or dir" Any help on this matter.

---

### Post by Daveth on 2008-03-07
linux is case sensitive, so make sure your commands are in the correct case. Might also be worth navigating to where the files actually are and try running the terminal command with the exact path in place. Just a thought.

---

### Post by JoshuaRL on 2008-03-07
What IDE are you using?

---

### Post by Ricky93 on 2008-03-07
Are you in the right directory?

Are you using the command:      python (file name.py)?

replace the brackets with the file name.

---

### Post by weezy8802 on 2008-03-08
i am in the right dir and can actually see the file in the dir but when i try to open it it tells me its not a file or dir. its weird.:confused:

---

### Post by Belliinator on 2008-03-09
I know its really noob (and embarrasing) but I can't load save a script either. How do you save an run a .py file from the command line.

I think this is what the tutorial byte of python saying to do, but I get all these errors 

```

>>> #!usr/bin/python
>>> # Filename : helloworld.py
>>> print "Hello, world!"
Hello, world!
>>> python helloworld.py
SyntaxError: invalid syntax
>>> chmod a+x helloworld.py
SyntaxError: invalid syntax

```

Please help me. This is really bad.

---

### Post by erginemr on 2008-03-09
No problem.

You seem to have forgotten just one slash:
Instead of
```
#!usr/bin/python
```
try:
```
#!/usr/bin/python
```

---

### Post by erginemr on 2008-03-09
Alternatively, for a more general approach, you can write:
```
#! /usr/bin/env python
```
which eliminates the necessity of knowing where the python interpreter is, and lets the envionment variables handle its correct path.

---

### Post by erginemr on 2008-03-09
> **weezy8802 said:**
> i have been in some tutorials and save the programs that it had me write the same way it told me to. Now i have tried to run the programs the exact way it said to and is always giving me "no such file or dir" Any help on this matter.

In Linux CLI, you need to refer to a program (or shell script) that exists in the same directory by:
```
./<program_file>
```
So, for isntance, if the name of your script is "fubar", then first you need to make sure that it is executable:
```
chmod u+x fubar
```
and run it with:
```
./fubar
```
Otherwise, the system will not "see" it but instead will look for an executable "fubar" inside the directories defined by the PATH variable.

---

### Post by Belliinator on 2008-03-09
Thanks,
but there are still some errors!?!
```

>>> #!/usr/bin/python
>>> # Filename : helloworld.py
>>> print "Hello, world!"
Hello, world!
>>> python [COLOR=Red]helloworld[/COLOR].py
SyntaxError: invalid syntax
>>> chmod [COLOR=Red]a[/COLOR]+x helloworld.py
SyntaxError: invalid syntax
>>> 

```(The highlighted syntax is what IDLE highlighted.)

Edit: Oh sorry. You posted a simpler way, at the same time I posted.
But It still didnt work

```

>>> #! /usr/bin/env python
SyntaxError: invalid syntax

```

---

### Post by igknighted on 2008-03-09
judging by your prompt, you are in idle (the python command-interpreter shell).  You need to be in bash (the normal shell).  You should see a $ for your prompt.  From there you can run your program.

---

### Post by Belliinator on 2008-03-09
> **igknighted said:**
> judging by your prompt, you are in idle (the python command-interpreter shell).  You need to be in bash (the normal shell).  You should see a $ for your prompt.  From there you can run your program.

Cool now in terminal, but is it saving it using that code:
```

>>> #! usr/bin/env python
... print "hello world"

```

And how do I run it?
```
>>> python helloworld.py

```
Didn't run it.

Thanks for your help!

---

### Post by igknighted on 2008-03-09
If your prompt looks like this >>>, then you are not in the terminal.  It should say [username@hostname ~]$.  Also, you need to write that file in a normal text editor, not IDLE.  Gedit (applications -> accessories -> text editor) is the easiest, but nano is easy as well (and CLI based).

---

### Post by Belliinator on 2008-03-09
Yes! I got it to work! Thankyou!

I thought you meant run the commands in the terminal python command line
You mean just the terminal, and the editor was gedit. (come to think of it, Ive tried this before)

Where do reccommend I save .py files in the future? At the moment I saved mine in /usr/bin/ because the help file mentiond something about it.

Thanks again.

---

### Post by BandD on 2008-03-09
I wouldn't save them in /usr/bin.  That is usually the place where all the binary code that all your programs are made up of is stored.  I jsut save all my python scripts in a 'Python Scripts' folder I made in my home folder. But you can save them anywhere that is convient for you!

---

### Post by Belliinator on 2008-03-09
> **BandD said:**
> I wouldn't save them in /usr/bin.  That is usually the place where all the binary code that all your programs are made up of is stored.  I jsut save all my python scripts in a 'Python Scripts' folder I made in my home folder. But you can save them anywhere that is convient for you!

Oh my goodness! Ill save them some where else, thankyou!

---

### Post by erginemr on 2008-03-09
One final bit of advice:

You can also use IDLE to write your scripts as you write them in gedit or any other text editor. For that, you can use New or Open... from the main menu of IDLE, and save your file (preferably in a subfolder of your choice under your home) and run it with F5.

IDLE has a few advantages over generic text editors such as code coloring (gedit does that too) code completion and testing the script on the fly.

Another fantastic programmer's editor is geany:
[http://geany.uvena.de/](http://geany.uvena.de/)

You can try it with:
```
sudo aptitude install geany
```

---

### Post by weezy8802 on 2008-03-09
i read some different tutorials and found my mistake, i was saving files with a space instead of an underscore. i quess i will leave the thread open until the other issue is resolved.

---

### Post by erginemr on 2008-03-10
> **weezy8802 said:**
> i read some different tutorials and found my mistake, i was saving files with a space instead of an underscore. i quess i will leave the thread open until the other issue is resolved.

FYI, you can run programs with spaces by enclosing them with single or double quotes. So,
```
python ./"word1 word2"
```
should work.

---

