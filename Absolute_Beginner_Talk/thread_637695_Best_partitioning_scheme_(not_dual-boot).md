---
title: "Best partitioning scheme (not dual-boot)"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by skroops on 2007-12-11
I am curious about which partitioning scheme is the best for a pure ubuntu installation, without dual-booting.  I've seen some reccomendations, but most of them weren't justified, and after searching for a definitive answer (not likely anyway), the most things I found were related to dual-boot systems. (like this article: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)).  I understand that a seperate /home is a good idea but I've seen suggestions for a /opt and /var, what do these do and what size should they be?  If there is an additional hard drive I've heard that a /swap on the other hard drive improves OS speed, is this true?

The last time I reformatted this was my set up:
/boot 100MB ext2

and the following with LVM
/ 10 GB ext3
/swap 3GB (I know this is too big but that's why I'm using LVM)
/home ~65GB ext3

Is that about right, and where should /opt and /var fit in there? 

Also I'm considering converting my Windows MCE box into a mythbuntu front/backend
I have 2x500GB hard drives running as raid0 and a 120GB hard drive in that system.
What would be the best use of that space for a mythbuntu system, and should I use xfs or ext3?

Please justify your responses with reasons for your suggestions, that's the reason why I'm asking.

---

### Post by swoll1980 on 2007-12-11
I would would create one partition for the entire hardrive for /  I found that using a / and a 
/home ends up making some of the drive wasted space. It will actualy be two partitions because you need a swap too. Your swap should be twice as much as your ram. as far as xfs vs ext3 goes ext3 is readable by windows with a driver called fsdriver you can download from thier web site so that makes thing easier down the road

---

### Post by jaybombalous on 2007-12-11
> **bloor75 said:**
> I would would create one partition for the entire hardrive for /  I found that using a / and a 
/home ends up making some of the drive wasted space. It will actualy be two partitions because you need a swap too. Your swap should be twice as much as your ram


complete and utter bs. U don't need a swap and u don't need it to be twice as much as your ram. If u do have a swap and it is over 500mb then its to big, u will never use it all and thats** WASTED **space!


and as far as I know u can't setup LVM on a /boot (bootable) partition. But does that what LVM- means? Kind of confusing right there???

Personally I would only encrypt the /home partition and leave / (root) as is. Everything in / (root) is open source anyway, whats encrypting it gonna prove,except increase application load time? Ask me /home is the only partition that needs LVM and my home directory right now hasn't even hit 1gib of used space.

---

### Post by vanadium on 2007-12-11
It is to a certain extent a matter of preference, and there are no hard rules of what is "best". For a laptop with a relative small hard drive (say 40 - 60 GB), I would not hesitate to recommend just the default approach of the Ubuntu install program: a root and a swap. Rationale for a separate swap partition over a swap file: it is accessed slightly (= not noticeably) faster.A separate /home has some advantages: 1) you cannot accidentally fill the system disk (although Gutsy should handle such a situation better); 2) on fresh reinstall, you can keep your user data in place, and even take over the application configuration settings of your previous OS; 3) if anything happens to the /home partition, the system partition remains unaffected and vice versa.

Bottom line: for personal desktop computers, it does not matter that much. It is different when you build a large server system.

---

### Post by swoll1980 on 2007-12-11
whatever you say buddy

---

### Post by Bartender on 2007-12-11
> **bloor75 said:**
> I found that using a / and a /home ends up making some of the drive wasted space. 

I'm not sure what bloor means by "wasted space".  

I think that for the average Linux user (in other words, no college degree in Linux system administration) the var and opt and etc. partitions are probably unnecessarily geeky.

From my own experience, a separate /home partition is an absolute must.  Last week I screwed something up and was stuck with some kind of weird "Kernel Panic Error" message.  I didn't know what to do so just re-installed Ubuntu to the /partition.  30 minutes later I was up and running again like nothing had happened.  Documents, music, photos, even desktop wallpaper and the icons in the panels were all there on the first boot after re-install.

I love Linux \\:D/

I don't worry about swap.  If you've got at least a gig of RAM it'll be used rarely if ever.  As long as your HDD isn't so small that you're carefully rationing storage, just set it at a gig and don't worry about it.  There may be some small boost by putting swap on a separate drive but if it's rarely accessed then why fret about it

---

### Post by skymera on 2007-12-11
to be honest

i have one partiiton of 50GB EXT3, pwerhaps changing to  ReiserFS

---

### Post by rahimveron on 2007-12-11
A Separate /home partition should be created to avoid data loss after re-install and save yourself re-configuring the applications all over again. In short, it saves time and effort.

---

### Post by skymera on 2007-12-11
i find ubuntu only takes 30mins to get settings back, so id rather just scrap it all,

then atleast you dont have invalid menu items and setytings.

---

### Post by ken_vh on 2007-12-11
> **skymera said:**
> i find ubuntu only takes 30mins to get settings back, so id rather just scrap it all,

then atleast you dont have invalid menu items and setytings.

Exactly.
And people should regularly make a backup of their /home/user folders anyway, so there's no problem in recovering that after a reinstall in either case.

---

### Post by skymera on 2007-12-11
> **ken_vh said:**
> Exactly.
And people should regularly make a backup of their /home/user folders anyway, so there's no problem in recovering that after a reinstall in either case.

yeah i backup my music and pictures onto an external about once everry...2months.

when i reinstall i have a fresh system

---

### Post by az on 2007-12-11
> **rahimveron said:**
> A Separate /home partition should be created to avoid data loss after re-install and save yourself re-configuring the applications all over again. In short, it saves time and effort.

You can do that without creating a separate partition -  just do a conventional backup.  It's easier and safer to just do a backup.  A separate partition on the same drive will not spare you from hardware failure and is a false sense of security.

Not to mention that you limit your use of disk space by creating more partitions.  You only need a / partition and a swap partition for a desktop.

There may be reasons for keeping separate partitions, but none of them apply to a simple desktop system.  For example, on a mail server, you may want to create separate /var partition so that a spammer doesn't take down your system by filling up your hard drive.

---

### Post by thelatinist on 2007-12-11
Is the reason people warn to create a separate home partition just so you don't lose data in your /music /documents and /videos folders?  Because who would keep those in their /home folder anyway?  The first thing I did when I installed Ubuntu was create a separate data partition and set those bookmarks to link there.

I've been following other people's advice to create a separate /home partition, but increasingly wondering why.  If I've got the few MBs of config files in there regularly tarred and saved on a separate partition, I can always restore from there, no?  And since I regularly back up /root, wouldn't it be even easier just to include that in my regular backups?

---

