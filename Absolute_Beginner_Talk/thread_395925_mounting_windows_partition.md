---
title: "mounting windows partition"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by shantz24 on 2007-03-28
after looking over these forums i still cannot find an answer.  i have ubuntu installed as a dual boot with xp.  xp is on hda1 and "/" is on hda5 and /home on hda6.  i have found many guides to mount the windows partition but none of them work for me.  the one i found from ubuntu.com says there should be "disks" in Stystem, Adminstration, but there isnt.  i also tried [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) because i seen the link in another post.  but when i try to follow these steps i see hda1 when i run "sudo fdisk -l" but when i run "sudo nano /etc/fstab" to edit it, hda1 is not listed.  only my partitions running ubuntu are listed.  what am i doing wrong?  any help would be great.

---

### Post by Michaelt74 on 2007-03-28
When you boot up do you see hda1 on your desktop?

Do you mean by 'mounting', you are trying to enable write access to the NTFS partition?

---

### Post by shantz24 on 2007-03-28
i didnt think ubuntu supported write to ntfs?  i just wanted to play my music files from my windows partition.  i found a command line in another post and ran it and i now have access to my windows partition.  and no it was not on my desktop, it was no where in ubuntu that i could find and i have been looking for the past 3 days and trying different things.  thanks for responding though.

---

### Post by halitech on 2007-03-28
guess you fixed it, never mind :D

---

### Post by machoo02 on 2007-03-28
Have you seen [this thread]("http://ubuntuforums.org/showthread.php?t=217009&")?

---

### Post by Yorboy on 2007-03-31
Hey all.
After much consternation and re-installing of 6.10, I read that Fiesty 7.04 beta was the upgrade now available, to be launched in April as stable version.  I decided to upgrade and viola, my ntfs and screen issues solved.  I now have access to my ntfs drive, can copy and paste FROM it,  still don;t have write access yet.  My screen refresh rates are now great, I use Radeon X1950 card.  I'm a happy camper.  

Try it out.

---

