---
title: "advantages to /home/ on separate partition and other partitioning fun"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by NicoleM on 2007-03-26
ok i'm that much closer to making the jump to install now...I think i've read every partitioning thread on the forum plus a lot of external links as well.  I'm very familiar with windows partitioning schemes. [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) has been particularly helpful in helping me apply that knowledge to linux.

right now i have a master and slave hd on primary IDE cable and a external USB drive.

master drive has a C partition for Windows then the rest data.  I like keeping the OS separate in case I want/ned to reformat.

my slave drive will be clear in preparation to install linux.  I understand i need a partition for root and one for the swap.

the size of my swap partition will be  about 1.5-2gigs.

my main question here is whether it would make more sense to put the OS in 1 partition or to make a separate /hom/ partition as I've seen in other guides.

also i know it can vary from user to user, but on average how big are your partitions.  I like to keep as much of the hard drives partitioned for data as possible.  I do a lot of digital video work and need all the space I can get. 

so my partitioning options right now are:

entire ubuntu os (?? GB), swap (1.5GB)

/root/ partition (??GB, /home/ partition ??GB, swap (1.5GB)

which of the above options do you think is most in line with being able to clean install often (due to either curiosity or user error).  and what's an average idea of how much space i should reserve for each partition (again, I understand it can vary based on programs, but at the moment i have NO basis for reference when it come sto specific sizes

ONE more quick question: I want to stay away from FAT32 for shared data partitions because i sometimes work with very large files.  is ther any advantage to using the ntfs-3g for linux and just using ntfs for shared space over using FS-drive for windows and having windows read/write from linux partiitions?

EDIT: the hard drive in question is about roughly 279GB capacity once you do the bits and bytes marketing math from a 300g drive if oyu needed an idea of the amount i'm space i'm working with for this isntall.

---

### Post by aysiu on 2007-03-26
Having a separate /home partition in Ubuntu is like having a separate C:\Documents and Settings partition in Windows. It's perfect for someone who reinstalls often.

As for sizes, I think I allocated about 15 GB for the Windows partition I never use, 9 GB for Ubuntu, and 130 GB for data (I use a separate /documents partition instead of a separate /home because I don't like all my settings carrying over from one install to another--only my Firefox and Thunderbird ones).

You can find out in this thread about different people's approaches to space allocation: [What's your partition table look like?](http://ubuntuforums.org/showthread.php?t=386169)

---

### Post by stimpack on 2007-03-26
/dev/hda5             9.8G  3.0G  6.9G  30% /
/dev/hda1             102M   64M   39M  63% /boot
/dev/hdc1             153G  138G   15G  91% /home
/dev/hda3              30G   18G   12G  60% /media/windowsc
/dev/hda6              35G   11G   24G  32% /media/windowsd

My fairly matured system. I gave nearly 10G for / but only 3G used, so next time Ill knock that down some.

God knows why I have a /boot, I read some guide, forgot now.

1G of swap not shown, tbh ive never seen swap used, I have it anyway, 1G doesnt hurt nowadays.

/home is essential to have as its own partition, you keep all your data here, so make it *big*. You can now reinstall, full clean upgrade, and keep you data partition as it was.


just to clarify somthing in your post. You need a '/' partition (often called root partion), You do *not* need a /root partition. (user root)

---

### Post by aysiu on 2007-03-26
Oh, I forgot to mention that I have never used more than 4 GB on my regular / partition (as opposed to the /documents partition where all my data lives).

---

### Post by NicoleM on 2007-03-26
thanks for the input guys.  that's one partition thread i must have missed...good stuff.

ok so a 8g / (not /root/ thanks for the clarification!) partition should be sufficient.

still one question about the /home/ partition:  if i'm storing all documents on an external drive and would just like to keep /home/ for settings and general "computer stuff" to make reinstalls more smooth how much would you recommend i reserve for /home/

i have a pretty detailed storage system for my current files at the moment and was hoping to just add new files to the current scheme. using ntfs-g.  Under this line of thinking, i wouldn't need /home/ for so much storage as much as I'd like it to just be there to save current settings for when i reinstall.  does this make sense?  or am I off base in the usage of the /home/ directory.

as much as i'm sure you guys are sick of windows comparisons ;) my c:\documents and settings folder doesn't contain any personal data files at all...i sort all of that manually in an array of other folders.  some some users with a docs and settings folder that contains data would need as much space as possible.  my docs and settings folder is only about 1.5GB

i don't intend to use /home/ for data files, i'll be using shared data drives for this.  

will it be trial and error to see how much my /home/ partition uses?  is 5gb sufficient for settings? 10gb?

---

### Post by aysiu on 2007-03-26
The config files in /home would be negligible as far as space goes (probably not more than a few megabytes, I'm guessing), **but** you should keep in mind that if you ever download something to your desktop (like a huge DVD image or something), that your desktop lives inside your /home/nicolem folder. There should be enough space to accommodate any data temporarily located in /home, even if it eventually moves to an external drive.

---

### Post by NicoleM on 2007-03-26
> **aysiu said:**
> The config files in /home would be negligible as far as space goes (probably not more than a few megabytes, I'm guessing), **but** you should keep in mind that if you ever download something to your desktop (like a huge DVD image or something), that your desktop lives inside your /home/nicolem folder. There should be enough space to accommodate any data temporarily located in /home, even if it eventually moves to an external drive.

great! that's about the answer i was looking for.  even if i have overkill for my / and /home/ partitions I'd definitely rather err on the side of having too much than too little space.  I'll still have installed the whole OS in less space than my windows partition takes up.

i think i'm going to set aside a nice even 20GB, i'll go 8 for /, 10 for /home/, and 2gb for swap from what i've been reading this should be more than enough.

you guys have been a big help! thank you

---

### Post by NicoleM on 2007-03-26
oops! just thought of one more thing.  the link i referenced in my first post mentions the swap partition being at the end of the physical disk, but the author said he/she wasn't sure why, but that's where default installation usually put it.

could i have say

|__/__|_/home/|_swap_|_____________data_____|

or does swap have to be at th eend of the physical disk?

---

### Post by Pausanias on 2007-03-26
One more thing. If you use Evolution as your mail reader, it will store all your email in a .evolution folder in your home directory. Mine's pushing a Gig now...

Plus there is .Trash for your deleted files from the desktop, and the .thumbnails cache in your home directory that can get big depending on your usage. Various other applications will use space in a .whatever file. The best way to check your system is to do a

```

 du -ck ~/.??* | sort -n

```

The bottom line will tell you how much space you are using in your dot files, and it'll be all sorted for you above that line.

> **NicoleM said:**
> great! that's about the answer i was looking for.  even if i have overkill for my / and /home/ partitions I'd definitely rather err on the side of having too much than too little space.  I'll still have installed the whole OS in less space than my windows partition takes up.

i think i'm going to set aside a nice even 20GB, i'll go 8 for /, 10 for /home/, and 2gb for swap from what i've been reading this should be more than enough.

you guys have been a big help! thank you

---

### Post by Pausanias on 2007-03-26
It doesn't matter where swap is.

> **NicoleM said:**
> oops! just thought of one more thing.  the link i referenced in my first post mentions the swap partition being at the end of the physical disk, but the author said he/she wasn't sure why, but that's where default installation usually put it.

could i have say

|__/__|_/home/|_swap_|_____________data_____|

or does swap have to be at th eend of the physical disk?

---

### Post by NicoleM on 2007-03-26
> **Pausanias said:**
> One more thing. If you use Evolution as your mail reader, it will store all your email in a .evolution folder in your home directory. Mine's pushing a Gig now...

Plus there is .Trash for your deleted files from the desktop, and the .thumbnails cache in your home directory that can get big depending on your usage. Various other applications will use space in a .whatever file. The best way to check your system is to do a

```

 du -ck ~/.??* | sort -n

```

The bottom line will tell you how much space you are using in your dot files, and it'll be all sorted for you above that line.

thanks! definitely bookmarking this post and I'll try to keep an eye on my usage.  I recently migrated away from thunderbird on my windows system in favor of using gmail's web interface.  If i went back to a client I'd probably use thunderbird and not evolution, but I'm sure it's a valid concern in either circumstance.  

Now i'm getting impatient.  I'm working on getting some larger video projects finished and off my computer so I can have a totally clean drive to install ubuntu.  I think I'm still a couple days away from an install as of now by the time I finish all of the projects, but at least it's giving me some time to do some good research and do some serious forum browsing.

thanks again :)

---

### Post by arron on 2007-03-26
Be a true geek!  Run squirrelmail, your own web based email server, and host it on your own website.  I have run it for years, and i can still connect via imap server on my lan so i can use whatever email program to view the mail in the folders.  Add this with fetchmail and hotway its a total email server setup.

---

### Post by NicoleM on 2007-03-26
> **arron said:**
> Be a true geek!  Run squirrelmail, your own web based email server, and host it on your own website.  I have run it for years, and i can still connect via imap server on my lan so i can use whatever email program to view the mail in the folders.  Add this with fetchmail and hotway its a total email server setup.


haha even if it was meant as a joke, it certainly sounds interesting (does that mean I'm a bigger geek than i thought?!)

i'm taking it one step at a time for now though! :)

---

