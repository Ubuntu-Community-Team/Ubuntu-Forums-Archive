---
title: "'failed to create partition' ???"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Willson on 2006-07-09
Hey guys, I am trying to install ubuntu and I keep getting to this point and it will not let me install it. 

I try get to step 5 of 6 in the installation process where you select how much room you want to partition for the install. 

I am resizing my NTSF drive with windows on it. It is 80GB and i currently have 50GB free. In the Ubuntu install I will set the partition to 30GB and i keep getting the message 'failed to create partition' ... and this is after like 20 minutes when i tell it how big i want it to be. 

Do you think i need to defrag my hard drive with windows or something?:confused:

---

### Post by taurus on 2006-07-09
Bail out of installer right now.  Boot into XP and defrag your harddrive.  May want to do that, defragging, a couple of time.  Now, boot Dapper into LiveCD and use gparted to resize your NTFS!  After you have resized it, then do the installing...

---

### Post by Willson on 2006-07-09
Thanks for the reply

I opened up gparted and i get this message when i select the drive:

"Unable to read the contents of this file system!
Because of this, some operations may be unavailable

Did you install the correct plug in for this filesystem?"

The file system is NTFS, and in gpart it wont show me how much space is used and unused

---

### Post by Willson on 2006-07-09
CRAP! Well i shut down and tried to boot back up in windows.. i get to the screen where windows is loading, a blue screen comes up for a half a seconds then my comp just restarts!!! help!! Is my C drive corrupt now?!?!

---

### Post by molly_001 on 2006-07-09
Willson --

Your experience in using the LiveCD to install Ubuntu has went exactly as mine on the first time that I wanted to install Ubuntu onto a single hard drive with an existing single NTFS partition.

Don't worry, though -- as you can see by my existence here, you can get it back.

Now, hopefully, you made a backup of 100% of your data from the Windows installation, before beginning the Ubuntu install process.  If you did not do so, just accept that you may never see it again.  HOWEVER, you can *might* be able to use the idea below to repair your MBR on the hard drive to again find Windows.

If you have your Windows XP reinstallation CD, which would have come with the new computer purchase in many cases, just put it in the CD drive and reboot the machine.  When you get to the point where you can choose 'R' for Recovery, do so.

You will need to enter your Administrative password, if you had ever set one.

Then type----> fixmbr , at the DOS-like prompt.

---

### Post by Willson on 2006-07-09
> **molly_001 said:**
> Willson --

Your experience in using the LiveCD to install Ubuntu has went exactly as mine on the first time that I wanted to install Ubuntu onto a single hard drive with an existing single NTFS partition.

Don't worry, though -- as you can see by my existence here, you can get it back.

Now, hopefully, you made a backup of 100% of your data from the Windows installation, before beginning the Ubuntu install process.  If you did not do so, just accept that you may never see it again.  HOWEVER, you can *might* be able to use the idea below to repair your MBR on the hard drive to again find Windows.

If you have your Windows XP reinstallation CD, which would have come with the new computer purchase in many cases, just put it in the CD drive and reboot the machine.  When you get to the point where you can choose 'R' for Recovery, do so.

You will need to enter your Administrative password, if you had ever set one.

Then type----> fixmbr , at the DOS-like prompt.
I do not have the original XP cd but i do have a newer one, will that work?

I backed up probably 80% of my data before i tried to install Ubuntu. Just exactly what happened here? I don't understand how my C drive went bad. 

Anybody know of any recovery programs that i can use in linux to see files on my old c drive? I need to get some files off the desktop.

---

### Post by Willson on 2006-07-09
anyway to mount the drive off linux so i can get my old files off?

---

### Post by molly_001 on 2006-07-09
> **Willson said:**
> (A)  I do not have the original XP cd but i do have a newer one, will that work?

(B)  I backed up probably 80% of my data before i tried to install Ubuntu. Just exactly what happened here? I don't understand how my C drive went bad. 

(C)  Anybody know of any recovery programs that i can use in linux to see files on my old c drive? I need to get some files off the desktop.

Answers to your questions A,B, and C, are below:

(A)  In all likelihood, your newer CD media will work for the task of getting to the Recovery Console.

(B)  There is no evidence that your hard drive went bad.  Rather, by partially installing Ubuntu, you wiped over the MBR of the hard drive.  First, use the fixmbr method described above to have Windows repair the MBR of the volume, and see if that allows you to boot back into Windows.

