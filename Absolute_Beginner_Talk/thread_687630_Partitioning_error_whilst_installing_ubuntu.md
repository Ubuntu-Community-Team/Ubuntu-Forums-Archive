---
title: "Partitioning error whilst installing ubuntu"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by thinch on 2008-02-04
Quite a while back I decided to take the plunge and install Ubuntu on my laptop.  Using the partitioning program on the cd I managed to partition my hard drive (it already was split in two), but unfortunately two things happened:

1. I accidentally made the Ubuntu partition waay bigger than necessary, only leaving me about 300MB of space left on one part of the partition, the other space for Ubuntu.

2. The installer unexpectedly crashed, leaving me with a problem.  It seems that it has left some "dead space" that doesn't appear when I try and view it using windows.  This has in effect lost me about 20-25GB of space.  I'm not sure why it crashed, as it was a few months ago, yet I had used the CD as a live cd successfully, and it was one that I ordered through the ubuntu website, so it couldn't have been a burning error (I don't think)

In an ideal world I could dual-boot Ubuntu and Windows XP (which I already have installed), and manage to "find" that space that I lost whilst partitioning the hard drive, so any help would be greatly appreciated! :)
tom

---

### Post by cotcot on 2008-02-04
Download and burn the Gparted LiveCD. Boot from this CD and check your partition. Delete the partition you made too big and restart. 
With gparted it is good to do 1 action and then execute (apply) and then the second , execute ... .

---

### Post by gkestrel on 2008-02-04
Try getting a copy of the Gparted live cd and then boot with that first, then you should be able to see all of your partitions including any dead space. Make sure you Leave the windows xp partition alone  and any recovery, and utility partitions that may be present on your laptop, so that you still have the ability to recover windows if need be. Next delete all other partitions and make an extended partition inside the empty space you have made  you can then  make any logical partitions you need and apply the changes ( I usually make three one for root, one for home and one for swap).  Then reboot and insert your ubuntu cd and try installing again. Hope this helps, if you need any further help just ask

---

### Post by thinch on 2008-02-04
Ok, thanks to all for the quick replies..! I'm downloading the gparted live cd right now, so will keep you both posted.
again, thanks for the help..
tom

---

