---
title: "want to split an existing ntfs partition"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-12-26
I've just got a new HDD and I forgot to leave some space unpartitionated in order to install Ubuntu later on. Now I have a separated partition for Windows and others for holding movies, games etc. What I want to do is to split an existing NTFS partition in two so that I can split the newly resulted unpartitionated space into 2 (i think there were only two - swap and ext3 no?) partitions for installing Ubuntu. Is that possible? If yes, how?

Thanx in advance.

---

### Post by LaRoza on 2007-12-26
> **the_nomad said:**
> I've just got a new HDD and I forgot to leave some space unpartitionated in order to install Ubuntu later on. Now I have a separated partition for Windows and others for holding movies, games etc. What I want to do is to split an existing NTFS partition in two so that I can split the newly resulted unpartitionated space into 2 (i think there were only two - swap and ext3 no?) partitions for installing Ubuntu. Is that possible? If yes, how?

Thanx in advance.

You can shrink the NTFS partition and create a new one from the freed space.

You can only have four primary partitions, and Ubuntu uses two.

The Ubuntu install disk will allow you to do this, but the GParted Live CD is better in my opinion, see the link in my sig if you want it.

---

### Post by the_nomad on 2007-12-26
thanx for replying first,
second - how do i shrink the ntfs partition ?:-k

---

### Post by the_nomad on 2007-12-26
oups i havent seen the last row of the post sorry. thanx

---

### Post by LaRoza on 2007-12-26
> **the_nomad said:**
> thanx for replying first,
second - how do i shrink the ntfs partition ?:-k

With the GParted Live CD, you right click on it and shrink it. All GUI, very easy and powerful.

---

