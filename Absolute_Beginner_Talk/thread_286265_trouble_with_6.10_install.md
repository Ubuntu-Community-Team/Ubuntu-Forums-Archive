---
title: "trouble with 6.10 install"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by ride1226 on 2006-10-27
hi guys and this will be my first post here...i recently have decided to make the switch to linux on my pc and currently have windows xp. i have a 200gb hdd so i decided ill duel boot ubuntu and get used to it and set it up but still game on windows. i have downloaded and correctly made the install cd. im currently running the live cd with no problems. i tried to install via the icon on the desktop but am runnin into problems. probably just my lack of knowledge. but anyways i get to the step where it will add a partition to the hdd and u can select how big u want it to be. my problem is it just stalls when i click next. id like to set it up with 50gb for linux and 150 for my windows. any advice on installation. i tried to u gpart? or w.e its called to make my partition but it had an error resizing the windows partition so i could make a 50gb linux part. thanks guys sry if thats confusing.

---

### Post by whizbaby on 2006-10-27
Please resize the windoze partition with a windoze-tool because ntfs-support is still beta (not officially released). You others correct me if I'm not up to date.

---

### Post by ride1226 on 2006-10-27
that was my next thought thank you very much. does anyone have any idea of a program i can use in windows to do this? links well appreciated. currently in class right now so i dont have my pc. but ill give w.e a try when i get home. thanks.

---

### Post by whizbaby on 2006-10-27
Once upon a time I used windows and there was a prog called partition magic (unfree I think, was on the driver cd of a mainboard). If you resize a hd  better be sure to backup your data (what you should already have done before starting to try. Have you?).

EDIT:
BTW what happend to upper cases? Most keyboards have a shift key right above the ctrl...(used to improve readability)

---

### Post by ride1226 on 2006-10-27
sorry about the no uppercases i only use them when writing formally lol becuz i try to type fast. im sorry. but yea neways i didnt back nething up becuz i was in such a hurry to get back on ubuntu and get it set up. not too big of a deal though i only rly have media which is all on my ipod and maybe a few pictures. but when i go home i will back everything up before tryin to resize my partition. ill google partition magic that is if anyone else doesnt have other programs or ideas. thanks for the responces guys i can see this is a great helpful community.

---

### Post by Henry Rayker on 2006-10-27
I know for a fact that Partition Magic isn't free. I don't know of a free tool to do it from within windows.

---

### Post by ride1226 on 2006-10-27
well im home from class now and i got partition magic and boot magic. im in the process of installing them and backing everything up. someone on here said something about multiple partitions...dont i just make a windows partition and a linux partition? man this is confusing cant wait till i understand it all so i can just completly make the switch. thanks for the help.

---

### Post by chuckyp on 2006-10-27
Well basically just resize your windows partition and leave free space on the drive for ubuntu.  The installer will let you create multiple partitions out of the free space if you want.  Like I have /home on its own partition that way if I switch distro's or multiple boot distro's all of my files are saved.

---

### Post by ride1226 on 2006-10-27
im at step 5 of 6 on the live cd installer right now. i have ran partition magic and resized windows and left 40gb open for linux. right now i have an icon that says 

No mount point selected for Partition 1 Disc IDE/ATA 1 (Primary) [hda1].
No root file system


i dunno what that means. or what to do from here. but im at that step

---

### Post by ride1226 on 2006-10-27
anybody gimme a hand here...im on the live cd right now. i dont wanna mess up my 150gb partition with windows on and im not sure what to do.

---

### Post by ride1226 on 2006-10-27
hmm becoming vry frustrated now becuz i cant even rly browse the internet. firefox keeps closing out on me if i go to lets say myspace.com or break.com i dunno whats goin on id like to get this installed so i can work out the bugs but its rly frustrating for a first timer.

---

### Post by whizbaby on 2006-10-27
I guess you are in a window where on the left are listed drives and mount points and on the right you can select if you want to format. You can create a mount point (directory where the drive will be accessible later) for hda1 if you want and you *have* to mount one partition (the root) as mount point '/'(right, just the slash).

---

### Post by ride1226 on 2006-10-27
yes. im at that screen but isnt my 160gb hda1 my windows partition?  and then there are two more choices below it. god this is confusing.

---

### Post by ride1226 on 2006-10-27
anybody? i just wanna get this thing installed and then start learning and customizing it to be an OS for me. right now im just stuck here wit gaim. cant listen to music or browse the internet cuz firefox crashes w.e i go to a flash site.

---

