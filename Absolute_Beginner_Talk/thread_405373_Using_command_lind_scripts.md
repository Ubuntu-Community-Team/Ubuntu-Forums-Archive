---
title: "Using command lind scripts"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Gina on 2007-04-09
This is such a fundamental query and should be blindingly obvious - but not to me.  I have searched wikis etc. without finding the answer.

All over the place, scripts are mentioned which contain command lines.  In many cases one command needs to finish before the next one is run so copying and pasting the whole file directly into a terminal winsdow doesn't seem to work.  I'm sure there must be a command that accesses a text file and takes one line at a time and executes it.  (I seem to remember doing this in DOS umpteen years ago)  I have been doing it by hand - ie. copying each line, pasting into a terminal and pressing Enter to execute it - waiting for things to finish before doing the same with the next command.  Very tedious, and I've had enough :lol:

I feel so silly asking this but how do you run a text script, please?

---

### Post by rai4shu2 on 2007-04-09
Here's a pretty good guide for what you want:

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_01_05.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_01_05.html)

---

### Post by Swab on 2007-04-09
Open a text editor...  create the following.

```

#!/bin/bash
command 1
command 2
command 3

```

save it as whatever.sh

From the command line set the script to be executable

```
chmod +x whatever.sh
```

Run it with..

```
./whatever.sh
```

---

### Post by Bachstelze on 2007-04-09
In a nushell, open a text editor, type

```
#!/bin/bash

command1
command2
```

save as script.sh and execute with *bash script.sh*.
Another approach is to do

```
command1 && command2
```

that way, command2 will be executed after command1 is finished *successfully*. If, for whatever reason, command1 fails, command2 will *not* be executed.

---

### Post by Gina on 2007-04-10
Thank you everyone - I'll try that :):)

---

