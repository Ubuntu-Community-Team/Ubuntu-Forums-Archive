---
title: "Partition Trouble"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by CybaCowboy on 2006-05-13
I think I messed up my partitions!


When I was installing Ubuntu, I thought I'd be difficult and install *two* copies of it on different partitions, (I wanted to setup one with KDE manually, and one with GNOME), meaning that I'd essentially have *two* (slightly) different operating systems...

Suffice to say, it didn't work and now I have a spare partition that I don't think is being used for anything!


And here's where it gets sticky - I want to delete what I suspect is the spare partition, but GParted tells me that it is a locked partition, so I can't delete it!


It is the /dev/hda3 ("extended") partition I am referring to...

If I understand it all correctly, the /dev/hda5 ("linux-swap") partition is the swap file for Ubuntu, the /dev/hda2 ("ext3") partition is for Ubuntu itself, meaning that the /dev/hda3 ("extended") partition is the one I stuffed up, which is wasting space on my hard drive.


Take a look at the screen-shot and you'll see what I mean...

---

### Post by Sendervictorius on 2006-05-13
Did you use windows to set up the original partitions?

I did on my pc, and now I have partition tables that GParted can't change. Apparently, some versions of windows (win2k in my case) don't format partitions in a standard way, and GParted can't cope.

Anyway, you don't have to delete the partition. you can just create a new filesystem on the partition (use mkfs command), and mount it (add a line in the /etc/fstab file to make permanent), and you are away.

I would suggest you copy your current /home to this partition, then mount the new partition under /home. That way, it makes it easier to upgrade ubuntu to the next version.

---

### Post by RRS on 2006-05-13
It would appear that the swap partition is using all the space in hda3 so there isn't any actual waste.

To change partitions with gparted you need to run it from a live cd. The locks are because they're mounted when your system is booted.

Since hda1 is NTFS I'll assume you've installed as dual boot with Windows.

How big is your drive, it looks like about 60g is currently formatted, if that's the actual size then you'll have to reduce the size of hda1 and hda2 to form a fourth partition. Otherwise just use any remaining freespace.

---

### Post by CybaCowboy on 2006-05-13
Okay, I'm confused!:confused:


Is it *safe* to delete the /dev/hda3 ("extended") partition and if so, I *should* be able to do this with the live CD, right?


[i]Edit:
When I used GParted with the live CD, I could see and manage the /dev/hda2 ("ext3") partition, but not the other two.

For clarification, what I want to do is get rid of the /dev/hda3 ("extended") partition, assuming it's not actually required by Ubuntu...

