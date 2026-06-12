---
title: "I cant see my Partition!!!"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-06-27
I'm a linux newbie and just installed kubuntu 6.06, before installation I made 3 primary partitions on my HDD:

10Gig System files
48Gig My files
15Gig Swap

Anyways, I have been searching for quite awhile now and cannot seem to navigate to my 48Gig partition in order to begain creating the directories I need, could someone please tell me what im missing...

Thanks

---

### Post by deanjm1963 on 2006-06-27
when you made the partitions, did you do it with Kubuntu or some other partitioning software?

10gig for root is more than sufficient, but 15gig for swap is overkill, how much ram do you have? my 80did hard drive is 8gig root, 71gig home and 1gig swap.

edit: as your question about "my files" partition, its a folder called "home", and your files should go into a folder within that e.g. mine is /home/dean. There are no seperate drives like windows, e.g. C:, D:, E: etc, everything, including a separate partition is a "file/folder" located within " / " ... took me a while to get used to it...

---

### Post by charles.g.moore on 2006-06-27
I originally did the system partition and the swap during the install, the "home" was done using  qtparted with the slack left over.  

Is the swap thing a big deal?  

Do you think it would be a good idea to change the size? 

Can I even do that with qtparted?

---

### Post by deanjm1963 on 2006-06-27
that's a tough one to decide upon, if it were me I'd do a reinstall and repartition within the installer. Unless you've only got a small amount of ram, it's seldom used (in my case, might not be others), and when it has been its only been 1-15mb. The system "swaps" whats into memory to hard drive space allocated to "swap" when real memory is running low, if you've got 512mb-1gb ram, 1gb swap is more than enough.

---

### Post by charles.g.moore on 2006-06-27
[QUOTE=deanjm1963]when you made the partitions, did you do it with Kubuntu or some other partitioning software?

10gig for root is more than sufficient, but 15gig for swap is overkill, how much ram do you have? my 80did hard drive is 8gig root, 71gig home and 1gig swap.

edit: as your question about "my files" partition, its a folder called "home", and your files should go into a folder within that e.g. mine is /home/dean. There are no seperate drives like windows, e.g. C:, D:, E: etc, everything, including a separate partition is a "file/folder" located within " / " ... took me a while to get used to it...[/QUOTE]


Do you know the man command to find the size of my "home" file?  So that I can make sure Im saving into the right one, or am i still stuck in the windows frame of mind?

How did it know to create that home directory for me in another partition?

---

### Post by deanjm1963 on 2006-06-27
open a terminal and type df -T -h and that will tell you the name and size of your partition, you'll see a few others there, but they're system created on boot.

> How did it know to create that home directory for me in another partition?

you said that you made a 48gb "my files" which I assume is your home partition.

As for saving stuff to the right folder, linux won't let you save stuff outside of your home folder unless you have permissions for other partitions/folders. It's not like windows where it will let you save anything anywhere, that's whats so great about linux, it protects your system from just about anything.

---

### Post by charles.g.moore on 2006-06-27
[QUOTE=deanjm1963]open a terminal and type df -T -h and that will tell you the name and size of your partition, you'll see a few others there, but they're system created on boot.



you said that you made a 48gb "my files" which I assume is your home partition.

As for saving stuff to the right folder, linux won't let you save stuff outside of your home folder unless you have permissions for other partitions/folders. It's not like windows where it will let you save anything anywhere, that's whats so great about linux, it protects your system from just about anything.[/QUOTE]



Here is the dump
ilesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3    9.7G  2.1G  7.1G  23% /
varrun       tmpfs    506M   80K  506M   1% /var/run
varlock      tmpfs    506M  4.0K  506M   1% /var/lock
udev         tmpfs    506M  124K  506M   1% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   19M  488M   4% /lib/modules/2.6.15-25-386/volatile

It is'nt showing the other partition is it because it is a primary partition???

Oh and the swap is actually 1004Mb...Doh!!!

---

### Post by deanjm1963 on 2006-06-27
What's happened is you haven't made a home partition at all, you only have the root " / " partition with a home folder within that.

e.g. /dev/hda1 = root    /dev/hda2 = home     /dev/hda3 = swap

you should have a seperate entry for your home partition e.g. (mine)
> /dev/hda2      ext3     67G  9.2G   57G  14% /home

did you use the live/install cd or the alternate-text mode cd? I had nothing but partitioning problems with the live/install cd.

---

### Post by charles.g.moore on 2006-06-27
[QUOTE=deanjm1963]What's happened is you haven't made a home partition at all, you only have the root " / " partition with a home folder within that.

e.g. /dev/hda1 = root    /dev/hda2 = home     /dev/hda3 = swap

you should have a seperate entry for your home partition e.g. (mine)


did you use the live/install cd or the alternate-text mode cd? I had nothing but partitioning problems with the live/install cd.[/QUOTE]


I used the Live text mode CD, I think I'm going to start all over

Should I just use Fdisk next time and set all of the partitions up first?
12 Gig partition 1
1Gig Swap
the Rest as partition 2
Each one being a primary partition?

Then just install into them?
Do you know of a link somewhere that can walk me thru it step by step?
I just want to make sure that my sys files are isolated.
Am i still in that MS state of mind?

---

### Post by deanjm1963 on 2006-06-27
my 80gb hard drive is as follows

8gb for root /
71gb for /home
1gb for swap

it doesn't matter whether they're primary partitions or secondary, the only difference is after the root " / " partition e.g. hda1, other user made "home, swap, etc" start at hda5 - onwards when they're secondary partitions.

I'd be inclined to put the swap at the end your disk as its seldom used.

Use the software on the live/install cd to set up your disks, you can "pre-partition" if you like, but you need to set the partitions as linux partitions, etc, format them as ext3 or reiserFS, etc. too much hassle to do it manually

Your system files will be isolated in " / " ... that's where the system goes, everything else should go into /home. That still applies if you just have one big " / " partition + swap, the home folder created is still where you save your files, etc, and the rest of the system is "read only" ... again, unlike windows where everything is up for grabs, you can only work within /home.

---

