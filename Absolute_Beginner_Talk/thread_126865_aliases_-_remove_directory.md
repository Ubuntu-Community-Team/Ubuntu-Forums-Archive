---
title: "aliases - remove directory"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by Grae on 2006-02-07
i've searched the forum and not found what i'm looking for. I want to be able to have rm interactive for single files and a command rmdir which is interactive in as much as it says "are you sure you want to remove dir" but only for the directory i ask it to delete, i don't want to have to confirm all its contents aswell.

so far i've got:

alias rmdir='rm -dr'
alias rm='rm -i'

but rmdir asks me to confirm every file.

Any ideas, someone must have achieved this!

---

### Post by skirkpatrick on 2006-02-07
Add f to your rmdir options, it'll force deletion.  If I want to delete a directory and all it's files, I always use **rm -fR <dir_name>**.

---

### Post by Grae on 2006-02-07
That's not quite what I want, I want it to ask if I'd like to remove the directory but not then continue to ask about each file or directory in its contents

---

### Post by skirkpatrick on 2006-02-07
Hmm, nothing I tried seems to work.  Maybe a script?

---

### Post by Grae on 2006-02-08
Hmm, so any ideas on a script then guys?

---

### Post by cwaldbieser on 2006-02-08
[QUOTE=Grae]Hmm, so any ideas on a script then guys?[/QUOTE]
How's this for a start?
```

#!/bin/bash

if [ -d $1 ]; then
   echo "Do you really want to delete the folder $1?"
else
   echo "$1 is not a directory." 1>&2
   exit 1
fi
read PROMPT
if [ $PROMPT == 'Y' ] || [ $PROMPT == 'y' ]; then
   echo "deleting $1..."
   #Insert command to do actual delete here.
fi
exit 0


```

---

### Post by Grae on 2006-02-09
Thanks that's the kinda thing I wanted

---

