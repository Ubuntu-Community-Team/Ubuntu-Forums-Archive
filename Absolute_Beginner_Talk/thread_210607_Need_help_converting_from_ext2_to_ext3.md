---
title: "Need help converting from ext2 to ext3"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by jonboy99 on 2006-07-07
Hi all
Have ubuntu dapper installed on one of my hd partitions which is ext2.  Want it to be an ext3 partition now.
Dapper is all one partition including /home and /boot.

If I boot using knoppix or similar, and copy everything in the partition to say, a usb hard drive, then use gparted to reformat the partition as ext3, then copy everything back from the usb drive, will it all work?


Cheers
Jon

---

### Post by crystal on 2006-07-07
EDIT: nevermind... I think I dont know enough on this to comment.

---

### Post by woedend on 2006-07-07
why not just turn it into ext3?
sudo tune2fs -j /dev/xxx 
where xxx is the partition
then change /etc/fstab to read ext3 instead of 2

---

### Post by jonboy99 on 2006-07-07
Didn't realise you could do that.  I presume I couldn't run that command from the OS on the partition i wanted to convert could I - do I need to do it from an OS on a different partition?

Should I change the fstab before converting to avoid not being able to boot into the OS after converting it?

---

### Post by woedend on 2006-07-07
you can do it on a mounted system, since its not making a drastic change.  please realize that ext3 IS ext2, with journaling.  

I guess I should say that it's been written by security freaks its never good to do things on a mounted filesystem but i've never had a problem with it honestly.  so i'd run the command, then change fstab, then reboot.  let me know if you get stuck.  you can use aim to contact me if you want.


theres something about the root filesystem though, so give me just a moment

---

### Post by jonboy99 on 2006-07-07
Doh!  Just found out it is already ext3!   But on bootup one of the first things it says is 'mounted filesystem is ext2fs'.   Does it say this for ext3?

Is there some command I can run to find out if my other filesystems are ext2 or ext3?  (Got about 6 partitions with OSs on, on 2nd computer).

---

### Post by woedend on 2006-07-07
lol...sorry i was reading up on converting root partition...apparently it shouldn't have been a problem now(on older kernels it was).
sure, to check out if its ext3, use  
mount | grep /dev/hda1

for example...

---

### Post by jonboy99 on 2006-07-07
Cheers!  Looks like they're all ext3!




I'm getting my coat now..  :D

---

### Post by woedend on 2006-07-07
well that was suprisingly and thankfully easy enough :p.  glad everything is going well for you....a learning experience for me as well.

---

