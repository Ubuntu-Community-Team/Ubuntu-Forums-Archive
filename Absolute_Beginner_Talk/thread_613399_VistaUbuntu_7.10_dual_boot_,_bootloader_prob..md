---
title: "Vista/Ubuntu 7.10 dual boot , bootloader prob."
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by stvdel on 2007-11-14
Hello, I have looked at countless tutorials on how to dual boot Vista and Ubuntu and seems so easy, but 
it hasnt worked that way for me so far. This is exactly what I did.

Shrank volume in Vista to get some free space
Started 7.10 live cd
Hit install
Went through the steps
Selected use largest continuous free space
But when it gets to the last step the Vista bootloader under migration assistant is not recognized. I tried
it once before without the bootloader being recognized and it just wiped out Vista. How can I get
this to work?

---

### Post by Inxsible on 2007-11-14
Try the Manual partitioning system. use this [link]("http://www.psychocats.net/ubuntu/installing") to help you in figuring it out

---

### Post by Duck2006 on 2007-11-14
You may have to install ubuntu and use EasyBCD as the boot loader to load linux.

---

### Post by dward526 on 2007-11-14
Query...GRUB does not work for you?  I have dual booted with it on multiple systems with vista.

---

### Post by stvdel on 2007-11-14
Thanks for the help so far, so I hope some of you more advanced users can help walk me through this then.

When I get to the manual partition step it is listed so far like this.
                         
                         mount point
/dev/sda1   ntfs  /media/sda1  20966
/dev/sda2                              41943
free space                             12000

Okay so right now I have my Vista on the sda1 20966, the 41943 is my D drive partition
which I will eventually use with Vista and format it. The free space is unallocated. Now
First how should I chop up the free space for Ubuntu and then should they be primary
or logical and what should the mount points be listed as. Also on the windows partitions
what should their mount points be and should they be primary or logical? 

After I complete this step, when I get to the point where it should show the recognized Vista bootloader if it does not again. Is there something in the advanced option I should do?

---

### Post by nikolas68 on 2007-11-14
Format the partition FAT32. Start installation.
When asked about the method of partitioning the HD select MANUAL. Right click the FAT32 you've created and select EDIT PARTITION. Enter a size about 2GB smaller then the one you've created under NEW PARTITION SIZE.
Select the Linux file system EXT32 through USE AS. 
For Mount point make sure you have only / symbol present.
The rest should be easy.

---

### Post by stvdel on 2007-11-14
Sorry , I hope you can give me a bit more clear instructions. I didnt hear anything about primary or logical selections or which partition to format fat32 I am assuming the free space? Also what if the bootloader is still not recognized do I have to mess with the advanced setting at all to specific where grub is loaded? If I could have gotten a clear layout of what to do I wouldnt be typing this again, but thanks for the help.

---

### Post by Inxsible on 2007-11-14
Did you try the link i gave you earlier. It lists all the steps for installing, in detail. They are also illustrated, so you can't go wrong.

---

### Post by stvdel on 2007-11-15
Okay I have read the tutorial and it doesnt offer much help. All I have done since it Manually created in the free space a ext3  primary partition as / at 11 gb and the rest for swap.
But when I get to the next step, NOTHING IS LISTED! under the Migration assistant. I have been here many times before and if I go on it will erase Vista. Again what do I have to do the tutorial says nothing about this problem its just like the rest of the ones i've read that says the bootloader should just appear. I still have no idea if I have my partitions set up right (primary or logical) I dont know exactly what that is for on all my partitions? Help if you can

---

### Post by wolfen69 on 2007-11-15
make your ubuntu partitions mount point "/". migration assistant is not needed for dual booting. ignore that and move on.

---

### Post by stvdel on 2007-11-15
what I am saying is that at the the step after the partition step , my vista bootloader is
not listed, it is blank where it should be. last time I tried to install without the bootloader
being recognized it installed ubuntu and rebooted right into ubuntu, the grub did not show
up and offer me a dual boot choice, I am trying to prevent this from happening again and
having to install vista again and start over.

---

### Post by erfahren on 2007-11-15
> **stvdel said:**
> .. last time I tried to install without the bootloader
being recognized it installed ubuntu and rebooted right into ubuntu, the grub did not show
up and offer me a dual boot choice, I am trying to prevent this from happening again and
having to install vista again and start over.
that's odd. Were you using the manual partitioning way when you installed that time?

---

### Post by confused57 on 2007-11-15
Here's how to boot linux from the Vista bootloader, using EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

You'll need to install grub to the root partition, rather than to the mbr, for this to work.

---

### Post by dward526 on 2007-11-15
> **stvdel said:**
> what I am saying is that at the the step after the partition step , my vista bootloader is
not listed, it is blank where it should be. last time I tried to install without the bootloader
being recognized it installed Ubuntu and rebooted right into Ubuntu, the grub did not show
up and offer me a dual boot choice, I am trying to prevent this from happening again and
having to install vista again and start over.

