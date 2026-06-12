---
title: "MacPro [OS X on one disk Ubuntu on another] (trouble mounting in os x)"
date: 2008-12-22
forum: Apple Hardware Users
---

### Post by papoose on 2008-12-22
So I ve been wanting to check out the hype about Ubuntu for a while. I finally gathered my strength and jumped right in it. I decided to install Ubuntu on my drive in bay 1. As a previous install nearly killed my system because of an error on my part, I took out my other drives from their bays. Before that I lauched bootcamp to tell it I was going to install an OS. So I boot on the cd and install directly everything goes well and soon after a couple of false restats I get Ubuntu to run from my hard drive. As my other drives return to their bay, I boot on OSX to check if everything is fine. And almost everything is, almost because every time I boot on my OS X disk, I get a pop up telling me the Ubuntu drive is not recognized... asking me to either format it ignore it or eject it. Now I have installed Refit which seems to works well for switching back and forth I ran its Table sync thing. 

So I thought that OS X doesnt recognize the linux file system of the disk which is the reason of my small problem. Thus I installed Macfuse, which unfortunately had little to no effect! I 'm hoping to get some insight for people runing both system each installed on a separate disk (it seems the most frequent installation is over partitions). Thank you in advance for any suggestion.

---

### Post by jwhendy on 2008-12-22
Excellent inquiry... I have not solved this problem myself. My solution since I use OS X as my primary OS (kind of...) and definitely as my primary storage location (the larger of my two partitions) is to simply store everything I need on the Mac side since I can access it via Linux. I cannot access things the other way around. I tried to read about MacFuse as I hadn't heard about it before, but I couldn't find a clear cut list of supported file systems.

I'd be interested to hear if you're able to access ext2/3 or xfs or reiserfs (what did you use for your Linux partition, by the way?) from OS X.

If it helps at all, my set up is as follows:
- 65 GB partition for OS X: stores all OS X system files (obviously), all OS X apps, and all my personal data (docs, pictures, music, etc.)

- 15 GB partition for Linux: stores all Linux system files (obviously) and the only thing else are Linux apps and the various things in my home folder (all the files with a . in front of them, usually user preferences, configs, and settings for apps). I created symlinks (like aliases) for my most used folders on the OS X side in my home folder so I can easily access my data from the Linux side. That gives me a generous helping of space on the Linux side for apps and anything else and leaves the rest of my OS X side for my 'storage bin'.

If you'd be interested to try out this setup, I'd be happy to help you out. You may have a tricky time getting your OS X partition to mount read-write. This is common. It's worked fine enough for me and I find it to actually be more 'uniform' regarding a storage system. Why have two folders of 'documents' on each OS partition? They're all your files - keep them in one place and just access them from each OS when you want.

Last note (can you tell I'm long winded?): I use Thunderbird and was able to set up the storage location for emails on the OS X side such that the Thunderbird on each OS accesses the same 'repository' so my emails are seamlessly shared whether I'm booting OS X or Linux. I thought that was pretty cool. I'm huge on filing emails in a mail client (vs just using gmail), so having access from each partition was a big deal for me. Ask away any questions you have - I'd love to at least get you over the hump to give a fair shot at Ubuntu or Linux in general rather than have you get frustrated on your second attempt - I have almost walked away several times!


-John

P.S. My apologies - I just noted that you use a separate hard disk for each. I 'read' that the first time, but it didn't sink in until I was re-reading your post. I don't think anything I wrote should be affected by which hard drive you boot from. The 'theory' (I believe) is still the same. Partitions look like separate disks to the OS, so anyone using the partition method will encounter the same problems/solutions as you do with separate hard disks. I think this is correct, anyway.

---

### Post by cyberdork33 on 2008-12-24
There is no good driver for ext2/3 in OSX now.

---

