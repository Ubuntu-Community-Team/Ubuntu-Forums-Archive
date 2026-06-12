---
title: "HOWTO: Change extensions - multiple files / multiple subdirectories"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by OmahaVike on 2007-03-21
[SIZE="3"]How To Change or Rename Multiple Files Within Multiple Directories[/SIZE]

Okay, so I've been on a quest to find a way to change a whole directory tree, with multiple subdirectories, with hundreds of .txt files to .html.  Essentially, in Linux, I want to rename all or multiple extensions.

Most guides are a regurgitation of the rename man page, or a full blown shell script, which doesn't help a lot for a novice.  I'm hoping to document the command structure here, and hopefully others can pitch in and add what knowledge they have.  Please add in any tags you feel would be useful for a search engine to pick up.  I came close to breaking physical objects in my quest for a real and concise answer.

So, I have a couple dozen directories of which I have .txt files throughout.  I wish to change all .txt files to .html.  It isn't beautiful, but it can be done like this:

Change directories to the highest level you wish to modify the extension with, and type this in....

find . -name "*.txt" -exec rename 's/\.txt$/\.html/' *.txt {} \;

Explanation:

"find ." - This means, start searching from the current directory I'm in, and everything below it.

"-name" - This means that we're looking at the name of the file.

""*.txt"" - DO NOT forget the quotes around this.  It's a common mistake which will make novices pull their hair out.  Essentially, we're looking for anything that ends with a .txt extension.

"-exec" - Okay, just like in grammar school, take the first part of the sentence and shove it into the last half.  This is telling the OS to take the results of the first part, and execute the statement afterward with the results.

"rename" - self explanitory, eh?

"'s/\.txt$/\.html/'" - you may feel free in thinking about this as, "substitute the .txt with a .html".  The forward slashes (/) are what separates the "substitute this" with  "that". 

 *.txt {} \; - not quite sure what any of this does, but it works!  Not quite sure it really matters, but I believe that the {} are a placeholder for the parameter coming from the very first part of the statement (the FIND command).

Hope this helps, somewhat.  I'd strongly emphasize trying it out on a test directory before you implement in a production environment.  Or, at least create a test directory with dummy files to test against.

Best of luck to you all, and I would appreciate any additional comments/guidance for those new to Linux.

---

### Post by Mr. C. on 2007-03-21
Make it faster, be not calling rename for each file, and only rename plain files:

```
find . -name "*.txt" -type f | xargs rename 's/\.txt$/\.html/' 
```

Change your double dashes into single dashes (-name, not --name).

MrC

---

### Post by devnulljp on 2007-03-21
You don't need that backslash in the replace part...everything in there is plain text
Nor do you need the *.txt glob after the rename expression (find has already taken care of it and that's what the {} is for.
Also, add a g for global replace after the replace 's/xxx/yyy/g'
 ```

find . -name "*.txt" -exec rename 's/\.txt$/.html/g' {} \;
```

But xargs is better than exec

```
find . -name '*.txt' | xargs rename 's/\.txt$/.html/g'
```

You can also restrict find to only files or only links etc
for files
find -type f ......
for soft links
find -type l .....
etc.

---

### Post by Mr. C. on 2007-03-21
Good catch on the \ of the replacement part of the RE.

But 'g' makes no sense.  There can be only one end of line.

MrC

---

### Post by OmahaVike on 2007-03-21
thank you to all for helping in the dynamics of this task.  hopefully it'll help someone else out as well.  for me, my task is done, so i'm cool.

next mountain to climb for me (and totally off-topic):  changing multiple lines inside of multiple files within multiple subdirectories...  if anyone can help put together a how-to for that, it'd be greatly appreciated.

---

### Post by Mr. C. on 2007-03-22
New mountain... new thread.

MrC

---

### Post by devnulljp on 2007-03-22
> **Mr. C. said:**
> Good catch on the \ of the replacement part of the RE.

But 'g' makes no sense.  There can be only one end of line.

MrC

You're right. That'll teach me to post at 4am. Well spotted.

---

