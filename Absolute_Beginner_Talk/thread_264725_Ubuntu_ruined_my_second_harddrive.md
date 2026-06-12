---
title: "Ubuntu ruined my second harddrive"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by carbonic on 2006-09-25
I had the following setup:
hdd0: 1 x harddrive with windows and programs etc. devided into 3 partions.
hhd1: 1 x harddrive with ubuntu, devided into a swap partion, a unbuntu partion and a NTFS partion with all my homemade movies and stuff.

Ubuntu have now ruined the MBR(I think) on the hdd1 harddrive, so I can still access my windows from GRUB, but anything on the hdd1 harddrive is gone. Can't even access my movies from Windows.

How do I save my movies partion on hdd1? I don't really give a **** about ubuntu, it can get it's own harddrive to ruin next time. I just want my movies back.

---

### Post by gn2 on 2006-09-25
This is an illustration of why dual-booting Ubuntu can really hack new users off.
There is no option to install Grub to it's own hard-drive, and so it overwrites the mbr.
Normally the first the new user knows about this is when he/she is in the situation you are in now.
There should be more info/warning during a dual-boot install.
Grub in your MBR is like having a virus.
To remove it you need to run fixmbr. There are a few ways to do this. 
If you've got a windows disc you can use the Recovery mode and run fixmbr, If you don't have this disc there are utilities you can download which will re-write the mbr for you.
I would suggest first trying to put the affected drive in a USB enclosure if you have one and see if you can access it that way.
If you have formatted or deleted partitions on the drive with the movies on you might be able to get them back with data recovery software.

Good luck.

Remember when installing a dual-boot set-up, leave your Windows master disc where it is, but disconnect the Power!
That way Ubuntu can't write a Grubby mess over the mbr.
Then use F8 at boot time to select the hard drive to boot from.

---

### Post by bigken on 2006-09-25
try the usb way 1st its the safest bet

---

### Post by dmizer on 2006-09-25
mbr is only on one drive.  you lost your hdd1 most likely because you overwrote what was there with ubuntu.  that's not ubuntu's fault.  and ubuntu didn't destroy your drive.

did you create a partition for ubuntu?  if so, are you sure that the partition you created is where you installed ubuntu?

can you still boot to ubuntu?  if so, post the output of df -Th.  it may be that the drive is still there, but windows is no longer able to see it.  that's easier to fix than if you've overwritten it with ubuntu.

---

### Post by gn2 on 2006-09-25
> **dmizer said:**
>  you lost your hdd1 most likely because you overwrote what was there with ubuntu.  that's not ubuntu's fault.  

STRONGLY disagree, there are NO warnings during install about this.

For any inexperienced user this is simply not acceptable, there should be warnings.

And warnings on the main Ubuntu website about dual boot installs.
There are none.

I learned the hard way but it's a lesson I won't forget in a hurry...

---

### Post by xpod on 2006-09-25
> Ubuntu ruined my second harddrive

Dont want to dispute a fellow jocks findings......BUT

Sorry,but when i first decided to jump in i found plenty stuff about what the grub does and where it does it....I even read some piece about unplugging your windows drive if you wanted to install ubunto without touching your HDA mbr then re-wrinting your grub menu to include windows.....hence the windows mbr staying untouched...

And they dont come much newer than moi to pc`s...
Ubunto dosent kill harddrives.....people do:D

---

### Post by dmizer on 2006-09-25
> **gn2 said:**
> STRONGLY disagree, there are NO warnings during install about this.
still not ubuntu's fault.  ubuntu is only doing what the user told it to do.  also, ubuntu does infact warn about what it's doing: [http://img130.imageshack.us/img130/2914/w2u325qt.png](http://img130.imageshack.us/img130/2914/w2u325qt.png)

at this point you can cancel the whole operation and things will be as they were before you stuffed an ubuntu cd in the drive.

but even if that were not the case ... in windows, if you had decided to change a drive's formating from fat32 to ntfs, you would be extremely careful about which drive you chose to reformat, and if you were unsure about exactly which drive it was, you'd make sure you knew before you proceeded.  you wouldn't assume that windows automatically picked the right drive or partition.  that's no different here.

ubuntu gives pretty good data about what's on these drives before you format them (better than windows does when you install it).  ubuntu displays the changed archetecture for you to review before you impliment it, and asks you if you're sure the configuration is the way you desire it to be.

---

### Post by xpod on 2006-09-25
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

It`s all just a matter of hunting PRIOR to jumping in

---

### Post by gn2 on 2006-09-25
Aye Xpod but not a' lunes is fair inquisitive lik yirsel,eh, ken?

