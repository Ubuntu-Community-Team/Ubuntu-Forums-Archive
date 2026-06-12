---
title: "Partitioning problems"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by kevin61 on 2007-06-05
Hello everyone.I am a bit out of my depth here and trying to install Ubuntu.Need to be able to dual boot to win XP for the wife.After reading screeds of stuff I didnt understand I decided to go ahead with the install and hope that I would be given the option to boot XP from the Ubuntu bootloader.First thing that goes wrong is I can only get Ubuntu to run on "safe graphics mode" (whatever that is).Think I can sort that out once I have proper installation.The problem at the moment is at the partioning stage.I resized the c: windows partition ok then created the"/" partion (2.5GB).then the swap partion..at this point the I am told the rest of the space on the disk is unusable.It tells me then that the file system has some amount of clusters not some other amount.There is another partition on the disk..d: but I dont know what that is,but I think it is causing the problem..Any ideas..Thanks in advance

---

### Post by ugm6hr on 2007-06-05
Most likely thing is the unidentified partition is a system recovery partition.  Whether you want to remove it or not is up to you - obviously if you use it for backups, then it would be prudent to keep it.

From the LiveCD (or GParted LiveCD) - open GParted (aka GNOME partition manager) and it should give you a graphical representation of what partitions you have.  If it still doesn't make sense, post a screenshot of it here.

---

### Post by southernman on 2007-06-05
> I can only get Ubuntu to run on "safe graphics mode"Your using which cd - live or alternate. Alternate does a simple text based install.

For your partitioning, boot into windows and see what partitions you have there. This way you know what you can delete or not.

If you haven't done so already, when in windows be sure to defrag your windows partition(s). Not doing so can really mess things up when you resize... though I see it may be to late for that advice! ;)

If you can't remove this alleged phanton "d" drive, then you'll want to use an extended partition for your ubuntu install.

I suggest you use these for Ubuntu:
/ - about 3gb
/home - as much as you can
swap - twice the amount of ram

This way, if you need to upgrade, reinstall you can save the data and configuration files for your user. Bit of a safety net that's well worth the small effort.

---

### Post by kevin61 on 2007-06-05
how do I get the screen shots in here?

---

### Post by southernman on 2007-06-05
after clicking the post reply button, scroll towards the bottom. You'll find it under attachments, or upload attachments. Something like that anyhow.

---

### Post by kevin61 on 2007-06-05
Here are the screenshots ..this is as far as i get

---

### Post by dstew on 2007-06-05
You need to do **chkdsk /f** on the fat32 partition from the Windows recovery console. Then, turn off the page file in Windows. Then, defragment. Then, try to partition again.

---

### Post by southernman on 2007-06-05
> **ugm6hr said:**
> Most likely thing is the unidentified partition is a system recovery partition.  Whether you want to remove it or not is up to you - obviously if you use it for backups, then it would be prudent to keep it.

From the LiveCD (or GParted LiveCD) - open GParted (aka GNOME partition manager) and it should give you a graphical representation of what partitions you have.  If it still doesn't make sense, post a screenshot of it here.Use Gparted as ugm6hr suggested. He/she is, without a doubt, correct about it being a system recovery partition.

Gparted will be found in System > Administration > Gnome partition manager

---

### Post by ugm6hr on 2007-06-05
Go to GNOME Partition Manager (somewhere in Applications or System) and put screenshots from there in (this program is GParted).

Other things:
How big is your hard drive?
What size was the Windows partition before you shrank it?
Judging by the shots you have put in, you have a tiny ext3 partition, a swap partition, a full fat32 partition (is this a data recovery partition?) and the unusable space is unusable because each hard drive can only have 4 primary partitions.  If you want more, you have to delete at least one primary partition to allow an extended partition to exist.

Suggestion:
In GParted - delete partitions sda3 and sda4 - create an extended partition (sda3) for your Ubuntu installation (2.5GB is probably a bit small - 10GB probably better). You can then create a further primary partition (sda4) in the rest of the space, for whatever you want it for.
Then run the installer - select the Guided - use largest continuous free space option.  This will save you having to set any defaults.  It should use the unallocated sda3 extended partition for both the / and swap.

EDIT: southernman is probably right about the /home partition - I just haven't gotten as far as doing that.  The guided install was just too easy ;)

---

### Post by kevin61 on 2007-06-05
Nice one I try the chdsk thing.How do I turn off page file and do I need to turn it back on again?..Have to say I appreciate your help people and your rapid responses.If this is what the open source community is all about I might just delete Microsoft from my world altogether..oops "she who must be obeyed" would render me useless..if u know what I mean..will let you know how I get on

---

### Post by kevin61 on 2007-06-05
Oh dear..Tried using the partition manager and couldnt follow directions.When I created extended partion ( 15GB)..all good..then when I made 4th partion with what was left ,it made it the swap partition automatically.I deleted and started again then it freaked out and told me to go away.I rebooted the disk and now when I access the partition manager it just presents me with the whole300G disk with all space unallocated.On windows disk management shows NTFS partition and extended partition I made earlier.How do I get the partition manager to read the disk again?

---

### Post by dstew on 2007-06-05
You have to do **chkdsk /f** from the Windows recovery console before you can partition the disk, because it seems there are some errors on it. After that, turn off paging: Start --> Control Panel --> System --> (System properties window opens) --> Advanced:Performance --> click Settings --> (Performance Options window opens) --> Advanced:Virtual memory --> click Change --> (Virtual memory window opens) --> click No Paging file radio button --> click Set --> (if you get a system control panel applet warning window, click Yes to continue) --> click OK --> (window opens telling you that you will have to restart the computer, click OK) --> click OK to close the Performance Options window --> click OK to close the System Properties window --> click Yes to restart the computer. Go back through the same steps except turn the page file on and give it 512 Mb size or so after you have finished repartitioning.

