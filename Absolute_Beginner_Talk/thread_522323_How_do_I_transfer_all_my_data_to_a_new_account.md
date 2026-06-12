---
title: "How do I transfer all my data to a new account?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-08-10
I have created a new user account and want to transfer all my data from the old account to the new.  So far I haven't been able to simply cut and paste everything to the new account.
So I had to copy everything instead which is bad.  

Since it's filling up unneccessary disk space and it also complains about my new user account not having read access to certain files so I'm forced to skip certain files during this process.
Which makes me really uncertain whether or not everything really got transfered.

What's the simplest way to cut and paste all my data from the old account to the new account :confused:  They both have Administrator rights and I used "gksudo nautilus" still there's problems in the way.

---

### Post by Ek0nomik on 2007-08-10
You are trying to copy files from /home/userone to /home/usertwo?

You could use the terminal and use the 'mv' command, or is that not what you want?

---

### Post by sisco311 on 2007-08-10
```
sudo mv /home/old_user /home/new_user
```
```
sudo chown -R new_user:new_user /home/new_user
```

---

### Post by jingo811 on 2007-08-10
Yeah basically but the catch is that I cannot cut and paste my entire /home directory like that because I want to avoid bringing all those .invisible folders and garbage system files to the new account.
So I need to do it folder by folder file by file.   Thus far there's only problems.

How do I cut and paste folders?
> mikey@renaissance:/home$** ls**
login  lost+found  michael  mike  mikey  pingu  Recycled
mikey@renaissance:/home$** sudo mv /home/mikey/bash /home/pingu/**
mv: cannot move `/home/mikey/bash' to a subdirectory of itself, `/home/pingu/bash'
mikey@renaissance:/home$ 

Cutting and pasting single files seemed to work however.
> mikey@renaissance:/home$ sudo mv /home/mikey/xmvsf_tricks.odt /home/pingu/
mikey@renaissance:/home$ 

---

### Post by trak87 on 2007-08-10
The command line is great. Just use the mv (move) command. I would do it differently than cisco311 mentioned though:


```
sudo mv /home/old_user/* /home/new_user/*
```

and then do the "sudo chown" as he mentions. This will avoid the invisible dot files and directories.



You could also install Krusader and just drag and drop too.

---

### Post by aysiu on 2007-08-10
Why don't you just cut and paste with the graphical user interface (point-and-click)?

Alt-F2 will get you a run dialogue.

In that dialogue, type ```
gksudo nautilus
``` for Ubuntu or ```
kdesu konqueror
``` for Kubuntu or ```
gksudo thunar
``` for Xubuntu

Then move the folders over with your mouse.

---

### Post by MenZa on 2007-08-10
Well, you need to use the -R flag (Recursive) to move files with subfolders. E.g.:

```
sudo mv -R /home/userone/* /home/usertwo/
```

---

### Post by jingo811 on 2007-08-10
> 
```
sudo mv /home/old_user/* /home/new_user/*
```
and then do the "sudo chown" as he mentions. This will avoid the invisible dot files and directories.

How does that avoid the invisible dot files and directories exactly?  I mean aren't I moving everything from old_user/home/ to new_user/home/?

---

### Post by aysiu on 2007-08-10
> **jingo811 said:**
> How does that avoid the invisible dot files and directories exactly?  I mean aren't I moving everything from old_user/home/ to new_user/home/?
Try my directions.

---

### Post by Ek0nomik on 2007-08-10
> **jingo811 said:**
> How does that avoid the invisible dot files and directories exactly?  I mean aren't I moving everything from old_user/home/ to new_user/home/?

Yes, you are correct.

You could write a bash script to not transfer the files that begin with, '.', but I imagine that's more than what you want to do.

You could still use his method and then delete all the hidden files by hand.

This gets me thinking; it would be nice if there was a website dedicated to hosting bash scripts.  It could be useful to a lot of people.

---

### Post by jingo811 on 2007-08-10
> This gets me thinking; it would be nice if there was a website dedicated to hosting bash scripts. It could be useful to a lot of people.
Maybe this guy is the one you're looking for.
[http://bash.zedzone.com/index.php?cname=bash&tzoffset=-120](http://bash.zedzone.com/index.php?cname=bash&tzoffset=-120)


Hmm....**"gksudo nautilus"** finally worked.  It seems like using that when logged into NewUser won't work properly for certinan files.  Only now when I'm logged in as OldUser can I transfer files like I want with Nautilus.  Tnx for your help and attention, seems like situation is under control now.

---

### Post by trak87 on 2007-08-16
To Menza: There is no "-R" recursive option for the mv (move) command. When you move a directory, everything in that directory moves with it, including its child directories. So mv works recursively by default when moving directories. If moving files, then it only moves files.

My original solution:
> sudo mv /home/old_user/* /home/new_user/*
Followed by 'sudo chown...'

> **jingo811 said:**
> How does that avoid the invisible dot files and directories exactly?  I mean aren't I moving everything from old_user/home/ to new_user/home/?


If you did 

```
sudo mv /home/old_user/* /home/new_user/*
```

This would work. You would only move every visible file from your old directory to the new directory. Invisible files wouldn't move. On the other hand, if you did

```
sudo mv /home/old_user/ /home/new_user/
```

This would move everything, including the directory and the invisible files into the new directory, and you'd end up with this:

```
/home/new_user/old_user/
```

but then you'd have to move everything *again* (minus the dot files) from old_user up one level to the new_user directory. So my original suggestion was correct. However, it might be easier to to use aysiu's suggestion and just use nautilus, a gui solution.

---

### Post by MenZa on 2007-08-18
> **trak87 said:**
> To Menza: There is no "-R" recursive option for the mv (move) command. When you move a directory, everything in that directory moves with it, including its child directories. So mv works recursively by default when moving directories. If moving files, then it only moves files.

That's quite true; I mistook it for cp at the time. Thanks for correcting me! :)

However, another way of doing it could be to move the output of ls:

```
sudo mv ls `/home/old_user`/home/newuser
```

---