First thing they ken is when they're up to the sporran in a glaury clabbery mess!

---

### Post by siacs on 2006-09-25
There's still no reason to be spreading fear as you're doing gn2. If someone wants to dual boot, they need to be directed to documentation, not told 'BE CAREFUL! use a second drive', etc. 

The Alternate install CD gives a clear warning and option for GRUB on the MBR. 

[IMG]http://users.bigpond.net.au/hermanzone/p2d/21fat32.png[/IMG]

As with all things new to a user, reading up is essential before jumping in. Not doing so is pure folly.

---

### Post by gn2 on 2006-09-25
> **dmizer said:**
>  [http://img130.imageshack.us/img130/2914/w2u325qt.png](http://img130.imageshack.us/img130/2914/w2u325qt.png)


When this warning is given, the unsuspecting nOOb is well (too far) down the install procedure and may not understand the full implications of the warning which just looks like small print, not a big flashing danger sign.

When this screen is displayed the nOOb is just ONE click away from disaster.

Still think there should be more warnings...
Nothing you say will change my opinion on this.

---

### Post by xpod on 2006-09-25
Fit ye talking aboot?am nae fae aberdeen.um an arbroath smokie by birth, you lunes and quins(?) are too high up fir ma liking..it`s twa cauld up yonder peterheed:D 
Un um a "cock anee" noo..lol:mrgreen:..

Stop it..lol
You`ll hae the poor guy even mare confused with yer waffling:mrgreen:

EDIT:Um awa tae work....happy ubuning people...it`s nae that hard:mrgreen:

---

### Post by gn2 on 2006-09-25
> **siacs said:**
> There's still no reason to be spreading fear as you're doing gn2. If someone wants to dual boot, they need to be directed to documentation, not told 'BE CAREFUL! use a second drive', etc. 

The Alternate install CD gives a clear warning and option for GRUB on the MBR. 

[IMG]http://users.bigpond.net.au/hermanzone/p2d/21fat32.png[/IMG]

As with all things new to a user, reading up is essential before jumping in. Not doing so is pure folly.


Don't think I'm spreading fear. Just giving my view.

Alternate CD's aren't generally what the nOOb uses, and they're not available from Shippit.

Also new user don't know what he don't know, so how do he know he need to read up?

---

### Post by rovernaut on 2006-09-25
One thing I found in my search and experimenting with Linux distros ( A  Linux Newb) and I stuffed up my MBR with grub, but i found that by runninng a Kanotix Live cd and selecting 'Reinstall original MBR'  worked by restoring my Windows MBR, even though I was using another linux distro when I had the problem.
My be ubuntu/kubuntu could incorporate this feature as in Kanotix.

---

### Post by siacs on 2006-09-25
That's hopefully why you and I and all the other more experienced users are here gn2! To inform less experienced users what their options are. Shippit is beside the point.

**Common sense** tells a new user to read up before starting something completely new. Over the years I've seen many tears and hard luck stories. Most of the time the cause is the same, lack of information on the user's part.

Unfortunately common sense isn't always so common. There's not much you can do there but help them pick up the pieces. But if a user comes here asking for direction beforehand, the best you can do is *calmly* direct them to proper documentation.

---

### Post by siacs on 2006-09-25
Mepis also has the MBR restore option last I checked, it may be of help here.

---

### Post by xhaan on 2006-09-25
> **siacs said:**
> That's hopefully why you and I and all the other more experienced users are here gn2! To inform less experienced users what their options are. Shippit is beside the point.

**Common sense** tells a new user to read up before starting something completely new. Over the years I've seen many tears and hard luck stories. Most of the time the cause is the same, lack of information on the user's part.

Unfortunately common sense isn't always so common. There's not much you can do there but help them pick up the pieces. But if a user comes here asking for direction beforehand, the best you can do is *calmly* direct them to proper documentation.


I've always done my research before trying something unfamiliar with a computer... I've done it since I was 8 years old, maybe I was just born that way. :D  I still don't completely understand why users don't do this... I'm not blaming anyone and I try to help where I can, but I just simply don't comprehend what they do sometimes.

---

### Post by nudnik on 2006-09-25
There should be a warning, I agree. Fortunately it is fairly easy to fix. Once you get into DOS one merely types "fixmbr" and all is well.

I boot from two drives, and having GRUB installed to the master is far easier than having to enter the BIOS every time. 

Now if only Ubuntu had a SUSE-like X configuration....yeah:mrgreen: and SUSE used Synaptic...ahh, the world would be a beautiful place. :rolleyes:

---

### Post by slimdog360 on 2006-09-25
> **gn2 said:**
> This is an illustration of why dual-booting Ubuntu can really hack new users off.

Or an illustration of someone who wasn't smart enough to backup their data before doing something like installing another operating system even though its common sense.

---

### Post by gn2 on 2006-09-25
> **slimdog360 said:**
> Or an illustration of someone who wasn't smart enough to backup their data before doing something like installing another operating system even though its common sense.

Actually I did have a back-up of all my files etc, but not everyone does.
And they should be better warned.
Because if they come to do an Ubuntu dual-boot install without the knowledge that they require to have a back-up then they could be turned off Ubuntu for life.
That would be a shame and a loss.

Would you let your small infant children burn themselves so they could learn about the danger of fire?

Or warn them first?

---

### Post by gn2 on 2006-09-25
> **nudnik said:**
> There should be a warning, I agree. Fortunately it is fairly easy to fix. Once you get into DOS one merely types "fixmbr" and all is well.

I boot from two drives, and having GRUB installed to the master is far easier than having to enter the BIOS every time. 

Now if only Ubuntu had a SUSE-like X configuration....yeah:mrgreen: and SUSE used Synaptic...ahh, the world would be a beautiful place. :rolleyes:

What's so hard about pressing F8 then selecting a drive?

I like the easy way for me for that means F8 dual-booting with PCLinuxOS, it has a Control Centre where *everything* can be configured through a GUI, and Synaptic.

It's not for everyone but it suits me beautifully.
As does Ubuntu, single booted on my laptop.

---

### Post by gn2 on 2006-09-25
> **siacs said:**
> That's hopefully why you and I and all the other more experienced users are here gn2! To inform less experienced users what their options are. Shippit is beside the point.

**Common sense** tells a new user to read up before starting something completely new. Over the years I've seen many tears and hard luck stories. Most of the time the cause is the same, lack of information on the user's part.

Unfortunately common sense isn't always so common. There's not much you can do there but help them pick up the pieces. But if a user comes here asking for direction beforehand, the best you can do is *calmly* direct them to proper documentation.



Completely agree.

Perhaps I *am* being too alarmist.

If peole screw up their Windows install, well it'll be a beneficial learning experience for them.

So that's OK then.

Now I'm being sarcastic for which I sincerely apologise, I don't mean to irritate, offend or annoy anyone.

---

### Post by nudnik on 2006-09-25
> **gn2 said:**
> What's so hard about pressing F8 then selecting a drive?

I like the easy way for me for that means F8 dual-booting with PCLinuxOS, it has a Control Centre where *everything* can be configured through a GUI, and Synaptic.

It's not for everyone but it suits me beautifully.
As does Ubuntu, single booted on my laptop.

No worries. Your PC should indeed be configured in whatever way makes you the most comfortable and efficient. 

Just remember...never put a kilt on a penguin, its unnatural and the plaid clashes with the tux. :-$

---

### Post by rickc on 2006-09-25
Yea, I learned this the hard way too back in my early Red Hat days...
I never touched LINUX & I though because I was taking aclass on it, I should install it. I did some reading up on it, but never played with it. I wish lived CD's were more wide spread back then, like they are now. 
Its a pain full lesson to learn & sux dog butt! I feel your pain , really I do.
I would ALWAYS do some research before attempting to format a hard drive. No matter what OS,no warning needed, just plain common sense. I've had windon'ts crap on me and fudge up a HD, but in the end it was my fault, after all computers only do what you tell them. I put the disk in & clicked the button. Once you get your files back [via USB] 
I would read up on dual boots, samba and maybe even [vmware]("http://www.vmware.com/"). I like it better, because I can run windows & Linux & switch back and forth without rebooting & I can access files on both OS's via Samba, but to each his own.

---

### Post by crokett on 2006-09-25
> **carbonic said:**
> 
Ubuntu have now ruined the MBR(I think) on the hdd1 harddrive, so I can still access my windows from GRUB, but anything on the hdd1 harddrive is gone. Can't even access my movies from Windows.


The MBR is different from the partition table and is stored in a different spot on the drive. Overwriting the MBR should not do anything to the partition table.  I am dual-booting XP and Ubuntu using GRUB and can access my windows data just fine from Windows.   Did you rework the partitions when you installed Ubuntu?  Did you  write to the windows drives from Unbuntu?

---

### Post by BLTicklemonster on 2006-09-25
Hey, I know, why not have ubuntu NOT overwrite the mbr on a windows disk at any time for any reason whatsoever until such time as someone decides they really want to do so?

Or not, whatever. Just seems like it would make sense to do it that way if it's such a mind boggler.

---

