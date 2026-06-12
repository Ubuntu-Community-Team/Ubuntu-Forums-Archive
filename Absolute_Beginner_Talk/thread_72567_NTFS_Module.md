---
title: "NTFS Module"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by likedude15 on 2005-10-06
I tried running the ntfs.ko module file to recognize my ntfs parition but i got access denied...any suggestions?  sorry for being so needy.


chris
[email]tjno1son@gmail.com[/email]

---

### Post by Ampersand on 2005-10-06
you should be able to mount it using the mount command. In a terminal, type 'sudo mount -t ntfs [partition name] [target]'. Replace [partition name] with the location of your windows partition (often /dev/hda1, reply if you need to know how to find it). Replace [target] with the directory you wish to mount the drive to. You will have to use 'sudo mkdir' to create this directory.

---

### Post by likedude15 on 2005-10-07
alright i created it,:)  my hard drive contents do not show up and i am not able to write to it:-| any ideas....?

chris 

[email]tjno1son@gmail.com[/email]

---

### Post by patrick295767 on 2005-10-07
paragon ntfs for linux (to write)

i havent tried yet but looks promising !

---

### Post by likedude15 on 2005-10-07
thanx!:) try it when it get home....cant do anything at school!

---

### Post by KingBahamut on 2005-10-07
Patrick and likedude, Ive had limited success with paragon in the way of writing. I would warn you to be sure you have everything backed up safely before you procede with it. 

I messed one up pretty bad enough to force to rebuild the maintenance parition in a hex editor (took a week).......=(

---

### Post by patrick295767 on 2005-10-07
[QUOTE=KingBahamut]Patrick and likedude, Ive had limited success with paragon in the way of writing. I would warn you to be sure you have everything backed up safely before you procede with it. 

I messed one up pretty bad enough to force to rebuild the maintenance parition in a hex editor (took a week).......=([/QUOTE]


Thank you for ur advices !! 

Not much folk talk about paragon 
It was damn case for Captive NTFS for linux which is very unsecure !
  
On the web-site, they mention it's rather stable... 
Maybe a survey concerning paragon would be worth ... 
Is there some people happy of their Paragon NTFS for Linux ?

I wish as lot of people writing in my Ntfs partitions ... (anyhow, vmware is also another solution but that's sthg else)

More information concerning Paragon are damn well welcome by the Linux community !!

Thank you 

Pat'

---

### Post by likedude15 on 2005-10-07
Like partick said thankx:)  for warning me, i want to write to my ntfs parition becuause i want to save my settings while in live without going through installation everytime i boot up. i guess ill research a way to do this.  :rolleyes: Oh well im on the interent tonight, oh darn!:rolleyes:

---

