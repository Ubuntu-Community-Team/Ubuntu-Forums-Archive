---
title: "a few quick questions"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by tehno0blet on 2006-03-27
someone just told me about ubuntu today and i wanted to check it out.  I have been using windows for quite a long time and i am tired of it.  The only reason i sill use it is i play alot of PC games.  Here are a few of my questions, i was reading some of the stuff on this site but i am still confused on some things.

1)is there a dual-boot system that will allow me to still boot XP to play games?

2)are there any major changes i have to make to my system to use ubuntu? (inculding formatting the HD)

3)will having ubuntu installed mess up any of my settings and or lan capabalites in windows if i use a dual-boot?

4)do most of the windows programs (such as x-fire, aim, ext) work with ubuntu?

5)will any files i save from windows be avaible in ubuntu?

6)can i keep all of my songs and other files from xp and use them in ubuntu?

thanks in advance

---

### Post by NeghVar on 2006-03-27
> 1)is there a dual-boot system that will allow me to still boot XP to play games?

Yep, when you install it will give you some options.

> 2)are there any major changes i have to make to my system to use ubuntu? (inculding formatting the HD)

When you install it will give you an option for how you want your hard drives set up, you can tell it to use a blank area, a second disk or resize an existing partition to fit on. Oh and I also believe you will have to add Windows to your Grub list.

> 3)will having ubuntu installed mess up any of my settings and or lan capabalites in windows if i use a dual-boot?

Shouldn't change any settings, you'll just have to add windows to your boot manager (Grub).

> 4)do most of the windows programs (such as x-fire, aim, ext) work with ubuntu?

Nativly no, but there are programs like wine (free), crossover office and cedega both non free that will allow you to use MS software to an extant. Cedega allows you to play games btw. Oh and also most MS products have a good equivalant native to linux.

> 5)will any files i save from windows be avaible in ubuntu?

Yes, If you use fat32 fs then you can even write to your windows hd, ntfs is still experimental with writing but you can read once you mount it.

> 6)can i keep all of my songs and other files from xp and use them in ubuntu?

Yes.

Hope that helps a bit.

---

### Post by Papa-san on 2006-03-27
I am looking to do the same thing, so can you please explain the GRUB thing a bit more for someone who isn't very familiar with it?

---

### Post by sn123 on 2006-03-27
welcome to the ubuntu club :), I would recommend using a Ubuntu Live CD to play around with Ubuntu first before going with a full-blown install till you're comfortable with Ubuntu & answers are inline

[QUOTE=tehno0blet]someone just told me about ubuntu today and i wanted to check it out.  I have been using windows for quite a long time and i am tired of it.  The only reason i sill use it is i play alot of PC games.  Here are a few of my questions, i was reading some of the stuff on this site but i am still confused on some things.

1)is there a dual-boot system that will allow me to still boot XP to play games?
**Yes.**
2)are there any major changes i have to make to my system to use ubuntu? (inculding formatting the HD)
**No formatting is needed but you would need to partition your harddisk, I would recommend using Partition Magic though others should work just fine.**

3)will having ubuntu installed mess up any of my settings and or lan capabalites in windows if i use a dual-boot?
**Generally the answer is no but just in case you do mess up something during install you can always use Windows Rescue disks to get your system back to normal.**
4)do most of the windows programs (such as x-fire, aim, ext) work with ubuntu?
**I've never heard of x-fire and ext (maybe wine would work), but you can use gaim to connect to other IM servers like AOL, Yahoo, MSN & Google Talk**
5)will any files i save from windows be avaible in ubuntu?
**Yes, there are two ways to do it, if all you care about is to "view" the files you save in Windows on Linux then you don't have to do anything. If you want a read-write share between linux and windows then you would need to create another FAT partition which can be shared between Windows and Ubuntu.**
6)can i keep all of my songs and other files from xp and use them in ubuntu?
**Yes.**
thanks in advance[/QUOTE]

HTH,
S

---

### Post by aysiu on 2006-03-27
If you want to dual-boot, this guide is your friend:

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by sn123 on 2006-03-27
[QUOTE=Papa-san]I am looking to do the same thing, so can you please explain the GRUB thing a bit more for someone who isn't very familiar with it?[/QUOTE]
Grub is a boot loader which allows you to dual boot between different OSes.
Go through the manual of Grub on gnu.org to get more info:
[http://www.gnu.org/software/grub/manual/grub.html#Introduction](http://www.gnu.org/software/grub/manual/grub.html#Introduction)


S

---

### Post by Papa-san on 2006-03-27
Thank you all!

(I love these guys!):-D 
:-D 
:-D

---

### Post by tehno0blet on 2006-03-27
wow thanks a ton

i think i will try that cd thing to get the hang of this before i commit to doing it

---

### Post by tehno0blet on 2006-03-27
ok i just ordered the CD's

*Yes, there are two ways to do it, if all you care about is to "view" the files you save in Windows on Linux then you don't have to do anything. If you want a read-write share between linux and windows then you would need to create another FAT partition which can be shared between Windows and Ubuntu.*

so this would mean 3 partitons?  i have another, older 20 gig HD (my main is 80 gig) that i could use as storage between the two. would that work just as good as or better than a 3rd partition?

---

### Post by sn123 on 2006-03-27
[QUOTE=tehno0blet]ok i just ordered the CD's

*Yes, there are two ways to do it, if all you care about is to "view" the files you save in Windows on Linux then you don't have to do anything. If you want a read-write share between linux and windows then you would need to create another FAT partition which can be shared between Windows and Ubuntu.*

so this would mean 3 partitons?  i have another, older 20 gig HD (my main is 80 gig) that i could use as storage between the two. would that work just as good as or better than a 3rd partition?[/QUOTE]
If the 20 gig HD is FAT32 or you don't mind re-formatting it as FAT32 if it isn't, then you don't need three partitions on your main HDD (I am assuming the older HDD can be plugged into your system or is already plugged in :) )

S

---