### Post by whizbaby on 2006-10-28
Don't get confused. Yes, your hda1 is most likely to be the windows partition. If you want to access it from your linux system you have to specify a mount point (if not don't, won't matter to the system), e.g. /media/hda1 or /media/windows. Mounting a drive wouldn't change it at all. So as long as you don't set the mountpoint of hda1 to '/' and you don't check the little box to format it the data (and dozer) will remain.
I guess the installer made a root and a swap partition. Select the (ca 50 gig) partition to be formatted and mounted on /.
(sorry for being away nine hours but I was sleeping (live in europe))

---

### Post by cjm5229 on 2006-10-28
I have never had success using the partioner in the install part of the live cd. I have found if you use the the gnome partioner in system>administration on the live cd first you can successfully partion the HDD. Then run the installer. Choose the manual partioner, skip past the partioning section, choose the partions you are installing to. and install. Hope that helps.

---

### Post by ride1226 on 2006-10-28
ill give that a try whizbaby.thank you. im currently gaming so im on windows but later on ill see how that works. so basically my hda1 150 gig will be mounted as /media ? is that an option. then my 50 gig partition that i want linux on will be just / ? thats all i need? and then it should install...i didnt use the installer to partition i used partition magic on windows to do it. vry simple. thanks for the help.  next ill be back here to figure out why my firefox keeps crashin w.e i go to a flash site.

---

### Post by ride1226 on 2006-10-28
im on the live cd now and this is what i have.

step 5/6
 
/media/hda1      150gb     partition 1 disk IDE/ATA (primary)[hda1]
/                40gb      pertition 5 disk IDE/ATA (logical)[hda5]

reformat isnt checked on either of the. and what it tells me when i click next is 

! No Root File System


what i dont get is why it says thats a 40gb partition when i partitioned it to be 150 and 50gb. and this is where i stand. thanks.

---

### Post by ride1226 on 2006-10-28
also if there is anyone who could give me some like live help via aol instant messenger thatd be great! thanks guys

---

### Post by ride1226 on 2006-10-28
is there any reason why i dont get responses? have i broken rules or somthing. this is killin me here im about to just stick to windows cuz i cant figure this out.

---

### Post by MySweetTedy on 2006-10-28
I have the same problem as ride1226, here what i did, i am at windows XP, i have made 2 partitions of my disc for linux, one is 8 GB the other one is 2 GB, for Root and for SWAP, cause when i start installing the new ubuntu it asks me for a min of 2 GB for Root and 256 MB for Swap, when i reach the part for mounting i set the 8GB disk (hdd6) to "/" and check on the reformat box, and swap to the 2 GB disk (hhd7) also with check at the reformat box, and i still get the msg "! No Root File System"

i will be very greatfull at some help here

---

### Post by ron999 on 2006-10-28
Hi ride1226
You haven't broken any rules.
Sometimes it takes a while to get a response.](*,) 
Forum users are in different time zones.
Hang on in there.8)

---

### Post by whizbaby on 2006-10-28
> **ride1226 said:**
> ill give that a try whizbaby.thank you. im currently gaming so im on windows but later on ill see how that works. so basically my hda1 150 gig will be mounted as /media ? 
Not exactly. The default is /media/hda1, you can change it (if you want).
> just / ? thats all i need? 
No, you need a swap partition (virtual memory) approx twice as big as your physical RAM (recommended).
EDIT:
to 2x(physicalRAMsize) rule: it's only a recommendation (to speed up transfer I think).

---

### Post by MySweetTedy on 2006-10-28
i have 1.5 gb ram, are u sure i need 3 gb swap part(i have left 2gb right now)?

---

### Post by ride1226 on 2006-10-28
well i have a gig of ram so i should do two gigs for the swap partition. i guess il try to use gpart to make my new partitions if not i gotta go back to windows. ill give it a try.

---

### Post by ride1226 on 2006-10-28
ok so i went back to windows to use partition magic and set up my harddrive again. heres what i made. i made a 150gb partition for my windows. then made a linux ext3 partition of 38 gigs. and a 2 gig linux swap partition. now i am at the setup again stuck on step 5 and its telling me no root file system.

what am i doing wrong?

---

### Post by whizbaby on 2006-10-28
If you have

-a swap partition 
-an ext3 partition mounted at point /

ubuntu should install. If not, something goes wrong (CD broken, non-standard APIC on mainboard?).

EDIT:
to 2x(physicalRAMsize) rule: it's only a recommendation (to speed up transfer I think).

---

