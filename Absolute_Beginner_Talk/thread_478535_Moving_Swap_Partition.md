---
title: "Moving Swap Partition"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Spono on 2007-06-19
I'm running a dual-boot setup with WindowsXP and Ubuntu Feisty.

My hard drive partitions are shown below:

[IMG]http://i161.photobucket.com/albums/t228/spono_photo/Partition.jpg[/IMG]

I want to combine the Windows partitions D and E, but the linux swap space is in the way.

Is it ok to wipe the linix swap space, combine D and E, and then put the linux swap at the end of the HDD?  Will this mess up anything in Ubuntu?

---

### Post by Alex&amp;Linux on 2007-06-19
I suppose so.
I had to do something similar when I setup my first dual-boot.
However, If you have any data stored on the disk that you are not ok with loosing, always back it up, even during simple partitioning tasks!
Why so many NTFS?

---

### Post by starcraft.man on 2007-06-19
*cries at the sight of seeing partition magic with symantec logo* WHHHHHYYYYYYYYYYYYYYYYYYYYYYYYYYY? I'm sorry, I actually liked that product back in the day when I used it... before symantec bought it out. It's like Symantec loves to buy out products I use, they bought my firewall called sygate too and made that bloated as well. Symantec, do you hate me and the products I used to use (did use at purchase)?

/end rant

Anyway, first thing. BACK UP!!! I don't want no crying, I've seen sap stories from every suite about how the ONE file someone absolutely needed got corrupted in a merge (or insert other partition change). I'm not responsible for that if it happens.

Now, on to actual questions. In order, Yes and no. I'm pretty sure (I think I read it...) that Ubuntu detects at boot up wherever the swap space is located... thus moving it is fine long as its not otherwise messed up.

One thing I would like to know is why 1.5 GB of Swap? How much RAM do you have? 1.5 GB will never be used IMO unless you have some puny amount of physical ram like 256... 

My _RAM/Swap recommendation_ is: 1) Physical RAM less than 2 GB, Swap size up to 1 GB (if you really do lots of work like VMs). 2) Physical RAM 3 or more GB, 256 or less Swap. Pick which one you fit under and resize accordingly, IMO 1.5 is wasted space.

Thats it. I think its all answered. Oh and in case it wasn't clear... I **_HATE_** *eyes burn* Symantec. They make me mad.

---

### Post by Spono on 2007-06-19
> **Alex&Linux said:**
> Why so many NTFS?

Ugh, I dunno.  It's an old habit I got from my dad of partitioning my windows into three drives.  Can't seem to shake it.

> **starcraft.man said:**
> *cries at the sight of seeing partition magic with symantec logo* WHHHHHYYYYYYYYYYYYYYYYYYYYYYYYYYY? I'm sorry, I actually liked that product back in the day when I used it... before symantec bought it out. It's like Symantec loves to buy out products I use, they bought my firewall called sygate too and made that bloated as well. Symantec, do you hate me and the products I used to use (did use at purchase)?

/end rant

Anyway, first thing. BACK UP!!! I don't want no crying, I've seen sap stories from every suite about how the ONE file someone absolutely needed got corrupted in a merge (or insert other partition change). I'm not responsible for that if it happens.

Now, on to actual questions. In order, Yes and no. I'm pretty sure (I think I read it...) that Ubuntu detects at boot up wherever the swap space is located... thus moving it is fine long as its not otherwise messed up.

One thing I would like to know is why 1.5 GB of Swap? How much RAM do you have? 1.5 GB will never be used IMO unless you have some puny amount of physical ram like 256... 

My _RAM/Swap recommendation_ is: 1) Physical RAM less than 2 GB, Swap size up to 1 GB (if you really do lots of work like VMs). 2) Physical RAM 3 or more GB, 256 or less Swap. Pick which one you fit under and resize accordingly, IMO 1.5 is wasted space.

Thats it. I think its all answered. Oh and in case it wasn't clear... I **_HATE_** *eyes burn* Symantec. They make me mad.

Oh don't worry, the only thing on D and E are video files and games.  I've already backed up the videos and I can (and plan to) re-install the games.  In fact, the reason I'm doing this is to have more space to install some games.

So just to be clear, this will only affect the two windows partitions, and won't affect the linux partition, correct?

EDIT: Also, will linux get angry with me for shrinking it's swap space to 1GB?

---

### Post by starcraft.man on 2007-06-19
> **Spono said:**
> 
So just to be clear, this will only affect the two windows partitions, and won't affect the linux partition, correct?

Yup, thats my understanding of it... delete/move swap partition and then merge drives, hopefully it works right. I don't really like changing partitions after installing things. I partition once for the longterm and thats it.

Edit: No, it uh doesn't have feelings... how much RAM do you have anyway? It should run just as smoothly in almost all cases.

Edit 2: Oh and have a look at gparted once your done... I really don't recommend supporting Symantec and their now bloated products, they've been going down hill for a long time.

---

### Post by Spono on 2007-06-19
Well I've got either 512MB or 768MB of RAM.

Before I sent this computer back to Dell for a motherboard replacement, both my 512 stick and my 256 stick worked fine, but when I got it back, it doesn't recognize the 2nd stick half of the time.  I've still gotta get them to fix that before the warranty expires in September.