(C)  Create a GAG Boot Manager CD (.iso burn) in case the method in (B) fails.  Click here for more on GAG Boot Manager ... [http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

---

### Post by Willson on 2006-07-09
Thanks for the help guys.. I didn't really understand what a BMR was, I do now. 

I don't have my windows xp cd with me, I will be able to get to it some time this week though. 

Since i dont have my windows cd right now, will method C above work for me right now? Do you think it is ONLY the BMR that is messed up in windows?

Thanks a ton for your help guys

---

### Post by molly_001 on 2006-07-09
> **Willson said:**
> (D)  Since i dont have my windows cd right now, will method C above work for me right now? Do you think it is ONLY the BMR that is messed up in windows?

Answer to your question D below:

(D)  GAG Boot Manager will probably get you back into a bootable Windows situation.  (That is, bootable from GAG.)  You will need to read the directions at the site I gave to you, as well as read the instructions on the front panel interface of the GAG menu.

---

### Post by Willson on 2006-07-09
Well since i am in the live Ubuntu cd mode right now, Am i able to download and burn that program?

---

### Post by molly_001 on 2006-07-09
I believe you should be able to, yes.  Of course you have the internet connection already, and the LiveCD context menu should be able to offer you the option of 'Burn to CD' once the .iso file is on your partition (or Desktop, which is where I would put it for now.)

---

### Post by Willson on 2006-07-09
Well I cannot seem to open the file. When i click the zip file i get the message

"The filename "gag46.zip" indicates that this file is of type "ZIP archive". The contents of the file indicate that the file is of type "HTML document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "HTML document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

and when i right click there is no 'extract to' option. If i could figure out how to open the zip file, i would be ok!

---

### Post by molly_001 on 2006-07-09
Right click the .ZIP file and choose Archive Manager.

---

### Post by Willson on 2006-07-09
"An error occurred while loading the archive."

Command line output:
[/home/ubuntu/Desktop/gag46.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/ubuntu/Desktop/gag46.zip or
        /home/ubuntu/Desktop/gag46.zip.zip, and cannot find /home/ubuntu/Desktop/gag46.zip.ZIP, period.

---

### Post by molly_001 on 2006-07-09
Delete the .ZIP file and download it again, perhaps from the mirror source.
Here's your download page:
[http://gag.sourceforge.net/download.html](http://gag.sourceforge.net/download.html)

---

### Post by Willson on 2006-07-09
same error... Is the file corrupt/incomplete or something?.. is it 14kb for you?

---

### Post by SilverBear on 2006-07-09
Hello, Willson.

Frustrating & scary where you are right now! I've been there.

My own experience is that GAG works, but is not so great.

And the Ubuntu partitioning utility stinks on the live/install disk. Trying to install Dapper totally hosed my laptop HDD!

I believe the other guys who have answered you may be right: your MBR [Master Boot Record} may have gotten messed up. So long as the partition table for the HDD is still OK, you may get out of this easily.

My own preference for partition work is GPartEd, a mini-Linux distro that is geared just to the utilities for partitioning hard drives.
DL it from:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It's only 28.4 megabytes, so it will download and burn to a disk quickly.  It comes as an .iso --a disk image, so your burner should handle it just fine.

I'll write another post on what to do before you try to mess with that Windows system partition. Be careful! Windows is a touchy OS. I have successfiully resized mine with GPartEd, but there are a few necessary preparations to do first.

Good luck.  I'll get back to you with the Windows preparation info if you decide to DL GPartEd.

-SilverBear

---

### Post by molly_001 on 2006-07-09
To Willson --

The file is 807.1 KB.  So, you are definitely not acquiring the full download there for some reason.

---

### Post by Willson on 2006-07-09
SilverBear, I may download that program. I am just concerned here that the problem may or may not be my BMR. I dont want to start partitioning things until i know it is just the BMR that is acting up. 

I am getting a friend right now to download the gag ZIP file and email it to me. we'll see if this works

---

### Post by Willson on 2006-07-09
got the GAG program, unzipped it.. tried to copy to a floppy and founf out i dont have a 4mb floppy. UGH

Can i burn this to a cd? (if i take the Ubuntu live cd out right now, will things go nuts?)

---

### Post by molly_001 on 2006-07-09
Yes, burn the image to CD.

---

### Post by Willson on 2006-07-09
and of course something else goes wrong...

I took out the Ubuntu CD, put in a blank one..  
Right clicked the ISO.. Burn to disc and get this error

"Please put a disc, with at least 3 MiB free, into the drive.  The following disc types are supported:
CD-R, CD-RW, DVD+R, DVD+RW"

I tried 10 different blank cds and i still got the the erro
:: pulls hair out ::

---

### Post by molly_001 on 2006-07-09
That particular error is beyond my approach, if in fact you are using the correct specified type of CD media.

---

### Post by SilverBear on 2006-07-09
The GPartEd ISO is having trouble on all of the North American mirrors I've tried. 

The 2.5-3 is the latest version, just released today.  

I've also tried getting it from mirrors in Australia, Japan & Europe --no luck.  It may not be available until tomorrow. I even tried the 2.5-2 version --same thing. The Servers can't seem to serve it up.

Good luck with the gag bootloader, Willson. I'll check in on this forum tomorrow to see how you did.  I wish you success. You'll like Dapper Drake once you get it up & flying!
--SilverBear

---

### Post by Willson on 2006-07-09
SilverBear, I was actually able to download the gparted iso (v. 2.5-3) with no problems.

---

### Post by SilverBear on 2006-07-09
I saw yopur message about not being able to burn. Is this still the case, or did you fix it?

---

### Post by Willson on 2006-07-09
but yet i get the same error as above when trying to write it to the cd. sigh... Dont really know what else to do here now guys.

---

### Post by Willson on 2006-07-09
> **molly_001 said:**
> I believe you should be able to, yes.  Of course you have the internet connection already, and the LiveCD context menu should be able to offer you the option of 'Burn to CD' once the .iso file is on your partition (or Desktop, which is where I would put it for now.)

> **SilverBear said:**
> I saw yopur message about not being able to burn. Is this still the case, or did you fix it?
nope cannot burn a cd with the default writing program

---

### Post by SilverBear on 2006-07-09
OK. Don't panic yet. . .  if you want to give me a little while to see if I can duplicate the problem, I may be able to figure out the glitch.
Exactly what Live CD did you boot from to get to where you are now?

---

### Post by Willson on 2006-07-09
the regular 32 bit install

---

### Post by Willson on 2006-07-09
I am just unable to write an ISO to a disc, the program is not working.

---

### Post by SilverBear on 2006-07-09
That's Ubuntu 6.06 -386 "Dapper Drake" live/install. right?

OK --one problem might be that you are trying to burn from the Gnome graphic interface menu and you don't have root privileges to write to a CD.  Let me boot that disk and see if that could be it.

please stand by. . .

BTW, do you have any other Live Linux CDs available right now?

---

### Post by Willson on 2006-07-09
No sadly i do not. Wish i had knoppix or something. Yes it is version 6.06

---

### Post by molly_001 on 2006-07-09
SilverBear --

If you are correct that the LiveCD while-in-operation does not allow a user root privileges to write a CD, then:
(a)  That is a particularly astute and keen observation, which 
(b)  should be rectified by the next release of Dapper.

If that is the case, Ubuntu development team should consider to correct it post-haste!

---

### Post by SilverBear on 2006-07-09
OK.
Please check in the top menu "places" and open "computer."

You should get a window that has a list of your disks' partitions and CD-RW at the top of the list.

Right-click on the CD-RW and get the dropdown menu: choose properties.

Click on the "permissions" tab on the new "CD-RW Drive Properties" window that comes up.

Do you have "write" permission as a user, or only "read" permission for Owner, Group & Others?

---

### Post by Willson on 2006-07-09
well i guess i could always burn the gag iso from work tomorrow. Well if it will let me, i dont have many privledges on the computer. Does the built in xp cd burner burn ISOs? I cant install any apps at work, system doesnt let me. 

i really wish i could burn it here though. Let me know if you find anything silverbear

---

### Post by Willson on 2006-07-09
> **SilverBear said:**
> OK.
Please check in the top menu "places" and open "computer."

You should get a window that has a list of your disks' partitions and CD-RW at the top of the list.

Right-click on the CD-RW and get the dropdown menu: choose properties.

Click on the "permissions" tab on the new "CD-RW Drive Properties" window that comes up.

Do you have "write" permission as a user, or only "read" permission for Owner, Group & Others?
only read for all 3. Good work! I will make the changes and see if that was the problem

---

### Post by Willson on 2006-07-09
err it wont let me change the permissions

---

### Post by SilverBear on 2006-07-09
Right. This is one of the problems with Ubuntu. . .  You aren'y root.

Please stand by while I play around with my version of the mess here. I'll get back with a suggestion in a few minutes.

---

### Post by SilverBear on 2006-07-09
That was supposed to be "aren't"

When I type fast, I make mistakes.

---

### Post by Willson on 2006-07-09
no problem, knew what you meant!

---

### Post by SilverBear on 2006-07-09
OK
I'm working through this as we go, so let's do one step at a time so we stay together.

Open a terminal window from the applications > accessories menu.

When the $ prompt comes up type this:
sudo passwd root

It will say "enter new UNIX password:
type:
#rootman

[I just made that up because it's easy to remember.]

let me know when you get that far, and if the prompt changes from $ to # afterwards.

---

### Post by Willson on 2006-07-09
ubuntu@ubuntu:~$ sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$

---

### Post by SilverBear on 2006-07-09
Great!
Now type 

su

and use your new password.  The prompt should change to indicate root status.

---

### Post by Willson on 2006-07-09
alright good so far


root@ubuntu:/home/ubuntu#

---

### Post by SilverBear on 2006-07-09
OK.
Now we get to an Ubuntu problem area. You can't just log out and log in again as root via the graphic login. 

What we need [I think} is the correct command line to burn your disk. 

Frankly, I'm going to have to search through some online manuals. This is not something I usually do.  Stand by.

Oh, BTW, are you just using one computer for all this --accessing this forum on your Live-CD Ubuntu boot?

---

### Post by molly_001 on 2006-07-09
[SIZE=6][COLOR=Magenta]molly_001 declares SilverBear as a [COLOR=RoyalBlue]Studuntu !!

[COLOR=Black](an Ubuntu Stud)[/COLOR]
[/COLOR][/COLOR][/SIZE]

---

### Post by Willson on 2006-07-09
yep, sadly enough. Or else i would have burned the cd on another computer.

---

### Post by SilverBear on 2006-07-09
Molly! You're making me blush!

---

### Post by SilverBear on 2006-07-10
OK, Willson. This will take a few minutes for me to hunt up. 

Get a snack or something. I don't know what time of day it is where you are.  But I'll report back as soon as I find what I'm looking for. I have dozens of Linux help sites bookmarked.
Now to find the right one. . .
[bear shuffles offstage]

---

### Post by Willson on 2006-07-10
No problem mate, its midnight where I am. Thank you for all your help by the way. I may be going to bed within 20-30 minutes (have to get up at 6 tomorrow for work) so if you dont find it within that time just post here and let me know. If i dont get it tonight i will tackle this tomorrow after work.

---

### Post by SilverBear on 2006-07-10
This may take until tomorrow then.

Here is one article on mounting the CDR:
[http://www.codecoffee.com/tipsforlinux/articles/035.html](http://www.codecoffee.com/tipsforlinux/articles/035.html)

It's 12:27 here too. I'll check back with you tomorrow after I research the problem in the AM.

Goodnight.

---

### Post by Willson on 2006-07-10
No problem, I read this forum all day at work haha. Hope to hear from you tomorrow. Please don't forget about me! haha

Thanks for all the help

---

### Post by Willson on 2006-07-10
mmm 7am here.. My quest begins to see if i can fix this at work

---

### Post by Willson on 2006-07-10
I was able to burn the GAG Boot Manager and GPartEd to CD's

So I will have them when I go home today. 

SilverBear, you mentioned 
"I'll write another post on what to do before you try to mess with that Windows system partition. Be careful! Windows is a touchy OS. I have successfiully resized mine with GPartEd, but there are a few necessary preparations to do first.

Good luck. I'll get back to you with the Windows preparation info if you decide to DL GPartEd."

Assuming the GAG Boot Manager works, I will begin to resize my partition for NTFS drive. Any advice is welcomed.

---

### Post by molly_001 on 2006-07-10
> **SilverBear said:**
> ... post on what to do before you try to mess with that Windows system partition. Be careful! Windows is a touchy OS. I have successfiully resized mine with GPartEd, but there are a few necessary preparations to do first.
-SilverBear

I too am interested in these preparations mentioned before resizing an existing NTFS partition with GParted.  In my experience, no preparations were needed, everything went fine -- perhaps I was lucky?  My steps were:
(1)  Installed XP onto 100% of the hard drive; That is, a single NTFS partition containing XP covered the whole volume.
(2)  Then used GParted to shrink that 100% partition to my chosen smaller size, leaving the newly created space as entirely unpartitioned space.
(3)  Then LiveCD installer allowed me to install Ubuntu into that unformatted space, and handled the rest beautifully.
(4)  Note: After step 2, and before Step 3, I did allow XP to boot up as normal, and that's when XP did its five-minute check-up, having detected a change in the size of its installed partition.

---

### Post by SilverBear on 2006-07-10
Good morning, molly_001.

You might have been just  "lucky." Or it might have been due to the fact that you were resizing a new install of XP. Who can say for sure?

Hello Willson. Don't work too hard today. You gotta be fresh for when you get home to the 'puter!

My thinking on the matter goes like this:
fat32 and ntfs filesystems used by Microsoft OS's are prone to fragmentation. It's my understanding that this fragmentation can take place across the entire available space of the active partition that Windows is writing to. Especially on the partition on which it does constant read-writing --wherever it's pagefile and temp files are located.

If you have just one partition that does everything --which is the default on an XP install-- it may start our fairly "in order."  "Ship-shape in Bristol fashion" as the old timers used to say.  But the more you use the operating system, right from it's first voyage out and back again to harbour where it packs itself away at shutdown, XP's busy little sailors are stowing gear where it's quick and easy. 

Personally, I usually do a defrag right after an install, before I even get all the updates & write anything more to the HDD.  I have been surprised to find that there is even fragmentation right after a new installation!

Anyway, I'm sure you get my point by now, so I'll go on to describe my obsessive Virgo approach to shrinking the Windows partition.  This is especially necessary [IMHO] when the installation is months old.

Before you do anything on my list, get a thumb drive or burn to CDs or DVD-RWs or whatever ALL YOUR DATA FILES THAT YOU CAN'T LIVE WITHOUT.

1] Empty the recycling bin. No point in wasting time defragging the trash.
2] In CONTROL PANEL go to "system" or get there through the "My Computer" icon. Choose the "Advanced" tab click "Settings" under the first item: "Performance."  In the new window under "Advanced,"  click the radio button that says "no paging file."
Later you can change the virtual memory to equal the size of your RAM, or accept the Windows suggestion, or whatever.

Reboot the computer.

3] Run the "clean up" by right-clicking on the drive icon in File Explorer and going down to the "properties". Under the "general" tab you see a pie chart of your disk or partition, and a button:"disk cleanup."
BEFORE thou pressest ye button, check the "compress drive to save disk space" and do NOT check the one about indexing --it'll just take twice or three times as long to do the cleanup.

4] After a bit of pondering, you'll get a window with a list of stuff checkmarked to delete and compress, giving you an estimate of how much space you'll gain from the operation. Check everything except the last item, "Catalog files etc."  Most likely they'll all be already checked off.

5] Click "OK". It does it's thing, and you meditate on how much easier this is than shovelling out a stable or cleaning the bathroom. . . If the disk is large with a lot of stuff on it, you might have to wait a bit.

