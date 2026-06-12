---
title: "How to change partition size?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Quiltkid on 2006-10-03
Hello,

I've dual booted Ubuntu Dapper 6.0.6 recently w/Windows XP on a Compaq Presario; 1.83GHz, 53Gb's Free space with 512 RAM.  I seem to have cut myself short on space on my C: drive.  So short, in fact, that I was unable to defrag; only had 6% free space, needed 13% I think. Also, some apps, particularly Adobe Photoshop is way too slow now.   I realize Adobe is resource intensive, so how can I make my C: drive larger than only 15GB's?  I only have 2.01 GB's Free space left? My F: drive, made for using the files I'd commonly share between the two OS'es is almost 40 GB's.  I have a swap file of 15 GB's and one other of only 1GB basically.  A friend helped me to set this up as I know very little about partitions.  Any help would be greatly appreciated.

Also, is it really difficult to download other Linux programs and update what I have with dial-up?  I don't have access to DSL or broadband, and was wondering if I should wait on using Ubuntu until I have a faster connection.  Thanks again.

Regards,  Quiltkid

---

### Post by RideP2 on 2006-10-03
I'm also sort of new to linux, but have you ever heard of QTParted, it can modify partitions, although, I'm not shure if you can modify you're Ubuntu partition if you are using it, and since your on dial-up, downloading the Knoppix Live-CD would not be an option. 
But you can try QTParted, I believe you hafto type "sudo apt-get install qtparted".

---

### Post by Quiltkid on 2006-10-03
Hi RideP2,

Thanks for your reply.  Just one major problem; I still can't dial out from Linux as Ubuntu doesn't support my WinModem.  I wonder if this tool can be downloaded via Windows?  Thanks.

Quiltkid

---

### Post by RideP2 on 2006-10-03
No problem, but QTParted will not run on Windows YET. I just went and checked the site, they say that they may make a version in the future. As for any other program, I did allot of "Googling" and found one that works called Swifknife I think it was. I will go look for it and post back in a minute with the link.

---

### Post by RideP2 on 2006-10-03
Found it! "http://www.compuapps.com/Download/swissknife/swissknife.exe" 
That should get you out of your delema.

---

### Post by Ocxic on 2006-10-03
dude if you really have a 15GB swap file, that is wwwaaayyy to much overkill, generally your swap should be half of your total RAM, so if you have 1GB of ram you would use a 500MB swap, increasing the swap size will not increase you computer speed, and prolly slow disk acces dramatically if it gets to big.

---

### Post by RideP2 on 2006-10-03
I thought it seemed big, but I don't know much about swap partitions so I diden't say nothing.

---

### Post by Imsati on 2006-10-03
> **Ocxic said:**
> generally your swap should be half of your total RAM, so if you have 1GB of ram you would use a 500MB swap,

I was always told it was twice the size of RAM (so 5**12**mb RAM would require 10**24**mb Swap)

But regardless, yess...15GB is "way overkill, yo"

---

### Post by RRS on 2006-10-03
> **Quiltkid said:**
> Hi RideP2,

Thanks for your reply.  Just one major problem; I still can't dial out from Linux as Ubuntu doesn't support my WinModem.  I wonder if this tool can be downloaded via Windows?  Thanks.

Quiltkid
'Till you get your modem working in Ubuntu you can download things into windows and then reboot into Ubuntu and copy/paste from the windows partition to Ubuntu.

This may also help with setting up your modem. Check the "How To" section of the forums for a possible fix, beyond my own experiance I'm afraid.

As for changing the partitions, gparted is installed on the Ubuntu live cd and should do the job for you. If you don't have the cd then download gparted from [here]("http://gparted.sourceforge.net/livecd.php") and burn it from windows, it's only about 33mb so it shouldn't be much problem with dial-up.

Hope this helps ya out a little.

---

### Post by Quiltkid on 2006-10-04
Okay, so obviously I'm a real newbie to Ubuntu and partitioning. I appreciate everyone's feedback.  Let me try to clear the swap file size up a little.  Here's what I have as partitions:

  C: NTFS    15.00 GB's capacity  2.01 Free Space  18% Free

  D: FAT 32   4.07       "        972 MB's   "     23%   "

  F: FAT 32  39.46       "        39.42 GB's "     99%   "

  Unknown    15.00 GB's  "        15.00      "     100%  "

  Unknown    1019 MB's   "        1019 MB's  "     100%  "

The F: drive is the space I'm using to put files, etc that will be used in both OS'es.  Wish I could tell you more, I'm still learning.  

We've already established through a program called "ScanModem" that Ubuntu does not support my particular WinModem.  Mine is one of the two they don't, there are 4 others they do.  Lucky me, huh?

