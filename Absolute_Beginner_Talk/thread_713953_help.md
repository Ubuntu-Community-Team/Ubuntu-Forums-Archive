---
title: "help"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-03-03
i m asking this question immediately just i installed ubuntu
i m having 80GB hd
now i par in this way
swap 1gb,  10gb / ext2,  rest  /home ext2 ,plz answer my 2 doubts

  1.   when im partitioning i didn't understand this,it asked
        (a) type of new partition(primary,logical),how ever i selected primary for all
        (b) location for new partition (begining,end),  how ever i selected begining for all
        
 2.   where does it get store whan i store something on desk top and
        i alloted a 60gb for /home where could i find this space

plz help me

---

### Post by TeoBigusGeekus on 2008-03-03
1)[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html")
2)If you go to the menu Places (top panel) you can find your home folder.
Anything stored on your Desktop is saved in a folder in your home folder called Desktop (i.e. /home/Desktop)

EDIT: Make that /home/yourusername/Desktop

---

### Post by phanipalagummi on 2008-03-03
thanks a lot :)

---

### Post by owbizi on 2008-03-03
Like already said, and also a primary partition generally is where the operational system - in this case, Ubuntu - is located, and an extended, where you store files (a logical partition is *inside* an extended one).

However, why did you choose ext2, and not ext3?

---

