---
title: "How do you know if your drive can read DVD-Rom? or write data to DVD?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by babysteps on 2007-07-04
I'm sorry for a stupid, but wishful question: 

Is there a guide line as to how much you can get out of your CD/DVD drive?  There are lots to learn when first learning to use Ubuntu with setting the right permissions for read, and or write..etc.  But is there a way to find out for example, if my drive can ever be configured to do more than just read CD Roms and watch DVD Movies?  

Is it all pre-determined in the physical make of the drive? 

On one of my laptops I was able to write to DVD after changing some parameter.  If I hadn't read that online somewhere I would have thought this drive was limited in its capabilities.  There's another older laptop with a CD Rom that's also a DVD movies player, but I don't think it could write to CDs even...so, how do I know for sure?

Thanks!

Babysteps

---

### Post by orb9220 on 2007-07-04
> Is it all pre-determined in the physical make of the drive? 

Yes all you do is look up the manufacture model number and it will tell you exactly what the drive is capable of.

There are drives especially in laptops called DvDrom/cdrw drives that can only read DVD's for watching movies,etc... and can read/write to CD's. But they cannot write or burn DVD's and they cannot be made to write or burn dvd's because the only have the laser to read dvd's and do not have the laser to burn to dvd's.

People not familar with cdrom's terminology are easily confused by this and assume if they can read dvd's they must also be able to burn too.

Hope this helped.

---

### Post by zerobinary on 2007-07-04
go to hardware info in administration not very sure but give it a try

---

### Post by babysteps on 2007-07-06
Orb9220, thanks for the answer.  I was just curious about any sort of firmware upgrades, but I suppose anything upgradable would also be indicated.  I now will have to shop for a spare CD/DVD burner. 

Zerobinary, yes I did go to what's called Device Manager in my old Breezy version.  Actually it was here that I got hopeful.  The external DVD burner's status actaully changed to include DVD-R burning abilities after I followed a  few instructions from the forum.

---

### Post by hypnojazz on 2008-03-30
sudo su

sysctl -a | grep dev.cdrom

---

### Post by Sef on 2008-03-30
> I'm sorry for a stupid, but wishful question: 

The question was not stupid, but just a question that was asking for information.

---