6] When it's done click on "Disk cleanup" AGAIN.
At this point you will wonder why it shows you will still save more disk space if you compress files! You just did that!
Well, fragnented files don't compress well.  But before we move on, choose the tab that says "more options."

Here you get 3 areas to choose from:
7] Windows components:
Click "clean up" and UNCHECK any windows component or sevice that you never use. When in doubt, say something like "fax service" that you never used but might want, uncheck it. I can always be reinstalled from your XP install disk. Sometimes it doesn't even erase the files to run the service, just doesn't start them up on boot, so you get a little time saving if nothing else.  Remember unchecked means it will be gone, checked means it will be installed [or stay installed].

8] Installed programs:
Go through the list and be honest. Remember, you're packing to MOVE. Throw out your old jeans from high school. You can always re-install most stuff you later decide you've _got_ to have, if you make a mistake. Just don't un-install anything you if don't know what it is. It could be important.

9] System restore:
"clean up" to delete all but the most recent system restore point.

10] Hit OK and let it do it's thing. 

11] you're back at just the "Local Disk C: Properties window. Click the "tools" tab. There are 2 choices: Error checking and Defragmentation.

Be tough. You've come this far. Do it right. click "check now." Check BOTH of the boxes, "fix file system errors AND "scan for and attempt recovery of bad sectors."

 It will tell you it can't do anything because you're using the disk [It's mounted," in Linux lingo.] It will ask if you want to do it at next boot time. Say YES. Click OK. Close File Explorer and reboot.

It should run the diskscan before booting to Windows. Now you are reasonably certain that when you defrag you will be writing to good sectors and not lose any bits or bytes.

12] Go back and do steps 3-5 again. Click OK and exit File Explorer. You want nothing running you don't need or defragging will just take longer.

