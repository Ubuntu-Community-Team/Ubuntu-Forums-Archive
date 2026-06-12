---
title: "how to show hidden files in terminal?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by grumby on 2007-11-27
like in the title, i'm new to my kubuntu 6.06 Dapper, and need to get to hidden files and dirs in terminal. what's the trick?

---

### Post by jordanmthomas on 2007-11-27
In the terminal, to list all the files including hidden files, do this:
```
ls -a
```
the -a means "all"

---

### Post by Inxsible on 2007-11-27
```
ls -la
```

---

### Post by grumby on 2007-11-27
oki, thx for fast help!

---

### Post by jordanmthomas on 2007-11-27
> **Inxsible said:**
> ```
ls -la
```
I see people use -la a lot when describing this.  Is there any reason other than preference to put the -l?  

You can tell the difference in regular files and directories by color anyway.
Just wondering..

---

### Post by w7kmc on 2007-11-27
The -l is simply for a long listing.  You get the times the file was last changed and their sizes as well.

My personal favorite:

ls -latr

Which lists everything recursively by age.  The newest modified file is on the bottom...the oldest on top...

---

### Post by jordanmthomas on 2007-11-27
I know what the -l is for, but why include it when someone just asks to see hidden files?
I think it makes it harder to read sometimes because you have to scroll through the list to see everything.  With just ls -a it makes several columns so you can usually see it all in one screenful.

**edit**
also, ls -latr doesn't recursively list anything.   You'd want -R for that.

---

### Post by Inxsible on 2007-11-27
> **jordanmthomas said:**
> I see people use -la a lot when describing this.  Is there any reason other than preference to put the -l?  

You can tell the difference in regular files and directories by color anyway.
Just wondering..
The l option also gives you the permissions and such including the owner and group of the files/directories. Its just the long listing of the files in case you need it.

---

### Post by jordanmthomas on 2007-11-27
So you just use it because you prefer it?  I still am kind of confused as to why people always say to use -la for listing hidden files.

Do you see what I'm saying?  I feel like I'm not being clear and you think I just don't know what the -l does.

---

### Post by Inxsible on 2007-11-27
> **jordanmthomas said:**
> So you just use it because you prefer it?  I still am kind of confused as to why people always say to use -la for listing hidden files.

Do you see what I'm saying?  I feel like I'm not being clear and you think I just don't know what the -l does.Well, when I posted, the two messages above were not there :)

Yeah, its just a preference. I never use only ls either. That way, I always have the info I need. so getting hidden files is -la (for me) even if I wanted to use other options for ls, I think I would always have the l option

---

### Post by jordanmthomas on 2007-11-27
Ok, glad to know I wasn't just missing something obvious or something.  :)

---