Can I change the partition sizes through Window's "Disk Management Console?"  Thanks again to all of you of there.

Quiltkid

---

### Post by Imsati on 2006-10-04
> **Quiltkid said:**
> Here's what I have as partitions:

  C: NTFS    15.00 GB's capacity  2.01 Free Space  18% Free

  D: FAT 32   4.07       "        972 MB's   "     23%   "

  F: FAT 32  39.46       "        39.42 GB's "     99%   "

  Unknown    15.00 GB's  "        15.00      "     100%  "

  Unknown    1019 MB's   "        1019 MB's  "     100%  "

The F: drive is the space I'm using to put files, etc that will be used in both OS'es.  Wish I could tell you more, I'm still learning.  

Can I change the partition sizes through Window's "Disk Management Console?"  Thanks again to all of you of there.

Quiltkid


Ok...Unbuntu partitions...you'll want three of them: 1 Swap, 1 /Root, 1 /Home

Swap is (in simplest terms) to Linux what Virtual memory is to Windows. Make it double what your physicam RAM is (512 mb RAM = 1024 mb (1 GB) Swap partition)

Root is, again in simplest terms, the actual OS. By designating a separate partition for Root, you can delete/format/reinstall should you ever have a problem and not worry about losing all your personal files. Dont give it more that 15GB of HDD space

Home is going to be *your* partition for Ubuntu. Use this to store all your music, etc. files. Give this as much HDD space as you desire.

Those are your three basic Linux Partitions that you want, regardless of anything else.

I have a separate NTFS formatted XP drive, so I don't need to do this following step, but if you have only one HDD, take it into consideration...

If space allows, AFTER making sure the XP partition is the correct size and AFTER making sure the Ubuntu partitions (all three of them) have the correct size, you can make another FAT32 partition so both Windows and Ubuntu can read with the greatest ease.

So basically, regarding your current partitions... Keep C: the way it is, delete the others and start using the above as a guidline. But...PLEASE BACKUP important files before doing so...some folks learn that the hard way...and it's not pretty :evil: 


As far as your Windows DMC question, no you can't do it.

~Jay

---

### Post by Quiltkid on 2006-10-04
> **RRS said:**
> 

As for changing the partitions, gparted is installed on the Ubuntu live cd and should do the job for you. If you don't have the cd then download gparted from [here]("http://gparted.sourceforge.net/livecd.php") and burn it from windows, it's only about 33mb so it shouldn't be much problem with dial-up.

Hope this helps ya out a little.

Thanks RRS,

I do have the Live CD, I will run it tomorrow and see what I can do with the gparted.  Can you offer any advice as to how much larger I should make my C: drive to better handle both Windows and Ubuntu?  Also, by how much do you think I can reduce the F: drive?  I sure appreciate any help.  

Thanks,  Quiltkid

---

### Post by Quiltkid on 2006-10-04
> **Imsati said:**
> Ok...Unbuntu partitions...you'll want three of them: 1 Swap, 1 /Root, 1 /Home

Swap is (in simplest terms) to Linux what Virtual memory is to Windows. Make it double what your physicam RAM is (512 mb RAM = 1024 mb (1 GB) Swap partition)

Root is, again in simplest terms, the actual OS. By designating a separate partition for Root, you can delete/format/reinstall should you ever have a problem and not worry about losing all your personal files. Dont give it more that 15GB of HDD space

Home is going to be *your* partition for Ubuntu. Use this to store all your music, etc. files. Give this as much HDD space as you desire.

Those are your three basic Linux Partitions that you want, regardless of anything else.

I have a separate NTFS formatted XP drive, so I don't need to do this following step, but if you have only one HDD, take it into consideration...

If space allows, AFTER making sure the XP partition is the correct size and AFTER making sure the Ubuntu partitions (all three of them) have the correct size, you can make another FAT32 partition so both Windows and Ubuntu can read with the greatest ease.


As far as your Windows DMC question, no you can't do it.

~Jay

Hi Jay,

Okay, some of this is starting to sink in, finally.  It looks like I'm okay on the Ubuntu "swap" file, as I've got 1019 MB.  My "root" file is probably the other Unknown file I mention that is 15.00 GB. I also have the FAT 32 file you mention where both OS'es can work together.  I'm questioning tho, the nearly 40 Gb's of space we've allowed it to have, when my Window's OS now resides on a mere 15.00 GB's, and it obviously isn't very happy with that number since I couldn't even run my Defrag on it (got the message that I didn't have enough Free Space to do it.)

So, what numbers might you recommend I change those two files to?
If I can get my head around some better numbers, then the gparted ought to go more smoothly - I'm guessing.

Thanks,

Quiltkid

---

### Post by hyper_ch on 2006-10-04
Since you have windows installed I would recommend PartitionMagic from PowerQuest. I have resized partitions (Fat32, NTFS, Ext3 [incl. root partition]) a few times without any problems. I tend to think PM works excellent at this.

Regarding the filesystems in general. If you have things you want to share between Windows and Linux I recommend creating a Fat32 partition. Both can OSes can read/write to it.
In Linux writing to a ntfs partition is still quite experimental as I have read here several times. Everybody recommends the use of a Fat32 partition :)

