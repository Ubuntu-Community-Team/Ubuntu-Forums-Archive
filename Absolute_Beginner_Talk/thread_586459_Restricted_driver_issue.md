---
title: "Restricted driver issue"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Metal Mick on 2007-10-22
Hi everyone,

I've got a fresh install of 7.10 on my machine:

running in a partition on a slave HD on an AMD Athlon XP 2500+ chip, with 1GB of RAM and an ATI X1950Pro card.

When I tried to install the restricted driver for the ATI card off the DVD I got an error message along the lines of:

"An error occurred. The following details...W: failed to fetch cdrom[Ubuntu...Hash sum mismatch"

My reading indicates there's a chance this could be due to a faulty install disk. Does this seem so from the error message? I've searched this forum, and haven't found much that's similar, except for one posting in the install forum, but that solution hasn't worked for me.

How can I get my "restricted driver" installer to work?

Cheers,

Michael P

---

### Post by bobpur on 2007-10-22
There is, probably, code to fix that I'm not familiar with so...
It appears you have a checksum error meaning your download was faulty
I'd assume that the download was corrupt and find another download source; download again and burn another cd. Burn it at as slow a speed as possible. About 4X or so. 
If you try to burn from the download you have, you could get the same problem again. That's why you re-download from another source.


                                                                      Good Luck.

---

### Post by GrammatonCleric on 2007-10-22
Looks like you need to comment out the CDROM in your apt source list.  From a terminal try the following.

```


 sudo  gedit /etc/apt/sources.list


```
Now,  put a # in front of the line for cdrom.  Save and close. Then run..

```


sudo apt-get update


```Now try installing the restricted drivers.

---

### Post by Metal Mick on 2007-10-22
Hi,

thanks for the help and suggestions.

I tried opening the sources.lst file. It is empty.

Perhaps I have a faulty iso after all?

Regards,

Michael P
(It's night in Oz, so I shall not see any replies till the morrow.)

---

### Post by realvz on 2007-10-22
its sources.list not sources.lst

---

### Post by Metal Mick on 2007-10-22
Hi all,

...apart from my inability to read (smile)... I checked the iso files from where I downloaded them, and found that for some bizarre reason, the dvd iso was incomplete on the download server I used.

I recall thinking it was rather small at 1.7GB, but it downloaded anyway. Checking the download page again, the file is now listed in the vicinity of 4.5GB, so I'll try getting the whole file down and right first.

Sorry to have done this to you.

Cheers,

Michael P

---

