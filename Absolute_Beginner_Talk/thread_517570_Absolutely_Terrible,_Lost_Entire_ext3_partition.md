---
title: "Absolutely Terrible, Lost Entire ext3 partition"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by ScaredNoob on 2007-08-04
Hey everyone,

I was in windows going to reformat an external hard drive  when  I accidentally deleted the linux partition (ext3) from my active hard drive.  I did not reformat the hard drive, it is now simply unallocated space.  To make matters worse, the now linuxless laptop has a burned out cd rom drive.  Here's what I'm thinking...  I have in my possesion a dsl-not bootable usb drive with fully functional internet and kernel 2.6.  I read a similar post talking about using a program called testdisk[testdisk]("http://www.cgsecurity.org/wiki/TestDisk").  If anyone out there can take a look at testdisk and my idea of running it from usb damn small linux and tell me I'm on the right track (or not) it would make my day.  One quick question:  will damn small linux use that precious unallocated space (with all my digital camera pictures on it) as a swap drive when booting?  Please help me save my precious memories.

Thanks all,

Mike

---

### Post by benx009 on 2007-08-04
if testdisk will work in dsl, then go for it:)  do not worry, dsl will not use the extra space as swap.

good luck:)

---

### Post by carloslosgrande on 2007-08-04
I agree with Benx009, give it a try.

---

### Post by ScaredNoob on 2007-08-04
> **carloslosgrande said:**
> I agree with Benx009, give it a try.

I will give it a try, but this is priceless stuff I'm dealing with here so I want to make a backup first.  How about this... I have an case for a 2.5" hd.  I put the lappy hd in there, take it to my other computer and use gparted to create a copy of the entire hd... will that work?  Can gparted copy unallocated space (ie the lost partition) or does it just do actual partitions?  Sorry if these posts are getting progressively more paranoid and/or desperate but you guys gotta understand I just lost 5 gigs of my digi cam pictures.  Thanks for the help everyone...

---

### Post by carloslosgrande on 2007-08-04
I think maybe PartImage may be better suited for that, have a look here;> [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