### Post by ride1226 on 2006-10-28
im on a standard dell pc...nothing done to it besides bigger hdd and ram. its a dell 4600c. dunno why that would affect anything i dont think they use a weird mobo.this is how my install screen reads.

/media/hda1   150gb   partition 1 disk IDE/ATA (primary)[hda1]
swap          2gb     partition 6 disk IDE/ATA (logical)[hda6]
/             38gb    partition 5 disk IDE/ATA (logical)[hda5]

and then there is one blank space not filled with anything. and the reformat box is checked on the swap partition. still says no root file system.

---

### Post by whizbaby on 2006-10-28
I don't exactly know, but trying to create an ext3 filesystem in a windows extended partition may be the cause of the problem. Try without embedding in the extended partition.

EDIT:
Ignore above if you already have a seperate extended for linux

---

### Post by Zeke73SG on 2006-10-28
It seems that other people are having this problem and the best advice I can give you is to install 6.06 instead. If this is your first linux experience try Dapper, I've been using it for a couple months and I'm not about to tackle Egdy, not yet.

---

### Post by ride1226 on 2006-10-28
ok. so i figured the same thing and got out my 6.06 live cd....im runnin it now and go to install...get to that step and hey looky there same error.im gettin...

No root file system.

i have it setup so its mounted to my windows partition and then / is at the 38gb partition and swap is on 2gb partition just like before. i dont get it.

---

### Post by adriantry on 2006-10-29
> **ride1226 said:**
> ok. so i figured the same thing and got out my 6.06 live cd....im runnin it now and go to install...get to that step and hey looky there same error.im gettin...

No root file system.

i have it setup so its mounted to my windows partition and then / is at the 38gb partition and swap is on 2gb partition just like before. i dont get it.

Hi - I'm posting this from the Edgy live CD, and I'm having the same problem with the same error messages.

I believe there is a problem with the live CD installer.

I'm trying to install to sda6, an extended partition I use for extra distros/installs. I'm also using my usual swap partition (sda7, which is double my ram).

The installer will not progress past the "Prepare Mount Points" stage, with the error message, "No root file system". (Incidentally, the installer doesn't seem to want to progress without me mounting every partition on my hard drive, whether I want them mounted or not.)

I have no hard drive problems or anything else that should cause these error messages or stop the install. I successfully installed Suse 10.1 for fun on there just two days ago. It definitely seems to be an installer issue.

Has anyone else successfully installed Edgy using the Live CD installer onto an extended partition? From the other posts I've read, I think the "extended partition" bit might be the problem.

Adrian

---

### Post by whizbaby on 2006-10-29
Yes, installer problem or broken cd is what I think. The installer (6.06 and 6.10) works fine on a dell optiplex 620G (or similar) so I'm in a slight favour of broken cd (though it doesn't have to be). Try checking md5sum and burning at slow speed. If this doesn't help try with noapic kernel option
(hit F6 when you see the start menu when you boot from cd, then put *noapic* before the final -- of the line that appears then) just to see if it's an apic issue (BTW a lot of mainboards have non-standard apic).
EDIT:
better try vice-versa (first noapic then burning)

---

### Post by willy1234x1 on 2006-10-29
it's strange that edgy isn't working for you I started using ubuntu just last week and had 3x the problems with dapper and then edgy solved them all and now I'm getting pretty good at sudo and such these forums have been a great help in my complete abandonment of windows. so try a complete repartition and maybe just download the alternate install disk iso I prefer it over the live installer it may be old and cruddy looking but it is simpler and doesn't rely on your video cards ability to display larger resolutions before the install of the driver

---

### Post by adriantry on 2006-10-29
Thanks Whizbaby and Willy

There are several people reporting the same error message, so it's not a bad CD. I still think it's a problem with the Live CD installer.

Has anyone managed to install Edgy on an extended partition using the Live CD install? That's the common thread that seems to be common to these posts.

Adrian

---

### Post by whizbaby on 2006-10-29
What I like to know is:
does the setup we're talking about look like this ({} = extended, [] = logical, () = primary )
(win){[ntfs][swap][ext3]}
or like this
(win){[ntfs]}{[swap][ext3]}
?

---

### Post by adriantry on 2006-10-29
> **whizbaby said:**
> What I like to know is:
does the setup we're talking about look like this ({} = extended, [] = logical, () = primary )
(win){[ntfs][swap][ext3]}
or like this
(win){[ntfs]}{[swap][ext3]}
?

Hi again, Whizbaby. Thanks for your question. 

