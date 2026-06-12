---
title: "install Ubuntu under Windows 2000"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by maigege on 2006-09-23
I am newbie here and a newbie with Linux, unbuntu. I had this huge problem with installation , please help...thanks.

I have a Pc (Pentium 4 2G cpu, 512M memory, 80G HD) with Windows 2000 installed on the C: (FAT32 format), there are two other FAT32 partitions D: and E:. I have tried installed Ubuntu to drive D: from the Ubuntu CD but failed miserably for many times. I have looked in internet and this forum but still can not find a way to do it. 

Could anybody give me some help, please......... I am desperately want to install the Ubuntu!!!!!!!!!! But just cannot get it to work!!!!!!!! Uhhhhhhhhhhh!!!!!!!!!!!
Help,,,,,pleeeeeeeeeeeeeeeeeeeeeeeeeeeese!!!!!!!!! I want to kill meself, i have tried it for a day still could not install it sucessfully. Help.......................

---

### Post by maigege on 2006-09-23
I am newbie here and a newbie with Linux, unbuntu. I had this huge problem with installation , please help...thanks.

I have a Pc (Pentium 4 2G cpu, 512M memory, 80G HD) with Windows 2000 installed on the C: (FAT32 format), there are two other FAT32 partitions D: and E:. I have tried installed Ubuntu to drive D: (i want to keep the Windows 2000 in C:) from the Ubuntu CD but failed miserably for many times. I have looked in internet and this forum but still can not find a way to do it. 

Could anybody give me some help, please......... I am desperately want to install the Ubuntu!!!!!!!!!! But just cannot get it to work!!!!!!!! Uhhhhhhhhhhh!!!!!!!!!!!
Help,,,,,pleeeeeeeeeeeeeeeeeeeeeeeeeeeese!!!!!!!!!

---

### Post by maigege on 2006-09-23
Please, somebody please help!!!!!!!!!!!!! I am so desperately

---

### Post by maigege on 2006-09-23
Please, somebody please help!!!!!!!!!!!!! I am so desperately

---

### Post by Mr Egg on 2006-09-23
> **maigege said:**
> I want to kill meself

You should get some help first. Could you please explain what your doing when you install Ubuntu more clearly and then maybe me or someone else on the forum can help you better.

---

