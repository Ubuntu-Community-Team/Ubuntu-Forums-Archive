---
title: "Beige G3- Got it running, need much help installing Ubuntu"
date: 2007-05-16
forum: Apple PPC Users
---

### Post by joshjani on 2007-05-16
OK- I manged to rescue a beige G3 tower from the trash, and I got it up and running. I have it running OS 9.

I want so badly to have it running Ubuntu that I've spent close to a week now poring over all sorts of info here in the forums, wikis, etc, that I don't know what got me to where I am. I think I'm close to success, but it's just not there yet!
[https://help.ubuntu.com/community/Installation/OldWorldMacs]("https://help.ubuntu.com/community/Installation/OldWorldMacs")
Via the info in that link, I can do : "vmlinux (the linux kernel) to “System Folder/Linux Kernels”. Copy initrd.gz (the init ramdisk image) to “System Folder” and rename it to ramdisk.image.gz" However, I think from reading other stuff somewhere that ramdisk.image.gz actually has to be in the kernels folder too.

Anyway, I can manage to get Ubuntu to mostly install, using the 6.10 alternate CD for PPC, until I get about 85% done with selecting and installing software. I think it's because there's no bootloader. So I continue without loading a bootloader. When the computer restarted, I expected to boot to OS 9, then have to switch to  Ubuntu using BootX. Instead, I got nothing but a blinking ? over a disk- the mac doesn't boot to anything.

I am not experienced enough to know what I'm talking about, but I read something that says I have to move a NEW kernel to the kernels folder somewhere during the installation using command line. I wish I knew how to do that. This is where I think I'm falling down and messing things up.

Has anyone had enough success with getting a Beige G3 to run Ubuntu that you could post your commands that allowed you to get through the install and boot (eventually) into Ubuntu? 

I ask because much of what I can find relates to older versions of Ubuntu, and when I try to follow instructions, there are too many differences. I don't know if it makes a difference, but I thought that the newest version would be best at installing and running. If that's not the case, where I can download earlier versions that might at least get me going, where I can then do updates and such.

Are there things better than BootX to accomplish this?

I'm sure I'll keep at it- and I know I'll have more to share and ask as you post replies. Thanks

JC

---

### Post by gwoodard on 2007-05-17
6.10 is a "little" too much for the old world macs so you might want to try 6.06 alternate and see what happens

---

### Post by Brian Smith on 2007-05-17
[http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-powerpc.iso](http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-powerpc.iso)

Maybe you should install using that, or any of the others at:
[http://releases.ubuntu.com/6.06.1/](http://releases.ubuntu.com/6.06.1/)

I'm using that on a G3 Beige with no problems except the normal oldworld difficulties.
The Xubuntu desktop is snappy enough for good web browsing use, I also use Opera as a browser and have 384meg of ram in the machine.  Works for me, and I could probably help with simple installation problems for it, too.  You seem dedicated to getting this running.  I was too, I think it was worth it in the end, though after the week of hassle I wasn't sure!
I actually had better hardware support of PCI USB cards and whatever else I plug into them than I do in OS9 or OSX on that machine.  That's pretty hot considering the old rumors of bad hardware support in Linux distributions.  Ubuntu is excellent!

---

### Post by joshjani on 2007-05-17
> **Brian Smith said:**
> [http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-powerpc.iso](http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-powerpc.iso)

Maybe you should install using that, or any of the others at:
[http://releases.ubuntu.com/6.06.1/](http://releases.ubuntu.com/6.06.1/)

I'm using that on a G3 Beige with no problems except the normal oldworld difficulties.
The Xubuntu desktop is snappy enough for good web browsing use, I also use Opera as a browser and have 384meg of ram in the machine.  Works for me, and I could probably help with simple installation problems for it, too.  You seem dedicated to getting this running.  I was too, I think it was worth it in the end, though after the week of hassle I wasn't sure!
I actually had better hardware support of PCI USB cards and whatever else I plug into them than I do in OS9 or OSX on that machine.  That's pretty hot considering the old rumors of bad hardware support in Linux distributions.  Ubuntu is excellent!

Thanks, Brian- I did download earlier versions- I have a representative of each of the last 4 releases now, I think! I am glad to hear that you'd be willing to help. I AM dedicated now, despite my best judgement that this is a giant time sink that I've gotten myself into... I don't even know what I'm going to do with it once I get Ubuntu on it. It'll be computer 6 in my home! I started off trying to refurbish it for a give-away, but now after all this trouble I feel like I need to keep it.

I think I can get through most of it with just a little coaching. 

First, with partitioning- so far, what I've done is install OS9 on half of a 40gb IDE drive, leaving about 18gb unallocated for Ubuntu. I left the partitions this big because I wanted a functional system either way I boot- my kids like to play these reading games and stuff, and an ancient Mac fits the bill. I would be glad to make the Mac partition smaller, as long as I can still use the Mac side- if only VERY occasionally. I have seen more in-depth partitioning schemes, where folks leave swap space and all, but I just let the installer install where it wants to. Should I do better partitioning???

Anyway- I get the drive partitioned, and I download BootX. I use 1.1.3- I know it's old, but that Ubuntu documentation page says it works, so... I stick the extension in the extensions folder, the application in the apple menu items. I leave Linux Kernels folder in the System folder. I am able to copy from the Ubuntu cd vmlinux and the ramdisk.img. I put vmlinux in the Kernels folder, but I am unsure what to do with the ramdisk. I think I left it in the System folder. Please advise here, too.

Now I get lost- I got through 85% of the install, but then it crashes, saying only that the step "finding and installing software" has failed. I can skip it if I want to. The next step in the installer is "continue without installing a bootloader" I think it's here that I need to do some arcane Linux magic, copying the new kernel into the folder in the Mac partition. I have seen code that I can copy, but it was just slightly different than what I saw on my screen. 

So I guess that's my situation right now. I can get almost there, but I need help with navigating the command line to copy that file and re-boot. And, of course, if I've done anything wrong so far let me know.

Thanks for sticking with the post this far... I appreciate any help you, or any other readers, can give!

JC

---

### Post by Tommy on 2007-05-18
> **joshjani said:**
> I am able to copy from the Ubuntu cd vmlinux and the ramdisk.img. I put vmlinux in the Kernels folder, but I am unsure what to do with the ramdisk. I think I left it in the System folder. Please advise here, too.

technically the ramdisk initrd.img file can be anywhere but I suspect most people keep each in the kernel folder along with its associated kernel -- I keep them together and keep the names similar so I can easily delete them when they're outdated. For example, you only ever use the kernel and initrd from the CD when you are installing... after that you don't need them anymore.
> 
Now I get lost- I got through 85% of the install, but then it crashes, saying only that the step "finding and installing software" has failed. I can skip it if I want to. The next step in the installer is "continue without installing a bootloader" I think it's here that I need to do some arcane Linux magic, copying the new kernel into the folder in the Mac partition. I have seen code that I can copy, but it was just slightly different than what I saw on my screen. 

Since you got the installer to run, you have the kernel and initrd.gz files right. You might try adding "nodma" to your kernel arguments in bootx and see if that lets things get farther. 

Here's a post you might find helpful, though it's describing installing Feisty 7.04 [http://ubuntuforums.org/showthread.php?p=2419715#post2419715](http://ubuntuforums.org/showthread.php?p=2419715#post2419715)

ALSO SubGothius has a much older Mac than yours... Your computer probably has IDE drives in it, but it also has a SCSI bus so you may also have SCSI peripherals. For example, I believe your CD drive is SCSI instead of IDE, so the installer may not have the mesh module loaded, and that may explain why it can't install the software.

You might try switching to a shell and typing this command
```
modprobe mesh
```
and switching back to the installer and seeing if it can install the packages. I'm writing this from memory, however so I apologize if I'm leading you astray.

---

### Post by joshjani on 2007-05-18
> **Tommy said:**
> Since you got the installer to run, you have the kernel and initrd.gz files right. You might try adding "nodma" to your kernel arguments in bootx and see if that lets things get farther. 

Here's a post you might find helpful, though it's describing installing Feisty 7.04 [http://ubuntuforums.org/showthread.php?p=2419715#post2419715](http://ubuntuforums.org/showthread.php?p=2419715#post2419715)

ALSO SubGothius has a much older Mac than yours... Your computer probably has IDE drives in it, but it also has a SCSI bus so you may also have SCSI peripherals. For example, I believe your CD drive is SCSI instead of IDE, so the installer may not have the mesh module loaded, and that may explain why it can't install the software.

You might try switching to a shell and typing this command
```
modprobe mesh
```
and switching back to the installer and seeing if it can install the packages. I'm writing this from memory, however so I apologize if I'm leading you astray.

Thanks for the reply- what does "nodma" do? And do I just type that in as-is to the kernel arguments?

I'm sure I have IDE drives- both use the same 40-pin cable I'm used to seeing. I did, however, try using modprobe mesh during one of my attempts. Would that have caused problems since I don't have SCSI?

I'm ready to start again- I have BootX loaded, running at startup (finally read the directions properly!) I have one 7.5gb partition that OS9 is sitting on, and the rest is unallocated. 

BTW- when I was initializing the hard drive, I had an option of "Linux Home" Anyone know what that is? Would that help the install at all?

Anyway- I'm looking forward to re-trying, but I'm just confused about when to drop to the shell to try to copy the new kernel to the mac side, and what I have to type to navigate to the right spot and actually copy it. That zcat's How-to has sdax in his examples, but I do not. What do I have again with IDE drives? hda? So, I don't know how to distinguish the partitions from each other in that shell, and I don't fully understand mounting/unmounting the mac partition so I can copy the new kernel. 

I'd love an explanation of that part- like, if I let the installer just do it's thing, using the largest space available to it, what's it going to make as far as partitions, and what partition # will contain the mac part where the kernels folder is? That's where I'm stuck, and where I anticipate trouble.

---

### Post by joshjani on 2007-05-20
I am trying to follow what SubGothius did to get Ubuntu running on his OldWorld. The summary I am reading is here:
[http://ubuntuforums.org/showthread.php?t=395441]("http://ubuntuforums.org/showthread.php?t=395441")

I do not have SCSI discs, though, and the install process tells me that hda7 is the partition that I'm installing to. So at step 5/6-

# Mount newly-installed system at installer's /mnt point
# (e.g. /dev paths from my case appear below):
mount /dev/sdb4 /mnt

I put 

mount /dev/hda7 /mnt

I can make it all the way to the step 14. where we are preparing to copy the new vmlinux and ramdisk files. 
At this point, I'm supposed to:
# Mount MacOS partition at /mac:
mount -t hfsplus /dev/sda4 /mac

When I do this, substituting hda7 for sda4 I get a message saying that I can't mount /mac, as hda7 is already mounted or is in use. I'm sorry I can't copy exactly what's written, but that's pretty close. (I'm in the middle of my 6th/7th attempt to re-install right now!)

I noticed that in the first mount command, SubGothius uses "sdb4", and in the second, he uses "sda4"
I can't tell if that's a typo or if I should have some correlation with my IDE drive letters.

I'm increasingly confident that I can make this work, but I desperately need help getting through this one sticky part of copying the new kernel and ramdisk to the Mac side for BootX.

Thanks for any suggestions!

JC

---

### Post by pxwpxw on 2007-05-20
The second mount is meant to be your macos partition, you need to know what partition your macos system is on. I need to read the howto again, will do now.

---

### Post by pxwpxw on 2007-05-20
Something is out of sequence there, yoy seem to be stuck here:

> # Mount MacOS partition at /mac:
mount -t hfsplus /dev/sda4 /mac
# Verify that recognizable MacOS files/folders are in partition just mounted:
ls /mac


which is still in step 12, if I am reading the same reference.

In your case, it will not be /dev/sda4, it will be the partition your macos is on, you need to note this when running the partitioner in step 6.

If you can get that far, and you are sure you dont have scsi, you can probably skip down to

> # Copy new kernel and boot ramdisk files to MacOS:
cp /boot/vmlinux* /boot/initrd* /mac

and continue on from there.

---

### Post by joshjani on 2007-05-20
WHOOO HOOO!:D:D:D

I got it!

Followed SubGothias directions to the letter, except for where his partitions and locations didn't apply. 

In my case, where SubGothias had: 

modprobe hfsplus

I had:

modprobe hfs (I had initialized the mac disk as plain old hfs earlier)


And where he had:

mount /dev/sdb4 /mnt   

I had: 

mount /dev/hda7 /mnt

And where, later, he had 

mount -t hfsplus /dev/sda4 /mac    

I had: 

mount -t hfs /dev/hda6 /mac

Thank you thank you thank you to SubGothias for the step-by-step summary, and to pxwpxw for giving me the hint that I needed to copy the kernel and ramdisk image. I couldn't have done it without you!

Ill post a step-by-step of my experiences, even though I am a relative noob. I relied heavily on that SubGothias post, so I'll probably rely heavily on it for my step-by-step, just adding comments wherever I have something different.

---

