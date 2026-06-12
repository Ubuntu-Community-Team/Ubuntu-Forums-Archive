---
title: "[SOLVED] Can't extract *.tar.gz, &amp;quot;no such file&amp;quot;"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by cjv998 on 2007-11-30
Hi everyone, I tried searching around for a solution to my problem, and I was surprised that I couldn't find one.  I'm having trouble with .tar.gz files, specifically extracting them.  Here's what comes up when I try to extract a file that's placed on my desktop (The Lexmark Z600 printer driver, in this case, but it's happened whenever I try to extract a .tar.gz file).

```
chris@chris-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

``` 

I know you don't always have to use .tar.gz files, but according to the how-to I read ([http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)), that's the way I have to install the printer driver.  What's going wrong here?

---

### Post by wormser on 2007-11-30
The error " No such file or directory" make me believe you are not in the same directory as the file.  If you are not in the same directory when running a command you need to specify the whole path.  Like /home/username/Desktop/filename.   Try opening a shell:

```
cd Desktop
```
Then run your command.

---

### Post by Drate on 2007-11-30
unless of course you downloaded the file elsewhere, then "cd" to there.  Firefox does by default download to Desktop though.

---

### Post by eolson on 2007-11-30
if all else fails try 

gzip -d    filename

---

### Post by lespaul_rentals on 2007-11-30
Do you have the case exactly the same?  You might try dragging-and-dropping the file into the Terminal, then select paste, that way you know it's right.

---

### Post by cjv998 on 2007-11-30
> **lespaul_rentals said:**
> Do you have the case exactly the same?  You might try dragging-and-dropping the file into the Terminal, then select paste, that way you know it's right.

This did it.  I figured out what my problem was...this was user error.  I saw the "chris-desktop" and assumed that meant I was in the "desktop" folder...I forgot that chris-desktop is my computer's name. :lolflag:  So turns out I never was in the desktop folder, I just had the impression that I was.  Stupid mistake, but everything's smooth as butter now...I even got my printer working!  Thanks everyone!

---

### Post by wormser on 2007-11-30
> **cjv998 said:**
> This did it.  I figured out what my problem was...this was user error.  I saw the "chris-desktop" and assumed that meant I was in the "desktop" folder...I forgot that chris-desktop is my computer's name. :lolflag:  So turns out I never was in the desktop folder, I just had the impression that I was.  Stupid mistake, but everything's smooth as butter now...I even got my printer working!  Thanks everyone!

That "chris-desktop" had me a bit confused too.  But, I have seen that error message before and it is always solved by CDing into the right directory.  Mark the thread as Solved.  Directions are in my signature.

---

### Post by poudin on 2007-11-30
could edit your machine name in /etc/hosts...to prevent it from happening again...

we've all been there before.

---

