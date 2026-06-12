---
title: "[SOLVED] Adding new HD to system, want to keep fiesty install but redo windows"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Lokanna on 2007-07-26
So here goes...

After less than a week of Ubuntu, I've decided I want to keep it and use it for my every day OS.  However, I work in game retail and enjoy gaming to a huge extent.  This leaves me with the necessity to keep Windows. 

I currently have a 300gb hard drive that has C: for windows, D: for "storage" (in ntfs unfortunately), and my two linux partitions. I'm adding a 150gb Raptor drive and want THAT to be the standard ntfs windows drive.  

From there, I'd like to repartition the 300gb drive to 200gb FAT32 for a "D:" drive to store mp3s, pics, docs, etc, and have 100gb dedicated to Ubuntu.

That said; is there any way to do this (that's linux-newb friendly), while keeping the Ubuntu install?  I know, it's only been a week, but I really dig the customization I have :)  

If it's seriously too much trouble, I suppose a reformat of my current HD would be in order?  

I've got gparted installed currently and it seems to be able to create a nice partition in FAT32.  However, I need to move some of the info off of the ntfs formatted partitions (which I don't think would be too tough to do).  

Any help/advice would be immensely appreciated.  I apologize if this was asked/answered.  I checked the forums and didn't see this particular scenario posed.

---

### Post by davidsrsb on 2007-07-26
Windows blindly overwrites the MBR when it is installed and wipes the grub data.
If you don't touch the Ubuntu partitions your data is still there.
Boot on the install cd and you can see your data. It is then possible to reinstall grub onto the MBR

---

### Post by Lokanna on 2007-07-26
> **davidsrsb said:**
> Windows blindly overwrites the MBR when it is installed and wipes the grub data.
If you don't touch the Ubuntu partitions your data is still there.
Boot on the install cd and you can see your data. It is then possible to reinstall grub onto the MBR

What would happen if I disconnected the original HD containing the ubuntu install and windows, then reinstalled windows on the new HD, and then reconnected the previous HD.  I'd then have two conflicting MBRs, correct?

---

### Post by Vague on 2007-07-26
> **Lokanna said:**
> What would happen if I disconnected the original HD containing the ubuntu install and windows, then reinstalled windows on the new HD, and then reconnected the previous HD.  I'd then have two conflicting MBRs, correct?

That's the way I would do it.  Then just make sure you're booting from the Ubuntu drive first, and add an entry for Windows to GRUB's menu.lst.  I'm pretty sure that will work.  Alternatively, you could just disconnect your Ubuntu drive whenever you boot into Windows, and vice versa, but that really defeats the purpose of that storage partition.

---

### Post by Lokanna on 2007-07-26
> **Vague said:**
> That's the way I would do it.  Then just make sure you're booting from the Ubuntu drive first, and add an entry for Windows to GRUB's menu.lst.  I'm pretty sure that will work.  Alternatively, you could just disconnect your Ubuntu drive whenever you boot into Windows, and vice versa, but that really defeats the purpose of that storage partition.

Let's see if I'm understanding this correctly:

1. Disconnect 300gb HD.
2. Install 150gb HD.
3. Install Windows; activate, blah blah blah.
4. Re-connect 300gb HD.
5. Boot into Ubuntu and edit GRUB (I'll have to google how to do that :D) to recognize new HD.

Question: At this point, won't I have to reconfigure GRUB entirely?  The HD's will be set differently.  Instead of my partitions being 0,3,5, wouldn't that change to 1,3,5?  

After I get that sorted out, I'll want to use gparted to reset the 300gb partitions and reformat them into FAT32 for the storage partition, correct?

Once all that is done, I boot into Windows and it will then recognize the gparted FAT32 partition and I can assign it whatever drive letter I want.  Is that correct?

So then, my current set up would be:

C: 150GB Raptor (windows, NTFS)
D: 200GB (storage, FAT32)
/: 97ish GB (ext3 ... I think that's what it's called, something3 ;D)
3ish GB (Linux Swap)

Is all of that about right?  

Sorry, for all the questions, I just want to be as sure as possible this will work and I plan on doing it tomorrow 

:)

---

### Post by Vague on 2007-07-26
> **Lokanna said:**
> Let's see if I'm understanding this correctly:

