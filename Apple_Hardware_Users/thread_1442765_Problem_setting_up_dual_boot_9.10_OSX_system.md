---
title: "Problem setting up dual boot 9.10 OSX system"
date: 2010-03-30
forum: Apple Hardware Users
---

### Post by kadymae on 2010-03-30
I have done this before [http://members.cox.net/kadymae/dualboot.html]("http://members.cox.net/kadymae/dualboot.html"), but these instructions date from 6.06 and no longer work with the different installer in 9.10

I have partitioned the disk into a 40 and 70 gig drive.  Mac OS X is on the 70 gig partition.  I want to put Xubuntu on the 40 gig partition.

Here's what I'm doing:

I get to a screen that tells me what partitions I have. 
I select the manual option.
I select the 40 gig partition and delete it.

*In theory I now have 40 gigs of free space.*
I click forward and it tells me it can't install because I have no boot, root, and swap partitions.

If I click the back button, I tells me that I have a 40 gig HFS partition and a 70 gig HFS partition.  

(In the 6.06 installer, as soon as I created free space and clicked auto partition option the installer automatically created root, boot and swap. Is there an auto partition option in the Xubuntu 9.10 installer, if so, where is it?)

I've tried searching the wiki, but all instructions I find are for dual booting Intel systems and using Bootcamp.  (This is a PPC system.  There is no bootcamp for PPC.)

How do I turn that 40 gig partition into free space which the Xubuntu installer will recognize?

Thank you.

---

### Post by linuxopjemac on 2010-03-30
Cannot you do it manually? You seem to know which kind of partitions you want to have ;)

---

### Post by Necrom@ncer on 2010-03-30
Heres what to do: Go to Diskutil, delete the 40GB HFS. Go back to the ubuntu installer, click use the largest free space. It will do it for you, boot swap yaboot whatever it works, thats how I setup dual boots with Leopard and 9.10 for people.

---

### Post by kadymae on 2010-03-31
> **linuxopjemac said:**
> Cannot you do it manually? You seem to know which kind of partitions you want to have ;)

I have only a vague idea of how to set this up manually.

---

### Post by kadymae on 2010-03-31
> **Necrom@ncer said:**
> Heres what to do: Go to Diskutil, delete the 40GB HFS. Go back to the ubuntu installer, click use the largest free space. It will do it for you, boot swap yaboot whatever it works, thats how I setup dual boots with Leopard and 9.10 for people.

When I open the disk utility it doesn't give me an option to delete the partition.  I can erase it, but that automatically reformats it to HFS+.

---

### Post by Neds Moar Salt on 2010-03-31
> **kadymae said:**
> I have done this before [http://members.cox.net/kadymae/dualboot.html]("http://members.cox.net/kadymae/dualboot.html"), but these instructions date from 6.06 and no longer work with the different installer in 9.10

I have partitioned the disk into a 40 and 70 gig drive.  Mac OS X is on the 70 gig partition.  I want to put Xubuntu on the 40 gig partition.

Here's what I'm doing:

I get to a screen that tells me what partitions I have. 
I select the manual option.
I select the 40 gig partition and delete it.

*In theory I now have 40 gigs of free space.*
I click forward and it tells me it can't install because I have no boot, root, and swap partitions.

If I click the back button, I tells me that I have a 40 gig HFS partition and a 70 gig HFS partition.  

(In the 6.06 installer, as soon as I created free space and clicked auto partition option the installer automatically created root, boot and swap. Is there an auto partition option in the Xubuntu 9.10 installer, if so, where is it?)

I've tried searching the wiki, but all instructions I find are for dual booting Intel systems and using Bootcamp.  (This is a PPC system.  There is no bootcamp for PPC.)

How do I turn that 40 gig partition into free space which the Xubuntu installer will recognize?

Thank you.

Delete your linux partition, but then create a ext3 partition with / as a mount point and a swap partition out of the free space that got created.

---

### Post by Necrom@ncer on 2010-03-31
What OS X version are y ou using? It sounds like Tiger from what u r saying,try booting into diskutil on your install disk and deleting from there, or boot into a leopard install disk, because that diskutil version is MUCH better. You could try command line as root or ipartition as well

---

### Post by kadymae on 2010-03-31
> **Necrom@ncer said:**
> What OS X version are y ou using? It sounds like Tiger from what u r saying,try booting into diskutil on your install disk and deleting from there, or boot into a leopard install disk, because that diskutil version is MUCH better. You could try command line as root or ipartition as well

I am using Tiger (don't have a Leopard disk that isn't intel only).  I'll try the trick with the install disk as well as iPartition, which I do have on another machine.*  

(Commandline ... I would rather not go there, but I will if all else fails. However, I have only pea-soup foggy idea of where to go and what to do and would have to have *excruciatingly detailed* instructions about what to type.)

Thanks!

*Anything above 10.4.8 is notoriously unstable on MDD PowerMacs, so I don't have 10.4.11 on it, which iPartition requires.

---

### Post by kadymae on 2010-03-31
> **Neds Moar Salt said:**
> Delete your linux partition, but then create a ext3 partition with / as a mount point and a swap partition out of the free space that got created.

What would I call the swap partition?

There is a drop down menu on the Xubuntu installer disk tool from which I have choices like: / and /boot

But there is nothing called /swap.

---

### Post by Necrom@ncer on 2010-03-31
Leopard runs fine on my MDD, and 10.4.11 ran fine when I had it, so no reason to not upgrade unless some other reason you may have? Also, another thing to do is: While in Live CD, go to terminal and type (as root) ```
apt-get install gparted
``` after install run gparted. You can delete the 40GB HFS+ from there, then go to installer and use largest free space.

---

### Post by kadymae on 2010-04-05
> **Necrom@ncer said:**
> Leopard runs fine on my MDD, and 10.4.11 ran fine when I had it, so no reason to not upgrade unless some other reason you may have? Also, another thing to do is: While in Live CD, go to terminal and type (as root) ```
apt-get install gparted
``` after install run gparted. You can delete the 40GB HFS+ from there, then go to installer and use largest free space.

I've had nothing but bad luck with 10.4.11 on my dual 867, but it turns out that GParted is already on the Xubuntu disk; I discovered it when I went to find the terminal.  

WooT!  My dual boot system is now installing a whole slew of updates.

Hands you your preferred drink.  Thank you.

----

[How to Set Up a Dual Xubuntu 9.10/ OS X (PPC) System]("http://kadymae.livejournal.com/1004977.html")

---

