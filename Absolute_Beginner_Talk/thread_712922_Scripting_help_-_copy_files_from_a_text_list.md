---
title: "Scripting help - copy files from a text list"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by dogugotw on 2008-03-02
I have a text file that contains a list of path/filenames.  I'd like to move each entry in the list from its current location to a new 'hold' directory.

I've found some simple examples elsehere on the web but they don't seem to do what I want.

For the sake of clarity; my source file list is called 'CleanFile.txt'.  The destination directory is /home/Me/hold

I've tried:

for i in CleanList.txt; do cp $i /home/Me/hold;done

I've put single and double quotes around CleanList.txt and /home/Me/hold.

All that copies is the file CleanList.txt...

I've also tried:
while read CleanList.txt;do cp "sourcefile" "/home/doug/hold";done

It goes into an endless loop and, again, just CleanList.txt copies over.

I know I'm doing smething stupid but I'm not a scripter and don't know what to try next.

Any tips are appreciated.

Doug

---

### Post by Jad on 2008-03-02
cat CleanList.txt | while read file ; do cp $file /home/user/distination; done;

if you are going to copy directories use -R after cp.

---

### Post by es@urito on 2008-03-02
Try this:
```

for i in $(cat CleanList.txt); do cp $i /home/Me/hold; done

```
Tell me if it works...

---

### Post by dogugotw on 2008-03-02
es@urito - I am running your command and it seems to be working great.  I can see the files being added to my hold directory.

Jad - thanks for the command; it works like a charm also!

Thank you both for the assist.

Doug

---

