---
title: "Command Line help:  ps command ..."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-25
I was thinking I saw some post using a linux command similar to ps but would filter based on application name.  For example, when I search for all Fire Fox applications, I do:

ps  -ef | grep -i fire


I though I saw a command like this:  ps fox


Any hints?

Carl


PS:  I also noted something like say the user is carl and the group is carl a command that would change the user/group with one command sorta like:  chown  carl:carl  filename

Any other handy command-line insights???

---

### Post by Seisen on 2007-06-25
Here is a list of commands 

[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

---

### Post by bodhi.zazen on 2007-06-25
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Otherwise do a google search and you will find lots of sites ;)

---

### Post by cwmoser on 2007-06-26
Anyone interested, I found the commands I was seeking:

 $  pgrep  evolution                    <-- show process id for processes named evolution

 $ pkill evolution                       <-- kill process named evolution


The above is easier than:
 $ ps  -ef  |  grep  -i  evolution

 $ kill  -9  18761


Carl

---

### Post by Nekiruhs on 2007-06-26
> **cwmoser said:**
> Anyone interested, I found the commands I was seeking:

 $  pgrep  evolution                    <-- show process id for processes named evolution

 $ pkill evolution                       <-- kill process named evolution


The above is easier than:
 $ ps  -ef  |  grep  -i  evolution

 $ kill  -9  18761


Carl
For kill, you could also use killall PROCESSNAME

---

