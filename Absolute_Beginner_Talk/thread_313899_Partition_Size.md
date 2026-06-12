---
title: "Partition Size"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Stevo0687 on 2006-12-06
Hey all!  I'm getting ready to set up my computer (Dell E1405) to install Vista and Ubuntu 6.06.  I am going to use GParted to repartition my hard drive to allow me to add Vista and Ubuntu.  I am currently running XP Media Edition.  Currently, and the way the laptop came it is set up for 80 GB for C drive and a D drive back up using 26 GB.  The D drive is completely full, I guess that is the way it is supposed to be.  The C drive I am only using 15 GB right now for XP.  My question is how should I divide up the 80 GB C drive.  I have never used GParted, but from what I hear it will basically push all of my XP together on a partition of whatever I choose and then divide the rest into my other two for Vista and Ubuntu.  I'm thinking about 26GB for each is about even if I divide the 80 GB up.  Is that enough for each?
   I just installed Ubuntu on a project computer in school and when we tried to create a partition for Ubuntu it recognized it as being used and wanted to create its own.  So...do I want to make a partition for the current XP and then use the rest for Vista and when I install Ubuntu I will use a portion of the Vista partition, or when I set the partition for Vista should I create one for when I install Ubuntu in a few weeks. Also, how does the partition for the backup D drive factor in when I use GParted? Thanks in advance for your help.  I'm new to this and have been doing a good bit of research now its time to move ahead.  Sorry this is so long. I wanted to try to get all my current questions out at once.

---

### Post by housam on 2006-12-06
Welcome to ubuntu.
first you have to appoint a separate partition for ubuntu with format type ext3 i.e 10-15G. And another one o.512-1G swap type partition. these two partitions are essential for installing any ubuntu version.
Second, Gparted will resize / create partitions without harming your back-up one. 
Third, you have to defrag your HDD before any partitioning.

Good luck

---

