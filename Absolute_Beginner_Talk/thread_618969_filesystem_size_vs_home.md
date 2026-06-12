---
title: "/filesystem size vs /home"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by whazooo on 2007-11-21
hello
I have a 149 gig partition reserved for ubuntu.
when installing , I used it all for /

The more I get into ubuntu, I feel I should divide this partition
into a / 
and a /home.

I use lampp for website script and page development.

I also have many video and music files. I also use wine with many web development tools

I figure 50gig for /

and the rest as /home 

My question really is, Will 50gig be sufficient for root directory?

Also if I add a third hard drive (sata) will I be able to split it between / and /home?

TIA
Whazooo

---

### Post by siciliancasanova on 2007-11-21
I have a 200gb HDD.

20 gb for /
and 157gb for /home

It has worked plenty fine for me

EDIT:  I'm also a web dev with the same set up that you need as far as applications and the linux/apache set up go.

---

### Post by LaRoza on 2007-11-21
I do not follow the typical Linux method of having /home in a larger partition, and / in smaller one. I do not use /home for storing data. I have other partitions for this, and are given names according to their data.

I have Ubuntu (/ and /home) in a single partition, and several other partitions of various sizes for data.

I use a directory on another partition for my web sites (for development purposes) by adding an alias to Apache. I don't know if you want to do that, but that is what I do because I have two hard disks with an operating system on each, but neither use the whole drive.

---

### Post by bluepowder7 on 2007-11-21
+1 (sort of) to not storing my files and docs in the /home directory.

i have /root and /home residing in what totals 5gigs or so, and all of my documents, music, and other crud is in a whole separate partition that is mounted as /media/stuff, and that partition is a good 40gigs and up - and it could be a whole 500gig partition if it's on a second SATA drive.  this way, if i do obliterate an OS or add another one, those docs that are shared across multiple OSes like my resume, spreadsheets, presentations, tunes, and pornpics are all in a non-home and non-OS-specific directory.

---

### Post by MrFSL on 2007-11-21
Since the home directory contains most of the users configs, I also use it to store most of the data. This simplifies backups and disk imaging.

I personally don't use my home folder to hold my dev files, instead I have a directory /home/storage which is then subdivided by project.

For me this works well.

---

### Post by whazooo on 2007-11-21
Thanks for all the replys,
I'm going to go with a
 /  
 /home 
schema. 

I have two 300 gig drives on the system.

the first is sda1 and is a ntfs single partition for windows. (i know, I know)

the second drive is split evenly between an ntfs partition for transitional stuff and ubuntu.
heres a screenshot of the second drive:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=50895&stc=1&d=1195636409[/IMG]

My plan is to use gparted to reformat sdb3 to ext3. 
If I remember right, I cant merge partitions to the left.
so I'll move it to the right of sdb1 then merge sdb3 into sdb1.

that will give me a 290gig or so sdb1.

From that I'll cull the /home directory to 200 gigs and the rest for /

In my home directory I have four users, 
The main one (me) for updating and sys admin stuff + music+videos+websurfing
number 2 for stuff I do in wine
number 3 for my scripting+music
number 4 for web development

My main reason for the separate partitions is for ease of backups.

My lampp is set up in /opt so eventually I'll most likely want to add /opt to its own partition.

I'm going to follow the great advice from here to get started:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)  

Does it seem I'm on the right track as far as ease and security goes?

Thanks again
Whazooo

---

### Post by natehatewindows on 2007-11-21
just talked about this yesterday...

[http://ubuntuforums.org/showthread.php?t=618146](http://ubuntuforums.org/showthread.php?t=618146)

---

### Post by whazooo on 2007-11-21
Yes I saw your thread, But because I had diffrent questions and reasons,
I didnt want to do any threadnapping and decided to start one of my own.
lots of good info over there.

---

