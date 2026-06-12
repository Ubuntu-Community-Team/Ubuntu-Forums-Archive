---
title: "Formatting Floppy"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-15
Hi,

I'm trying to formatt some old floppies i had from my windoze days. 

Applications/System Tools has Floppy Formatter i see. Under Filesystem settings i have the option of Linux Native (ext 2) or DOS (fAT) I click on Linux although mine is ext3 and i got back:

The filesystem creation utility (/sbin/mke2fs) reported the following errors:

/dev/fd0 is mounted; will not make a filesystem here!
 (54)

on another floppy i got:  Error formatting track #0

Does someone here have experience or know-how as to preconditions for being able to formatt floppies on GNU/LInux-Ubuntu ?

Suggestions gratefully received,

--
sophtpaw

---

### Post by heimo on 2005-08-15
Try unmounting the floppy first (if you have a floppy disk icon on your desktop, right click and select unmount *guess*). Or you could do the same thing on terminal:

to unmount:
 ```
umount /dev/fd0

```

To format using ext3:
 ```
 /sbin/mkfs.ext3 /dev/fd0

``` 

You can substitute ext3 with ext2 or msdos (if that one doesn't work, try installing dosfstools package).

---

### Post by sophtpaw on 2005-08-15
[QUOTE=heimo]Try unmounting the floppy first (if you have a floppy disk icon on your desktop, right click and select unmount *guess*). Or you could do the same thing on terminal:

to unmount:
 ```
umount /dev/fd0

```

To format using ext3:
 ```
 /sbin/mkfs.ext3 /dev/fd0

``` 

You can substitute ext3 with ext2 or msdos (if that one doesn't work, try installing dosfstools package).[/QUOTE]

thank you Heimo,

Now i know what that meant. Wheras i didn't before so it didn't prompt me to check in one of the other workstations to see i had floppy open, which got in the way,

It appears to be working now, regardsless of being set to ext2 (i dont actually know what that means and/or the difference with ext3) The proof is after the formatt i can save data on it!

cheers,

--
sophtpaw

---

### Post by sophtpaw on 2005-08-15
To format using ext3:
 ```
 /sbin/mkfs.ext3 /dev/fd0

``` 


i punched that command into CLI and it did something but i don't know what :-) 
It doesn't fully and thoroughly formatt the disk, does it? partial? 
 

maybe you could tell me more or direct me if you happen to know where i could learn more about ext2/3 and floppy disc

thx,

sophtpaw

---

### Post by heimo on 2005-08-15
ext2 and ext3 are filesystems, so are reiserfs, xfs and jfs - and on Windows side: fat16, fat32, ntfs. I think fat16 is probably quite suitable for most purposes, but for best compatibility with all the file permissions and stuff, ext2 should do it very well. Ext3 is the default filesystem in Ubuntu and it has so called "journaling", which in my opinion is of no use on floppy (just wastes space).

---

### Post by xmastree on 2005-08-15
[QUOTE=sophtpaw]on another floppy i got:  Error formatting track #0[/QUOTE]That sounds like a bad disk. I have loads like that.


Whatever happened to floppy disks? They used to be reliable but these days it seems you just can't trust them. I didn't think anyone still used them, since a blank CD is cheaper, or a thumbdrive is more convenient.

---

### Post by heimo on 2005-08-15
[QUOTE=xmastree]That sounds like a bad disk. I have loads like that.


Whatever happened to floppy disks? They used to be reliable but these days it seems you just can't trust them. I didn't think anyone still used them, since a blank CD is cheaper, or a thumbdrive is more convenient.[/QUOTE]

Hmm... floppy raid-1? Anyone? ;) (If I can find two floppy drives from my closet, I'm gonna do it.)

EDIT: Hmm... How many floppy disk drive controllers do I have...

---

### Post by xmastree on 2005-08-15
[QUOTE=heimo]Hmm... floppy raid-1? Anyone? ;) [/QUOTE]Seen [this?](http://ohlssonvox.8k.com/fdd_raid.htm) 

(are you following me... ?)  :)

---

### Post by heimo on 2005-08-15
*lol* That's funny. :) And yes, I had seen that before, just didn't remember anymore - only remembered some folks making USB memory stick raids. Pretty useless, but geeky. To top that 3.5" floppy disk raid array, I guess I have to go 5,25" or 8".

---

### Post by rudiz on 2005-10-16
In breezy i have the folowing problem:

if i try to format a floppy  (Applications>System Tools>Floppy Formatter) i get this messages after  a while:

problem reading cylinder 0,expected 18432 reading 4096.

Somebody can help me with the solution of this problem?

---

### Post by heimo on 2005-10-16
Not sure, but you could try A) formatting mode: thorough, B) another floppy disk. Have you already tried this?

---

### Post by rudiz on 2005-10-16
still the same negative results.

after a while the process stopped , showing the err message.

---

