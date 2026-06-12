---
title: "How much disk space..."
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by MoLeak on 2005-10-04
...does an install of Ubuntu require?  I have a "play" drive (4 gig) I use to try to understand Linux and had no problems installing other iterations of Linux.  I seem to be running out of disk space even thought the disk is formatted clean prior to the install.
Does Ubuntu need more than a gig to install?  Maybe I need a link to how to install this puppy because I've never had trouble installing anything before.

-MoLeak

---

### Post by Ampersand on 2005-10-04
4Gb is probably just about large enough. Do you have a seperate home partition?

If you find that you're running out of disk space, try running 'sudo apt-get clean' from a terminal to remove the .deb files that have been installed.

---

### Post by SilentCacophony on 2005-10-04
Hello. I currently have the full Breezy Preview release with extra packages installed, and mine is well less than 4 GB. I also have a minimal ubuntu 'server' install with a lightwieght windowmanager and some extra pakages installed that is less than a gig.

```
brian@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             4.9G  2.4G  2.3G  51% /  <- Ubuntu (Breezy)
tmpfs                 221M     0  221M   0% /dev/shm
tmpfs                 221M   13M  209M   6% /lib/modules/2.6.12-8-686/volatile
/dev/hda1             2.4G  588M  1.9G  25% /media/hda1
/dev/hda2             3.0G  890M  1.9G  32% /media/hda2  <- Ubuntu (server)
/dev/hda5             3.9G  285M  3.4G   8% /media/hda5
/dev/hda6             3.9G   65M  3.7G   2% /media/hda6
/dev/hdb1             9.6G  3.5G  6.2G  36% /media/share

```

---

### Post by az on 2005-10-04
[QUOTE=MoLeak].
Does Ubuntu need more than a gig to install?  Maybe I need a link to how to install this puppy because I've never had trouble installing anything before.
-MoLeak[/QUOTE]
Are you onlyusing a small portion of your drive?
The base system (server - no Graphical interface) requires 350 megs of space.  The full desktop requires 1.8 gigs of space (plus swap and filesystem data = 2.1 Gigs or so)
So, if you use the whole 4 Gig space, you should be fine.  Tell the installer to use the whole drive and do all the partitoining itself (guided partitioning)  It will make the root and swap partitions for you on the drive you select.

---

### Post by MoLeak on 2005-10-04
[QUOTE=azz]Are you onlyusing a small portion of your drive?
The base system (server - no Graphical interface) requires 350 megs of space.  The full desktop requires 1.8 gigs of space (plus swap and filesystem data = 2.1 Gigs or so)
So, if you use the whole 4 Gig space, you should be fine.  Tell the installer to use the whole drive and do all the partitoining itself (guided partitioning)  It will make the root and swap partitions for you on the drive you select.[/QUOTE]
The drive is my test drive.  It can use as much as it needs to get this installed and I want the graphical interface.  I am a Linux Noob to the nth degree and I know by saying that, my support level drops off but don't run out on me yet.  I'm a quick study and pretty familer with DOS. ;-)  I'll look at the documentation and try this again.  

-MoLeak

---

### Post by Mustard on 2005-10-04
I've had Ubuntu running on my daughters 3 GB drive, just fine.

---

### Post by MoLeak on 2005-10-08
[QUOTE=Mustard]I've had Ubuntu running on my daughters 3 GB drive, just fine.[/QUOTE]

Amazing.  I've tried so many times I almost turned this 4 gig into a frisbee.  I mean it would go along like it was going to make it then all of a sudden I get that stupid red screen.  I've downloaded it twice and burned it at the slowest speed.  I wonder if the distro has a crappy copy?

-MoLeak

---

### Post by az on 2005-10-08
What is written on the red screen?

---

### Post by N17R0 on 2005-10-11
[QUOTE=MoLeak]Amazing.  I've tried so many times I almost turned this 4 gig into a frisbee.  I mean it would go along like it was going to make it then all of a sudden I get that stupid red screen.  I've downloaded it twice and burned it at the slowest speed.  I wonder if the distro has a crappy copy?

-MoLeak[/QUOTE]

Hi I have seen that red-screen also, the problem was my DVD-ROM device could not read my CD-RW media which I burned ubuntu on, so I put the CD-RW into my CD-ROM writer device, and then it finally worked.
I don't know if you burned ubuntu to a CD-RW or a CD-R media, but I have more problems with CD-RW media not being read, then with normal CD-R media.

So u can try another brand CD-R media, and/or try a other CD-ROM device. 

Hope this helps you.

---

### Post by MoLeak on 2005-10-13
[QUOTE=N17R0]Hi I have seen that red-screen also, the problem was my DVD-ROM device could not read my CD-RW media which I burned ubuntu on, so I put the CD-RW into my CD-ROM writer device, and then it finally worked.
I don't know if you burned ubuntu to a CD-RW or a CD-R media, but I have more problems with CD-RW media not being read, then with normal CD-R media.

So u can try another brand CD-R media, and/or try a other CD-ROM device. 

Hope this helps you.[/QUOTE]

I'll give that a try.  I'm finding out it isnt' a space problem because I tried install on one of my laptops and got the same errors.  I have to say this is really wierd. 

-MoLeak

---

### Post by MoLeak on 2005-10-13
WooHoo.  I'm installed!!!  It failed so many times in the past that when it finally finished, I thought I was dreaming.  What I had to do was switch from my DVD burner to my standard CD burner to get a good install disk.

Now I need to get my wireless to the network.  I'm a noob and if anyone has any ideas, holla.  Thanx N17R0.

-MoLeak

---

