---
title: "Command line input and output to text file?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Bob Ashley on 2006-09-04
As a lurking newbie, I've noticed the dependency on getting the output of command line commands into text files for the purpose of problem solving and general communication. 

Is there a command which will record both the input (command) and its output to a text file? 

Also, I would like to know how to capture the start up or boot script in a text file. 

Appreciate your help.

Bob

---

### Post by Anonii on 2006-09-04
> **Bob Ashley said:**
> As a lurking newbie, I've noticed the dependency on getting the output of command line commands into text files for the purpose of problem solving and general communication. 

Is there a command which will record both the input (command) and its output to a text file? 

Also, I would like to know how to capture the start up or boot script in a text file. 

Appreciate your help.

Bob
Lets see...
For example lets say that you want to record your dmesg in a .txt file, you can use the following command:

dmesg >> dmesg.txt

That will record the output of dmesg, in a text file **it will create** called dmesg.txt. i dont know how to also add the command (dmesg) but you can probably do it manually.

---

### Post by steve.horsley on 2006-09-04
There probably is, but I don't know it.
Perhaps involving a utility called tee?

I have always got by on either:

1: copy/paste from the terminal if the output isn't too long. This gets both the input and the output. Or

2: just pipe the output of the command into a text file and attach that to my posts. Anonii shows how to pipe the output to a file. This only gets the output. You can always edit the file later to add the input at the top.

---

### Post by cwaldbieser on 2006-09-04
> **Bob Ashley said:**
> As a lurking newbie, I've noticed the dependency on getting the output of command line commands into text files for the purpose of problem solving and general communication. 

Is there a command which will record both the input (command) and its output to a text file? 

Also, I would like to know how to capture the start up or boot script in a text file. 

Appreciate your help.

Bob

The "script" command can record your session.
```

$ script
Script started, file is typescript
$ #do some stuff
$ exit
Script done, file is typescript

```
The file can be played back with:
```

$ cat typescript

```

You can also save timing information and play the script back with "scriptreplay" so it happens at "human speed".

---

### Post by Bob Ashley on 2006-09-05
Appreciate the tips everyone. Thanks. 

bob

---

### Post by xyz on 2006-11-26
Also:
Type a command (this is an example/works with any command)
```
cat /etc/apt/sources.list
```
Then:
```
 cat /etc/apt/sources.list | tee sources.lst

```
will save your sources.list to a file you may have named "sources.list"
If at the time you are in:
> th@luser:~/Desktop$

The file will be saved to your Desktop.
So:
```
 whatever_command | tee name_file_accordingly
```

I've encountered some pbms saving large output this way.

Also:
man tee
man info tee

---

### Post by Tomosaur on 2006-11-26
The following will put the output of command into text_file.txt. If the file doesn't exist, it is created.

```
command > text_file.txt
```

The following will APPEND the output of command into text_file.txt. Again, if the file does not exist it will be created, but if the file DOES exist, then the information will just be added on to the end of the file, rather than overwriting it.
```
command >> text_file.txt
```

The final line here will use the output of command1 as the input of command2:
```
command1 | command2
```

---

### Post by motoperpetuo on 2007-12-24
> **Tomosaur said:**
> The following will put the output of command into text_file.txt. If the file doesn't exist, it is created.

```
command > text_file.txt
```

The following will APPEND the output of command into text_file.txt. Again, if the file does not exist it will be created, but if the file DOES exist, then the information will just be added on to the end of the file, rather than overwriting it.
```
command >> text_file.txt
```

The final line here will use the output of command1 as the input of command2:
```
command1 | command2
```

one other question, how could i do the above, but send the output to a text file in a different directory?

---

### Post by erginemr on 2007-12-25
> **motoperpetuo said:**
> one other question, how could i do the above, but send the output to a text file in a different directory?

All you need to do is to specify its full path. For example:
```
ls > ~/Desktop/output.txt
```
will put the output of the current directory listing in a file "output.txt" in my desktop.

In addition to the above replies on forwarding the standard output, you can manipulate the standard input by:
```
command < input.txt
```

For more, read the following tutorial:
[http://www.tuxfiles.org/linuxhelp/iodirection.html](http://www.tuxfiles.org/linuxhelp/iodirection.html)

---

### Post by motoperpetuo on 2007-12-31
thanks! if i knew how to do one of those official thank yous, i would.

---

### Post by p_quarles on 2007-12-31
> **motoperpetuo said:**
> thanks! if i knew how to do one of those official thank yous, i would.
I did it on your behalf. ;)

---