what were the steps you used with the failed install?  i.e. where was your Vista partition, did you install GRUB in the MBR, where did you mount the root partition.  I have succesfully dual-booted 3 vista/ubuntu and other vista/linux systems, and have only had a problem once when I accidently formatted my Vista via LVM...I was new at this ;).

---

### Post by stvdel on 2007-11-16
Okay let me explain exactly what I have done First install attempt , I tried following a dual boot tutorial

Shrank volume in Vista to get some free space
Started 7.10 live cd
Hit install
Went through the steps
Selected use largest continuous free space
But when it gets to the last step the Vista bootloader under migration assistant is not recognized. I went on with the install as is without the vista bootloader being recognized, it installed rebooted and booted
right into ubuntu, there was no selection to choose from vista or anything.

Now I have been trying my best from posts from everyone here to follow the advice I have seen. I booted the live cd hit install went through the same steps except I choose manual install this time.
When I get to the manual partition step it is listed so far like this.

-------------------mount point
/dev/sda1 ntfs /media/sda1 20966
/dev/sda2 ---------------------41943
free space ---------------------12000

Okay so right now I have my Vista on the sda1 20966, the 41943 is my D drive partition
which I will eventually use with Vista and format it. The free space is unallocated.

I took the free space and made two more partitions out of it in the manual steps 11gb
as primary ext 3 and the root and 1 gb as primary swap file which adds two more like this
/dev/sda3 ext3--------/--------11gb
/dev/sda4  swap 1gb
When I go to the next step I do not seethe Vista bootloader recognized and am afraid if I go
on I will make the same mistake and go on with the install and it just boot right into ubuntu.

---

### Post by Inxsible on 2007-11-16
The point where you selected largest contiguous space, try selecting Manual and do the partitions yourself. Its much safer that way and you know exactly where your Vista is and where your Ubuntu will go.

Once you select Manual, you will be able to see your unallocated space and you can then go on and make partitions within that space.

I find that I trust my eyes more than any automated software. :)

---

### Post by stvdel on 2007-11-16
confused 57,, I will give the easy bcd a try also, I am just hoping to figure out what I may be 
doing wrong, like I notice there is an advanced tab I think that says where to install the 
grub but I am not sure exactly where it should go if that is the problem.

---

### Post by stvdel on 2007-11-16
can someone confirm if this will work right, so far above i have given all the steps i have done, now to list exactly what it says on the final page of the install steps.

The partition tables of the following devices are changed
SCSI 1(0,0,0)(sda)

The following partitions are going to be formatted
partition #3 of SCSI1 (0,0,0)(sda) as ext3
partition #4 of SCSI1 (0,0,0)(sda) as swap

If I click the advanced tab it show up as this:
checked box for install boot loader
Device for boot loader install (hd0)

Also on the top of the screen (not in the advanced tab) there is nothing that lists the 
Vista bootloader,(it is not recognized) now if I continue with this will it erase Vista or do
I need to change something.

---

### Post by Inxsible on 2007-11-16
i dont think it will remove vista. but it will overwrite the vista bootloader with grub (ubuntu's bootloader)

you can choose to install grub in the same partition where you are installing ubuntu. or you can install EasyBCD to keep using the vista bootloader.

IMHO, grub is the best. it shows you the list of Operating systems to choose from.

---

### Post by erfahren on 2007-11-16
no, it's not doing anything to the Vista or the D partitions. That's pretty much how it looks when I do it.

I'd go with GRUB as well.

---

### Post by bumanie on 2007-11-16
I agree, although I am no expert, that list you provided looked OK to me. Won't guarantee anything, but I believe you should soon have a dual boot system.

---

### Post by jaybombalous on 2007-11-16
This is not hard, once u overwrite the shitty boot loader that windows installs all u need to do is boot to ubuntu and 


```
gksudo gedit /boot/grub/menu.lst
```

and enter in the information for your windows vista boot partition.

A quick google search and u can find this info. In the mean time I will look too, but u should try to find it yourself.

---

### Post by Inxsible on 2007-11-16
> **jaybombalous said:**
> This is not hard, once u overwrite the shitty boot loader that windows installs all u need to do is boot to ubuntu and 


```
gksudo gedit /boot/grub/menu.lst
```and enter in the information for your windows vista boot partition.

A quick google search and u can find this info. In the mean time I will look too, but u should try to find it yourself.
If you install Windows before Ubuntu, the ubuntu installer will automatically add that for you in the grub.

---

### Post by jaybombalous on 2007-11-16
> **Inxsible said:**
> If you install Windows before Ubuntu, the ubuntu installer will automatically add that for you in the grub.


then whats the problem??? he has no option in grub, so the first place to look is grub and u should see this entry...

```
title         "Windows Vista"
root         (sd0,0)
chainloader      +1
```


if not then there is other problems, maybe he should read this page and the problems presented with windows vista and linux...

[http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

---

### Post by stvdel on 2007-11-16
jaybombalous i think this is the answer i have been looking for, since ubuntu is not recognizing
windows and not adding it to grub i think i have to go into the menu.lst file and change it after
because when the install finishes it just boots right into ubuntu and grub does not pop up.
thanks for this!

---

