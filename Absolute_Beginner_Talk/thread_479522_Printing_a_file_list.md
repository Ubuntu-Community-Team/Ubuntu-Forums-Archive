---
title: "Printing a file list?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by fjf on 2007-06-20
How do you print the list of files in a folder or a recently burned DVD?.  The ls command lists the files, but I cannot find any option to send it to the printer.

---

### Post by dreadlord_chris on 2007-06-20
you could redirect the output to a file:
```

ls -la > files.txt

```
then print the file
actually, I think you could do it with:
```

ls -la | lpr

```
as long as the default printer was configured.

---

### Post by fjf on 2007-06-21
Hey, it works!!.  Thankyou!

---

### Post by dreadlord_chris on 2007-06-21
> **fjf said:**
> Hey, it works!!.  Thankyou!

My pleasure :p

---

### Post by Golyadkin on 2007-06-21
Be careful with that though, I once made a typo and piped a binary through lpr with this command ( less instead of ls ) which resulted into a network printer dumping out 120 pages of gibberish before the paper ran out :$

---

### Post by LaRoza on 2007-06-21
I wrote a program which prints out a directories contents (subdirectories and their files), and saves the results in an easy-to-read document. 

I could e-mail the program to you if you send me one with your address. I do not have it with me at them moment, so you'd have to wait until tomorrow, unless you want the Windows version, which might run in Wine.

It is a simple program, but it works.

---

### Post by dreadlord_chris on 2007-06-21
> **Golyadkin said:**
> Be careful with that though, I once made a typo and piped a binary through lpr with this command ( less instead of ls ) which resulted into a network printer dumping out 120 pages of gibberish before the paper ran out :$

lol... I bet that was fun

---

