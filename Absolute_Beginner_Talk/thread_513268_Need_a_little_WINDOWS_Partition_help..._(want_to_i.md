---
title: "Need a little WINDOWS Partition help... (want to install on partition)"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-07-30
So I have an old XP machine (upgraded from 2000 - has a bunch of programs and basically this is the PC that no one uses -  so we are handing it off to my bro.)

I want to install ubuntu on a different partition.

I did this
"click Start, and then click Control Panel. Click Performance and Maintenance, click Administrative Tools, and then double-click Computer Management. " then navigated to my disk. I have the following:

[IMG]http://image.bayimg.com/caemnaabo.jpg[/IMG]


I am not sure if 4gb is enough to install and run ubuntu and since I do have an extra 8gb left in the C drive, how do I take that extra 4 gb + add 4gb out of the remaining 8gb for the windows one making 8gb and 20gb partitions? 

Hope you can understand my blah blah blah :lolflag:

Thanks

---

### Post by FleetAdmiral74 on 2007-07-30
In XP, first you will want to defrag. Maybe more then once, but you want to see everything shift left.

Now I don't think 8 gigs is enough. Maybe you could, in fact, install, but after some use it would fill up. You can check the sys requirements for Fluxbuntu, which might be lighter weight. If not, you will have to use something like Damn Small Linux (only 50mbs)

Well either way you will use gParted (either off the Fluxbuntu CD if you use that, or of a seperate gParted CD (is easiet) if you use DSL) and use that to just modify the partitions, making the xp one smaller, and then creating a linux one with some swap in the extra space. Then installing. 

If you need more, do a quick search on dual booting xp and ubuntu. Lots of guides out there.

---

### Post by dptxp on 2007-07-30
Backup Data.

The XP partition surely has a lot of data. Delete Some, you can put it in separate data partition that can be common for XP and Ubuntu.

Suppose final used capacity is 15 GB.

Defragment the C drive in Windows.

Now you can make your new partitions either with GParted Live CD or Ubuntu CD.

Resize the C Drive to 18 GB. You can make it smaller, depends on how much space your program files are using.
Delete all other partitions.
Make /root ext3 - 4-6 GB.
Make a data partition of rest space minus 1 GB, give any name, can keep the default name, format in ext3. This will be 7-9 GB
Last 1 GB SWAP.

Total 4 partitions, so you can make all primary.

---

### Post by ajskhan on 2007-07-30
> **FleetAdmiral74 said:**
> In XP, first you will want to defrag. Maybe more then once, but you want to see everything shift left.

Now I don't think 8 gigs is enough. Maybe you could, in fact, install, but after some use it would fill up. You can check the sys requirements for Fluxbuntu, which might be lighter weight. If not, you will have to use something like Damn Small Linux (only 50mbs)

Well either way you will use gParted (either off the Fluxbuntu CD if you use that, or of a seperate gParted CD (is easiet) if you use DSL) and use that to just modify the partitions, making the xp one smaller, and then creating a linux one with some swap in the extra space. Then installing. 

If you need more, do a quick search on dual booting xp and ubuntu. Lots of guides out there.

Actually I am quite convinced 8gb is enough. I installed Ubuntu on a old 9gb HD in a super old laptop, see sig, and it still has 6gb left. It depends what you'll use it for, this will be primarily internet games (arcadetown.com, etc) and other websurfing/chatting. nothing else... so - how do I go about resizing my current used and used partitions?

---

### Post by FleetAdmiral74 on 2007-07-30
> **ajskhan said:**
> Actually I am quite convinced 8gb is enough. I installed Ubuntu on a old 9gb HD in a super old laptop, see sig, and it still has 6gb left. It depends what you'll use it for, this will be primarily internet games (arcadetown.com, etc) and other websurfing/chatting. nothing else... so - how do I go about resizing my current used and used partitions?

when you boot up and use gparted, it will become apparent. You can just click and drag the partition sizes. have you tried yet, or just wanted clarification.

---

