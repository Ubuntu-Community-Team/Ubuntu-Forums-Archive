---
title: "I need HELP PLEASE!"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-07
I have looked all over n googled and cant find a clear explaination on how to partition, here is my current status.

Ok I am doing a dual boot install. my windows is already set.

I have three fat32 partitions for windows i think, the smaller of the partitions is 2.93 and i have 1.09gigs left unused that one is hda1 the other two windows parts are hda2 and hda3, 26.39 gigs and 12.17gigs respectively.

That leaves a 14.39 unallocated amount of space. I right click it i get many after i press new. 

it says create as new primary partition, which cannot be changed to logical or extended. it says zero mb free space preceding and new size(mb) 14739 then after that it says free space following(mb) zero.

it says filesystem ext3 but has many options to choose from when i click that box.

so I am stuck as to what to do now i read online linux needs 3 partitions
/root
/home
swap

so how do i do that with the unallocated space of 14739gigs?

i would like to shrink one of the windows drives a little and give ubuntu more space.

but how do i set things up for the partition?

I am so lost...

and second question,

if I have mp3's and other media in my windows partition can Ubuntu read and play them?

---

### Post by aysiu on 2006-06-07
Can you read these two links and then post back here if you don't understand them?
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

And, yes, Ubuntu can read other media from the Windows partition. You'll need to install the proper codecs, though:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by maddbaron on 2006-06-07
ok, I am at the prepare partitions part
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

I dont know how to set up the unallocated 14.39gigs.
I right click it then...

That leaves a 14.39 unallocated amount of space. I right click it i get many after i press new. 

it says create as new primary partition, which cannot be changed to logical or extended. it says zero mb free space preceding and new size(mb) 14739 then after that it says free space following(mb) zero.

it says filesystem ext3 but has many options to choose from when i click that box.
....

I have no idea what to do now...do I keep the new size as is? add anything to the free space preceding or the free space following? what file system do I choose?

I have the three windows partitions which I think I need to change since Ubuntu can read media files in windows as u said I can slowing learn Ubuntu and access my media from windows.

my biggest issue right now is solving the unallocated 14gigs n how to set it up.

---

### Post by aysiu on 2006-06-07
Make sure you read the second link I posted--it tells you a bit about partition planning.

---

### Post by maddbaron on 2006-06-07
ok reading the second link. ok i leave it as ext3. leave windows and its 3 parts alone. I think I have to leave the 14gig alone as one big partition? have no free space before or following right? then click add then forward?

then it should take me to mount where I break the 14gig until 3 subsections? 

am I correct? or do I break the 14gig into 3 subsets in the create new partition box? if so how?

---

### Post by aysiu on 2006-06-07
Can you post the partition table screen up here...? It all seems a little abstract.

When you have it the way you want it, post a screenshot in this thread.

---

### Post by maddbaron on 2006-06-07
This is the partitions window. Sorry if its so blurry I used my phone to take it.

[IMG]http://xs301.xs.to/xs301/06233/screen1.jpg[/IMG]

The 3 green ones are my windows partitions.
/dev/hda1    fat32     2.93gib.
/dev/hda2    fat32     26.39gib         boot iba
/dev/hda3    [COLOR="Cyan"]extended[/COLOR]   12.17gib      lba

The Last one is the unallocated its grey.
unallocated    unallocated       14.39gib
-------------------------------
I right click the unallocated and select new and get this window

[IMG]http://xs301.xs.to/xs301/06233/screen2.jpg[/IMG]
it says create new partition
Free Space Preceding(MB)   [0]                    Create as: [Primary Partition]
New Size(MB)    [14739]
Free Space Following(MB)    [0]                    Filesystem: [ext3]


[check symbol] Round to cylinders                [cancel]   [+add]

---------------------------------------------------------------------
now I don't know how what to do now?

---

### Post by aysiu on 2006-06-07
I'm not seeing an image, for some reason.

It sounds as if you're in a good place, though--creating a new partition as Ext3 (You don't want a separate /home partition? I guess that's your choice). When you get to the next screen (after you've created the new partition), you can select where to mount it and that you want to reformat it.

---

### Post by maddbaron on 2006-06-07
I plugged in the cable line from my dsl modem and took some screen shots.
This is the prepare partitions window
[IMG]http://xs101.xs.to/xs101/06233/Screenshot-1.png[/IMG]

