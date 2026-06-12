---
title: "rEFIt, Ubuntu, &amp; Snow Leopard - Why don't they play nice?"
date: 2009-09-01
forum: Apple Hardware Users
---

### Post by kphinney on 2009-09-01
First post, long time reader.  Thanks for all of your past and future help.  I hope when I know enough to chime in I can be of as much assistance as ya'll have been thus far.  Anyway, I just posted this over at the Apple Discussion forums, and I'm sure it'll only get me the typical "flash your PRAM" or "erase everything and start over" responses:

I've joyously dual booted my unibody MB Pro since buying it in February with no major issues. I used Boot Camp Assistant to make a partition for Ubuntu and installed rEFIt to serve as my boot loader so I can choose which OS to boot into.

Today I brought home 10.6, Snow Leopard and, following the directions, encountered the inability to install it over my 10.5 partition. My hard drive has the triangle and "!". Following the guidance of another post I attempted to resize my disk and I'm presented with the following:

"Partition Failed
Partition failed with the error:
MediaKit reports no such partition."

Any ideas that don't involve messing up my Ubuntu install?

---

### Post by tubasoldier on 2009-09-02
I've got a similar issue with Snow Leopard and a Linux install.
My log file says that my drive is not bootable. Yet, here I sit in a booted OS X 10.5.8
BTW, I removed rEFIt and there are no changes.

I too am interested if anyone has any ideas.

---

### Post by tubasoldier on 2009-09-02
kphinney

Well I got my mac updated to 10.6
For a lot of people they chose to use the disk utility to move the partition a bit off and then back to the original point. Then click the apply button. No partitions are changed it just rewrites the partition table. For me this didn't work because I didn't use boot camp to install Linux. So I had to remove Linux all together and then use the partition editor to extend my OSX partition to the whole disk. I deleted Linux. 

But it worked and since I rarely boot Linux up on my mac it was a good fix for me.

---

### Post by kphinney on 2009-09-02
> **tubasoldier said:**
> kphinney

Well I got my mac updated to 10.6
For a lot of people they chose to use the disk utility to move the partition a bit off and then back to the original point. Then click the apply button. No partitions are changed it just rewrites the partition table. For me this didn't work because I didn't use boot camp to install Linux. So I had to remove Linux all together and then use the partition editor to extend my OSX partition to the whole disk. I deleted Linux. 

But it worked and since I rarely boot Linux up on my mac it was a good fix for me.

Thanks Tubasoldier.  

Erasing Ubuntu is what I'd really like to avoid.  
(Unless someone can remind me how to backup the user installed packages and settings?)

Wiggling the partition doesn't do it for me.  
Well, more specifically, I cannot wiggle it.  Hitting Apply gives me the above error and my partitions are left unchanged.

Thanks and I appreciate your response.

---

### Post by quailman67 on 2009-09-03
I'm in the same situation- I'm unable to wiggle the partitions. I'm willing to lose my ubuntu partition, but I was not able to do so using disk utility.

Thanks as always for the great advice.


Edit: I've also removed refit, but I'm getting the same error message as kphinney when I try to make any change to the partitions. Ubuntu studio is installed on the linux partition.

Edit 2: For those who may be interested, tomorrow morning I'll try shaking the partition table around with gparted and then see what happens, unless someone here comes up with a better idea first. I'll let you know how it goes.

---

### Post by buttertoad on 2009-09-03
What kind of partition table are you using? If I remember correctly 10.6 requires GUID. How did you install 10.6? 

Snow Leopard worked perfectly for me. I did a fresh install to the partition I had for OS X and then I did a restore from a Time Machine backup. This even reinstalled rEFIt for me, and I didn't need to adjust any settings.

Hopefully with a little more info we can figure out how to make your partitions play nice again.

---

### Post by quailman67 on 2009-09-03
I don't know if this is helpful to anyone else, but I was able to boot off a live cd and run gparted to remove my linux and swap partitions. As soon as I did this I was able to install 10.6 no problem. Disk utility under OS X was then able to stretch my mac partition back to take the whole drive.

---

### Post by kphinney on 2009-09-04
Thanks quailman67 & buttertoad, 
I'll try shaking the partitions using gparted later today.  Just so we're clear - you didn't loose your Ubunto ability Quailman?

Buttertoad - I'm glad to hear it worked for you without any screwing around, but I'd love to know what is different between your machine and mine. 
Intel MB Pro
rEFIt
Ubunto
OSX 10.5.8
Installed OSX then used Boot Camp Utility to resize my partition to allow 40GB for Ubuntu.

