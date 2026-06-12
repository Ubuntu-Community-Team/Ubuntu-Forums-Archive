---
title: "Win7: backing up just the bare minimum needed"
date: 2011-06-21
forum: Any Other OS
---

### Post by hanzj on 2011-06-21
Hello,
A  new Windows 7 Home laptop does not come with any Win7 DVDs to use in case of virus attack. 

So we would like to create some backups. According to [http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/backup-system-image-vs-full-back-up-i-ran-both-and/ca611f77-fa88-4b7d-92fa-fbe9d6690450](http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/backup-system-image-vs-full-back-up-i-ran-both-and/ca611f77-fa88-4b7d-92fa-fbe9d6690450) there are two types of backup: Full Backup and System Image. 

What do I need to backup just the required Win7 files? I don't care about backing up my own files (media, pics, documents, etc.) I also don't care about backing up the stuff that came pre-installed with the laptop, like the trial version of MS office or the trial version of Norton Security or the games. I also don't want to backup stuff I've added after turning on the computer, like MS Security Essentials or VLC or Gimp.

Just the really bare minimum needed in case my computer wiped clean accidentally. Thank you.

---

### Post by NRWlion on 2011-06-22
Good Morning hanzj,

first of all it would be good to know whether you are able to divide the difference between the two types of backup described at the link you gave (no offense ;) just asking to enable you to understand my reply!)

A "System" Image is an exact copy of your HDD containing all necessary files to run Win after re-installation. Choosing the "Full Backup" Option means to choose the folders you want to be backed up yourself. 

If I were you, I would take the System Image to have all necessary files / drivers to run Windows. Ok, you get the folders with the pre-installed programms as well, but you can choose the time for your back-up yourself. 

So - this is how i would do this! - I would install the Windows and set all Programms how I need them and then burn a system image to have the win7 like I need it. This safes you a lot of time from installation / loading drivers etc.) 

Have a nice Day!
NRWlion

---

### Post by mips on 2011-06-22
> **hanzj said:**
> 
A  new Windows 7 Home laptop does not come with any Win7 DVDs ...

There should be a system restore partition on the HDD from which you should be able to create Win7 DVD install media.

What brand/model laptop is it?

---

### Post by NRWlion on 2011-06-22
> **mips said:**
> There should be a system restore partition on the HDD from which you should be able to create Win7 DVD install media.

What brand/model laptop is it?

Well I was assuming this partitionhad been deleted.

NRWlion

---

### Post by YesWeCan on 2011-06-22
Hi hanzj, like your photo.
In addition to what NRWilon wrote, you could also temporarily move the data you don't need for your restore image somewhere else so is not included. Uninstall the apps and games you don't need.
I gather you are trying to minimize the number of DVDs required for the image backup.

---

### Post by hanzj on 2011-06-22
> **mips said:**
> There should be a system restore partition on the HDD from which you should be able to create Win7 DVD install media.

What brand/model laptop is it?

There should be? Where? Are you sure?
Toshiba Satellite

---

### Post by hanzj on 2011-06-22
> **NRWlion said:**
> Good Morning hanzj,

first of all it would be good to know whether you are able to divide the difference between the two types of backup described at the link you gave (no offense ;) just asking to enable you to understand my reply!)

A "System" Image is an exact copy of your HDD containing all necessary files to run Win after re-installation. Choosing the "Full Backup" Option means to choose the folders you want to be backed up yourself. 

If I were you, I would take the System Image to have all necessary files / drivers to run Windows. Ok, you get the folders with the pre-installed programms as well, but you can choose the time for your back-up yourself. 

So - this is how i would do this! - I would install the Windows and set all Programms how I need them and then burn a system image to have the win7 like I need it. This safes you a lot of time from installation / loading drivers etc.) 


How can I just backup the operating system and necessary files, WITHOUT backing up extra programs? 

Also, I plan on using a third party program. I've downloaded EASEUS Todo Backup. I've reached a screen prompting me to make  a decision I'm unable to make. Please see attached screenshot.

---

### Post by hanzj on 2011-06-22
> **mips said:**
> There should be a system restore partition on the HDD from which you should be able to create Win7 DVD install media.