The 3 green ones are my windows partitions.
/dev/hda1 fat32 2.93gib.
/dev/hda2 fat32 26.39gib boot iba
/dev/hda3 extended 12.17gib lba

this is what i get after right clicking the unallocated space
[IMG]http://xs101.xs.to/xs101/06233/Screenshot.png[/IMG]

it says create new partition
Free Space Preceding(MB) [0] Create as: [Primary Partition]
New Size(MB) [14739]
Free Space Following(MB) [0] Filesystem: [ext3]

I dont know what to do?
on a google web find and all over here i see stuff like 
/home
/root
/swap

how do I set those up based on these screen shots?

---

### Post by aysiu on 2006-06-07
I think you just need an understanding of what a "separate" partition means.

First of all, you don't need separate partitions for /home and /root.

I'd advise a separate /home one, but that's not necessary. Swap is its own thing--it doesn't get mounted as part of the file system.

If you create one Ubuntu partition, it will be mounted at /
/ is the top of the directory hierarchy.
Within that partition, there will be folders. /home is one of those folders.

If you create a separate /home partition, and you're in / and click on the /home folder icon, instead of going to the /home "folder," it's a shortcut that goes to a different partition.

So it basically appears as if one partition is inside another partition.

It's sort of like in Windows. If you use a folder a lot like "My Music." If you right-click on it and select **Send to desktop (create shortcut)**, it appears as if there's a My Music folder on your desktop, but it's really just a shortcut to your C:\Documents and Settings\username\My Documents\My Music folder.

---

### Post by maddbaron on 2006-06-07
ok so when it says create new parition just say add(in reference to the second pic?) and it will be ok? and will then install linux in that part i just created? and once installed it will have /home already? i dont have to personally create a root,home,swap to finish installing?

i am so confused..

---

### Post by aysiu on 2006-06-07
At the bare minimum, you'll have to create two partitions--one for / and one for swap.
You must create these on the partition creation screen (where you are now).

After you're satisfied with your changes, there's a separate screen where you can choose which partition to format as /, which to format as /home, which to format as swap.

I've attached screenshots of these two screens.

If you're still confused, maybe you should hold off on installing Ubuntu. Play around with the live CD for a week or two--get familiar with Ubuntu first.

---

### Post by maddbaron on 2006-06-07
ok lemme see if i got this right.

in create new partiton i open that box 3times. or 4times.
the 1st one will be ext3 and say about 500mb with the 14gig moving to the following free space box and nothing being in the preceding free space box.
click ok.

then i create another new partiton by right clicking the 14.50gig. and i reduce that to 12gig's and make it linux swap. I click ok.

then that leaves 2gig's unallocated. then i create a new partiton and and make that ext3 for say 1gig then click ok.

then i do that again for the remaining 1gig unallocated?

then i press forward and assign them as such

"/"

"/root"

"/home"

"/swap"

is that correct?

---

### Post by maddbaron on 2006-06-07
ok that idea doesnt work.

i can only create one more primary partiton according to the install box.

so does it have to be big or small?

---

### Post by maddbaron on 2006-06-07
ok i said ok and got this is it correct?

do i click forward now and leave it alone as "/" ?

---

### Post by maddbaron on 2006-06-07
uh oh i clicked forward and it started installing and i got this message

what do i do?

---

### Post by maddbaron on 2006-06-07
i really have no idea what i am doing. 

it says to create a new parttion i must 1st create a new partition since i can only have 4 primaries how to do create  extended?

do i demount the 14gig ext3 part that was just created?

---

### Post by maddbaron on 2006-06-07
ok i deleted the partition and now i am back to my unallocated space. i went to create new partition and it wont let me make it anything but primary partition. i cant create an extended partition.

so how do i create space for the swap and root?

---

### Post by aysiu on 2006-06-07
When you get to this part, choose for **New Size** 9483. For **Free Space Following**, select 5256. Then click **Add**.

This should give you a primary partition of about 9.5 GB. There should be about 5.2 GB following this as unallocated space.

Then right-click *that* unallocated space and create an extended partition of 5000 MB. Add that as Ext3.

Then right-click that and add an extended partition of 256 MB and add it as swap.