It is my understanding that Ubuntu only requires the /dev/hda2 ("ext3") and /dev/hda5 ("linux-swap") partitions, which is why I want to delete the /dev/hda3 ("extended") partition and make it free space (well, merge it with Ubuntu's storage space) so that's it's not sitting there useless.[/i]

---

### Post by RRS on 2006-05-13
I think yes, it should be "safe" to delete hda3 but if you have less then 512m RAM you may notice some slowdown without the swap partition.

However, if I'm reading your gparted screen correctly this will only gain you 1192mb of space, not enough for another OS.

I can't remember if gparted is on the Breezy live cd. If not it's available as a stand alone live cd (sorry don't have a link handy).

I've used the partitioning tool in the Breezy installation cd, simply exit after going thru the "manually partition" section rather then completing the installation.

BTW, have you considered simply adding KDE to you're system rather then a complete additional installation? I've seen instructions for doing these elsewhere in the forums. Seems this would allow you to choose between Gnome and KDE during log in to decide which you prefer without having to install an entire extra system.

I hope I've decreased rather then increased your confusion.

---

### Post by CybaCowboy on 2006-05-13
[QUOTE=RRS]I think yes, it should be "safe" to delete hda3 but if you have less then 512m RAM you may notice some slowdown without the swap partition.

However, if I'm reading your gparted screen correctly this will only gain you 1192mb of space, not enough for another OS.[/QUOTE]

Isn't */dev/hda5 ("linux-swap")* Ubuntu's swap partition, *not* the /dev/hda3 ("extended") partition?


[QUOTE=RRS]However, if I'm reading your gparted screen correctly this will only gain you 1192mb of space, not enough for another OS.[/QUOTE]

I don't *want* to install another operating system, just free that space for storage use.

It is my understanding that the /dev/hda3 ("entended") partition is not actually being used for anything, and certainly not for Ubuntu's swap file, so I want to free this space up and use it for storage...

Of course, if I'm wrong about its use, feel free to correct me someone.


[QUOTE=RRS]BTW, have you considered simply adding KDE to you're system rather then a complete additional installation? I've seen instructions for doing these elsewhere in the forums. Seems this would allow you to choose between Gnome and KDE during log in to decide which you prefer without having to install an entire extra system.[/QUOTE]

That's what I did just recently, but doing so littered GNOME's menus and interface with KDE programs and components...

The idea of having Ubuntu installed on two different partitions, as two different operating systems, was that each desktop environment's programs and components would remain completely independant of the other.

---

### Post by RRS on 2006-05-13
> It is my understanding that the /dev/hda3 ("entended") partition is not actually being used for anything, and certainly not for Ubuntu's swap file, .......

Unless I'm misreading your screenshot (quite possible) it appears that /dev/hda5 is contained in /dev/hda3. **IF** this is correct then deleting /dev/hda3 would also delete /dev/hda5 and you would need to create a new swap partition, thus no gain in space.

Normally only 4(?) primary partitions are allowed on a drive, creating one as "extended" allows you to create additional partitions inside it if more then 4 are needed.

> The idea of having Ubuntu installed on two different partitions, as two different operating systems, was that each desktop environment's programs and components would remain completely independant of the other.

That makes sense, understand now.

Please keep in mind that I've only been using Ubuntu for a few months myself so if I seem a little vaque it's because I don't want to provide directions that could be incorrect.

I'll be offline soon but'll check back in a few hrs. Hopefully in that time someone with a little more expertise can shed light on our confusion and suggest a solution for you.

---

### Post by CybaCowboy on 2006-05-13
I think I'm more confused than ever now (partitioning *really* isn't my specialty)!:confused: 


When I first installed Ubuntu, I had one partition for Windows XP and two for Ubuntu; this time 'round, I have one for Window XP and *three* for Ubuntu!


Anyway, lets make this dead simple - am I *really* losing out by having this third partition, or am I gaining something and just being paranoid?

---

### Post by pommattski on 2006-05-13
... it looks as though RRS has got it pretty well covered...

From the screenshot:
/dev/hda1 is a Primary partition; presumably with Windows installed as it is ntfs
/dev/hda2 is the Primary partition that Ubuntu is installed on.
/dev/hda3 is an Extended partition.  This can hold many Logical partitions.
  /dev/hda5 is a logical partition within the Extended Partition formatted as linux-swap.
(FYI, if you had another Primary partition, it would be labelled hda4)

The "pad-locks" do mean they are locked; this is because they are in use.

I hope this clarifies things a little more for you.

Edit:
No. You're not losing out by having the partitions arranged like this.  There are many ways to skin a cat, as some say.  You probably just had the swap partition as a third Primary partition originally.

---

### Post by CybaCowboy on 2006-05-13
[QUOTE=pommattski]... it looks as though RRS has got it pretty well covered...

From the screenshot:
/dev/hda1 is a Primary partition; presumably with Windows installed as it is ntfs
/dev/hda2 is the Primary partition that Ubuntu is installed on.
/dev/hda3 is an Extended partition.  This can hold many Logical partitions.
  /dev/hda5 is a logical partition within the Extended Partition formatted as linux-swap.
(FYI, if you had another Primary partition, it would be labelled hda4)

The "pad-locks" do mean they are locked; this is because they are in use.

I hope this clarifies things a little more for you.

Edit:
No. You're not losing out by having the partitions arranged like this.  There are many ways to skin a cat, as some say.  You probably just had the swap partition as a third Primary partition originally.[/QUOTE]

I understand... Sort of.


Thanks.

---

### Post by catlett on 2006-05-13
/dev/hda3 and /dev/hda5 are the same thing. When you make an extended partition it will be a partition (/dev/hda3). You can make  partitions inside of the extended partition. Which is what /dev/hda5 is. Your getting confused because you only have one partition inside of the extended partition. It is easier to understand if there were more partitions inside of dev/hda3.
Anyways, DO NOT DELETE ANYTHING. YOU DO NOT HAVE WASTED SPACE.
Right now you have the correct setup for a dual boot.
hda1 is windows
hda2 is ubuntu
hda3 is the extended partition
hda5 is ubuntu's swap which takes up all of hda3

UNLESS THERE IS ANOTHER PARTITION THAT IS NOT SHOWING UP FOR SOME REASON, DON'T DELETE ANYTHING. Your setup is fine.
Only change this if you are an experienced user and you want to rearrange your partitioin structure. To be technical the swap doesn't have to be an extended partition but it doesn't really matter a whole lot. There are certain setups that can increase the efficiency of the system, but if you just want a partitioning scheme that works, yours is fine.

---

### Post by CybaCowboy on 2006-05-13
Oh, okay.

That makes it clearer...


This is gonna be fun when I finish setting up my computer (I want Windows XP: Professional, SUSE Linux, Ubuntun Linux, eComStation and possibly FreeBSD all installed on my machine)...

A partition nightmare!

lol


Thank you peoples!

---

