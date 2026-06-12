---
title: "Partitioning for &quot;home &amp; dev"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-10-14
Hi all, what's the advisablity of making seperate home & dev partitions for multiple installs of linux[currently 6 w/more to come]?  How big a home partition should I make[plan on having at least 10 distros] & how big a dev?  Is it even feasible?
Before you ask, yes, I am looney, crazy, wacked, whatever.  I just like the idea of having alot of OS's to play with :)  I will always have win98se[highly modded] on a seperate hdd[hda], the rest of win I wouldn't have if given!
As always, thanks for any replies
Randy

---

### Post by PriceChild on 2006-10-14
If you've going to be testing 10 different distros... firstly i reccomend you use live cds.

Secondly i reccomend you DON'T share the /home partition. - different versions of apps on different distrobutions may cause breakage.

And lastly, if you're going to be installing so many to test, why not just use one partition for each one, and share a swap.

---

### Post by deadgobby on 2006-10-14
You are crazy for one. Ya live Cd's are great, but not all distro's come with one. 
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
 I do not know what you have in mind on testing different ditros. Have you ever gone to 
[http://distrowatch.com/](http://distrowatch.com/)
 Not all will be easy to install. Like Gentoo.
If you want to test and then Dl like 5 to 15 disk distro. 
Gobby

---

### Post by randiroo76073 on 2006-10-14
Thanks for the reply PriceChild, I wasn't aware that using 1 home might break others, will take that into consideration :)  As to why not live, I want any changes I make to stick, not redo everytime I load cd.  Is a central repository for apps/dev feasible w/o breakage?  I already share swap[21/2 x ram=5gb].  Any other pitfalls I might run into?
Thanks
Randy

---

### Post by taurus on 2006-10-14
Then go find a spare PC and play around with all the distros you want on that!  Until you find the one you like, install it on your own personal PC.

---

### Post by PriceChild on 2006-10-14
> **randiroo76073 said:**
> I want any changes I make to stick, not redo everytime I load cd.  Is a central repository for apps/dev feasible w/o breakage?I stick by my advice to give each its separate partition.

Different distros use extremely different methods of and different versions and just not a good idea :)

---

### Post by randiroo76073 on 2006-10-14
Roger on that PriceChild, I have room[320gb], this begs another question, how many patitions will linux recognize on 1 hdd?

---

### Post by deadgobby on 2006-10-14
I do not know, but your are going to run GRUB crazy.

---

### Post by randiroo76073 on 2006-10-14
tarus, if it's not too much problem, I kinda like everything on 1 PC :)
deadgobby, why then it'll be just like me! LOL!

---

### Post by PriceChild on 2006-10-14
> **randiroo76073 said:**
> Roger on that PriceChild, I have room[320gb], this begs another question, how many patitions will linux recognize on 1 hdd?the only limit should be primary partitions - 4. However you can have a logical partition with loads more in.

---

### Post by randiroo76073 on 2006-10-14
OK PriceChild, how does this sound:  hda1 primary1= Ubuntu+ necessary home & dev[logicals], Kubuntu[logical] + home & dev, Xubuntu[logical] + home & dev, Mephis[logical] + home & dev. Shared swap

had1 primary2= Some similar based distros + etc.
hda1 primary3= etc. 
hda1 primary4= open/storage

---

### Post by deadgobby on 2006-10-14
> **randiroo76073 said:**
> tarus, if it's not too much problem, I kinda like everything on 1 PC :)
deadgobby, why then it'll be just like me! LOL!
All I can say is this... You do not sleep much. Cause, like for Suse it takes a good hour, FC takes a good hour, Mandriva and so on. The advr time to install a distro is a hour time. So 10 hours right there. For each distro to up grade on a cable modem is about from 2 minutes to an hour. Then to get each distro to run the with extra goodies. About an hour each one. So add it up. Not too mechen the stop time to get Gentoo up and running. 
What in this world of the 10 distro's you want to test any ways?

---

### Post by randiroo76073 on 2006-10-14
deadgobby, LOL! you don't know the half of it, I'm on dialup & dl 24hrs a day[separate phoneline] & puter[90ish] just for that, + when your "60" you don't need much sleep :)

---

### Post by ReaderRat on 2006-10-14
> **randiroo76073 said:**
> deadgobby, LOL! you don't know the half of it, I'm on dialup & dl 24hrs a day[separate phoneline] & puter[90ish] just for that, + when your "60" you don't need much sleep :)
Ah-Ha, another 60 y.o..
Somebody correct me if I am wrong. I believe you can only boot from a Primary partition, and you are limited to 4. Believe me,  it is enough work just to boot 2 distros. Stick with Ubuntu and one other. IMO,You are using the best & easiest to learn, install, upgrade, etc..........Ubuntu........:D

---

### Post by PriceChild on 2006-10-14
> **ReaderRat said:**
> Ah-Ha, another 60 y.o..
Somebody correct me if I am wrong. I believe you can only boot from a Primary partitionYes.. ie grub. However that can then launch any other distro.

There is something about a 100 distro grub floating around somewhere.

---

### Post by randiroo76073 on 2006-10-14
100 !!! WOW, I'm not THAT ambitious, 10-12 will do me plenty LOL!

---

### Post by randiroo76073 on 2006-10-14
To digress to post #11, is this now a do-able scenario or have I fubared it?  Any replies welcome :)
Thanks
Randy

---

### Post by randiroo76073 on 2006-10-14
Yup, would be fubar, forgot hda0 primary1=98se + 3 logical
hda1 primary2= Ubuntu+ necessary home & dev[logicals], Kubuntu[logical] + home & dev, Xubuntu[logical] + home & dev, Mephis[logical] + home & dev. Shared swap
had1 primary3= Some similar based distros + etc.
hda1 primary4= open/storage 
Does that make it do-able?

---

