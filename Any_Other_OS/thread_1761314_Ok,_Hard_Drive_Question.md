---
title: "Ok, Hard Drive Question"
date: 2011-05-18
forum: Any Other OS
---

### Post by TAspr on 2011-05-18
I have one Hard Drive, a 320 GB Windows 7 Drive and purchased a 500 GB one as well that I have not installed yet.  I would like to transfer windows 7 on the 500 GB drive and leave the existing 320 GB for Ubuntu.  Is it possible to do this wihtout screwing things up?  Is there a utility to make this happen as well as erasing the drive after the transfer of Windows 7 from the 320 GB drive?

---

### Post by frankbooth on 2011-05-18
It's very possible.

In your case, install Windows7 on your new 500gb drive. Move the data you want to save from the 320gb drive to the 500gb drive.

Then  boot the Ubuntu installation CD and choose to use the entire 320gb disk when partitioning.

---

### Post by prshah on 2011-05-18
> **TAspr said:**
> I would like to transfer windows 7 on the 500 GB drive and leave the existing 320 GB for Ubuntu.  Is it possible to do this wihtout screwing things up? 

This can be done, but it is tricky and a little difficult for a variety of reasons.

a) I have no idea how licensing issues come into play.
b) You can attach the 500GB HDD, then boot into a linux live CD, and install and use any of the following to transfer your W7 installation to the 500GB:
[indent]i) dd (Eg, sudo dd if=/dev/sda of=/dev/sdb bs=32M), etc
ii) ntfsclone command
iii) partimage (Partition imager and restorer)
[/indent]
c) After the cloning is done, unattach the 320GB, attach the 500GB  in it's place (recommended, but not required), and attempt to boot W7; it should boot fine (chkdsk may run 2/3 times, with reboots inbetween). Note your partition size will be the same as the 320GB, but you can use W7's diskmgmt.msc utility to expand the partition to use the full 500GB.
d) You can now add the 320GB HDD back to the system, then boot using the live CD and setup linux on the new HDD.
e) All of this assumes we live in an ideal world, where HDDs don't have bad sectors, Windows licensing will smile favorably at the new HDD and gremlins will not appear.
f) Please post back if you want more details on any cloning methods; please be exceedingly careful when using "dd"; it's fast and it's powerful. THE COMMAND I HAVE GIVEN IS ONLY AN EXAMPLE; please do not run it blindly without understanding it.
g) All at your own risk only, sorry.

---

### Post by Hedgehog1 on 2011-05-18
+1 on using **dd** or **ddrescue** (if you have any bad sectors) to completely copy the smaller drive to the larger drive, and then expanding the last partition on the larger drive to fill the drive.

I used ddresuce to move the dual boot of Win7 & Ubuntu from the 640 gig drive with bad sectors to a new 1tb drive.

I did not have to reinstall anything - Windows and Ubuntu booted perfectly on the new drive - the PC had no idea the 'drive exchange' even happened!

The Hedge

:KS

---

### Post by Elfy on 2011-05-18
Thread moved to Other OS/Distro Talk.

---

### Post by TAspr on 2011-05-18
> **prshah said:**
> This can be done, but it is tricky and a little difficult for a variety of reasons.

a) I have no idea how licensing issues come into play.
b) You can attach the 500GB HDD, then boot into a linux live CD, and install and use any of the following to transfer your W7 installation to the 500GB:[INDENT]i) dd (Eg, sudo dd if=/dev/sda of=/dev/sdb bs=32M), etc
ii) ntfsclone command
iii) partimage (Partition imager and restorer)
[/INDENT]c) After the cloning is done, unattach the 320GB, attach the 500GB  in it's place (recommended, but not required), and attempt to boot W7; it should boot fine (chkdsk may run 2/3 times, with reboots inbetween). Note your partition size will be the same as the 320GB, but you can use W7's diskmgmt.msc utility to expand the partition to use the full 500GB.
d) You can now add the 320GB HDD back to the system, then boot using the live CD and setup linux on the new HDD.
e) All of this assumes we live in an ideal world, where HDDs don't have bad sectors, Windows licensing will smile favorably at the new HDD and gremlins will not appear.
f) Please post back if you want more details on any cloning methods; please be exceedingly careful when using "dd"; it's fast and it's powerful. THE COMMAND I HAVE GIVEN IS ONLY AN EXAMPLE; please do not run it blindly without understanding it.
g) All at your own risk only, sorry.
************************************************************************
[I]b)** You can attach the 500GB HDD, then boot into a linux live CD, and  install and use any of the following to transfer your W7 installation to  the 500GB:**
[/I]
So which "Linux live" CD do I use?  Are you talking about having them both hooked up at the same time so one could be transfrerred to another?  Because after that you said,[B] [I]c) After the cloning is done, unattach the 320GB, attach the 500GB  in it's place.
[/I]
[/B]Now, what about your statement**,d) You can now add the 320GB HDD back to the system, then boot using the live CD and setup linux on the new HDD.  **Are not there going to be two conflicting hard drives?  One transferred to and one transferred from?

