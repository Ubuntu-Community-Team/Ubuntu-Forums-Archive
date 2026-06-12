---
title: "a disk error has occurred"
date: 2012-11-30
forum: Any Other OS
---

### Post by Naughtmare on 2012-11-30
Okay so here is the deal. I am a somewhat average computer user, and today I've stumbled at a dead end.
Last night, I left a program running which finished this morning, what program Ill refrain from posting because it is irrelevant. Now I had VLC +  2 Folders open, and I was watching James Bond the Golden Finger :popcorn:.
This morning, the computer was at its worst, so I figured Ill turn if off completely and let it cool off. Its a somewhat average computer for its age. 
Well when I turned it back on: 
a disk error has occurred
That is what it keeps saying. 
Thus I am here, because I was able to run ubuntu from an old experiment I had on a CD. It seems to work after a couple of tries but originally it too was a pain in the rear.
I really need to fix this as my harddrive is completely fine. I accessed it through Ubuntu and backed up anything that was required. Now I am here begging for help to fix an issue with Win7 on a linux based OS forum... I dont know where else to go :(



EDIT:
Okay I think I see something relevant. My HDD is partitioned into C & D, C being win7 files and etc, and D being my own. Well in Ubuntu I only see the D partition.

---

### Post by TheFu on 2012-11-30
> **Naughtmare said:**
> Okay so here is the deal. I am a somewhat average computer user, and today I've stumbled at a dead end.
Last night, I left a program running which finished this morning, what program Ill refrain from posting because it is irrelevant. Now I had VLC +  2 Folders open, and I was watching James Bond the Golden Finger :popcorn:.
This morning, the computer was at its worst, so I figured Ill turn if off completely and let it cool off. Its a somewhat average computer for its age. 
Well when I turned it back on: 
a disk error has occurred
That is what it keeps saying. 
Thus I am here, because I was able to run ubuntu from an old experiment I had on a CD. It seems to work after a couple of tries but originally it too was a pain in the rear.
I really need to fix this as my harddrive is completely fine. I accessed it through Ubuntu and backed up anything that was required. Now I am here begging for help to fix an issue with Win7 on a linux based OS forum... I dont know where else to go :(



EDIT:
Okay I think I see something relevant. My HDD is partitioned into C & D, C being win7 files and etc, and D being my own. Well in Ubuntu I only see the D partition.

I don't understand what the issue is.  "at its worse" is not descriptive in a way that we can help solve.  A few specifics and exact details would be helpful.  Think about copy/pasting log errors as a first step to getting more help.

Also, if your title were clearer, you might find more people able to help. I know next to nothing about Windows.

---

### Post by dannyboy79 on 2012-11-30
im not sure what you're asking for but if it's help with windows 7, you won't get that help within UBUNTU forums.

---

### Post by Naughtmare on 2012-11-30
> **dannyboy79 said:**
> im not sure what you're asking for but if it's help with windows 7, you won't get that help within UBUNTU forums.

Pretty sure I made it clear but okay.
Computer went super freaking slow. Like as though I was using up 90%+ of my CPU so I decided to restart it, but upon restarting it came up with this error:
a disk error has occurred, press ctr alt del to restart
and when I do it just loops non-stop.
And like I mentioned in the edit:
My HDD is partitioned into C & D, C being win7 files and etc, and D being my own. Well in Ubuntu I only see the D partition.
Is C corrupted then if its not coming up at all?

---

### Post by Elfy on 2012-11-30
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Naughtmare on 2012-11-30
I posted here because I need help with the HDD issue I am having, it wont allow me to run into win7 but forces to stay on either CD/DVD or ctraltdel ****.
I am truly only here because I read on some forum about Ubuntu having a disk checker and thought that maybe you guys know about this.

---

### Post by dannyboy79 on 2012-11-30
Ubuntu wouldn't show you the "C" drive as it looks in windows 7, you can mount it with the ntfs-3g driver. You need to determine what /dev/sdX device it is. you can use sudo fdisk -l to find out. then to mount it
mount -t ntfs-3g /dev/sdb1 /mnt/ntfs/

BUT, that won't help you run a chkdsk on it, you'll need a windows recovery console. You may be able to check a NTFS partition with linux but I am not sure how reliable it is.

---

### Post by Naughtmare on 2012-11-30
> **dannyboy79 said:**
> Ubuntu wouldn't show you the "C" drive as it looks in windows 7, you can mount it with the ntfs-3g driver. You need to determine what /dev/sdX device it is. you can use sudo fdisk -l to find out. then to mount it
mount -t ntfs-3g /dev/sdb1 /mnt/ntfs/

BUT, that won't help you run a chkdsk on it, you'll need a windows recovery console. You may be able to check a NTFS partition with linux but I am not sure how reliable it is.

So even if i do find out and mount it theres a no way for me to get chkdsk to go? See the thing is I can get a win7 disk. But the original disk gives me an error code 5 saying I cannot start from cd/dvd. I dont see why that happens but it does.


Ill keep trying but nothing can be done. Anyway thanks so much for all the replies :) 
Bye

---

### Post by TheFu on 2012-11-30
If you have a disk issue for a Linux disk, use Linux tools to fix it.
If you have a disk issue for a Windows disk, use Windows tools to fix it.

NTFS is Windows.
FAT32 is Windows.
EXT2, EXT3, EXT4, XFS, JFS,  .... are Linux.

For Windows, you'll want to get into a "recovery console" - if you don't know what that is, google.  Then you want to run both
* scandisk
* chkdsk
on all your Windows partitions.  If you've encrypted any of these partitions, I hope you have a good backup. This applies to Linux too.

I'm not convinced that your HDD isn't having a failure.
I'm not convinced that your disk controller isn't having a failure.
I'm not convinced that your PC RAM isn't having a failure.

A slow PC can mean many hundreds of things are wrong or just failing.

There are many, many other faults that could cause disk corruption, but without log files, we can't possibly guess with any level of accuracy.

Facts and data are needed.  

The best solution for most issues is to restore from a good backup set, determine the root cause of the problem - either software or hardware, replace the offending item, restore from a good backup set and continue computing happily.  Without a good backup, we're sorta stuck.

---

### Post by deadflowr on 2012-11-30
>  Now I am here begging for help to fix an issue with Win7 on a linux based OS forum... I dont know where else to go


[SevenForums]("http://www.sevenforums.com/")

---

### Post by Naughtmare on 2012-11-30
Okay another thing is for me to be able to access recovery through win7 I need the Disk
I am alloted a free win7 through my Uni but .pkg or w.e is not readable through Ubuntu. Anyone know of a guide on how I can do it;;
The website for the download says the following:

[LIST=1]
[*]                                                      Download the Secure Download Manager (SDM) installation file                             [[IMG]http://static.onthehub.com/prod/images/sdm/question-icon.png[/IMG]]("http://e5.onthehub.com/WebStore/Account/SdmDownloadFaq.aspx?ws=eea405de-ea9b-e011-969d-0030487d8897")                         
                         Download SDM                          	                              (If you have completed this step previously, go to step 3)                                                      
                          
[*]                                                      Locate the file from step 1 and run it to install the SDM                             [[IMG]http://static.onthehub.com/prod/images/sdm/question-icon.png[/IMG]]("http://e5.onthehub.com/WebStore/Account/SdmDownloadFaq.aspx?ws=eea405de-ea9b-e011-969d-0030487d8897")                         
                          
[*]                                                      Download the .SDX file for your order                             [[IMG]http://static.onthehub.com/prod/images/sdm/question-icon.png[/IMG]]("http://e5.onthehub.com/WebStore/Account/SdmSdxDownloadFaq.aspx?ws=eea405de-ea9b-e011-969d-0030487d8897")                             
                         Download .SDX                          
[*]                                                      Locate the file from step 3 and open it to download your software order                             [[IMG]http://static.onthehub.com/prod/images/sdm/question-icon.png[/IMG]]("http://e5.onthehub.com/WebStore/Account/SdmDownloadingSoftwareFaq.aspx?ws=eea405de-ea9b-e011-969d-0030487d8897")                         
[/LIST]

---

### Post by MadmanRB on 2012-11-30
Maybe I can assist as I do dual boot win7
You are saying that your computer isnt booting windows correct?
And that for some reason Ubuntu isnt detecting it?
Hmm, do you have the proper NTFS configuration?
How many hard drives are you running?

---

### Post by Naughtmare on 2012-11-30
> **MadmanRB said:**
> Maybe I can assist as I do dual boot win7
You are saying that your computer isnt booting windows correct?
And that for some reason Ubuntu isnt detecting it?
Hmm, do you have the proper NTFS configuration?
How many hard drives are you running?

I dont dual boot I am using Ubuntu as a back up because win7 wont load at all. It gives me an error I mentioned in the OP.
What happens now is I am trying to get a win7 cd through the use of my University because I get a free win7 prof. but .pkg files arent usable. Im using Wine atm to have it work but its a bitch.

What I basically need to do is this:
[http://askubuntu.com/questions/152102/how-can-i-download-windows-7-dvd-installers-from-ubuntu](http://askubuntu.com/questions/152102/how-can-i-download-windows-7-dvd-installers-from-ubuntu)
But I have no idea what that guys is talking about.

---

### Post by MadmanRB on 2012-11-30
Okay well there is the strong possibility that your HDD was on its last legs.
Are you running ubuntu on a USB drive or something?

---

### Post by Naughtmare on 2012-11-30
> **MadmanRB said:**
> Okay well there is the strong possibility that your HDD was on its last legs.
Are you running ubuntu on a USB drive or something?

I dont doubt that but I really hope it isnt... :( I am still able to access the D partition of the said HDD but anyway.
I'm running it on a CD i had from a while back. I believe v11 something?
By the way, can I do what I posted in the previous post?
this?:
[http://askubuntu.com/questions/152102/how-can-i-download-windows-7-dvd-installers-from-ubuntu](http://askubuntu.com/questions/152102/how-can-i-download-windows-7-dvd-installers-from-ubuntu)

---

### Post by MadmanRB on 2012-11-30
Well there is a chance that your HDD died, if ubuntu isnt picking it up its a chance no windows install will work

---

### Post by kiyop on 2012-12-01
The OP; Naughtmare's HDD may be close to ( or is now maybe ) out of order.
But how about checking the output of dmesg and so on?
```
dmesg
fdisk -lu

```I do not use ubuntu so often, but even I know there are good tools to check HDD, like palimpsest ([gnome-disk-utility]("http://packages.ubuntu.com/quantal/gnome-disk-utility")), smartmontools, and tool to recover files, like testdisk, photorec, and so on.

As for SDM, why not asking at Windows 7 support or Windows Forum or SDM forum?
[http://e5.onthehub.com/WebStore/Account/SdmDownloadFaq.aspx?ws=eea405de-ea9b-e011-969d-0030487d8897&JSEnabled=1](http://e5.onthehub.com/WebStore/Account/SdmDownloadFaq.aspx?ws=eea405de-ea9b-e011-969d-0030487d8897&JSEnabled=1)
> The following operating systems and browsers are supported:

                 
[LIST]
[*]Windows XP
[*]Windows Vista
[*]Windows 7
[*]Mac OS X v10.4 - v10.7
[/LIST]
       
[LIST]
[*]Internet Explorer
[*]Firefox
[*]Chrome
[*]Safari
[/LIST]
Wine maybe works, but ... Naughtmare, you should contact to Microsoft Support first.

Did you read [http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/](http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/) ?
I am not sure if the above Linked iso's are legal or illegal or malware (virus). ;)

---

### Post by ugm6hr on 2012-12-01
> **kiyop said:**
> The OP; Naughtmare's HDD may be close to ( or is now maybe ) out of order.

This is the most likely scenario.

HDs on their last legs behave unusually - I have suffered the exact same situation where I could access (and backup) files booting from a LiveCD, but the HD would not boot. In fact, this was the exact situation that prompted me to try Linux in the first instance.

My suggestion:
Back up all files (sounds like you have already done this).
Wipe the HD.
Try installing Windows again from scratch.

If this doesn't work, it's a hardware fault. Take things forward from there...

---

### Post by Mark Phelps on 2012-12-01
> **Naughtmare said:**
> So even if i do find out and mount it theres a no way for me to get chkdsk to go? 
CHKDSK runs only in Windows and, despite what you may have been told, there is no equivalent you can run in Linux.

You need to use the sevenforums link.  Their forums have tutorials that you can follow, including how to boot into command line from the CD to do some repairs.

---

### Post by viper250 on 2012-12-02
download hirens boot cd and use its burning program to write the cd.
once you have a boot cd boot it and start minixp
this will start minixp and give you access to read, diagnose and possibly repair the problems with the drive.
it can even repair grub errors (which by the way sounds like the problem you are having)

---

