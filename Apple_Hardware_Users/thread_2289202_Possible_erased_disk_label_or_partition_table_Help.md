---
title: "Possible erased disk label or partition table? Help?"
date: 2015-08-02
forum: Apple Hardware Users
---

### Post by jdeks on 2015-08-02
I dun goof'd.

Up until about an hour ago, I had a working installation of 14.0 on my 2013 Macbook Air, with full disk encryption as set up in the standard installation process.

But tonight, in the process of of trying to fix a corrupt SD card, I accidentally called "Parted" on /dev/SDA/, and then ran a mklabel on in. Below is a transcript of the damage:

```

ubuntu@ubuntu:~s sudo parted 
GNU Parted 2.3
Using /dev/sda
welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel
New disk label type? msdos
warning: Partition(s) on /dev/sda are being used.
Ignore/Cancel? I
warning: The existing disk label on /dev/sdb will be destroyed and all data on this disk will be lost. Do you went to continue?
Yes/No? y
Error: Partition(s) 1 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partition(s) will remain in use. You should reboot now before making further changes.
lgnore/cancel? c
(parted) 

```

Lo and behold upon rebooting, I'm greeted with a flashing folder questionmark - which I think is Mac-speak for "I can't find a boot/system partition". I've got a liveboot Ubuntu USB and can get it to start off that, but when I look at the main SSD in disk utility it just sees 250gb of free space.

Yep, I'm a muppet, no argument there. But at least I know when to stop and get help fromthose who know better. I could try out random stuff from Google, but I really do't know quite what Im doing and I dontwant to make this worse. I worry my encryption might complicate things.

Any guidance on how to find out just what damage I've done and how to recover it?

---

### Post by jdeks on 2015-08-03
Anyone? I'm really up the creek without a paddle here....

---

### Post by oldfred on 2015-08-03
I do not know Mac.
Can you just mklabel back to gpt or have partitions totally been deleted.
What does gdisk show?
       sudo gdisk -l /dev/sda
    
If deleted you may be able to use testdisk. Choose gpt not Intel/MBR/msdos.
       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If just converted to MBR from gpt you may be able to convert back?
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by jdeks on 2015-09-17
Bump? Anyone?

Gdisk doesn't work, testdisk's tutorial doesn't match what I'm getting when I run it, and I don't know what this GPT/MBR stuff is.

I'm happy to learn as I go if someone can give me some steps to follow, but  'just use this thing' doesn't help me at all. I'm not an expert - I'm a guy whose been running round in circles on Google through a 4" phone screen for a month now trying to.fox something I still don't really.understand!

---

### Post by oldfred on 2015-09-17
You absolutely need to know gpt.
Apple converted to using UEFI with gpt partitioning when they converted to Intel chips. They were one of the first with UEFI.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table

      [/URL]
 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Some older threads, but newer versions of Ubuntu should work better with UEFI.

 Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[URL="http://www.rodsbooks.com/ubuntu-efi/index.html"]
http://www.rodsbooks.com/ubuntu-efi/index.html[/URL]




    [URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]
[/URL]

---

### Post by luciano.x on 2015-09-17
Ouch. I hope you have backup.
I think you're able to fix it. Now first things first did you tried to write a new partition table?
Generic steps: boot ubuntu from usb; write a new gpt partition table; create esp (vfat, 200MiB, flag boot) and your other partitions; install a fresh ubuntu; recover your data.
The thing is IDK what is the best tool for the job. Sorry. If I were in your shoes I'd research and read around gdisk.
Maybe [this]("http://www.rodsbooks.com/missing-parts/index.html") helps?[URL="http://www.rodsbooks.com/missing-parts/index.html"]
[/URL]

---

### Post by jdeks on 2015-09-17
Guys thankyou for replying but this is really no help to me at all.

I don't want to read through pages and pages of generic, nonspecific technical exposition, especially when I'm stuck on a phone screen, have other work in my life to do, and all of those links are full of technical jargon that I don't understand and require their own pages of reading. I tried that for the last month, its a never ending cycle - I just want my computer to work again.

I have no idea if I tried to "write a new partition table". I don't really know what that is, let alone how to write a new one, "create esp" or what gdisk even is (trying to run it from the rescue remix it says command not found). Everything that happened is in the OP. That's as much information as I have, I tried to be as specific and detailed as possible.

