---
title: "[SOLVED] Resizing causes fail to boot"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-09-24
I'll be the first to admit it - I did something stupid. I should have backed up *before* resizing partitions or doing anything like that. Well, I didn't. Here's what I *did* do.

In order to create a dual-boot system (Linux/Windows), I followed the advice some time ago of one [Matthew J Miller]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") and created a dual-boot system which didn't install GRUB to the MBR... this is important to note. The PC actually sees Windows NTLDR in the MBR and boots to Windows **_or Linux_** using boot.ini with the following settings:
> [boot loader]
timeout=30
default=C:\UBUNTU.BIN
[operating systems]
C:\UBUNTU.BIN="Ubuntu Linux"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


with Windows on  hda[0,0] and Linux on hda[0,1]. Linux is installed to an EXT3 partition. Everyhting was fine, everyone was happy, except Poser was needing more and more room, so after I'd uninstalled all the junk and cleaned up Windsows as much as I could and was *still* cramped for space, I decided to take a little from the Linux space. I booted to a Gentoo-based Rescue Disk, invoked GPartEd and resized a bit.

So now, Windows loads just fine, but when I try to get Linux to load, it just says GRUB and a blinking underline after it - freezes there. Doesn't go on to stage two. Now, I was able to get into the system and see all my Linux files using a Knoppix 5.1 cd, and all my files are safe as far as I can see. I was even able to open
 /hda2/boot/grubmenu.lst
 and edit it... but I'll have to admit, I don't really know what I'm looking at and might be doing more harm than good. I can't help but feel there is some setting in one of these files that I can change which will let Linux load again the way it used to. Is there anyone who might have an idea what I should do?

Thanks kindly to all who respond,
Robyn

---

### Post by LaRoza on 2007-09-24
Is there a reason you didn't install to the MBR? If you are afraid of not being able to boot Windows, get the Super Grub Disk, so you can easily restore the MBR for Windows (any version)

