---
title: "Fixed order of several USB drives"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by brodie_sewak on 2007-01-07
Hi,

I don't know if this was asked a million times before but I didn't find anything.

I have three external USB drives connected to the computer via USB hub. I've added entries for all three drives in fstab to mount them automatically.

/dev/sdc1  /media/sdc1     ext3         errors=remount-ro,users,user  0  0  
/dev/sdd1  /media/sdd1     ext3         errors=remount-ro,users,user  0  0  
/dev/sde1  /media/sde1     ext3         errors=remount-ro,users,user  0  0  

My problem is that whenever I restart the machine the order of the drives is different. So I never know which drive is /dev/sdc1 because it could be any of the three. But I want to share a folder on one of the drives, so I need to know where this drive will be mounted to.

I hope anybody knows what I'm talking about...:D 

regards,
brodie

---

### Post by oyvindaa on 2007-01-07
[This](http://ubuntuforums.org/showthread.php?t=91948) is what you need.

Good luck :)

---

### Post by brodie_sewak on 2007-01-07
That's exactly what I needed... Thanks Bob ;)

---

