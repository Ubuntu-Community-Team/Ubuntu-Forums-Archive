---
title: "Cant create a primary partion"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-25
When i try to using G parted it wont give me the option it blanks it out, and only gives me the option to choose logical. Anyone know whats wrong

---

### Post by Nikron on 2007-05-25
You can't have more than 4 primary partitions.

---

### Post by mikewhatever on 2007-05-25
How many partitions do you already have? You can't have more then 4 primary ones, and besides, what is wrong with logicals?

Also check that you are not making that primary partition inside an extended one.

---

### Post by mojo123 on 2007-05-25
this is a pic, as far as i know i only have 1 primary partion and its ex3
[http://aycu10.webshots.com/image/16969/2001705256615820007_rs.jpg](http://aycu10.webshots.com/image/16969/2001705256615820007_rs.jpg)

---

### Post by bodhi.zazen on 2007-05-25
:lolflag:


Create a partition where ?

You need free space ...

resize (make smaller) sda1 and make a new partition into the resulting free space.

---

### Post by ryanVickers on 2007-05-25
Obviously!  after that it should work fine.  Besides that, it all looks normal, no problem!

Oh, you can't modify a mounted partition.  Unmount it first, unless that's where linux is, than you have to do it using the live cd, because I wouldn't recommend unmounting the partition your running on lol!

---

### Post by mojo123 on 2007-05-25
i know but look now
[http://img02.picoodle.com/img/img02/8/5/25/f_proofm_ba26798.png](http://img02.picoodle.com/img/img02/8/5/25/f_proofm_ba26798.png)

---

### Post by insane_alien on 2007-05-25
you also can't make a primary partition inside an extended partition,

---

### Post by mojo123 on 2007-05-25
what do you mean?

---

### Post by insane_alien on 2007-05-25
well, the unallocated space you have is with in the partition you've set out to contain extended partitions. you can't make a primary partition in there.

you can only make logical drives in extended partitions.

if you delete /dev/sda2 then make a primary partition and you can create another partition for your swap.

i think my set up is close to what you want. Gparted seems not to realise that sda2 is mounted at /home for some reason

---

### Post by mojo123 on 2007-05-25
It wont give me the option to delete my extended partition

---

### Post by insane_alien on 2007-05-25
its because its mounted.

boot up from your live cd

install gparted then edit your partition table as you want.

---

### Post by trak87 on 2007-05-25
If you shrink sda1 you can add more primary partitions.

---

### Post by mojo123 on 2007-05-25
will the g parted live cd work?
Ill try it now

---

### Post by insane_alien on 2007-05-25
yeah the gparted CD was built for this sort of thing. i just assumed you already had an ubuntu live CD on hand.

---

### Post by mojo123 on 2007-05-25
Right now im posting from the live cd neither g parted cd nor ubuntu cd give me the option to delete my exteneded partition. Can someone help

---

### Post by mojo123 on 2007-05-25
please anyone know why!

---

### Post by trak87 on 2007-05-25
> **mojo123 said:**
> Right now im posting from the live cd neither g parted cd nor ubuntu cd give me the option to delete my exteneded partition. Can someone help

You have to first delete the logical partitions inside the extended partition before you can delete the extended partition itself.

---

