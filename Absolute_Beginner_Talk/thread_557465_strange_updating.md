---
title: "strange updating"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-09-22
usually after logging on i get updates popping up.

but lately this hasent happened, 2 days or so, maybe 3.

so i do

sudo apt-get upgrade

still nothing...hmmm

i try:

sudo apt-get update

then upgrade

and stuff appears!?!?

why do i have to update my sources list whenever i update now?

---

### Post by agurk on 2007-09-22
Hmm, I think you have it backwards, the procedure is:
sudo apt-get update (this reads the index of available packages, it does not install anything)
sudo apt-get upgrade (this installs any newer versions available, except for stuff like new kernels, you'll need sudo apt-get dist-upgrade for that)

---

### Post by skymera on 2007-09-25
i know!

i did sudo apt-get update
2 days before when i got new repos.

but no updates appeared for like 2 or 3 days.

unless i do apt-get update AGAIN

i been using ubntu for 6months, i know what im doing when it comes to apt-0get

this has just puzzled me

---

