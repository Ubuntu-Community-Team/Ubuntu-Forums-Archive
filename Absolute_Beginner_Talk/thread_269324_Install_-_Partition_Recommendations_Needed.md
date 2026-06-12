---
title: "Install - Partition Recommendations Needed"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by walesmd on 2006-10-01
After burning 6 coasters I got a good CD and messed around within the LiveCD boot. I am absolutely amazed and can not wait to get started with Ubuntu.

I've decided to completely format my hard drive, destroying WinXP, and go Ubuntu only. The reason I chose to try Ubuntu now was because WinXP needed a reformat anyways.

So, I am sitting here at my partition table trying to determine how to set this up. I have read some articles talking about placing /home on a seperate partition - so you don't have to reconfigure things after an upgrade. This seems logical to me, and something I'd like to do.

Unfortunately, I don't know enough about Linux to make an educated guess as to how large these partitions should be. My primary concern is: where are applications installed and their configurations (ie. Apache, PHP, MySQL)? Are these placed in /home or are they placed elsewhere?

I read somewhere that '/' should be fine at 10GB - if this is where applications are installed, is 10GB really large enough?

If /home is where my applications and their configurations will reside - here is what I have planned:

78GB Hard Drive
10GB for '/'
67GB for '/home'
1GB swap

Can someone provide their own recommendations? My Install window is impatiently waiting :D

---

### Post by renzokuken on 2006-10-01
your plan is exactly what i have used, around 10 gig for the root partition, (although some would argue u could reduce this alot more) and the rest for /home

its a wise idea to keep them seperate but not essential.

id go with your plan. enjoy Ubuntu!! >_<

EDIT: i just checked my / partition (root) and considering ive installed alot of apps and allsorts of crap on it, ive only used 4gb of it, 10gb should be plenty

---

### Post by bulldog on 2006-10-01
You're spot on :D  the only thing you should concider,how much RAM sticks in your box?

If you have 1GB or more a swap of 1GB is sufficient.

I have a  / of 10GB and it's running for months now,and I installed quit some stuff and have 4,6GB still free.

---

### Post by walesmd on 2006-10-01
Alright - here's what I have, basing this off of work I have done on Windows machines - I assume it is the same here in the Linux world.

Primary Partition (ext3): 9.77GB
Extended Partition: 63.76GB
- Logical Partition (ext3): 63.76GB
Parimary Partition (linux-swap): 1000.07MB

I'm just wanting to confirm that this all sounds good before I click the button - I don't want to kill my only computer and have no way to get help.

---

### Post by walesmd on 2006-10-01
bulldog:
2GB of RAM

---

### Post by bulldog on 2006-10-01
You are doing this with gparted on the install cd??

If so hit apply,if you do this any other way,tell it because you could get troubles when you come to install ubuntu.

bulldog:
2GB of RAM

Should be enough :D

---

### Post by walesmd on 2006-10-01
Yes, using the Partition application off of the LiveCD. Booted to it, double-clicked Install.

Running with it right now - let's see how it works. Thanks for your help once again!

---

### Post by walesmd on 2006-10-01
Another question - now as I think of it. Once I have Ubuntu all installed and booting to it (without the LiveCD), how do I get /home to this new partition? I am assuming all of Ubuntu will be installed to my 10GB Primary to begin with?

Is this an option later on in the install process or something I'll accomplish once the system is up and running.

---

### Post by Fass on 2006-10-01
If you have 2GB of RAM, then I think 1 gig of swap is a bit much. I have 1GB of RAM and I limited my swap to 256mb because I know from experience that Linux in general doesn't swap that much at all - in fact, on this box, the swap partition usage always seem to stay below 10mb.

If you're worried 256 won't be enough, go with 512. 1 gig of swap for a 2 gig of RAM machine is too much, IMHO. Then again, harddrive space is cheap, so it's not like 1 gig is what it used to be...

---

### Post by bulldog on 2006-10-01
> **walesmd said:**
> Another question - now as I think of it. Once I have Ubuntu all installed and booting to it (without the LiveCD), how do I get /home to this new partition? I am assuming all of Ubuntu will be installed to my 10GB Primary to begin with?

Is this an option later on in the install process or something I'll accomplish once the system is up and running.


No you have to mount it when youre partitioning!!!!!!!!!

You mount / 10GB
swap 1GB
/Home   at your desire

But mount it before you hit apply!

---

### Post by walesmd on 2006-10-01
Alright - as I progressed to the next screen I saw that step.

Now, I know what I am about to say is going to make all of you laugh - probably really hard. I even laughed at myself here when I noticed it.

**I forgot I had another hard drive!** :D

So, I'm looking at:
hda: 76GB
hdb: 80GB

I am now thinking of mounting /home to hdb - giving it all of the space and using hda for root and swap.

Are there advantages to creating partitions for /usr, /var? As I said, complete Linux newbie here and I can't find much on what these locations are used for and what the advantage of partitioning them out would be. Would there be an issue with making all of hdb as well as the 63GB from hda mounted to /home?

Finally, I have a ton of MP3s and movies - literally thousands. I remember seeing a /media location as I was messing around on the LiveCD and I assume this is the logical place for this type of data. Maybe leaving my /home on hda and mounting /media to the entirety of hdb is a good idea?

BTW: Your welcome for the laugh - lol. I can't remember the last time I opened this machine up...

---

### Post by bulldog on 2006-10-01
:D :D :D :D :D 

Okay what you say make sense but making /var and so on separate partitions is only for skilled Linux users.

Your /media folder keeps the mounted partitions and cd drives not your mp3's.

That stuff you can place in your /home [it's the only place which belong to you,the rest of the system belong to root]

Now you have plenty of space suddenly:D :D :D you can concider to make a FAT32 partition so you can exange stuff between Ubuntu and Windows.
How large may you decide however.

You can read NTFS partitions and copy data of it,but writing to it is not supported and I shouldn't do so,although there are ways to do it.

---

