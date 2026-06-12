---
title: "How do you delete a folder"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by mlalich on 2006-11-13
How do you delete a folder with the rmdir command even if there are files within the folder you want to delete? I basically want to delete a folder and all of it's contents.

Thanks!

---

### Post by earobinson on 2006-11-13
rm -r <folder name>

for more info use "man rm" in the terminal

---

### Post by taurus on 2006-11-13
```
rm -rf <directory name>
```

---

### Post by CatKiller on 2006-11-13
I normally use ```
rm -rd <directory name>
``` but I second earobinson's suggestion to read **man rm** to get more information. Most programs have a manual page that you can access with **man <command name>** that contains useful information. More people should look at them.

---

### Post by dannyboy79 on 2006-11-13
when i did man rmdir it says how you can erase full directories but it doesn't work, I have tried, so at first I used to enter the dir then do rm *, then back out of the dir and do rmdir blah and it would work. man rmdir states this
Remove the DIRECTORY(ies), if they are empty.

       --ignore-fail-on-non-empty

              ignore each failure that is solely because a directory is non-empty

       -p, --parents
              Remove DIRECTORY and its ancestors.  E.g., ârmdir -p a/b/câ is similar to ârmdir a/b/c a/b aâ.

       -v, --verbose
              output a diagnostic for every directory processed

       --help display this help and exit

       --version
              output version information and exit

which doesn't tell you what to put in for --ignore-fail-on-non-empty so what do I put??? when I do man rm, then it tells me. what's up with this????

---

### Post by Endwin on 2006-11-13
I always use ```
rm -fr <DIRECTORY>
``` to remove directories.

---

### Post by Otsuko on 2006-11-13
Cant you just right click the folder to be deleted then put in trash?

---

### Post by earobinson on 2006-11-13
who knows the op may want to do this in an sh script

---

### Post by joshsherman on 2006-11-13
Remember -rf removes the file (or folder) indefinately (no return). 

-i will prompt you if you're sure and it's not a bad idea to set up a sort of wrapper to always force the -i

Might sound dumb, and you might think "well I want to indefinately kill that whole tree" but the day may come (comes like 2 times a year or so, roughly) when you end up 86ing an entire directory that you didn't want you.  I've seen it happen, and I've done it myself... 

So yeah, be very careful with -rf

Also, rmdir works if your directory is empty, i.e. if you do mkdir test; rmdir test; it will work, but if you try to remove a directory with files (let's say /home) it will error out.

Don't go deleting your /home, that'd be highly illogical.

-j

---

### Post by CatKiller on 2006-11-13
> **dannyboy79 said:**
> 
which doesn't tell you what to put in for --ignore-fail-on-non-empty so what do I put??? when I do man rm, then it tells me. what's up with this????

Yes it does. In fact, you've just said what you put here. -***x*** is often a shorter version of --*e**x**tended-option-name*. Note the one dash for the short version and the double-dash for the long version: this is fairly common.

Not that this option will delete a non-empty directory. It just won't tell you that it hasn't.

---

### Post by dannyboy79 on 2006-11-15
> **CatKiller said:**
> Yes it does. In fact, you've just said what you put here. -***x*** is often a shorter version of --*e**x**tended-option-name*. Note the one dash for the short version and the double-dash for the long version: this is fairly common.

Not that this option will delete a non-empty directory. It just won't tell you that it hasn't.

huh? where did you see in my thread that I said anything about -***x*** is often a shorter version of --*e**x**tended-option-name*??????? i'll ask a modified form of my question since what the man page says for rmdir isn't working, i tried sudo rmdir --ignore-fail-on-non-empty test, which is a folder that contains 1 file and it doesn't delete the dir nor does it even produce an error, so what do I put or is the only way to use the rm -rf function? 

also, to the guy that suggests putting a wrapper for the rm function so that it always asks if I really want to delete the file, a couple of things, is this done by creating an alias? next, if I do this, and say I cd to a dir and do rm *, assuming I have that alias setup so that rm = rm -i, is it going to confirm that I want to delete every single file???? if I have 100 files, I wouldn't want the terminal to ask, do you want to delete this, then it waits for me to type y or n, then it keeps doing that for 100 times would I? or does it only ask you once?? this question also applies to using rm -irf not with an alias, is it going to ask just once correct? i actually just answered that myself, i created a test folder and put 1 file in it, then did rm -ir test, it first asked me if I wanted to discend into the test folder, i typed y, then it said do I want to delete the test1 file, i typed y, then it said do you want to delete the test dir, i typed yes. so it sure enough does ask you about every file, so if I am sure I want to remove the dir and all of it's contents than why would I want to create an alias that's gonna ask me 100 times if I wanna delete it?? i answered some of my own questions but if you could answer the ones I didn't I would be very thankful.

---

### Post by CatKiller on 2006-11-15
> **dannyboy79 said:**
> huh? where did you see in my thread that I said anything about -***x*** is often a shorter version of --*e**x**tended-option-name*??????? 

You didn't. You said "what do I put for **rmdir --ignore-fail-on-non-empty**?" when that's exactly what you put. I thought some explanation might clear up your confusion, but obviously I was wrong.

> i'll ask a modified form of my question since what the man page says for rmdir isn't working, i tried sudo rmdir --ignore-fail-on-non-empty test, which is a folder that contains 1 file and it doesn't delete the dir nor does it even produce an error,

> **CatKiller said:**
> Not that this option will delete a non-empty directory. It just won't tell you that it hasn't.

---

### Post by macdo on 2006-11-15
Let's start from the top. 

rmdir is a command that removes empty directories. If the dir isn't empty, then rmdir con't and won't remove it. If you tell it to not tell you about failures because of non-emptyness (a failure in this case being a non-deleted directory), then it won't.

rm is a command that removes things (files, folders, links, roast chickens, the works...). If you use the option -R (or -r or --recursive), then the command will remove everything in a folder and then the folder itself. Warning : this is seriously powerful. 

Hope that helps

---

