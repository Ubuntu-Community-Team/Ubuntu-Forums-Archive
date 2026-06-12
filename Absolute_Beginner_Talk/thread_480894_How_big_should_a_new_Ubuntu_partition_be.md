---
title: "How big should a new Ubuntu partition be?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Randybob on 2007-06-21
If I get a new hard drive and install Ubuntu on it, what is the recommended size for Ubuntu's partition? I want to have something like my Windows setup, where I have one partition for the OS and programs, and the other for data. Or is there a better way to do this since Linux is involved? I could probably find the *absolute* minimum, but I'm looking for a realistic recommended size. Thanks.

---

### Post by Hobo Joe on 2007-06-21
Well, that all depends on what you want to run on it. I suppose it's possible to have it run on 1 GB, but that's completely impractical, as all you would be able to fit is the OS itself.

In the end, it's really all up to you. What do you plan on putting on it? Will it be mostly programs, or will you have lots of files.(Music videos etc.)

---

### Post by schwascore on 2007-06-21
Here is my current setup, which I have used for the past five years with great success.

Partition 1
Mount point: /
Size: at least 10 Gigs

Partition 2
Swap
SIze: 2 x your RAM, but not above 2 gigs (from my experience, others my disagree)

Partition 3
Mount Point: /home
Size: Everything else (lots of room!)

With this setup, I have plenty of room for the operating system on the root partition and a separate partition for all of my data and personal installs (Cedega/Wine video games, music, etc.)

I personally like this setup the best because should I ever break anything in Ubuntu with my constant tinkering, I can always just re-install to the root partition and all of my data and most importantly, my program preferences, etc. are saved on the home partition.

Just my $0.02

---

### Post by NeoLithium on 2007-06-21
Well, if you have a seperate partition for windows that has your files, you can access that from Ubuntu after you install.  The good bet is to have at least 2GB or better for your Ubuntu Partitions when all is said and done.  2x your RAM for swap isn't necessary anymore unless you have like 2GB of ram and edit videos for Paramount Pictures or something.

---

