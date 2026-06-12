---
title: "Partitions, Partitions, Partitions...!"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by higherness on 2006-01-12
I'm not really a beginner, but I've got a question that should be in here, and others can use for future reference.

I've got a 40gb hard drive. I've got about 10-15gb of media that I desperately need to keep without damage. Right now my 40gb has 2 partitions:
-swap partition thing (500mb?)
-the rest of the hard drive

I've currently got 5.10 installed (a corrupt 5.10 in need of a fresh install, or kubuntu-the reason why I'm asking this question) and have a challenge;

I want to make a partition on my hard drive for media and storage (I'll say 30gb). I also want a partition to install the operating system in. Hypothetically, if I were to create another partition (30gb where I put files in) and I put my important (I'm stressing important ;) ) files in it and wanted to reinstall Ubuntu or Kubuntu in the smaller partition, would it affect the files in the 30gb partition?

Breakdown:

-40gb hard drive (38 )

3 partitions wanted:
-swap
-OS (8gb)
-storage (30gb)

Can I, after creating the partitions, put in my ubuntu cd and in the install menu choose to install it to the 8gb partition without affecting my files in the 30gb partition?

Thanks, 
Tom

---

### Post by paulmilliken on 2006-01-12
[QUOTE=higherness]
Can I, after creating the partitions, put in my ubuntu cd and in the install menu choose to install it to the 8gb partition without affecting my files in the 30gb partition?

Thanks, 
Tom[/QUOTE]
I haven't tried doing that with Ubuntu, but I have done a similar thing in the past with other distros without any problems.

Paul

---

### Post by jimrz on 2006-01-12
Looks as though that would work. However it looks as tough you are going to be really squeezed for hd space. Do you have an open bay for a 2nd drive, or another drive already available with additional space? With both / and /home on that 8Gb it will fill up pretty quickly.

EDIT:  Ooops...misread, thought you had 30Gb of important files you were concerned about. Sorry. Looks as though Sef (next relpy below) has the right ideas for you.

---

### Post by Sef on 2006-01-12
I would use Breezy Live CD and use GParted.  Applications ----> System Tools      ----> GParted.   Then I would create a /home directory to save those files.

Before doing any of that, **back up[B]** your 15 gb of files....Either on a few DVDs, or a external hard drive.

When doing a reinstall, manually partition the hard drive.  If your not sure how to do that, read this by Herman:

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

---

### Post by higherness on 2006-01-13
Thanks for all the help.

---

### Post by John C on 2006-01-13
[I]When doing a reinstall, manually partition the hard drive. If your not sure how to do that, read this by Herman:

[http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/) [/I]

Thanks for the link -- very useful.  I like the information on GAG.

---

### Post by cotcot on 2006-01-14
As said ina previous reply backup your veru important files anyway. Even after your new install you should have the backup.
I use partimage on a external HDD. I found out that i needed a live CD from Kanotix to have USB 2.0 supported.

---