You can reinstall grub using the live cd [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Robynsveil on 2007-09-24
> **LaRoza said:**
> Is there a reason you didn't install to the MBR? 
Yes, only because Matthew J Miller was quite adamant in his article *not* to. Now, I'm not sure how to fix the problem, since it does appear that GRUB is installed to hda2, my ext3 partition. Would it be prudent to try to change how the whole thing works *now* by installing GRUB to the MBR? I'm just green enough at Linux to be concerned about stuffing it all up further. After all, I can still access my Linux files using Knoppix.

I did read that thread you suggested - it all seems straightforward enough. My question is: with my current install, will it remove the /boot/grub stuff and put it in the MBR? or do I need to manually remove it? I ask this because it does say:

> This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.


Also, will dual-booting still work, since Windows XP is installed to my boot drive?

---

### Post by logos34 on 2007-09-24
I'd run a filesystem check from the knoppix livecd:
[B]
e2fsck -y -f -v /dev/hda2[/B]

---

### Post by psusi on 2007-09-24
You need to reinstall grub because resizing the partition moved it, so now the boot sector can't find it.

---

### Post by Robynsveil on 2007-09-25
> **psusi said:**
> You need to reinstall grub because resizing the partition moved it, so now the boot sector can't find it.

Ultimately, that's what I've ended up having to do. Quite frankly, I *still* don't really feel I have even a decent grasp of how the whole thing seems to work - what I *think* is happening was this: I was using NTLDR which lived on the MBR to invoke a menu in the boot.ini file - all this based on the above-mentioned Matthew J Miller's recommendations. This boot.ini menu offered options to boot to Linux or Windows, and if I chose Linux, then it would try to find GRUB, which was installed somewhere on my ext3 partition. Now, I had resized the partitions once before, making the Windows partition smaller and the Linux one larger. That did not seem to affect the boot process. However, doing the inverse appeared, as Psusi pointed out, to put GRUB somewhere where the Ubuntu.bin file could no longer find it - it must have been at a very specific location on the partition.

Feel free to correct me if I'm wrong.

In any event, as luck would have it, I stumbled on this brilliant site: [Super Grub Disk]("http://supergrub.forjamari.linex.org/"). I downloaded the iso and burned it to CD, then ran it. I was *not* able to restore the GRUB on the Linux partition - couldn't figure out how to do that from the disk, although the instructions seemed to indicate this was a possibility. Instead, I over-wrote the NTLDR thingie in the MBR with GRUB and voila! able to boot happily to Linux and Windows again, all safe and sound.

So now, if I do run into any dramas for *whatever* reason, including re-installing Windows (which probably *will* stuff up GRUB in the MBR) I'll be able to restore things to the way they should be with this tool. Check it out, folks, and tell me what you think.

---

### Post by psusi on 2007-09-25
Glad you got it working, but I thought I would clear up a few things.  NTLDR is in a file of the same name in the root of your windows partition.  It is loaded by the boot sector code that MS installs in fat and ntfs partitions they format.  The boot sector of the active partition is loaded by the code MS places in the MBR.  When you set it up for NTLDR to chain load linux, you captured the grub boot sector and stored it in a file for NTLDR to load.  That boot sector knew the exact starting location of /boot/grub/stage2, which must have moved as a result of your resize.

---

### Post by Robynsveil on 2007-09-26
> **psusi said:**
> Glad you got it working, but I thought I would clear up a few things.  NTLDR is in a file of the same name in the root of your windows partition.  It is loaded by the boot sector code that MS installs in fat and ntfs partitions they format.  The boot sector of the active partition is loaded by the code MS places in the MBR.  When you set it up for NTLDR to chain load linux, you captured the grub boot sector and stored it in a file for NTLDR to load.  That boot sector knew the exact starting location of /boot/grub/stage2, which must have moved as a result of your resize.

So, if I understand you correctly, here's the sequence of events:
1. MBR is read - used to be MS code, presumably is now Linux code
2. boot sector of *active* partition is found - in this case, sda1, which was and *is* NTFS
3. NTLDR was invoked - not sure what is invoked now
4. chain loaded Linux via some information spelling out physical starting location of /boot/grub/stage2, perhaps the ubuntu.bin file stored this location? 

So, what I had before was MS code in the MBR load NTLDR, which then invoked boot.ini which, if I selected Linux from the menu, then searched for and found the GRUB stage2 via... what? Ubuntu.bin? So, in order to have restored the previous function (instead of overwriting the MS code in MBR with Linux code) I would have needed to re-generate the Ubuntu.bin file, which was created at the time of my first Linux install (6.10 - Edgy). Does it then follow that the captured *physical* location of the Linux grub boot sector was somehow stored in Ubuntu.bin - or was it stored somewhere else?

This brings up another question.

What's happening now? NTLDR, I'm going to assume, is out of the loop completely, or is it? I mean, according to GPartEd, my boot sector is *still* the NTFS one, so some file on there must still play a role.

Thanks so much for taking the time to explain all this to me - I've tried to read up on MBR and how Linux does GRUB and all that, but I can't get my little head around it, for some reason...
:confused:

---

### Post by adrian15 on 2007-09-26
> **Robynsveil said:**
> So, if I understand you correctly, here's the sequence of events:
1. MBR is read - used to be MS code, presumably is now Linux code
2. boot sector of *active* partition is found - in this case, sda1, which was and *is* NTFS
3. NTLDR was invoked - not sure what is invoked now
4. chain loaded Linux via some information spelling out physical starting location of /boot/grub/stage2, perhaps the ubuntu.bin file stored this location?

That's correct. And yes it loaded ubutu.bin 

> **Robynsveil said:**
> 
So, what I had before was MS code in the MBR load NTLDR, which then invoked boot.ini which, if I selected Linux from the menu, then searched for and found the GRUB stage2 via... what? Ubuntu.bin?


Ubuntu.bin, yes.

> **Robynsveil said:**
> 
 So, in order to have restored the previous function (instead of overwriting the MS code in MBR with Linux code) I would have needed to re-generate the Ubuntu.bin file, which was created at the time of my first Linux install (6.10 - Edgy).

You are right but before regenerating Ubuntu.bin file you should reinstall grub in the linux partition boot sector.

> **Robynsveil said:**
> 
 Does it then follow that the captured *physical* location of the Linux grub boot sector was somehow stored in Ubuntu.bin - or was it stored somewhere else?

In ubuntu.bin. Did not you create this file yourself ?

This brings up another question.

> **Robynsveil said:**
> 
What's happening now? NTLDR, I'm going to assume, is out of the loop completely, or is it? I mean, according to GPartEd, my boot sector is *still* the NTFS one, so some file on there must still play a role.


NTFS is the first partition file system. NTFS partition do not have boot sector.
Another thing is the MBR or Master Boot Record (Before the first partition). In the MBR now you have the grub stage1 which it is something equivalent to the ubuntu.bin contents.

SUMMARY:

Now you boot the grub stage1 from your mbr which chainload stage1_5 which it is between the mbr and the first partition. Then stage1_5 loads /boot/grub/menu.lst whereever it is.

When you resize a partition the location of stage1_5 or stage2 or menu.lst changes and thus the ubuntu.bin has to be regenerated.

But before regenerating it you have to reinstall grub in the linux partition boot sector. It seemed you were not able to do so with Super Grub Disk. Installin grub in a linux partition boot sector is not very frequent so it is a little hidden in Super Grub Disk.

Steps for installin gru in a linux partition boot sector are: Advanced -> Grub -> Restore Grub to a partition and then you select twice your linux / partition.

Once you have done this you will have to regenerate the ubuntu.bin file (It's usually done with the dd command) and copy it to c:\ so that it rewrites your former ubuntu.bin file.

adrian15

---

### Post by Robynsveil on 2007-09-26
> **adrian15 said:**
> That's correct. And yes it loaded ubutu.bin 
Now you boot the grub stage1 from your mbr which chainload stage1_5 which it is between the mbr and the first partition. Then stage1_5 loads /boot/grub/menu.lst whereever it is.

When you resize a partition the location of stage1_5 or stage2 or menu.lst changes and thus the ubuntu.bin has to be regenerated.

But before regenerating it you have to reinstall grub in the linux partition boot sector. It seemed you were not able to do so with Super Grub Disk. Installin grub in a linux partition boot sector is not very frequent so it is a little hidden in Super Grub Disk.

Steps for installin gru in a linux partition boot sector are: Advanced -> Grub -> Restore Grub to a partition and then you select twice your linux / partition.

Once you have done this you will have to regenerate the ubuntu.bin file (It's usually done with the dd command) and copy it to c:\ so that it rewrites your former ubuntu.bin file.

adrian15
Oops.

Actually, what I *did* do was install GRUB - I'm pretty sure this is what I did - just not sure to *what* I installed it. Here's what happens when I turn on the computer... it goes *straight* to stage 2, which is where you see all the different Linux boot options, like previous builds and diagnostic boots and like that. Right at the bottom, I have the option to booting to Windows, which when I chose gives me the menu in boot.ini. So, I can boot like normal but I have no idea what I've installed it to. I *have* found this [great site]("http://users.bigpond.net.au/hermanzone/p6.htm#What_is_the_MBR_or_Boot_Sector") that explains MBR and GRUB and all that wonderful stuff in a language that even *I* can get my head around.
So, I'm going to very carefully study this and *then* ask questions (if any remain)... and maybe even have a clue as to what exactly I did.

I'm just elated to have my Ubuntu install back, regardless... :popcorn:

---

### Post by adrian15 on 2007-09-26
> **Robynsveil said:**
> Oops.

Actually, what I *did* do was install GRUB - I'm pretty sure this is what I did - just not sure to *what* I installed it. 

If you choose the Linux -> Fix Boot of Linux (GRUB) then you installed it to the MBR.

adrian15

---

### Post by psusi on 2007-09-26
> **Robynsveil said:**
> So, if I understand you correctly, here's the sequence of events:
1. MBR is read - used to be MS code, presumably is now Linux code
2. boot sector of *active* partition is found - in this case, sda1, which was and *is* NTFS
3. NTLDR was invoked - not sure what is invoked now
4. chain loaded Linux via some information spelling out physical starting location of /boot/grub/stage2, perhaps the ubuntu.bin file stored this location? 


Almost... the MS MBR code loads the boot sector of the active partition.  The grub MBR code does not; it just knows the location of /boot/grub/stage2 and loads it directly.  Or it can be configured to directly load a copy of stage1.5 which has been hidden within the partition just after the boot sector, but usually it just loads stage2 directly.  If you use stage1.5, then the MBR knows its location, which is just following the boot sector rather than being in a normal file on the partition.  Stage1.5 then is smart enough to read the filesystem in the partition and locate the stage2 file, instead of having to have been built knowing its exact location.  This allows the stage2 file to be replaced or moved around without having to reinstall grub.  

> **Robynsveil said:**
> 
So, what I had before was MS code in the MBR load NTLDR, which then invoked boot.ini which, if I selected Linux from the menu, then searched for and found the GRUB stage2 via... what? Ubuntu.bin? So, in order to have restored the previous function (instead of overwriting the MS code in MBR with Linux code) I would have needed to re-generate the Ubuntu.bin file, which was created at the time of my first Linux install (6.10 - Edgy). Does it then follow that the captured *physical* location of the Linux grub boot sector was somehow stored in Ubuntu.bin - or was it stored somewhere else?


Yes, Ubuntu.bin was just a file that you made that contained the original grub boot sector/MBR code.  Since that code contains the physical location of the stage2 file, you would need to reinstall grub to get the new location, and recapture the Ubuntu.bin file.  

> **Robynsveil said:**
> This brings up another question.

What's happening now? NTLDR, I'm going to assume, is out of the loop completely, or is it? I mean, according to GPartEd, my boot sector is *still* the NTFS one, so some file on there must still play a role.

Thanks so much for taking the time to explain all this to me - I've tried to read up on MBR and how Linux does GRUB and all that, but I can't get my little head around it, for some reason...
:confused:

The way you have it now, grub loads the NTFS boot sector when you choose the windows option, which in turn loads NTLDR, which in turn loads windows.  


> **adrian15 said:**
> 
NTFS is the first partition file system. NTFS partition do not have boot sector.


Not true.  Every filesystem has a boot sector of some sort; it is simply the first sector.  Some filesystem's don't contain any boot code there, but most, including NTFS, do.  

> **adrian15 said:**
> 
Now you boot the grub stage1 from your mbr which chainload stage1_5 which it is between the mbr and the first partition. Then stage1_5 loads /boot/grub/menu.lst whereever it is.

When you resize a partition the location of stage1_5 or stage2 or menu.lst changes and thus the ubuntu.bin has to be regenerated.


He wasn't using stage 1.5 or the resize would not have caused a problem.  Resizing the partitions doesn't effect the area following the MBR where stage1.5 would be, and it would still be able to find stage2 by reading the filesystem.

---

### Post by adrian15 on 2007-10-02
> **psusi said:**
> 

Not true.  Every filesystem has a boot sector of some sort; it is simply the first sector.  Some filesystem's don't contain any boot code there, but most, including NTFS, do.  



He wasn't using stage 1.5 or the resize would not have caused a problem.  Resizing the partitions doesn't effect the area following the MBR where stage1.5 would be, and it would still be able to find stage2 by reading the filesystem.

You are right psusi although in my opinnion the windows boot sector is not an standard boot sector because you cannot install grub on it without frying your windows files.  ;)

adrian15

---

### Post by psusi on 2007-10-02
> **adrian15 said:**
> You are right psusi although in my opinnion the windows boot sector is not an standard boot sector because you cannot install grub on it without frying your windows files.  ;)

adrian15

I'm pretty sure you can actually.  It does still start with a jmp opcode to the code section, just like a FAT boot sector.

---

### Post by adrian15 on 2007-10-02
Are you sure? Please try it inside a virtual machine and you tell us the results.

In my opinion after the grub install you should not be able to mount your windows partition.

adrian15

---

### Post by psusi on 2007-10-02
The boot sector is laid out essentially the same, so it should work.  They just assign different meaning to the data fields for NTFS.  There used to be a utility in the resource kit that would read the any sector on the disk and display it, and it could decode the data in the MBR or boot sector.  

I can't test in a vm because I don't have one, nor a copy of windows handy.

---

