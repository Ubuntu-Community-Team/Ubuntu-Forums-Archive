---
title: "Need help with dual boot install"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Uberuntu on 2007-11-21
I would like to have both windows and ubuntu on one hard drive. I partitioned my HD like so:

1)linux-swap 2 gigs
2)ext3 100 gigs (for gutsy)
3)NTFS 150 gigs (for xp)

The reason i want to do this is because i need xp to play my games and that is ALL i am using it for (if i use it for anything else it starts getting conflicts of all kinds and it becomes a nightmare). And i want ubuntu for multimedia and just general use. So that being said, i installed XP first with no problems. Then i tried to install gutsy and i got as far as the partition editor (this is in text mode) and i chose the ext3 for the root and gave it the option to boot. Then when i select "done editing partitions" it says ive made an error in the choices i made and it gives me the option to go back and edit. I dont know if i made a mistake in the ways i set up the partitions in the first place or if im missing something in the installer but if anyone can guide me through what im supposed to do that would be awsome.

---

### Post by bluepowder7 on 2007-11-21
presumably these are all primary partitions?  i'm not familiar with the text-based installer, but why not use the graphical one?  then follow the brief tutorial on psychocats

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by bobpur on 2007-11-21
I usually dualboot on two different HD's but I have done one or two on a single drive. 
My preference would be;
         1). NTFS (As you would install Windows first to not screw up GRUB)
         2). SWAP (As a no-mans land between two OS's)
         3). EXT3  (Linux as second install after Windows)
As I said this is my preference. I put my partitions in the order of install and use Swap as a barrier between Windows and Linux. I dunno, just me:)

---

### Post by rsambuca on 2007-11-21
What is the exact error message it gives you?  We are not mind readers here!

---

### Post by bluepowder7 on 2007-11-21
ooh, i think i've seen a similar error pop up.  have you actually edited the partition entires on that table to indicate which is mounted as /root (or simply / ), and which is to be formatted for and used as swap?

oh, by the way, don't flag that ext3 partition as /boot, but flag it as /root or just /
it needs an explicit / mount point assigned, and if you don't specify a separate /home and /boot, it'll toss those into that same partition by default.

---

### Post by doubl00 on 2007-11-21
Well, I played around with a dual boot installing Debian (command line) onto a 'spare' computer and wished  I had used the XP boot (NTLDR) instead of Grub.  When all was done and said, I had to edit menu.lst to start XP as the first first choice for others who would be using the computer.  I was able to reclaim all the hard drive space except for 500 MB that I left for the boot.  

So my recommendation would be to use the NTLDR to boot when it gives you the option to install the boot on the XP partition.  (hd0????).  

Sorry, I can not give too much specifics as I have only been at it a couple of days.  Perhaps someone else could expand on the benefits of which shytem should boot.

---

