---
title: "about indexing remote folders"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-06-10
Is it possible to set Beagle search to index remote folders? 

I succeeded putting such folders in the "Places" bar within Nautilus GUI so that I can copy-paste, drag and drop files and everything but I still do not find how to point beagle to index such folders? The server I am connecting to uses SUSE Linux.

If beagle cannot do it, is there another desktop search tool that could do it?

One last question, how can I set up "search folders" in my desktop, I mean how to create a folder populated with the files from a search result that automatically re-populates itself when new files are created?

Thanks,
Daniel

---

### Post by DBStevens on 2007-06-11
Do you understand the potential load you will be placing both on your machine and the other system?

---

### Post by jdrodrig on 2007-06-11
Thanks for the reply...I

In terms of indexing...I was thinking more about periodic indexing and with a low priority as a process (I understand most indexing engines use only idle cpu time, isn't?)

Maybe too naively, but I thought that given that I can "see" the files in Nautilus, Beagle Search could index them whenever I am connected to the internet. My reference is that at school, I have my WinXP desktop using google desktop search configured to index some network folders that appear in "My PC" through a samba implementation.

What about folders containing the output of a beagle search, is it possible? could they re-populate automatically?

> **DBStevens said:**
> Do you understand the potential load you will be placing both on your machine and the other system?

---

### Post by DBStevens on 2007-06-11
Given enough baling wire, bubble gum, and time most things associated with computers manipulating data are possible.

The specifics involved can sometimes be very simple and sometimes not.

You could probably crontab a script to periodically push the beagle index button to repopulate a file of search results.   You'll probably also discover that this can result in flaky results when accessing the file as it is being repopulated.

These particular kinds of lash ups are possible, frequently messy, always fun to do, and sometimes illegal (this depends on many things).

---

### Post by jdrodrig on 2007-06-11
Well, it sounds, at least to me, a project interesting enough to work on...of course, I could just wait for Google to port its Desktop Search to Linux....but then I would not learn anything about file systems and shadow copies and at the end, about the true flexibility of bubble gum...

> **DBStevens said:**
> Given enough baling wire, bubble gum, and time most things associated with computers manipulating data are possible. The specifics involved can sometimes be very simple and sometimes not.

---

