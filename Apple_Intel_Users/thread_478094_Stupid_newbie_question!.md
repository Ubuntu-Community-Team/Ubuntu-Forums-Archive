---
title: "Stupid newbie question!"
date: 2007-06-19
forum: Apple Intel Users
---

### Post by BananerBreadMan on 2007-06-19
Okay, I have a 17" intel based iMac that I'd wish to install Ubuntu on, but being inexperienced with Linux and bootcamp holds me back. So... I need some instructions on installing Ubuntu... thanks.

---

### Post by kevinlyfellow on 2007-06-19
Installation should be pretty straight forward.  Just download the image for your computer (x86) and burn it to a cd, and pop it into your mactel and boot from the cd.  Here is the download page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  There are instructions on the page after you click the link to download.

---

### Post by ronocdh on 2007-06-19
> **BananerBreadMan said:**
> Okay, I have a 17" intel based iMac that I'd wish to install Ubuntu on, but being inexperienced with Linux and bootcamp holds me back. So... I need some instructions on installing Ubuntu... thanks.
What do you mean by "bootcamp holds [you] back"? As Kevinly said, it is a rather straightforward process: partition (using Boot Camp), then boot to the installer CD and install Ubuntu. Please describe in detail any trouble you're having.

---

### Post by Greywhind on 2007-06-19
Here's what I used for my Intel 17" iMac

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Note: Some of the instructions there are just for MacBooks, but at least the basic installation works for iMacs.

---