---

### Post by rfurman24 on 2007-06-19
I tried to move my swap space before, doing something similar to what you are doing and it left my linux unbootable. Maybe I did something wrong but I would do some more checking first.

---

### Post by starcraft.man on 2007-06-19
> **Spono said:**
> Well I've got either 512MB or 768MB of RAM.

Before I sent this computer back to Dell for a motherboard replacement, both my 512 stick and my 256 stick worked fine, but when I got it back, it doesn't recognize the 2nd stick half of the time.  I've still gotta get them to fix that before the warranty expires in September.

512 is more than enough combined with 1 GB of swap. I would be very mad at Dell for breaking my stick though, get on their case to send you a replacement, thats not right. I don't care for tech support from any companies though, I do my own, that way I know I broke it :p.

It's probably cheaper for you to just go and buy a new 512 stick to replace the 256 one. RAM has really bottomed out in price.

> **rfurman24 said:**
> I tried to move my swap space before, doing something similar to what you are doing and it left my linux unbootable. Maybe I did something wrong but I would do some more checking first.

Swap is actually not really needed (not in the strictest sense from what I seen) to boot up. If your box became unbootable you likely corrupted the main root partition. That will make you unbootable. One thing I know swap to be 100% necessary for is hibernation, the computer can only store data into the HDD because the RAM becomes unpowered (loses data when no power) in hibernation.

---

### Post by Spono on 2007-06-19
Hmm, well it looks like it's a tie game with one for-the-plan and one against-the-plan.

Anyone else care to chime in?

---

### Post by Alex&amp;Linux on 2007-06-19
Hey Starcraft.man,

Just wanted to let you know that I deeply share your hatred for symantec.
I do networking technical support, and of course everyone uses some sort of windows system. 

There are times when I ask someone if they have had any issues with malware, computer viruses, and they reply "oh I have Norton", to which I reply, "ok, so we've found one so far, what else?"

Regarding the partition issue, its actually not too bad of an idea to have a few logical NTFS, for security and stability reasons, though its been quite some time since ive dealt with that crap.
My suggestion is: Back up files, format drive. If absolutely necessary, install windows, and resize the patrition to leave desired volume for Ubuntu, Then install ubuntu. Im sure that eventually you will forget you have windows installed!

---

### Post by psusi on 2007-06-19
I watched partition magic munch way too many drives to trust it any further than I can throw it.  Though that was back when it was still powerquest or whoever it was before symantec.

---

### Post by starcraft.man on 2007-06-19
> **Alex&Linux said:**
> Hey Starcraft.man,

Just wanted to let you know that I deeply share your hatred for symantec.
I do networking technical support, and of course everyone uses some sort of windows system. 

There are times when I ask someone if they have had any issues with malware, computer viruses, and they reply "oh I have Norton", to which I reply, "ok, so we've found one so far, what else?"


ROFL! I know what ya mean. I have seen Norton _Cripple_ PCs it was installed on with its overzealous protection. It causes way too many troubles IMO today than its worth, whatever useful it used to have in the past, stayed in that distant past.

> Regarding the partition issue, its actually not too bad of an idea to have a few logical NTFS, for security and stability reasons, though its been quite some time since ive dealt with that crap.
My suggestion is: Back up files, format drive. If absolutely necessary, install windows, and resize the patrition to leave desired volume for Ubuntu, Then install ubuntu. **Im sure that eventually you will forget you have windows installed!**

Seconded. Do the partition change, since your not doing any modification to Windows/Ubuntu itself I don't see a problem. Always good to be prepared though, that is the nature of a PC.

---

### Post by Alex&amp;Linux on 2007-06-19
> **Spono said:**
> Hmm, well it looks like it's a tie game with one for-the-plan and one against-the-plan.

Anyone else care to chime in?

Thought you might be interested in this:

[http://people.debian.org/~psg/ddg/node81.html](http://people.debian.org/~psg/ddg/node81.html)

Its recommended that you allow swap space to be (available physical RAM)x2
However, youll probably find that linux is great on resources, not too much of a need to get into swap anyhow!

And yea, as long as you have the important stuff backed up, I'd go for it, shouldnt be too much risk involved in moving swap partition around, and like starcraft.man said, it will be detected regardless of its location!

There is always a risk when partitioning, but hey, its only a computer...in any case, youll have everything setup by tonight!

---

### Post by louieb on 2007-06-19
Ubuntu will have its revenge if you delete the swap partition and don't tell Ubuntu about it..  do your thing  to your NTFS partitions, then create a new swap partition. Before you change your partitions around comment out the swap partition line in /etc/fstab.
then when done jacking your partitions around point the swap line to your new partition. 
Because i'm lazy you will need to search on 3 things **uuid, swapon and swapoff.**

---

### Post by louieb on 2007-06-19
> **Alex&Linux said:**
> Thought you might be interested in this:[http://people.debian.org/~psg/ddg/node81.html]("http://people.debian.org/%7Epsg/ddg/node81.html")
Yes it takes me back to the old days. Their examples reference machines with 8MB and 16MB of memory.

---

