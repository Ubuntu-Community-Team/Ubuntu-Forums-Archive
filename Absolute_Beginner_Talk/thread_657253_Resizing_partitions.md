---
title: "Resizing partitions"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by DonDodge on 2008-01-03
Is it possible to add size back to a windoze partition by reducing the size of the ubuntu partition on the same drive without screwing up either installation?

---

### Post by stchman on 2008-01-03
> **DonDodge said:**
> Is it possible to add size back to a windoze partition by reducing the size of the ubuntu partition on the same drive without screwing up either installation?

Yes, use the Ubuntu LiveCD and fire up gparted.  Before you start I recommend you run a chkdsk /f and defrag your Windows partition.

Are you using Vista or XP?  If using Vista you can shrink partition on the fly.

---

### Post by DonDodge on 2008-01-03
Sorry, I forgot to say I use XP Home

---

### Post by DonDodge on 2008-01-03
Shrinking /dev/sda2, the  ubuntu partition, went very well. Windoze and Ubuntu both boot.

Now I have a 60 gb /dev/sda4 partition. I can't find the right combination to integrate this recovered space back into /dev/sda1, my windoze C: drive. 

Windoze doesn't seem to have a disk command to accomplish this task. All it sees is a new H: drive and I don't see how to move it with diskpart or Disk Management.

Any help?

---

### Post by dstew on 2008-01-03
Probably the most straightforward way would be to expand the /dev/sda1 partition at the expense of the /dev/sda4 partition, using gparted. You might have to move the other partitions over to create new unallocated space to expand into. I do not think you can merger partitions unless they are right next to each other.

So: shrink /dev/sda4, slide /dev/sda2 and /dev/sda3 over, then expand /dev/sda1 (if they are in that order).

---

### Post by DonDodge on 2008-01-03
Thanks for the info. I'll have a look at it again.For some reason, gparted isn't offering me a way to move any partitions.  Maybe I can kill sda4 and then it will allow expansion of sda1.

---

### Post by sciencewhiz on 2008-01-03
gparted won't give you the option to move. You can, however, expand a partition on the right and shrink it on the left, which has the same effect.

---

### Post by DonDodge on 2008-01-03
Thanks guys. I think I have it figured out now and it appears to be working like a champ.

---

### Post by DonDodge on 2008-01-04
Oops, that didn't work out so well after all. I moved sda2 to the right and when I rebooted to the hard drive to check it out, I lost my grub loader. I got a message:
GRUB loading stage1.5. 
and then:
GRUB loading, please wait...
error 18

and that's as far as it goes. Back to booting with the live cd

I started up gparted to see what that showed and it said sda2 wasn't mounted. Now, after finding the /boot/grub/menu.lst file and looking at it and restarting gparted, it now shows sda2 mounted at media/disk

Another try at booting to the hard disk gave me the same result. Gparted says sda2 isn't mounted until I go into the computer file browser and access the disk.

Did I lose my mount point? Do I need to edit menu.lst or fstab or what? 

Help, it's been  four years since I goofed with the guts in linux and I'm lost.

---

### Post by matthx on 2008-01-04
Im a linux noob but when im not debuging my own system i like to find out what other users' problems are so if it ever happen to me i would have a clue on what to do. Here is what i found about your grub error 18:

> Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel. 

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem. 
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.


What i found to "fix" this:

> Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range).

So my guess is that you should try to move your partition that handles grub. Since i have never messed with this yet i cannot help you more. GL!

---

### Post by DonDodge on 2008-01-04
Dang! I guess I moved the grub too deep into the disk. I read something about how grub needs to  be near the front of a partition or the front of the partition can't be too far back. 

I suppose I'll have to move the partition back up to the front so I can at least access my windoze drive.

---

### Post by DonDodge on 2008-01-04
Moving my newly shrunken ubuntu partition back to the left, directly behind my already too small windoze partion gave me back control of the computer and allows for a boot into either windoze or ubuntu.

This still leaves me with the problem of how to merge the rest of the hard disk back into the windoze partition.

Is there a way to get rid of the grub and make windoze recognize ubuntu as a secondary operating system, thus allowing me to control the boot with the windoze boot manager?

---

### Post by DonDodge on 2008-01-04
I tried using a floppy based GAG Boot Manager to see what it would do. It booted windoze just fine but I had to run grub setup to reinstall the grub to the first sector of the ubuntu partition before GAG could boot it up. At that point, the regular booting off the hard disk would boot either OS and I could boot either system with the GAG.

