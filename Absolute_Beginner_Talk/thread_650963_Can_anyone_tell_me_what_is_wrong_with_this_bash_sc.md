---
title: "Can anyone tell me what is wrong with this bash script?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-12-27
I managed to make a script in python with easygui that prints the results of a message box. I used this as a variable in a bash script, so that, when I run my script it runs a message box (using foo.py) that asks me to choose between A and B, if I choose A, it prints A. Then the variable is used in a test script, and I reached a snag.

```
#!/bin/bash -x
choice=$(/home/owner/bash/foo.py)
echo $choice
if "$choice" = "A" 
then 
	/home/owner/bash/A
fi

```

what it is supposed to do is see that choice = A and A = A, and then run the script in my folder, which changes the current background song playing. 
This is the output in terminal:

```
owner@ubuntu:~/bash$ ./music
++ /home/owner/bash/foo.py  (here it opens the message box with the buttons)
+ choice=A (I clicked A)
+ echo A (it runs the command...)
A (I know it is reading choice as A)
+ A = A
./music: line 4: A: command not found (I have no idea why it is giving me this.)
owner@ubuntu:~/bash$ 

```
It's one AM right now, so I'm sure it's just something I'm not seeing, any help is appreciated.

---

### Post by p_quarles on 2007-12-27
Did you make the script called /home/owner/bash/A executable?

---

### Post by bodhi.zazen on 2007-12-27
My guess is you need brackets and a ;

```
#!/bin/bash -x
choice=$(/home/owner/bash/foo.py)
echo $choice
if [ "$choice" = "A" ]; then 
	/home/owner/bash/A
fi
```

You might also want to look at zenity

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

---

### Post by Xavieran on 2007-12-27
[QUOTE=Romanus81;4021097]I managed to make a script in python with easygui that prints the results of a message box. I used this as a variable in a bash script, so that, when I run my script it runs a message box (using foo.py) that asks me to choose between A and B, if I choose A, it prints A. Then the variable is used in a test script, and I reached a snag.
You're code:
```
#!/bin/bash -x
choice=$(/home/owner/bash/foo.py)
echo $choice
if "$choice" = "A" 
then 
	/home/owner/bash/A
fi

```
This is in python.right?
What I would do:
```
#!/bin/python
choice=(/home/owner/bash/foo.py)
print choice
if "choice" == "A": 
    then: 
        /home/owner/bash/A
fi

```

---

### Post by Romanus81 on 2007-12-27
> **bodhi.zazen said:**
> My guess is you need brackets and a ;

```
#!/bin/bash -x
choice=$(/home/owner/bash/foo.py)
echo $choice
if [ "$choice" = "A" ]; then 
	/home/owner/bash/A
fi
```

You might also want to look at zenity

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
That was it! Thanks!

---

### Post by sillygates on 2008-01-10
Hmm, you really should use zenity for this.

Try it out :)

---

