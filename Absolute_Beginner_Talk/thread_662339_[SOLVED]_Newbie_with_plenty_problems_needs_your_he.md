---
title: "[SOLVED] Newbie with plenty problems needs your help"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Desperate on 2008-01-08
Hello you all, new and stupid here, 50 plus and no real computer experience, but a fast learner. I need help for real dummies I'm afraid.
Long story short, downloaded image, got the install cd burned, Was running XP pro on a Compaq Presario, must have renamed a file as it doesn't start windows anymore, not even in safe mode. Wanted dual install anyway and Ubuntu shows my _un_ mounted volume, but can't mount it, been reading help files for ever, but those are even too complicated for me. Started (after trying to get online with Ubuntu for three hours :) )reading about dmraid or something like it, but it doesn't make sense to me, Lots of word have no meaning at all to me. Old fart and English isn't my first language, although they say that I'm improving :) Chatted on other computer to compaq help desk, but no solution there. Is there a way that I can save all my data on that volume (? no idea what that is) and insert a new volume to run Ubuntu ?
Volume info; Raid Volume info still accessible, but not able to get past initial screens to be able to  change anything in windows. It loads the system files from that volume and then crashes into the famous blue screen without text and reboots then.
Could use some help to squeeze Ubuntu in there so I can access the windows part to fix the mishap. free space on that volume/disk at least 100 gig.
Any hints welcome, more info when needed of course.

Thanks
Richard

No need to hurry, I'm going to treat my headache with a nice cold one and I don't drink and type :lolflag: 5 am till 7:30 pm I did my best for today.

---

### Post by sowelie on 2008-01-08
Hey, well you're much braver than most.  I think that's the biggest part about learning computers is being brave enough to try things, because MOST of the time the stuff you're using is pretty well engineered and won't let you do any real damage.  That being said, dealing with hard drives can be a little tricky.  What version of Ubuntu are you working with?  If you are using 7.10 (Gutsy), your windows partition should be automatically mounted.  If not it's pretty easy to mount.

Let me first say, [here's]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") a pretty good beginner's guide to a lot of things Ubuntu (Gutsy).

If you're running 7.04 (Feisty), [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions") is a good guide to mounting windows partitions.

Good luck, you've come to the right place for help.  There's always someone here willing to help out, and we're all newbies at some point.

---

### Post by Gazneth on 2008-01-08
Since your Windows failed to boot the NTFS partition is logging errors.  Ubuntu by default will not mount that partition. Open a terminal window type or paste ```
sudo mount /media/volume name here -o force
```
That will mount your partition and you can then copy your files to a backup device.

Was that machine running a RAID disk?  If it was you may need to use the utilities that came with your motherboard to rebuild it.  I don't think you can partition a disk after defining a RAID setup, it breaks the RAID.

Most of the time your volume name will be sda1 or something similar.
Look in Filesystem>Media

---

### Post by Desperate on 2008-01-09
Hello and thanks, 
Up till now going in with safe mode I could fix what I renamed (trying to stop Billy G keeping track of me by catroot program) But I wrecked that option now :) I have to get the grandkids pictures out of there or I have to start digging a comfortable hole somewhere :)

I'll read and read some more and if I dare and think I know what I'm doing I give it a try. All I need is a mental boost form you guys and a few hints to limit the reading :)

For the record, Running Gutsy Gibbon from install disk.
Raid disk with two volumes Intel ATA ? whatever that means :) Gotta learn a bit more first.
First victory today, online in 15 minutes :) after boot! I'm smiling and hoping

Thanks, new day, new chances

Richard



@Gazneth
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
doesn't work as I'm running from the cd and haven't installed it yet, I could slide in a different extra hard disk and install Gutsy on there? That's an option? As said, very newbie :)

---

### Post by mirexastan on 2008-01-09
Hello there Richard. Me too a newbie in Ubuntu. Your main problem, well, as aforesaid, I'm
a newbie too, so cannot help much, but, for the other bit of infos that you need answers
to, try googling for it, i.e., typing your questions into the search box and you'll get all the
answers that you care to read. For that matter, I'll google also to find out what these
pata and sata means.Bye...

---

### Post by Desperate on 2008-01-09
@Mire,
thanks for the help anyway, I need moral support too :) 
My problem starting from a faulty machine is not the ideal solution, But I never give in or up :) Former Dutch eh, wooden shoes, wooden head, wouldn't listen. 
Reading all I can now and learning lots, but with no hard disk I can't do much, (download and install) so the option of wrecking my other computer and add a hard disk seems to be the easiest way for now, With no warranty that it ever gets solved though, so I'm hesitating to tell my wife we have no computers at all :) 
READ and READ some more, that's it for now.
Thanks gang, good to find out that there is so much support here.

---

### Post by phar on 2008-01-09
Hi Desperate,

If you want to get your XP installation running so you can get your data off I would suggest booting up with your XP CD and waiting until you get to the recovery console (it will ask you to enter R) and then use the command line to enter "fixboot".  The chances are good that you will then be able to once again run XP and get your data off the hard drive so you can set up a dual boot for both XP and Ubuntu.

Good Luck

---