### Post by mo79 on 2006-12-06
Linux needs at least 2 partitions. One is EXT3 for Ubuntu, and one is Linux-Swap. 
Linux-Swap is recommended to be about twice the size of your RAM, so if you have 512MB RAM, make this partition 1024MB (I also think a partition of 1024 is the maximum recommended; shouldn't be more than this). 
Your Ubuntu EXT3 partition can be 26GB (this itself can be divided into further partitions such as /home, but let's keep this default and simple), and XP and Vista can be the same size. They don't need their own swap partitions. These partitions will be NTFS.
You only need to resize the XP one as it already exists. I don't know how to install another Windows on the same disc without affecting the other, so I hope someone else can help with that. It'd be better if you just upgraded XP to Vista?

In total you'll use approx. 79MB in the above example. But you have to factor *actual* disk space (as hard discs aren't exactly the written amount) and of your course your Linux Swap.

Don't worry too much about decisions. As you can resize/delete partitions later with GParted.

GParted will only look at Drive D if you point it look at that. And indeed defrag your disk first.

---

### Post by lemonsCC on 2006-12-06
As far as I know Vista ***_REQUIRES_*** 20gb minimum.  so I would start from there.  Are you planning on making a seperate /home partition?  (I would, it saves tons of grief)

---

### Post by Stevo0687 on 2006-12-06
Alright, lets see if this will make things simpler for me starting off since I've never used GParted.  Can I set XP to use 26 GB and set Vista to the rest (minus the backup)and worry about setting the 2 other partitions later when I'm ready to install Ubuntu. (so resize the Vista partition later and make is smaller so I can use some for Ubuntu)   Or will the whole process be easier if I do all my partitioning at once.  I don't plan on installing Ubuntu for at least a week and probably a little later than that.  Thank for all the help so far.  And I have run defrag.

---

### Post by housam on 2006-12-07
Do the partitioning for vista first to see how things goes on, then afterwards you can repartition for ubunto.
**IMPORTANT:**while defraging windows partition try to locate the green mark (the unmovable data)which is windows system files and i.e. if it is in the middle of the partition , be careful not to shrink the partition to behind that limit or you will damage your windows system files.
For Gparted , it is on the live CD .  set your computer to boot from the cd-rom then insert the CD and click system >> admin. >> Gnome partition editor.

---

### Post by Stevo0687 on 2006-12-07
Well, I ran defrag again to see where the free was.  It is fairly far to the left but I don't know exactly how much space I  have to work with.  I was hoping to set XP in its own 26GB partition now and use the rest for Vista and when I am ready for Ubuntu I'll use part of the Vista partition and leave XP alone.  Here is a screen shot of my defrag complete.  I would be using 26 GB and this spectrum shows 79.18GB so I was wondering if someone could tell if that looks like I'll be safe or not.  I can go 30 if I need to and make Vista or Ubuntu a little smaller if I have to.  I just wasn't sure if that blue can be "pushed" to the other side to fill in the gaps and just the green has to stay or how that works.  Thanks again so much for all the help.



[img]http://i70.photobucket.com/albums/i110/83turboranger/screenshotdefragment.jpg?t=1165510358[/img]

---

### Post by housam on 2006-12-07
It seems that you can shrink windows partitions to a minimum of 32-33G (26% of 120G HDD), To be safe 35G is ok.
No worry about the blue data , it'll be transfered during resizing.
Do the shrinking step first and after that reboot and test your windows,then complete the partitioning steps.
You can read [this thread]("http://www.ubuntuforums.org/showthread.php?t=312439&page=3&highlight=PARTITIONING").
Good luck

---

### Post by Stevo0687 on 2006-12-07
Alright, I repartitioned to give XP its own smaller partition.  I have 45 GB unallocated that I wanted to use for Vista.  I assume I then create a new partition and set that to be ntfs.  

Here is what the screen shows for what partitions I already have.  I know that the "/dev/sda2" is what XP is on and the "/dev/sda3" is my backup drive.  I don't know what the sda1 and sda4 are.  Does anyone?  
[img]http://i70.photobucket.com/albums/i110/83turboranger/gparted.jpg?t=1165550315[/img]

When I try to create a new partition using the unallocated 45 GB.  I get: "**It is not possible to create more than 4 primaary partitions**
If you want more partitions you should first create an extended partition.  Such a partition can contain other partitions.  Because an extended partition is also a primary partition it might be necessary to remove a primary partition."

My question is, what do I do about this?  Can I delete the sd1 or sda4??  I know Mo79 said that XP and Vista don't need their own swap but is one of them the swap for Windows?  Or do I make one of these an extended partition?  

Thanks so much for your help, Housam.  Anyone else, feel free to chime in!

---

### Post by housam on 2006-12-08
I see that you have about 5 G used in drive sda4 , check about the contents of that drive before deleting.
if it is something important to you ,you can transfere it to windows drive and then delete it through Gparted to get an unallocated space of about 50G.(ignor sda1 it's very small).
Now you've 3 primary partitions.point for the unallocated space (the 4th primary partition)and change the creation type to extended partion. It will create an 50G extended partition.
Now you can devide the extended partition to many logical partions and choose the format as you want to use i.e. ntfs, fat32, ext3 or swap.

---

### Post by Stevo0687 on 2006-12-08
Alright, sounds good. But I don't know how to tell what is on the sda4.  How do I find out what is on that?  I went into GParted and all I was able to find it that it said "unmounted" I don't know if that means anything or not.  What else can I do to find out what to do w/ it?  If it is important do you mean to put it with the XP partition or the Vista?  I'm guessing with XP but I thought I'd check. Thanks.

---

### Post by housam on 2006-12-09
Did you checked it under win-xp? can you see it when you open my computer as a separate partition?
It's a fat32 type file!,it should be seen under win-xp.
If you get able to check it, then transfere the contents to the win-xp partition.

---

### Post by Stevo0687 on 2006-12-09
I don't see it under Win XP.  Should I be able to see it in My Computer w/o going into anything?  When I open my computer I do not see a third partition.  Only the C drive and my D drive (backup) and then my documents and shared documents and my DVD drive, Bluetooth places and my printer.  Is that where I should be looking?

---

### Post by housam on 2006-12-09
Yes, but it is strange to have partitions that you didn't create and can't see in my computer!, any way leave sda4 till we can recognize it.
let me ask if you noticed these two partitions before shrinking the win-xp one?
what was the figure after opening Gparted for the first time?

---

### Post by Stevo0687 on 2006-12-09
Uh, I wasn't looking for them.  But I believe they were there.  If they weren't I think I would've noticed if I only had 2 partitions and then had 4 plus the unallocated space afterwards.  I'm pretty sure they were there before, but not possitive.

---

### Post by housam on 2006-12-09
Ok,go for all programs >> accessories >>  system tools >> system information >> components >> storage >> drives and then disks to check if windows is recognizing all the partitions.
Also go for all programs >> accessories >> command prompt and type:CHKDSK to see if every thing is ok with the C drive.

---

### Post by Stevo0687 on 2006-12-09
Well, I'm not sure exactly what I'm looking for on either.  Everything appears fine, to me, under System Informations, but under the command prompt I get a warning and errors found.  What does this mean? 

Here is what I got: 

[img]http://i70.photobucket.com/albums/i110/83turboranger/checkingpartions.jpg?t=1165725125[/img]
[img]http://i70.photobucket.com/albums/i110/83turboranger/checkingpartions2.jpg?t=1165725447[/img]

---

### Post by housam on 2006-12-10
It's strange too ! you have two drives C & D from 4 partitions.
You have two hidden partitions which I don't know how to deal with it.
Also you have some errors in your HDD conserning deleting some files.
I would advice you to see your DELL computer agent to clarify the situation of the two hidden partitions and also to fix your HDD.

---

### Post by Stevo0687 on 2006-12-10
So something is broken or just wrong w/ my Hard drive?  And it has to do with deleting some files?  Is that probably something I did?  Either way, I guess I'll give Dell a call.

---

### Post by rsambuca on 2006-12-10
A lot of the Big Box computers like Dell, HP, Compaq, etc. have these small partitions on them for recovery system files and stuff like that.

---

### Post by housam on 2006-12-11
It could be , but he already has a recovery partition. and also why they are hidden? something is wrong with that HDD.

---

### Post by Stevo0687 on 2006-12-11
When you say something is wrong w/ that HHD do you mean it was bad from the factory or something went bad?  I have a warranty for it though.  And I have backed up my files for this project so if I have to get it repaired or an new HDD I guess I'll be alright.

---

### Post by rsambuca on 2006-12-11
I don't think anything is wrong with the drive.  As I said, that is usually big box computer manufacturers putting stuff on the PC.  Mine has it as well, as well as a bunch of my friends whose I have checked as well.

---

### Post by Stevo0687 on 2006-12-11
> **housam said:**
> something is wrong with that HDD.

Well, thats what he said.

---

### Post by Stevo0687 on 2006-12-11
Actually, I ran CHKDSK again and this time I got:
[img]http://i70.photobucket.com/albums/i110/83turboranger/checkingpartitions2.jpg?t=1165874913[/img]

I figure I should probably run it with the /F (fix), but thought I'd check.  I didn't get that option before. Thanks.

---

### Post by housam on 2006-12-11
Now it looks OK , nothing wrong in drive C:, but we still unable to create the expanded partition as long as we can't delete sda1 or sda4 because we don't know the contents of them.
As rsambuca said it might be some stuff on them related to Dell company. You can't delete any of them untill you ask Dell.
I have a new HP laptop with only one drive E: as a recovery partition,no other hidden partitions, so I partitioned dive C: the same way as I described to you and got a clean install of Dapper.

---

### Post by Stevo0687 on 2006-12-11
Alright, well that makes my question for Dell easier.  Do I not need to run that CHKDSK /F (fix) then?

---

### Post by housam on 2006-12-12
No, no need to run CHKDSK /F any more. only one of the hidden partitions (sda1 or sda4)we need to delete after transfering its data.

---

### Post by Stevo0687 on 2006-12-13
The more I think about this the more I wonder if I should just upgrade from XP to Vista.  Will this transfer all my files and info, such as iTunes and all my songs?  I beginning to think that would be better.  Has anyone else used Vista yet?  Do you think it is safe or should I keep XP as a backup.  If I would though, wouldn't I have to transfer all my files manually?  

I still want to know what the other 2 partitions are and delete what I don't need or include it in the Windows or XP partition.  

Thanks.

---

### Post by rsambuca on 2006-12-13
Yeah, I am trying Vista as well (RC2, build 5744).  I currently have 6 OS's on my PC for some silly reason.  XP, Vista, ubuntu 32 bit, ubuntu 64 bit, and Sabayon 32 bit, and Sabayon 64 bit.  I use ubuntu 32 bit and XP the most.  

My personal feeling on Vista is to wait a bit if you are on a work/production machine.  Some things still do not run very smoothly due to driver issues.

I will probably not make a full move from XP to Vista until the first Service Pack comes out (unless I just go with linux entirely by then!).  As far as those weird unknown partitions - I have left mine untouched, just-in-case.  My machine came with Windows MCE pre-installed, so I don't have the full install disks, just these stupid recovery disks.  I am not sure if I need the info from those other partitions if/when I do another re-install/recovery of XP.

---

### Post by housam on 2006-12-13
> **rsambuca said:**
> Yeah,   As far as those weird unknown partitions - I have left mine untouched, just-in-case.  My machine came with Windows MCE pre-installed, so I don't have the full install disks, just these stupid recovery disks.  I am not sure if I need the info from those other partitions if/when I do another re-install/recovery of XP.


The problem is he can't create a partition to install ubuntu untill one of these two weird partitions deleted.I don't know if he used the recovery disk , they will disapear or not.
he should ask Dell about that.

---

### Post by Stevo0687 on 2006-12-13
I am also running XP MCE.  It came preinstalled and I got absolutely no disks for Windows.  I'm in my first semester at college and have a final Friday and one Monday, that is why I haven't called Dell yet to find out about the partitions.  It sounds like I should keep XP though which isn't a problem.  I don't want to go to Vista only and not be able to do certain things in it that I could do in XP.  

My Ubunto 6.06 LTS CDs came today.  So once I get my partition problems all worked out and Vista installed, I'll be ready to attack that.  

Do either of you use iTunes?  I was just wondering when I switch to Vista, will I be able to put iTunes or atleast the songs on a DVD and transfer them or do I have to load them into Vista all over again?  I have almost 3 GB of music and am currently adding and didn't know if I should hold off on adding more until I have Vista up and running.  Thanks.

---

### Post by say592 on 2006-12-13
Ouch! XP, ubuntu, and vista on that small of drive? I recommend upgrading to vista not tri-booting, Email them and ask them what the 26gb is for, I have a computer that the small one is for backups, auto backups, and can be formated! Try that, remember, you are gonna want 15gb for vista, thats the minimum, ubuntu should have 5gb if I remember correctly, and xp uses about 7gb.........

---

### Post by Stevo0687 on 2006-12-13
Doesn't seem that small to me especially when you say how much each needs.  Sounds like I have plenty.  Are you missing something or am I?  I'm working with a hard drive thats about 100 GB, about 80 that isn't being used by my back up.  With the specs you gave as minimum there is still 53 extra GB so I could make all of them significantly larger.

---

### Post by housam on 2006-12-14
> **Stevo0687 said:**
> 

Do either of you use iTunes?  I was just wondering when I switch to Vista, will I be able to put iTunes or atleast the songs on a DVD and transfer them or do I have to load them into Vista all over again?  I have almost 3 GB of music and am currently adding and didn't know if I should hold off on adding more until I have Vista up and running.  Thanks.
No, I'm not using iTunes. But I think that you can see your music files on xp while running vista ( same software source ) and also you can transfere it. we can do that between xp and ubuntu.

---

### Post by Stevo0687 on 2006-12-14
Alright, thanks housam.  I guess I'll keep uploading my songs to XP and deal with it when I get Vista. Thanks.

---

### Post by Stevo0687 on 2006-12-14
Alright, I called dell.  The man said that the 47MB partition is for utilities and diagnostics.  He said the 5GB is for the PC restore.  That has everything if I need to restore my computer to factory standards.  I've used that before when I first bought it an had a problem.  I just push ctrl + F11 and it restores everything.  

So do I transfer the 5GB system restore to the XP partition?  Will that hurt anything or will it still be functional?  Should I transfer the utilities partition there also so I have 1 less partition or should I leave it alone.  I know you said once I get down to 3 partitions I can create a 4 that I can split up for Vista and Ubuntu correct?

---

### Post by rsambuca on 2006-12-14
Most, if not all linux distros will play nice and can live in separate logical partitions within one larger extended partition.  I am not sure if Vista will live within a logical partition.

As far as the iTunes stuff goes, I am not sure how you have it set up to save your files, but you can probably configure it to use the same directories in both XP and Vista.  For instance, I use Firefox and Thunderbird, and I have set up the profiles to use the same  directories in both XP and Vista, so that no matter which one I am using, all of my bookmarks and cookies are the same in Firefox, likewise for my email in Thunderbird.  You can actually set it up to have the same shared system including linux distros as well, if you use Fat32 or some of the beta drivers.

---

### Post by housam on 2006-12-14
Yes , it is correct. so, what about transfering the data of sda1 (47Mb) to xp partition? there is no harm doing this move, but how we can do it if we can't see it ??
Another way . if we gonna use sda4 for restoring xp to factory sittings, there is no need for the recovery one (26Gb):-k 
my openion is to leave sda4 as it is for restoring xp when needed and find a way to transfer data from sda1 to sda2. then we can proceed for partitioning and installation.

---

### Post by rsambuca on 2006-12-14
Do you have a Dell System Recovery program folder in XP?  I have an OEM Cisnet System Recovery program folder on my machine.  I used to have those two extra partitions like you, but I think in the recovery program I used an option to create recovery media (CDs), which mysteriously made one of those extra partitions disappear.

---

### Post by Stevo0687 on 2006-12-14
> **housam said:**
> Yes , it is correct. so, what about transfering the data of sda1 (47Mb) to xp partition? there is no harm doing this move, but how we can do it if we can't see it ??

I can see it in GParted. Thats all I need to be able to see it in to transfer it, correct?  Can't I just transfer it in GParted to the XP partition?   I really don't see a need to keep the 26GB backup either.  It seems to be working with a Norton Recovery system, which was a trial and expires in 5 days anyway.  And every time it tries to back it up, it says that the disk is full.  

So I guess I should move the utilities (sda 1) to the XP (sda 2) partition and then delete the 26 GB?  How does it work transferring sda1 (fat16 file type) to sda2 (ntfs file type)?  

rsambuca, is the setting up of the iTunes directories something I can deal with once I get Vista and even Ubuntu installed?   I also may want to do that for Firefox like you do so that my favorites will be shared.  

I couldn't find the Dell System Recover, but I could just not be looking at the right place.

---

### Post by housam on 2006-12-15
You can change the format type through Gparted, but be sure if it can be done without deleting the contents. also from windows command prompt >> convert after pointing to the required partition.

---

### Post by Stevo0687 on 2006-12-17
So I transfer sda1 to sda2...do and change sda1 to ntfs and it should still work?  Also, how do I know for sure if changing th eformat will delete the contents or not?  

What is the Windows command prompt thing?  Is that a way to transfer sda1 to sda2?  If it is, I feel safter transfering Windows patitions with a Windows program, but I'm not quite sure what your're talkng about.

---

### Post by housam on 2006-12-17
Before changing the format type there will be a warning message telling if that action will delete the partition contents or not.  

In the windows command prompt, type : HELP . You will see all the command orders that you can use to achieve specific tasks. I can't see one for transfering data from a partition to another.

---

### Post by Stevo0687 on 2006-12-20
Alright, I went in to GParted and tried to move things around and couldn't.  I am able to change sda1 to ntfs with no problem and even changed it back, but the program doesn't have the capablities to move ntfs files.  It says it can move fat 16 files like it is, but I can' t figure out how and even if I do I didn't know if I need to change it to ntfs ahaed of time or if it will do it for me.  Does anyone know how to do this in GParted or can you recommend another freeware program or tell me how to do it in windows.  I wasn't able to figure out how to do it in windows.

---

### Post by housam on 2006-12-21
As I told you that I don't know a way to transfer files through a partition tool and I think it is not possible to do it that way.
Any way, to solve this situation you have to call Dell again consulting them about deleting either sda1 or sda3. I think this is the best way to have a free partition.

---