---

### Post by TAspr on 2011-05-18
> **Hedgehog1 said:**
> +1 on using **dd** or **ddrescue** (if you have any bad sectors) to completely copy the smaller drive to the larger drive, and then expanding the last partition on the larger drive to fill the drive.

I used ddresuce to move the dual boot of Win7 & Ubuntu from the 640 gig drive with bad sectors to a new 1tb drive.

I did not have to reinstall anything - Windows and Ubuntu booted perfectly on the new drive - the PC had no idea the 'drive exchange' even happened!

The Hedge

:KS

So, what did you do to avoid conflicts from the old drive if they were both hooked up?

---

### Post by Hedgehog1 on 2011-05-18
Once dd or ddrescue completes, power down the PC and remove the old drive.  In my case I drive became a door stop.  If your old drive is still good (and I think it is in your case) I would do this:

Remove the smaller drive and 'store' it for two weeks to be sure the new drive is OK.  after 2 weeks if everything is OK,  disconnect the new drive, plug in the old and format the old to whatever shape you want it to take.

Then both drives and live in the same system again.

***The Hedge***

:KS

---

### Post by crispy_420 on 2011-05-18
Isn't the use of dd a little overkill here? It is going to go bit by bit and move everything over, even the "empty" drive space and those files marked to be deleted. So that could take hours because you are cloning unneeded data too. Or do you need a forensic copy?

Wouldn't Clonezilla be a better option. It would only move the functional information needed to keep the system functional and operating. Depending drive space used you may be talking less than an hour.

---

### Post by prshah on 2011-05-18
> **TAspr said:**
> 
So which "Linux live" CD do I use?  Are you talking about having them both hooked up at the same time so one could be transfrerred to another?  

Are not there going to be two conflicting hard drives?  One transferred to and one transferred from?

yes, both drives should be hooked up at the same time, the 500GB preferably on a SATA port that is higher than the SATA port of the 320GB (to avoid conflicts in booting order).

You can use practically any Linux live CD, especially if you plan on using dd; or you can try the [System Rescue Live CD]("http://www.sysresccd.org/Download").

I don't really understand what you mean by two "conflicting" hard drives. If the cloning has gone well, you should have two "complimentary" hard disks, not "conflicting". In any case, I have told that you have to remove the 320GB before booting off the 500GB (preferably attaching the 500GB to the same SATA port as the 320GB was connected to). Considering that you are removing the 320GB HDD, I don't really see what conflict you are referring to.

@crispy_420: While partimage or ntfsclone will be a better option than "dd", I prefer to use "dd" since the reading and cloning takes place simultaneously. This allows me to perform the operation unattended (eg, overnight). Further, dd is present on every Linux live CD; I don't know if the OP can manage to install repo software or download software in the live environment.

It's a matter of choice. I prefer dd. It is also considerably fast when you use the bs (BlockSize) parameter; I usually copy in 64M chunks.

---

### Post by crispy_420 on 2011-05-19
I do agree dd would be easier to come by but the [Clonezilla LiveCD]("http://clonezilla.org/") would meet the requirements needed but accomplish faster. dd may be faster to get up and running but reading/saving non-system data adds to time processing. 

The LiveCD is up and running after a few selections from menu. It can do a disc-to-disc (as requested), disc-to-image and image-to-disc. I believe it verifies data but I'm not 100% on that.

But as you said, everybody has their own favorite. My choice depends on task at hand. Not to diminish dd at all, it is great tool that can be used on the most stubborn of failing drives. This has motivated me to test each against each other when I got extra time.

---

### Post by TAspr on 2011-05-19
> **crispy_420 said:**
> Isn't the use of dd a little overkill here? It is going to go bit by bit and move everything over, even the "empty" drive space and those files marked to be deleted. So that could take hours because you are cloning unneeded data too. Or do you need a forensic copy?

Wouldn't Clonezilla be a better option. It would only move the functional information needed to keep the system functional and operating. Depending drive space used you may be talking less than an hour.

Ok, downloading Clonezilla now..

How does this need to be done then, does the new drive, 500 GB have to be added as a second drive first?

Ok, can someone layout the steps to do this specifically?

i.e., 
1) hook second drive up
2) take second drive and copy to first, etc. etc.

Sorry guys, brain is fuzzy this morning..

---

### Post by TAspr on 2011-05-19
> **Hedgehog1 said:**
> +1 on using **dd** or **ddrescue** (if you have any bad sectors) to completely copy the smaller drive to the larger drive, and then expanding the last partition on the larger drive to fill the drive.