### Post by Desperate on 2008-01-09
Hi Phar, 
Of course I tried recovery, It gives an error and stops the machine, compaq helpdesk couldn't help there :(
When I run safe mode it shows loading system files from that volume, so it is readable for the machine then, but no way to break in in there while it is running and when it stops I have a blue screen and no text for three seconds, then it reboots. Second owner of this machine, no cd's, but I could try to find one and see if that would work if they let me boot the machine, then I'm good. 
My mistake :mad: Trying to stop Billy G reading along with me, With the last update he installed something "ASPI" and that reports back to Billy what ever you do, outside the normal channels through a program called Catroot, doesn't show in windoze, but by the amount of data it collects and the resistantly it has to reinstall it self again after every reboot and it slows down my already slow connection. 
So one after the other I renamed dll files, rebooted and checked if everything worked as it should except catroot, if not safe mode and repair, no problem until the last one :) Disk is okay, but it can't load something it needs or by Billy G set as if not there then don't start.
We'll get there, it's just software and I have a big hammer if needed :)

---

### Post by Ex-windows on 2008-01-09
When you try to get into the windows side does it show the option of "Last known good configuration"?   It should be just above or below the safe mode option.You could also just take enuff room for a ubunut install say 5 gigs (if you can spare it) That would help yo to get those personal files on the other side (windoz) . Also If you have the serial # of the presario they can send you the restore disks . As I recall they weren't very expensive. I hope you can get this resolved, It would truly s**k to lose all those pix.
Good luck

---

### Post by Desperate on 2008-01-09
Thanks Ex
I tried every option together with the compaq help desk and nothing worked (didn't think he was too smart though, you never see your scsi disks listed in your IDE drives :) as far as I know) I'll try the restore CD option by the end of the week when I'm not getting further any other way. Their option, bring it to a dealer and have him fix it ( no warranty of saving data and lots of $$ ) As I'm 80 miles from town, that's the last resort any way :)
All input helps, it learns me somethiong or improves my mood :)

Remarkable community here, if problem is resolved and all data saved I'll run Ubuntu instead of Billies Windoze.

Reading along here :)

---

### Post by Gazneth on 2008-01-09
Here is a how to that may help you out. I had a bad experience with a striped RAID years ago, I will never do that again. Linux LVM or backing up using Grsync to another drive works for me. Good Luck.
[HTML]https://help.ubuntu.com/community/FakeRaidHowto[/HTML]

---

### Post by Desperate on 2008-01-09
Thanks Gaz,
I'll read it and see if... The extra disk I can "borrow" from another computer is only 1.99 Gig  so I'm not making it easier :) 
Might go and buy a 100 gig cheap and install Ubuntu on there, then the pictures aren't gone (over 15.000) you just can't see them right now :) Gives me time to find/try all solutions untill it works. I'll post in here if I can make any progress.
Remarkable community and that for a stupid newbie like me, 

=D>Thanks girls and guys.

Edit:
seems so easy but gives me trouble, found where I can add it, but the right address ?? [quote] add the universe software repository. [\quote]

Edit: Stupid found it in Wiki :)  Thanks

Edit three ;(   got this now
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_bccebhcagd_RAID0" already active
RAID set "isw_bccebhcagd_RAID01" already active
and fdisk will only recognize my memory stick of 65 Mb
I can not mount my Volume, so I'll have to start looking in that direction ? Cause when that works I can rename my original mistake and get the whole thing going again (he wrote hopeful :) )

Edit 4 get the error "you must be root"  I quit for a while now, just to get some fresh air and feed the horses. Ubuntu is half Chinese and 15% Greek to me :), Need more coffee !

---

### Post by argraff on 2008-01-09
A thought...and maybe I'll get beaten up for this? To rescue seriously messed up Windows files (ie pictures and data) I have a version of Knoppix that I keep with me. Maybe it's redundant and the Ubuntu Live CD does the same thing? 

Anyway, I'm posting this in the interest of as many possible solutions to get those photos safely off there and onto Ubuntu!

---

### Post by Desperate on 2008-01-09
Thanks Argraff,
All options welcome, never heard of it, but I'll look it up and see if.....
Desperate, that's no joke :) Anything that might will be checked and tried.

Thanks
No progress yet and i can't even get Ubuntu online now :(  It teaches you patience working on a 400 herz laptop in windoze'98 again :) 


Edit: Got the big one running again, found Knoppix and that seems to be the way to go(Thanks Argraff), but :) my 64MB memory stick wont be able to eat it all and that's all the storage space I have for the moment. So now I have to find a computer where I can load and write a cd to fix mine. As work is busy today, I will have to wait with that a bit and I haven't given up Dmraid yet, but have to study what all can be done there.

Thanks all so far, I'm beginning to believe I'll see my grand kids pictures again :)

---

### Post by Desperate on 2008-01-10
Break through :)
all commands I tried where written for a IDE drive SDA, but I have a scsi drive :) SCD0 !!!
Fdisk now works, but I have to feed the cows now :(   


HAPPY CAMPER HERE :) 
I'll solve it with all this help, got to!


I'll be back


Richard

Edit Disk /dev/scd0: 729 MB, 729608192 bytes
255 heads, 63 sectors/track, 22 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

Disk /dev/scd0 doesn't contain a valid partition table
   It's something, but not what I needed I think, better read some more

---

### Post by Desperate on 2008-01-10
recovery set of CD's from Compaq $40 Can delivery 4-5 days by fedex 
Knoppix cd $9.95 Can delivery by mail 3 days, seems clear what to do here first :)

Thank you all for the help, but I'll be quiet for a few days and then report back here when I have problems installing Ubuntu on the hard disk. Lets see if we can save one for XP and one for Ubuntu as my favorite game SH4 won't run on Ubuntu.

CU soon(I hope)

Richard

---

