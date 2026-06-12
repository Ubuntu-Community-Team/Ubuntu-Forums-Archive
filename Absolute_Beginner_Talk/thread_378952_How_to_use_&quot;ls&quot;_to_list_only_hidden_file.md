---
title: "How to use &quot;ls&quot; to list only hidden files?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-03-07
What's the trick for making the *ls* command list only the "hidden" files (those whose name begins with a "." period character) in a directory?

That is to say, I want a simple list of filenames that excludes any files that do not begin with a period (".") character.

I've tried **ls .*** and **ls ./.***, but these both produce the following sort of vertically spaced, recursive output (excerpted to save space):

> .AbiSuite:
AbiWord.Profile  coquille.conf

.adobe:
Acrobat  Linguistics

.aptitude:
config

.beagle:
config  Indexes  Log  socket  socket-helper  TextCache  ToIndex


Surely there's some way to get *ls* to list **_only _** the files whose names begin with a period ("."), as in this excerpt:

> 
drwxr-xr-x  2 rbv  rbv     4096 2007-01-21 17:30 .themes
drwx------  5 rbv  rbv     4096 2007-01-23 17:30 .thumbnails
drwx------  3 rbv  rbv     4096 2007-01-21 23:19 .thunderbird
drwx------  2 rbv  rbv     4096 2007-02-15 15:50 .Trash
drwx------  2 rbv  rbv     4096 2007-03-02 13:59 .tsclient
drwx------  2 rbv  rbv     4096 2007-01-22 08:45 .update-notifier


(Note that I copied the preceding excerpt from a list that contained unwanted non-hidden files...)

Cheers & thanks,
Ric
SFO

---

### Post by girishv on 2007-03-07
Hi,

the following command will achieve what you are looking for. If you want to use this often, then it might be a good idea to make an alias for this. All I am doing is rejecting
all the file/directory names that do not start with a '.' at the beginning. 

ls -a | grep '^\.'

cheers

Girish

---

### Post by ~chinook~ on 2007-03-07
Grep is god. Good command to know.

---

### Post by Phrawm48 on 2007-03-08
Thanks all.  Yes, *grep* definitely works.

I'm slightly amused that *ls* can't quite do it natively, but using an alias for the *ls -grep* duad works great...

Cheers & thanks 'gain,
Ric
SFO

---

### Post by mscir on 2008-03-05
Very nice, thanks!

---

