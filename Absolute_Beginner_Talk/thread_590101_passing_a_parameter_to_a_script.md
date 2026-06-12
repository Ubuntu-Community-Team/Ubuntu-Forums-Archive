---
title: "passing a parameter to a script"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-24
Basically I'm wondering how I can write a script that uses parameters passed into it when the script is called in the command line.

i.e.

I could call

ScriptAlias "/some_file"

and then some_file could be passed to the script to be used

thanks

---

### Post by Dr Small on 2007-10-24
In what language ?
BASH ?
SHELL ?

---

### Post by Hospadar on 2007-10-24
I'm sure there's a better way to do it, but you could always you output redirection, and just pull the args you need from stdin.

like for example
<you@compy$> ls | ./your_script

would pipe the output from ls to the standard input for your script.

---

### Post by KCPokes on 2007-10-24
Not sure I understand the use of ScriptAlias in your example.  If it were a standard shell script, then you just pass in the variables one after the other...

./my_script.sh <one> <two> <three>

Within your script you just reference the variables by order...

VARIABLE_ONE=$1
VARIABLE_TWO=$2
VARIABLE_THREE=$3

This may not be anywhere near what you are asking based on your example call, but your description seems to be asking for something similar to this.

---

### Post by brennydoogles on 2007-10-24
> **ssaamon said:**
> Basically I'm wondering how I can write a script that uses parameters passed into it when the script is called in the command line.

i.e.

I could call

ScriptAlias "/some_file"

and then some_file could be passed to the script to be used

thanks

What exactly are you trying to make your script do? In bash, if you are trying to have a certain action done to the first argument (such as removing it) you could do:```
rm $1
``` meaning if your script was called myscript you would type ```
myscript text.txt
``` and it would be removed. Does that help??


P.s.-- you can do the same with any number of arguments, such as ```
rm $1 $2 $3 $4
``` would delete the first 4 arguments passed to the script.

---