1. Disconnect 300gb HD.
2. Install 150gb HD.
3. Install Windows; activate, blah blah blah.
4. Re-connect 300gb HD.
5. Boot into Ubuntu and edit GRUB (I'll have to google how to do that :D) to recognize new HD.

Essentially, that's it.  Remember that you have to boot from your Ubuntu drive and not your Windows drive, though.  And you should be able to find a ton of stuff about adding Windows to GRUB if you Google for it.  Also, I'm assuming you're installing Windows XP here.  I think Vista gets a little pickier about things like where GRUB is installed, and if you're going with Vista, I'd definitely get a second opinion before you start.  For XP, though, I think you'll be fine doing this.

> Question: At this point, won't I have to reconfigure GRUB entirely?  The HD's will be set differently.  Instead of my partitions being 0,3,5, wouldn't that change to 1,3,5?

I don't believe so.  Your partitions on your Ubuntu drive should be the same, so if you had SDA1, SDA3 and SDA5, those won't have changed, and your new partition on your new disk will be something like SDB1.  In GRUB, your Windows partition will probably be (hd1,0), reflecting that it's on your second drive in the first partition.

> After I get that sorted out, I'll want to use gparted to reset the 300gb partitions and reformat them into FAT32 for the storage partition, correct?

Theoretically, yes.  I'm not totally sure how your drive is currently partitioned, but that *should* work fine.

> Once all that is done, I boot into Windows and it will then recognize the gparted FAT32 partition and I can assign it whatever drive letter I want.  Is that correct?

That sounds right to me, yes.

> So then, my current set up would be:

C: 150GB Raptor (windows, NTFS)
D: 200GB (storage, FAT32)
/: 97ish GB (ext3 ... I think that's what it's called, something3 ;D)
3ish GB (Linux Swap)

Is all of that about right?

That sounds fine.  Of course, you have to keep in mind that those partition sizes will be different, due to the fact that hard drive manufacturers don't see GB in quite the same way your OS does.  Besides that, I think this setup should work.  I should probably add that I have never actually done this, but I'm pretty confident that what I said will work.  If you have any other questions, just ask, and good luck getting everything up and running!

---

### Post by Lokanna on 2007-07-26
> **Vague said:**
> Essentially, that's it.  Remember that you have to boot from your Ubuntu drive and not your Windows drive, though.  And you should be able to find a ton of stuff about adding Windows to GRUB if you Google for it.  Also, I'm assuming you're installing Windows XP here.  I think Vista gets a little pickier about things like where GRUB is installed, and if you're going with Vista, I'd definitely get a second opinion before you start.  For XP, though, I think you'll be fine doing this.

I'm confused (I know, like you didn't see that one coming).  What do you mean by "You have to boot from your Ubuntu drive and not your Windows drive".  If I do that, won't windows become confused because it will see two seperate windows installs?  Or are you saying I just format the existing windows install before disconnecting my current HD and placing the new one on the sata port? 

> I don't believe so.  Your partitions on your Ubuntu drive should be the same, so if you had SDA1, SDA3 and SDA5, those won't have changed, and your new partition on your new disk will be something like SDB1.  In GRUB, your Windows partition will probably be (hd1,0), reflecting that it's on your second drive in the first partition.

This is most likely confusing because I've never tried to edit GRUB before.  What does SBA(B) stand for?  And won't GRUB be looking at HD1 (which will be the newly installed 150gb HD) for the linux ext3 partition?  I want the new drive to be the #1 HD in the BIOS.. or do I?  I guess if it's listed as the first HD, GRUB won't work correctly will it, since the HD will load windows by default?  

I think that's what I'm looking for... how do I get GRUB to boot before windows?  Previously, the LiveCD took care of that for me during the Ubuntu install.  

At this point, I'm starting to think I should just copy what I want off of the current "C" drive, format it to FAT32, copy all my storage items there; plug in the new HD, reboot, and... well.. that's where I get confused because I won't understand how to bypass grub in order to allow windows to install.  

I'm confused!  ](*,)

To add to this mix, I am installing Vista.  However, I have an upgrade so I'll just throw XP on there first and then worry about Vista later :)

> Theoretically, yes.  I'm not totally sure how your drive is currently partitioned, but that *should* work fine.
...
That sounds fine.  Of course, you have to keep in mind that those partition sizes will be different, due to the fact that hard drive manufacturers don't see GB in quite the same way your OS does.  Besides that, I think this setup should work.  I should probably add that I have never actually done this, but I'm pretty confident that what I said will work.  If you have any other questions, just ask, and good luck getting everything up and running!

