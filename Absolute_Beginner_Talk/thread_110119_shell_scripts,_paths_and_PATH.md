---
title: "shell scripts, paths and PATH?"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by nsa_767 on 2005-12-30
I've created a shell script which executes a perl and awk script:
> 
#!/bin/bash

cd / ; cd /home/me ; cd futures_data ; perl retrieve.pl ; gawk -f commo.awk today ; echo "DATA GATHERED"

I've placed this in a directory /home/me/bin and if I cd to that directory and execute this script (. gather.sh) it all works as it should.

OK, so now I do the following:
```
PATH=${PATH}:/home/me/bin
```
But, if I now execute the script from outside the directory /home/me/bin, then it complains about not being able to find commo.awk.... 
```
[me@localhost ~]$ gather_data.sh
Can't open perl script "retrieve.pl": No such file or directory.
Use -S to search $PATH for it.
gawk: fatal: can't open source file `commo.awk' for reading (No such file or directory)

```
What is wrong with this? Why does it not work now?

Oh, any pointers about refining the script are welcome... This is my first shell script... I think I'm love shell scripting!

---

### Post by Suger on 2005-12-30
1 - What are the uses of the 2 first cd ?

Try modifying to
```

#!/bin/sh
cd /home/me/futures_data
perl retrieve.pl
gawk -f commo.awk today
echo "DATA GATHERED"

```
(easier to read this way)
don't forget to chmod +x /home/me/bin/gather_data.sh

Oh, and were are your retrieve.pl and commo.awk files stocked ?

---

### Post by nsa_767 on 2005-12-30
Wow, that does look a lot cleaner, and it works now.... Oh, retrieve.pl and commo.awk files are in /home/me/futures_data.

Now that this works, I need to add it to my bashprofile? Right, eh???

Thanks for helping me so far.... I'm alos planning on setting up a cron job to run this three times a day....

---

### Post by Suger on 2005-12-30
yes, you have to add /home/me/bin (or ~/bin) to the PATH of your .bash_profile

For the cron tables, you will use crontab -e (and not sudo crontab -e : /home/me/bin is not in roout's path)

---

### Post by nsa_767 on 2005-12-30
I opened .bash_profile, and it seems as if the require entry is already there:
```

# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

# User specific environment and startup programs

**PATH=$PATH:$HOME/bin**

export PATH
unset USERNAME

```

Thanks for all your help.

---

### Post by Suger on 2005-12-30
yes it is. Sorry, I'm using tcsh and set my profile so long ago I don't remember what was already in from what I added.

---

