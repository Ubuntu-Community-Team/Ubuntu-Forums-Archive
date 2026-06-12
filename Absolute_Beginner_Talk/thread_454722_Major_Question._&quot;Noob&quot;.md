---
title: "Major Question. &quot;Noob&quot;"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Usurshadow on 2007-05-25
I am currently on my new laptop which is fairly decent and it came with windows vista on it already "which sucks to all hell" and I want to install ubuntu on it and replace windows. Do I just reformat my computer and install ubuntu or do i just install ubuntu and have 2 operating systems on my laptop?

---

### Post by juxtaposed on 2007-05-25
You can have two operating systems (or more even).

You have to partition the file system (its like setting aside a certain ammount for each operating system).

It might be complicated for a new user, but there are many guides on how to dual boot windows and ubuntu on the internet.

---

### Post by starcraft.man on 2007-05-25
> **Usurshadow said:**
> I am currently on my new laptop which is fairly decent and it came with windows vista on it already "which sucks to all hell" and I want to install ubuntu on it and replace windows. Do I just reformat my computer and install ubuntu or do i just install ubuntu and have 2 operating systems on my laptop?

Uh, thats your choice... you can do both quite easily. If in the installer you tell it to use the entire disk, there goes your vista install. If you tell it to use the largest free space (if there is any, OEM computers usually partition up the whole drive with no free space) then it will dual boot. I prefer people to do a manual install if its a dual boot, I've heard enough "AHHHH (insert windows version) is GONE!!!!". 

[This red pill]("http://www.psychocats.net/ubuntu/installing") will lead you to a live install.

[This red pill]("http://users.bigpond.net.au/hermanzone/p2.htm") will lead you to a dual boot with a fat shared partition.

Your choice, choose wisely, once you have seen what is outside the Matrix, you may NEVER be reinserted again :p

Thats it I think, have fun and lets stamp out Vista use together, we can show MS we don't need em :D.

PS: I know, there are no blue pills in my scenario :p

---

### Post by Usurshadow on 2007-05-25
would it just be easier to have ubuntu the only operationg system and than install WINE on it for the windows programs i may be running?

---

### Post by starcraft.man on 2007-05-25
> **Usurshadow said:**
> would it just be easier to have ubuntu the only operationg system and than install WINE on it for the windows programs i may be running?

Neither WINE nor Cedega/CrossOver provide perfect emulation for all programs (especially newer ones). I would say, keep Vista on for gaming (can always find a copy of XP if you don't like Vista, I don't, there are free means to get a copy anyway >.> *coughs loudly* torrent). I'd suggest make a dual boot, the guide I gave ya is pretty well explained and easy, make sure to get the alternate disk off the main site to follow along.

---

### Post by Usurshadow on 2007-05-25
This install process is for a computer with 1 hard drive right? I am currently running only 1 hard drive at the moment.

---

### Post by starcraft.man on 2007-05-25
> **Usurshadow said:**
> This install process is for a computer with 1 hard drive right? I am currently running only 1 hard drive at the moment.

Yup, I'm pretty sure the second one is a dual boot on one drive (the top of the page links to elsewhere for a guide to two HDs). Just make sure when you get to the partitioner you have all the partitions on the same drive as windows. You may have to resize btw, I'm not sure. It depends on your partition set up.

Read [this about planning partitions]("http://www.psychocats.net/ubuntu/partitioning"). Should help. Make sure you think about what your doing twice before you push commit once a partition overwritten, its gone >.>. (I assume theres nothing important on the Vista partition anyway so no loss even if you mess up :p.

That should be it, good luck, I'm sure it will be fine. Don't hesitate to ask question if your worried :).

---

### Post by jerrylamos on 2007-05-25
How big is the hard drive?  For example, let's assume 40 GB.  One setup is to have two Linux's, one the current version that works, and one for a new version which you might be trying out.  Example I have a Edgy 6.10 and a Feisty 7.04.  As you might gather from scanning the forums sometimes Feisty runs great and sometimes it doesn't.

On CD Live you do System Administration Gparted.  If it's not on the CD, use Applications, Add/Remove, search for Gparted, mark for install, and apply.

With Gparted you could set up a 19 GB first partition file type ext3, a 1 GB swap file type swap, and an 20 GB partition for a second Linux file type ext3.  With dual boot you could select either Linux.  The one swap is used by whichever Linux is booted.

Then when you install Ubuntu use manual install so you can select which partition to use for mount point /

Cheers, Jerry

---

### Post by Inxsible on 2007-05-25
Have a look-see here to get an in depth understanding of partitions and installing 

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ramjet_1953 on 2007-05-25
Another option is to do what I did.

Buy a new hard drive and install Ubuntu onto that.

That way, you will not be tinkering with your Windows setup and if you discover Linux is not for you, you just plug-in your old drive.

Laptops usually just have a trap-door on the bottom and the hard drive is usually screwed into a small metal caddy, which then just plugs in. It is literally just a 2 minute job to switch hard drives.

After I completely converted to Ubuntu, I then bought one of those small USB boxes and put my old hard drive into it and now use Ghost for Linux (G4L) to clone my working drive to it for the ultimate backup.

Worth a thought, as hard drives are fairly cheap there days.

Regards,
Roger :cool:

---

### Post by nightfall_sgp on 2007-05-26
Hi.

I just installed Ubuntu onto my laptop too. It was running on XP pro. I simply clicked on installed and let Ubuntu installed to another partition. 

This allows me to have the ability to choose either to boot Ubuntu or WinXP Pro on startup.

Cheers!

---

### Post by Karl S. on 2007-05-26
> would it just be easier to have ubuntu the only operationg system and than install WINE on it for the windows programs i may be running?

I use VirtualBox to do that and like it a lot.

---