The next screen should allow you to mount the 9.5 GB partition as /, the 5.2 GB partition as /home, and the .2 GB partition as swap.

Let's cross our fingers and hope it works.

---

### Post by maddbaron on 2006-06-07
ok i tried it.





but to no avail :(

---

### Post by aysiu on 2006-06-07
[QUOTE=maddbaron]ok i tried it.





but to no avail :([/QUOTE] Hm. So it creates the Ext3 partition, but the unallocated space becomes greyed out. Damn GParted and its greyed out areas! QTParted does this too sometimes.

I'm going to go on my rant, and you may think I'm crazy, but DiskDrake is the only partitioning tool I've found that works 100% of the time. No stupid greyed out options where there shouldn't be. No weird errors. The unfortunate thing is that DiskDrake is not part of Ubuntu.

I had to download the PCLinuxOS live CD to get and use DiskDrake.

You may think downloading another distro just to do disk partitioning is a bit excessive. If that's so... I'm not sure what to tell you. GParted stinks. I'd say it works about 80% of the time, but sometimes it does... this (what it did to you).

**Edit**: There is one other thing you can try without downloading DiskDrake.

The Ubuntu installer integrates GParted into it, but GParted is a separate application, and I believe it can be run as such.

Close the Ubuntu installer, press Alt-F2 and type ```
gksudo gparted
``` and see if you can create the primary partition, apply the changes, and then create the other extended partitions and apply those changes.

---

### Post by maddbaron on 2006-06-07
it wont let me create and extended.

it says i cant create more than 4 primary's.

when i try to change it to extended it keeps saying primary.

is it possible i should delete the partition of the smaller hda1 which is like 3gb? so i can have one extra slot for an extended? 

after i make that 14 an extended i can go back and make the 3bg a primary again?

---

### Post by aysiu on 2006-06-07
Try whatever works.

To be perfectly honest, I don't even know what the difference is between a primary and a logical partition. I guess that's why I prefer DiskDrake, because it appears to be smart enough to handle that for me.

You could always try making them all extended partitions, I guess--"all" meaning the intended / partition, the /home partition, and the swap partition.

---

### Post by maddbaron on 2006-06-07
I have a kubuntu live cd...should i install with that? and i read i can apt-get the gnome desktop also so i can have that environment and the kubuntu kde environment on the same system?  if so would 14gb be enough?

---

### Post by aysiu on 2006-06-07
[QUOTE=maddbaron]I have a kubuntu live cd...should i install with that? and i read i can apt-get the gnome desktop also so i can have that environment and the kubuntu kde environment on the same system?  if so would 14gb be enough?[/QUOTE] My guess is that you'd run into the same problem with the Kubuntu live CD, but--hey, it's worth a shot.

You can install Gnome on top of it and switch between the two:
[http://www.psychocats.net/ubuntu/gnome.html](http://www.psychocats.net/ubuntu/gnome.html)

And 14 GB is plenty. I have Gnome, XFCE, and KDE on one installation, and I have 2.8 GB used.

---

### Post by Horizon on 2006-06-07
[QUOTE=maddbaron]it wont let me create and extended.

it says i cant create more than 4 primary's.

when i try to change it to extended it keeps saying primary.

is it possible i should delete the partition of the smaller hda1 which is like 3gb? so i can have one extra slot for an extended? 

after i make that 14 an extended i can go back and make the 3bg a primary again?[/QUOTE]
You can only have a maximum of 4 primary partitions on any single hard drive. If you need more than four then you can create an extended partition which takes the space of one primary partition but can house multiple partitions within it. The partitions housed within the extended partition are called logical partitions and you can have as many as you want.

So basically you can have 3 primary partitions and 1 extended partition. Then partition the extended partition into logical partitions. You follow or have I lost you? Basically you can't create another extended partition because you already have 4 primary partitions and an extended partition is a primary partition which would make 5 which is not allowed. An extended partition is like an extension cable. It takes up one plug socket (in this case one of the 4 allowed primary partitions) but gives you many more. All the partition's names that aren't indented are primary.

---

### Post by H.E. Pennypacker on 2006-06-07
Madbarron, for now, let's assume that you're just testing out Ubuntu.  If you are testing it out, there's really no need for a nightmare.  What you do doesn't matter that much.  You are spending a lot of brain power on how much space you should give what, and whether such space will be sufficient.  You shouldn't be doing that.  Don't put your mind in the wrong place to begin with.  What's important is that Ubuntu will be on your computer, and that you will be able to use it.  

Exactly what space is given to what is irrelevant at this point, because it doesn't matter that much for a newbie.  Don't freak out about that.  Any partition you create, with the exception of SWAP, give it at least 2GB.  It doesn't matter how much space you give it, because you're only testing out Ubuntu.  Later, when it becomes a real operating system for you, you can start considering space.

Like I said before, SWAP should be double what your RAM is.  If you have 256 like me, your SWAP should ideally be 512MB.  

What's most important?  Playing around with things until you're very comfortable.  But playing around with things also requires knowledge of what you're doing.  That's why it helps to know the difference between an extended partition and a logical partition, and so on.  

Personally, I learned about all this right from Windows.  I downloaded Paragon Partition Manager and it came in Demo version.  I was able to do everything I wanted to do, but nothing would go into permanent effect, because it was only a Demo version (you have to buy the software before it works).  That made me quite comfortable with partitioning, and it gave me an idea of how things worked.  Test out the waters before you do anything.  

I would say that you should not go with Kubuntu.  I don't like Kubuntu myself, but you may have a difference of opinion.  Kubuntu, I believe, uses something like Disk Drake, which is different from what Ubuntu uses (GParted).  GParted is the best there, in my opinion.

---

### Post by maddbaron on 2006-06-07
ok here's what i have done.

I went in and deleted the original extended partition.

turned the 14gig into a 27gig.

then i made that into a 20gig extended  ext3 and the remaining 7gigs into fat32 so my windows can use it as space(even though it no longer has the lba it used to when i reboot in windows will it recognize it as extra space? I didnt delete the main windows partition just the empty one it was using for space)

so now i have a 20gig extended exclusively for ubuntu with unallocated space. when i right click it lets me create logical partition. how big should that be? and can i create another logical from any left over from the 1st logical partition?

---

### Post by maddbaron on 2006-06-07
so logical partition should be swap and about 2gb's?

what should the remaining unallocated space in the extended be?

another ext3 logical?

---

### Post by maddbaron on 2006-06-07
Is this good?

And when i go forward

can i do this?

/swap-2.53gb
/home-ext3/5.86
/root- ext3/5.48
/boot-ext/5.86  (is that too much for a boot?)

should this work?

---

### Post by maddbaron on 2006-06-07
ok i changed it. the boot i want to be 4gb(still seems like too much)

and i made another 1gb ext3 for the "/"

is that ok?

---

### Post by maddbaron on 2006-06-07
oops made the "/" 2gb instead.

is the boot amount too much at 4gb?

and the 6gb i made a fat32 when i start windows. windows will make it a new windows space right it doesnt have the lba flag it did b4 iu changed it around, will it still be a windows file space?

---

### Post by maddbaron on 2006-06-07
ok one last check before i complete installation
is the 1st picture ok? and are many unknowns in gpart cause for concern?(pics after my last message)

and should i have included the 7gb primary ida4(which i want windows to use) in this or remove it and leave it blank?

---

### Post by maddbaron on 2006-06-07
and one last question.

when install is complete and i reboot.

will the screen give me the option to boot windows or ubuntu or will it boot them both at same time?

---

### Post by aysiu on 2006-06-07
You'll get a choice to boot Windows or Ubuntu.

---

### Post by maddbaron on 2006-06-07
ok now i feel comfortable.

this is how my final install table look like before i click forward is it ok?

---

### Post by aysiu on 2006-06-07
[QUOTE=maddbaron]ok now i feel comfortable.

this is how my final install table look like before i click forward is it ok?[/QUOTE] I'll quote pennypacker on this one: [quote=H.E. Pennypacker]You are spending a lot of brain power on how much space you should give what, and whether such space will be sufficient. You shouldn't be doing that. Don't put your mind in the wrong place to begin with. What's important is that Ubuntu will be on your computer, and that you will be able to use it.

Exactly what space is given to what is irrelevant at this point, because it doesn't matter that much for a newbie. Don't freak out about that.[/quote] I think that's good advice. Just go for it!

---