I used ddresuce to move the dual boot of Win7 & Ubuntu from the 640 gig drive with bad sectors to a new 1tb drive.

I did not have to reinstall anything - Windows and Ubuntu booted perfectly on the new drive - the PC had no idea the 'drive exchange' even happened!

The Hedge

:KS


But DD rescue in a Linux Native application.  Which one will allow me to take the drive and copy it to another?  Please help as I am just about to do this..

---

### Post by TAspr on 2011-05-19
> **prshah said:**
> yes, both drives should be hooked up at the same time, the 500GB preferably on a SATA port that is higher than the SATA port of the 320GB (to avoid conflicts in booting order).

You can use practically any Linux live CD, especially if you plan on using dd; or you can try the [System Rescue Live CD]("http://www.sysresccd.org/Download").

I don't really understand what you mean by two "conflicting" hard drives. If the cloning has gone well, you should have two "complimentary" hard disks, not "conflicting". In any case, I have told that you have to remove the 320GB before booting off the 500GB (preferably attaching the 500GB to the same SATA port as the 320GB was connected to). Considering that you are removing the 320GB HDD, I don't really see what conflict you are referring to.

@crispy_420: While partimage or ntfsclone will be a better option than "dd", I prefer to use "dd" since the reading and cloning takes place simultaneously. This allows me to perform the operation unattended (eg, overnight). Further, dd is present on every Linux live CD; I don't know if the OP can manage to install repo software or download software in the live environment.

It's a matter of choice. I prefer dd. It is also considerably fast when you use the bs (BlockSize) parameter; I usually copy in 64M chunks.

Man alive, I booted on the system rescue CD, and Man, it is difficult.  I am sorry, I am a total nube at this.  What is the easiest utility to use?

---

### Post by TAspr on 2011-05-19
Well, I have decided to use the already 320GB drive with Windows7 and load Linux on the 500GB Drive.  Please tell me how to accomplish this, please.

---

### Post by crispy_420 on 2011-05-21
Quick question that may lead to an easy way out.

Is either drive a Western Digital model? 

They give out a customized version of [Acronis True Image Home]("http://www.acronis.com/homecomputing/products/trueimage/index.html") but a Western Digital drive must be used. It is real easy to use and works well. It can be had [here]("http://support.wdc.com/product/downloaddetail.asp?swid=119&wdc_lang=en") for free.

---

### Post by TAspr on 2011-05-21
> **crispy_420 said:**
> Quick question that may lead to an easy way out.

Is either drive a Western Digital model? 

They give out a customized version of [Acronis True Image Home]("http://www.acronis.com/homecomputing/products/trueimage/index.html") but a Western Digital drive must be used. It is real easy to use and works well. It can be had [here]("http://support.wdc.com/product/downloaddetail.asp?swid=119&wdc_lang=en") for free.

Yes, absolutely...  It worked perfectly on the Western Digital.  It made a duplicate of the partition and all, no need to do anything really.  I formatted the old drive, but did not want to use it yet as I installed Ubuntu inside of Windows, so if I have any issues, I can simply remove it, for now, but I think I will eventually move over to Ubuntu.  I am really liking this software.

Let me aask you another question, should the drive that I am not using be unpartitioned as compared to reformatting?  I know to repartition the drive is a lot faster than to reformat it as it took me a few hours to do this last night.

---

### Post by prshah on 2011-05-21
> **TAspr said:**
> I know to repartition the drive is a lot faster than to reformat it as it took me a few hours to do this last night.

Repartitioning will automatically mean re-formatting (the new partitions are unusable unless formatted). However, there is always the option of a "fast" format, which is also usually the default. A full format is only suggested in situations where you suspect there are bad sectors in the HDD.

"unpartitioning" a drive is laughably simple; from any kind of Linux session, ensure that your target hdd has no mounted partitions, then give the command```
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1 && sudo partprobe /dev/sdX
``` This will return your target drive (/dev/sdX) to a "virgin" state, even erasing the disklabel, in matter of seconds.

EDIT: Information added: If you do this, your data is still present on the HDD and can be recovered (eg by scanning for it, or by rebuilding the partition table). The drive seems blank, that's all.

---

### Post by TAspr on 2011-05-21
> **prshah said:**
> Repartitioning will automatically mean re-formatting (the new partitions are unusable unless formatted). However, there is always the option of a "fast" format, which is also usually the default. A full format is only suggested in situations where you suspect there are bad sectors in the HDD.

"unpartitioning" a drive is laughably simple; from any kind of Linux session, ensure that your target hdd has no mounted partitions, then give the command```
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1 && sudo partprobe /dev/sdX
``` This will return your target drive (/dev/sdX) to a "virgin" state, even erasing the disklabel, in matter of seconds.


Very Cool, thank you!

---

### Post by crispy_420 on 2011-05-22
Solved now?

---

