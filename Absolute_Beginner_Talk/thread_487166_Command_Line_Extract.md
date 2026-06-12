---
title: "Command Line Extract"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-06-28
Hello. I was wondering, how do you extract tar files through the command line? Any help is appreciated, thank you.

---

### Post by Rocket2DMn on 2007-06-28
First off, you can always help yourself by checking the commands
```
man tar
```
To answer your question, if the file is uncompressed (.tar)
```
tar -xvf filename.tar
```
if it is compressed (.tar.gz or .tgz, etc...)
```
tar -xzvf filename.tar.gz
```

---

### Post by bodhi.zazen on 2007-06-28
I add this to ~/.bashrc :

> # Extract files from any archive
# Usage: ex <archive_name>

ex () {
     if [ -f $1 ] ; then
        case $1 in
                *.tar.bz2)   tar xjf $1        ;;
                *.tar.gz)    tar xzf $1     ;;
                *.bz2)       bunzip2 $1       ;;
                *.rar)       rar x $1     ;;
                *.gz)        gunzip $1     ;;
                *.tar)       tar xf $1        ;;
                *.tbz2)      tar xjf $1      ;;
                *.tgz)       tar xzf $1       ;;
                *.zip)       unzip $1     ;;
                *.Z)         uncompress $1  ;;
                *.7z)        7z x $1    ;;
                *)           echo "'$1' cannot be extracted via extract()" ;;
        esac
     else
        echo "'$1' is not a valid file"
     fi
}

# Thanks to rezza at Arch Linux

Then extract any archive with :

ex <archive>

---

### Post by kevCast on 2007-06-28
Thank you, and sorry. I was looking at the usage text for 45 minutes and it wasn't clicking.

:/

---

### Post by Rocket2DMn on 2007-06-28
That's pretty sweet bodhi.zazen, I think I might give that a go, too.  
For kevCast: That's a great little tool bodhi has provided for us - it will do the extraction for us depending on the file type.  You should, however, learn what the differences are, you might not always have access to this (like if you're on somebody else's computer).
Thanks bodhi

---

### Post by bodhi.zazen on 2007-06-28
> **Rocket2DMn said:**
> That's pretty sweet bodhi.zazen, I think I might give that a go, too.  
For kevCast: That's a great little tool bodhi has provided for us - it will do the extraction for us depending on the file type.  You should, however, learn what the differences are, you might not always have access to this (like if you're on somebody else's computer).
Thanks bodhi

he he he ... And it is faster then xarchiver :)

You are most welcome. If you look close you can see it can be shortened by two lines, but heck I'm lazy :rolleyes:

---

### Post by ameeno on 2008-07-12
thanks bodhi zazen.. ur a star!

---

