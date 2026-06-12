---
title: "[SOLVED] Include a text file in conky"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-03-24
Hey, 

I currently have a .conkyrc file which i have running on my desktop. what i would like to do is add a section on the end that links to a .txt file and shows the text in the .txt file.

Much like in php you would use include("");

So i want my conkyrc to show the text from a seperate .txt file.So i can easily just edit the .txt file and it changes my notes on the bottom of my conky display.


Saj

---

### Post by kerry_s on 2008-03-24
man conky

```
 exec  command
    Executes a shell command and displays the output in conky. warning: this takes a lot more resources than other variables. I'd recommend coding wanted behaviour in C and posting a patch.

execbar command
    Same as exec, except if the first value return is a value between 0-100, it will use that number for a bar. The size for the bar is currently fixed, but that may change in the future.

execgraph command
    Same as execbar, but graphs values.

execi interval command
    Same as exec but with specific interval. Interval can't be less than update_interval in configuration. See also $texeci

execibar interval command
    Same as execbar, except with an interval

execigraph interval command
    Same as execigraph, but takes an interval arg graphs values

execp command
    Executes a shell command and displays the output in conky. warning: this takes a lot more resources than other variables. I'd recommend coding wanted behaviour in C and posting a patch. This differs from $exec in that it parses the output of the command, so you can insert things like ${color red}hi!${color} in your script and have it correctly parsed by Conky. Caveats: Conky parses and evaluates the output of $execp every time Conky loops, and then destroys all the objects. If you try to use anything like $execi within an $execp statement, it will functionally run at the same interval that the $execp statement runs, as it is created and destroyed at every interval.

execpi interval command
    Same as execp but with specific interval. Interval can't be less than update_interval in configuration. Note that the output from the $execpi command is still parsed and evaluated at every interval.

```

---

### Post by raja on 2008-03-24
The 'execi' command in conkyrc will allow execution of any command at intervals. So you can just use this to run 'cat some.file'

---

### Post by saj0577 on 2008-03-24
Cheers i will try it and let you know if it works.

Saj

---

### Post by saj0577 on 2008-03-24
So what do i add to the bottom of my conkyrc file for it to work ive tried various different $ and i cant seem to get it to work.

Saj

---

### Post by saj0577 on 2008-03-24
${execi 10 cat ascii.txt}
it works

---

### Post by raja on 2008-03-24
```
Test: ${execi 2 cat /home/raja/test.txt}
```
works for me.

---

