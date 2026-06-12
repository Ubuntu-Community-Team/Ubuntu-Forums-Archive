---
title: "Switching to Ubuntu"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by spacegypsy on 2006-10-02
First of all, helo to everybody of this forum.

I have a dual boot laptop with XP and SuSE 10.0 on it, and I want to try another distro. Don't misunderstand me I liked SuSE 10.0 (my first encounter with linux) and it was a good distro for me to learn a bit of linux.
So I downloaded Ubuntu 6.06 to see if... you know.
My Question are;
How do I change my machine from XP/SuSE to XP/Ubuntu?
Is there a special procedure to follow or do I just install it from the CD I downloaded?

thx

---

### Post by nalmeth on 2006-10-02
If you want to get rid of Suse, you can manually edit the partitions in the installer, just format it's ext3 and swap. 

1 question, do you have multiple HD's? The liveCD installer in dapper has been known to have problems with multiple HD setups.

---

### Post by spacegypsy on 2006-10-02
No multiple HD, just 3 partitions; windows C:\ and D:\ and one for Linux /

---

### Post by bulldog on 2006-10-02
> **nalmeth said:**
> If you want to get rid of Suse, you can manually edit the partitions in the installer, just format it's ext3 and swap. 

1 question, do you have multiple HD's? The liveCD installer in dapper has been known to have problems with multiple HD setups.

Two HD's in a laptop are not very common though.

I have a desktop with two hdd's and if you're a little handy with GRUB and the BIOS,there's no prob what so ever.

Did even an install with 4 hdd's and it was a little fiddling but if you make a list of your drives and keep it handy,no problems there.

Think the problems which are encountered had to do with the fact that GRUB installs on the first boot device by default.

This can easely be corrected.

---