Correct.  I just use the round numbers.  I understand that my 320GB HD is really not that, which is why I've been saying 300.

By the way Vague, thanks a lot for your time.  I realize I'm still confused, but at least my original thought process seems to be somewhat on the right path.

---

### Post by Armman on 2007-07-26
never mind. <deleted>

---

### Post by Vague on 2007-07-27
> **Lokanna said:**
> I'm confused (I know, like you didn't see that one coming).  What do you mean by "You have to boot from your Ubuntu drive and not your Windows drive".  If I do that, won't windows become confused because it will see two seperate windows installs?  Or are you saying I just format the existing windows install before disconnecting my current HD and placing the new one on the sata port?

No, this shouldn't cause Windows any trouble.  Your Windows installs are going to be on different partitions, so as long as you point to the right one in GRUB, you'll be fine.

> This is most likely confusing because I've never tried to edit GRUB before.  What does SBA(B) stand for?  And won't GRUB be looking at HD1 (which will be the newly installed 150gb HD) for the linux ext3 partition?  I want the new drive to be the #1 HD in the BIOS.. or do I?  I guess if it's listed as the first HD, GRUB won't work correctly will it, since the HD will load windows by default?

I think that's what I'm looking for... how do I get GRUB to boot before windows?  Previously, the LiveCD took care of that for me during the Ubuntu install.

SD stands for a SCSI or SATA drive (I think all hard disks are now SD in the fstab in Feisty, but it's really not all that important for the current discussion).  A designates that it's the first drive, B that it's the second, etc.  These are actual, physical drives.  The numbers designate the partitions.  So SDA1 is the first partition on your first disk, SDB2 the second partition on your second disk, etc.  You are correct in assuming that GRUB won't work correctly if you just put the other drive first.  GRUB needs to be in the MBR of whatever disk boots first, or it won't load.  It doesn't particularly matter which drive that is, as far as I know, but since you already have GRUB on your 300 GB disk, it makes sense to boot from that one first.

> At this point, I'm starting to think I should just copy what I want off of the current "C" drive, format it to FAT32, copy all my storage items there; plug in the new HD, reboot, and... well.. that's where I get confused because I won't understand how to bypass grub in order to allow windows to install.  

I'm confused!  ](*,)

You don't need to bypass GRUB.  If you have your BIOS set to boot from CD first, you should have no trouble getting into a Windows install.  I would just suggest only having the drive you intend to install Windows on plugged in to simplify things.

> To add to this mix, I am installing Vista.  However, I have an upgrade so I'll just throw XP on there first and then worry about Vista later :)

Ah, I can't help you there, but if you search the forum for "grub windows vista" or "dual boot windows vista" you should find a lot of help.  I'm sure there are plenty of people around who can help with that, too.

> Correct.  I just use the round numbers.  I understand that my 320GB HD is really not that, which is why I've been saying 300.

Ah, good.  I was just making sure.

> By the way Vague, thanks a lot for your time.  I realize I'm still confused, but at least my original thought process seems to be somewhat on the right path.

Anytime.  I'm still very much a beginner myself, but I try to help out if I think I know the answer to something.

---

### Post by Lokanna on 2007-07-27
I think I'm beginning to make sense of this. 

I think the main issue I was confusing myself with was the fact that I'm still thinking like a Windows/DOS user and trying to replace the beginning partition (my current vista install) with a new physical drive; because I want Windows on "c:" drive and Linux on "e:"... when in reality, it's moot because Windows will use C: and Linux could give two sh...well.. you know how it ends. :)

So here's my plan...

1. Backup what I want to keep.  
2. Format the old ntfs partitions to wipe clean.
3. Disable via BIOS/disconnect current HD.  
4. Install new HD, load windows, boot, stabilize, reboot...
5. Enable prior HD and ensure it's primary HD in BIOS (ensuring boot priority)
6. Boot into Ubuntu, configure grub to point to new HD/partition.
7. Use gparted to reconfigure existing HD in manner I want
8. Stop bothering you :)  

If that's the gist of what I'm going to do, I think I've got it.  :-\"

---

### Post by Vague on 2007-07-27
I think you've pretty much got the idea of it at this point, and the hardest thing you'll probably have to do is add that entry to GRUB.

---