13] Go to Administrative Tools" in the start menu. It might be in the Control Panel.  Or go to "All progs"> Accessories> System tools> Disk Defragmenter. Highlight the disk you want to work on and click "Defragment."

I don't know how closely the bar graph corresponds to any real picture of the sectors or bytes of data on your disk. But chances are it will be all full of thick and thin lines. If most of them are blue, it will go quicker than if most of them are red.

When it's done, click "view report."
What you want to see is 0% on "Volume," "File" and especially "Free Space" fragmentation. Write down the data on the first 5 lines:
Volume size, Cluster size, Used space, Free space and Percent Free Space.
14] Repeat #13 You may be surprised to see that it is doing more defragging and compressing that it couldn't do before.
15] Repeat #14 as many times as necessary until you have solid blue on the left side of the bar graph and solid white on the right. Or until clicking "defragment gives you nothing but an instant "defragmentation complete" notice.

Each time you take another pass at defragging, files get compressed that were formerly too scattered to compress efficiently.

If you are really getting into this, reboot, run steps 12-15 again. Whenever you feel, to the point of  metaphysical certitude, that you have defragged and compacted all your Windows bytes, thank the Supreme Being, or your lucky stars or whatever, that you are weening yourself away from this kind of crappy OS forever. [http://ubuntuforums.org/images/smilies/eusa_pray.gif](http://ubuntuforums.org/images/smilies/eusa_pray.gif)

Put the GPartEd CD-ROM in the drive and shut down Windows. Take a break. 

I'll go on and on about how I do GPrtEd, too, if you want. But in another message.

be of good cheer,[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)
--SilverBear

---

### Post by SilverBear on 2006-07-10
Hey! Why didn't my little smilies come out right?

Maybe you better not listen to me about disk partitions if I can't even do smilies right!
     :-(

---

### Post by Willson on 2006-07-10
SilverBear, great post! that must have taken a lot out of you haha. I appreciate it, thanks mate. 

I haven't defraged in over a year, so i'm sure it will take quite a while. 

When you have time, I would like to know how you use Gparted. Thanks again

:: Crosses fingers the GAG Boot manager will work when i get home.

---

### Post by Willson on 2006-07-10
Well a new concern....

1. I wanted to test out the GAG Boot manager on this work computer. I booted up with the cd and installed it per these directions. 
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

It worked of course, but now how do i get rid of it off this computer? I have limited access on this computer and i dont know how to get GAG off of it. When i start up, GAG starts up (even without the cd in)

---

### Post by SilverBear on 2006-07-10
I'll put together a similarly over-wordy bit on GPartEd so it'll be ready for you whenever you want it.

Thanks for your thanks.  'Twixt thee & me and a cuppa tea, I don't have a lot going for me these days, except occasionally being helpful when and where I can. It's my pleasure. Besides, it's due to a number of others who have done likewise that I've been able to learn Linux to the small extent I know it.

I've used GAG in the past, but I'm pretty certain molly_001 is a lot more knowledgeable about it than I, so listen to her when you go to try that.

BTW, how did you get the GAG & GParted disks burnt? A friend?

---

### Post by SilverBear on 2006-07-10
Hmmm... sounds like you installed the GAG to the MBR of the hard drive. You'll need a Windows 2000 or XP install CD to go back to a Windows bootloader.

Let me hunt it up, and give you a link to this guy's posts on JustLinux forum. He is THE MAN when it comes to all things bootish.

---

### Post by molly_001 on 2006-07-10
[LEFT]> **SilverBear said:**
> Personally, I usually do a defrag right after an install, before I even get all the updates & write anything more to the HDD. I have been surprised to find that there is even fragmentation right after a new installation!  --SilverBear
 
With regard to defragmentatio, your points are well noted.  I think it's a good idea to do all of the things listed in your instructions to Willson, right before an attempt to resize NTFS with GParted.  I use Diskeeper v.9 for defragmentation.  It's so much more powerful than Windows XP default defragmentation utility (*note below).  (Though both are made by the same company, Executive Software.)  Like you, Silverbear, I start to defrag using Diskeeper from the moment I have a fresh XP install, before getting updates.  
 
*note -- Windows XP default defrag utility is dumbed down beyond belief.  As an example, you can make a fresh install, then go through all of the steps you described to Willson for a great defrag.  You run XP's default defrag utility a few times, and you think "Great, I am as defragged as I can be!".  Not hardly...  
 
THEN just try running Diskeeper after all of the above!!  Diskeeper will then display hundreds of files that are still not yet in a defragged state.  It will then work another 15 minutes (on top of your previous default defragger runs) to further defrag the drive!  Getting Diskeeper was the best $14 I ever spent.  It truly makes for a very tangible performance increase when used often.
 
-----
I hope that Willson can get the GParted LiveCD to do the job later![/LEFT]

---

### Post by molly_001 on 2006-07-10
[LEFT]I don't want to repeat Silverbear, but here goes: He is correct, you installed GAG to the MBR of the volume for that work computer.  You would need to rewrite the MBR using a proper boot loader for Windows.  For that (on the work computer) you will need the original imaged software.  You might want to offer lunch to one of the IT staff?[/LEFT]

---

### Post by Willson on 2006-07-10
Haha it's ok. I am only a summer intern student here (i am a college student) I will let them know when i leave, but i don't think it's something that will get me fired or anything. 

Silverbear, i downloaded the ISO's at work and burned them here. That is how i obtained them.

---

### Post by SilverBear on 2006-07-10
Here we go. This thread --and saikee's other stickies on JustLinux-- are IMO _essential_ reading. The guy is not only a maniac at experimentation, but has the grace to explain it to those of us who need scraps of his experience.

The classic thread:
"To install Linux and keep Windows untouched like a virgin"
[http://www.justlinux.com/forum/showthread.php?t=130715&page=2&pp=15](http://www.justlinux.com/forum/showthread.php?t=130715&page=2&pp=15)

The motherload! 
&#8220;You have been with JustLinux Forum for 1.5 year, What have you learned?&#8221;
I murmured "Just booting tips"
[http://www.justlinux.com/forum/showthread.php?t=144294](http://www.justlinux.com/forum/showthread.php?t=144294)

As the salesman on the infomercial says: "But wait! There's more!"
"A grub menu booting 100+ systems of Dos, Windows, Linux, BSD and Solaris"
[http://www.justlinux.com/forum/showthread.php?t=143973](http://www.justlinux.com/forum/showthread.php?t=143973)

Brother, if it isn't there, I don't know it! 

I will try to answer any questions you have. But if saikee's around, he's the man.


My last point before I go off to write about Gparted: DO NOT do anything rash if GAG or GParted don't fix the Windows boot problem. If the PT is damaged, THERE ARE ways of repairing the damage. But if you add another layer of damage on top of that, by hasty action, you might as well reformat the whole drive and start again fresh.

Excuse me. I have to charge up the cattle-prod. My lazy teenage son thinks he's a vampire, I guess. I need to get him out of bed and into the daylight before the nosferaturian transformation is complete!

--SilverBear

---

### Post by SilverBear on 2006-07-10
Hi, Molly.

Thanx 4 the tip re: Diskeeper v.9!  I've been aware of the feebleness of the default defragger 4 Windows, but have been reluctant to spend $$ without a firm recommendation. $14 doesn't seem like a lot to spend in order to save the time of going thru all the iterations I specified to Willson! Thanks again!

BTW, forgive my getting personal but you aren't Molly Miller, nee Johnson, are you?  The chances are astronomical, esp. considering her father takes a dim view of Linux. But in this vast multiverse, one never knows.

Anyway, depending on to what extent I continue to use XP. I will seriously consider getting Diskeeper. I know I'll have to keep at least 1 bootable Windows partition in the house, since some HW will only install via Win or Mac.  Like a used DSL modem I just bought on ebay for $11.00 + shipping. 

Last: I don't know if "Defragmentio" is a typo or intentional, but it lends an exotic flavour to a tedious stew.  Tip'o'th'hat  for the turn of phrase!

--SilverBear

---

### Post by Willson on 2006-07-10
> **SilverBear said:**
> Here we go. This thread --and saikee's other stickies on JustLinux-- are IMO _essential_ reading. The guy is not only a maniac at experimentation, but has the grace to explain it to those of us who need scraps of his experience.

The classic thread:
"To install Linux and keep Windows untouched like a virgin"
[http://www.justlinux.com/forum/showthread.php?t=130715&page=2&pp=15](http://www.justlinux.com/forum/showthread.php?t=130715&page=2&pp=15)

The motherload! 
&#8220;You have been with JustLinux Forum for 1.5 year, What have you learned?&#8221;
I murmured "Just booting tips"
[http://www.justlinux.com/forum/showthread.php?t=144294](http://www.justlinux.com/forum/showthread.php?t=144294)

As the salesman on the infomercial says: "But wait! There's more!"
"A grub menu booting 100+ systems of Dos, Windows, Linux, BSD and Solaris"
[http://www.justlinux.com/forum/showthread.php?t=143973](http://www.justlinux.com/forum/showthread.php?t=143973)

Brother, if it isn't there, I don't know it! 

I will try to answer any questions you have. But if saikee's around, he's the man.


My last point before I go off to write about Gparted: DO NOT do anything rash if GAG or GParted don't fix the Windows boot problem. If the PT is damaged, THERE ARE ways of repairing the damage. But if you add another layer of damage on top of that, by hasty action, you might as well reformat the whole drive and start again fresh.

Excuse me. I have to charge up the cattle-prod. My lazy teenage son thinks he's a vampire, I guess. I need to get him out of bed and into the daylight before the nosferaturian transformation is complete!

--SilverBear

Great links! Thanks for sharing. I have a lot of reading to do, looks like a great forum for information. 

Just got some fillings in my teeth today, hopefully i will feel up to fix my computer when i get home today. I will report back soon!

And regards to your son, I remember those summers, sleeping till noon, heh. I kind of miss them. I'm only 19 but working 7-4 everyday stinks, can't wait till i get back to school in august!

---

### Post by tastic on 2006-07-10
I ran into this same problem over the weekend when attempting to install Ubuntu.  I was working on a clean (but not patched) install of WinXP Home set up on a a single-partitioned NTFS drive.

To fix it, I booted back to windows, used Partition Magic to re-partition the NTFS drive and left the rest of the space unallocated.  

Then, back to Ubuntu, and let the installer set up and the ext3, swap and fat32 partitions I wanted.

Also, Ubuntu didn't like it when PM created and formatted the partitions, stick to the installer for this.

From there the install was painless.  Good luck.

---

### Post by SilverBear on 2006-07-10
Willson,

In your particular situation, as I understand it, you want two things:
To regain the ability to boot into WinXP, and to resize the WinXP partition from 100% of the HDD down to where you have room to add more partitions so you can install Ubuntu 6.06 for a dual-boot computer.

The theoretical assumptions I make in offering my way of doing these steps may not be assumptions with which you agree ,or at least, are not sure about. That's up to you of course. That's why I'm going into my reasons for each step. If you think I'm mistaken, you can not do them. If I sound sober and sane, you might try them.

OK. 
The HDD has both a Master Boot Record [MBR] and a Partition Table [sometimes abbrv't'd to "PT" but not always. I'll abbr'v'te, because when one types with one hand, one likes abbrvtns!]  

If the MBR gets hosed, the 'puter will not boot. This is easily fixed if one has the right tools. The right tools == your original Windows install CD to fix a Windows-only MBR, or an alternate bootloader CD to install a different bootloader. Other bootloaders will usually boot not only Windows but a variety of other OSs. The most common "other" bootloaders seem to be the older Linux "Lilo", the newer Linux GRUB [the one I prefer, which Ubuntu uses] and non-OS specific ones like GAG and another one whose name escapes my declining memory, but it's not under current consideration, so who cares?

On the other hand, if the PT becomes scrambled eggs, the hdd is a candidate for professional data recovery. More $$ than you or I want to think about paying.

I just DL'd the latest GPartEd, 2.5-3, so we'll be working with the same version.

After you have a GPartEd boot CD, put it in the CD drive and reboot. If your BIOS is set to boot from the CD, it should come up booting linux and go right into the gparted program. [Gnu Partition Editor]


1] DO NOT try to reach your goal on the first step. You want to repair your MBR, sure. But your PT is touchier, and it's the more important aspect of the problem, in terms of irrevocable actions. Our goal is , as saith Hipprocates, "First: Do no harm."

SO, try the GAG bootlader solution first. If it works, great! The all you have to do is go about the Windows Pre-shrink Ordeal, as outlined in my previos post.

If GAG doesn't give you back the ability to boot XP, try this first:

2] In GPartEd, choose your drive [which I assume has only 1 partition right now] and click "resize/move"

Remember your XP partition is not really prepped to do a final resize.
SO, all we will try to do is minimally affect it so as to get ZGParted to write a new partition table to the hdd. 

Say, for example, it is an 80 gig drive. Formatted, it will show up as 74.53 GB in the Gparted window. Resize it to say, 72 GB. Click "apply." 

3] When it is done, choose "New" and make a second primary partition in the 2.xx GB. Apply. 
Quit Gparted when it's done. 

4]Now try to install GAG again.

The idea is that gparted gets to rewrite the PT almost as it was, without really screwing up much of anything except the last 2 gigs or so of disk space. It's a fairly safe bet than no essential system files are located there.

There are other partition rescue progs that are more certain of success. Most of them cost money. I have found a couple that don't, but I don't have the names of them handy. I used them to rescue 8 partitions on a 320 GB data-only drive. But with only 1 partition to "rescue" thetrick I outline here ought to work.

MOLLY-001: double check my reasoning & jump in if you think this is a mistake. Same goes for anybody else reading this.

IF THIS DOESN'T FIX YOUR WINDOWS BOOT,  I will look through my prog attic and come up with the tools you need.

Until I hear from you again, best wishes,
SilverBear

---

### Post by SilverBear on 2006-07-10
Last message for now:
It looks like a thunderstorm is moving in fast. I'm shutting down the computers & network until it passes. I'll check back whenever I can. 
Best wishes.

---

### Post by Willson on 2006-07-10
Well i have bad news... and more bad news, :mad: 

I tried GAG first, and the same thing happened. I got the windows loading screen for a second, then a blue screen with white text came up for half a second then the comp just rebooted. 

So i then read your reply and did as you recommended, trying to resize the drive in GPARTED by 2gb. Once i was in gparted, i got the same error i got while trying to use gparted in this live session. Take a look at the screen shot..

It is the same error i got in the boot mode of gparted. 

Any idea on what to do now? I fear i may be losing all my data on my old C drive and that saddens me :|

---

### Post by Willson on 2006-07-10
Edit: The warning section in that screen shot is a little different than the boot session. 

the warning i got read:

Warning: 
Failed to load SMFTMIRR: I/O error
Failed to startup volume: I/O error
Could not mount device '/dev/hda1': I/O error

---

### Post by SilverBear on 2006-07-10
Well, it doesn't look good if the GParted boot disk can't read your drive.

Hmm... I will attempt to locate the software that I used to bail my boat out when the 320GB data disk partition table got hosed.

This may take a while. I have a lot of stuff in my archives. Fortunately it's mostly categorized.

In the mean time don't do anything to make matters worse. All is not yet lost.

---

### Post by SilverBear on 2006-07-10
In the mean time, here is some good background info:
"How It Works: Partition Tables"
[http://www.ata-atapi.com/hiwtab.htm](http://www.ata-atapi.com/hiwtab.htm)

---

### Post by molly_001 on 2006-07-10
Unfortunately, the words I wrote 23 hours ago come to mind ... "Now, hopefully, you made a backup of 100% of your data from the Windows installation, before beginning the Ubuntu install process. If you did not do so, just accept that you may never see it again. HOWEVER, you *might* be able to use the idea below to repair your MBR on the hard drive to again find Windows..."  

I do wish this wasn't the outcome for you, Willson.  I only can say that I completely comisserate with you, having had the same thing happen to me.  I don't remember the dialogue boxes at the beginning of the Ubuntu LiveCD install ... but there should be a series of three pop-up boxes when that CD install is inserted ...

(1) "If there is anything else on the drive (or drives) you are about to configure, consider it all lost at the next prompt.  Continue?  Yes/no"

(2) "So you should abort now if you do not have 100% of your data backed up onto safe, alternative media.  Do not proceed unless you have achieved the 100% backup.  Continue?  Yes/no"

(3) "It's all Russian Roulette from here, only the pistol has but two chambers.  Feeling lucky?   Yes/no"

---

### Post by SilverBear on 2006-07-10
OK, I'm pretty sure that whatever I used was from this guy's site:

"MBR, Partition Table and Boot Record Tools"
[http://mirror.href.com/thestarman/asm/mbr/BootToolsRefs.htm](http://mirror.href.com/thestarman/asm/mbr/BootToolsRefs.htm)

It's a list of free software with links. If your 'puter is kaput, you may need to use someone elses to dl & burn these. 

The Hard Disk Editor from PhysTech is excellent, but probably too byte-level powerful to use unless you has gots a dugree in computer scienz.

This might be what I used:
PTedit32:
[http://mirror.href.com/thestarman/tool/FreeTools.html#PARTINFO](http://mirror.href.com/thestarman/tool/FreeTools.html#PARTINFO)

It looks familiar. 

Sorry, Willson, but that's about all I can do for you right now. I'll check in later to see how it's going.

May success brighten your horizons.  Knowledge has a cost in terms of grueling experiences. Etc, etc...

All the best,
SilverBear

PS:
another good info link, if you miss those late nights of studying:
[http://www.mossywell.com/boot-sequence/](http://www.mossywell.com/boot-sequence/)

---

### Post by molly_001 on 2006-07-10
Also, Willson, consider putting an extra hard drive into your case.

Then you could have an 80GB hard drive as primary (like it is now) -- and you can dual boot Windows XP and Ubuntu onto that drive.

And the second physical drive, which you pop in, would be used solely for data backup.  A sweet, easy way to ever avoid losing data in the future.

---

### Post by Willson on 2006-07-10
> **molly_001 said:**
> Also, Willson, consider putting an extra hard drive into your case.

Then you could have an 80GB hard drive as primary (like it is now) -- and you can dual boot Windows XP and Ubuntu onto that drive.

And the second physical drive, which you pop in, would be used solely for data backup.  A sweet, easy way to ever avoid losing data in the future.

Actually Molly I do have another hard drive in my computer, it is 80GB as well. That is where i backed up most of my data. 

Question - my other hard drive is ~40GB NTFS where i backed up my data and the rest (~40GB) is unpartitioned. Is it possible to install ubuntu on this unclaimed partition and mount the old drive in Ubuntu and possibly see the files? (since linux can read NTFS)

Sounds like a long shot though, i know. 

SilverBear, Thanks for all the info. I plan to burn a app or 2 at work tomorrow and see if i can get anywhere. 

I'm am kind of at a decision stage now. Is it worth all this trouble to get the data off the old drive? Or should i just bit the bullet? There were a few files i wouldnt mind having back (like my resume!) but for the most part i have all my important data. But then again, i have come this far with your help, and i hate to be a quitter!

I don't have a Comp. sci degree yet, but i will in 2 years. Wish I knew more at this level.

---

### Post by illadelphian on 2006-07-11
Hey guys....Molly pointed me to this thread because I was having a problem rebooting XP once i installed the dapper.  Okay...heres my situation, which i think is different than Wilsons.  

Here's my setup:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs   nls=utf8,umask=0222 0 0 defaults,nls=utf8 ,umask=007,gid=46 0       1
/dev/sda4       none            swap    sw              0       0

So i had my XP Pro 2006 install cd which I used to boot and repair my MBR.  I still could not boot XP, just the dapper.

Then I dl'd GAG and created OS boot options, but I still couldnt boot XP.     What I am confused about (may be a clue to you guys) is that when I used GAG to add XP using /dev/sda2....the ntfs...it actually would boot the dapper.  And when I setup /dev/sda3 ...the ext3 to boot the dapper nothing would boot.  I even setup up /dev/sda1...the fat32 to boot XP, but nothing happened.  Why is the ntfs booting the dapper?

---

### Post by molly_001 on 2006-07-11
Pretty strange.  For sure, the MBR of the drive is telling the ntfs loader to look in the wrong partition to continue the boot.

To me, though, that seems to tell me that you can (once inside of Ubuntu) change GRUB's menu.lst file to point GRUB to the correct place.  Of course, at this point, you would need to re-install GRUB to your MBR. 

Does anything in the previous paragraph look familiar?  I ask this because you didn't mention GRUB in your post in this thread.

Thanks.

---

### Post by illadelphian on 2006-07-11
I had forgotten what GRUB was for a second when GAG came into the picture,,,haha.  Anyway...when I installed the dapper I chose to install GRUB on my ubuntu partition and not the MBR.  How can i confirm I did this?

I feel as if my problem has to do with XP not being activated.  When I had installed GRUB to the ubuntu partition, I could not use QtParted in the System Rescue cd to get to my XP drive (/dev/sda2) to make it "set active."  The program would hang when I selected the HD.

WHere is that GRUB file located to change the partition assignments u mentioned?

---

### Post by molly_001 on 2006-07-11
I'm not familiar with installing GRUB outside of the MBR, however, I would encourage you to take your most recent post and submit it as a new thread in this forum.  I fear it will get lost here in this thread, and personally I would want folks with more expertise than myself to help you on your problem.

---

### Post by SilverBear on 2006-07-11
molly_001 said:
(1) "If there is anything else on the drive (or drives) you are about to configure, consider it all lost at the next prompt. Continue? Yes/no"

(2) "So you should abort now if you do not have 100% of your data backed up onto safe, alternative media. Do not proceed unless you have achieved the 100% backup. Continue? Yes/no"

(3) "It's all Russian Roulette from here, only the pistol has but two chambers. Feeling lucky? Yes/no"
---------------------------
LOL!!  That's dead on! I esp. love the last one.


***************************************************************
*****Partitioning an 80 GB HDD for Dual Boot w/ MS-Win & Linux*****

This assumes you are actively using Windows for some ongoing reasons and will be needing to share new data between the two OS's.

My suggestions, with my reasons for each following the chart:


hda1 - ntfs  - 10 GB - Windows installation, set boot flag
hda2 - ntfs  -  2 GB - set this to hold Windows' pagefile & temp files
hda3 - fat32 - 20 GB - Data files you want both OS's to utilize rw-
hda4 - extended partition  [about 42 GB left on the drive]
hda5

---

### Post by SilverBear on 2006-07-11
woops! I don't know how I posted that. I'm not done.
Still early AM, still on my first cuppa. . .
I will write it again in gedit and paste the whole thing when I finish.

---

### Post by Willson on 2006-07-11
> **Willson said:**
> 

Question - my other hard drive is ~40GB NTFS where i backed up my data and the rest (~40GB) is unpartitioned. Is it possible to install ubuntu on this unclaimed partition and mount the old drive in Ubuntu and possibly see the files? (since linux can read NTFS)

Sounds like a long shot though, i know. 


any comments on this SilverBear?

---

### Post by SilverBear on 2006-07-11
Theoretically not a bad idea. 

But if GParted can't decipher the partition table on the hard disk, the installed version  Ubuntu won't be able to read it either. 

What you might want to try is opening up your case, and change the IDE ribbon to make that drive "IDE 0" --the Primary Master-- and make the sick one the slave. Then you can go ahead and use GPartEd boot disk to partition the unclaimed 40 GB on the new master. 

My advice is to make your partitions BEFORE you install Ubuntu. There is something very flaky about the Dapper installer. It's a step back from Breezy in that respect.

Also,  get the "Ubuntu 6.06 alternate" install disk. It seems to have fewer tendencies to do nutty things during install.  It's definitely the one to use if you're installing a dual boot setup:
see:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

This is a grudge I have against the people designing Ubuntu's website. It's a dirty little secret that ought instead to be on the front page. The Live CD really should NOT be used for a dual boot install!  From my experience and from what I read, I wouldn't use it as an install in any circumstances.

Many people have gotten screwed up because Ubuntu doesn't advertise adequately that the Live/Install CD will probably only work well if you are going to let it take over a whole hard disk for itself.  The "alternate install" is more like a real Linux installation CD. It is THE one to use, IMO.  

The Live CD stinks as an installer, and it stinks as a workhorse Linux Live CD [as we discovered the other night trying to burn a disk with it!]. All it's good for is to test-drive Dapper.  

As an attempt to make Dapper the viable Linux alternative to Windows, Ubuntu has shot itself in the foot more than once.  This screwy install problem is one of them.  It's going to turn people away from what is in many ways an excellent OS.

---

### Post by Willson on 2006-07-11
OK, I think i will install Ubbuntu on my other hard drive. 

I am just a little concerned right now that my data on the NTFS partition (the stuff i backed up) will still be ok once i put linux on the other partition.

---

### Post by SilverBear on 2006-07-11
Hi, Willson.

Right now, I can't reassure you about your data.  My advice is forget Ubuntu. There are just too many problems with Dapper Drake.  Life is too short to spend hours fixing messes left by a buggy OS.

My reason for saying this right now?  I booted up today and posted on this forum, as you know.  I was doing some other tasks, and the icon came up that there were updates available for Ubuntu. 

So I clicked to DL & install.  If I remember, the kernel images and CUPS were among the 50 or so MB it needed to dl.

After updates were installed, it said I needed to reboot. So I did.

Bang. Dapper screwed me again. It got as far as showing

GRUB

in the lower left of my screen, and no further. Not even to stage 1.5.

This is third time Dapper has broken my system [once on my desktop, twice on my laptop.]  Three strikes & IT'S OUT.  The only way I'll consider booting Dapper again is "out the door."

Mepis 6 is due to come out any day.  Next to [previous editions of] Ubuntu, Mepis is the easiest to install and the most versatile Debian distro.  Warren Woodford has decided to base the new version on Ubuntu repositories since the Debian repos are reputed to be too flakey right now.  It is a real working Live Linux CD, as well as a good install gisk, and a repair disk. At least the previos versions of Mepis were. I once cloned 3 partitions with operating systems from one hard drive to another using Mepis 3.4-3 as a Live CD, and all three [including Windows2000] booted and ran fine.

My wife used Mepis 3.3-1 as her only OS for almost a year, until I switched her to Dapper.  I'll make sure not to run any system updates on her machine, and switch her to either Mepis 6 or SUSE 10.1.

So I plan on installing Myah 2.1 this afternoon where Dapper lived up until this morning.  

I already know I like SUSE 10.1, and it works on my laptop to, as does Myah 2.0.  After playing with those two and the new Mepis for a few weeks, I'll decide which is going to be my main Linux OS.

But Ubuntu 6.06 is history. I'll try Ubuntu again next year. I liked Warty [my first Ubuntu] and then loved Breezy when it came out. But Dapper is a disaster, in my book. 

My new advice to you is either wait for Mepis a couple days or else install  Myah 2.1.  Or SUSE 10.1, but thats a DVD to download.

bitterly,
SilverBear

---

### Post by SilverBear on 2006-07-11
Actually I see that Mepis has just released RC3, so it'll be about a week for it to come out:
[http://www.mepis.org/node/10515](http://www.mepis.org/node/10515)

---

### Post by Willson on 2006-07-11
Sorry to hear about that SilverBear!! I know it can be frustrating!!

I'm not really sure what I am going to do right now. I am waiting for my Windows XP cd to come in the mail sometime this week. Bought it for $20 from my university!

So I think I may wait for that and see if there are any recovery options. Slim in my opinion but worth a try. 

I am overly concerned about my data on my 2nd hard drive right now. I hope it is OK and can be readable later. Right now the partitions seem to be fine. 

Will keep you updated though, thanks for your input on this. 

I just gave blood today to the red cross van outside my work, feeling a little tired, so I might not mess with this tonight.

---

### Post by jackpipe on 2006-07-14
OK, I've just had pretty much the same problem, and recovered from it.

Firstly, a note to the guys that do the ubuntu partitioning stuff.   WTF are you playing at ???!!!!!  This is the second ubuntu install I've done, and BOTH times, I've had a major problem trying to get my XP partition to work again.  The first time was with breezy I think, and caused by the disk being changed to LBA mode or something if I remember, and even booting into XP recovery console and running fixmbr etc didn't work.

This time, I started with a system runing XP on the entire disk in a single partition.  I tried to resize the NTFS partition and create a Linux partition from the live CD.  The NTFSresize failed, leaving the partitions marked black, and 'invalid'.  I understand dapper is using v0.1 of NTFSresize - they need to start using v0.2, and release a new version ASAP before more people get burned, and put off ubuntu (and thus linux) forever.

The problem for me turned out to be that NTFS resize failed,  erasing (ie all zeroes) the NTFS boot sector.  Luckily the backup boot sector was still intact, and I simlpy copied it to sector 0 of the NTFS partition.  It took almost half a day to work all this out though, since booting from the XP CD was also failing.

I did all of this from the live ubuntu CD, since I'm on a laptop, and that's all I have.
Basically, boot from the live CD.
Run a terminal
Have a look at the boot sector.  
```
sudo dd if=/dev/hda1 count=1 ibs=512 | hexdump -C
```
If all is well, it should look like this, and you can stop reading this post.
```
00000000:EB 52 90 4E 54 46 53 20 -20 20 20 00 02 08 00 00 .R.NTFS ........ 
00000010:00 00 00 00 00 F8 00 00 -3F 00 FF 00 3F 00 00 00 ........?...?... 
00000020:00 00 00 00 80 00 80 00 -4A F5 7F 00 00 00 00 00 ........J....... 
```

If it doesn't look like that, it will possibly start with a line containing all zeroes.  That means the boot sector was erased, just like in my case.
The backup boot sector is stored at the end of the partition, so we need to get the partition size
```
sudo fdisk /dev/hda
``` and look at the partition table, with 'p'.  If all is OK, note down the size of the XP partition, and multiply by 2 (to get the value in 512-byte blocks) and subtract 1.  lets call this figure 'offset'.

Now have a look for the backup boot sector.
```
sudo dd if=/dev/hda1 count=16 ibs=512 skip=<offset> | hexdump -C | more
```
Were <offset> is the offset figure you calculated before.  Again you're looking for the boot sector above.

You may need to reduce 'offset' a bit if the partition size no longer matches the original.  When/If you find it, you'll have to calculate the exact address in blocks (it may be at 'offset', but maybe before) again.
Once found, you can copy the boot sector to a file:

```
sudo dd if=/dev/hda1 of=bootsector count=1 ibs=512 skip=<offset>
```

And then replace the actual boot sector with this

```
sudo dd if=bootsector of=/dev/hda1 ibs=512 obs=512 count=1
```

I realise this isn't exactly newbie friendly, but I hope it helps.

---

### Post by molly_001 on 2006-07-14
To jackpipe --

That really is an incredibly insightful and useful post, jackpipe !!
If I could reach out and twist your arm there, I'd try to squeeze you into collaborating with me.  Collaboration to make a single web page (credited to you, of course) at my site for the purpose of showing others how they might be able to recover a boot into XP.  I certainly do wish I would have known this when I first installed Ubuntu alongside XP.  (If you have the patience, read back through this thread and discover what all I had done BEFORE using the LiveCD to give myself several escape routes in case anything went wrong ... and even still, I was unsuccessful to boot back into XP and needed to wipe everything out and start from scratch!)

Now where was I ... OH! ... yeah, arm twisting ... [cough cough]

Thanks.

---

### Post by Willson on 2006-07-17
Hey Guys, sorry I have been MIA for a while. 

Anyway, I got my XP cd in the mai, i ordered on from my uni for like $20 (i am a student)

And i popped it in, it fixed the partition, and i am back up and running on my windows xp OS. 

I want to thank you all for helping me, esp. silverbear and molly. You guys stuck it out through the end with me, i really appreciate it! If only we knew a simple repair from the XP cd would take care of things...

---

### Post by molly_001 on 2006-07-17
We knew that fixmbr (when directed from a Repair Console DOS prompt) would fix your MBR, but I believe you did not have an XP installation CD on hand at the time.

In any case, you are now in a perfect position to forge ahead with a dual boot of Ubuntu and Windows XP.  Just ask if you want an overall plan for this, as I have done it on several machines now.

But ... for the moment ... by all means, no matter what, get thee to a backup of that data you had wanted to keep forever. :-)

---

### Post by Willson on 2006-07-17
haha yes of course, backing up EVERYTHING right now.. I will probably try to install ubuntu tomorrow night. I am dead tired from work today, ah Monday's.

---

### Post by molly_001 on 2006-07-17
No problem.  Don't forget that to dual boot your Windows and Ubuntu, you should install Windows first and let it write onto 100% of the available hard drive space.

Later you will use GParted to reduce the size of that Windows NTFS partition, and then use the text installer from the Alternate Install CD to handle the rest of the partition creations.

---

### Post by SilverBear on 2006-07-24
Hello, molly_001 & Willson,

I've been away from the forums for a while, so I hope things are going OK with your new attempt at installing, Willson.  Glad to hear your XP partition came back.  

Computer-related activities since I posted here last:
installed Myah OS 2.1, Dream Linux 2.0 and Mepis 6.0 on my main desktop machine, on top of already existing Windows 2000 and SUSE 10.1.  Have had problems getting Myah to recognize SATA drives, and have done some comparing notes with the guy who developed the distro.  

Also installed Myah on my laptop, so it is a dual-boot XP and Linux.  Since there is just one IDE HDD, the SATA issue is irrelevant, and Myah does a good job of auto-detecting my wireless connection. 

If you want any further advice, Willson, you can look me up on ICQ. When I started getting spam there too, I instituted pre-authorization, so you'll need to submit a request to me to authorize before we can chat. 

BTW, after you get Dapper running, you might try "Automatix" as a one-shot installer for a number of useful programs and all the audio & video codecs you'll probably need.  I've used it on my family's install of Dapper a few weeks ago, and last night on Mepis 6, and I experienced no problems with either.  I mention that, because some people believe it is too risky a script and prefer "Easy Ubuntu."

Here are the links to both, so you can judge for yourself which you might prefer:
Automatix
[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

Easy Ubuntu
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

all the best,
SilverBear

---

