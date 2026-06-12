---
title: "Reading files large than 2GB"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-09-30
I when to burn my wow install files to a few dvds and one fo the file in 3.75 GB.  when i went to burn it it said only window can read that file over 2.0 GB because it is use the UTF format.  so can ubuntu can files burned in UTF format?

---

### Post by smylie on 2007-09-30
Hi

The normal dvd ISO9660 file system can’t handle files larger than about 2 gig (which can be a real pain). Depending on what you're wanting you've got a couple of ways around it:

I've had this issue in the past, and [a few ppl]("http://k3b.plainblack.com/message-board/udf-data-dvd---files-bigger-than-4gig") mentioned that you can use Nero to burn them (as iit has udf filesystem support built in). 

I needed to burn encrypted folders (4 gig in size) to DVD - as I didn't need to read them in windows, I was able to use [growfs:]("http://blog.smylie.co.nz/17/easy-mostly-secure-free-off-site-backups-on-ubuntu-with-truecrypt-goodness%e2%84%a2/"). 
The down side to this though was not being able to directly read the image off the disk - it had to be copied back to a hard drive somewhere and mounted via loopback. (But in my case, for encrypted files further obfuscation is a good thing =)

Cheers
Dave Smylie

---