I'm not so interested in fixing my own personal problem as in pointing out a potential problem with the Live CD installer that will affect many people. I'm pretty sure I could just download the alternate CD and install without problems. If the Live CD installer doesn't work with certain sorts of partitions, then it should either be fixed, or at least made clear it doesn't support them.

My setup looks more like the first option, but without that terrible "win" word. "Win" doesn't make you a winner.  ;-)

Here it is exactly:

(ext3){[linux][linux][swap]}

I'm trying to install Edgy onto the second "linux" partition, which is sda6. The other partitions are: my main linux partition (ext3, sda1) and my home partition [linux, sda5].

Hope this helps.

Has anyone successfully installed Edgy onto an extended partition? If no one can comment on this, I may do a few experiments on a vmware drive tonight.

Adrian

---

### Post by adriantry on 2006-10-30
> **adriantry said:**
> Has anyone successfully installed Edgy onto an extended partition? If no one can comment on this, I may do a few experiments on a vmware drive tonight.

I did start to try this experiment last night in on a virtual machine in vmware. I was going to make different configurations of primary and extended partitions on a vmware drive to see what would install and what wouldn't.

Live CDs can be slow in real life, but it was happening much too slow in virtual life. After two hours of waiting I gave up.

I did try installing normally again as on the weekend, but still received the same error message.

Adrian

---

### Post by davirtavares on 2006-10-30
A simple work-around:

In the installation's partition manager, remove and recreate the partition you want to install Ubuntu. The next screen will show the partition marked as "reformat" and the installation will proceed.

Davi

---

### Post by cjm5229 on 2006-10-31
I just reinstalled Win XP on my Computer, had been trying out Vista, it's worse than XP. Anyway, I installed XP, Then used the Edgy live CD to partition my 80GB hdd. I first resized XP to 20GB,  then I created an extended Partition of 60GB, next I created an ext3 partition of 7GB for root roe Edgy.  I have 512 MB of Memory so I created a 1GB swap. Then I  created a 45GB partition for root for Dapper. I used the Gparted partitioner in System>Administration to set up the Partitions. Next I pulled up Install.  I  ran it to manual partition. I then wrote down the names of the partitions I wanted to use. I went to the next screen and checked my first 7GB Part. (hda4) as root and checked format. Then I checked my 1 GB as swap and checked format. Then i checked my 45GB Part. as home and checked format. When that was done I proceeded with the install. Edgy works great. Then I installed Dapper on that last partition the same way. I now Have WinXP, Edgy and Dapper installed and running wonderfully. You must check the reformat button on root and swap to install from the live CD.

---

### Post by adriantry on 2006-10-31
> **davirtavares said:**
> A simple work-around:

In the installation's partition manager, remove and recreate the partition you want to install Ubuntu. The next screen will show the partition marked as "reformat" and the installation will proceed.

Davi

Thanks Davi

When I removed and recreated the partition, the installer recognised it as being blank, and suggested Ubuntu be installed there. It must be part of the internal logic of the installer, and I was impressed! The install was able to proceed.

But the workaround had an unintended side effect.

My spare partition was sda6, and my swap partition sda7.

When I removed sda6, the partitioner renamed my swap partition sda6. When I recreated the spare partition, it was named sda7. I didn't notice this until later, when I tried to boot into my usual linux partition. It wasn't expecting the name changes, and couldn't boot.

I'm sure there are situations in which the workaround might work, but it's not one that I recommend anyone try without carefully thinking through the consequences.

Before I tried booting into my normal linux, I did try the new Edgy install, but it refused to boot too. I may keep working on why in the future, but don't have time now.

I recommend the installer be fixed. The workaround isn't advisable to use in many circumstances because partitions may be renamed. And I have previously installed both Dapper and Suse on this partition without any issues or complications or workarounds.

Will this thread/post be found by the developers, or is there something I should do to let them know?

Thanks to everyone for their help.

Adrian

PS I fixed the partition naming so that my normal Linux disto boots successfully.

---

### Post by Bartender on 2006-10-31
> **ride1226 said:**
> ok. so i figured the same thing and got out my 6.06 live cd....im runnin it now and go to install...get to that step and hey looky there same error.im gettin...

No root file system.

i have it setup so its mounted to my windows partition and then / is at the 38gb partition and swap is on 2gb partition just like before. i dont get it.

What did you mean by "mounted to windows partition"?  Take a good hard look at [this]("http://www.psychocats.net/ubuntu/installing") guide.  At the section on preparing mount points, is that more or less what you chose?