Next I moved the ubuntu partition all the way back to the right again to see if GAG could deal with it there. Nope. Same result, no good. Booting from the normal hard disk setup, I'd get error 18 again. With the GAG, I'd get only a GRUB text line with a flashing cursor. The only acceptable keyboard input at that point was Ctrl-Alt-Del. Reinstalling the grub again to the first sector made no difference. At least the GAG would allow a boot into windoze and take the dysfunctional ubuntu grub out of the loop.

Next experiment was to shrink the ubuntu partition from 40 gb down to 20 gb and leave it in place. This WORKED without any other manipulation. It boots to either OS off HDD or GAG. Now I have a 60-some gb block of unallocated space in front of the ubuntu partition and 20 gb following the ubuntu partition.

Now I still want to expand my windoze drive into that unallocated space but the way all this other stuff has been going, it's a little scary. I have all my backups but I'd still hate to lose all my windoze installation if this doesn't work.

Has anyone tried this and come out clean?

---

### Post by insertAlias on 2008-01-04
Have you looked into [Acronis Disk Director Suite]("http://www.acronis.com/homecomputing/products/diskdirector/")? It can do all kinds of partition manipulation and also has a nice bootloader that you can install.

---

### Post by DonDodge on 2008-01-05
That was nice while it lasted. After about three test boots to both operating systems, the party was over. I lost the ability to boot off the mbr. I never did try to expand my windoze partition into the unallocated space.

It started failing to boot with an error 17. I could still boot windoze just fine with the GAG but ubuntu refused to boot until I discovered my stage 1 was now at hd0,2 rather than hd0,1. Resetting the grub didn't help nor did editing menu.lst but I could boot ubuntu by manually editing the start item.

Next I moved the ubuntu partition all the way back to the left and it goes straight to failure on error 18 again. The only way I can use the computer is boot with GAG. Booting with the mbr fails on error 18. If I boot with GAG I can get the usual start up choices but have to manually edit the ubuntu start item and change it to (hdd0,2). Now, after another edit of menu.lst, I can boot with the GAG floppy straight into ubuntu.

Does anyone know the best way I can get my computer to boot off the mbr again? Like maybe use the windoze recovery console off the XP cd and run fixmbr? I imagine I could still boot ubuntu with GAG if I let windoze restore the mbr. If not, oh well. I need my computer back.

---

### Post by dstew on 2008-01-05
Here's the problem: To boot with grub from the MBR, the partition containing the grub root directory has to be *entirely* within the BIOS cylinder limit. At present, your grub root directory is in your Ubuntu partition, which is itself too big for the BIOS. The only way to get around this problem is to create a special boot partition that contains your /boot directory. The simplest way to do this is create a 50 megabyte partition at the very front of the drive, then re-install Ubuntu. Designate the mount point /boot for this new partition. When Ubuntu installs, it will put the kernel and grub root files there, and grub will be able to access them. After the kernel loads, it can mount and access the system root partition (mount point '/') anywhere on the disk.

