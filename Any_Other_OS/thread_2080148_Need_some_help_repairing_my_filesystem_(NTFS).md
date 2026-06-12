---
title: "Need some help repairing my filesystem (NTFS)"
date: 2012-11-03
forum: Any Other OS
---

### Post by Guises on 2012-11-03
All right, so I have a Windows XP partition and everything was running fine. I decided to reboot and after loading the BIOS I was left with a black screen, no Windows logo, no further progress. Interestingly, it was projecting black - my monitor did not go to standby. This implies to me that it was waiting on some process, but I let it run for a long time with no result.

I try some boot disks. All of my Linux-based tools work fine, but they tell me that something's wrong with my filesystem in my Windows partition and I need to boot into Windows and run "chkdsk /f". None of my Windows-based boot disks will boot, they all hang just like before, so I can't do that. I'm here in the Ubuntu forum because it's been suggested to me that I should try an Ubuntu boot disk and run fsck, but it's giving me this error:

"fsck: fsck.ntfs: not found"

Checking, I can verify that ntfs-3g is installed. So. If anyone could tell me how to resolve this error, or perhaps offer another approach on how to resolve my initial problem, I'd be most appreciative.

---

### Post by howefield on 2012-11-03
Thread moved to "*Other OS/Distro Talk*" forum.

---

### Post by Guises on 2012-11-03
Well, given that my question was basically, "How can I repair my NTFS partition using Ubuntu?" I'm not sure the Other OS forum was really correct. It's not especially important though, I'll take help wherever it comes.

---

### Post by jerome1232 on 2012-11-03
You can try using ntfsfix, but it doesn't fix very many problems and well you should really use a Windows repair disc to fix that ntfs partition.

You could try grabbing a Windows 7 installation disc to get into a repair console and run chkdsk

Here is a link with official Win 7 iso's. [http://en.community.dell.com/support-forums/software-os/w/microsoft_os/3316.2-1-microsoft-windows-7-official-iso-download-links-digital-river.aspx](http://en.community.dell.com/support-forums/software-os/w/microsoft_os/3316.2-1-microsoft-windows-7-official-iso-download-links-digital-river.aspx)

---

### Post by skstid2012 on 2012-11-03
> **Guises said:**
> All right, so I have a Windows XP partition and everything was running fine. I decided to reboot and after loading the BIOS I was left with a black screen, no Windows logo, no further progress. Interestingly, it was projecting black - my monitor did not go to standby. This implies to me that it was waiting on some process, but I let it run for a long time with no result.

I try some boot disks. All of my Linux-based tools work fine, but they tell me that something's wrong with my filesystem in my Windows partition and I need to boot into Windows and run "chkdsk /f". None of my Windows-based boot disks will boot, they all hang just like before, so I can't do that. I'm here in the Ubuntu forum because it's been suggested to me that I should try an Ubuntu boot disk and run fsck, but it's giving me this error:

"fsck: fsck.ntfs: not found"

Checking, I can verify that ntfs-3g is installed. So. If anyone could tell me how to resolve this error, or perhaps offer another approach on how to resolve my initial problem, I'd be most appreciative.

I have several questions that I would like you to answer before we can get to the root of what's causing your problem.  First, which boot disks did you try?  Were they boot disks specifically for Windows XP?  Were they boot disks for earlier versions of Windows or newer versions of Windows?  It's important to use the correct boot discs for the correct OS when it comes to Microsoft based OS's.

Why did you decide to reboot? Did you put off rebooting after a Windows update? There are specific Windows updates that cause the problem that you're describing.  The upgrade to SP3 is one of those updates.  Do you know if your computer recently updated?

While tools from other OS's can help with determining and troubleshooting problems for Microsoft OS's, they don't have the tools to fix those problems.  While I'm waiting on your response, I'm going to look through my boot disk tools. There's a specific program that might be able to help you restore things ... although, part of me is screaming, "reinstall Windows XP."

---

