---
title: "ext3 automount disk"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-10-11
Howdy,

Quick question, I have looked everywhere on this, tried many things but getting my <internal> 80gig maxtor etx3 format to auto mount has been so far impossible. Plus some other answers seem to pick up from those who were already past some steps leaving me lost. What I need to do here is this...

I have an extra <internal> drive just for storage as ext3, I want to auto mount this drive so I don't have to keep mounting it due to my backup program and constant use. If I happen to forget to mount it, my auto backup can't access it due to needing my password. 

In Gparted it's hdb1. I have tried to edit in a terminal using gparted then the /media/hdb1 ext3 etc..etc... but I have no option to save this after changing it. So perhaps someone could walk through some steps with me so I may get this done. 

Thanks,

Paul

---

### Post by dcstar on 2007-10-11
> **gimpguy2000 said:**
> Howdy,

Quick question, I have looked everywhere on this, tried many things but getting my <internal> 80gig maxtor etx3 format to auto mount has been so far impossible. Plus some other answers seem to pick up from those who were already past some steps leaving me lost. What I need to do here is this...

I have an extra <internal> drive just for storage as ext3, I want to auto mount this drive so I don't have to keep mounting it due to my backup program and constant use. If I happen to forget to mount it, my auto backup can't access it due to needing my password. 

In Gparted it's hdb1. I have tried to edit in a terminal using gparted then the /media/hdb1 ext3 etc..etc... but I have no option to save this after changing it. So perhaps someone could walk through some steps with me so I may get this done. 

Thanks,

Paul

Install the** pysdm** package, that will give you a GUI tool to have partitions automatically mounted (System-Storage Device Manager) as it will modify your /etc/fstab file for you.

---

### Post by gimpguy2000 on 2007-10-11
> **dcstar said:**
> Install the** pysdm** package, that will give you a GUI tool to have partitions automatically mounted (System-Storage Device Manager) as it will modify your /etc/fstab file for you.

Thanks, I'll give er a go and report back. 

Paul

---

### Post by gimpguy2000 on 2007-10-11
Hey! Thanks! That works wonders! I booted up and there it was. It doesn't get any easier to use, that's for sure. Appreciate the help. :) 

One happy camper:guitar:

Paul

---