If you create a /boot partition, it has to be a primary partition (/dev/sda1 to /dev/sda4). When you install grub, this partition will be grub's root, and you will install grub onto the MBR. For example, if your boot parition is /dev/sda4, the grub installation commands would be:```
root (hd0,3)
setup (hd0)
quit
```

---

### Post by DonDodge on 2008-01-05
Thank you for the info.

At this point, my only priority is restoring the computer to boot normally and preserving  windoze installation intact.  I don't want to take a chance of losing that because even with backups, I'll still have to download gigabyte quantities  of databases and programming at dialup speeds. Until I'm able to figure out how to make that program run in ubuntu, I'm tied to windoze.

Obviously, in any case, it appears ubuntu will have to be expendable for a while. Actually, I should have installed it to a partition on a secondary drive. That will ceratinly be where it will go if I have to reinstall.

---

### Post by rkd on 2008-01-05
It isn't clear to me from reading this thread whether you have fixed the MBR or not.  If not, I can tell you two simple ways to fix it.

1. Boot from the Windows install CD, go into the recovery console, enter the fixmbr command.

2. Get Super GRUB onto a CD, boot from it, select the Windows choice from the main menu, then select the restore NTLDR option.  Read more here (though it isn't very clear):

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by DonDodge on 2008-01-05
No, I haven't fixed it yet. I'm making images of my ubuntu installation and collecting other files to put on my laptop before I do it.

I'm also lookiong into the super grub program.

Thanks

---

### Post by rkd on 2008-01-05
Just to make sure -- I may not have been clear:

If you have the Windows install CD, you don't need Super GRUB.  You either boot from the Windows CD and user fixmbr or you boot the Super GRUB CD and use NTLDR, you don't need to do both.  If you don't have a Windows install CD, then Super GRUB is a workable answer.

---

### Post by DonDodge on 2008-01-05
I used super grub to fix the mbr. It seems to have worked well. I don't have any problem booting right into XP. I can also boot ubuntu with the GAG floppy, and I assume I'll be able to boot ubuntu with the super grub cd.

I reckon my next big move will be restoring my ubuntu backup image onto sdb2 and use super grub to fix up the booting for that.

I appreciate the advice and moral support. I'm breathing a little easier now.

---

### Post by DonDodge on 2008-01-06
I'm still fighting with this setup. I installed ubuntu on sdb1 and had a working installation that I could log on to but then I restored the backup image I took of ubuntu on the main drive and promptly blew it out, seemingly never to be found again by Super Grub, GAG or any other means. 

I also moved the original ubuntu partition back to the end of the main drive and lost access to it again.

Neither of these installations are bootable by GAG or Super Grub but I have found a way to boot the ubuntu at the end of the main drive (which is exactly where I want it).

To do so, I simply have to manually edit the start up menu item that says root (hd0,2) and change it to (hd1,0) and push b. It boots right up.

Problem is, I can't seem to find a way to save that change in the startup item. I've tried many ways using Super Grub but it won't stick. I can't save it. I've also done the sudo grub setup thing, both from the ubuntu itself and the Live CD but that doesn't help either.

Question is, when I start the computer with a normal hard disk boot and get the menu that allows a normal start of ubuntu, a recovery start, a memtest start or a boot to windoze, where do those commands live? How do I edit and save the ububntu start line item so it goes to root (hd1,0) rather than (hd0,2)?

---

### Post by rkd on 2008-01-06
To answer your question at the end of your post, that information is in /boot/grub/menu.lst

I don't know whether that is really all you need to know. If you have been editing that file and it doesn't seem to be taking effect, then I don't know what to say except to look into the descriptions of GRUB to try to understand better what it is doing.

I don't understand enough of what you mean when you said you restored the backup image to guess why that destroyed your GRUB setup. I also don't understand very much about the details of how GRUB works to say much about it. I have found a fairly long description of GRUB at this site:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I haven't had time to read it slowly and carefully to fully learn what it is saying. It isn't very suitable for a quick scan, so you might not be able to learn anything you need from it quickly.

There is also the official GRUB manual at:

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

It seems pretty well-written, but is also very long, so it probably won't provide you with any quick answers, either.

Have you considered the suggestion dstew made in post #16? It sounds like a simple, straightforward solution to me, but maybe there is something about what you are trying to do that makes it unsuitable for you.

---

### Post by dstew on 2008-01-06
Changes made by editing the boot commands on the menu screen are not permanent. If grub boots Ubuntu with root (hd1,0), you can permanently change the boot statements by editing the /boot/grub/menu.lst file. After you boot Ubuntu, open a terminal, and enter```
sudo gedit /boot/grub/menu.lst
```Change the root statement of the menu item, save the file and reboot.

---

### Post by DonDodge on 2008-01-06
I figured out most of what's going on here but it's pretty hard to explain. 

When I dumped the backup image from sda3 onto sdb1, it wrote over the menu.lst file, as I knew it would. I saved a copy of the original sdb1 file and assumed I'd have to replace the overwritten file. After it was overwritten, however, I didn't immediately replace it. I assumed it was inconsequential because I thought I'd be able to use GAG or Super Grub to get back into it. What actually happened is when I rebooted, everything disappeared and neither of those programs could fiind a trace of sdb1 ubuntu and trying to change boot order in the bios to access it was futile.

When I'd manually edit the boot menu line item at the grub from root (0,2) and change it to root (1,0) I was apparently sending grub to the menu.lst file on sdb1 at the front end of the D; drive to boot the ubuntu on sda3 at the tail end of the C: drive. That's why  I could edit that bejeezus outta that menu.lst file in the installation I COULD boot and it made no difference. 

When I finally went to media/disk/boot/grub/menu.lst on sdb1 from ubuntu on sda3 and edited that file to say root (1,0) and rebooted, both ubuntu installations showed up in the grub again and both became automatically bootable. Both installations require the start item of root (1,0) to boot. If I edit the boot command line for either install at the grub loader phase and change the root command to (0,2), neither one will start. 

I think what this means is the ubuntu installation at the back end of the C: drive is completely dependent upon the unbuntu menu.lst file at the front end of the D: drive since the grub can't find the menu.lst file that goes with the installation.

Which brings me to dstew's post and advice. Before I can ever get the ubuntu on the C: drive to function on it's own, I have to relocate the partition back toward the front of the drive (where I don't want it) OR install that boot partition at the very front of the drive. I think I can understand how that will work, although I'm not to clear on exactly how to set it up as a boot partition. What is preventing me from playing around with it is I'm afraid of moving my windoze partition 50 mb to the right for fear of screwing it up.

Let me ask you this... if I move that windoze partition 50 mg to the right, can I screw it  up or will windoze be force to cooperate with an operation like that? In effect, wouldn't I simply be allocating space for a much larger MBR? And why would it have to be 50 mb? What all has to go in there?

Man, this has been a learning experience.

---

### Post by DonDodge on 2008-01-06
> **dstew said:**
> Here's the problem: To boot with grub from the MBR, the partition containing the grub root directory has to be *entirely* within the BIOS cylinder limit. At present, your grub root directory is in your Ubuntu partition, which is itself too big for the BIOS. The only way to get around this problem is to create a special boot partition that contains your /boot directory. The simplest way to do this is create a 50 megabyte partition at the very front of the drive, then re-install Ubuntu. Designate the mount point /boot for this new partition. When Ubuntu installs, it will put the kernel and grub root files there, and grub will be able to access them. After the kernel loads, it can mount and access the system root partition (mount point '/') anywhere on the disk.

If you create a /boot partition, it has to be a primary partition (/dev/sda1 to /dev/sda4). When you install grub, this partition will be grub's root, and you will install grub onto the MBR. For example, if your boot parition is /dev/sda4, the grub installation commands would be:```
root (hd0,3)
setup (hd0)
quit
```

dstew,

I'm beginning  to understand what you're saying here. The problem is becoming obvious since the ubuntu installation works just fine when the front of the partition is 41.1 gb from the front of the drive. If if I move it 100 gb into the drive, it just doesn't work right at all without an intervention of sorts..

So... if I make a 50 mb boot partition at the beginning of the drive, can /boot simply be relocated to that partition and the rest of the installation be trained to work with it there?

Can the windoze partition be safely shifted to the right by 50 mb?

---

### Post by rkd on 2008-01-06
From what small amount I understand about booting, I think it is safe to move the Windows partition 50 megabytes as dstew suggested. But I wouldn't do it without having a fresh image of the Windows partition. If a power failure happens in the middle of an overlapping move like that, I'd expect to lose the partition.

I have seen articles claiming that Windows is only happy as the first partition on the drive.  On the other hand, I've seen a couple of systems that work fine with Windows not being the first partition.  So I'm quite skeptical of the claims that Windows has to be first. I'm sure people who say that have had problems that they cured by changing things so the Windows partition is first, but that probably wasn't actually what cured the problem.

I'm not sure whether you made an image of the Windows partition when you were making your backups -- you mentioned only the Ubuntu partitions yesterday. If you have an image of your Windows partition, I think you would be safe in moving the Windows partition 50 megabytes. If it turns out that it does break Windows, you could recover by deleting the new small first partition and the moved Windows partition, creating a fresh Windows partition at the front of the  drive (exactly where it is now), and copying the image back into that fresh Windows partition. 

The new first partition doesn't have to be exactly 50 megabytes. That's not a special magic number. That partition has to hold just the stuff that /boot has -- a few kernel images and related files, the various GRUB files, that's about it.

---

### Post by dstew on 2008-01-07
> can /boot simply be relocated to that partition and the rest of the installation be trained to work with it there?Yes, that can be done, but it might be difficult. I will look into it for you. However, if you install Ubuntu afresh, that will take care of the problem for you. You will need to re-install grub to find its root in the new partition.

---

### Post by DonDodge on 2008-01-07
I did make an image of windoze with partimage but it's no good for even doing a simulated restore. The program tells me the gzip file is an invalid compression level and then it crashes. Well, partimage is experimental for NTFS so I guess that's to be expected. I need to find another program to make an image or figure out how to use tar backup to do it. I do have a backup power supply and auxilliary power to back that up but it's silly to push my luck.

My /boot is 17.4 mb so I suppose 50 mb is a good, safe number to use. I just have to get a good windoze image and make sure I don't lose my linux again before I try this one out.

Thanks rkd. You are very helpful.

---

### Post by DonDodge on 2008-01-07
> **dstew said:**
> Yes, that can be done, but it might be difficult. I will look into it for you. However, if you install Ubuntu afresh, that will take care of the problem for you. You will need to re-install grub to find its root in the new partition.

Hmmm, I wonder if I could reinstall, then restore my backup and then get rid of the restored /boot. I just hate to start completely over with ubuntu since I have dialup and have spent days doing updates and program downloads. Thanks.

---

### Post by dstew on 2008-01-07
To create and use a new /boot partition without doing anything to your installed Ubuntu system, I think you would need to do the following:
1. Create the partition. 50 Mb will be more than enough.
2. Mount the partition onto your Ubuntu file system and copy the contents of /boot to the root directory of the new /boot partition.
3. Edit your fstab file to mount the new partition onto /boot
4. Edit the grub menu.lst file (the one in the new partition) so that the kernel line root commands will point to the new partition. The kernel root designations will not need to be changed, unless the enumeration of the non-/boot partitions has changed (which might happen).
5. Shut down and boot a LiveCD
6. Re-install grub to use the new boot partition as its root
7. Quit grub, remove the CD and re-boot

This is, of course, the outline. The details can be explained later, if you really want to try this. I don't know if it would work, but that is the best I can come up with at present. I think it would make an interesting experiment, if you can afford to have your system fail if it doesn't work.

---

### Post by DonDodge on 2008-01-07
I appreciate the info. I do want to try something like this to get the ubuntu at the end of the main dive to function on it's own but I need to work enough redundancy into the plan so I don't have to lose anything, no matter how badly it goes.

This sure is a workout. Every time I make a big change, it takes forever to get everything back again. I shrunk my ubuntu on sdb1 to make room for an E: drive and it was a bear getting both of the ubuntu installations back again. Now they both load off the menu.lst at sdb1 again. Super Grub doesn't help. It requires hand editing of all the menu.lst files to dial in the right combination. For read only files that are supposedly locked, they sure seem to change a lot whenever a partition is resized or moved.

I'll definitely need some help with fstab. That thing isn't making much sense to me, even after reading the man and info pages. I'll learn a lot if I can ever get sda3 to mount in the sdb1 ubuntu. Maybe that is something that just can't happen due to location.

Edit: I guess I should say,,, I'll learn a lot if I ever figure out how to see that drive since it is supposedly mounted.

---

### Post by dstew on 2008-01-07
> I'll learn a lot if I can ever get sda3 to mount in the sdb1 ubuntu. Maybe that is something that just can't happen due to location.You should be able to mount sda3 onto your Ubuntu file system no matter where it is in the system. It is only grub that cannot deal with partitions in your system bigger than 1024 cylinders because of your BIOS restrictions. Linux, however, does not use the BIOS to access disks like grub does, so it shouldn't matter to Linux.> I'll learn a lot if I ever figure out how to see that drive since it is supposedly mounted.Once a partition is mounted onto your file system, you just navigate to the mount point, and you should see it. For example, after the mount command```
sudo mount -t ext3 /dev/sda3 /mnt/sda3
```you would navigate to /mnt/sda3 and find the files there.

---

### Post by rkd on 2008-01-07
> **DonDodge said:**
> I'll learn a lot if I ever figure out how to see that drive since it is supposedly mounted.

In case you didn't know this, if you think something is mounted, but don't know where, you can enter the command:
```
mount
```
It will list every device that is mounted AND the mount point. Just "mount", no other parameters, and you don't even have to put sudo in front.

---

### Post by DonDodge on 2008-01-07
Okay, I moved sda1 50 mg to the right and apparently did only minor damage to windoze. It boots all the way to the desktop but then it shuts itself down. Shouldn't be a big deal, especially since I have a good image to restore the C: drive.

Both ubuntu installations boot just fine.

Now I need to format the new boot partition to ext3 and at that point, I imagine I'll lose everything until I edit the menu.lst files since the newly formatted boot partition should become sda1 and my windoze will become sda2.

Can you please offer some elaboration on mounting the new boot partition onto the sda3 ubuntu file system file system and fixing fstab?

---

### Post by rkd on 2008-01-07
I'm a little worried that Windows shuts itself down, but if you want to attend to that later, okay.

I think it won't renumber the existing partitions. They don't have to be in disk address order. The new one should be given the first unused number under 5.

To get the new /boot mounted put a line like this into fstab:

```
/dev/sda[n] /boot ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
```

I don't have a separate /boot partition, so I copied the options on that example line from a posting of someone else's fstab. Compare the options with those on the fstab line for your root partition and adjust if you see something that looks like it should be different.

When changing menu.lst, in addition to changing the root line, you will have to remove /boot from the filename in the kernel and initrd lines (because the files are now at the top level in their new partition).

After you have copied the contents of your existing /boot directory to the new partition, you can remove the files from /boot, but leave the directory -- that's where the new partition will be mounted.

For copying /boot to the new partition, you'll neet to create a temporary mount point for it:

```
sudo mkdir /mnt/newboot
```

and mount the new partition there:

```
sudo mount -t ext3 -o rw /dev/sd[n] /mnt/newboot
``` 

Then you can copy stuff to /mnt/newboot. I think the rw option is the only one you'll need.

Herman's site is hard to read, but has a lot of information. Here he describes making a separate partition for /boot. It won't all apply for you exactly, but you might find it helpful:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by DonDodge on 2008-01-08
This isn't going well at all so I'm going to attempt to start over by moving my windoze partition back to the front and hopefully, restore the image. I tried restoring it to the relocated  partition but it won't work.

Edit: Ubuntu can't move the partition back to the front because of NTFS errors. Gparted won't cooperate  until I run chkdsk /f and reboot windoze twice. Since I can't run chkdsk /f and reboot twice because I can't start windoze, even in safe mode or safe mode command prompt. I'm trying chkdsk /r from the recovery console. What a pain!

---

### Post by rkd on 2008-01-08
Gee, you sure are running into lots of problems.

I wonder whether the NTFS errors are simply that gparted checked the NTFS partition and found that Windows had not closed it cleanly (you mentioned that Windows shut itself down when you tried to boot it after moving the partition).

I don't know why Windows wouldn't run after the partition was moved. I'd be inclined to copy your image of the NTFS partition you made before moving the partition into the moved partition, on the theory that something got messed up in the move. If Windows still doesn't work after copying the saved image into the partition at the 50 MB offset, then I'd delete the partition, create it again at the beginning of the disk and copy back from the saved image. Assuming Windows works again, then I'd take some other approach. (I can think of at least one other approach that doesn't need a boot partition at the front of the disk.)

---

### Post by DonDodge on 2008-01-08
It lived. I ran the chkdsk /r and that was good enough for Gparted to let me move the partition back to the front. On boot,  windoze ran a complete chkdsk routine, quit again, restarted and is now okay. The system notified me three times it recovered from a serious error. Heheh. If it only knew.

I tried restoring the image into the moved partition but it wouldn't go. At that time, DOS said I didn't even have a C: drive. 

I think the problem with Gparted was indeed that fact windoze did a bad shutdown.

Back to the drawing board. I don't think that idea is gonna work.

Edit: On second thought, maybe if I did this in the exact proper sequence, it may work. I dunno but I think I'd rather be out catching rattlesnakes.

---

### Post by rkd on 2008-01-08
I'm glad Windows worked once you got it back to the beginning of the drive. Now this thread is going to supply more support for the people who say Windows won't work unless it is the first partition. I've seen it working in partitions that were not the first partition on the disk, but in those cases, Windows was installed into the partitions not at the start of the drive, not moved there later. Maybe that's the difference.

Anyway, on to solving your problem another way. I have the idea that your goal is to set up the disk so that the Windows partition is at the beginning, the Linux partition is at the end, and all the unused space is in the middle. Is that right? Is the reason that you want to be able to expand the Windows partition if you run out of space in it? If I don't have your goals right, please correct me. If I've misunderstood your goals, I might be overlooking a better solution than what I'm going to suggest here.

Somewhere, probably either on Herman's site or on the Super GRUB site, I saw directions for setting up GRUB to run from a floppy disk so that it would let you boot any partition on the disk. If you don't have a floppy drive in your computer, I imagine the directions could be adapted to booting from a USB Flash drive or a CD. Once set up, the computer would normally boot to Windows. If you put in the floppy (or Flash drive or CD) before booting, you'd boot to a GRUB menu, completely self-contained on the floppy, from which you could select any of the partitions to boot. I don't know whether it suffers from the limitation that the partition you are booting has to be below a certain cut-off address on the drive. We'd have to check into that.

Assuming it works, would that approach meet your needs?

If you don't like that approach, I wonder whether the mechanism in Windows' boot.ini that lets you select among a number of operating systems to boot is limited to booting other Windows instances or can it boot a non-Windows partition? Lot's of unknowns with that one, so I wouldn't count on it working, if I were you.

---

### Post by DonDodge on 2008-01-08
You know what I hate worse than anything? Letting windoze win.

---

### Post by DonDodge on 2008-01-08
Maybe I can force windoze to cooperate if I do things in the proper sequence and as a final step, install my windoze image into the re-shifted partition. I'm skeptical about this since DOS reports a broken C: drive with the extra partition at the front. As such, I couldn't make my image restore into the moved partition, at least on the first try. I was reluctant to keep hammering on it. I suppose there's a point where I should quit arguing with it and work out another solution.

Edit: Although I didn't think of it at the time, I suspect maybe DOS would have found my windoze on a D: drive and allowed a restore of my image into there.

As for my goals with this project:: eventually, I want to work myself out a linux program to analyze  stock market data and quit using the program that requires I buy their very expensive data subscription to work with their program. The data is freely available, I just need to find an open source program to manipulate it. Of course, the eventual end game is making a clean break from M$. 

I have a 160 GB main drive and a 40 GB secondary drive. I like to use the second drive to catch batch backups. I really don't want an OS on that secondary drive. I would prefer to use a portion of that drive for catching linux backups as well as windoze backups. 

I want to have room behind the windoze partition to either make it larger or add in another contiguous windoze partition. Ubuntu doesn't necessarily have to be at the very end of the drive but I don't want it right behind windoze..In fact, I need to find the sweet spot in the middle of the drive where the ubuntu can live and still boot off the grub so as to provide extra space behind it too. I'm not really comfortable with being floppy dependent.

I know I can move the ubuntu installation to some unknown point in the drive where it will boot from grub and allow for this. I just don't know where that point is but it's somewhere between 41 GB and 100-some GB. 

When I moved ubuntu to the very end and it worked for a while after I shrunk it from 40 GB to 20 GB. I realize now what blew that out. I formatted the unallocated space in between to NTFS. This is what I tried rather than trying to expand the windoze partition. After that, I lost my ubuntu, even with the GAG floppy boot, and that's when I set up the copy on the backup drive.

I suppose the path of least resistance is find the point in the middle of the drive where ubuntu will boot without being dependent upon the newer ubuntu installation and will still function with additional NTFS space in between it and windoze. 

The only way the original installation works now is if grub uses the menu.lst located at (hd1,0). I suppose an alternative may be to put a tiny /boot partition at the front of the D: drive. I kinda think grub simply needs to find a menu'lst file there to be able to boot the ubuntu on the main drive.

---

### Post by rkd on 2008-01-08
Okay, you don't like the idea of booting from a floppy to boot Ubuntu. You didn't say that you also don't want to boot from a Flash drive or CD, but I gather you don't like them, either. No problem.

I believe you are right that putting the /boot partition at the beginning of the backup disk would work fine. We can work on that approach, if you like. It should be easy to get working.

You just mentioned that you don't have to be able to expand the Windows partition, but adding another contiguous Windows partition would be acceptable. If I may ask, why do you care whether the second partition is contiguous with the first? It will have to be accessed via a separate drive letter no matter what. So if having two Windows partitions is okay, why not put the Ubuntu partition immediately after the current Windows partition, then when you want more space for Windows, create the second Windows partition following the Ubuntu partition? I'm sure you have some reason. I'm just trying to understand the constraints so I can think of ways to solve the problem within the constraints.

I'm concerned about your experience that adding an NTFS partition between the Windows partition and the Ubuntu partition made it impossible to boot the Ubuntu partition. The way I understand the disk stuff to work, that should not have caused any problem. Until we  understand what happened, I'd be afraid that if we got things set up and working, when the time came to give Windows more space, that would break your Ubuntu stuff again. If you want to investigate that, I'd be happy to work through that with you. We could work out a step-by-step plan before starting anything, and we wouldn't have to do things all at once. That might make experimenting less painful.

I don't know whether this applies to your system, but I remember that one of the magic disk size limits a few years ago was 137 GB. So it might be that the partition in which /boot resides must be completely below 137 GB.  Is that consistent with what you learned in your attempt to put the Ubuntu partition near the end of the disk?

---

### Post by DonDodge on 2008-01-08
Aha, indeed I do have the 137 GB limit. Duh. 

I have a more recent bios update I can flash in but I haven't gotten around to it yet  because I didn't see anything in the description regarding disk access. Not sure if that would fix anything or not.

Regardless, I moved that ubuntu partition to the middle of the drive and it boots just fine but I have to manually redirect the grub to root (hd0,2) from root (hd1,0). Grub keeps going to the menu.lst file at sdb1 and I can't seem to be able to make the change using: 
sudo grub
find /boot/grub/stage1     ---    which offers me two choices - (hd1,0) and (hd0,2)
root (hd0,2)
setup (hd0,2)

The bootup grub menu sticks with what's in the sdb1 menu.lst file and offers me boot choices for both ubuntu installations while the menu.lst file for the main installation only offers one ubuntu choice. When manually editing the bootup parameters for the sda3 installation, it also always has a "savedefault" parameter. I can't figure out where that's coming from since it's set to false. Time to play with that, I suppose.

As for losing access to my ubuntu after formatting the unallocated middle space to NTFS, I believe that was probably due to my ignorance in editing the menu.lst file.

I don't really want to boot from CD because my system won't boot properly from the slave which is a cdrw and i like to leave a dvd-rw in the main optical drive as a removable hard disk. I have a program that backs up a database to that disk every time I exit and I use it for some batch backups too. it's a pain switching disks all the time.

As for keeping contiguous partitions, it just make sense to me that disk access wiould be quicker that way and be less work on the hard drive. I may be all wrong with this notion.

---

### Post by DonDodge on 2008-01-08
Thanks for the wake up call rkd. I flashed the bios and capacity of my first drive increased from 136 to 160.

---

### Post by rkd on 2008-01-08
That sounds very promising. Now it should be very easy -- just move that Ubuntu partition out to the end of your drive, and you should have exactly what you wanted.

I hope it turns out to work that easily.

---

### Post by asmiller-ke6seh on 2008-01-08
> **DonDodge said:**
> You know what I hate worse than anything? Letting windoze win.

Machines CAN'T win - WE are the MASTERS! If you REALLY want to win, just dump Windoze into the bit bucket, and let it rot in 7734 - now THAT'S what I call a WIN/WIN.:lolflag:

---

### Post by DonDodge on 2008-01-08
I can't force this silly thing to recognize the menu.lst file on hd0 or sda. Just for laughs I inserted a blank menu.lst into /boot/grub on hd1 or sdb. The computer read this file but wouldn't read the one I directed grub to use. It wouldn't boot and offered no regular startup menu, only a grub> prompt. Once I restored the file, the gizmo is happy again and will boot any OS and will go to the proper menu file if I manually redirect it at the boot.

The front of this ubuntu partition is now at 85 GB.

---

### Post by DonDodge on 2008-01-08
> **asmiller-ke6seh said:**
> Machines CAN'T win - WE are the MASTERS! If you REALLY want to win, just dump Windoze into the bit bucket, and let it rot in 7734 - now THAT'S what I call a WIN/WIN.:lolflag:

It would be  fine thing if life could be that simple.

---

### Post by rkd on 2008-01-08
It might be that GRUB is numbering the disks differently than you think it is.  I just noticed a link at Herman's site to what seems like a well-organized description of this:

[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

Take a look and see whether that helps you figure out what is going wrong. If it doesn't show you the problem. Ask again and I'll dig into it with you.

---

### Post by DonDodge on 2008-01-08
Believe it or not but it appears I've tamed this beast. 

I couldn't find anything unexpected in device.map or anywhere else all the documentation said to look so I went back in through Super Grub and found everything was all the sudden mapped to hd0,2. and both installations booted just fine off that sda3 menu file. Or I could manually map it to hd1,0 and either would boot 

Next I went back to windoze  and ntfs'd  the unallocated space between hd0 and hd2 and called it a D: drive. Ubuntu booted without a single complaint this time. 

Now my main drive will be partitioned as  41 gb ntfs, 45 gb ntfs, 20 gb ext3, 44 gb ext3 and the linux swap file at the end. Maybe I'll just stretch the ubuntu drive to the right,  over the entire 66 gb space rather that screw around with trying to mount that partition to the file system. That will probably be simpler.

Finally, I copied an old menu.lst file from last week to boot/grub on sda3 and loaded it into the grub and now everything is working perfectly. Using the old file cleaned up all the garbage in the grub that I don't need anymore now that I can safely get rid of the extra ubuntu installation.

With that ubuntu gone, I'll allocate half of that 40 gb drive to windoze backup storage and half to ubuntu backup.

Gentlemen, I thank you so much for all your help  I think we can close the books on this issue. Now I can get back to learning what makes ubuntu crash like a drunk on Saturday night :D

---

### Post by rkd on 2008-01-09
You're welcome. I'm glad it is working properly for you now. I hope it keeps on its best behaviour.

---

