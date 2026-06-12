---
title: "File Serving"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by IanA on 2006-01-25
Does anyone here know a good place to start (like a webpage with instructions) on setting up a file and printer server with Ubuntu? I'm new to Linux, so I promise I'll eventually get it. Also, some of my old Macs still use Appleshare, so I need the name of an Appleshare Client that will work with Ubuntu.


Thanks,
Ian A.

---

### Post by tabinin on 2006-01-26
What are you sharing to?  Only Mac?  Or Windows, or another Linux box?  

Also, take a look at "netatalk".  I found it by using the [google linux search]("http://www.google.com/linux").  There are some articles there is you search for "appletalk".

---

### Post by IanA on 2006-01-26
I'm going to have Windows, Macs and Linux Boxes. I'll look at Netatalk. Thanks for the link. I had forgotten about Google Linux.

Ian A.

---

### Post by tabinin on 2006-01-26
I use Samba to share files and printers to Windows and NFS to export files to Linux.  For sharing to the Macs, I would guess NFS would work for newer versions of the OS (actually, Samba should too).  If you want a nice simple Samba config file as an example or to get started, let me know and I will post mine here.

There are lots of samba and NFS HowTos on this forum just a search away.

---