I DID have a backup, until I tried following instructions that were at a technical level above me, something went wrong that I didn't understand, and the person 'helping' me said it was my fault.for not being a  computer programmer and just knowing everything automatically and washed their hands of it. So no, now I DONT have a backup either.

I can boot the recovery remix and run the tesydisk tool. I don't undestand the output. If I posted some photos of that output, would that help?

Thanjs

---

### Post by oldfred on 2015-09-17
If you loaded testdisk with gpt not MBR it may have found partitions. 
But how did they get deleted.

You can attach screen shots with the forum's advanced editor and use the paperclip icon.
If data was encrypted it will be more difficult or impossible to recover. 
Was encryption just /home or the "full drive" install with LVM?

LVM with full drive encryption is more advanced. You have to make sure live installer has tools to work with that.
       Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

Mac are a lot different, so do not know if details are even the same?
May be best to find a local LUG. Linux users group and ask for help.

---

### Post by jdeks on 2015-09-17
The encryption was the normal full disk encryption, done using the install disc guide. I honestly don't know what LVM is, I just followed the prompts.

Here's a sequence of testdisk shots, in order. I selected the EFI option and not the Intel one.

This is the point where I don't really understand what I'm seeing.

One of these partitions looks like my boot partition?

Some of the MS data partitions show up as LUKS1 in the description at the bottom, but they are 2000kb. None of them are as big as I'd expect for the main encrypted container.

Also none of them are labelled [Partition 1] etc like in the testdisk tutorial.

---

### Post by oldfred on 2015-09-17
Please go back and attach screen shots. We are not supposed to post in line.
Not all users have high speed Internet and it makes their system slow.

Testdisk finds all the old partitions, or every version you had. So best if you knew your partitioning and had documented it somewhere or have a good memory.

Normal LVM installs with UEFI have the ESP, /boot & main install. But with BIOS installs it is just /boot & main install. Inside the one actual partition are usually the two logical volumes (LVM) with / & swap.

So you want to recover one set of partitions that do not overlap. But can be difficult to know which set is last version.

---

### Post by jdeks on 2015-09-17
Sorry - have changed the pics to attachments.

Normally macbooks are uefi from what I gather? So what is an ESP partition and what will it look like in test disk?

 And how do I find out which partitions to recover? There are several that look like /boot but only one had browsable files, I assume that's the /boot partition I want? What about the others? I have no idea how I would even 'document' partitions or how to tell the duplicates apart, or even why there are duplicates? How do I tell which are the most recent and don't overlap like you say?

---

### Post by oldfred on 2015-09-18
The ESP - efi system partition is the partition where UEFI looks for boot files. Many will have .efi at end, others may be support files or configuration files.

Testdisk probably does not have the driver for LVM nor encryption. So it will not mount the LVM nor ask for pass phrase to see all your detail files. You should see the files in the ESP and the files in /boot. The main partition with the LVM may not show anything at all?

In my ESP is the /EFI folder. It has boot & ubuntu folders in it /EFI/Boot & /EFI/ubuntu.
I do not have a separate partition for /boot, but it has kernels & /grub folder.

Do not know if Mac needs additional files or folders or partitions. I do know they boot somewhat differently. Most users with Macs use rEFInd in the ESP to control UEFI boot.

---

### Post by jdeks on 2015-09-18
Okay i think I found the esp partition. Testdisk says its about 200mb and shows files in it (pics attached).

I know I didn't use refind to install Ubuntu on this macbook. It was just a plain single boot install, so I just put it in and booted the USB from the Mac recovery startup and installed from there. I think/hope its the same as any other uefi machine

Hangon, does this look more like the esp you were talking about ? It has a whole heap of .efi file and an efi folder in jt

So I found this:

