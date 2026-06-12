---
title: "command question"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-10-08
if i want to move the contents of a folder to another folder, but not move the folder itself, what is the command for that? also, what will occur if there are some duplicates  in the new folder?

---

### Post by LaRoza on 2007-10-08
> **fuscia said:**
> if i want to move the contents of a folder to another folder, but not move the folder itself, what is the command for that? also, what will occur if there are some duplicates  in the new folder?

man cp, for the options, you can have a switch to prompt before overwrite (-i). I think if you navigate to the directory, and use "cp -i * <destination>", it will copy all the contents to another directory.

-EDIT, It does, but doesn't copy directories. use the -R for that.

```

cp -i -R * <destination>

```

---

### Post by fuscia on 2007-10-08
'man cp'! never thought of that. thanks for the response.

---

### Post by bashologist on 2007-10-08
If you meant "move" then, here are some examples to show you how mv works. First mv overwrites the file in destination by default.
```
foo@bar:~$ mkdir ~/source ~/destination
foo@bar:~$ touch ~/source/file1 ~/source/file2 ~/destination/file1
foo@bar:~$ ls ~/destination
file1
foo@bar:~$ mv ~/source/* ~/destination/
foo@bar:~$ ls ~/destination
file1  file2
foo@bar:~$
```

Using the "-i" option will prompt before overwrite.
```
foo@bar:~$ mkdir ~/source ~/destination
foo@bar:~$ touch ~/source/file1 ~/source/file2 ~/destination/file1
foo@bar:~$ ls ~/destination
file1
foo@bar:~$ mv -i ~/source/* ~/destination/
mv: overwrite `/home/foo/destination/file1'? n
foo@bar:~$ ls ~/destination
file1  file2
foo@bar:~$
```

The "destination" folder doesn't contain the folder "source'. I think that's what you wanted, idk. In any case, good luck.

---

### Post by fuscia on 2007-10-08
neither man cp nor man mv seem to indicate how to 'select all' within a directory.

---

### Post by Celegorm on 2007-10-08
> **fuscia said:**
> neither man cp nor man mv seem to indicate how to 'select all' within a directory.

That would be done via wildcards, such as '*'. For more information about wildcards see [this tutorial.]("http://linux.org.mt/node/49#N102D8")

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-08
yes using wild cards is the way to go 

```
cp -R  - i   /were ever your dir is/* /were ever you destinations/    
```

the * symbol is  a wild card it means anything or all 
if you only wanted to copy files ending with .avi then use *.avi  

so if you had 2 files bob.avi and jane.avi  using *.avi would copy both
using b*.avi would only get bob

the -R is so that is recursivly copy directories, with out this it would ignore them 

the -i is so it is interactive so if a file all ready exist in side the destination it will promt you 
(with out this i bleve it just over right them, how ever not to sure )

---

### Post by bashologist on 2007-10-08
Select all? Maybe use the great find command.
```
foo@bar:~$ mkdir ~/source ~/destination
foo@bar:~$ touch ~/source/file1 ~/source/file2 ~/destination/file1
foo@bar:~$ ls -l ~/destination
total 0
-rw-r--r-- 1 foo users 0 2007-10-08 12:22 file1
foo@bar:~$ find ~/source/ -maxdepth 1 -mindepth 1 -exec mv -t ~/destination/ {} +
foo@bar:~$ ls -l ~/destination
total 0
-rw-r--r-- 1 foo users 0 2007-10-08 12:22 file1
-rw-r--r-- 1 foo users 0 2007-10-08 12:22 file2
foo@bar:~$
```

---

### Post by fuscia on 2007-10-08
i was looking more to do this with mv. so, it ended up being *mv dir1/* dir2*.

phew! thanks for the help. that was driving me nuts.

---

