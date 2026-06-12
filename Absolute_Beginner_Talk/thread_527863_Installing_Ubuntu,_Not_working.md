---
title: "Installing Ubuntu, Not working"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by RENEVEAH on 2007-08-17
I get so far then I get No root file system is defined., Where the heck do I fix this? I am trying to partition my 2nd drive for this with the feature this thing has but NOTHING i try rids that message

---

### Post by Jimmyfj on 2007-08-17
Are you trying to partition the drive from the Live Cd or through Gparted?

---

### Post by eye208 on 2007-08-17
> **RENEVEAH said:**
> I get so far then I get No root file system is defined.
What does "so far" mean? Sorry but you have to be more specific unless you want to keep us guessing. When do you get the error message? Are you using the Live CD install or the text based one? Are you using the latest version (7.04)? Ubuntu or Kubuntu? What are the specs of your system?

---

### Post by funpop on 2007-08-17
sounds like a problem with partitioning:

you need to specify mountpoints for your partitions:

 "/" as your root partition (5-10 gigs)
"/home" for you personal data (everything left on your hd)
"/swap" (at least the size of your ram)

---

