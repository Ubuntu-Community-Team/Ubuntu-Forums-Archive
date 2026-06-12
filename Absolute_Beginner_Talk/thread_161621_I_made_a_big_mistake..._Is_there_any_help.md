---
title: "I made a big mistake... Is there any help?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-04-17
Hi, I tried to change permission of my hard disk and i typed ```
chmod -R 766 /media/hdb1/ 
```

Now not only the pemission isn't adjusted, but all the files on my harddisk are suddenly of an unknown type, and i can't do anything with them

Is there any way i can undo this?
And what was my misstake?

---

### Post by macdo on 2006-04-17
I don't know how to fix that, but I can tell you that the mistake was that you changed the permissions of all files to read/write/Execute for root, and read/write for group and user... That's what the R in your command does. You can't (as a user) do anything because you no longer have execute permissions on any application on your hdb. 

I have a sneaking suspicion - but confirm this, someone - that it would be faster and easier to reinstall ubuntu - especially if you haven't got much data or your data is on another partition.

If you have got data, you could copy it to another partition first from the command line using sudo. Be careful, root has execute pemission for every single file on that partition.
Good luck!

---

### Post by mostwanted on 2006-04-17
Log in from GRUB with the recovery option (just below the regular option). Change permissions to 777 or or something like that.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=macdo]
I have a sneaking suspicion - but confirm this, someone - that it would be faster and easier to reinstall ubuntu - especially if you haven't got much data or your data is on another partition.[/QUOTE]
Depends on the partition. What do you use /media/hdb1/ for?

[quote=mostwanted]Change permissions to 777 or or something like that.[/quote]
may create security issues (writable by everyone).

---

### Post by fdoving on 2006-04-17
I would suggest:
[CODE]
chmod -R a+rX foo/
[/CODE
That will make dirs 755 and files 644.
Now you'll have to chmod +x all files you want to be executable, if any.

---

### Post by GarethMB on 2006-04-17
Can you not use a root nautilus to change the permissions via properties?

---

### Post by fdoving on 2006-04-17
Yes,  you can. But I find the commandline much more powerfull in situations like this.

- Frode

---

### Post by Ecthelion on 2006-04-18
Just starting up your computer seems to be enough...
And even the permissions are OK!

Anyway thanks for your help guys!

---

