---
title: "Command line trouble"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-27
Hi..... I have created several folders in my Home folder that I have spaces in such
as My Music, My Photos, My Programs, ect.  I am having trouble opening up
these folders in the command prompt.  I've tried with the spaces, putting an _
between the name, putting a - between the words. I just can't get into that directory.
Should I have not put spaces in the names of the folders...... Does Linux not like
this as DOS did back in the day?

---

### Post by taurus on 2007-10-27
```
cd ~/"My Music"
cd ~/"My Photos"
cd ~/My\ Programs
```

---

### Post by markharding557 on 2007-10-27
ive just tested this and get the same thing i would remove the spaces you should have no problem then

---

### Post by Maestro23 on 2007-10-27
> **Orbital75 said:**
> Hi..... I have created several folders in my Home folder that I have spaces in such
as My Music, My Photos, My Programs, ect.  I am having trouble opening up
these folders in the command prompt.  I've tried with the spaces, putting an _
between the name, putting a - between the words. I just can't get into that directory.
Should I have not put spaces in the names of the folders...... Does Linux not like
this as DOS did back in the day?

Use " ".

> Ex:  mkdir "My Docs"

Then when you need to get into it:

cd "My Docs"



---

### Post by Orbital75 on 2007-10-27
Interesting......... so I can use  

cd ~/"My Music"  or  cd "My Docs"

Thanks.... I understand that ~ means home right?
So is it that Linux can't understate a command path with
spaces with out adding " " 

Thanks for the help guys, it was making me rip my hair out.
I'm kinda new to linux so you'll have to forgive my ignorance.
Is it bad practice to add spaces?

I'd like to pick your brain for one more thing.
If I'd like to open a txt file called MyResume.txt with gedit
what would be the command.... I'd like to learn to open files
with a program of my choosing from the command line.

Thanks

---

### Post by taurus on 2007-10-27
Or you can put a \ between the space like 

```
cd ~/My\ Music
```

```
gedit MyResume.txt
```
Assuming you are in the directory where that file is.

---

### Post by Orbital75 on 2007-10-27
that worked Great.....  It's been so long since I used a command line that I am trying to
learn again.  I keep entering in the Slashes in the wrong direction out of habit.  :)

Ask asked earlier, Is it bad practice to add spaces between words.
Is it something that is frowned upon?

---

