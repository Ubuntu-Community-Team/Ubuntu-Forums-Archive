---
title: "Checking Hard drive"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Johnny3 on 2007-09-17
I there a way to check your hard drive for errors and bad spots? When I type in fsck it says  WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.
So I don't do it. I do type in sudo shutdown -F -r now and it runs at start up..But it is so fast I can't red it. Is there a way to pause it and then start it up again. Does sudo shutdown -F -r now do the same thing as fsck?
Thanks Johnny3 
Gainesville Fl

---

### Post by jw5801 on 2007-09-17
fsck will take a reasonable amount of time to run, so it's unlikely it is running on reboot. Try running it from the LiveCD with:```
sudo umount -a
sudo killall gnome-volume-manager #to prevent it being remounted
sudo fsck
```

---

### Post by Nessa on 2007-09-24
Is this the only way to check a hard drive? Is it norman for a 160Gb hard drive to show up only as 149GB?

---

### Post by hyper_ch on 2007-09-24
Yes it is.

---

### Post by jw5801 on 2007-09-24
There are quite a few different ways to check a drive. Most of them will wind up calling ex2fsck (for ext2 and ext3 anyway), which is what fsck calls.

It depends where it's showing up as 149GB. Type ```
sudo fdisk -l
```and see how big it says your drive is. If that returns the correct amount then there's nothing to worry about, it's just the other program reading the drive funny.

---

### Post by Nessa on 2007-09-24
It's a new drive. The 149GB was unallocated. 

I'm on WinXP right now running the Western Digital diagnostics tool. It sees the whole 160GB here. From what I've read fsck requires unmounting the drive right?

---

### Post by jw5801 on 2007-09-24
Definitely. What filesystem is on the drive? If it's ntfs then I don't believe fsck will be able to check it. Instead you can use the CHKDSK utility in Windows.

---

### Post by Nessa on 2007-09-24
How much noise is normal for a hard drive?

---

### Post by jw5801 on 2007-09-24
Noise? As in electromagnetic interference? Not very much... :p Sorry I immediately thought Signal-to-Noise ratio when I read that!
As for audible noise (sound), what sort of sound are you hearing that you think might be bad?

---

### Post by master_kernel on 2007-09-24
> **Nessa said:**
> Is this the only way to check a hard drive? Is it norman for a 160Gb hard drive to show up only as 149GB?
That seems about normal, maybe a couple gigabytes below average...

---

### Post by Nessa on 2007-09-24
Real noise... I can't explain it. It's not like the click of death. But... hmm... The side panel of my case is open right now. I'm not sure if it's normal. I don't want to say grinding noise but that's the closest I can describe it. It's a brand new seagate 160GB ide drive that I got just a few hours ago. Diagnostics tests say it's ok.

I will need to wipe out my older 80G GB drive which has Ubuntu. I've already cloned that onto the new seagate drive and boots up fine. Only that noise. I need the older drive for something that's why I have to wipe it clean. Is there anything more I should do?

---

### Post by psusi on 2007-09-24
Hard drive manufacturers lie about the size of their disks, which is why it is smaller than advertised.  They use powers of ten instead of powers of two ( i.e. to them a KB = 1000 bytes instead of 1024 ).  

You might want to run badblocks on the drive to test for physical defects, or install the smartmontools and use that to have the drive run its internal diagnostics.

---

### Post by hyper_ch on 2007-09-24
160 * 1000/1024 * 1000/1024 * 1000/1024 = 149 Gb

---

