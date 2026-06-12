---
title: "How to copy hidden files from one directory to another?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-27
Under /test/ directory, I have .file1, .file2. How do I copy all the hidden files in test/ directory to another directory /targetdirectory ?

I tried 

mkdir /targetdirectory
cp -r /test/* /targetdirectory

but it replied with

cp: cannot stat './test/*': No such file or directory

Thanks !

---

### Post by Remmelas on 2005-11-27
do ```
cp -r /test/.* /targetdirectory
```to match hidden files in the director

---

### Post by Akhran on 2005-11-27
It returns me the following message:

cp: will not create hard link '/targetdirectory/test' to directory '/targetdirectory/.'
cp: cannot copy a directory, '/test/..', into itself, '/targetdirectory'




[QUOTE=Remmelas]do ```
cp -r /test/.* /targetdirectory
```to match hidden files in the director[/QUOTE]

---

### Post by ssam on 2005-11-27
are you sure test and targetdirectory are at the / (root) of your file system? if it is then you must be doing this with sudo, and if you are learning then this is not a safe way to do it.

the message "cp: cannot stat" probably means you are refering to a directory that does not exists.

start again in your home directory.

```

cd /home/$USERNAME
mkdir test
mkdir target

```
type
```
ls
```
to check that this worked.

make some hidden files using touch
```

touch test/.file1 test/.file2 test/file3
ls -al test/

```

now there are some subtleties to refering to directories.
```
cp -r test target
```
or
```
cp -r test target/
```
moves the whole test folder (and all its contents) into target

```
cp test/* target/
```
bash will expand the * to all files that match and perform the action on each one, ie move them to target

to get the hidden files use
```
cp test/.* target/
```

---

### Post by Akhran on 2005-11-27
debian:/home# mkdir test
debian:/home# mkdir target
debian:/home# cd test
debian:/home/test# touch .file1 .file2
debian:/home/test# cd ..
debian:/home# cp -r test/.* target/ 
cp: will not create hard link `target/test' to directory `target/.'
cp: cannot copy a directory, `test/..', into itself, `target/'
cp: cannot copy a directory, `test/..', into itself, `target/'
cp: cannot copy a directory, `test/..', into itself, `target/'
cp: cannot copy a directory, `test/..', into itself, `target/'

Still getting the same error :(

Thanks for following up :)

[QUOTE=ssam]are you sure test and targetdirectory are at the / (root) of your file system? if it is then you must be doing this with sudo, and if you are learning then this is not a safe way to do it.

the message "cp: cannot stat" probably means you are refering to a directory that does not exists.

start again in your home directory.

```

cd /home/$USERNAME
mkdir test
mkdir target

```
type
```
ls
```
to check that this worked.

make some hidden files using touch
```

touch test/.file1 test/.file2 test/file3
ls -al test/

```

now there are some subtleties to refering to directories.
```
cp -r test target
```
or
```
cp -r test target/
```
moves the whole test folder (and all its contents) into target

```
cp test/* target/
```
bash will expand the * to all files that match and perform the action on each one, ie move them to target

to get the hidden files use
```
cp test/.* target/
```[/QUOTE]

---

