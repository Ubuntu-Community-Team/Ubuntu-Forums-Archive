---
title: "Not Booting!"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by meep_meep on 2007-06-18
Hi guys,

I've only been using Ubuntu for a few days and this is my first post.

When I start my computer it will not boot.  I switch it on and it checks for a CD.

Then it checks to try and boot from a hard drive and it says that it can't!!

I am dual booting with windows.  I am currently running from Live-CD and I can access both my drives.

I think what I know what caused the problem.  I was looking at Gparted and and stupidly changed the flags on my drives and removed any flags I did have.....

anyway i have gparted open in Live-CD and I was wondering what flags I should put on my ntfs and ext3 partition?  Originally the only flag I had was on the ntfs partition and that was to 'boot'.

Thanks

meep

---

### Post by nitro_n2o on 2007-06-18
The NTFS partition where windows is must be bootable, as far as i remember there should be a star (*) next to the name

---

### Post by meep_meep on 2007-06-18
I was just wondering because shouldn't it boot into grub off the ext3 partition and not the ntfs one?

---

### Post by sessine on 2007-06-18
Your ext3 partition (I'm assuming you only have one) will also need to be bootable.  If you have more than 1 ext3 partition then the one that holds /boot is the one that needs to be bootable.

---

### Post by meep_meep on 2007-06-18
so should I mark under 'flags' for ntfs and ext3 'boot'?  

What do you guys with dual-boots have under flags in Gparted

---

### Post by dannyboy79 on 2007-06-18
> **sessine said:**
> Your ext3 partition (I'm assuming you only have one) will also need to be bootable.  If you have more than 1 ext3 partition then the one that holds /boot is the one that needs to be bootable.

AH, you can't have more than 1 bootable partition! It sounds to me like he needs to reinstall grub OR we need to know exactly what the error message is before suggested fixes.

---

### Post by sessine on 2007-06-18
> **dannyboy79 said:**
> AH, you can't have more than 1 bootable partition! It sounds to me like he needs to reinstall grub OR we need to know exactly what the error message is before suggested fixes.

His first post is quite clear, he has removed all flags from his patitions, therefore none of the partitions on his disk are bootable.  Also, if he can only have one bootable partition how do you propose he dual-boots, particularly when the ubuntu installer guided-resize option must put 2 bootable partitions on the same disk?

---

### Post by meep_meep on 2007-06-18
I was in Gparted on the live-CD and I only flagged my ext3 partition with 'boot' (no other flags) and it booted in grub fine!!!!!

Thanks for your help guys, tho I feel like I could have guessed this myself, sorry for wasting your time a little

meep

---

### Post by dannyboy79 on 2007-06-18
I am not going to argue with you. the boot flag is only used by the bios. which if he is dual-booting needs to be the drive that he installed Grub too, that is if he is using Grub as his boot loader. If you even try to set 2 partitions bootable, it won't even allow you to!!!!!! How the hell would the bios know which one to boot then????

BUt hey, If you know so much than you help him!!!

---

### Post by paradoc on 2007-06-18
Whoops!! meep-meep your first posting has a sting in its tail I think!
What the experts (not me, I'm only 'intermed') will want to see, if you find terminal (via accesories) i using a live CD..(check that your bios allows for CD first) is 
```
sudo fdisk -l (thats el)  
```
and ```
 gksudo gedit /etc/fstab
```

when you see the (to you) gobbledeygook,  copy and paste these two into Text editor, then post them in your next post.

This will give you the gen you need to get going again.........I hope;)

---

### Post by dannyboy79 on 2007-06-18
> **meep_meep said:**
> I was in Gparted on the live-CD and I only flagged my ext3 partition with 'boot' (no other flags) and it booted in grub fine!!!!!

Thanks for your help guys, tho I feel like I could have guessed this myself, sorry for wasting your time a little

meep

Very nice! I am glad I could attempt to help but as you found, you helped yourself first.

I would like to take this time to point out that you should NOT take the advice of just anyone without maybe confirming it with other user's posts first. Also, sometimes the Beans count can be some what of an indicator of how many posts the person has made. Now just because someones bean count is low, doesn't mean they don't know what they are talking about but it is something to keep in mind.

Glad you figured it out.

---