All worked well, until now.

---

### Post by buttertoad on 2009-09-04
kphinney, I think the only difference between your setup and mine is I did NOT use boot camp at all. I just set up some free space using Disk Utility in OS X and then I booted from the Ubuntu disc.

Are you running the 10.6 installer from OS X or are you booting from the 10.6 disc? I did a fresh install from the disc then migrated a time machine backup. That might be more forgiving of your partition setup.

Mac partitions can be touchy, I bricked my MBP only two hours after I first got it, but I think we can get it straightened out. The real question is how long do you want to devote to figuring this out. It might be easier to backup your Ubuntu and wipe that partition so you can install 10.6 then reinstall Ubuntu and restore the backup.

---

### Post by Bad Penguin on 2009-09-06
> **buttertoad said:**
> kphinney, I think the only difference between your setup and mine is I did NOT use boot camp at all. I just set up some free space using Disk Utility in OS X and then I booted from the Ubuntu disc.

I believe the problem is that the snow leopard upgrade needs 128MB free space immediately proceeding the osx partition being upgraded.  If you use boot camp to split your partitions you will notice it does this.

A couple of users in this [apple discussion](http://discussions.apple.com/thread.jspa?threadID=2130966&tstart=300&messageID=10137663#10137663) have confirmed this to be the case, for them at least.

---

### Post by wideaperture on 2009-09-11
I had the same problem and found the following CNET article to be extremely helpful.  Sadly, I ended up starting over with Ubuntu, but there are a variety of solutions suggested for people whose kung fu is stronger than mine.

[http://reviews.cnet.com/8301-13727_7-10330520-263.html](http://reviews.cnet.com/8301-13727_7-10330520-263.html)

---

### Post by inphektion on 2009-09-11
i just encountered same error as original poster.  
I am NOT willing to lose my ubuntu partition however.  

I'll keep monitoring threads to see if a real solution shows up.  I already tried the partition thing and repairing the disk etc.  I'm not willing to go crazy with it as the ubuntu side I use 90% of the time.

---

### Post by Bad Penguin on 2009-09-12
> **inphektion said:**
> i just encountered same error as original poster.  
I am NOT willing to lose my ubuntu partition however.  

I'll keep monitoring threads to see if a real solution shows up.  I already tried the partition thing and repairing the disk etc.  I'm not willing to go crazy with it as the ubuntu side I use 90% of the time.
Just out of curiosity, do you have 128MB of free (unpartitioned) space right after your OSX partition?  If not, have you tried booting the snow leopard CD and shrinking the OSX partition by 128MB via Disk Utility?

---

### Post by inphektion on 2009-09-12
no and no.  let me do my clonezilla backup and I'll give that a try I guess...

---

### Post by Yvan Seth on 2009-09-12
I've also just run into this and can confirm that it seems to be all about the partitioning, nothing to do with rEFIt...  When I used the OSX bootcamp partitioner thingy I wondered  what it was up to leaving empty space around, so I resized things during my Ubuntu install to turf the free space it left when preparing for a windows install.  It turns out the OSX installer requires this space! Doh!

After seeing this thread I tried using the OSX disc utility to resize the primary OSX partition, but this failed.

Lucky for me I arranged my partitions such that I had a Linux swap partition between the OSX and Ubuntu ones.  I turned off swap and used gparted to nuke the swap partition (i.e. leave it as a 1GB chunk of unpartitioned space) and now the Snow Leopard install is happy.  I can easilly re-create and enable the swap partition after the upgrade.

So, if you're lucky enough to have put your swap after your OSX partition this is a neat solution.

FYI, the upgrade has not touched my Ubuntu, and rEFIt is still there and working fine.

---

### Post by inphektion on 2009-09-13
when i try to resize my mac partition to have a 128mb piece at the end, disk utility seems to only want it to be 1.07GB at the smallest.  
Also is this supposed to be a mac extended journaled fs?

maybe gparted can make it 128mb, does that support making hfs partitions?

I don't care if i lose my entire hfs mac partition.  I just can't lose my 
/boot -sda3
/ - sda4
/home - sda5

that are right after it.

---

### Post by Bad Penguin on 2009-09-13
> **inphektion said:**
> when i try to resize my mac partition to have a 128mb piece at the end, disk utility seems to only want it to be 1.07GB at the smallest.  
Also is this supposed to be a mac extended journaled fs?

maybe gparted can make it 128mb, does that support making hfs partitions?

I don't care if i lose my entire hfs mac partition.  I just can't lose my 
/boot -sda3
/ - sda4
/home - sda5

that are right after it.
I would guess it needs 128MB _minimum_, since that is what boot camp does when creating partitions, so I assume 1.07GB would work.  On the second question, my OSX partition is mac extended journaled, which is the way it came from the factory...

---

### Post by inphektion on 2009-09-13
yea but if it only needs 128mb I'd hate to give it 1.07GB...
and this new partition is that hfs journaled as well?

---

### Post by Bad Penguin on 2009-09-13
> **inphektion said:**
> yea but if it only needs 128mb I'd hate to give it 1.07GB...
and this new partition is that hfs journaled as well?

Who said anything about a new partition ;)

Can you not boot from the snow leopard CD (hold down c key after powering on), go into disk utility, and shrink the existing hfs partition?  Then reboot and try the snow leopard upgrade?

You can always, after the upgrade is done, boot from the snow leopard CD again and expand it back to get your 1.07GB back...

Wiping the partition and creating a new one means you would lose your existing install (including rEFIt).  Which is exactly what I did, before realizing all I needed was at least 128MB free after the OSX partition, and spending hours re-installing leopard, restoring from a time machine backup, doing the snow leopard upgrade, and re-installing ubuntu.

For future reference I am always going to create a linux swap partition immediately after the OSX partition, so it can just be fdisk'ed away to do upgrades and added back afterwards, avoiding all of this brouhaha...

---

### Post by inphektion on 2009-09-13
I still get that media kit error trying to resize that partition in any way.  I'm doing a time machine backup now.  then i will try formatting only the mac partition.  Doing a clean install of snow leopard and then a restore from time machine which should give me refit back and the ability to boot into the supposedly untouched ubuntu partitions....
sound like a plan?

edit: 
sounds like what i'm doing now is what you did... but if you just format the hfs mac partition, why did you have to reinstall ubuntu?
I don't want to do anything that causes me to lose ubuntu or mess with those partitions.  I'd stay on leopard before that.

---

### Post by tubasoldier on 2009-09-14
Good luck to anyone still trying to update. The issue is in fact a partition error. 

After I upgraded to Snow Leopard I was terribly dissapointed. So many things broke. Fink is very unstable. So I've decided to head back to Leopard. Unless major changes are made I'll not be doing anything with Snow Leopard. I think I'll just bypass this OS X release.

---

### Post by Bad Penguin on 2009-09-14
> **inphektion said:**
> I still get that media kit error trying to resize that partition in any way.  I'm doing a time machine backup now.  then i will try formatting only the mac partition.  Doing a clean install of snow leopard and then a restore from time machine which should give me refit back and the ability to boot into the supposedly untouched ubuntu partitions....
sound like a plan?

edit: 
sounds like what i'm doing now is what you did... but if you just format the hfs mac partition, why did you have to reinstall ubuntu?
I don't want to do anything that causes me to lose ubuntu or mess with those partitions.  I'd stay on leopard before that.

You might want to try using diskutil, booted off of the SL CD, as [posted here](http://www.dawning.ca/tag/snow-leopard/).  I can't recall why I lost my ubuntu install, probably because I lost patience with trying to get SL upgraded and decided to start over from scratch.  It is a new macbook and I hadn't invested that much time getting ubuntu set up yet, so it was not a big deal at the time.

And I re-installed Leopard, then restored from backup, then upgraded to Snow Leopard.  I am not sure how things would turn out attempting to restore a leopard backup to snow leopard...

---

### Post by wideaperture on 2009-09-14
>  I re-installed Leopard, then restored from backup, then upgraded to Snow Leopard. I am not sure how things would turn out attempting to restore a leopard backup to snow leopard...


I also have a new mac and did exactly the same thing.  For the record, though, the CNET article upthread suggests that restoring a Leopard backup to Snow Leopard will work just fine.  But I doubt that SL would quarantine software broken by the upgrade under these circumstances, which is a nice feature of the standard upgrade.  If someone goes this route, report back.  It'd be good to know.

P.S. Turned out none of my software was broken during the upgrade anyhow, so going the roundabout way didn't make any difference.  Probably because I updated all my apps to the latest version before the upgrade.

---

### Post by inphektion on 2009-09-14
> **Bad Penguin said:**
> You might want to try using diskutil, booted off of the SL CD, as [posted here](http://www.dawning.ca/tag/snow-leopard/).  

yep that's exactly what i tried... and i get that mediakit error.  
I think my next try is to format my mac partition altogether and just install snow leopard into the newly formatted partition.  i don't care about losing anything in that partition I just REALLY want to make sure I don't fubar my ubuntu partitions while mucking with this one...

---

