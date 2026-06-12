---
title: "Modify shell startup script in .profile?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by jefft113 on 2007-08-31
Hey guys, Im kinda new and Ive never tried to modify my .profile before and it doesnt seem to be doing what it is suppose to. I just installed a statistics program(Stata10), it runs fine, but I have to run it out of the directly its located. Their book states there should be a way to modify the shell script so that I can run it from my home directory. Heres what the book says:

> 
If you use bash, sh, ksh, there is a line in your .profile that looks like:
PATH = "/bin:/usr/bin:/usr/local/bin:$HOME/bin"
Edit the line and add /usr/local/stata to the list:
PATH = "/bin:/usr/bin:/usr/local/bin:$HOME/bin:/usr/local/stata"


I am not sure exactly what they are talking about, I have been opening .profile with emacs, and the closest thing I can find is:

```
PATH=~/bin:"{$PATH}"
```

I have tried to add what I need to this, but I cannot get it to work, I am not sure if I am even putting it in the right place. Help please?

---

### Post by lloyd_b on 2007-08-31
> **jefft113 said:**
> Hey guys, Im kinda new and Ive never tried to modify my .profile before and it doesnt seem to be doing what it is suppose to. I just installed a statistics program(Stata10), it runs fine, but I have to run it out of the directly its located. Their book states there should be a way to modify the shell script so that I can run it from my home directory. Heres what the book says:



I am not sure exactly what they are talking about, I have been opening .profile with emacs, and the closest thing I can find is:

```
PATH=~/bin:"{$PATH}"
```

I have tried to add what I need to this, but I cannot get it to work, I am not sure if I am even putting it in the right place. Help please?

Try adding the following line the file "~/.bashrc":
```
PATH=$PATH:/usr/local/stata:
```
then, close the current terminal window, open a new one, and see if it works.  This assumes that the program in question is in "/usr/local/stata", of course.  If it's somewhere else, modify that path as required.

Lloyd B.

---

### Post by jefft113 on 2007-08-31
I still cannot seem to get it to work, where in bashrc should I put that line?

---

### Post by lloyd_b on 2007-08-31
> **jefft113 said:**
> I still cannot seem to get it to work, where in bashrc should I put that line?

It doesn't matter where you put it, as long as it's not inside of an "if ..." statement.  I'd suggest putting it as the last line of the file. 

A question: is that program being run from a terminal window, or is it a GUI program that you're running from an icon?  If the latter, then you will need to log completely off and back on before the change will take effect.  If running from a terminal window, the change should take effect the next time you start a terminal window.

If you still have problems, could you run the following command in a terminal window, and post the output?
```
env | grep PATH
```
(Note: that "|" is the "pipe symbol", <SHIFT><Backslash> on US keyboards).

Lloyd B.

---

### Post by jefft113 on 2007-08-31
Ok, its working now. Appears the reason I couldnt get your code to work before was because to run it the program I used "./stata" which in needs in the original directory, but from my home directory I only needed to type "stata", weird.

Thanks alot for the help.

---

### Post by lloyd_b on 2007-08-31
> **jefft113 said:**
> Ok, its working now. Appears the reason I couldnt get your code to work before was because to run it the program I used "./stata" which in needs in the original directory, but from my home directory I only needed to type "stata", weird.

Thanks alot for the help.

Actually, that's perfectly normal.  If a program is in the PATH, then all you need to do is type the program name.  If the program is *not* in the PATH, then you need to tell it explicitly where to find it.  

But if you explicitly tell it what directory to look in, then it will ignore the PATH completely.  And that is exactly what you were doing.  "." means "the current directory", so "./stata" means "run the program named stata that's in the current directory".

FYI - you *could* have run the program, while in your home directory, without the PATH modification, by giving it the full path: "/usr/local/stata/stata".

Lloyd B.

---

### Post by hbejainpenn on 2008-05-07
Hi Guys, I am new in ubuntu. It is the first time to install something without the synaptic.
I am on the same problem, I instaled Stata 10 but I can not edit the ./profile or even I can not see the nasrc file.
I tried with the vi editor and i can not save the changes and I keep getting warnings afterwards.
How did you do to open the profile and the bashrc  files?
I can not see profile in home directory as stata manual claims and when I opened with vi editor it seems really different it has only like 2 loops.
Thanks
Hernan

---

### Post by unutbu on 2008-05-07
Try

```
gedit ~/.bashrc
```

You might not have been able to find .bashrc or .profile in nautilus because files and dirs that begin with a dot are hidden. Ctrl-h toggles the hidden files.

---

