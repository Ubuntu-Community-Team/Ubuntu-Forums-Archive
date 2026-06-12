---
title: "bash renamer scripting"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-08-10
I'm trying to do a very simply file renaming " *.jpg to 1.jpg, 2.jpg, 3.jpg.... etc.  I'd really like to learn more about bash shell scripts.  Anyone know how to write that specific script and find general information on writing similar bash shell scripts? 

Thanks.

---

### Post by bodhi.zazen on 2007-08-10
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc2](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc2)

[http://tldp.org/LDP/abs/html](http://tldp.org/LDP/abs/html)

[http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

You want to rename all your .jpg to sequential numbered .jpg ?

do you want to preserve any of the name ?

---

### Post by bigboy_pdb on 2007-08-11
You can do this in one line. It is as follows:
```

i=1; for file in *.jpg; do mv $file ${i}.jpg; i=$((i+1)); done

```

I would recommend making a copy of the folder first and then testing the command to see that it does what you want. From what you stated, I'm guessing that you want each file to be renamed so that they go from names such as harold.jpg, susie.jpg, and cutie.jpg to names like 1.jpg, 2.jpg, and 3.jpg.

The command is easier to read if it is written this way (and it can still be pasted into the command line in this manner):
```

i=1;
for file in *.jpg; do
	mv $file ${i}.jpg;
	i=$((i+1));
done

```

What the script above does is:
* It declares a variable named **i** and assigns it the value 1
* It takes all the files that end in ".jpg" and assigns them one at a time to the variable named **file**

Within the loop the two following instructions are repeated (as long as there is another file name in the list to be read into the variable **file**):
* Move the current file called value_of_file (where value_of_file is the current file name for the variable **file**) to a file called value_of_i.jpg (where value_of_i is the current numerical value of the variable **i**)
* Increment **i** (in other words add one to the value of the variable **i**)

---