### Post by maigege on 2006-09-23
I have a Pc (Pentium 4 2G cpu, 512M memory, 80G HD) with Windows 2000 installed on the C: (FAT32 format), there are two other FAT32 partitions D: and E:. I have tried installed Ubuntu to drive D: (i want to keep the Windows 2000 in C from the Ubuntu CD but failed miserably for many times. I have looked in internet and this forum but still can not find a way to do it.

Could anybody give me some help, please......... I am desperately want to install the Ubuntu!!!!!!!!!! But just cannot get it to work!!!!!!!! Uhhhhhhhhhhh!!!!!!!!!!!
Help,,,,,pleeeeeeeeeeeeeeeeeeeeeeeeeeeese!!!!!!!!!

---

### Post by chuckyp on 2006-09-23
Alright delete the D partition.  Then boot to the cd and install ubuntu to the free space.  It will create the partitions it needs for you.

---

### Post by maigege on 2006-09-23
thanks for the reply. How do i delete the partition D: ?? Do i delete it in Windows 2000?

---

### Post by John.Michael.Kane on 2006-09-23
You should be able to use gparted livecd to edit the two partitions, and then install ubuntu

Link to gparted/live [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by maigege on 2006-09-23
i wanted to install Ubuntu in to D: drive. I used the CD to boot it successfully then Install icon on the desktop to start to install it. I choosed the "Manually edit partiton table" then in next step i choosed the D: drive (shown as: /dev/hda5) then next i choose patition D: (/dev/hda5) for "/", E: for "Swap" then click Next.Then click "Install". then it shown a Error message: "Invalid file system for this mount point" then it got back the step that let me choose the partition method. Over and over agin...

help plese

---

### Post by Sef on 2006-09-23
To dual boot, [click here.]("http://www.users.bigpond.net.au/hermanzone/")  Herman wrote up an excellent tutorial on how to dual boot.

---

### Post by maigege on 2006-09-23
thanks for the link. But with the CD i have there's no "Install in text mode" at all.

---

### Post by K.Mandla on 2006-09-23
Remember that the installer by default doesn't want to use a pre-partitioned space. That might be why you're having trouble.

Try this: Go back into Windows (I'll assume you're using XP or 2000), and right-click on My Computer. Pick Manage. Select Disk Management. Right-click on that FAT32 partition and tell it to delete the partition.

Then reboot with the Ubuntu CD and see if it will let you install to that partition.

---

### Post by K.Mandla on 2006-09-23
> **maigege said:**
> thanks for the link. But with the CD i have there's no "Install in text mode" at all.
Have you downloaded the live/desktop CD?

---

### Post by Sef on 2006-09-23
> thanks for the link. But with the CD i have there's no "Install in text mode" at all.

You're using the Live CD version instead of the **alternate version**. 

> i wanted to install Ubuntu in to D: drive. I used the CD to boot it successfully then Install icon on the desktop to start to install it. I choosed the "Manually edit partiton table" then in next step i choosed the D: drive (shown as: /dev/hda5) then next i choose patition D: (/dev/hda5) for "/", E: for "Swap" then click Next.Then click "Install". then it shown a Error message: "Invalid file system for this mount point" then it got back the step that let me choose the partition method. Over and over agin...

Are you using the default file system? If not, which one are you using?

Have you set it to format the partition?

Have you set it to boot?

---

### Post by maigege on 2006-09-23
My CD is from Ubuntu. version 6.06 LTS sent straight from them.

---

### Post by John.Michael.Kane on 2006-09-23
The version that is shiped to endusers is the live/cd non text-install.

The live cd can be flaky with setting up disk's.

Though it should allow you to edit your tables.

---

### Post by maigege on 2006-09-23
> **Sef said:**
> You're using the Live CD version instead of the **alternate version**. 



Are you using the default file system? If not, which one are you using?

Have you set it to format the partition?

Have you set it to boot?


My cd is free CD from the company who make the Ubuntu.

I used the FAT32 (i think ,because my hard drive has been formated to FAT32). I choosed to reformat. But it has only format the Swap partition but not the D: drive (i want the "/" to be there)

---

### Post by maigege on 2006-09-23
So, which CD is best to use?? I thought the original CD from them is the best, but clearly now it's not. I don't know much about all these Linux staff but i tried to learn. God, i am so frustrated now...

---

### Post by K.Mandla on 2006-09-23
> **maigege said:**
> So, which CD is best to use?? I thought the original CD from them is the best, but clearly now it's not. I don't know much about all these Linux staff but i tried to learn. God, i am so frustrated now...
It's okay. It's just that you want to dual boot with Windows, and the live CD you got from Canonical isn't quite intended for that.

If you want to dual boot with Windows you should think about [downloading the alternate/install ISO]("http://www.ubuntu.com/download") and [burning it to a CD]("https://help.ubuntu.com/community/BurningIsoHowto"). It's more reliable and better suited for [what you're trying to do]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo").

---

### Post by maigege on 2006-09-23
Just tried to boot to my Windows 2000, it failed.....Great...
All people are saying Ubuntu is so easy to install... God. 
It's not for human beings!!!Uhhhhhhhhhh..

anyway, i can now just delete all the partition and put the install Ubuntu on the clean HD. If it still fails then i don't know what i am going to do with this thing any more..

---

### Post by K.Mandla on 2006-09-23
Sorry. 

If you really, really want to dual boot, you should install Windows first -- now, really. 

But if you're willing to try just Ubuntu on that drive, then you can run the live CD you have and just use the partition defaults. 

Sorry we couldn't help in time. :(

---

### Post by maigege on 2006-09-23
Is the CD they gave to enduser any good for  a clean install ??thanks

---

### Post by maigege on 2006-09-23
> **K.Mandla said:**
> Sorry. 

If you really, really want to dual boot, you should install Windows first -- now, really. 

But if you're willing to try just Ubuntu on that drive, then you can run the live CD you have and just use the partition defaults. 

Sorry we couldn't help in time. :(

Thanks for the help. I am now re-installing it. This time is clean install and i use the default for partition (clear out the whole HD). At 15% now and i am sweating...

---

### Post by K.Mandla on 2006-09-23
Yup, it's perfect. You might want to blank the disk with something like [Killdisk ]("http://www.killdisk.com")first, but that's up to you. You can just boot your Ubuntu CD and start from scratch if you want.

---

### Post by K.Mandla on 2006-09-23
> **maigege said:**
> Thanks for the help. I am now re-installing it. This time is clean install and i use the default for partition (clear out the whole HD). At 15% now and i am sweating...
Great! Keep your fingers crossed. [-o<

---

### Post by maigege on 2006-09-23
> **maigege said:**
> Thanks for the help. I am now re-installing it. This time is clean install and i use the default for partition (clear out the whole HD). At 15% now and i am sweating...

53%,please don't hung there...

---

### Post by maigege on 2006-09-23
83% configuring local settings, but not moving...Sweating...

---

### Post by K.Mandla on 2006-09-23
That one will take a while. I think you're going to make it. :D

---

### Post by maigege on 2006-09-23
> **K.Mandla said:**
> That one will take a while. I think you're going to make it. :D

i am starting to worry now, why does it take so long to configure?? Configure what? Still hunging on 83%, CD room reving. come on................

---

### Post by maigege on 2006-09-23
> **K.Mandla said:**
> That one will take a while. I think you're going to make it. :D

It just keep hunging on there, 83%, CD stopped reving. Nothing is moving now. Oh my lord help me....

---

### Post by John.Michael.Kane on 2006-09-23
maigege  relax.. you will be fine. these things take time.

---

### Post by maigege on 2006-09-23
> **SD-Plissken said:**
> maigege  relax.. you will be fine. these things take time.

I just cannot. I have seen a few other people's posts in other forums with the same problem, it just hang there forever. There's no reason why it take so long to do this thing. It's not a slow machine, it got 2G cpu and 512M memory, 80G HD. 

I am so worried. It's 3am in the morning here in UK. I am still doing this thing. God help me....

---

### Post by K.Mandla on 2006-09-23
Don't worry. Even if that doesn't work, there's more than one way to skin a cat (as people are fond of saying around here).

---

### Post by maigege on 2006-09-23
> **K.Mandla said:**
> Don't worry. Even if that doesn't work, there's more than one way to skin a cat (as people are fond of saying around here).

Please work this time,,,,or maybe it went to sleep already before i do. It still in 83% not moving... What is going on ????Oh, god, it's so hopeless

---

### Post by maigege on 2006-09-23
> **K.Mandla said:**
> Don't worry. Even if that doesn't work, there's more than one way to skin a cat (as people are fond of saying around here).

If it fails this time, what else i can do to install it?? Is there any other better way to do it?? Help please....i need to prepare for the worst to happen now..

---

### Post by K.Mandla on 2006-09-23
Well, if it turns out that the live CD method isn't for you, we can move to the alternate/install CD. It's the one you probably could have used at the start, but it will work just as well for a pure-Ubuntu machine. 

If you have another machine, you could [start downloading it]("http://www.ubuntu.com/download"). Make sure you get the "alternate" ISO of Ubuntu 6.06.1. You can try the torrent download, if you're familiar with that. (If you want a direct link, tell us where you are on the planet. ;) )

Even if that method doesn't work, there are still *other* ways of getting Ubuntu on that machine. Don't sweat it. It _will_ work.

> **maigege said:**
> It's 3am in the morning here in UK.
EDIT: Here's [a link]("http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/ubuntu-6.06.1-alternate-i386.iso") for you. This is for 32-bit Intel machines.

---

### Post by ieee488 on 2006-09-23
.

---

### Post by maigege on 2006-09-23
> **K.Mandla said:**
> Well, if it turns out that the live CD method isn't for you, we can move to the alternate/install CD. It's the one you probably could have used at the start, but it will work just as well for a pure-Ubuntu machine. 

If you have another machine, you could [start downloading it]("http://www.ubuntu.com/download"). Make sure you get the "alternate" ISO of Ubuntu 6.06.1. You can try the torrent download, if you're familiar with that. (If you want a direct link, tell us where you are on the planet. ;) )

Even if that method doesn't work, there are still *other* ways of getting Ubuntu on that machine. Don't sweat it. It _will_ work.

Thanks for give me such assurance. I have got the ISO i downloaded about 3 weeks ago(i think?) it's 6.06.1 LTS version. 

My installation is still hanging on 83%. I doubt it will get over that. So next step is try the ISO CD?? I am going to sleep now , will leave the PC running, hope when i wake up several hours later it has been finished. Sigh....

---

### Post by LookTJ on 2006-09-23
> **SD-Plissken said:**
> You should be able to use gparted livecd to edit the two partitions, and then install ubuntu
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
Link to gparted/live [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

no use, if you have ubuntu livecd open terminal, type "sudo gparted" (without quotes) then it will boot gparted partition manager

---

### Post by maigege on 2006-09-23
> **Taylor said:**
> no use, if you have ubuntu livecd open terminal, type "sudo gparted" (without quotes) then it will boot gparted partition manager

where do i type those things to?? What is open terminal?? how do i get a window like DOS window in Windows to type command??Thanks

---

### Post by K.Mandla on 2006-09-23
> **maigege said:**
> I am going to sleep now , will leave the PC running, hope when i wake up several hours later it has been finished. Sigh....
Right on. Let us know what happens tomorrow. [-o<

---

### Post by empcrono on 2006-09-24
> **K.Mandla said:**
> Right on. Let us know what happens tomorrow. [-o<

ouch man it sounds like your having a ruff time i hope it gets better for u.

---

### Post by braheem on 2006-09-24
Since you're formatting and starting from scratch, Have you seen this VIDEO?

[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+boot&hl=en](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+boot&hl=en)

---

### Post by maigege on 2006-09-24
> **braheem said:**
> Since you're formatting and starting from scratch, Have you seen this VIDEO?

[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+boot&hl=en](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+boot&hl=en)

I am using the downloaded version of Ubuntu from Ubuntu website but where the hell can i get the Text Installation option?? 

My installation last night failed because it hung on 83% for a whole night and this morning when i woke up it's still hung on there so i kill it by reboot it. I am now try another attempt.

---

### Post by unisol on 2006-09-24
+put the cd in the drive when it loads choose safe graphics mode then you can use text-mode install good luck

---

### Post by maigege on 2006-09-24
> **unisol said:**
> +put the cd in the drive when it loads choose safe graphics mode then you can use text-mode install good luck

failed again. It hung on 83% again. I run a Check CD for defects and it turned out there are some errors in the CD. What the heck is that? I check the CD from Ubuntu and the cd i made myself both have errors. Something is going wrong. Can i trust the CD Check??

God, i am back to square one, now. what to do next??

---

### Post by Sef on 2006-09-24
> I am using the downloaded version of Ubuntu from Ubuntu website but where the hell can i get the Text Installation option?? 

The text version is known as the alternate version on the download page.

> I run a Check CD for defects and it turned out there are some errors in the CD. What the heck is that? I check the CD from Ubuntu and the cd i made myself both have errors. Something is going wrong. Can i trust the CD Check??

Sometimes CDs or the burns are bad.

> no use, if you have ubuntu livecd open terminal, type "sudo gparted" (without quotes) then it will boot gparted partition manager

GParted won't change any mounted partitions; hence, the GParted Live CD is better in this situation.

---

### Post by maigege on 2006-09-24
> **Sef said:**
> The text version is known as the alternate version on the download page.



Sometimes CDs or the burns are bad.



GParted won't change any mounted partitions; hence, the GParted Live CD is better in this situation.

where can i find MDhash checking tools work with firefox 1.5.0.7?? The cd i received from Ubuntu has one checksum failed in the checking.

---

### Post by talrasha on 2006-09-24
Are your Ubuntu CDs came from shippit?
Coz in shippit there are 5 CDs that ubuntu gave you so you can try the other four if the first one failed.

Realy I'm also a newbie in Linux but I succesfully installed it and I'm already configuring some drivers succesfully.

I'm feeling so sorry that you're experiencing this w/ Ubuntu. I almost also giveup installing it but I just belive in myself and in ubuntu.

---

### Post by maigege on 2006-09-24
> **talrasha said:**
> Are your Ubuntu CDs came from shippit?
Coz in shippit there are 5 CDs that ubuntu gave you so you can try the other four if the first one failed.

Realy I'm also a newbie in Linux but I succesfully installed it and I'm already configuring some drivers succesfully.

I'm feeling so sorry that you're experiencing this w/ Ubuntu. I almost also giveup installing it but I just belive in myself and in ubuntu.

5 CDs?? No, there's only one cd i received from Shippit. yes, it's from shippit.

---

### Post by kinematic on 2006-09-24
okey...let's do it this way.
if you have access to another pc install bittornado on it from here:
[http://bittornado.com/download.html](http://bittornado.com/download.html)
next grab the torrent for the ubuntu alternate cd from here:
[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso.torrent](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso.torrent)
then start up bittornado and navigate to the location where you downloaded the torrent to and dubbelclick on it....that will start the download.
(the nice thing about bittorrent program's is that they check the integrity of the download and 95% of the time this guarantees a correct download).
next burn the image to a cd with deepburner( [http://www.deepburner.com/download/DeepBurner1.exe](http://www.deepburner.com/download/DeepBurner1.exe) ).
pop the cd in your drive again and check it for errors(wich i expect there won't be if you use bittorrent)and continue with the installation ;)

---

### Post by maigege on 2006-09-24
> **kinematic said:**
> okey...let's do it this way.
if you have access to another pc install bittornado on it from here:
[http://bittornado.com/download.html](http://bittornado.com/download.html)
next grab the torrent for the ubuntu alternate cd from here:
[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso.torrent](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso.torrent)
then start up bittornado and navigate to the location where you downloaded the torrent to and dubbelclick on it....that will start the download.
(the nice thing about bittorrent program's is that they check the integrity of the download and 95% of the time this guarantees a correct download).
next burn the image to a cd with deepburner( [http://www.deepburner.com/download/DeepBurner1.exe](http://www.deepburner.com/download/DeepBurner1.exe) ).
pop the cd in your drive again and check it for errors(wich i expect there won't be if you use bittorrent)and continue with the installation ;)

Failed again when it got to 83%, same as before. I am giving up. What else Linux can i install on my machine if i could not install Ubuntu???

---

### Post by talrasha on 2006-09-24
I think there's a problem w/ your CD drive.

Did you reformatted your HD to ext3 filesystem?

---

### Post by maigege on 2006-09-24
> **talrasha said:**
> I think there's a problem w/ your CD drive.

CD drive?? Why ?? it seems OK

---

### Post by talrasha on 2006-09-24
sometimes CDROM burners have problems when reading CDs. so I use my CDROM (that has no capability of burning) to install some apps.

---

### Post by maigege on 2006-09-24
> **talrasha said:**
> sometimes CDROM burners have problems when reading CDs. so I use my CDROM (that has no capability of burning) to install some apps.


Bye bye Ubuntu... Have to jump back to my Windows 2000 now.Sigh..

---

