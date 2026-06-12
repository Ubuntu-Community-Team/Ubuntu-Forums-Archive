---
title: "Help please. Syncing Thunderbird email with a Windows drive"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by KeaponLaffin on 2007-09-04
1st off folks. I have looked at the other threads regarding how to do this. I've done the Profile Manager thing, but I havn't seen a post with a problem the same as mine.
Background: I'm running Feisty on it's own HD, I got Windows on a separate drive (FAT32, I think..how do I check?) I can access the Window's drive's files, copy em over to my Ubuntu drive and all that good stuff.

When I only had 1 drive I had Ubuntu installed via Wubi, and the Profile Manager trick worked then.
So now, I setup a ThunderBird profile in Ubuntu that points to my Window's Thunderbird Profile. However when I start Thunderbird, it gives me the error:
Mozilla-Thunderbird is already running, but is not responding. etc etc.

It doesn't give me this error when I use the default 'blank' profile on my Ubuntu drive

So I'm thinking maybe it's a security issue? But I'm still a noob and my CHMOD expertise is still limited to making scripts executable. One issue may be: When I 1st look at my drives, like in 'Places' the Windows Drive is named something like '70.7 GB Volume'..however when I then access it to look at the files..the name changes to simply 'disk'

Any help would be very appreciated. I love Ubuntu, love the community, you folks are the greatest......And I just got Compiz working, I dunno how I lived without a 3D Desktop Cube before, and it doesn't take 30 mins to start up or shut down. 
Ubuntu has singlehandedly made a Believer out of me. Go OpenSource!

---

### Post by rbprogrammer on 2007-09-04
> **KeaponLaffin said:**
> 
So now, I setup a ThunderBird profile in Ubuntu that points to my Window's Thunderbird Profile. 

when you say that do you mean that the thunderbird mailbox files are on the windows drive and that the linux thunderbird accesses the windows drive??

if not, then thats what i would do.. set up the windows thunderbird the way you want.  then in linux set the mailbox folder the the folder on the windows drive.

hope that helps.

---

### Post by KeaponLaffin on 2007-09-04
Yea, that's what I'm saying. The Thunderbird Profile/Email archive stuff is on my Windows drive. But when I setup my Ubuntu Thunderbird to use the files from the Windows side, it gives me that error. I can't do it the other way around (Put the mail Thunderbird Profile/Email repository on my Ubuntu drive) because Windows can't access that drive. And I still need ThunderBird on Windows to access all my emails for work purposes. 

Like I said, I'm a noob..Would it help to make a 'link' or shortcut or sumthing to the Windows directory? I don't know how to do that.

---

### Post by Obor on 2007-09-04
I have the same setup since I started Ubuntu also profile-share firefox this way as well.

I get the same error as you when my windows partition (which has my profile) is not available (e.g when my windows crashes and the partition can't get mounted properly in ubuntu or some other reason).

You say that you have write permissions for your windows partition and that should be all you need. Make sure that its mounted properly and you have write permission.

Depending on your file system[ these guides]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions") will help you with mounting windows partitions.

Also here is little help on thunderbird profile manager if you made a mistake somewhere there [http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

---

### Post by KeaponLaffin on 2007-09-04
I don't think I have normal-user Write-Permission for the Windows drive..

I got it I got..Thanks for that link regarding Mounting Partitions. Ends up my Windows drive is NTFS, so I had to get the utility to access it and change my fstab.

Thanks alot folks. Once again, you folks are the greatest

---

