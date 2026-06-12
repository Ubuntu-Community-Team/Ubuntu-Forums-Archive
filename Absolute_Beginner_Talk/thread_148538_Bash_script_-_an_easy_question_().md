---
title: "Bash script - an easy question (?)"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by megamania on 2006-03-22
I'm sure this one is pretty straightforward for most of you.

I want my script to place a logfile in the directory it is located in, i.e. if it is in /home/xxx/scripts and I run it from a shell whose current directory is home/xxx/music, the logfile must NOT be placed in the "music" directory, but in the "scripts" directory.

In my current script, the logfile is created in the current directory and that's not what I need!

Any suggestions?

---

### Post by kabus on 2006-03-22
Just specify an absolute path for your logfile (best to put it into a variable so you don't have type it out / change it in several places) :

```
logfile="~/scripts/log"
do something > $logfile
```

---

### Post by megamania on 2006-03-22
[QUOTE=kabus]Just specify an absolute path for your logfile (best to put it into a variable so you don't have type it out / change it in several places) :

```
logfile="~/scripts/log"
do something > $logfile
```[/QUOTE]

I tried that, but I would have to edit the script every time I move it to a different directory or use it on a different computer...

---

### Post by bscbrit on 2006-03-22
Use 'pwd' to get the current working directory, and then edit it to point to your logfile.

---

### Post by ow50 on 2006-03-22
```
#!/bin/bash

echo -n "Current directory: "
pwd

echo -n "Script file: "
echo $0

echo -n "Script directory: "
echo $(dirname $0)
```

When did bash scripting become absolute beginner talk?

---

### Post by kabus on 2006-03-22
You could get the location of the script with dirname $0, but that would only work if you always start it using the full path.
If you put it in a directory that is in your $PATH, you could also do dirname `which *script*`

---

### Post by megamania on 2006-03-22
thanks, I think the "$0" solution is the one.

[QUOTE=ow50]
When did bash scripting become absolute beginner talk?[/QUOTE]
well, I thought it was a beginner's question... :)

---

### Post by megamania on 2006-03-22
[QUOTE=ow50]```

echo -n "Script directory: "
echo $(dirname $0)
```
[/QUOTE]

when I try this, I get a "too many arguments" error. I tried a few alternatives, but I'm stuck - I told you I'm an absolute beginner... any help?

---

### Post by ow50 on 2006-03-22
[QUOTE=megamania]when I try this, I get a "too many arguments" error. I tried a few alternatives, but I'm stuck - I told you I'm an absolute beginner... any help?[/QUOTE]
Your script directory name seems to contain spaces. Quoting $0 should help.
```
echo -n "Script directory: "
echo $(dirname "$0")
```

---

### Post by nanotube on 2006-03-22
if you want it to always place it in the scripts subdirectory of the parent directory of your script, then you could just shove it to "../scripts"...

---

### Post by megamania on 2006-03-23
[QUOTE=ow50]Your script directory name seems to contain spaces. Quoting $0 should help.
```
echo -n "Script directory: "
echo $(dirname "$0")
```[/QUOTE]

Yes, it does contain spaces. Now I understand the reason of the "too many parameters" error.

I'll try your solution when I'm back home, but I'm sure it works.

Thanks again!

---

### Post by megamania on 2006-03-23
[QUOTE=ow50]Your script directory name seems to contain spaces. Quoting $0 should help.
```
echo -n "Script directory: "
echo $(dirname "$0")
```[/QUOTE]
I ended up doing:
LOGFILE= $0.log

which looked like a good solution because it creates (or is supposed to create) a filename with the same name as the script, plus a .log extension.

When I try to redirect the output to the file (echo &date  >> $LOGFILE), I get and "ambiguous redirection" error.

I also tried 
```

LOGFILE=\"$0.log\" 
```
to avoid the problem of spaces within the filename, but still get the same error... ](*,)

---

### Post by ow50 on 2006-03-23
```
#!/bin/bash

LOGFILE=$0.log
echo &date >> "$LOGFILE"
```

---

### Post by megamania on 2006-03-23
[QUOTE=ow50]```
#!/bin/bash

LOGFILE=$0.log
echo &date >> "$LOGFILE"
```[/QUOTE]
that works!

To be honest, I had considered that solution, but since the redirection to the logfile is widespread all over the script, I thought my solution was more efficient and equivalent in syntax. I was wrong, obviously. :-)

Thanks again,
gianfranco

---

