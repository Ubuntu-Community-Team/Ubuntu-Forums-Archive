---
title: "Partitioning Question"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by carrie.peary on 2006-10-29
I got to the part about partitiong and resizing my drive (Step 5 I think). I want to resize by the first choice (Resize IDE1 Master or something like that).

Anyways, the slider comes up with the percentage and disk space and that's where I stopped.

My question: Which is it showing me? Is the part it tells me info for the one that my Windows XP will run on? Or is this for Ubuntu? For instance, I want 10GB for Ubuntu, so would i roll the slider closer to the right? 

Just checking before I continue. Thanks!

---

### Post by tonyr on 2006-10-29
Give some more details, first.  How big is the drive? How many partitions
are there already on it?  Is XP already installed?  If XP is installed,
did you deframent the XP partition first?

Which instructions are you using?

And now the answer to your question.  The Resize applies to the existing
XP partition. You want to make that one SMALLER to create room for the
Ubuntu partition.

---

### Post by carrie.peary on 2006-10-29
It's on my laptop so it's only one drive, and I don't believe that there are any partitions already on it, since Windows is the only thing I run right now and I had no clue what partitioning was until a couple days ago. And yes, I deframented my drive so I have room. 

The instructions I'm following are here: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

And I have a 70GB HD, with 42GB free space. 

Thanks for the help! I guess I'll resize it to have 10GB free space on the end.

---

### Post by tonyr on 2006-10-29
Sounds like you have a good handle on it.  Have fun and good luck.

---

### Post by carrie.peary on 2006-10-29
OK, I tried to repartition it with 62GB for Windows, with the rest for Ubuntu and it says that it could not do it, any ideas why?

---

### Post by tonyr on 2006-10-29
Nothing specific. When you defragmented, did the fragment diagram
show a reasonable result, i.e. lots of empty space at the right
end?   One article I read reported having to defragment 3 times
to get a reasonable result (see [this article]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html"))

Here are a couple more references.  You may have to do more work, and/or
do the repartitioning independently (outside of the install process).
[http://www.devhood.com/tutorials/tutorial_details.aspx?tutorial_id=405]("http://www.devhood.com/tutorials/tutorial_details.aspx?tutorial_id=405")
[http://www.howtoforge.com/windows_linux_dual_boot]("http://www.howtoforge.com/windows_linux_dual_boot")

---

### Post by willy1234x1 on 2006-10-29
10 gigs seems a little small I'd say go with 15 but I wouldn't know how to help you since I completely cleared my HD and installed ubuntu

---

