---
title: "Very easy shell scripting question"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by PsychedelicReaction on 2007-06-23
Hi guys. I'm trying to write a very small script that makes backup of a certain file zipping and then uploading it to a ftp server. 

The file shoud be uploaded with the current date - time as name. that's my syntax:

```
datenow= date +"%F_%H-%M"
mv -v input.txt  $datenow
```

i tried a lot of combinations of ' and " around $datenow but or it doesn't work or input.txt is renamed as $datenow without being parsed.

any idea?

---

### Post by wjp.reg on 2007-06-23
Have you looked at **sbackup**?  I believe it does everything you want.

cheers!

P.S. Sorry, maybe someone else will handle the script part of your question :-)

---

### Post by dzoner on 2007-06-23
> **PsychedelicReaction said:**
> Hi guys. I'm trying to write a very small script that makes backup of a certain file zipping and then uploading it to a ftp server. 

The file shoud be uploaded with the current date - time as name. that's my syntax:

```
datenow= date +"%F_%H-%M"
mv -v input.txt  $datenow
```

i tried a lot of combinations of ' and " around $datenow but or it doesn't work or input.txt is renamed as $datenow without being parsed.

any idea?

this might help

```
#!/bin/bash

DATE=$HOME/date.now

date +"%Y.%m.%d" > $DATE

read DATUM < $DATE

mv file.tar $DATUM.tar


```

---

### Post by PsychedelicReaction on 2007-06-23
uhm i think sbackup it's just a little too much complicated to backup 2 files

---

### Post by Freikia on 2007-06-23
You can do it in one line:

```
mv -v input.txt  `date +%F_%H-%M`
```

---

### Post by Brucevdk on 2007-06-23
Even though the others have given solutions to the problem I just wanted to indicate what exactly was wrong about your original script.
> **PsychedelicReaction said:**
> 
```
datenow= date +"%F_%H-%M"
mv -v input.txt  $datenow
```


From what I know that's not how you assign values to variables, the spaces are what's causing problems. Another reason you need backticks is because you want to assign a value returned from a command. The best way is to enclose the entire variable value in quotes and the command itself in backticks.
```

datenow="`date +"%F_%H-%M"`"

```

Other examples would be (the quotes are not necessary in the case of somenumber and somechars):
```

somenumber="123"
somechars="abc"
somesentence="a bunch of characters"

```

---

### Post by PsychedelicReaction on 2007-06-23
thank you all, seems to work.

last question about the ftp codes.

i''ve found a script online and this is what i got

```
ftp -n $REMOTESERVER <<!

quote user $USERNAME

quote pass $PASSWORD

binary

cd tesi

put tesi_$DATUM.tar

quit

```

after i uploaded these files i would like to remove the tar from the local computer so i wrote

```
rm -v tesi_$DATUM.tar
```

but all the lines after the end of the ftp session are not parsed. where's the problem?

EDIT: found the problem, i forgot ! after quit. thank you again!

---

