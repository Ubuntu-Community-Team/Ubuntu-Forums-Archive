---
title: "zip multiple directories"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by actioncomics on 2007-05-06
not sure if i am missing something.  i have read the man for zip and came up with nothing.  I am trying to zip up multiple directories.  but i want the zip file to be named after each directory.  so if i have 5 directories i would end up with 5 zip files.  I can't find anything on this to make this more automated.  I will be zipping hundreds of directories and don't want to manually do each one.  any help?

thanks
ac

---

### Post by Skrynesaver on 2007-05-06
If all the directories are sub directories of your current directory you could use the following script.
```

for i in $(find ./ -type d -maxdepth 1);do
   tar -czvf $i.tgz $i
done

```
This will create a series of zipfiles in the current directory which are named <directory_name.tgz>

---

### Post by actioncomics on 2007-05-06
unfortunatly i need them to be zip files they will be used by another program that requires them to be this format.  any other ideas?

---

### Post by actioncomics on 2007-05-06
or is gzip the same as zip?

---

### Post by actioncomics on 2007-05-07
i figured out that gzip is not the same as zip.  any other ideas from anyone?

ac

---

### Post by Cypher on 2007-05-07
No, GZip and Zip are not the same..use this:
```

for i in $(find ./ -type d -maxdepth 1);do
   zip -r9 $i.zip $i
done

```

---

### Post by actioncomics on 2007-05-07
could this be turned into a nautilis script?  so that when you execute a script on a folder that it looks for all subdirectories of that folder and zips them.  Just curious.  I will have to try the above example when i get home. thanks for the help Skrynesaver and Cypher looks like that should do it just fine.

ac

---

### Post by actioncomics on 2007-05-07
i think i am having trouble because my directories have spaces in them.  it is still creating a zip will with everything in it and the file it creates does not have a name just ".zip" (without the quotes).  any suggestions on how to make directory names with spaces work?

thanks
ac

---

### Post by bashologist on 2007-05-07
> **actioncomics said:**
> i think i am having trouble because my directories have spaces in them.  it is still creating a zip will with everything in it and the file it creates does not have a name just ".zip" (without the quotes).  any suggestions on how to make directory names with spaces work?

Unfortunately a lot of the time people forget to quote variables or they use deprecated syntax.

Here are some of the archiving command I use.
```
## zip all files and folders in current directory
zip -r "${PWD##*/}.zip" *

## zip the contents of each folder from the current directory into an archive
for x in *; do if [ -d "$x" ]; then cd "$x"; zip -r "../$x.zip" *; cd ..; fi; done

## zip each folder into an archive
for x in *; do if [ -d "$x" ]; then zip -r "$x.zip" "$x"; fi; done
```You probably want the bottom one.

---

### Post by actioncomics on 2007-05-07
that did it.  thanks for the help everyone.

ac

---

### Post by actioncomics on 2007-05-07
this is for anybody else new to linux reading this thread.
using the above example, tie it to an alias.  then when you get to the directory you need it just takes one command.

> alias zipdir='for x in *; do if [ -d "$x" ]; then zip -r "$x.zip" "$x"; fi; done'


after that all you have to do is type "zipdir" and it will zip the entire directory making the appropriate filenames for each subdirectory.
just thought i would share the tip and any linux geniuses out the please correct the above if i am wrong.

ac

---

### Post by Skrynesaver on 2007-05-08
The default Input Field Seperator is "\w" (whitespace) if you add the following at the head of your script it should work
```

IFS="
"

```

---

