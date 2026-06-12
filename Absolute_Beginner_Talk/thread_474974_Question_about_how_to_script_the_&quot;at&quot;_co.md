---
title: "Question about how to script the &quot;at&quot; command"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by thatswhatshesaid on 2007-06-15
Is there a way to batch load commands into "at" similar to the way you can do it with crontab?

A little background:

I have a text file with a large number of commands to execute at a set interval.  The interval is the same for all commands (30 mins).  I already have a perl script that can add the interval to the current time and generate the commands (I'm not a developer but it works just fine for me).  I don't have to worry about taking up too many cycles on the machine (it's all mine until it goes into production).

Basically what I want is something that acts like this:
Run command on line 1
<wait for a set interval>
Run command on line 2
<wait for a set interval>
...
<wait for a set interval>
<run command on last line>

I have been using a script that generates a file that I can use with crontab but I just like the way "at" works more (read: I keep accidentally clearing my crontab file working on other things).  My crontab generating script output would look like this (the script adds the time interval between generating lines):

# # # # * command1
#2 #2 #2 #2 * command2
#3 #3 #3 #3 * command3

and then i just run "crontab <file_containing_lines_above>" to load everything in to the box.  So after all that, my question is: is there a way to bulk load commands into at, or is there a command line way that is easy to script.  

I have been using at manually by typing: 
at <time> <enter> 
<command> <enter>
<ctrl>+<D>
[and repeating]

This is fine for around ten items or so but soon I will have to tackle the same kind of thing with hundreds of individual commands (and I don't want to sit there typing at ... for hours).  I know there has to be a way to do this, just not sure what it is.

Anyone know a slick way to use <, >, |, or something else to do this?  If there is a one liner way to do this I don't have a problem scripting that either?

Any help or links are greatly appreciated. :)

---

### Post by gilgongo on 2007-06-16
If I understand you correctly, then you can just create a shell script to load in all the at jobs in one go, no? You'll still need to type the commands, but you do so into a text file, then once you are happy with it, run this file.

I'm a little mystified as to why you are using at here though, since at jobs are for running once and once only, so to repeat them you'd have to have a shell script running via cron - a very odd arrangement!

---

### Post by thatswhatshesaid on 2007-06-17
This is the whole picture of what I am trying to do:
I have a script that was written for me by a developer that can take a csv file as input.  My input file is very (around 9GB) and the developers script can't handle this all at once.  I made a script that splits up the large input file into many smaller ones and generates the commands to run so the developer's script doesn't crash.  Now the problem is I don't want to type the commands to run the developer's script hundreds of times.  I know how long it takes the developer's script to run with a smaller input so it is pretty easy to say I want it to run with input file #1, wait 10 mins, run with input files #2, and repeat (for days) until it runs though all the input files.  

I found it was possible to automate this using a script to space out running each of the iterations and use crontab.  The reason I want to use "at" is because each iteration only needs to be run one time and will never need to be repeated.  So I am really using cron to schedule the jobs to run once which is what "at" seems to be for.  Since I am using cron I am setting the file to run at time X on day Y on whatever day of the week it falls on.

I guess this works it just seems like I am doing it wrong by using cron and not at since it is a one time thing.  I'm not stuck, just trying to learn the right way to do things.

---

### Post by gilgongo on 2007-06-17
Ah OK. I may be off on the wrong track again, but might the "sleep" command help? That is, to run a bunch of commands with ten second intervals between them, create a script that contains this:

<commands>
sleep 10
<commands>
sleep 10

maybe execute it in the background with "scriptname.sh &"

---

### Post by pmg on 2007-06-18
Interspersing "sleep" commands in your script as gilgongo suggested should work, but if you still want to use **at**, one approach would be something like:
```
echo 'command1a; command1b; command1c'  | at time1
echo 'command2a; command2b; command2c'  | at time2
...

```
The quote markes in the above are importent, to make sure the ";" is passed into "at" and not processed by the current shell.

---

