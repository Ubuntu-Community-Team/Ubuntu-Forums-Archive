---
title: "Learning the Shell Commands"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by trobn76 on 2007-01-07
I am very unfamiliar with using a command prompt, and as a result I need very basic, small broken-down step by step instructions.

I am just learning the shell commands and I am having a problem using the mv (move) command, here is what I don't understand: I have successfully moved a folder (directory) from my home folder to the desktop by typing this in the terminal : mv *foldername* Desktop  (no period on purpose) That was just an expieriment and now I want to move that (and any other file I wish) from the Desktop directory back to my home folder (the Desktop folder is located in my home folder). I tired typing this: mv *filename* jordan (that's my home folder's name). I triple-checked the spelling of my own name and that it was lower-case like it is on the computer and it didn't move the file; instead it renamed it, jordan. This is confusing to me, what did I do wrong? I was in the /home/jordan directory so I tried this: cd Desktop and then tried the same command to move the file to it's original place and that didn't work either. I am using Ubuntu Dapper Drake Power PC version. Thanks for reading.

---

### Post by Simran on 2007-01-07
A nice basic guide which i used: [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)


Enjoy :)

---

### Post by IYY on 2007-01-07
Here is how mv works:

Suppose you issue a command

```
mv */path/to/source* */location/of/destination*

```

The action would be to move the file from *source* to *destination*.

If *source* is a file and *destination* is a directory, it will move the file *source* into the directory *destination*.

If both *source* and *destination* are directories, or both *source* and *destination* are files, it will overwrite destination with source. This is often used for renaming files.

But enough with theory. Your problem is a simple one. The command you issued was:

```
mv filename jordan
```

This tells me that you were currently in the directory in which the file *filename* resides. Paths in Linux can be given in two ways: either it is the complete path starting with a slash (/) or a relative path, starting from your current directory. Since you did not write a slash, your command was interpreted as:

```
mv /your/current/directory/filename /your/current/directory/jordan
```

another way of writing it is 

```
mv ./filename ./jordan
```

clearly the effect is renaming filename to jordan. What you actually wanted to do is this:


```
mv filename /home/jordan
```

---

### Post by madmetal on 2007-01-07
and another helpfull site..
[http://tldp.org/](http://tldp.org/)

---

### Post by trobn76 on 2007-01-07
Thanks for the helpful site -- will investigate.

---

### Post by trobn76 on 2007-01-07
Yours has been the most helpful, IYY for this reason, "I am very unfamiliar with using a command prompt, and as a result I need very basic, small broken-down step by step instructions." You actually read that part of it -- no offense to anyone else, just praise to IYY. Yes I see the error in my thinking -- I had read about relative vs specific file pathnames and I just entered the filename and where I wanted it to go, however, I did not think about the fact that I was not in the right directory to just give the filename so next time I will be more specific -- thanks for helping me with this problem.

---

### Post by Delkster on 2007-01-07
If you want to refer to your home directory/folder on the command line, the character ~ is interpreted as pointing to your home directory. Thus, you could also have entered
```
mv filename ~
```
Since the target is an existing directory, it moves the file or directory named *filename* into it.

The tilde (~) character can also be used as part of a longer directory description; for example ~/Desktop means /home/username/Desktop, i.e. your desktop folder.

---

### Post by Delkster on 2007-01-07
> **IYY said:**
> If *source* is a file and *destination* is a directory, it will move the file *source* into the directory *destination*.

If both *source* and *destination* are directories, or both *source* and *destination* are files, it will overwrite destination with source. This is often used for renaming files.

A small correction:

1. If *target* is a directory that already exists, the command will move *source* into it regardless of what *source* is -- even if it's another directory.

2. If, on the other hand, *target* doesn't exist, *source* is renamed to *target*. That won't change the type of the file so the resulting *target* will be a directory if *source* is a directory, and so on.

3. If *target* exists and is a regular file (not a directory), and *source* is a regular file (not a directory), *source* will be renamed to *target* and will overwrite whatever was previously called *target*. If *source* is a directory and *target* is an existing regular (non-directory) file, **mv** will refuse to perform the action because it can neither rename *source* into *target* without changing the type of *target* (like in case 2) nor move *source* inside *target* (like in case 1) because *target* isn't a directory.

---

### Post by IYY on 2007-01-07
Hm. I just re-read my post and realized that you are indeed correct. ](*,)

---

