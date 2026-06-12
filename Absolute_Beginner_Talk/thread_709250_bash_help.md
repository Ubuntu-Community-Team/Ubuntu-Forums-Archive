---
title: "bash help"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by chelfc on 2008-02-27
Hi how do I test whether a filename (which I have stored in a variable) has an extension, if not, don't do the commands below.

---

### Post by mali2297 on 2008-02-27
To check if the file name contains a dot,
```

if [[ "$filename" =~ "\." ]] ; then
# your commands
fi

```

To check if it contains ".txt",
```

if [[ "$filename" =~ "\.txt" ]] ; then
# your commands
fi

```

---

### Post by glennric on 2008-02-27
After a little testing it seems that your script is not quite right.  It should be
```
if [[ "$filename" =~ "." ]] ; then
# your commands
fi
```
According to the manpage of bash it seems that you should be correct as "=~" is supposed to consider the right hand side as a regular expression, and then you would have to escape the dot so that it is not considered as anything.  However, in practice it doesn't work that way.

---

### Post by chelfc on 2008-02-27
hey, I tried the code to check if the filename has a dot, but it still gives me a warning that says the file already exists (folder has same name as file), so it doesn't create it. However, I would like it to not attempt it at all (which I can do, just the condition you gave isn't working)

---

### Post by glennric on 2008-02-27
What are your commands?  We need more details to help you.

---

### Post by mali2297 on 2008-02-27
> **glennric said:**
> After a little testing it seems that your script is not quite right.  It should be
```
if [[ "$filename" =~ "." ]] ; then
# your commands
fi
```
According to the manpage of bash it seems that you should be correct as "=~" is supposed to consider the right hand side as a regular expression, and then you would have to escape the dot so that it is not considered as anything.  However, in practice it doesn't work that way.

Strange, for me it works.
```

[~]$ filename="footxt"
[~]$ if [[ "$filename" =~ "\." ]] ; then echo OK ; else echo NOT OK ; fi
NOT OK
[~]$ filename="foo.txt"
[~]$ if [[ "$filename" =~ "\." ]] ; then echo OK ; else echo NOT OK ; fi
OK

```

---

### Post by glennric on 2008-02-27
> **mali2297 said:**
> Strange, for me it works.
```

[~]$ filename="footxt"
[~]$ if [[ "$filename" =~ "\." ]] ; then echo OK ; else echo NOT OK ; fi
NOT OK
[~]$ filename="foo.txt"
[~]$ if [[ "$filename" =~ "\." ]] ; then echo OK ; else echo NOT OK ; fi
OK

```

What shell are you using?  I am using "bash".  You may be using "dash" which is the default for Ubuntu.  Perhaps that is the difference?  No, I just tested and with either dash or bash I have to remove the backslash for it to work as expected.  I used the exact commands you have above.

---

### Post by glennric on 2008-02-27
Interesting.  If I remove the quotes from the command, it works as expected with the backslash, but not without.

---

### Post by sryth on 2008-02-27
Here's a good spot for most things terminal.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by glennric on 2008-02-27
> **sryth said:**
> Here's a good spot for most things terminal.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

I have quite a bit of experience with bash scripting.  It is not a matter of learning how to use bash.  I just want to know why these commands are behaving differently on our two systems.  Refer to the above posts to see what I am talking about.

---

### Post by mali2297 on 2008-02-27
> **glennric said:**
> What shell are you using?

Bash, although I'm not using ubuntu right now.
```

[~]$ bash --version
GNU bash, version 3.1.17(1)-release (x86_64-redhat-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.

```

---

### Post by mali2297 on 2008-02-27
> **glennric said:**
> Interesting.  If I remove the quotes from the command, it works as expected with the backslash, but not without.

Interesting indeed. :-k 
Here's what I get if I remove the quotes.
```

[~]$ filename="footxt"
[~]$ if [[ "$filename" =~ \. ]] ; then echo OK ; else echo NOT OK ; fi
OK

```

---

### Post by mali2297 on 2008-02-27
I'm back home with Ubuntu Feisty Fawn.
```

[~]$ bash --version
GNU bash, version 3.2.13(1)-release (i486-pc-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.
[~]$ filename="footxt"
[~]$ if [[ "$filename" =~ "\." ]] ; then echo OK ; else echo NOT OK ; fi
NOT OK
[~]$ filename="foo.txt"
[~]$ if [[ "$filename" =~ "\." ]] ; then echo OK ; else echo NOT OK ; fi
NOT OK
[~]$ if [[ "$filename" =~ \. ]] ; then echo OK ; else echo NOT OK ; fi
OK

```
Thus, the syntax must have changed with a later version of bash. Strike the quotes in the code that I gave earlier.

---

### Post by chelfc on 2008-02-29
I've tried that =~ command, but it gives me an error, something about a unary operator (I'm not at a linux machine at the moment), also, is there meant to be a space between teh =~ and "\." ?

---

### Post by mali2297 on 2008-02-29
> **chelfc said:**
> I've tried that =~ command, but it gives me an error, something about a unary operator (I'm not at a linux machine at the moment), also, is there meant to be a space between teh =~ and "\." ?

Yes, and spaces can be important. 

Note also  that the conclusion was to remove the quotes from "\." .

---