### Post by Elfy on 2012-11-03
If you have several questions to ask before you can help then you really joined the wrong forum

This section is an add on and once the change to vb4 is complete threads here could well be closed before you get back.

While we are happy to have this section - this is not, and was never intended to be, a place for windows support.

---

### Post by skstid2012 on 2012-11-03
> **Elfy said:**
> If you have several questions to ask before you can help then you really joined the wrong forum

This section is an add on and once the change to vb4 is complete threads here could well be closed before you get back.

While we are happy to have this section - this is not, and was never intended to be, a place for windows support.

I realize that you're a forum administrator/moderator. I'm not sure how familiar you are with technical issues, but I assure you that my questions are extremely important due to the fact that when technical issues arise certain questions must be asked to investigate what's causing the issue.  Do you want me to write a book for each resolution wasting everyone's time?  Or would you prefer me to give the specific answer for the specific problem.  More than one thing causes what this individual described and I do have several Windows based certifications ranging from Administration to Security.

"While we are happy to have this section - this is not, and was never intended to be, a place for windows support." If that's the case, then you need to change the name of this section from "Other OS" to "Other Linux Distros" and remove the link to Windows Support on the main thread at the top of this discussion forum.  The term "Other OS" is very deceiving.

---

### Post by Guises on 2012-11-03
@skstid2012: I tried to boot using Windows XP install disks (I was just trying to get to the recovery console) as well as the UBCD4Win (using the files from my Win XP install discs to create the UBCD). I couldn't boot Windows with the UBCD, but it did have a DOS version that let me run chkdsk - it told me that the partition in question was not initialized (though it did recognize that the partition was NTFS formatted) and so I couldn't run chkdsk on that partition.

This concerned me greatly, but a guy in the UBCD forum told me to try Ubuntu with FSCK, so here I am. I am now downloading the Win7 disk, per jerome1232's suggestion (thanks jerome). The newer disk could possibly work better, though it's downloading very slowly. Looks like it'll be more than a day before that's done.

I decided to reboot originally because the audio in flash was garbled (was listening to Pandora). This has happened before, I don't think it's that unusual, I think it just happens when flash is competing with something else for use of the speakers. For the sake of full disclosure: I did manually close a few processes before rebooting, hoping to resolve the conflict without rebooting, but it didn't work and I was just guessing which processes to close so I said "Eh, whatever." and rebooted.

It's conceivable that that could have messed something up, but it seems unlikely.

I eagerly await your response. Reinstalling Windows wouldn't be a big deal, but 1: I can't do that because the install disks won't boot. I'd have to format the partition to boot the install disks. and 2: I really don't want to lose what's in that partition.

---

### Post by skstid2012 on 2012-11-03
Guises,

When a Windows XP NTFS becomes uninitialized, this usually means that a sector on your hard drive is being read over and over again (because it has become bad).  What's the solution to this problem?  I would suggest that you make a ghost or clone copy of your hard drive onto another hard drive.

If you're dual booting a Linux/Windows XP on your hard drive, use Linux to restore GRUB as GRUB will give you the option to start up the Linux OS or the Windows XP OS.

If you're using XP only, use one of your XP boot disks again to restore the MBR on the new HD. Windows provides two tools to restore your MBR.  Restore the MBR on the new HD, then you'll be ready to go. This is the easiest solution.

You could reinstall Windows XP on your current HD, but there's no guarantee that will work as that your hard drive will still have the bad sector. The problem would easily be able to repeat itself.

The problem in this situation isn't the OS, it's your HD.

Edit

Also realize this, if your HD is in poor enough condition making a ghost/clone might not work. Copying the information from the bad sector might be improbable (not that its impossible).  In this case, you would have to make a new installation of Windows XP anyway.

---

### Post by Guises on 2012-11-04
Thank you very much for your help skstid2012, it looks like the Win 7 boot disk has worked. I will take your warning about my HD to heart and start backing up my data religiously.

---