### Post by thinch on 2008-02-05
I downloaded "gparted-livecd-0.3.4-11.iso" from [http://download.tuxfamily.org/gpartedlive/](http://download.tuxfamily.org/gpartedlive/) yesterday, and put it onto a cd.  I made sure it was a bootable cd, but when i tried to boot from it, it simply didn't work..
it either didn't work at all, simply giving me a flashing "_" icon in the top left, or gave me a load of techincal stuff about it installing a mouse driver successfully.
When it installed the mouse driver(which it did instantly) it simply said A:\>  , expecting me to input something.

What's going on? Has the download not worked? could it be a problem with the burning of the CD? i've ran live CDs in the past, so that can't be the problem, surely? I'd really like to nail this problem, so any help would be appreciated.

tom

---

### Post by Algus on 2008-02-05
It might be a problem with the CD.  I had this exact same problem when I installed Ubuntu yesterday.  Someone told me to get gparter so I did, and used it, and I was able to fix my problem.  

I switched to XP, downloaded the ISO with GetRight, then used Deepburner to burn the ISO to a blank CD-R 

Inserted the CD-R then rebooted and it booted right up into gparter.  The program works great, but do allow yourself some time as it needs to copy the files on each partition you shrink and if you have a lot of data on one of the partitions it shrinks it may take some time.

---

### Post by thinch on 2008-02-05
Right, I made the cd again, and it successfully got to the menu before gparted, where it had various options such as what "type" of gparted to run.. So far I've tried pretty much all of them, but to no avail.. They either don't work, or ask me to enter a login and password, which of course, I don't know.

This is what appears after a lot of text-scrolling when I try the top option, the default:

"Error: Medium error -- (Sense key=0x03)
Unrecovered read error -- (asc=0x11, ascq=0x00)
The failed "Read 10" packet command was:
"28 00 00 00 0f 85 00 00 02 00 00 00 00 00 00 00"
end_request: I/O error, dev hdb, sector 15892"

Then lots of "SQUASHFS errors"

Maybe me typing all this was pointless, or maybe not.  If necessary then I can type the whole lot out, or maybe there'll be another method to solve this.

thanks in advance,
tom

---

### Post by rkd on 2008-02-05
It sure looks like the data being read from the CD is bad. It could have been written bad or it could have been downloaded bad.

When you burned the CD, did you set the burn speed to a low speed? I think 4x is recommended.  Some burners have trouble making an error-free burn at higher speeds.

If the Gparted site gives an MD5 checksum for the .iso file, it would be good to check it to verify that the download did not introduce errors.  If the site did give you an MD5 checksum, but you don't know how to check it, tell us whether you want to check in Windows or Linux and we'll tell you how to do the check.

---

### Post by thinch on 2008-02-05
Yeah, I set it on 4x, so I don't think it will be a write problem.
About the MD5 checksum, I don't think the website gave me one, or even whether you can download it as an option.  the website was [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) if anyone wants to check..
If I was to check it for errors though, I'd probably do it in windows.
btw i'm not too sure on md5 checksums anyway.. they're like a way to check whether a large file arrived 100% error free, right?

---

### Post by rkd on 2008-02-05
Yes, MD5 checksums are a way to verify that the file you downloaded hasn't been altered somewhere along the way.

The gparted site you pointed to does include the MD5 checksums for its .iso file.  Look in the download area for the file with the same name as the .iso, but with .txt added to the end. That is a small text file that contains some information about the .iso, including its MD5 checksum.

So go get the .txt file corresponding to the .iso you downloaded earlier.

To do the checking on Windows, I use digestIT, you can download it from 

[http://www.snapfiles.com/Freeware/system/fwfilemanagement.html](http://www.snapfiles.com/Freeware/system/fwfilemanagement.html)

Search down the page for digestIT -- it is about 80% of the way down.  Download and install it. It will add an item to the right-click context menu in Windows Explorer. Then to use it, in Windows Explorer, navigate to the directory containing the .iso file and the .txt file containing the MD5 checksum. Open the .txt file and copy the checksum to the clipboard. Close the .txt file. Right click on the .iso file, choose "digestIT 2004" from the context menu, then from the submenu, choose "Verify MD5 Hash". In the dialog box, click in the text box, type ctrl-v to paste the expected checksum into the box, and click OK. It will calculate the .iso file's MD5 hash and tell you whether it matches the expected hash. If they match, the downloaded .iso is good. If not, you'll have to download and check it again.

---

### Post by thinch on 2008-02-05
Hi, thanks for the help.. I did all of the steps that you suggested, downloaded digestIT, and verified the MD5 checksum.. It says it matches, so i'll try re-burning the cd and will report back.
tom

---

### Post by thinch on 2008-02-05
I re-burned the cd at a much lower speed, and it seemed to work better, getting further in the booting process, yet it's still not working, giving me more SQUASHFS errors.
However, after a point it seemed to allow some kind of user input, acknowledging when I type in simple commands, like init (don't know what it does, but it responded with a number)
Shall I just admit defeat or try a different method? Part of me says give up, but now I'm this far, I think I might as well get it done..!:)

---

### Post by rkd on 2008-02-05
I've never used the qparted live CD. I wonder whether it has boot options to turn off the acpi stuff like the Ubuntu CDs do. I'm just speculating, but maybe qparted needs that, too.

I'll go look at the qparted site and see whether it says anything about those kind of boot options.

Another approach might be to go burn a qparted CD on another system. That would only be helpful if the CD drive you burned it on was bad. If the problem is something like needing those special boot options, there might be nothing wrong with the qparted CD  you burned.

Perhaps try to boot your qparted CD on another computer, just to see whether it makes it all the way through the boot without those SQUASHFS errors. That would be some support for the idea that the CD is good and we need to use special boot options.

I wonder whether the Ubuntu live CD contains qparted. If so, then you could boot the Ubuntu live CD, with the special boot options, if necessary, and use qparted from it.  Or if qparted isn't there, use apt-get to install it from the repositories into the live CD environment (not touching the hard drive), then use it from the live environment.

Yes, we have a few things we can still try.

---

### Post by rkd on 2008-02-05
The Ubuntu 7.10 Live CD contains gparted version 0.3.3. The version you got from the gparted web site is 0.3.4.

I don't know what differences there are between the two, but I have a feeling that it probably doesn't make very much difference that the one on the Ubuntu 7.10 Live CD is a little older.

Even if you use the 7.04 Live CD, the version of gparted probably is quite suitable for the little bit of repair that you want to do.

I'm assuming that you didn't have any of the trouble with SQUASHFS errors when you used the Live CD to install Ubuntu, so you should be able to boot the Live CD, open a terminal, enter gksu gparted, and be off to the races.

---

### Post by bumanie on 2008-02-05
Gparted is usually a very reliable program. I've never heard of anyone having the problems you're having. What program are you using to burn the iso file to disk?

---

### Post by Forrest Gumpp on 2008-02-05
thinch,

Have you read this thread ( [http://ubuntuforums.org/showthread.php?t=687300&page=2](http://ubuntuforums.org/showthread.php?t=687300&page=2) ) started by stalkingwolf?

stalkingwolf claims victory in achieving a dual boot of XP (the 2004 edition) with Ubuntu 7.04 on a single HDD on a laptop in post # 12, and sets out clearly what he did.

It may well be that the problem does not lie with your live CD or GParted, but may arise from certain editions or updates of XP making it difficult to shrink a first installation of XP, initially made to an entire HDD, down to something like only half of the HDD size.  (I am assuming you have a HDD of around 40GB to 60GB.)  See my post # 11 in that thread.

Since making that post I have spoken with my computer club's Linux guru.  He tells me that Microsoft included files with Service Pack 2 for XP that were designed to be immovable, and that installed themselves near the end of the partition (in most cases, of course, the very HDD itself) upon which XP was already installed.  They can be removed, but the consequence is that Windows XP will no longer boot.

The only way around this, my guru tells me, is to do what stalkingwolf has already done, even if s/he (stalkingwolf) did not realize at the time what was the underlying cause of the difficulty in shrinking the existing XP partition.  The real underlying problem, of course, is that of Microsoft's being most undesirous of direct comparisons between its own and other operating systems on the one computer (especially, perhaps, those of less experienced users) and having underhandedly acted to appropriate HDD space that does not belong to it.

IMHO anything that frustrates straightforward dual booting should be of concern to the Ubuntu community.  If, however, something is done by a major corporation to deliberately frustrate the OWNERS of the computers (and, expressly, drive space) upon which that corporation's software is privileged to run WITHOUT TELLING THOSE OWNERS OF THE HARDWARE of its effect, I believe it should perhaps be of concern to the US Department of Justice as possibly intended anti-competitive conduct.

Where are all the Philadelphia lawyers?  Surely there is a monster class action here on behalf of purchasers of computers that were sold with XP pre-loaded that could, irrespective of its outcome, only benefit the Open Source community in general and Ubuntu in particular.  If such litigation even looked like being successful, just imagine the surge in the willingness of hardware suppliers and major software applications to build Linux compatibility into their products!

---

### Post by rkd on 2008-02-05
Forrest Gumpp: Let's not get too worked up about this apparent new detail about how Windows works.  Even if Microsoft did decide to make the paging file work the way you (and others) are speculating, there is no need to claim it is some actionable offense. There may be very good technical reasons for putting an immovable file at the end of the partition -- to make defragmentation work better, for example. And most Windows users don't need to know such technical details, so there isn't any reason for Microsoft to make a big deal of announcing such details.  Relatively few people will try to let third-party software such as Linux repartition their disk. The fact that the technical details have come out tells me that Microsoft didn't try to keep it a dark secret. It is just technical details that most people don't need to know.  I'm no apologist for Microsoft, but making outrageous claims like you report actually discredits legitimate complaints about Microsoft's other actions. 

Many people have successfully installed Linux systems onto notebook computers without running into problems due to apparent failure of the partitioning to work.  Maybe the paging file is responsible for problems some of the time. If it turns out to be a stumbling block, we will discover ways to deal with it. My first guess for an approach would be to turn off the paging file before trying to install Linux, then turn it back on again after the installation is successful. Or we may have to start advising people to use the Windows Disk Manager to shrink their Windows partition in XP just as we do in Vista.  If neither of those is the answer, someone will find a way that works short of wiping out the Windows installation and reinstalling.

So thanks for pointing out that some people have encountered problems due to the paging file. That is helpful. The over-the-top rant about Microsoft's conspiracy, though, isn't very helpful. Try to keep that under control.

thinch:

The point that Forrest mentions leads me to suggest that you boot the computer into Windows and use the Disk Management application to see what Windows thinks of the disk.  You may have already done that, since you mention viewing the disk with Windows.  If you aren't familiar with it, you get to it by right clicking on My Computer, selecting Manage from the menu that pops up, then when Computer Management opens, click on Disk Management (expand the Storage heading, if necessary to see Disk Management).  

If it doesn't seem obvious to you how to put the disk back into an acceptable state from what you see, perhaps it would be good for you to take a screen shot of the Disk Management display and put it into a post here. 

In case you don't know how to get a screen shot: First make sure the Computer Management window is the active window (click in it if necessary). Hold down the Alt key and push the PrtSc key (usually in the upper right part of the keyboard). That will put an image of the window into the clipboard. Then open some graphics application, such as Paint, and paste the clipboard into the graphics application. Then save the graphics file (select .jpg for the file type if it isn't already that). Then you can put that file into a post here.

Given the possibility that Forrest describes that gparted might not be able to deal with an immovable file in the Windows partition, if Disk Management shows that the size of the Windows partition still needs to be adjusted, use Disk Management to make the adjustment.  It seems worth trying to use Disk Management to delete any leftover Linux partitions.  I don't know whether Disk Management is able to delete Linux partitions. If it isn't, then you can do that with gparted.

I don't know whether you defragmented your Windows disk before starting the Ubuntu installation.  If you did not, it would be a good idea to do that now, before any attempt to further change the size of the Windows partition.

If you run into trouble, make note of the error messages and anything else that seems relevant and post the information here.

If you get the Windows partition adjusted to the size you want, then boot from your Ubuntu Live CD, open a Terminal, and enter the command ```
gksu gparted
```Delete any partitions left over from the first attempt at installing Ubuntu. Create an extended partition (or logical partition, I forget which term gparted uses) to use all of the disk not in the Windows partition, then create whatever Linux partitions you want within the extended partition. Then start the Ubuntu install and when it comes to the disk partitioning part, choose the manual partitioning and you'll get to tell it how to use the partitions you've set up.

If you are unsure about what to do at any point, ask us about it before you start, or if you find you have a question in the middle of things, stop when you encounter the question and ask us.

I'm pretty sure we quickly will be able to get you back on the way to getting a dual boot set up on that computer.

---

### Post by thinch on 2008-02-06
Wow, thanks for the replies everyone! I haven't got enough time today to try all of the solutions, but I'll try them tomorrow.

@rku: I should have realised earlier that gparted was on the ubuntu live cd, i'll definitely give that a go, since it seemed to work fine last time, since it was the installer that crashed I think.

@bumanie: I've tried about three different programs, some doing better than others. I can't remember all of them, but one was NTI somethingorother which came bundled with my pc, one was a downloadble one, and one was a really small (~300kb) download. (Funnily enough the 300kb one worked best)

@Forrest Gumpp: I'm a bit pressed for time now so i'll have to check the other thread tomorrow.  As for your point about the manufacturers purposefully "hogging" the HDD, I know what you mean.  As far as I can tell, my pc came "ready-partitioned", with the HDD split down the middle, so maybe I'm lucky..?

@rku: Again, thanks for the advice, I'll give it a go tomorrow.

All in all, thanks a lot everyone, it's really great to have this kind of support through the long process, and to me, it's one of the things that makes linux and ubuntu special.. the community side of things. :)
tom

---

### Post by thinch on 2008-02-07
Ok, here's a screenshot of the computer management screen, and from what I can tell it seems ok and hopefully fixable.. I'm not sure how to move the partition, but from what I can tell, Computer Management seems to be able to delete the 20.22GB partition.  It also says that the 941MB one is a "logical drive", but it seems to be able to delete this too.
Call me over-cautious, but i'd rather only mess about with partitions and delete them once i've been told what to do and how to do it since its quite a major thing in my mind, so i'll set my pc to defragment now, and await further instructions..

---

### Post by rkd on 2008-02-07
Good thing to be cautious. If I read the disk information display correctly, the 20GB partition has been marked as the active partition -- the one the BIOS will try to boot from. Before you delete it, you need to make the C: partition be the active one and probably have to fix up the MBR (master boot record).

When you start the PC now, does it start Windows directly, or does it display a menu from which you get to select Windows or Ubuntu? From your initial description, it seemed like the Ubuntu install didn't get far enough to affect the startup, but maybe it did. So what do you see when you start the computer?

There are a number of ways to fix up the MBR, should it be necessary. 

Maybe the easiest is booting from a Windows 98 boot floppy. Do you have one? Does the computer have a floppy disk drive?

Booting from a Windows XP Install CD and going into the recovery console is another way to restore the MBR. Do you have a Windows XP Install CD (not a recovery CD)?

Another way is to download a utility named mbrfix and run it from within Windows. I've only read about it, but it looks easy enough, so we could do that if none of the other ways are possible.

Does the D: partition contains files you need to keep? I imagine that is true, but I want to check. Did the D: partition exist before you tried to install Ubuntu or did you create it later? You said the disk was already split in two, so I imagine that was C: and D: before you tried to install Ubuntu. Did the Ubuntu install attempt reduce the size of one or both of the existing partitions?

How would you like the disk space to be divided among C:, D:, and Ubuntu?

I'll wait for your answers to these questions before giving the detailed directions. (I don't want to spend time writing directions for an option you can't use.)

---

### Post by thinch on 2008-02-07
Well I've just set D: to defrag, so I'm just waiting right now, but I'll explain the situation to you..

On startup now it boots Windows up straight away, without any menu or anything like that, so the ubuntu installation didn't change that..

The computer hasn't got a floppy drive, and it didn't come with a Windows CD either, so that's not going to work. I could use MBRfix if necessary, though.

The D: partition *does* include files I want to keep, it's where all my music is stored, and it did exist before I tried to install Ubuntu.. I think it was 40GB for C: and another 40GB for D:.

On installing Ubuntu, I tried to chop D: up to free around 5 to 10GB for Ubuntu, but I dragged the slider to the wrong end of the scale, leaving me with about 1GB left for D: and the other 20GB for Ubuntu (which in essence disappeared)

I'd like the disk space to end up like this:
C: Around 40GB - as it is now.
D: With about 10GB more than now, so around 25GB
Ubuntu: Around 10GB

Another question: presuming everything goes to plan, would I be able to access the files on C: and D: when booting Ubuntu, or would that be "off limits"? Stupid question probably, but I thought I might as well ask. If this is so, then I could manage with 5GB for Ubuntu, leaving the other 5 for D:

thanks,
tom

---

### Post by rkd on 2008-02-07
You will be able to access the Windows partitions from Ubuntu. That works fine.

Do you have another computer on which you could access the forums and on which you could download and burn CDs in case the computer we are trying to fix becomes unbootable?

Do you have a backup of the important files on the computer?

---

### Post by thinch on 2008-02-07
Yes I do have another computer with internet access and a CD burner, and I do have a full backup of all the data on the laptop dated 11th Nov 07 (though I'd probably do another quick backup of the most recent files)
tom

---

### Post by Forrest Gumpp on 2008-02-07
thinch
I don't mean to butt into what seems to be the absolutely excellent help you are getting from rkd, but here is a link to a site you may find useful for a general understanding of dual booting Ubuntu with other OSs:  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This site is linked to in the forum sticky thread (at the top of the index page) by ubuntu_demon under the section heading #6, "Dual Boot Problems".  It is quite an extensive site.  I am still trying to digest it all after several weeks of surfing its links.

rkd

Sorry if I wasted your (or anyone's) time with my rant the other day about immovable Windows files appearing to frustrate partitioning.  It wasn't a new discovery, however.  I heard about it over a year ago at my computer club, but was not paying close attention at the time, which is one reason why I was so vague in describing it.  I have no more detailed information on the subject, nor, probably, the technical competence to expound much upon it.  I note that forum member LowSky (928 beans) seems to mention this immovable files problem in this post:  [http://ubuntuforums.org/showpost.php?p=4274518&postcount=27](http://ubuntuforums.org/showpost.php?p=4274518&postcount=27)  .  It would thus appear there may be some substance to claims for its existence.

Perhaps I imputed the wrong motives to Microsoft in my rant.  It certainly would be outrageous of me to perpetuate an urban myth of this nature, if that is what it is.  My attitude toward Microsoft has arisen out of profound frustration at seeing the difficulty my (computer competent) son has encountered activating his (genuine) Windows XP after his frequent re-installations of it.  There was no mention of any 'limit' to the number of re-activations of XP when I paid my cold hard cash for it.  Resolving this problem with Microsoft directly has proven impossible.  When you try to contact Microsoft from Australia, you get stuck in a seemingly endless loop of offshore call centre operators telling you in heavily accented English what you already know.  No more!

I mentioned this apparent feature of XP (or its service packs) because I thought it in the interest of the Ubuntu community in general, and new users in particular, to be able to dual boot with as little difficulty as possible.  I was hoping that someone might have a precise explanation of the phenomenon.  Perhaps it may be of interest to the Beginners Team, but I don't yet know how you bring things up to them from this forum.

Thank you for the time and effort that obviously goes into your help to other posters.  I am passionate about Ubuntu Linux and dual booting and am watching this and related threads with acute interest.

---

### Post by rkd on 2008-02-08
Forrest: 

Yes, Herman has a lot of very helpful information at his site. It can be a bit hard to read, but for those who make the effort, there is a lot of help there.

The information about unmovable files you brought up in an earlier post was good -- I had not heard that it happened on XP. My criticism is only about claiming Microsoft did it deliberately to frustrate Linux. I assume we have no proof of that, nor even strongly suggestive evidence. Microsoft has provably done lots of things to frustrate Linux. We should avoid making a fuss about things we have no proof of, so they can't point to those unproven criticisms as defense against the provable ones.

thinch:

I think the risk of losing your data is small, but having backup would be prudent.

I believe you are pretty familiar with Windows, so I'm not going to write as much detail about the Windows commands as I will for the Ubuntu commands. If I don't have enough description of the Windows commands, just ask and I can fill in more details. If it looks like any of the directions I wrote here are wrong, ask about it. I might have made a typo or other mistake. Better to clear up any questions than risk doing something wrong.

First, get the MBRFix program. Boot Windows on the computer to be fixed. Go here: 

[http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)

MBRFix is the first item on that page. Find the word 'DOWNLOAD" in the bottom right corner of the box for MBRFix and click on it to start the download.

The download is a .zip file. Extract its contents. Copy the MBRFIX.EXE file to the root directory of your C: drive.

Open a Windows command prompt window, and enter these commands:```
c:
cd \
MbrFix /drive 0 fixmbr /yes
```
MBRFix won't display any message if it is successful, so don't expect to see anything.  As I mentioned before, I've never used MBRFix, so I'm just copying the directions about how to use it.

Now go into the Disk Management utility, right-click on the entry for the C: partition (either in the table of partitions or in the graphical display, doesn't matter) and choose "Mark Partition as Active" from the pop-up menu.  It has been a while since I've used the Disk Management utility.  I don't remember whether it will ask for confirmation, tell you to reboot, or what. I trust it will be fairly clear in whatever interaction occurs.

Now restart your PC and make sure it still comes up in Windows okay.  Assuming it does come up okay, go into the Disk Management Utility again. Right-click on the 20 GB partition and choose "Delete Partition" from the pop-up menu. I don't remember what the interaction will be like. I hope it is clear. When that partition is gone, do the same for the 941 MB partition.

At this point, the picture of the partitions should show the PQSERVICE partition at the left.  The C: partition should be next, to its right. Then there should be the extended partition (the green outline) with the D: partition inside it. There should be some unused space inside the extended partition (to the right of the end of the D: partition), and more unused space to the right of the extended partition.

If it doesn't look like that, you probably ought to post the image of the Disk Management window so I can see what it does look like.  If it does look as I described, continue.

Restart the PC again to make sure it still comes up in Windows okay.

Assuming that's okay, shutdown and boot from the Ubuntu Live CD. Open a Terminal and enter the command:```
gksu gparted
```
We need to do several things in gparted: Make the extended partition grow to occupy all of the empty space on the disk. Increase the D: partition to the size you want it to be. Create a Linux main partition and a Linux swap partition in the extended partition.

I know this is the part where you had some trouble in your earlier attempt. If you find you are unsure about how to operate gparted, post your questions here. When you are doing things with gparted, it doesn't actually do the commands as you enter them. It saves them up until you click the Apply button. If you do something wrong or get confused, you can undo commands or clear out the whole list and nothing will have been done to the disk.

In the table of partitions, if the triangle at the start of the line for the extended partition is pointing to the right, click on that triangle so it opens the extended partition and displays the partitions that are inside it.

So to grow the extended partition, click on its line in the table of partitions in the middle of the gparted window, then click on the Resize/Move button. In the dialog that opens, drag the right edge of the image of the extended partition all the way to the right. The box labeled "Free Space Following" should show 0. Click the Resize/Move button in the dialog window to close it. This does NOT perform the operation -- it just puts it on the list of operations to be done later.

Then, assuming you want to make the D: partition larger, click on it -- it will be the only partition inside the extended partition and should be named /dev/hda5 (or maybe /dev/sda5). Then click on the Resize/Move button. In the window that opens, either drag the right edge of the partition image to make it the size you want or go to the New Size box below the image and either adjust the size with the up or down arrows or type in the exact new size you want. When you have it the size you want, click the Resize/Move button to close the dialog.

Now, to create the main Linux partition, click on the line for the unallocated space under the extended partition, then click on the New button at the top left corner of the gparted window. That will open the new partition dialog. Go to the Free Space Following box, type in 1500, then push the Tab key. That should set the size of the partition you are creating to fill all but 1.5 GB of the unallocated space. We will use that remaining 1.5 GB for the swap partition. If you want the swap partition to be larger or smaller than that, use your desired swap size instead of 1500. The filesystem type will default to ext2, which is a good enough choice. If you want a different type, go to that button and pick the type you want. Then click the Add button.

Finally, to create the swap partition, click on the line for the unallocated space under the extended partition, then click on the New button. The new partition dialog will open. It should show all the remaining space in the New Size box (the other two should show 0). Go to the Filesystem button, click and select linux-swap as the type. Then click the Add button to close the dialog.

Now review the image of the partitions and the table describing the partitions to be sure it describes exactly what you want.  If anything isn't right, you can either use the Undo button to undo operations from the end of the list or go to the Edit menu to clear out all of the operations so you can start over.

If everything looks right and you want to make the changes, click the Apply button. I don't know how long it will take to do all of the operations. I have a feeling growing the D: partition will take a while because it probably does a filesystem check of the partition, which is a lot of I/O. I believe the other operations are very quick.

When gparted is done with all of the work, quit gparted and restart the computer (take the CD out of the drive) to make sure it still boots into Windows okay. If it doesn't boot, don't panic. I don't expect there to be a problem, but you ought to check at this point to be sure. If it doesn't boot into Windows, stop and tell me about it.

If it still boots into Windows okay, then you can install Ubuntu. 

When you are ready to install Ubuntu, boot from the Live CD again, and when it has completed, double-click on the Install icon. There will be a couple of windows in which you are asked about language, timezone, and keyboard. When it comes to the one named Prepare Disk Space, select Manual and click the Forward button.

On the next window, you tell it which partitions to use for Ubuntu.  Click on the large Linux partition that is immediately after your D: partition. It should be named /dev/hda6 with type ext2 (unless you picked a different filesystem type). Then click the Edit Partition button. In the dialog that opens, change the mount point to "/" (the first choice). Click Okay to close the dialog. Then click on the swap partition, which should be right below the one you just set. Click the Edit Partition button to open the dialog and check to be sure it says to use it as swap. Click Okay to close the dialog. Then click Forward to go on to the next window.

In my dry run, this next window asked about importing accounts from other Ubuntu installations that are on the disk. I don't know what you will see on that window, since there won't be other Ubuntu installations on your disk. Maybe it will skip that window.

In the next window, it asks for your name, what you want your login name to be, password, and name for the computer. Fill in what you want them to be, then click Forward.

The last window lets you review all the choices you've made. If they look right, click the Install button to start the installation. Or you can cancel if things aren't right.

When the installation is done, restart (take out the CD) and you should get a boot menu that lets you choose between Ubuntu, Ubuntu in recovery mode, a memory test, or Windows. Try selecting Windows to make sure that still works. If it does, restart and try selecting the normal Ubuntu to make sure it comes up okay.

That should be all -- you should have a dual-boot Windows and Ubuntu system. Your Windows partitions ought to automatically appear in Ubuntu. If they don't, ask about it and we'll figure out how to get them to appear.

If you want to change things about the boot menu, that is pretty easy to do. Ask if you want to make changes and I'll tell you how.

The directions I gave for gparted assumed that you wanted to use up all the space on your hard drive. If you would like to leave some space free, it is possible to do that. If you want that, tell me what you want and I'll adjust the directions.

I gave directions for the simplest partition arrangement for Ubuntu -- one main partition and a swap partition. Some people recommend two main partitions -- one for /home and one for everything else. The main advantage for that approach is that you can do a complete reinstall of Ubuntu without losing your personal files, since they are in a separate partition from the system files. The main drawback is that you have to decide how to divide the space devoted to Ubuntu between /home and everything else. I think that doing it the simple way is good when just starting out with Ubuntu. Sometime later, you can repartition and reinstall if you want to change to a separate /home partition. But if you want to do that from the beginning, we could.

---

### Post by thinch on 2008-02-09
Thanks for the guide, it's been a real help.. I'm stuck on one of the final stages though.  I followed all your steps, but after telling ubuntu which partitions to install onto I got this message:

"ERROR!!!
File system has an incompatible feature enabled."

When I clicked on OK, this error message appeared:

"The test of the file system with type ext2 in partition #6 of SCSI1 (0,0,0) (sda) found uncorrected errors.
If you do not go back to the partitioning menu and correct these errors, the partition will be used as is."

I clicked on "Go Back" and I've left it alone.  Here's a print screen of what the menu before is showing me.  Do you think it could be to do with the fact that it's not completely free, with 67MB being used?

EDIT: Just found this:
[http://ubuntuforums.org/showthread.php?t=583176](http://ubuntuforums.org/showthread.php?t=583176)
??

---

### Post by rkd on 2008-02-09
Yes, that seems to be a bug in the installer. There is a very easy workaround, though.

Just tell the installer to format the partition into which you are installing Ubuntu. You do that by checking the box on the line for /dev/sda6 in the Prepare partitions window. When you tell it to format the partition before installing, it doesn't have to check what is already there. Once you do that, you should be able to click the Forward button and continue with the rest of the procedure.

I don't know why I didn't catch this on my dry run. Maybe I checked the Format? box and didn't remember to put it into the instructions. (I have run into this before and knew what to do.)  Sorry for the slip-up.

---

### Post by thinch on 2008-02-11
Wow, thank you so much for all the help with partitioning, installing and everything! This morning I successfully installed Ubuntu as a dual-boot.  I'm using Ubuntu to write this, and over time will hopefully make the full-time switch from Windows.  In the meantime though, this is a great alternative..! So once again thanks for all the help!
tom

---

### Post by rkd on 2008-02-11
You're welcome. I'm glad you got things working.

---