---

### Post by highneko on 2006-10-31
> **ride1226 said:**
> hi guys and this will be my first post here...i recently have decided to make the switch to linux on my pc and currently have windows xp. i have a 200gb hdd so i decided ill duel boot ubuntu and get used to it and set it up but still game on windows. i have downloaded and correctly made the install cd. im currently running the live cd with no problems. i tried to install via the icon on the desktop but am runnin into problems. probably just my lack of knowledge. but anyways i get to the step where it will add a partition to the hdd and u can select how big u want it to be. my problem is it just stalls when i click next. id like to set it up with 50gb for linux and 150 for my windows. any advice on installation. i tried to u gpart? or w.e its called to make my partition but it had an error resizing the windows partition so i could make a 50gb linux part. thanks guys sry if thats confusing.
I believe it's called qpart or something. I'm not sure if it'll help but try entering "df -hT" into a terminal from the live cd and paste the results. If you have to resize I recommend PartitionMagic 8.0. I have only used it for ntfs, and had no problems. It has pretty gui too! Are you sure you have room for this partition? You should make a linux-swap partition also. Please paste the results of "df -hT". Good luck.

---

### Post by stimpack on 2006-10-31
[IMG]http://img522.imageshack.us/img522/9475/snapshot1yy9.png[/IMG]

Yes same bug with trying to install root onto an extended partition. this was *not* a problem in any previous version of Ubuntu. And as for deleting partition and recreating, if it doesnt work I lose Dapper too :/

I really really wish this thread was here before I downloaded 6.10.

---

### Post by cjm5229 on 2006-11-01
You have to click the reformat box on root. That is why you keep getting the "no root" error.

---

### Post by adriantry on 2006-11-01
> **cjm5229 said:**
> You have to click the reformat box on root. That is why you keep getting the "no root" error.

No, you get the "no root" error even if the reformat box is clicked.

There is definitely a problem here! I hope it can be fixed.

Adrian

---

### Post by whizbaby on 2006-11-02
Do I get this right? You got four primary partitions and the extended (with logical in it) additional to that? If so no wonder it doesn't work, I don't know of any BIOS(or IDE controller?) supporting more than four primary partitions per HD. If you have four primary partitions (on one HD) you can't add anything to that.
So instead of 

primary
primary
primary
primary
extended(logical1,logical2,logical3,...)

you have to 

primary
primary
primary
extended(logical1,logical2,logical3,...)

---

### Post by adriantry on 2006-11-03
> **whizbaby said:**
> Do I get this right? You got four primary partitions and the extended (with logical in it) additional to that?

No, he has two drives: hda and hdc.

And he's not the only one having problems!

There's quite a few of us, and the problem is genuine. There is a bug in the installer!

What is the normal process of filing a bug report so we can have this fixed? Everyone seems intent on trying to prove there's no problem!

Adrian

---

### Post by adriantry on 2006-11-03
> **adriantry said:**
> (ext3){[linux][linux][swap]}
I'm trying to install Edgy onto the second "linux" partition, which is sda6. The other partitions are: my main linux partition (ext3, sda1) and my home partition [linux, sda5].Adrian

I had an opportunity to do some more experimenting tonight, this time with different results. I hope they can shed some light on the problem.

When I first tried to install Edgy on sda6 (and kept getting the "no root" message no matter what), I had previously installed Suse on that partition. I don't know what file system Suse uses, but I don't think it's the Ext3 that Edgy uses.

Since then I've installed Elive on that partition. I purposely used Ext3, knowing that Edgy used it. I wondered whether that would make a difference when I came to reinstall Edgy. Well, it did. I was able to get past the partitioning stage, and install Edgy.

(Edgy still wouldn't boot afterwards, but I think that's another issue.)

So, the existing file system seems to make a difference. If the existing file system is Ext3, the installer is happy. Otherwise, it seems not to be happy. This doesn't make much sense, since the little box is ticked so that the partition is about to be formatted anyway! 

Or is selecting the correct file system during the partitioning stage the key step? Perhaps we could use a more helpful error message during the allocating partitions step, or better instructions during the creating partitions step. I'm fairly sure that other distros weren't that fussy (including Dapper), but I could be wrong.

Anyway, I hope this sheds some helpful light on the problem.

Adrian

---

### Post by stimpack on 2006-11-05
Tried looking through bugs on launch pad, cant find anything related to this. I guess I have to wait for Fiesty or Mepis?, I dont see them releasing a new working CD :/.

---

