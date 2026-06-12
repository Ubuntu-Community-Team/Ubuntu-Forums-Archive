---
title: "Partitioning"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Aurixious on 2007-07-01
I decided that I wanted to try linux and that ubuntu would be the most idiot proof.  I've been trying to install this infernal thing for months.  Every time I try it's always something.  I have xp pro installed and am trying to dual boot.  I have the 6.06 version I believe, and yes I know it's an old version but the 7.xx version gives me errors.  I tried dling it from multiple sources on your web page but it's always the same problem.  So that's why I'm using the old version.  Anyway, I pop the live disk in and i get to the partitioning part but dont know what to do from there.  I know I need to go to the manual setting since the hdd I want to install to has files from xp in it already.  I formated 20 gb to ext3 which I want to dedicate to linux.  Now from reading some posts in the forum I see that multiple partitions are needed? For example /home, /swap, /root.  I've been able to emulate linux virtually on vm worstation, which takes care of all the partitioning for me, and from what I know about linux (which isn't much) those are just files on the same hdd.  Well anyways my problem is that at the "prepare partitons" menu I see the partition I want to use  but it has a sub category with the same amount of space alloted to it.  Not shure what to make of this but I selected the one at the top of the hierarchy.  The next menu is even more confusing since it seems to want to use all my hdds for various "mounting points".  All of the mount points begin with "/media/" which doesn't seem to make sense since everything I've been reading says I need root, swap, home etc.  The only thing I can even make out of this page is the hda1 which is my first hdd; all the others have the sda title followed by some number.  The only thing I can guess that to mean would be sata which is what my other hdd is connected to.  What I want to know is how to distribute the /root etc...  on my 20gb if space without destroying my other data.  Please enlighten a frustrated (that's lightly putting it) customer.

---

### Post by splintercellguy on 2007-07-01
Can't you just select the guided resize option? My knowledge is limited to 7.04 though.

---

### Post by dptxp on 2007-07-01
You need at least 2 partitions, minimum 4 GB for / (root), and 1-2 GB for SWAP.
/home is recommended but optional. By default you store your data at /home.
Else /home resides in /.
You can store data in any partition, even
in Windows partitions (FAT32).

SElect manual partition.
Delete the partition.
Resize the 20 GB to 6 GB for /.
Resize the 14 GB to 12 GB for /home (ext3)
Set rest 2 GB as SWAP.

---

### Post by Raineer on 2007-07-01
Only one partition is **needed** for Ubuntu to run. The rest are just for organizational purposes.  If you want a swap partition (which is recommended, but not 100% required), then you should set aside some space for that. You _do not_ need to have a /home, /root, whatever partitions.  Ubuntu will install 100% fine with your /home and /root directories on the same partition.

As for the /media nomenclature that you see, that is the way Linux refers to the drives. 
**/media/hda1**  is your first IDE drive
**/media/sda1**  is something you might see if you have a SATA hard drive

You don't want to modify any of that, but it is worthwhile to know which drive is which, and which partition goes by which name.  You should be able to determine that from the drive sizes.

Since you already have a Windows partition, Ubuntu should do just fine at setting up **grub** to dual-boot for you with Ubuntu as the default selection (if you don't move the selector at boot-up time).  This can easily be changed later.

---

### Post by Aurixious on 2007-07-01
These are my options:  "/dev/hda: IDE1 master (hda) - 82gb........"
                                      "/dev/sda SCSI3 90,0,0) (sda) 250.1gb.........."
                                      "manulally......"

---

### Post by Aurixious on 2007-07-01
From what i read choosing the first two will completely reformat the hdd.

---

### Post by Aurixious on 2007-07-01
Ok I deleted the ext3 partition and reformatted it as a ext3 partition again but in the process it shaved off 1.32mb as a separate partition (unallocated) and the remaining is "unknown" with a yellow yield sign and exclamation point in the center.

---

### Post by Aurixious on 2007-07-01
Ok this is just ridiculous this is the reason why I never have gotten linux installed on my computer.  I run into a problem try to reference help and get nothing what's the point.

---

### Post by Raineer on 2007-07-01
I would use the manual option (you are correct, the others might format windows) and follow the advice from dptxp. I agree with him, that's probably the best selection for how to format.

---

### Post by Aurixious on 2007-07-01
................................All I get is reiteration, no help.  dptxp's advice seemed promising until I hit another brick wall.  Can you people please read my post and not slap some reply only based on the title of the post.

---

### Post by drowner on 2007-07-01
> **Aurixious said:**
> ................................All I get is reiteration, no help.  dptxp's advice seemed promising until I hit another brick wall.  Can you people please read my post and not slap some reply only based on the title of the post.

i read your post. twice now.

you aren't telling us what the problem is.

---

### Post by Aurixious on 2007-07-01
Ok in the most basic English I know I will RESTATE the problem.  I'm stuck at the partitioning screen where you choose the partition to install ubuntu to.  Now I deleted the ext3 partition as was suggested. I currently have 20 gb  of space that is unallocated which i want to install ubuntu to.  Now if I format it to ext3 again i get an ERROR.  The space turns black and says UNKNOWN. If I double click it it says WARNING:unable to detect filesystem! Possible reasons are: filesystem is damaged, filesystem is unknown to libparted, there is no filesystem available (unformatted).

---

### Post by candtalan on 2007-07-01
Have you used the check CD option in the live CD start up menu choices? It is possible that your image burning is giving errors. The download sites have md5sum information for each dld file. This can be used by your CD burn software to verify that the image is perfect before burn, and also verify it after burning.  

If the CD is perfect at that stage, then if you have problems it is best to check that the CD drive can correctly read the all of the CD in your target machine. The Live CD startup check option will give you a single end result. 

The Installer for 6.06 is ok but the one in 7.04 is improved I find and I prefer it. 

The guided (automatic, or  semi automatic) option is easiest but expects your hard drive to be a single partition of windows. If you have space on the drive, and that space is 'uncommitted' - such as unformatted space (I think) or an unformatted partition, then guided install is again easy. You might like to consider this - in your 20 GB space get rid of any partitions you have created for linux, and create just one partition, leave it *unformatted*. The installer will recognise this and you can choose it in the automatic install choices.

Manual (install) option using the live CD is not difficult, but it is easy to make disastrous mistakes if you do not have a suitable basic understanding of the necessary structures. The minimum is two partitions for swap and /root. The install goes into the /root partition, and all other directories and files hang under /root, including /home. It is easily possible to use separate partitions for some of these directories such as /home, and if you have pre arranged the conditions, this can be used during the live CD 'manual' install.

I trust you have a good backup of your windows data?

Have you considered getting an extra spare HD maybe a small one (8GB?), using it as a slave setting, and using all of it for ubuntu install to get you started?

7.04:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
6.06, 6.10:
[http://www.psychocats.net/ubuntu/installingdapperedgy](http://www.psychocats.net/ubuntu/installingdapperedgy)

hth

---

### Post by Aurixious on 2007-07-01
This doesn't make sense since i just formatted it to ext3.

---

### Post by candtalan on 2007-07-01
> **Aurixious said:**
> This doesn't make sense since i just formatted it to ext3.

What does not make sense? It makes sense if you want to use the automatic install. But not if you are in the middle of a manual edit install.
Good luck.

---

### Post by Aurixious on 2007-07-01
I've tried to dl the newest version of ubuntu from MULTIPLE sources based on this web page and have run into the same problem so I'm fairly sure there is a problem with the source not me.  Also I'm not going to wait another o\hour for a bad copy.  I do have an 8 gb flash drive  but I tried using it some time ago with no luck.  There isn't a problem with the disk I just ran a check and it was fine.  The only thing i want right now is to know what to do after I delete the partition.  By your explanation it would seem as if you want me to set /root, /swap, and /home to the same 20 gb.  I wish to do as the previous post said to do and create partitions for each.  I only want an answer to these things not other methods that don't apply to me.

---

### Post by drowner on 2007-07-01
> **Aurixious said:**
> I've tried to dl the newest version of ubuntu from MULTIPLE sources based on this web page and have run into the same problem so I'm fairly sure there is a problem with the source not me.  Also I'm not going to wait another o\hour for a bad copy.  I do have an 8 gb flash drive  but I tried using it some time ago with no luck.  There isn't a problem with the disk I just ran a check and it was fine.  The only thing i want right now is to know what to do after I delete the partition.  By your explanation it would seem as if you want me to set /root, /swap, and /home to the same 20 gb.  I wish to do as the previous post said to do and create partitions for each.  I only want an answer to these things not other methods that don't apply to me.

You got some unformatted space right?

You want to do it manually?

Format 6gb as / (ext3)
12gb as /home (ext3)
2gb as swap

No methods there. You dont need a seperate /root partition. 

Alternatively, you could leave the space unformatted and do a guided partition into that space. Its really up to you.

Now, this 'black screen' when youre trying to create a new partition worries me. I think you may have clicked something wrong.

---

### Post by Aurixious on 2007-07-01
First it's delete the partition then it's format.  Make up your mind.  You say to format it to X amount of space for home but I can't change the partition size from this app. it's UNALLOCATED space.  I have two options when I right click the unallocated (20gb) space: new and deactivate.  I don't know what deactivate does but I know it doesn't apply to me.  If I go to new that creates a new partition.  It defaults to primary partition, I don't know if that's the problem, the only other option from there is extended partition.  I WILL STATE AGAIN, since you guys still aren't fully reading my posts, I CANNOT RESIZE THE UNALLOCATED SPACE AND IF I FORMAT IT TO EXT3 IT TURNS FROM UNALLOCATED TO UNKNOWN.  After I format it it automatically goes to the next page.  If i click back that's where I see the unknown title for the 20gb partition.

---

### Post by Aurixious on 2007-07-01
I don't know what this "GUIDED" partitioning is but it's not one of my options; AGAIN, I'M USING THE 6.06 VERSION NOT THE 7.04 VERSION.

---

### Post by drowner on 2007-07-01
Dude. Seriously. Relax.

Part of the problem is that you bring up more information as people help you, rather than at the start.

Do you have 20gig unallocated? Yes or No?

If No, make 20 gig unallocated.
If yes.
Click the unallocated space. Click 'New' Make a new primary partition, 6gig. this is / and it is formatted ext3

Next, click some more unallocated space. Make a new extended partition.

Click the extended partition. Make a new logical drive, 12 gig. /home ext3

Click the remaining extended partition make a new logical drive. 2gig swap

Does that make sense?

---

### Post by buuntuu! on 2007-07-01
> **Aurixious said:**
> I decided that I wanted to try linux and that ubuntu would be the most idiot proof.  I've been trying to install this infernal thing for months.  Every time I try it's always something.  I have xp pro installed and am trying to dual boot.  I have the 6.06 version I believe, and yes I know it's an old version but the 7.xx version gives me errors.  I tried dling it from multiple sources on your web page but it's always the same problem.  So that's why I'm using the old version.  Anyway, I pop the live disk in and i get to the partitioning part but dont know what to do from there.  I know I need to go to the manual setting since the hdd I want to install to has files from xp in it already.  I formated 20 gb to ext3 which I want to dedicate to linux.  Now from reading some posts in the forum I see that multiple partitions are needed? For example /home, /swap, /root.  I've been able to emulate linux virtually on vm worstation, which takes care of all the partitioning for me, and from what I know about linux (which isn't much) those are just files on the same hdd.  Well anyways my problem is that at the "prepare partitons" menu [COLOR="Red"]I see the partition I want to use ** but it has a sub category **with the same amount of space alloted to it.[/COLOR]  Not shure what to make of this but I selected the one at the top of the hierarchy.  The next menu is even more confusing since it seems to want to use all my hdds for various "mounting points".  All of the mount points begin with "/media/" which doesn't seem to make sense since everything I've been reading says I need root, swap, home etc.  The only thing I can even make out of this page is the hda1 which is my first hdd; all the others have the sda title followed by some number.  The only thing I can guess that to mean would be sata which is what my other hdd is connected to.  What I want to know is how to distribute the /root etc...  on my 20gb if space without destroying my other data.  Please enlighten a frustrated (that's lightly putting it) customer.

please be patient with the people who are trying to help you! you are not making it easier for them nagging that they don't read your post!writing a 10-line problem description isn't exactly making it easy  to understand what the problem is!

IF i was able to make some sense of your post, i'd say the problem is that you have an extended partition with a logical partition in it (the sub-partition you mentioned). your previous steps were only formatting the logical partition though, leaving the extended partition that CONTAINS the logical one untouched. you would have to deactivate the logical partition first, then the extended partition that contains it can be deactivated and edited.

BUT it seems that you jumped head-first into this without reading up some info on what you were going to do, so
I RECOMMEND you take a close look at [www.psychocats.net]("http://psychocats.net/ubuntu/index.php") which explains the steps necessary for a successful installation in perfect english, so you don't have to run into brick walls with every step you take!
good luck

---

### Post by Aurixious on 2007-07-01
This is not the first time I've said these things......Anyways there is a new problem which is when I try to format the remaining approx 3 gb it says it is not possible to create more than 4 primary partitions.  This doesn't make sense because i want to make an extended partition not a primary partition.  Also, this happens when I click new; I can't even get to the config screen for the partition because of this error.

---

### Post by drowner on 2007-07-01
Why dont you take a screenshot and show us how they currently look?

---

### Post by Aurixious on 2007-07-01
To insert an image i need to have someone host it.

---

### Post by splintercellguy on 2007-07-01
There's ImageShack.us

---

### Post by Aurixious on 2007-07-01
Thank you for the useful link, the first of the day!  If you guys need more pics to help then ask.

[http://img256.imageshack.us/img256/4783/screenshotaf8.png](http://img256.imageshack.us/img256/4783/screenshotaf8.png)

[http://img243.imageshack.us/img243/9070/screenshot2jv7.png](http://img243.imageshack.us/img243/9070/screenshot2jv7.png)

---

### Post by drowner on 2007-07-01
OK!

Now I see!

The thing is the extended partition that you've created should be 14 gig, and go right to the end of the drive.

WITHIN that extended partition create 2 logical drives: one for /home (ext3, 12gig) and one for swap (2gig).

---

### Post by Aurixious on 2007-07-01
New problem:).  at the "prepare mount points" menu I've chosen /, /home, swap.  I can get the / to line up with the 6gb partition but the 12gb and 2 gb partition aren't in the list. I think I remember reading that it limits you to four max. and it want to include my ntfs partitions in there not the newly formed ext3 partitions.

---

### Post by buuntuu! on 2007-07-01
> **Aurixious said:**
> This is not the first time I've said these things......Anyways there is a new problem which is when I try to format the remaining approx 3 gb it says it is[COLOR="Red"] not possible to create more than 4 primary partitions.  This doesn't make sense because i want to make an extended partition not a primary partition[/COLOR].  Also, this happens when I click new; I can't even get to the config screen for the partition because of this error.

i can only repeat: GO FOR SOME KNOWLEDGE BEFORE YOU GO ACTIVE and read the link i posted above, (sorry you don't consider it a useful one)
it perfectly makes sense, 'cause an extended partition is a primary partition which can hold several logical partitions. so: 
either 4 primary partitions
 or 3 primary + one extended partition (with n logical partitions in it)

hat's the max number of partitions  you can put on any hd!

---

### Post by Aurixious on 2007-07-01
I read the part in the link about partitioning and it wasn't useful.  Sorry but one size doesn't fit all.  Anyways this is what a forum is for.

---

### Post by buuntuu! on 2007-07-01
yea, but it really seems you don't know what you're doin and get angry at those who are trying to help!
have you read this [sticky thread]("http://ubuntuforums.org/showthread.php?t=232059"), maybe it will suit you!
many have installed and it is more than likely that someone has encountered the same problems you face!b

---

### Post by Aurixious on 2007-07-01
That was the first thing I looked at.  If I had found my answer I wouldn't be posting here.

---

### Post by Aurixious on 2007-07-01
To update anyone trying help me my current problem is that I've made the partitions but they wont show up on the drop down menu in the "prepare mount points" section.

---

### Post by dptxp on 2007-07-01
You can have only 4 primary partitions on a hard disk. Any space after that goes waste.

So when you make the 4th partition, you make it extended and create logical drives. THe 5th, 6th and 7th too.

Can you just list your partitions in the order you have made ?

---

### Post by Aurixious on 2007-07-01
Ok first partition made was ntfs for xp pro on my maxtor, second was ntfs on my western digital (sata), third was ntfs for vista but I got rid of vista so now it's just a blank partition (western digital), fourth was the ext3 for root (primary)(on the western digital) this one comes up as unknown if i go back from the mounting points page, fifth was ext3 for home (extended)(on the western digital), and I can't make another for swap it gives me the error in the screenshot on the previous page (I want this on the western digital as well).

---

### Post by Aurixious on 2007-07-01
Here's some additional information that may be helpful.  The two ntfs partitions that show up are from my sata hdd.  My ide hdd doesn't even register, but that's ok since it has xp pro installed to it and I don't want to mess with that hdd.

---

### Post by Aurixious on 2007-07-01
Could I put the swap as an extended partition under the partition I made for home which is also an extended partition.

---

### Post by Aurixious on 2007-07-01
I tinkered with it and was able to line up the correct partitions with the correct sizes to /, /home, and swap.  My new question is should I check the reformat box next to /home and swap.  /home isn't checked but swap was checked by default.  If I go back from this screen the /, and swap partitions are set as unknown.  So would a reformat be necessary?

[http://img20.imageshack.us/img20/2724/screenshot3be4.png](http://img20.imageshack.us/img20/2724/screenshot3be4.png)

---

### Post by Aurixious on 2007-07-01
After someone can answer my other question I would like to know why when you go back it lists some partitions as unknown.  No one seemed to address this and this is what has really been bothering me as it seems as if the format i did didn't go through.

---

### Post by Aurixious on 2007-07-01
Ok I just went ahead with it and all seems to be working properly so far.  Will need to see if xp is still bootable but I think I shouldn't have a problem with that.  Also, to help others who may need the information could someone clarify the need to "reformat" and why some partitions turn to unknowns when you go back.

---

### Post by drowner on 2007-07-01
Provided GRUB 'saw' the XP partition during install, it wont be a problem.

As far as the 'unknown' partitions go, i have no idea. It was probably because you were trying to make too many, and hadn't formatted them yet.

gParted WOULD have seen the IDE drive with XP... you just needed to select it from the drop down menu...

---

### Post by Aurixious on 2007-07-01
Just out of curiosity how would I change the partition size once ubuntu was installed?

---

### Post by dptxp on 2007-07-02
> **Aurixious said:**
> Just out of curiosity how would I change the partition size once ubuntu was installed?

Using partition editor like GParted. Practically it may be tough, depends on what you have and what you want.
THe order of partitions matter.

---

