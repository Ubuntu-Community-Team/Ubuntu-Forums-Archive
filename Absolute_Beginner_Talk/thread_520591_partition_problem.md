---
title: "partition problem"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Aspra on 2007-08-08
Some of you are probably going to laugh, but I have a 80 gig hard drive on my laptop. I wanted to have windows and Ubuntu on this hard drive, so I used the manual option for partitioning it and now Ubuntu is on the windows partition and I had allocated only 25 or so gigs to it, thinking its going to be for to Ubuntu partition. So now i only have 8 gigs left of 25 and i don't even know whats with the rest of it. heres a pic.

[http://i12.photobucket.com/albums/a238/Nuclearanthrax/desktop1.jpg](http://i12.photobucket.com/albums/a238/Nuclearanthrax/desktop1.jpg)

hope i can get some help, I need to get Ubuntu off the windows side without hurting windows and getting the rest of my hard drive back..

---

### Post by Inxsible on 2007-08-08
I dont understand what you are asking.

you are logged into Vista, so you have definitely not over written your Vista. so what do you mean Ubuntu is on your windows partition?

If you havent installed Ubuntu yet, you can combine the empty partitions and then re-create the partitions the way you want them.

---

### Post by hyper_ch on 2007-08-08
Well, it seems you resized your windows parititon to 25GB and you have already used 17GB out of it... hence 8GB are free on that partition...

Next to that you did create two other partitions, one is 31GB and one is 18Gb....

So, what do you want to do now actually?

---

### Post by Aspra on 2007-08-08
Its just XP with the zune theme. What im saying is that I resized my disk to be 25 gigs ,thinking it was going to ubuntu, that it would be no where near my windows file system leaving windows to the rest of my drive 50 or so gigs. But what happened is that it resized my drive and now the rest of  the space on the 80 gig drive is an unkown partition so i cant get to it.

So now my ubuntu and XP file system are on the 25 gig partition and with just 8 gigs left.

---

### Post by Aspra on 2007-08-08
> **hyper_ch said:**
> Well, it seems you resized your windows parititon to 25GB and you have already used 17GB out of it... hence 8GB are free on that partition...

Next to that you did create two other partitions, one is 31GB and one is 18Gb....

So, what do you want to do now actually?

Id like to get the 31 and 18 gigs usable again, right now it says in Ubuntu and windows that my hard drive is 25 gigs max

---

### Post by oilchangeguy on 2007-08-08
this may help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by miggols99 on 2007-08-08
This means that the partition is 25GB, not the hard drive.

---

### Post by Inxsible on 2007-08-08
> **Aspra said:**
> Id like to get the 31 and 18 gigs usable again, right now it says in Ubuntu and windows that my hard drive is 25 gigs max

Have you installed Ubuntu already ? or do you mean the LiveCD ?

Like I said already, if you havent installed Ubuntu yet, then you can simply use the XP Partitioner and delete the 31GB and the 17 GB drives and then re create the partitions again the way you want to.

---

### Post by bodhi.zazen on 2007-08-08
Partitioning is tricky, and terminology is different with Linux and windows.

Best do a little reading before you change too much ...

Try these links :

Gparted : Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by Aspra on 2007-08-08
> **Inxsible said:**
> Have you installed Ubuntu already ? or do you mean the LiveCD ?

Like I said already, if you havent installed Ubuntu yet, then you can simply use the XP Partitioner and delete the 31GB and the 17 GB drives and then re create the partitions again the way you want to.

I have installed it,  Im in it right now. Liking its for the most part beside this little mishap..

---

### Post by Inxsible on 2007-08-08
> **Aspra said:**
> I have installed it,  Im in it right now. Liking its for the most part beside this little mishap..

you have to resize the partitions then using GParted. Try reading up on partitioning from the links that bodhi gave. It would save you a lot of grief :)

---

### Post by Aspra on 2007-08-08
I will.

---

### Post by bwtranch on 2007-08-08
I would definately do an external back-up of data FIRST. Then, I would do a fresh install, windoze first, then Linux.:)

---

### Post by Aspra on 2007-08-08
> **bwtranch said:**
> I would definately do an external back-up of data FIRST. Then, I would do a fresh install, windoze first, then Linux.:)

lol Even though I could do that, windows is a bitch to install, way more time consuming than this god of OS's you call Ubuntu. But if it comes down to that I probably will. All this info on Gparted and partitioning is leaving me with a headache and an overwhelming sensation that I cant do this..

---

### Post by Aspra on 2007-08-08
Uh, im still trying to get the hang of this but couldn't I delete the unknown partition while  in wndows then reformat it? and isnt that what gparted is capable of also?

---

