---
title: "What is wrong with these pictures? Disk Related."
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by SMF on 2006-02-19
Ok gang. Get your thinking caps on :mrgreen: 

I did a manual partion using Partition Commander before is installed Ubuntu.

When I did install Ubuntu, I think I made more partitions. What I want is to get any extra space back on to my ubuntu partition since I am going to using ubuntu now and kinda kicking windows to the curb.

With that being said.....Here is what I got. BTW is there a tool I can use while on ubuntu to gain that space back or do I have to go back to my windows xp and figure it out on there?


[IMG]http://img387.imageshack.us/img387/632/screenshot8kb.png[/IMG]
Partition 1 This of course is a shot of my NTFS and those 14/16 GIGS are allocated to Windows. Blah.


[IMG]http://img91.imageshack.us/img91/7768/screenshot12ms.png[/IMG]
Partition 5 is not in use. How do I get that 4.93 GIGS over to my ubuntu?


[IMG]http://img91.imageshack.us/img91/153/screenshot29qf.png[/IMG]
Partition 6 is being used by ubuntu 



[IMG]http://img91.imageshack.us/img91/3730/screenshot38lp.png[/IMG]
What the hell is a swap partition? 



[img]http://img91.imageshack.us/img91/1328/screenshot44iv.png[/img]
Dont know where this partition 3 came from and why it has only 101 MiB



[img]http://img91.imageshack.us/img91/4736/screenshot58cp.png[/img]
Partion 4 has some meat on it too:mrgreen: but is not being used. How can I get those 13.35 GIGS to ubuntu?




Thank you for taking the time to look into my matter and I hope I made my self clear enough to come up with the answer. BTW I only have WinXP and Ubuntu installed on 1 HD.

Which also reminds that when I boot/reboot ubuntu I get the same messege duplicated one over the other about wether I want to log in regular or do I want to arrow down and log in to recovery mode. Why are that feature listed twice on the same screen one under the other? I am sure there has to be reason to that but it just looks odd to me.

Thanks again for you time and I will hope for a response soon.

Sincerely SMF who lives on ubuntu

---

### Post by cjm5229 on 2006-02-19
Hi, Yes you appear to have too many partitions there. The easiest fix is to reinstall Ubuntu and when the disk partitioner comes up do a manual partition. When the partitioner comes up again click on each extra partition and use the delete option. once you have deleted all the extra partitions click the empty one and choose the, install to empty space, option. You may use a live CD and redo the partitions with Gparted "Applications>System>Gparted. The way it looks though, you would still have to reinstall Ubuntu. Gparted would let you resize the Windows Partition, and create a fat32 partition you can use to move files back and forth between Windows and Ubuntu. Herman has a great howto here,       [http://http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")

---

### Post by Netisan on 2006-02-19
Don't hurry to reinstall! I've never partitioned automatically but I still can see strong reasons for that partitioning. 
First partition goes for your existing windows 14+ G means you have lot of stuff there. 
Second windows 4+ G one is probably a newly created and serving as an exchange-with-windows place. Readable and writeable by both OSes. Third obviously is root. Its OK to have separate root if you plan to experiment with Linux distros, etc. But your root is in fact your entire ubuntu. 
Swap is essential for Linux (though ubuntu works without it as separate, or it all). It's OK. 
The small not mounted partition should go for boot. If so, it's OK. 
And the last big unused one is in fact free space that you can manually manage. For instance, you can create a home partition, and separate it from root. 
Again, everything is OK for the moment!

---

