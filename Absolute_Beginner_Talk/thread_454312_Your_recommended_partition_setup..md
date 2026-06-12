---
title: "Your recommended partition setup."
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-25
Swap + Linux EXT3? Swap + Root + Linux EXT3? What is it?

If I go the route with having root on a separate partition, how much space should I allocate to the root partition?

I'm running into this problem. I was going to just set it up with swap + ext3. But when I try to mount ext3 as root at the installer screen, it automatically changes the partition... changing the ext3 partition and giving 4gb as root and the remainder as unallocated.

With Fiesty am I unable to mount my main partition as root??

---

### Post by Inxsible on 2007-05-25
> **Roasted said:**
> Swap + Linux EXT3? Swap + Root + Linux EXT3? What is it?
 
If I go the route with having root on a separate partition, how much space should I allocate to the root partition?
 
I'm running into this problem. I was going to just set it up with swap + ext3. But when I try to mount ext3 as root at the installer screen, it automatically changes the partition... changing the ext3 partition and giving 4gb as root and the remainder as unallocated.
 
With Fiesty am I unable to mount my main partition as root??
 
I would recommend the following partitions:
/ (root) ~ 10GB
/home ~ 20 GB
swap ~ 1GB
 
Additional partitions that I have 
/shared ~ 70 GB (this is where I have my music, movies and pictures, which I have mounted in Vista so I can access them from both OS'es)

---

### Post by aeiah on 2007-05-25
id go with roughly the same as the poster above. the root and home partitions being ext3. your swap should be twice the size of your ram, although i have 2GB ram so i just use a 2GB swap.

i have them in the order:

/ -18gb
swap -2gb
/home -20gb
/media/fat -the rest (for a shared partition)

---

### Post by Inxsible on 2007-05-25
I have 2GB of RAM too. Its a general consensus that the swap size should be 1.5 to 2 times that of your RAM.
 
But over the last few months that I am using Ubuntu, I used the system monitors to track the usage of Swap. What I found in my experience (atleast for my usage) is that my Swap even though only 1GB hardly gets used. I have never seen Swap used more than 7%.
 
So I think that works for me !!
 
But if you do use a lot of memory intensive apps at the same time, things would definitely be different for you !

---

### Post by Nythain on 2007-05-25
my current get up
/boot - ext2 100meg
/swap - swap 2gb
/ - ext3 rest of hard drive 1
/data - ext3 all of hard drive two

i prefer not to have a separate partition for /home because i have no need to save the file's contained there in... and chances are, if i have to reformat its because something in that folder is jacked so it gets reformated every time anyways

---

### Post by vanadium on 2007-05-25
I also recommend for desktop systems just the simple approach of one root partition besides the swap. USB drives are cheap these days, so it is easy to backup user data, or the entire home directory altogether.

---

### Post by bmeyer on 2007-05-25
> **Roasted said:**
> Swap + Linux EXT3? Swap + Root + Linux EXT3? What is it?

If I go the route with having root on a separate partition, how much space should I allocate to the root partition?

I'm running into this problem. I was going to just set it up with swap + ext3. But when I try to mount ext3 as root at the installer screen, it automatically changes the partition... changing the ext3 partition and giving 4gb as root and the remainder as unallocated.

With Fiesty am I unable to mount my main partition as root??

My best advice is, if you have enough room, use around 2 times as much RAM for your swap (ex: 1gig ram, 2gig swap).  I'll then usually use 10-15gb for / and the rest for /home.
So, using an 80gig with 1gig ram as an example, I'd go this route:
2gig swap
10gig / (ext3)
68gig /home (ext3)

Make sure all are primary partitions.  Doing it in that order (swap, /, /home) seems to work well, leaving all the remainder for /home.

---

### Post by Roasted on 2007-05-25
Figure this one out guys.

Few questions here.

1 - When using Gparted, why is it whenever I apply the changes and try to create the new partitions, ALL volumes try to mount. You can't work on a drive with active mounts. So why is Gparted trying to mount these volumes as I apply new partitions to the hard drive?

2 - Why is it that with the installer, I had the following partitions. 25gb NTFS, 2gb SWAP, 200gb EXT3 (rest). I tried to set the EXT3 partition as Root. However, when I set it as root, it split up the 200gb EXT3 partition. It split it into 4gb mounted as root, and the remaining 196gb as unallocated for. WTF?!

---

### Post by Roasted on 2007-05-26
Just to clarify something... technically I won't work out of my "home" directory, because "home" would be located on my /root directory. Essentially, since I keep all of my music and videos and pictures in 1 directory (previously, my home directory), this time around I'd be keeping all of that stuff on media/sda4. Sda4 is the main bulk partition I created to house all of my personal files.

Therefore, media/sda4 is my new "home" (per se) partition. Whereas the original home folder is located on the root directory, which has a limitation of 10gb. Correct? Is my thinking right on this? So I just need to keep in mind when I want to open my home directory, go for sda4 instead. Ehh? But then that pisses me off... cause I used to LOVE to hit F9 to open my home folder. Now what can I do is all of my stuff is in sda4?

---

### Post by drowner on 2007-05-26
> **Roasted said:**
> Just to clarify something... technically I won't work out of my "home" directory, because "home" would be located on my /root directory. Essentially, since I keep all of my music and videos and pictures in 1 directory (previously, my home directory), this time around I'd be keeping all of that stuff on media/sda4. Sda4 is the main bulk partition I created to house all of my personal files.

Therefore, media/sda4 is my new "home" (per se) partition. Whereas the original home folder is located on the root directory, which has a limitation of 10gb. Correct? Is my thinking right on this? So I just need to keep in mind when I want to open my home directory, go for sda4 instead. Ehh? But then that pisses me off... cause I used to LOVE to hit F9 to open my home folder. Now what can I do is all of my stuff is in sda4?

No no no

If you have your home on a separate partition, all that will happen is that sda4 will be mounted as /home

so when you press F9 your home folder, on sda4 will open.

---

### Post by Roasted on 2007-05-26
All I really did was throw root on a 10 gig partition, swap on another, and the remainder as /ext3. I didn't specify anything as home. :(

---