mips, 
is my "system-restore partition" showing in this screenshot? [http://ubuntuforums.org/attachment.php?attachmentid=195778&stc=1&d=1308798103](http://ubuntuforums.org/attachment.php?attachmentid=195778&stc=1&d=1308798103)

If so, is it as simple as copying that 9.72 GB HDDRECOVERY partition to a DVD (or set of DVDs)? 

Is that 9.72 GB HDDRECOVERY partition what my computer was like when I first turned it on for the first time? In other words, is that partition like a "fresh install"?

---

### Post by hanzj on 2011-06-22
I searched the net for "HDDRECOVERY" and found that the partition is probably something that Toshiba did. I was wondering if you folks think that simply going through the Toshiba Recovery Media Creator program is good enough, or whether I should still go ahead and use another backup program (whether Microsoft, Macrium Free Reflect, or EASEUS Todo backup)?

Thanks.


UPDATE: It's too bad that the program forces me to use either DVDs or USB Flash. I would have preferred putting the backup files onto the hard drive, then uploading them to the cloud. Is this possible? If so, how?

---

### Post by oldfred on 2011-06-22
If your computer totally crashes how will you load the cloud on your machine?

I would make the recovery DVDs and separately have the windows recovery. I am surprised the windows recovery requires a DVD. The one I downloaded which was just a bare recovery environment was only about a third of a CD. They do not have downloads available, so you need to have bootable repair CD/DVD for windows.

You also should have a current version of Ubuntu's liveCD or USB. Then you have repair disks for all installed systems.

In Ubuntu & windows I like to separate system from Data. And I have seen some post that you should do the same in windows, but it is more difficult as many applications will only write data into the C: fixed location. I had to create a .bat file to copy data to my windows shared data partition for those applications when I was using windows more.

---

### Post by hanzj on 2011-06-23
> **oldfred said:**
> If your computer totally crashes how will you load the cloud on your machine?

I would make the recovery DVDs and separately have the windows recovery. I am surprised the windows recovery requires a DVD. The one I downloaded which was just a bare recovery environment was only about a third of a CD. They do not have downloads available, so you need to have bootable repair CD/DVD for windows.

You also should have a current version of Ubuntu's liveCD or USB. Then you have repair disks for all installed systems.

In Ubuntu & windows I like to separate system from Data. And I have seen some post that you should do the same in windows, but it is more difficult as many applications will only write data into the C: fixed location. I had to create a .bat file to copy data to my windows shared data partition for those applications when I was using windows more.

Oldfred,
thanks for the reply.
1. I'd load the cloud on some other computer. I like the cloud because 
[LIST]
[*]it's everywhere I go
[*]the data won't degrade over time
[*]it's easy to find when I need it
[/LIST] 

2. What do you mean by windows recovery? How's that different from Recovery DVDs?

3. Why did you mention Ubuntu?

---

### Post by oldfred on 2011-06-23
3. I always mention Ubuntu.:) But I always suggest current version  recovery disks/liveCDs for every system you have installed and I prefer keeping systems separate from data. Both for ease of backup and reinstall of system and a slight performance if system is in a very large 1GB partition for example, drive has to potentially look for the most used system files anywhere on drive. Data is used less frequently and can be anywhere on drive. 

Windows recovery is just a recovery environment to make windows repairs. It will not restore a system. 

The vendor recovery is a image of the system just as you purchased it. It also is not a full install, because they are too cheap to burn a disk and instead take part of you stated hard drive space as the image. I think Microsoft also does not want full install disks available.

