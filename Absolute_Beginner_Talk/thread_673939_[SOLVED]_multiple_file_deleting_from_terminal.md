---
title: "[SOLVED] multiple file deleting from terminal"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by duruttye on 2008-01-21
So, I'm just wondering.

I installed something a while ago, have no use for it, now I'm unable to uninstall it. Neither with synaptic, nor with sudo  aptitude remove, nor with Add/Remove.

I read somewhere that simply deleting the files of an application will uninstall it. I searched with slocate and found numerous files. The question is that can I remove them with one command even is they are not in one folder?

I cannot type in rm /path/to/file1 /path/to/file2 and so on.
The command I'm looking for is:
rm all the files containing the name: XY

The reason for this is that I have limited space on my drive.

Any suggestions will be greatly appreciated.

thanx

---

### Post by frup on 2008-01-21
rm *apple* will delete ANY file that contain apple in the name doing rm -f *apple* will force it. Adding sudo in front will make sure it happens and adding -R (eg -Rf) will force it and delete any files inside a folder called *apple*. * is a wild card so *apple* could delete something called mapples as well as a file called apple. Do this wisely and make sure you don't delete anything by accident.

---

### Post by banewman on 2008-01-21
rm is very powerful so I'm not suprised that reading "man rm" shows no option for that.
It looks like it might be one file at a time...
:)

---

### Post by duruttye on 2008-01-21
Okey.
Then my next question is: does slocate find all the files which will be deleted by that wildcard?

Meaning that right now, what slocate finds I have no use for (I think :)), so rm can find more?

Hope not :)

---

### Post by hyper_ch on 2008-01-21
also something like this could be used:

```

locate XYZ | xargs -0 rm

```

BUT there might be two issues:

(1) slocate db is not up-to-date so the desired files are not to be found
solutino:
```

sudo updatedb

```

(2) locate may return too much.

When searching for XYZ locate will also return aXYZ and XYZb and aXYZb and so on....

first run a single:
```

locate XYZ

```

to get the output.

---

### Post by duruttye on 2008-01-21
This answers my question!

Thanx guys for the really quick answers!!

---

### Post by hyper_ch on 2008-01-21
instead of "locate" you could also run "find" which has a lot more options (but is also a lot more complicated to use). However with find you can do some amazing things. Best to google it up....

---

### Post by duruttye on 2008-01-21
Well, forgot to tell you, that I'm kindda new to the terminal.

so:

```
sudo rm *vive*
rm: cannot remove `*vive*': No such file or directory

```

I cd-ed to the root directory...

What now? What am I doing wrong?

---

### Post by hyper_ch on 2008-01-21
What are you trying to delete?

(And where)

---

### Post by duruttye on 2008-01-21
The application called "vive".

There are like 30 files found in several different folders.

I'm not to lazy to delete them one-by-one, I'm trying to learn too :)

---

### Post by hyper_ch on 2008-01-21
well, by running this command:

```

sudo rm *vive*

```

It only tries to delete any "vive" in the current folder.

---

### Post by mister_pink on 2008-01-21
Ah this is so useful. I was annoyed that you couldn't pipe filenames to rm, so I made a script that looped through to delete files. But with xargs I can delete annoying windows leftovers with ease:
```
find . | grep desktop.ini|xargs -d '\n' rm
find . | grep Thumbs.db|xargs -d '\n' rm
```

I imagine you can use a similar thing in your situation. I wouldn't do "find ." in root though, it might take ages. If slocate found only the files you wanted to delete then you could do
```
slocate *what you were looking for* | xargs -d '\n' rm
```

Might need a sudo there somewhere, but I'd do a dry run, replacing rm with echo, to check what its deleting. Can you not remove this program using apt or anything then? The only time you should only have to do this that I can think of is if you did a "make install". If so then next time have a look at checkinstall. It allows compiled programs to be removed with apt like something from the repos.

---

### Post by duruttye on 2008-01-21
Wow man!

I searched and found many unused files from old removed applications, that I only tried out  and newer used again and removed them, 'cause they used up huge amounts of space.

Why oh why aren't they removed when the application is uninstalled????

Thanx guys allot!!!

---

### Post by hyper_ch on 2008-01-21
well, what files were not removed? Config files? The downloaded .debs ? User generated files?

---

### Post by duruttye on 2008-01-21
I'm not sure what kind of files they were, probably all those.

---

### Post by JeremyStein on 2008-01-21
Try something like this:
find . -name "*vive*" -print0 | xargs -0 echo rm -rf

If you like the results, re-run without the "echo" to do it for real.

---

### Post by duruttye on 2008-01-21
It's done already! I removed many files of removed application.

Thanx anyway!

---

