---
title: "installed Ubuntu OK but lost i have now lost it"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by timmy toad on 2007-05-06
hi all, newbie struggling already.

i have just installed UBUNTU onto a compter that was/is running Win XP, i have  removed the install CD and  Rebooted but now i can only see Win XP, i cannot see where Ubuntu is installed at all, how do i get it back please ?.

tim

---

### Post by Skrynesaver on 2007-05-06
When XP booted, was  there a menu of OSes first?
If not you didn't install GRUB. 
Is your "c:" drive the same size as before?
If so you didn't repartition the drive.

If either of the above is the case you may need to o through the install process again

---

### Post by timmy toad on 2007-05-06
thanks pal, i now realise what i should have done, when i got the ubuntu desktop come up, i now see there is an icon that says "install", so i have now clicked on that and it now seems to be doing what i expected, it is now creating a couple of partitions and copying files, so time will tell.

tim

---

### Post by timmy toad on 2007-05-06
the very latest is,** i am still stuck,** it only boots up into Ubuntu now. i dont get the option to boot into Win XP, also in the Ubuntu File viewer it doesnt show my Windows files either !!!!!!!!!!

tim

---

### Post by Skrynesaver on 2007-05-06
When you created a couple of partitions did you first reduce the size of your windows partition so there was space to form the partitions in?

---

### Post by drowner on 2007-05-06
Oh oh.

Did you install GRUB? I hope not!

---

### Post by timmy toad on 2007-05-07
I am still plodding on, thankfully i am using a spare computer which hsnt got any precious DATA to loose, but  i now know where i went wrong :-

I firstly installed Win XP on a 40 gig drive, then i installed UBUNTU by clickingon the INSTALL icon on Live CD desktop, it then asked me about Partitions and stuff during the installation but i obviously ticked the wrong box, because it obviously didnt know i had Win XP installed as well as it partitioned the drive  with just the two partitions it needed,succesfully removingany evidence of WinXP completely.

So i am currently installing WINXP AGAIN,BUT what i aim to do this time **BEFORE** i install UBUNTU AGAIN is to create the LINUX partitions first, i have found that Partition Magic will let me do this, it will let me specify what type of partitions i want.

I was doing quite well with it all lastnight until we got a Power Cut, so i went to bed and dreamed about PENGUINS !!!!!  LOL.

tim

PS. i havent found any GRUB yet !

---

### Post by seshomaru samma on 2007-05-07
After you install Windows and before you install Linux read [_**this**_]("http://www.psychocats.net/ubuntu/installing") carefully.

(The guide is written for a specific version of ubuntu , your version might be slightly different, if you get asked where to install Grub to ,'MBR' is the answer you are looking for)

---

### Post by timmy toad on 2007-05-07
thanks for that friend i will definitley do that, in fact straightaway.

tim

---

### Post by steve.horsley on 2007-05-07
My advice is that after you've reinstalled XP, delete that partition you made for Ubuntu, leaving un-partitioned space. Then tell the installer to use the un-allocated disk space (**not** the whole disk, this time). This will be easier than leading the installer by the nose telling it you want to install on **this** particular partition, and will also allow the installer to creat the swap partition that it wants.

---

### Post by timmy toad on 2007-05-07
cheers friend, i reckon i have now come to that conclusion myself now LOL, after quite a few dummy runs, i  am now installing Ubuntu for (jeez, i hope so) the last time, but it is so slow.

tim

---

### Post by Feba on 2007-05-07
I highly doubt ubuntu didn't see your XP installation, it's usually very good at that. You are probably the one that didn't see it.

This is why you need to be very careful anytime you get anywhere near installing a new OS or partitioning a drive.

---

### Post by timmy toad on 2007-05-07
LOL, i'm blind youre dead right LOL.

I have now selected the top option when asked about Partitioning methods etc. it should be OK this time (I hope) previously i selected the 2nd or 3rd options thinking it would find the partitions i had already created using Partition Magic**, but it didn't** LOL.

I have now seen that a lot of folk have had trouble when doing this with partition magic.

tim

---