[https://apple.stackexchange.com/questions/71592/can-the-contents-of-a-partition-be-recovered-after-partition-table-is-overwritte](https://apple.stackexchange.com/questions/71592/can-the-contents-of-a-partition-be-recovered-after-partition-table-is-overwritte)

Is this similar to what I did?

---

### Post by oldfred on 2015-09-18
Your screen shot #3 is the /boot partition. You should also have the main partition with the encrypted files and the ESP/efi partition.

---

### Post by luciano.x on 2015-09-18
> I've got a liveboot Ubuntu USB and can get it to start off that, but  when I look at the main SSD in disk utility it just sees 250gb of free  space.
This is how you create a new GPT partition table:
(This will destroy all your data but you can start over and install ubuntu again)
Start ubuntu usb
select try ubuntu
lauch gparted
Menu device -> create new partition table
or right click "free space" -> create new partition table
choose GPT

Now you must create 3 partitions:
esp partition: ESP, 200MB, fat-32, flag boot
swap partition: 4GB, swap
file system partition: all space left, ext4
Apply changes

Forgot the steps to create partitions. I'll check how the menus look when I get home tonight.

---

### Post by jdeks on 2015-09-18
> **oldfred said:**
> Your screen shot #3 is the /boot partition. You should also have the main partition with the encrypted files and the ESP/efi partition.

...okaaay...but I don't? Now its an esp/efi partition? So they're the same partition now? 

And there's still no 'main' partition, and I wouldn't know what to DO with it if there was  

Seriously why is everyone being so coy about explaining this. I get the real.impression I'm being fed jjust enough information that people can laugh at me for not being able to actually fix anything.

---

### Post by jdeks on 2015-09-18
> **luciano.x said:**
> This is how you create a new GPT partition table:
(This will destroy all your data but you can start over and install ubuntu again)
t.


This is completely useless to me - I don't want to just destroy all my data and install a fresh copy of Ubuntu. I'm trying to.recover what I had. Tharts what I said in the first post.

Seriously this is worse than trying to deal with Microsoft tech support. I've written out everything verbatim, I've got the utilities. Its not like I'm just demanding people do the work for me - I'm willing to learn but ive wwited a MONTH and now everyone just giving vague unhelpful statements. Is this like standard policy for inexperienced people who ask for help?

The problem is really straightforward- I accidentally changed the disk.label type to msdos. My drive won't boot and can't seem to find its partitions. Everyone says testdisk is apparently how to fix this - without getting a masters in IT, how do I fix this?

---

### Post by oldfred on 2015-09-18
I only jumped in since no one else was.
I do not know Mac, do not know LVM and do not know encryption.
So I cannot give all the details needed.

But do know UEFI and standard installs reasonably well.
And I have seen many Boot-Repair summary reports with LVM.
Those with UEFI have 3 standard partitions, ESP/efi, /Boot and main install.
The ESP is always FAT32 with the boot flag.

But without knowing what partitions your had and exact sizes it is very difficult to tell you which combination to choose. And the more times you repartitioned drive, the more versions that testdisk shows, making it more difficult. 

This user posted his summary report with UEFI, LVM & encryption.
[http://paste.ubuntu.com/10612776/](http://paste.ubuntu.com/10612776/)
The /boot is always ext2 and not as large as many would like or about 240MB.
And main install is rest of drive and inside it are is the LVM or logical volumes.

---

### Post by imattux on 2015-09-20
OldFred - I understand that you're trying to help, but you're really     not helping at all...
    
    Jdeks - here we go:
    1. I hope you've learned your lesson, but I'll summarize for you:     Whenever you use "sudo" that means "Super User (says) do (this)" and     once you enter the password, you can break everything. So don't use     it when you don't know what *exactly* what you're doing.
    2. "Parted" is a tool that can be dangerous, that's why it requires     "sudo" to use it. Why were you using it? What were you trying to do?
    3. You blew thru 3 warnings that you were going to overwrite your     data. What were you thinking? Don't do that again!
    4. Why did you choose to encrypt your data and why did you choose to     use LVM? If you had data that was important enough that you need to     encrypt it, you would not be in this situation. Both of them make     everything harder and if you don't know exactly why you need them,     you don't need them.
    (Scolding over, now I'll try to help you)
    4. If you haven't done anything since your last post, there is a     reasonable chance that you'll be able to recover your system or at     least your data. Having said that, **no guarantees**.     You made a very serious mistake despite several warnings and you     might have lost everything. **Caveat Emptor.**
    
So you know what I'm telling you to do: For our purposes now, a partition is a section of a disk that is separate as if it was a separate physical device. There is a table that tells the system where each partition starts, where it ends, and what format the data is in. What we are trying to do is recover and restore the partition table to the state it was in before your mistake. Make sense?

According to your first picture, you changed the partition table for /dev/sda and /dev/sdb. Changing the table is not the same as changing, deleting or erasing the data, in this case, you just changed the label of /dev/sda from ESP (**E**FI **S**ystem **P**artition, the partition that has the EFI file(s), usually nested in /efi/EFI/) to msdos. In truth, the ESP was already msdos (FAT) format because that's the default format according to the specification. ESP is technically special, but the data on it is written to a FAT filesystem. What this means is that the data has a better chance of being intact because nothing really changed very much. I think. Probably. I'm pretty sure it's just a few bits flipped one way vs. another.


5. Boot your box from the medium you used to install Ubuntu, choose "Try Ubuntu without installing" (I don't know the toll you are using and I do know gdisk and it's on the Ubuntu installer)
6. Launch your terminal and follow along. gdisk doesn't actually write anything until the end. You can review everything before writing anything. If you're not sure about anything, take a screenshot, type q and come back here:

```
-> **sudo gdisk /dev/sda**
[sudo] password for imattux: 
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

###Yours will likely be different or gdisk will tell you it's creating a new GPT header, it's ok####

Found valid GPT with hybrid MBR; using GPT.

Command (? for help):** ?**
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): **p**
Disk /dev/sda: 1465149168 sectors, 698.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): EE73B6FA-51CA-4B62-A7CB-16B0B5CB3EF3
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1465149134
Partitions will be aligned on 8-sector boundaries
Total free space is 264565 sectors (129.2 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640      1952255591   930.7 GiB   AF00  mreQuad1TBi
   3      1952255592      1953525127   619.9 MiB   AB00  Recovery HD

Command (? for help): **r**

Recovery/transformation command (? for help): **?**
**b    use backup GPT header (rebuilding main)              ** ####hopefully this will be enough ####  
**c    load backup partition table from disk (rebuilding main)     **###### if not, we'll have to try this #####
d    use main GPT header (rebuilding backup)
e    load main partition table from disk (rebuilding backup)
f    load MBR and build fresh GPT from it
g    convert GPT into MBR and exit
h    make hybrid MBR
i    show detailed information on a partition
l    load partition data from a backup file
m    return to main menu
o    print protective MBR data
p    print the partition table
q    quit without saving changes
t    transform BSD disklabel partition
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Recovery/transformation command (? for help):[B] b
[/B]
Recovery/transformation command (? for help): **p**
Disk /dev/sdc: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 112CBE35-4F22-4B29-A58C-E48676355059
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 13 sectors (6.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition      ##### This is what you're looking for to be bootable again ####
   2          409640      1952255591   930.7 GiB   AF00  mreQuad1TBi      
   3      1952255592      1953525127   619.9 MiB   AB00  Recovery HD

##### If you've got an ESP, you should be good to go####
Recovery/transformation command (? for help): [B]w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y


[/B]##### If not, try c ##########


Recovery/transformation command (? for help): [B]c
[/B]
Warning! This will probably do weird things if you've converted an MBR to
GPT form and haven't yet saved the GPT! Proceed? (Y/N): [B]Y
[/B]
#### You don't have much choice ####
 
Recovery/transformation command (? for help): p
Disk /dev/sdc: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 112CBE35-4F22-4B29-A58C-E48676355059
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 13 sectors (6.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640      1952255591   930.7 GiB   AF00  mreQuad1TBi
   3      1952255592      1953525127   619.9 MiB   AB00  Recovery HD

Recovery/transformation command (? for help): w

[B]Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y[/B]


```


Hopefully, you'll be able to load the backup header (this is the low level information about your drive and partitions, like a map that tells the system where the info is, how it's formatted and what to do with it)

Do the same thing for /dev/sdb - I don't encrypt so I'm not sure if, when or where you will need to enter your password, but everything else should be the same...

I spent a fair amount of time here. Please lmk how it goes.

P.S. Encryption is encryption. It's several orders of magnitude harder to recover encrypted data than regular data but nothing is impossible to recover. If the data on your laptop is so important that it needs to be encrypted, then you need to be backing it up regularly to the cloud and/or an location that is some distance from the place where the laptop is. You're obviously not doing that, so what are you encrypting for? If someone is going to hack you or steal your identity, they're way more likely to do it by some means other than stealing your laptop. Password protection is sufficient to protect your sensitive data from someone who finds your laptop because you lost it. Install a minimal MacOSX on it and enable find my Mac. You might actually get it back and you can wipe the drive remotely. That's my $.02

LVM stands for Logical Volume Management. It means that the system can dynamically grow or shrink the hard drive. It's probably a good thing, but again, it makes data recovery more challenging and data loss slightly more likely vs. not using it. It'll come in handy if you decide to create a ~40G Mac partition so you can use find my Mac.

Cheers,

imattux

---

### Post by jdeks on 2015-09-20
Imattux, ***thankyou***, for the first and only real helpful answer so far. I really appreciate the time you took writing that.



> **imattux said:**
> OldFred - I understand that you're trying to help, but you're really     not helping at all...
    
    Jdeks - here we go:
    1. I hope you've learned your lesson....
    3. You blew thru 3 warnings that you were going to overwrite your     data. What were you thinking? Don't do that again!

Well, to offer some explanation - those commands were issued while booted off a live CD. For whatever reason, the whole night up until then, sda was the SD card I was trying to recover, sdb the host machines internal drive. For reasons I dont understand, that switched on my at some point.

Yes, I know if should have checked each and every single time I ran the command, and again before I hit 'y'. But I had checked, dozens of times already, and every time, sda was the disk i wanted. Why ubtunu suddenly changed it on me after, I dont know. Mistakes happen. We all make them.

> **imattux said:**
> 

    4. Why did you choose to encrypt your data and why did you choose to     use LVM? If you had data that was important enough that you need to     encrypt it, you would not be in this situation. ...

P.S. Encryption is encryption. It's several orders of magnitude harder to recover encrypted data than regular data but nothing is impossible to recover. If the data on your laptop is so important that it needs to be encrypted, then you need to be backing it up regularly to the cloud and/or an location that is some distance from the place where the laptop is. You're obviously not doing that, so what are you encrypting for? 


I chose encryption because given my current circumstances, it's a prudent measure. Higher than average risk of theft, have to travel with moderately private personal data on the machine. I was aware of the complications it presents, and DID have a backup. I mentioned a few posts back though, after following some bad advice from another source that was corrupted in an attempted restore effort.

And I use LVM, because that's what the automated installer uses when you check the full disk encryption option. I simply assumed if thats the default setting, it's best to do it that way.

[U]Now, as it happens, I have actually solved this:
[/U]
Another guy on a motorbike forums of all places suggested and walked me through the same Gdisk restore methods you so kindly outlined (again though, big props for such a detailed walkthrough).

In my case, when I hit 'p' I got nothing. No partitions. None. Restoring the backup tables didn't change anything. So I figured whatever partition tables were once there were now gone. I need to build new ones.

[COLOR=#111111][FONT=Ubuntu]I found this:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://ubuntuforums.org/showthread.php?t=895224](http://ubuntuforums.org/showthread.php?t=895224) (oddly enough, no-one helped this guy out either...)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Long story short, he nuked his table too with mklabel. But the  data was still there, and he got it back by making a new table with one partition over the whole disk. But I didnt have that, I had multiple partitons and one was LUKS[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then by sheer luck I found this:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://ubuntuforums.org/showthread.php?t=2214497](http://ubuntuforums.org/showthread.php?t=2214497) (also another person who had to "bite the bullet" and go for it without advice...)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Again, summarizing -[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Despite what it says (or rather, doesn't say) on its documentation Testdisk for whatever reason can't restore full LUKS partitions. In fact it cant even find them!! But - you can at least use it to get some ideas on what sector the LUKS partition might have started - it at least picks up the LUKS header as a 4096 / 2MB partition.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]You can then take the starting sector of this header and make a new partition manually from there to the end sector of the disk (assuming you encrypted all the remaining disk - if you don't know the end sector you're in trouble, testdisk can't find it. But if you get it right and write a new partitions table with those sectors, viola - you have a mountable partition and can recover your data. If you can find the sectors you can restore the EFI and boot partitions too (test disk at least can do this itself, it picks up the FAT and efs2).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However, even with a boot flag on the EFI partiton, it still wouldn't boot. Im not sure why. Something was still messed up - possibly related to having a hybrid MBR/GPT (I still dont understand that...)

So instead, I dd'd each of these recovered partitions separately onto an external drive, re-installed a a fresh encrypted copy of ubuntu, then dd'd the recovered partitions back into their respective places. I know, a bit of a long way round, but the partition sizes are all identical and it all booted up like nothing had ever changed, even swap worked.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So, what have I learned? Well, if you fry your partition table, even with an encrypted install, the data IS recoverable.

Yes, I am now making new backups of the drive and the partiton tables.[/FONT][/COLOR]

---

### Post by imattux on 2015-09-20
I'm very glad things worked out for you. And roundabout or not, you've got your data back. You also learned a little something along the way. Cheers.

---

