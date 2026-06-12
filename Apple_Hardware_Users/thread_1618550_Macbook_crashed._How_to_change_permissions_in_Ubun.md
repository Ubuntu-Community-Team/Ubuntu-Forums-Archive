---
title: "Macbook crashed. How to change permissions in Ubuntu?"
date: 2010-11-10
forum: Apple Hardware Users
---

### Post by Bwib on 2010-11-10
Hi guys, new to this forum. I assumed that this would be the place to come to inquire about the incredibly irritating problem that I've currently been faced with.

My macbook (2GB RAM; 2.1GHz dual core intel processor (I think)) recently crashed and wouldn't let me boot up into OSX. 

Due to my luck (of course), the last backup I did was about three months ago, and since then I've written a few EXTREMELY important essays for my A-levels, and without them, my life will hypothetically and literally go down the drain (parents/teachers/suicide will kill me) 

So, of course, I proceeded onto booting from the OSX install disks and attempted to archive and install, but I had too little HDD space to carry on with this.

I then remembered back to reading that snow leopard was in fact almost half as SMALL as leopard, so I went ahead and got myself a copy of that (legitimately, of course ;-) ) soon to find out that apple had scratched the 'archive and install' function on snow leopard. Great.

Next, I attempted to copy everything off my HDD and onto an equivalent sized external dive using terminal. (I copied some codes online. My actual knowledge of UNIX is extremely limited.) 

I finally came to the sudden realisation that I could attempt to see my HDD in a GUI'd environment by running Ununtu off the disk, right? 

So I proceeded to download Ubuntu and burned it to a disk, etc. 10 minutes later I had Ubuntu up and running. Clicked into the 'finder' equivalent and quickly found my 'Macintosh HD'. Thank God.

I was hoping that it would be as easy as just dragging the files that I wanted onto my external drive, but of course, it wasn't. There were permissions. 

I am now asking you guys HOW I would remove/change these permissions on these folders as my knowledge of UNIX and the Ubuntu OS is highly lacking. Is there a terminal code that I could use to remove them? If not, how? 

Thank you so much for reading and for your help in advance, 
Alex Glassman,
a desperate teenager in need.

---

### Post by hansdown on 2010-11-10
Welcome to the forum, Bwib.

Running the live disk, click 

applications> accessories> terminal.

Type

```
gksudo nautilus
```

Hit enter. 

You should be able to drag and drop your folders to a thumbdrive, etc.

---

### Post by Bwib on 2010-11-10
Hansdown, that seems to be working a charm. Thank you so much for your help, it seriously is appreciated!

---

### Post by hansdown on 2010-11-10
Glad you're getting things fixed.

Post back, if you have issues.

---

