---
title: "Viewing Hard Drives by Device not Mount Point"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-02-10
Hi.
I have 2 hard drives.  One holds my install and one is mounted at /media/linuxstore .  The hard drive that holds my install is a 20 GB.  It says I have 12 GB left.  Last I checked I had around 15, so I figure I've copied something huge over and forgotten about it.  Is there a way to view my drives by the drive and not by the mount point?  Similar to browsing c:/ on windows shows my C drive and d:/ shows my D drive.  My filesystem also has a network NFS drive mounted.

I need to find the space hog.  Any advice.

---

### Post by kidders on 2007-02-11
Hi there,

I'm not sure I follow your question about "drives". The way to browse the contents of a particular disk is to navigate to its mount point.

If you're looking for space hogs, the "du" command might be helpful. You can use it to add up and compare the amount of space being used by different stuff.

**Edit:** Alternatively, "find" has a -size switch that you could use to simply ask for a list of files larger than, say, 100MB.

---

### Post by l951b951 on 2007-02-11
By drives, I mean hda and hdb.  I have two IDE hard drives installed.  

I think during the backing up and moving around of some things, I've put a large folder (lots of files) onto hda (the hard drive that holds my installation).  I want all my backup/duplicate files on hdb.  I am looking for a quick way to identify these ridiculous folders (1gb+) without having to navigate to each folder to see its contents/disk-usage.

---

### Post by kidders on 2007-02-11
Linux provides loads of ways of finding things. Which one would be fastest/easiest for you sort of depends on how you feel you could identify what you're looking for. For instance, if you want to see a list of large directories, you can use "du". Something like **du -h|grep "^[0-9]\{3,\}M"** would do the trick, by returning a list of directories with sizes in the hundreds of megabytes.

On the other hand, if you know the name of one of the files you want to move, you could identify its location with something like **find -name "whatever"**, to get back its path. If the files you want have been in situ long enough to be indexed, **slocate "whatever"** would be far faster.

How about one of these?

---

### Post by l951b951 on 2007-02-11
> **kidders said:**
> Linux provides loads of ways of finding things. Which one would be fastest/easiest for you sort of depends on how you feel you could identify what you're looking for. For instance, if you want to see a list of large directories, you can use "du". Something like **du -h|grep "^[0-9]\{3,\}M"** would do the trick, by returning a list of directories with sizes in the hundreds of megabytes.

On the other hand, if you know the name of one of the files you want to move, you could identify its location with something like **find -name "whatever"**, to get back its path. If the files you want have been in situ long enough to be indexed, **slocate "whatever"** would be far faster.

How about one of these?

Thanks.  Last follow up question.  can you explain the command line argumens you used here: >  du -h|grep "^[0-9]\{3,\}M".

---

### Post by kidders on 2007-02-11
Oops sorry... that *was* a bit opaque, wasn't it! (Keep the questions coming though ... the next thing we write here might be exactly what someone else needs.)

[LIST]
[*]The basic command **du** has a parameter **-h** which switches its output to "human readable" mode. (See **man du** for more detail.)
[*]The horizontal line is a "pipe" which feeds the output of **du** into **grep**.
[*]Grep is one of a huge range of utilities for manipulating text.
[*]"^[0-9]\{3,\}M" is a regular expression, which is a way of describing patterns in text. (See **man grep** for more detail.)
[/LIST]

Oh heck! That regular expression is not terribly straightforward ... sorry! After a while, you get so used to using them, that you don't give it a second thought any more.

[LIST]
[*]^ anchors the pattern at the start of a line.
[*][0-9] is a range of acceptable characters.
[*]{3,} is a repetition (3x) with no upper limit. The backslashes are used to "escape" the curly braces, because they have a special meaning that I don't want to use.
[*]M is the character "M".
[/LIST]

Basically, the **du** command produces an awful lot of output, so I wanted to show you how to filter it for stuff you're more likely to be interested in. The regular expression ensures that you only see lines that start with 3 or more digits, followed by an M (for megabyte) ... these equate to directories that have at least 100MB of stuff in them. You might like to use a 'G' (for gigabyte) instead.

I hope I didn't over-explain that!!

---

### Post by l951b951 on 2007-02-11
Using the command kidders showed me > du -h|grep "^[0-9]\{3,\}M" searches my entire file system.  which helps me find the huge folders.  One note is to make sure you browse to "/" because otherwise it only searches the current directory and subdirectory.  

However, it still brings me back to my initial quandry, how can I only search for large folders and only limit the results to items found on hda1?  The du command works, but I have to remember which drive is mounted at which folder/mountpoint.

I could unmount my extra drives and then use du, but I'd rather not unmount my drives.

---

### Post by kidders on 2007-02-11
> **l951b951 said:**
> how can I only search for large folders and only limit the results to items found on hda1?Navigate to its mount point and run the command there. If that doesn't suit (often, filesystems can be mounted one inside the other), you can use du's **-x** option to stop it traversing filesystems. (See **man du**.)

> **l951b951 said:**
> I have to remember which drive is mounted at which folder/mountpoint.Yes. Operating systems normally expect you to know what's mounted where ... but if you forget, you can always check what's what, by typing **mount**.

---

