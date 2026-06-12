---
title: "write directly to cd/dvd?"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by gatomlinson on 2007-07-14
I am using the latest fiesty-fawn liveCD and want to have tar(or what ever ) write directly to the dvd/cdrom in my writer. I have looked everywhere and have seen people pose the question, but no answers appear.  Creating small files in the in memory filesystem and then "dragging" them to the dvd/cd is dangerous and a pain (dangerous if I stuff it to full).

I can't figure out how to do it. 
 In:
  tar -cf filename  dir/goodstuff 
    OR
  tar -c dir/goodstuff >filename
  what do i replace "filename" with to force the archive to the dvd/cd?

 I don't think something _like_ the OLD "/dev/rmt" for magtapes would work here!
 
thanx
george

---

### Post by alzaf on 2007-07-15
I'm not sure if we've got our wires crossed here but I remember looking into a few years ago about the possibility of using a CD as a hard disk like the function in XP.

I'm sure it is that you need to format the CD/DVD as a UDF filesystem to to allow this. I've found two links about this.

[http://packet-cd.sourceforge.net/](http://packet-cd.sourceforge.net/)
[http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW](http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW)

Not sure if there is support for UDF on Ubuntu.

---

### Post by gatomlinson on 2007-07-17
thanks for the reply.  Yes I am asking if packet writing is supported in Ubuntu, and also if yes then what is it media is it supported on?  I am guessing the answer is NO since one seems to talk about it.  

By the way the links you posted were interesting and on target.  
**THANKS**  again,
george

---

### Post by Alchera on 2007-07-30
[HOW-TO: Packet Writing without tears]("http://ubuntuforums.org/showthread.php?t=129093&highlight=udf+support") \\:D/

---

