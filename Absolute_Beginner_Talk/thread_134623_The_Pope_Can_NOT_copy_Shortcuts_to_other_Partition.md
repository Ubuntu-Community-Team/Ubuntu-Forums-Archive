---
title: "The Pope Can NOT copy Shortcuts to other Partitions"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-22
Dear Beloved Sons of God....

This is the Pope.

I am writting to you because I can not copy a Shortcut from one Partition to Another.

How can I do this with Ubuntu?

May God (& Ubuntu) be with ME & we will solve this problem in no time...


Love you My Sons,

The Pope.

---

### Post by pope on 2006-02-22
_Note by the Pope_:

For some Reason this message got written under a different user name....

---

### Post by Brunellus on 2006-02-22
[QUOTE=dvarsam]Dear Beloved Sons of God....

This is the Pope.

I am writting to you because I can not copy a Shortcut from one Partition to Another.

How can I do this with Ubuntu?

May God (& Ubuntu) be with ME & we will solve this problem in no time...


Love you My Sons,

The Pope.[/QUOTE]
what is a "shortcut" in this context?  Do you mean a Bookmark, a symbolic link, or an application launcher?  Windows uses "shortcut" interchangably to mean all those things, and they are quite different.

---

### Post by pope on 2006-02-22
[QUOTE=Brunellus]what is a "shortcut" in this context?  Do you mean a Bookmark, a symbolic link, or an application launcher?  Windows uses "shortcut" interchangably to mean all those things, and they are quite different.[/QUOTE]

I mean my Son, that if you right-click on an icon (say e.g. a "Writer's" icon or ".deb" file's icon) on the Desktop & select "make link", then the created link (or in the windows environment called "shortcut"), can NOT be copied in another Partition...
(as opposed to Windows, where you can copy "shortcuts" from Partitions to Partitions with NO problem - even if the file they are pointing at has been deleted).

So the Question is:
How can I copy&paste a "link" to another partition?


God bless you,

The Pope.

---

### Post by Cirrocco on 2006-02-22
the pope sounds like a 'smurfy' guy...

---

### Post by az on 2006-02-22
[QUOTE=pope]How can I copy&paste a "link" to another partition?


God bless you,

The Pope.[/QUOTE]


Infallable, huh?

I suppose this is a bug.  Have you checked to see if it has already been filed?

In nomine padre, filii, spiritus-ubuntu, amen.

[indent]|[/indent]
-F----j----S- 
[indent]|[/indent]
[indent]|[/indent]  
[indent] HG[/indent]


(I'm an atheist, can you tell?)
Edit:  I finally got the cross to look right...

---

### Post by Brunellus on 2006-02-22
I don't think the pope can even really speak ex cathedra on things like symlinks, anyway.

tibi oportet Lingua latina melius scribere, azz.

---

### Post by pope on 2006-02-22
Dear Beloved Children of God...

I do NOT know if my computer or Ubuntu 5.10 has a Bug...

And I do NOT know how to check on that....

I would appreciate if a nice "Believer" would do that for me...

In my "church's" language, I would suppose that my PC is "possesed" with negative forces !!!

Maybe I should perform an "Exorcism" on my Machine...

At the same time, my Ubuntu case remains unresolved...


Gob bless Ubuntu & the whole community !!!


Your beloved,


The Pope.


P.S. > I am looking for the Users: "god", "jesus", "devil" , "masonic telmple", to 
          form a group called "paradise" or the "trinity community"...:KS 
          Does anybody know where to find them?

---

### Post by az on 2006-02-22
[QUOTE=pope]Dear Beloved Children of God...

I do NOT know if my computer or Ubuntu 5.10 has a Bug...

And I do NOT know how to check on that....
[/QUOTE]
Hey Benny!  Look here:
[https://launchpad.net/malone](https://launchpad.net/malone)

And it is a bug, I guess.  You should be able to create a soft link to a file on another filesystem.

---

### Post by Kimm on 2006-02-22
> 
P.S. > I am looking for the Users: "god", "jesus", **"devil"** , "masonic telmple", to
form a group called "paradise" or the "trinity community"...
Does anybody know where to find them?


Note: Searching for the devil to form a group called Paradise?! ;) 

Dear Pope,
What partion are you trying to copy your link to? If it happens to be a windows partion the link will defenently not work, since Linux handles folders differently and since windows cant read the default Ubuntu Filesystem (EXT3) or any other Linux filesystems for that mather.

---

### Post by cotcot on 2006-02-22
Looks more like a thread for a forum of [www.vatican.org](www.vatican.org)

---

### Post by NoWhereMan on 2006-02-22
[QUOTE=dvarsam]May God (& Ubuntu) be with ME[/QUOTE]
don't know about God, but I hope that an Ubuntu won't never stay with an **ME** ;)

---

### Post by pope on 2006-02-22
Dear beloved son of God "Kimm":

YES, you are correct !

I was trying to backup my files from an EXT3 to a FAT32 Partition.

I perform this operation only when I feel I have to Format my EXT3 for some reason.
So, in such a case, I backup my files to a FAT32 & then (after the EXT3 format), copy them back to Linux EXT3.


So is this something that can NOT be fixable?
Will I always have trouble when copying "make link" files (the Windows known "shortcuts") from EXT3 to FAT32?


Thanks for your response,

The pope.


P.S. > The Vatican's doors will always be open for all of you.

---

### Post by Kimm on 2006-02-22
Yes, shortcuts are build differently inside Linux then windows. This makes it impossible for windows to understand that it is acctually a shortcut.

Another reason is that difectories are completely different in windows and linux.
For example, windows will never be able to find a directory called "/usr/bin", just as Linux will never be able to find "C:\Program Files"

---

### Post by carlosqueso on 2006-02-22
[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features)  May be of interest to Your Holiness.....I realize it's from the heretical book of wikipedia, but is quite instructive.

---

