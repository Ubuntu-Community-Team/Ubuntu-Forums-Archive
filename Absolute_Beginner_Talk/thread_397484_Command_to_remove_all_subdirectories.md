---
title: "Command to remove all subdirectories"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by chymo on 2007-03-30
I'm looking for a command that will search through a few levels of directories and remove one specific recurring directory and it's contents.  

How can this be done?  

I tried rm -r dirname but that didn't work.  I also didn't see any flags on the rmdir command which would work.

---

### Post by yabbadabbadont on 2007-03-30
Let's say that the directory that you want to remove is called "stuff" and that it occurrs multiple places in a specific directory tree.  As long as you want to remove every occurrance of "stuff" and all it's contents, then this should do it for you:
```
find /path/to/top/of/tree -type d -name stuff -exec rm -rf {} \;
```
Be **VERY** careful with that command.

---

### Post by chymo on 2007-03-30
It worked, now could you explain what the heck all that means?  ;-]

The output displayed: "No such file or directory" for every directory that was removed.  

Thanks!

---

### Post by yabbadabbadont on 2007-03-30
I don't know why it printed out that message, but I'm glad it worked.  OK, now for the explanation.  Open a terminal window and run "man find".  :D

Ok, Ok, enough joking.

It says, starting at "/path/to/top/of/tree", find all directories "-type d", that are named stuff "-name stuff", and run the following command on them "-exec rm -rf {}".  "{} is replaced by the item that matches all the parameters when the "rm -rf" command is run.  The "\;" is needed to terminate the "rm -rf" command in this case.  "rm -rf" says to remove, recursively "-r", and force removal without question (if possible) "-f", the object listed as a parameter.

Edit: It probably printed out that warning message because I didn't include the "-depth" option with the find command.

---

### Post by chymo on 2007-03-30
Ladies and Gentlemen, er... Nevermind.  I have just witnessed The True Power Of Linux.  

See this is the type of thing I'm after.  Being able to mesh commands when I need to do something like this.  I'll keep readin' Thanks yabbadabbadont!

---

### Post by Maestro23 on 2007-03-30
> **chymo said:**
> Ladies and Gentlemen, er... Nevermind. [COLOR="Red"] I have just witnessed The True Power Of Linux.  
[/COLOR]
See this is the type of thing I'm after.  Being able to mesh commands when I need to do something like this.  I'll keep readin' Thanks yabbadabbadont!


Welcome to the Dark Side. :guitar:

---

### Post by yabbadabbadont on 2007-03-30
> **chymo said:**
> See this is the type of thing I'm after.  Being able to mesh commands when I need to do something like this.

Here is a better example of chaining commands together ;)
```
curl --cookie "$ScriptDir"/sexydesktop.co.uk-cookies.txt \
http://www.sexydesktop.co.uk/index.htm 2>/dev/null | \
sed -f "$ScriptDir"/iso2html |\
grep -i "wallpaper listing" | \
sed "s/^.*[wW]allpaper [lL]isting//" | \
sed "s/<BR>/\n/g" | grep "<a href=" | \
sed "s/^.*='//" | \
sed "s/'.*//" | \
sort -u | \
sed "s/.htm$//" > BabeIndexList
```

Oh, and you're welcome.

---

