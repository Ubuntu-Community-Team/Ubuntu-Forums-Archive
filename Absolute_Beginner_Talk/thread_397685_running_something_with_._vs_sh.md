---
title: "running something with ./ vs sh"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by bkildow on 2007-03-31
Hi, I was just wondering if someone could explain to me the differences in running a script with ./ vs sh. For example: 

sudo ./something

vs. 

sudo sh something

---

### Post by martinw89 on 2007-03-31
That's a good question actually, I've never considered it and always regarded them as interchangeable.  OK, turns out that "./" requires the program to have the executable permission, while "sh" does not.  Other than that I can't seem to find any surface differences.

---

### Post by jordanmthomas on 2007-03-31
Look at the first line of the file.  If sh does succeed in running it, you'll see this as the first line:
```
#!/bin/bash
```
If you have #!**programtouse** and the script is executable (ie you can run it with ./) then it will try to run the script using **programtouse**

Usually, it's good to add #!/whatever at the beginning of the script.  Then, you can just chmod +x it and the correct program will be used.  Here's why that is advantageous:

EXAMPLE FILE
```
#/bin/perl
*perlcode....*

```

running sh filename wouldn't work, but ./filename would work fine.  Did I make sense here or am I just rambling?

---

### Post by martinw89 on 2007-03-31
OK so ./ essentially executes the file using the program that is listed on the first line.  That makes a lot of sense.

---

### Post by jordanmthomas on 2007-03-31
Yes, well put.  Better than I put it at least. :)

**edit**  This is only true for text files.  Binary files are just executed when using ./

---

### Post by bkildow on 2007-03-31
Ok, I think I understand ./. Now sh on the other hand, when that is run, what does that do exactly. I know when run alone, by just typing sh in a terminal, it will bring up another shell. Does running sh somefile, just it assume the file is written in bash and interpret it?

---

### Post by martinw89 on 2007-03-31
Check out sh's manual page, "man sh" or [here]("http://www.research.att.com/~gsf/man/man1/sh.html").

---

### Post by ComplexNumber on 2007-03-31
> **bkildow said:**
> Hi, I was just wondering if someone could explain to me the differences in running a script with ./ vs sh. For example: 

sudo ./something

vs. 

sudo sh something
although other people have mentioned it, i'm just going to reiterate to summarise.

for a bash script, they are both exactly the same. if, for example, you write your own bash script called My-Bash-Script and proceed to execute it by typing in the command **./My-Bash-Script**

that it exactly the same as:
[B]sh ./My-Bash-Script

[/B]
if, for example, the program is a python script,  the following 2 are i_dentical_:
**./My-Python-Program**

[B]python ./My-Python-Program
[/B]

in the above example, "sh" just means to run the program as a bash script, whereas "python" means to run it as a python script. its not really necessary, though. the first line of a particular program can indicate what language the script is to be executed using.

preceding the program name with "sh", "gcc"(C compiler), "python", "perl" is not a necessity, but can make it clearer to others what the program is written in for the sake of good documentation.

---

