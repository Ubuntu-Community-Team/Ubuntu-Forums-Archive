---
title: "Why primary EXT3 of linux cannot be resized ?? Only part. into extended can ?"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-26
(with gparted or qtparted ) 
  
Is there a way to resize even primary partitions of linux (not in extended part)

thank you very much !!
  
pat

---

### Post by gord on 2005-11-26
you'll need to make sure you arn't using the partitions at the time else things would get screwy, if you just mount it and its not /home or something else thats needed to work, just right click it in GParted and then resize it or whatever else you want to do :)

other wise you'll need a live cd (or a seperate linux install), and then you can do the same as long as you don't have the partitions mounted

---

