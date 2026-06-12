---
title: "partitions?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by shantz24 on 2007-03-31
i have ubuntu running on my desktop and i want to try it on my laptop.  i have ran the live cd but it is slow and it is always reading off the disc so i want to see what it can do installed.  i was just wondering if it doesnt work out can the partitions i made be deleted or will i just have to reformat them and use them as extra sotrage drives for windows.

---

### Post by sauyeeluo on 2007-03-31
make sure before you install you defrag your main windows partition twice before shrinking it. then proceed with the install and create a swap, root, and maybe a home partition if you wish.  if after you install on your laptop and no longer wish to use ubuntu you can use the same utility, gparted or qtparted, to delete those partitions that you created and resize the windows partition back to its original size. 

personally, im not too big of a fan of screwing around with partition sizes once they are set, seeing as if qtparted does a qtfarted (which has happened to a friend of mine) then the whole drive kinda...goes to hell.

---

### Post by DoorGunner on 2007-03-31
I do agree with sauyeeluo about the defragging. NTSF leaves program bits allover the place.

Like he also said there is a partition editor in the install package. What I did was to use it to partition off what i wanted to have for Ubuntu then just installed to the largest unused area. Then Ubuntu decided what it wants for the sizings.  It was the simplest way for me.

I was really impressed howfar ubuntu has come. The installation will migrate some of your window info over for you if you want it. With Feisty it even set up fstab for you as well. Really cool stuff.

---

