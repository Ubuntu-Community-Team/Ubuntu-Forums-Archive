---
title: "Cannot locate my .Trash directory"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by BLaFrance on 2008-03-08
I have a folder in my trash bin that I cannot for the life of me delete.  The only method I could find to solve the problem requires navigating to some .Trash directory through the terminal and deleting it with sudo.  However there is not such folder.  I looked in both my root and user directories using ctrl-h to view hidden folders.  Nothing comes up under searches either.

I am using Ubuntu-Studio 8.04 if that helps.

---

### Post by Rocket2DMn on 2008-03-08
If the file you're deleting is on another disk/partition, you have to go to the mount point of that disk/partition and find the .Trash-[yourusername] folder.

---

### Post by MONODA on 2008-03-08
it is called the .trash directory, linux is case sensitive.

---

### Post by Rocket2DMn on 2008-03-08
> **MONODA said:**
> it is called the .trash directory, linux is case sensitive.

Linux is case sensitive indeed, but it is with a capital T.  I have never seen a lower cased trash.

In your home directory you have .Trash but on any other partition you have .Trash-[yourusername]
root also has a trash in /root/.Trash

---

### Post by BLaFrance on 2008-03-08
> **Rocket2DMn said:**
> Linux is case sensitive indeed, but it is with a capital T.  I have never seen a lower cased trash.

In your home directory you have .Trash but on any other partition you have .Trash-[yourusername]
root also has a trash in /root/.Trash

Thanks for the quick replies, but I have no .Trash folder in either my home or root directories.  Neither hidden nor otherwise.

---

### Post by ghostdog74 on 2008-03-08
the next time you don't know where your files are, do a search..using find 
```

find / -iname "*trash* -print

```

---

### Post by MONODA on 2008-03-08
did you try viewing hidden files? ctrl+h

---

### Post by Rocket2DMn on 2008-03-08
> **MONODA said:**
> did you try viewing hidden files? ctrl+h

Hehe, hate to pick on you tonight MONODA, but the OP said in his post that he did try that.  Please read more carefully in the future, we DO appreciate your help :)

---

### Post by handy on 2008-03-08
This may or may not be useful to you, but this code will empty the trash that you can't get rid of:

***sudo rm -fr $HOME/.Trash/***

---

### Post by Rocket2DMn on 2008-03-08
> **handy said:**
> This may or may not be useful to you, but this code will empty the trash that you can't get rid of:

***sudo rm -fr $HOME/.Trash/***

Thanks handy, that is a useful quickie for emptying the trash bin, I've used it myself.  I just want to remind anybody who reads this to be VERY CAREFUL when using the rm command, esp with the -r option since it is so powerful.  What is rm'ed cannot be undone, so type out your commands with extreme caution.  ( For more info on dangerous commands, see here: [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73) )

---

### Post by handy on 2008-03-08
> **Rocket2DMn said:**
> Thanks handy, that is a useful quickie for emptying the trash bin, I've used it myself.  I just want to remind anybody who reads this to be VERY CAREFUL when using the rm command, esp with the -r option since it is so powerful.  What is rm'ed cannot be undone, so type out your commands with extreme caution.  ( For more info on dangerous commands, see here: [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73) )

Thanks for bringing that to our attention Rocket2DMn.

I didn't even think about the data terrorists!

---

### Post by Rocket2DMn on 2008-03-08
> **BLaFrance said:**
> Thanks for the quick replies, but I have no .Trash folder in either my home or root directories.  Neither hidden nor otherwise.

Ah, sorry I missed that post.
your trash directory should be in 
/home/[yourusername]/.Trash
and on any other partition that you've deleted stuff from
/media/[mountpoint]/.Trash-[yourusername]

You can check from the terminal using the ls command
```
cd ~
ls -al | grep .Trash
```

---

### Post by ahaslam on 2008-03-08
Maybe the OP is using Xubuntu? In that case their trash will stored within ~/.local/share/Trash. The deleted files are under 'files' & the restore info is under 'info'. If you want rid of all trashed items it's quite safe to issue issue the following:
```
sudo rm -r ~/.local/share/Trash/*
```
;)

---

### Post by handy on 2008-03-08
> **ahaslam said:**
> Maybe the OP is using Xubuntu? In that case their trash will stored within ~/.local/share/Trash. The deleted files are under 'files' & the restore info is under 'info'. If you want rid of all trashed items it's quite safe to issue issue the following:
```
sudo rm -r ~/.local/share/Trash/*
```
;)

He's using Ubuntu Studio, which may explain why things aren't where we expect them to be?

---

### Post by BLaFrance on 2008-03-08
> **BLaFrance said:**
> I have a folder in my trash bin that I cannot for the life of me delete.  The only method I could find to solve the problem requires navigating to some .Trash directory through the terminal and deleting it with sudo.  However there is not such folder. ** I looked in both my root and user directories** using **ctrl-h to view hidden folders**.  **Nothing comes up under searches either**.

I am using **Ubuntu-Studio 8.04** if that helps.

I really do appreciate the help, but it doesn't seem like anyone actually read anything beyond the thread's title.](*,)

---

### Post by ahaslam on 2008-03-08
^Shows how observant I am ;)
As for US, I have no idea...

Another way to locate the folder is with:
```
locate Trash
```
;)

---

### Post by BLaFrance on 2008-03-08
> **ahaslam said:**
> ^Shows how observant I am ;)
As for US, I have no idea...

Another way to locate the folder is with:
```
locate Trash
```
;)

Thats the one! It was /home/username/.loca/share/Trash  Why would none of the other commands locate the folder? :confused:

---

### Post by ahaslam on 2008-03-08
> **BLaFrance said:**
> Thats the one! It was /home/username/.loca/share/Trash  Why would none of the other commands locate the folder? :confused:
Thought it'd be there if not in your home dir, I guess US have implemented the restore feature?
The other commands didn't work because they were either wrong, or didn't search deep enough.
They work better as:
```
find -iname "*Trash*" -print
```
```
ls -aR | grep .Trash
```
So now you know 3 ways of doing the same thing, each has it's perks. ;)

---

