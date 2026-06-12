---
title: "harddrive thrashing..."
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2007-12-31
Hi.
I have Windows on hda1(rarely accessed) and Kubuntu Gutsy on hdb1.
When I boot up, into Gutsy,  about 4 minutes or so after it's been started, one of the harddrives- I presume it is hdb- starts to thrash constantly for about two minutes or so. 
 This is usually when adept-update checks the system (when I notce the notification). 
Should this thrashing take so long just for update, or is something else going on , like indexing, or something? 
How can I check?
Can I check what might be running, as the thrashing is happening?
What do you think?
Happy New Year. \\:D/
Bob

---

### Post by taurus on 2007-12-31
Open a terminal and run
```
top
```

---

### Post by baracuda68 on 2007-12-31
> **taurus said:**
> Open a terminal and run
```
top
```

I guess I can use top to see what's running as the thrashing is happening...
Thanks.

---

### Post by The Cog on 2007-12-31
I think its probably indexing the whole filesystem. On Ubuntu, it's called something like updatedb and launches after a couple of minutes. I noticed it launches a little later on Kubuntu, 4 mins sounds about right, but I can't remember the program name.

---

### Post by meindian523 on 2007-12-31
Was that beagle?I'm not sure either.

---

### Post by asmiller-ke6seh on 2007-12-31
When you say that the disk is thrashing, do you mean to say that the disk drive seems to be doing some work for no apparent reason - that is, you are not using any application that you would expect to need enough disk resource to require the disk drive to be active (such as downloading, or watching a video that is stored on your hard disk drive)?

Hard Disk Drive thrashing has another meaning; the following is from Wikipedia:  [COLOR="Blue"]Paging or swapping systems that are overloaded waste most of their time moving data into and out of core (rather than performing useful computation) and are therefore said to thrash. Thrashing can also occur in a cache due to cache conflict or in a multiprocessor.[/COLOR] 

Usually, disk thrashing refers to the requirements to move data from main memory to the disk drive and from the disk drive to the main memory (cache) so often that the system does not seem to accomplish much (so it is drive- bound). I don't think you are referring to this.

Happy New Year.

---

