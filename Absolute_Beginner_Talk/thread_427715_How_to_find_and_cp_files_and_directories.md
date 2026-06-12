---
title: "How to find and cp files and directories?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by fireant on 2007-04-29
Hi All,

I have a windows disk which is mounted in a usb caddy as /media/disk.

I want to copy all the jpg files off it into my home directory, but I also want to create the directories the jpg files are in as it copies. 

This is because my photo collection is a mess and I have loads of different pictures with the same name. A simple find and copy into the same directory would cause an overwrite.

I've tried:

find . -name *.jpg -exec cp '{}' ~/photos/ ';'

This nearly works, it just doesn't create and copy the directory structure.

Thanks

---

### Post by zetsumei on 2007-04-29
I would just sudo cp *.jpg /home/YOURUSERNAME then just organize them there.  Or you could get more advanced and write a script to copy, rename, and sort the files into different folders.

---

### Post by fireant on 2007-04-29
Thanks for the reply.

If I do that the cp *.jpg only copies from the current directory though? 
I need it to search the whole disk for jpg files and copy them over to my home account, creating the directory it found them in as it does so.

---

### Post by zetsumei on 2007-04-29
To do that you would need to write a script.  I'm new so I wouldn't know how to write the script to search the entire drive and move the images into the correct directories.  Sorry.

---

### Post by bashologist on 2007-04-29
#It's in the manual:
man cp

#Maybe this is what you want?
find . -iname '*.jpg' -exec cp --parents {} ~/photos/ \;

---

### Post by zetsumei on 2007-04-29
I thought you could only do that via a script.

Offtopic: bashologist, what dock is that you're using?

---

### Post by yabbadabbadont on 2007-04-29
**File:** go.sh
```
#!/bin/bash
cd /media/disk
find . -type f -name "*.jpg" -print | while read imagefile
do
pathpart=$(dirname "$imagefile")
mkdir -p ~/photos/"$pathpart"
cp $imagefile ~/photos/"$pathpart"
done

```
Save that using whatever name you like (I used go.sh) and change the permissions so that it is executable.
```
chmod 755 go.sh
```
Then run it using ```
./go.sh
```
Hopefully it will do what you wish.  (I haven't tested it, but it should work)  If you don't have any spaces or special characters in your directories or image filenames, then you can remove the double quotes I used around the imagefile and pathpart variables.

EDIT: Too slow.  That's what I get for writing a script when cp will apparently do the job itself...  :D
@bashologist: You learn something new everyday I guess.  Also, I learned the various command line utilities on an old version of Unix and the cp command there didn't have that option, so I tend to jump straight to scripts.  :lol:

---

### Post by bashologist on 2007-04-29
> **zetsumei said:**
> I thought you could only do that via a script.

Offtopic: bashologist, what dock is that you're using?

It's just the gnome-panel. It was set to 34px and expand was false I believe.
> **yabbadabbadont said:**
> @bashologist: You learn something new everyday I guess.  Also, I learned the various command line utilities on an old version of Unix and the cp command there didn't have that option, so I tend to jump straight to scripts.  :lol:Yep, that's a good option for sure. And the great find makes it a unique command since it copy's only *.jpg. n_n

---

