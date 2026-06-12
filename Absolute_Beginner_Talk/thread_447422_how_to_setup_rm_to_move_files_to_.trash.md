---
title: "how to setup rm to move files to .trash"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-18
is there a way to send files to the trash bin when i type rm?  or, is there a way to retrieve files if i do rm <some file>?

---

### Post by earobinson on 2007-05-18
Im willing to bet no, and even if there was a way you wouldn't want to do it since many programs may rely on rm.

---

### Post by sthapit on 2007-05-18
fair enough.  is there another command i can use, or is there a way i can create a command (e.g. erase or delete) that would send files to the trash?

---

### Post by earobinson on 2007-05-18
I have been thinking about it but im not sure

---

### Post by earobinson on 2007-05-18
> **sthapit said:**
> fair enough.  is there another command i can use, or is there a way i can create a command (e.g. erase or delete) that would send files to the trash?
```
 mv rmtest ~/.Trash/
``` will do it but thats a bit cumbersome

---

### Post by trent dillman on 2007-05-18
...

---

### Post by earobinson on 2007-05-18
> **earobinson said:**
> ```
 mv rmtest ~/.Trash/
``` will do it but thats a bit cumbersome
Its not the best script and a bit of a hack but you can download [http://www.edwardandrewrobinson.com-a.googlepages.com/trash.sh](http://www.edwardandrewrobinson.com-a.googlepages.com/trash.sh), and then browse to the same dir as the you save the file then do a ```
 ln -s trash.sh /bin/trash
chmod +x trash.sh
``` And then you should be able to do [code]trash <filename>[/trash] to move a file to the trash.

---

### Post by trent dillman on 2007-05-18
...

---

### Post by earobinson on 2007-05-18
> **trent dillman said:**
> Heh, our scripts are almost identical :-)

I used "$*" so multiple files could be deleted
Yours is better! Thats why open source is so great

Edit: Updated mine.

---

### Post by jpk on 2007-05-18
another way is to put this "function" in your .bashrc / .bash_aliases:

```

function rm() { 
    mv -f $* ~/.Trash/; 
}

```

---

### Post by mrchaotica on 2007-05-18
I hate to break it to you guys, but those simple trash scripts aren't sufficient. In addition to actually moving the file to the trash directory (or rather $TRASH/files), the program should *also* create an entry in $TRASH/info describing the original location of the file, etc. There's actually an entire [specification]("http://www.ramendik.ru/docs/trashspec.html") to implement!

---

### Post by sthapit on 2007-05-29
> **jpk said:**
> another way is to put this "function" in your .bashrc / .bash_aliases:

```

function rm() { 
    mv -f $* ~/.Trash/; 
}

```

where do i find  .bashrc / .bash_aliases?

---

### Post by eentonig on 2007-05-29
> **mrchaotica said:**
> I hate to break it to you guys, but those simple trash scripts aren't sufficient. In addition to actually moving the file to the trash directory (or rather $TRASH/files), the program should *also* create an entry in $TRASH/info describing the original location of the file, etc. There's actually an entire [specification]("http://www.ramendik.ru/docs/trashspec.html") to implement!

Don't hate to break it to us. I know I for one am very happy to read this from you. Now at least, I know I need to review my script.

---

### Post by earobinson on 2007-05-29
Yup, maybe when I have some time ill make the whole thing work

---

### Post by jpk on 2007-05-31
> **sthapit said:**
> where do i find  .bashrc / .bash_aliases?

you should find .bashrc in your home directory, it's startup script for bash shell. You can then create another file .bash_aliases in the home directory and source it from .bashrc. Here is a cut from my .bashrc showing how to include .bash_aliases:
```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

---

### Post by original_jamingrit on 2007-05-31
I've been wondering about this very same thing, this is a handy thread, thanks!

---

### Post by pk386 on 2007-06-02
I just read some of the "linux haters hand book" and he devotes almost all of chapter 2 to this problem :lolflag:

I think I'll start moving files to .Trash instead of rm'ing them...:KS

---

### Post by Endolith on 2007-12-15
Can this be built into Ubuntu by default?  The regular rm command is far too destructive for a user-friendly OS.  Just see [http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54).  Hotwire shell even overwrites the "rm" command to make it send things to the trash.

---

### Post by Endolith on 2007-12-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/176489](https://bugs.launchpad.net/ubuntu/+bug/176489) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Filed a bug.

---