After you restart, defragment the main NTFS partition (Start --> Programs --> Accessories --> System Tools --> Disk defragmenter). After that, put in the Live CD and boot it. Open a terminal window and post the output of the command **sudo fdisk -l**

(EDIT: for those who think using windows GUI for system settings is easier than using the command line, note that to turn off paging in linux, all you need to do is enter **swapoff** at the command line.)

---

### Post by ugm6hr on 2007-06-05
OK.

First things first.  Make sure you have anything of importance backed up from that hard drive.  Partitioning can make a mess of all your data, even in the most experienced hands.

Try the GParted LiveCD - it has a more recent version of GParted:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Boot from this CD (using the second boot option). It opens with GParted, and should show a picture of your hard drive.  Hopefully it will show your partitions.  If not, then I suspect that in meddling with your partitions, the partition table (I think that is what it's called - it keeps a database of your partitions) has become corrupted.  I have no idea how to rectify that (without reformatting everything).

If it does show your partitions - then you can try again (after backing up).  My instructions from previously should work.  If you are not sure - repost a GParted picture, and someone will try and help.  I am not quite sure what you mean by

> it made it the swap partition automatically

Was this following installation - or within GParted?

And what exactly did you do here?:

> I deleted and started again then it freaked out and told me to go away.

Deleted what? Started what again?

I hope you appreciate that I'm not being difficult, but it's pretty important that you explain exactly what you are doing and what errors get thrown up.  Otherwise we're just plain guessing.  

PS: Have you decided what the unspecified partition is yet?

---

### Post by kevin61 on 2007-06-05
Ok ugm6hr..Thanks for your patience..(I have backed up and made a system recovery disk before I dipped my toe into Ubuntu).When I made the 4th partition and it scanned the disk it came up with the list of partitions and the last one(118GB) was marked as swap.I didnt like the look of that so I tried to delete all but the 2 windows partitions (The D: partition is indeed a system recovery partition and I am going to leave it alone)I dont remember exactly what the next message was but it definately wanted to reformatt the whole drive from scratch.I am going to follow dstew's instructions first to make sure all is ok in windows then try again..Once again Thanks to all of you.

---

### Post by ugm6hr on 2007-06-05
Sounds reasonable.  I have to say - I'm not quite sure what the initial error message that you posted a screenshot of meant - but it appeared to reference the system recovery partition.  I'll keep an eye on this thread to see if I can learn something too.

---

### Post by kevin61 on 2007-06-05
Ok dstew I have turned the page filing off..had problems doing chkdsk from console  but here is screenshot of terminal and gpartd window

---

### Post by kevin61 on 2007-06-05
try screenshot again

---

### Post by southernman on 2007-06-05
um Kevin, did you intend on formatting the entire drive, or have I missed something. I thought you were leaving windows on, and dual booting.

From that screeny, you no longer have windows. Just a clean blank slate.

---

### Post by bren on 2007-06-05
Hi kevin

I am a linux newbie so dont take anything I say as gospel ...... but i have just been having very similar problems to you.

BUT don't worry i think it is your partition table that is the problem and not the data on the drive

you can repair this via a system recovery cd (you will need another computer to download and burn the iso by the looks of it)

see post #5 in [this thread]("http://ubuntuforums.org/showthread.php?t=463584&highlight=bren") for more details.

if you need help to get through the testdisk bit ( techy interface) then let me know

bren

---

### Post by ugm6hr on 2007-06-06
> **bren said:**
> 
BUT don't worry i think it is your partition table that is the problem and not the data on the drive


I thought so too.  Good to know that you can repair it.  Hopefully, his Windows installation still boots to allow him to fix it.

---

### Post by kevin61 on 2007-06-06
Good morning all.Firstly the windows partition is still there and XP is booting no problem.I have been trying different things and here is what I've found.I tried the sysrecovery disk but didnt get to far with that.Bit above my head.What I need to clarify is where the problem is.The  XP disk manager recognises and displays the partitions I made.Is it reading the partition table?.If it is then the table must be ok?.In the recovery disk I did manage to get the Ranish disk manager up and it saw the partitions as well.From what I can decypher from the "sudo fdsk" command (see screenshot above) they seem to be there also.This leads me to believe that the problem is with Gnome Partition Editor because its the only program that cant see them.

---

### Post by kevin61 on 2007-06-06
Hello all..Coming to you live from my shiny new Ubuntu, installed and dual booting.The answer to my problem was quite simple in the end.In the XP disk manager I deleted the partitions I made with GParted.I created an extended partition with the free space.When I went back into Ubuntu GParted scanned and seen the new partition and I used it to install.I presume that the XP disk manager rewrote the partition table and whatever I had done to confuse GParted was no more..(see screenshot of how I ended up)..Thanks  umghr.Southernman,dstew and bren no doubt we'll talk soon!!

---

### Post by southernman on 2007-06-06
Whewwwww! I was pretty concerned for a moment, that something had gone terribly wrong for you. Other than these small hurdles of course. Glad it all worked out for you, in the end. :)

For what little part I had in this... Your welcome. umghr, dstew, bren, and YOURSELF are the real heros of the day here. Pat yourself on the back.

Later

---

### Post by ugm6hr on 2007-06-06
@kevin61:
Glad you persevered!  And sorry couldn't offer a solution.

For future reference - use GParted LiveCD for any partitioning in future - anything else (apart from Partition Magic) puts your HD at risk if you're using NTFS partitions.

---

