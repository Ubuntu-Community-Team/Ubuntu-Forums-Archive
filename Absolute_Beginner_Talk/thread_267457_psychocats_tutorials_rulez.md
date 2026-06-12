---
title: "psychocats tutorials rulez"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-28
listen here noobiez

go to [http://www.psychocats.net]("http://www.psychocats.net")
!!!this site will get you going quickly!!!

anyway,
im going through a few commands on the terminal.
i created a folder called deleteme to scrap
when i type rm /blah/blah/blah/deleteme 
it say cant delete file is directory

instead of rm i should use....

rmdr or somthing??
rmdr dont work

so i need the command for deleting directorys plz.
thnx

---

### Post by uk_sphinx on 2006-09-28
or better still is there a command that will list all commands available

kind of like "help" on the xp terminal?  u know ms.dos

---

### Post by bulldog on 2006-09-28
Try ```
 rm -r 
```

---

### Post by UCAP on 2006-09-28
rmdir is the command you are looking for

---

### Post by aysiu on 2006-09-28
I believe *rmdir* can delete only empty directories. Is that correct, anyone?

To delete directories that are full, you'd use the ```
rm -rf /directoryname
``` command

I think for removing and deleting things, I would refrain from using the terminal--it's too powerful. If you type the wrong command or hit the Enter key too early, you might end up doing something you regret.

Much better to delete through the graphical interface.

---

### Post by uk_sphinx on 2006-09-28
r they both the same?

---

### Post by aysiu on 2006-09-28
Are which both the same?

---

### Post by uk_sphinx on 2006-09-28
i know but i want to memorize all the command or at least get a good grasp on them even if i dont use them that much

do you know about the listing commands i asked earlier?

---

### Post by uk_sphinx on 2006-09-28
rm - and rmdir commands


oops you already said

---

### Post by aysiu on 2006-09-28
I believe if you hit the **Tab** key twice, it'll list all commands... maybe I'm wrong about that.

---

### Post by aysiu on 2006-09-28
> **uk_sphinx said:**
> rm - and rmdir commands


oops you already said
*rm* removes files.

*rmdir* removes empty folders.

If you have full folders, you can remove them with the command *rm -rf*

The *-r* tag means the deletion is recursive.
The *-f* tag forces a removal.

More info here:
[http://www.pvv.ntnu.no/~steinl/vitser/rm.html](http://www.pvv.ntnu.no/~steinl/vitser/rm.html)
[http://www.hmug.org/man/2/rmdir.php](http://www.hmug.org/man/2/rmdir.php)

---

### Post by echo $USER on 2006-09-28
> **aysiu said:**
> I believe *rmdir* can delete only empty directories. Is that correct, anyone?

To delete directories that are full, you'd use the ```
rm -rf /directoryname
``` command

I think for removing and deleting things, I would refrain from using the terminal--it's too powerful. If you type the wrong command or hit the Enter key too early, you might end up doing something you regret.

Much better to delete through the graphical interface.

Yeah, but you can use rm -r instead (without the -f) so the terminal will prompt you for every file to make sure you want to delete it, but I'm sure you know that, they might not).  Its much more safer than using nautilus to delete.

---

### Post by uk_sphinx on 2006-09-28
yeah tab 2 works but it dont give a description

theres over 1300 
maybe i wont learn them all

---

### Post by uk_sphinx on 2006-09-28
yeah il use nauticlus but im just experimenting

---

### Post by skymt on 2006-09-28
I just Googled "list of linux commands" and found [this](http://www.ss64.com/bash/).

---

