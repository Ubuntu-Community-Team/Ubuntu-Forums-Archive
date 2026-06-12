---
title: "Script to open files"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by sabrina on 2006-11-19
Hi! 

I'd like to make a script for opening multiple files (just to practice).

I want it to be simple, but at the same time I want the files to open at the same time. But

#!/bin/sh
read -p "which files: "
for ((N=1; N<$#+1; N++)); do

  gedit ${N}

done

doesn't work, since it can't seem to figure out that ${N} is number N parameter.

Please don't come up with difficult solutions, since it's my third script.

---

### Post by gborzi on 2006-11-19
Try this script:
> 
#!/bin/bash
read -p "which files: " LIMIT
for ((N=1; N<$LIMIT+1; N++)); do

gedit ${N}

done
there are two differences: use bash instead of sh and the LIMIT variable to store the answer to the "which files: " prompt.

---

### Post by sabrina on 2006-11-19
Hi!

Thanks for the reply.

Kan a variable contain more words and still be able to seperate them like the script asks it to?

Any particular reason that you choose bash?

---

### Post by sabrina on 2006-11-19
It still doesn't work. If I type "2" to the answer "Which files" - it opens a file "1" and a file named "2" in gedit.

---

### Post by bodhi.zazen on 2006-11-19
Try:

> #!/bin/bash
read -p "which files: " LIMIT
for $X in "$LIMIT"
do
gedit $X
done

---

### Post by gborzi on 2006-11-19
> **sabrina said:**
> Hi!

Thanks for the reply.

Kan a variable contain more words and still be able to seperate them like the script asks it to?

A variable can contain more words (i.e. FILES="1 2 3") and to access them in sequence you can use another form of the for cycle, that mentioned by bodhi.zazen.

> **sabrina said:**
> 
Any particular reason that you choose bash?
Yes, it is much easier to make a script in bash than in sh. There are more goodies for programming.

> **sabrina said:**
> 
It still doesn't work. If I type "2" to the answer "Which files" - it opens a file "1" and a file named "2" in gedit.
Sorry, I misunderstood the aim of your script. I thought you wanted to open several _numbered_ files. The script by bodhi.zazen is almost OK, this is a working version:
> 
#!/bin/bash
read -p "which files: " FILES
for X in $FILES; do
gedit $X
done

Note that I use X instead of $X in the for loop, because X is the variable assigned by the for loop, $X its value, in other words use X to assign a value, $X to retrieve it. Also, one need to use $FILES instead of "$FILES" in the for loop, because if you use the quotes X is made equal to the whole FILES variable, not to one of its words in sequence.

---

### Post by bodhi.zazen on 2006-11-19
> **gborzi said:**
> Note that I use X instead of $X in the for loop, because X is the variable assigned by the for loop, $X its value, in other words use X to assign a value, $X to retrieve it. Also, one need to use $FILES instead of "$FILES" in the for loop, because if you use the quotes X is made equal to the whole FILES variable, not to one of its words in sequence.

Thanks. 8)

---

### Post by sabrina on 2006-11-19
Thanks to both of you for the good replies! :)

Now I got it working.

Do you know links to some good tutorials on shell scripts in bash?

---

### Post by sabrina on 2006-11-19
Just wondering... How would the script look, if I want to give the filenames as parameters to the program?

So I type the following in the command-line:

$ script-name test.tex hello.tex

?

---

### Post by bodhi.zazen on 2006-11-19
> **sabrina said:**
> Just wondering... How would the script look, if I want to give the filenames as parameters to the program?

So I type the following in the command-line:

$ script-name test.tex hello.tex

?

I do not think your script changes at all as long as the files are in your current directory. If not, use the path...
[indent]Problems ?[/indent]

for bash tutorials :

[Bash Tutorial](http://www.hypexr.org/bash_tutorial.php)

[Linux Shell Scripting Tutorial v1.05r3](http://www.freeos.com/guides/lsst/)

[Advanced Bash-Scripting Guide](http://tldp.org/LDP/abs/html/)

---

### Post by sabrina on 2006-11-19
Thank you for the links!

I still can't get it to work, when I type the filenames on the commandline.

---

### Post by bodhi.zazen on 2006-11-19
> **sabrina said:**
> Thank you for the links!

I still can't get it to work, when I type the filenames on the commandline.

I'll look at it later (as you can guess, I am now at work on a windows box !).

Post your current script.

---

### Post by David_T on 2006-11-19
Hi sabrina,

To just iterate through your arguments on the command line, all you have to do is something like:

```

#!/bin/sh

for file
do
    gedit $file &
done

```

This would allow you to call ./script file1 file2 file3 and have it pop open three gedit windows.

---

### Post by sabrina on 2006-11-19
Thank you so much.

The current script is

```

#!/bin/bash

read -p "which files: " FILES

for X in $FILES; do

    gedit $X

done

```

---

### Post by gborzi on 2006-11-19
> **sabrina said:**
> Just wondering... How would the script look, if I want to give the filenames as parameters to the program?

So I type the following in the command-line:

$ script-name test.tex hello.tex

?
It should be like this
> #!/bin/bash

for X in $*; do
    gedit $X
done
where $* contains all the arguments given to the script, in your example $* is *test.tex hello.tex*.

---

### Post by bodhi.zazen on 2006-11-19
LOL :lol:

Such a simple script, look at the three of us ! I'm blinder then you ....

This works:> #!/bin/bash
read -p "which files: " FILES
for X in $FILES; do
gedit "$X" &
done

Sometimes when I run the script with multiple windows I get multiple windows, but most of the time I get one window with multiple tabs.

It takes documents in the current directory and by path.

Input of> test test2 mobile/Referance.txt opens 3 documents:
test
test2
and Referance.txt

Thank you for this side track ! :p 8)

---

### Post by bodhi.zazen on 2006-11-19
> **David_T said:**
> Hi sabrina,

To just iterate through your arguments on the command line, all you have to do is something like:

```

#!/bin/sh

for file
do
    gedit $file &
done

```

This would allow you to call ./script file1 file2 file3 and have it pop open three gedit windows.

That works as well. Thank you.

---

### Post by sabrina on 2006-11-20
Thank you to all three of you!

I'm glad, it wasn't just me that had problems ;)

---

