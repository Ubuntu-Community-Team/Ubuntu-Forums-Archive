---
title: "noob question: what is PATH?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-09-12
... and can someone explain how to read the output of ```
echo $PATH
```?  What is the format?  How do I add a folder to my path?

if it's already been answered, please point me to the link.  I searched here on "path" and got too many results.

thanks,

-steve

---

### Post by fritz_monroe on 2006-09-12
[Here's]("http://www.troubleshooters.com/linux/prepostpath.htm") a link to more info, but basically, to add an additional directory to the end of PATH, you would do this.

```
PATH=$PATH:/data/myscripts
```

---

### Post by robins_web on 2006-09-12
Doing it that way sets your PATH until you log out. You can make it permanent by adding that same line in your .bash_profile file.

---

### Post by robins_web on 2006-09-12
Doing it that way sets your PATH until you log out. You can make it permanent by adding that same line in your .bash_profile file, which is in your home directory (/home/yourloginname

---

### Post by mike3k on 2006-09-12
I found these two useful functions for adding an item at the beginning or end of the path, while preventing duplicate items from being added:

```

append_path()
{
  if ! eval test -z "\"\${$1##*:$2:*}\"" -o -z "\"\${$1%%*:$2}\"" -o -z "\"\${$1##$2:*}\"" -o -z "\"
\${$1##$2}\"" ; then
    eval "$1=\$$1:$2"
  fi
}

prepend_path()
{  if ! eval test -z "\"\${$1##*:$2:*}\"" -o -z "\"\${$1%%*:$2}\"" -o -z "\"\${$1##$2:*}\"" -o -z "\
"\${$1#
#$2}\"" ; then
    eval "$1=$2:\$$1"
  fi
}


```

if you add that code to your .bashrc or .bash_profile, you can do something like this:

```

append_path PATH ~/bin
append_path PATH /usr/local/bin
append_path PATH /usr/X11R6/bin

if [ -d /usr/local/gp2x ]
then
    append_path PATH /usr/local/gp2x/bin
    append_path MANPATH /usr/local/gp2x/man
fi

```

---

### Post by stevieb on 2006-09-13
so in my case, i would write in terminal ```
PATH=$PATH:/usr/local/RealPlayer/./realplay
```
is that right?
-steve

---

### Post by skymt on 2006-09-13
> **stevieb said:**
> so in my case, i would write in terminal ```
PATH=$PATH:/usr/local/RealPlayer/./realplay
```
is that right?
-steve

What's the dot doing in there? I think it would be:```
PATH=$PATH:/usr/local/RealPlayer
```"realplay" is the program itself, right? $PATH only makes sense with directories, not individual files.

For that matter, why not create a link to realplay in /usr/local/bin, which is (probably) already in your path:```
sudo ln -s /usr/local/RealPlayer/realplay /usr/local/bin/
```

---

