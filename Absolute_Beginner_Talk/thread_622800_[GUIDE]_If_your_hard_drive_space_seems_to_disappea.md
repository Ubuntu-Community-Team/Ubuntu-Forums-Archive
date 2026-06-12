---
title: "[GUIDE] If your hard drive space seems to disappear"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by baqai on 2007-11-25
For past few days i was puzzled by this problem that i kept deleting files but there was no difference in the hard drive space, so by searching and reading i figured out a way to solve this problem,I thought about writing this small tip/guide for newbies like me

**Problem / Symptom**

I delete files from my hard drive (it can be linux partition or it can be NTFS partiont) yet the space on hard drive remains the same as it was before deleting the files.

**Solution**

What happens when you delete a file in GUI is that Linux moves the files to a Trash folder instead of actually deleting the file,

**For Linux Partition** i would suggest you open the terminal go to

```

cd /home/<username>/.Trash

```

Replace the <username> with your user name e..g

```

cd /home/baqai/.Trash

```

now to see if you have any hidden files in the directory

```

ls -a

```

this will show you all the hidden / non hidden files in the directory

now for deleting the files 

```

rm <filename>

```

If you want to remove a directory than use

```

rm -R <directoryname>

```

**For Windows Partition**

Say you have a windows partition mounted and the volume of that drive is "Downloads" you can follow the same principals as above with slight twist

First lets go to your partition

```

cd /media/Downloads

```

Now lets find those files which you deleted

```

cd .Trash-<username>

```

e.g. in my case i typed

```

cd .Trash-baqai

```

Now you will enter a new directory 

```

ls -a

```

You will be again shown a list of files, now you can follow the steps above to get rid of the files once and for all and can recover your hard drive space.

On windows partitions you will also have another directory by name of **.Trash-root** which you should also check just in case you deleted some files by your root account and they are there, For most of the new users like me it should not be a case normally :)

If i am wrong than please do correct me, i am myself very new here, hope i haven't broke any rules by posting this guide?

---