### Post by ronocdh on 2007-06-19
> **Greywhind said:**
> Here's what I used for my Intel 17" iMac

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Note: Some of the instructions there are just for MacBooks, but at least the basic installation works for iMacs.
Yes, that is certainly a good guide. I'll add the following:
[LIST]
[*][Ubuntu on MacBook Pro]("http://ubuntuforums.org/showthread.php?t=198453")
[*][OnMac.net's triple boot guide]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu")
[*][rEFIt's documentation on triple booting]("http://refit.sourceforge.net/tripleboot/")
[/LIST]
HTH!

---

### Post by BananerBreadMan on 2007-06-20
> **kevinlyfellow said:**
> Installation should be pretty straight forward.  Just download the image for your computer (x86) and burn it to a cd, and pop it into your mactel and boot from the cd.  Here is the download page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  There are instructions on the page after you click the link to download.

Straight forward? Well that isn't the case with me. Anyway, I'm having trouble with splitting bootcamp, wait, I don't even know how to do that!

---

### Post by ronocdh on 2007-06-20
> **BananerBreadMan said:**
> Straight forward? Well that isn't the case with me. Anyway, I'm having trouble with splitting bootcamp, wait, I don't even know how to do that!
Again, I'm a little confused: what do you mean by "splitting bootcamp"? The Boot Camp utility has built-in graphical partition editor which asks you to drag a slider bar. It'll automatically resize and partition, all you have to do is drag the slider.

---

### Post by BananerBreadMan on 2007-06-20
> **ronocdh said:**
> Again, I'm a little confused: what do you mean by "splitting bootcamp"? The Boot Camp utility has built-in graphical partition editor which asks you to drag a slider bar. It'll automatically resize and partition, all you have to do is drag the slider.

Okay, I've found that out. Now what is this intaller CD you mentioned earler? I've got Ubuntu on a disk, is that what you mean?

---

### Post by ronocdh on 2007-06-20
> **BananerBreadMan said:**
> Okay, I've found that out. Now what is this intaller CD you mentioned earler? I've got Ubuntu on a disk, is that what you mean?
Correct!

---

### Post by BananerBreadMan on 2007-06-20
> **ronocdh said:**
> Correct!

Okay, so how exactly do I "boot" the CD? 

I tried going to start the windows intaller on boot camp.

I tried popping in the disk before log in, also, it only says Macintosh HD.

What now?

---

### Post by ronocdh on 2007-06-20
> **BananerBreadMan said:**
> Okay, so how exactly do I "boot" the CD? 

I tried going to start the windows intaller on boot camp.

I tried popping in the disk before log in, also, I only say Macintosh HD.

What now?
Insert the CD, reboot, hold down the C key to boot from the CD.

---

### Post by BananerBreadMan on 2007-06-20
> **ronocdh said:**
> Insert the CD, reboot, hold down the C key to boot from the CD.

I tried. I insterted the disk, I shut the thing own, booted up (holding the C key) and nothing happened. I thought you meant the Control key, so I tried that, nothing happened. I thought you meant hold the alt and C ket at the same time, nothing happped. I must have missed something...

---

### Post by Betta on 2007-06-20
How did you burn the .iso onto the disc? It's likely that you didn't burn the .iso correctly and as such, the CD is not usable.

Here's a good guide on how to do that with Mac: [http://www.macosxhints.com/article.php?story=20060619181010389](http://www.macosxhints.com/article.php?story=20060619181010389)

-Betta

---

### Post by ronocdh on 2007-06-20
> **Betta said:**
> How did you burn the .iso onto the disc? It's likely that you didn't burn the .iso correctly and as such, the CD is not usable.

Here's a good guide on how to do that with Mac: [http://www.macosxhints.com/article.php?story=20060619181010389](http://www.macosxhints.com/article.php?story=20060619181010389)

-Betta
I always use **Burn**. Find it at [OpenSourceMac]("http://www.opensourcemac.org").

---

### Post by russo.mic on 2007-06-21
My God, This site is the doorway.  It's not going to reach out and drag you through it.

google is your friend.

That having been said,  put the ubuntu CD in the drive, and shut the computer down.  hold down the C key while turning it on.  That forces the MBP to boot from the CD drive.

If you've burned the CD correctly, it will boot up.  You've probably just dragged the ISO file onto a burn folder in OS X and burned it as an ISO file on the disk.  This will not work. 

Use NERO, or TOAST, or BURN, or something to MOUNT the ISO file first.  that will create a directory structure on the CD.  this is will create a bootable CD.  just dragging the ISO file on a CD will NOT.

You'll have to install fglrx manually from the command line most likely, god help you.  There are plenty of good walkthroughs available, so there's no need to re-write on here.  My advise for you is to use Ubuntu 7.04 Fiesty Fawn, as Gusty is still quite in development.

Follow the walkthroughs, and you'll learn alot. if you need some help from there, then we'll all help I'm sure.  
Good luck.

---

### Post by ronocdh on 2007-06-21
> **russo.mic said:**
> My God, This site is the doorway.  It's not going to reach out and drag you through it.

google is your friend.

That having been said,  put the ubuntu CD in the drive, and shut the computer down.  hold down the C key while turning it on.  That forces the MBP to boot from the CD drive.

If you've burned the CD correctly, it will boot up.  You've probably just dragged the ISO file onto a burn folder in OS X and burned it as an ISO file on the disk.  This will not work. 

Use NERO, or TOAST, or BURN, or something to MOUNT the ISO file first.  that will create a directory structure on the CD.  this is will create a bootable CD.  just dragging the ISO file on a CD will NOT.

You'll have to install fglrx manually from the command line most likely, god help you.  There are plenty of good walkthroughs available, so there's no need to re-write on here.  My advise for you is to use Ubuntu 7.04 Fiesty Fawn, as Gusty is still quite in development.

Follow the walkthroughs, and you'll learn alot. if you need some help from there, then we'll all help I'm sure.  
Good luck.
As I'm sure you're aware, you're kind of being a dick. We all have our moments, though, so it's no big deal, but I wanted to point out that your dismissive attitude may have led you astray in diagnosing the OP's problems: OP indicated the machine was a "new" 17" MBP, which means it'll have an Nvidia graphics card, and therefore the fglrx driver is not applicable.

---

### Post by russo.mic on 2007-06-21
Excuse me for  being precived as a "dick".  All I'm saying is that there is plenty of instructions on the web and this site that answer all these questions.  I think that everybody needs a certain amount of self-suffiecency if there going to move forward.  If everybody everytime they need something rushes to post a problem without bothering to try and get the info themselves we'll all be spending a lot more time in the future answering the same questions over and over again.

Your right, he prob. does have the nvidia graphics card.  I missed it.  

I am not trying to be a dick.  which is why I said if he needs help beyond the walkthrough, or something of that nature, i'll (and I assumed we, or us, i.e. the people of this forum) would be glad to help him.  It's just not fair for everybody to answer the same questions over and over again.

I'm not blaming anybody for not knowing something, but with the WWW as a resource, there's no excuse not to find out.

---

### Post by kzm. on 2007-06-23
hm. i think thats an interesting point there about how to use a forum. little bit off topic of this thread but i would like to speak up anyway..
i find myself sometimes too, that i actually found some info for my problem, but then the post is from a year ago or i find two and have not enough background to judge them. so i think a lot of people, noobies in particular, rather ask for guidance which to trust, which solution approved them self, what is the quintessence of all those numerous threads looked at before. the community is a living thing and problems get solve or change and need new questions.
on the other side, its good to remember people to use the forum not incautious all the time. 
so i guess a forum needs "dicks" and "noobs"... sorry for being so intermediating.

---

### Post by ivesjd on 2007-06-23
I'm kinda on the "dick" side on this one. If this person is having this many problems just trying to boot the live-cd, maybe they should stick with OS X for awhile and read up a bit more on linux. Or maybe not, maybe they are just new to macs and haven't spent the time to learn it yet. But either way, linux isnt for everyone.

---