Good luck

P.S.: Before altering partitions and stuff: Make sure you have backups of your valuable data :)

---

### Post by Quiltkid on 2006-10-04
Hi Sjau,

Thanks for the tip on Partition Magic.  Before I check that out, I want to check out the gparted that's supposed to be on my live CD to see if that'll do the trick.

I do already have a FAT 32 partition created so both OS'es can read/write to it.  That's the one I mention above that's nearly 40GB's.  

What I'm having the problem with seems to be the C: drive where my Window's OS is.  At 15GB's, with nary 2GB's Free Space left, I'm unable to defrag that drive due to insufficient space to do so, and my Adobe Photoshop is running pretty slow as a result of the cramped space.  

Specifically, I'm wondering how much additional space I should allow for C: drive so Window's will be happier and run correctly. Any ideas on that number?  

Thanks,  Quiltkid

---

### Post by Quiltkid on 2006-10-04
Hi Sjau,

Thanks for the tip on Partition Magic.  Before I check that out, I want to check out the gparted that's supposed to be on my live CD to see if that'll do the trick.

I do already have a FAT 32 partition created so both OS'es can read/write to it.  That's the one I mention above that's nearly 40GB's.  

What I'm having the problem with seems to be the C: drive where my Window's OS is.  At 15GB's, with nary 2GB's Free Space left, I'm unable to defrag that drive due to insufficient space to do so, and my Adobe Photoshop is running pretty slow as a result of the cramped space.  

Specifically, I'm wondering how much additional space I should allow for C: drive so Window's will be happier and run correctly. Any ideas on that number?  

Thanks,  Quiltkid

---

### Post by Imsati on 2006-10-04
Glad to see you're coming to realize how it works! So you want your Windows NTFS partition bigger...let's move it from 15 GB to 25 GB--that sounds good. Not sure why it won't defrag though, but honestly, I've never tried it on a drive that small with so much information stored on it. I think the smallest drive I ever had on a desktop was a 20 GB running Win98SE (which was only 250-ish MB instead of XP's nearly 3 GB).

After you resize and defrag it, I'd say just delete all the other partitions and start over with the Ubuntu install and re-create the partitions I mentioned earlier in the thread. I'm sure the ones you have are find, but practice makes perfect, so let's turn the 'coming to realize' into 'continuing to have a better grasp'.

After everything is installed, you can rename all the drives from XP (except swap as XP will see it as a 'raw drive' which is fine). Further, you can go into Windows Disk Management Console and re-assign drive letters. Aside from my C,D, and F (all drives for my XP disk), my Swap is 'S', Root is 'R' and Home is 'H' (just to simplify it and have no 'drive guessing').

~Jay

---

### Post by Frak on 2006-10-04
use gparted,
if that don't work,
use qparted.

---

### Post by helios on 2007-09-03
nothing like being late to a thread.  I was just curious as to how this guy got along with gparted.  I only post this now for anyone using certain key words about gparted.  Had I been here in time, I could have warned him about it.  It handles little jobs ok but in repartitioning anything over 60 gigs, it will take about two days and for your time and effort you will be 100 percent assured of a corrupted disk.  I tell people to avoid gparted like the plague unless they have little piddly jobs to do...it handles those ok.  The big jobs should be left to QTparted or the Acronis programs on the windows side.  gparted has hosed more peoples data than any other program from the looks of the google searches.

h

---

### Post by Quiltkid on 2007-09-04
Hi Helios,

Funny, you are no later to this thread than I am doing something about my original situation. :lolflag:
Would you believe I still haven't solved this issue, mostly because I've two surgeries this year and am still crawling back to normalcy from them.  Beyond that, I'm still on lowly Dial-up, and am stuck with a Win modem that will not play nice with anything linux.

My son has sent me an older US Robotics 56k modem to swap out with the Win modem, but I haven't felt up to the task.  Still hoping DSL will come to our rural mountain area soon.  Can't get line of sight for a wireless broadband connection.

Anyway, I appreciate your thoughts immensely on the gparted program, and after re-reading others' responses again, looks like I definitely have some options.  I do have the latest version of Ubuntu, 7.0.4, and am looking forward to eventually getting everything set up to work.  Thanks too, for taking the time to respond to me, even at this late date - how cool is that! :)

From a middle aged quilting grandma, who borders on computer geekdom :KS

---

