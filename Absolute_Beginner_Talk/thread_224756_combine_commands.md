---
title: "combine commands"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Ziox on 2006-07-28
ok, this is a very n00b question...how do you combine commands?

i'm trying to combine these two commands 2gether:

3ddesk --acquire

and 

3ddesk

i've tried ";" and "&&" but both of them only activate the first command: 3ddesk --acquire, but it doesn't activate the second command 3ddesk...some one help please.

---

### Post by jordilin on 2006-07-28
You can use **pipes** in order to combine commands. For example:
```
ls -l | grep txt
```
will give you all the lines that have the string txt. You are combining the command ls with the command grep. Is this what you need?

---

### Post by Ziox on 2006-07-28
no...my first command is to make the program 3ddesktop to cache my desktop images, then my second command is to actually start 3ddesktop's virtual view...I've also tried piping, but doesn't work...:(

---

### Post by kabus on 2006-07-28
If neither of these work

```
3ddesk --acquire; 3ddesk
3ddesk --acquire && 3ddesk
```

then the issue has nothing to do with combining commands.
It's more likely there's something wrong with your 3ddesk installation or configuration.

---

### Post by FenrisAbraxas on 2006-07-28
> **Ziox said:**
> ok, this is a very n00b question...how do you combine commands?

i'm trying to combine these two commands 2gether:

3ddesk --acquire

and 

3ddesk

i've tried ";" and "&&" but both of them only activate the first command: 3ddesk --acquire, but it doesn't activate the second command 3ddesk...some one help please.
Haven't you tried ```
$ 3ddesk --acquire; sleep 20 3ddesk
```
the "sleep" comand accept integer values giving seconds, so you do 3ddesk --aquire and when finished cacheing the images it waits 20 seconds before launching 3ddesk

---

### Post by chalex on 2006-07-28
> **jordilin said:**
> You can use **pipes** in order to combine commands. For example:
```
ls -l | grep txt
```
will give you all the lines that have the string txt. You are combining the command ls with the command grep. Is this what you need?

The pipe passes the output of the first command to the input of the second.  While this could be considered "combining" commands, it doesn't seem to be what the OP is looking for.

For the OP, simply typing the two commands in succession should be sufficient:
$command1 <hit Enter>
...wait for it to be done
$command2 <hit Enter>

Putting a semicolon in between allows you to put them on the same line; the result is exactly the same as above.
$command1;command2

The OP wasn't clear about what isn't working?  What's the problem?  Is there an error message?

---

### Post by Ziox on 2006-07-28
thanks for all the replies, but none of them worked.  I know that i install correctly because i can start 3ddesktop with just 3ddesk.  However, whenever I combine that with 3ddesk --acquire: 

3ddesk --acquire ; 3ddesk

only the first part would start, but 3ddesk doesn't work...

EDIT: maybe here's the problem, the [acquire] option takes parameters, so would it consider the ";" a parameter? 

EDIT: Also, i'm asking this so that i can make a launcher

---

### Post by Ziox on 2006-07-28
i've been trying something different currently. I'm trying to write a script. Right now my testing script looks like this:

#!/bin/bash
# My first script

3ddesk --acquire

echo "3ddesk --mode=random"

when i execute it, i noticed that the second command was executed before the first one was done.

So my question is, does anyone know how to slow the execution speed of the second one down, so that it would execute in order?

Thanks in advance.

---

### Post by Ziox on 2006-07-28
finally worked...thanks to fenrisabraxas.  this is my command now:

3ddesk --acquire ; sleep 5 ; 3ddesk --mode=random

I didn't know what the sleep function did, so i googled it.  After that I knew that it was to delay the execution of other commands, so after finding the write time frame, it now works! :) 

Thanks for all the replies.

---

### Post by Ziox on 2006-07-28
Maybe i've spoken too soon.  It appears that the sleep function does not work unless it is ran from the terminal or something similar...because i am still having trouble running that command.  

note: the command works fine from a terminal, just not from a launcher

EDIT: now for some reason it works...i put that whole in a script and linked my launcher to that script...weird..

can some one explain to me why that command wouldn't work straight from the launcher?

---

### Post by gThree on 2006-07-28
fyi, instead of "sleep n" you can also use "wait" which will pause your script until the previous command is done running ...

---

### Post by Ziox on 2006-07-28
> **gThree said:**
> fyi, instead of "sleep n" you can also use "wait" which will pause your script until the previous command is done running ...

thanks, but unfortunately wait doesn't work...

Does anyone know a command that can make one process wait until the previous process finishes?

I know "sleep" works, but I have to keep on changing the waiting times, because sometimes it takes longer for the previous process to finish.

Thanks in advance

---