Make your own recoveryCD:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by mips on 2011-06-23
> **hanzj said:**
> mips, 
is my "system-restore partition" showing in this screenshot? [http://ubuntuforums.org/attachment.php?attachmentid=195778&stc=1&d=1308798103](http://ubuntuforums.org/attachment.php?attachmentid=195778&stc=1&d=1308798103)

If so, is it as simple as copying that 9.72 GB HDDRECOVERY partition to a DVD (or set of DVDs)? 

Is that 9.72 GB HDDRECOVERY partition what my computer was like when I first turned it on for the first time? In other words, is that partition like a "fresh install"?

YES, that's it!

There should be software on your laptop or toshiba site that will create installable DVD's from that partition. Simply just copying the partition to DVD won't do this although you might also want to image that partition, compress it and split it across two DVD's as a backup should you ever lose that partition but also back it up to an external HD or something.

You need to create DVD's from that partition or you might be able to recover directly from it. I dunno how you boot from it but maybe there is an option in the bios or something. I suggest you check the Toshiba site for info. Using that partition will restore your laptop to it's original state as per when you switched it on for the very first time.

I would not bother backing up your existing system. Best to do a fresh install and then image the entire drive at the stage where you are happy with what what's installed. This way you end up with a clean environment every time you restore it.

Doing the above you can upload the DVD images, recovery partition images and your own custom partition images to wherever you want.

---

### Post by hanzj on 2011-06-23
> **mips said:**
> YES, that's it!

There should be software on your laptop or toshiba site that will create installable DVD's from that partition. Simply just copying the partition to DVD won't do this although you might also want to image that partition, compress it and split it across two DVD's as a backup should you ever lose that partition but also back it up to an external HD or something.

You need to create DVD's from that partition or you might be able to recover directly from it. I dunno how you boot from it but maybe there is an option in the bios or something. I suggest you check the Toshiba site for info. Using that partition will restore your laptop to it's original state as per when you switched it on for the very first time.

I would not bother backing up your existing system. Best to do a fresh install and then image the entire drive at the stage where you are happy with what what's installed. This way you end up with a clean environment every time you restore it.

Doing the above you can upload the DVD images, recovery partition images and your own custom partition images to wherever you want.

Yes, the Toshiba came with "Toshiba Recovery Media Creator". It needs 4 DVDs, 3 for the Recovery discs and 1 for the Windows 64-bit environment, whatever that means.

When you say "fresh install" do you mean "using the recovery discs"?
Now to find a web service offering free 10 gigabytes of cloud storage. (Amazon Cloud has 5GB max for free, and Google Docs has 1GB for free.

---

### Post by mips on 2011-06-23
> **hanzj said:**
> 
When you say "fresh install" do you mean "using the recovery discs"?

Now to find a web service offering free 10 gigabytes of cloud storage. (Amazon Cloud has 5GB max for free, and Google Docs has 1GB for free.

Yes.

Good luck, let us know if you find any. This is only a viable option if you have fast internet access I reckon.

---

### Post by hanzj on 2011-06-23
> **mips said:**
> YES, that's it!

There should be software on your laptop or toshiba site that will create installable DVD's from that partition. Simply just copying the partition to DVD won't do this although you might also want to image that partition, compress it and split it across two DVD's as a backup should you ever lose that partition but also back it up to an external HD or something.
[...]
Doing the above you can upload the DVD images, recovery partition images and your own custom partition images to wherever you want.
If I wanted to save DVDs, how can I get the HDDRecovery partition copied to the cloud? Is imaging necessary? What is imaging, and why can't I just upload the 9-gigabyte partition to the cloud?

---

### Post by mips on 2011-06-23
> **hanzj said:**
> 
What is imaging, and why can't I just upload the 9-gigabyte partition to the cloud?

If I wanted to save DVDs, how can I get the HDDRecovery partition copied to the cloud? Is imaging necessary? 


I'm not aware of any virtual drives in the cloud that allows you to specify the partition type & size, as far as I'm aware they only offer file storage services at this point.
You can't just copy a partition across as it does not keep it's integrity or what makes it a partition in the first place and your system will have no knowledge on how to restore that partition if it's no longer in it's original format.

Image the partition. Imaging refers to making a bit for bit duplicate image of the original partition with all it's attributes in tact. Restoring from the image file is a simple procedure and essentially the reverse of creating the image. Yes I would say imaging is necessary and the better route to go. You can use utilities like dd, clonezilla, acronis true image, norton ghost, macrium reflect etc etc to image a partition or entire drive with.

Oh, Windows Live [SkyDrive]("http://explore.live.com/windows-live-skydrive") will give 25GB of free online storage but file size is limited to 100MB per file which is useless in this scenario.

---

### Post by hanzj on 2011-06-23
So in the worst-case scenario of everything on my hard-drive being deleted, what is the easiest solution: using an imaged partition? Or using recovery DVDs?

---

### Post by mips on 2011-06-23
> **hanzj said:**
> So in the worst-case scenario of everything on my hard-drive being deleted, what is the easiest solution: using an imaged partition? Or using recovery DVDs?

If you don't have a working OS or access to a networked computer the image is useless to you floating in the cloud. The image will also have to be transferred via usb stick or external hard drive. It's still however a good idea to keep a backup image of this partition in case you lose the drive etc

The easiest way to restore your system is via DVD discs you created from this partition with the Toshiba software. You don't need an OS, network or another computer to do this, just the discs will be enough.

---

### Post by hanzj on 2011-06-23
I'm somewhat confused. 
If I get access to the imaged partition and I want to use that on a completed wiped-out hard drive (a hard drive without any files remaining), what are the steps to make the computer "like new" again?

---

### Post by mips on 2011-06-23
Restore the partition. Go read up on how clonezilla for example works.

We're going in circles here, hopefully someone else would be able to help you.

---

### Post by YesWeCan on 2011-06-23
I like to mention Ubuntu too. :) Using U to make an image file of your entire Windows disk that can be copied to a new disk is easy peasy. It's a one-liner in linux.

What's tricky is your requirement to pick and choose which Windows applications are included in the image. It almost sounds like you want a means to make a vanilla copy of Windows as a backup.

Have you visited a Windows forum to get some more ideas?

---

