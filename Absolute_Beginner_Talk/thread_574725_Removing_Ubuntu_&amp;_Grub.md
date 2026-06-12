---
title: "Removing Ubuntu &amp; Grub"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Joeb454 on 2007-10-13
Quick question - Think I know the answer, but need to be 100% sure.


If I dual boot Ubuntu & Vista, obviously I'll have Grub as the bootloader, that's fine. *IF* I decide to remove Ubuntu, to remove Grub do I simply pop in the Vista install CD that I have lying around somewhere and type ```
fixmbr
``` into the recovery console?

Also would I be able to use GParted to make the 2 partitions back into one? Or is that not recommended and I'd be better to just stick with the 2 separate partitions now I have them?

---

### Post by banewman on 2007-10-13
If you format the partition with ubuntu on it that gets rid of grub as well. You can use the live cd to remove the ubuntu partition and grow the windows partition. best of luck :)
oops - should have mentioned that gparted is the program on the live cd that will let you do these things..

---

### Post by Joeb454 on 2007-10-13
Thanks, just wanted to make sure I wouldn't bork it all if I wanted to switch back to just windows due to all the Uni work :(

---

### Post by banewman on 2007-10-13
Best of luck. Been ubuntuing for five years since I gave XP the flick, there are new things to learn just the same with any OS in my opinion. :)

---

### Post by Joeb454 on 2007-10-13
Yeah I've used Ubuntu on my Desktop, I dual-boot that for compatibility reasons. Same with the laptop, that'll be dual-booted for compat. reasons.

Only reason I'd switch back to Vista totally is Uni, obviously they have a lot of Windows programs, although there's a surprising amount of open source there (and they run Fedora 7 in VM's). Might have to keep a Vista partition on here anyway for Media Center with the brother's 360 :p

---

### Post by banewman on 2007-10-13
The only thing that I haven't been able to solve using linux is the latest games. As I'm busy doing other things that is not an issue - but I'm sure there would be a solution for that as well :)

---

### Post by scruff on 2007-10-13
> **banewman said:**
> If you format the partition with ubuntu on it that gets rid of grub as well. You can use the live cd to remove the ubuntu partition and grow the windows partition. best of luck :)
oops - should have mentioned that gparted is the program on the live cd that will let you do these things..

That may or may not be true depending on where you chose to install the bootloader. I *think* the default is to put it in the MBR (as I have mine) in which case you would need to do the 'fixmbr' command to remove GRUB.

---

### Post by Duck2006 on 2007-10-13
> Also would I be able to use GParted to make the 2 partitions back into one? Or is that not recommended and I'd be better to just stick with the 2 separate partitions now I have them?

You will have to do that from with in vesta.

---

### Post by por100pre1 on 2007-10-13
Used a different method. I installed GRUB in Ubuntu's partition and added Ubuntu to Vista's bootloader using EasyBCD. This method is good if you are considering to remove Ubuntu. The problem here is that now I want to remove Vista and that requires to install GRUB to MBR, of course there are many ways to do so. :)

---

### Post by steve.horsley on 2007-10-13
If you let Ubuntu install GRUB to the MBR, then you must be aware that GRUB depends critically on files on the Ubuntu partition. Deleting the Ubuntu partition will disable GRUB and leave you unable to boot Windows either. But then, I guess you figured this out anyway. The best thing to do is to remove GRUB by replacing the MBR before you delete Ubuntu. I know this can be done from a Windows install disk. It may also be possible just by running the command **fdisk /mbr** from within your running windows (it used to be possible, I don't know if recent versions of windows can't do it any more).

por100pre1 has a different approach, using a different bootloader in the MBR, which isn't such a bad idea, but I have never ever seen Ubuntu succesfully install its bootloader to the root partition - I get a fatal error and an unbootable Ubultu every time. Still, maybe Gutsy will break the pattern.

---

### Post by blueboy4 on 2007-10-13
> **banewman said:**
> If you format the partition with ubuntu on it that gets rid of grub as well. You can use the live cd to remove the ubuntu partition and grow the windows partition. best of luck :)
oops - should have mentioned that gparted is the program on the live cd that will let you do these things..

I'm sorry but I have to disagree with you there. When you let the Windows partition grow, it screws up all your files. It did for me and had to re-install Windows. So I would highly recommend against the idea actually. :confused:

---

### Post by Sbarton on 2007-10-13
The post #10 by steve.horsley offers you the opportunity of fixing the MBR before taking any other action, (worth a try). Why bother to grow windows, keep the partition unallocated (after deletion) if you are not desperate for space. It will be easier to use next time for whatever you want to do with it.
regards

---

### Post by Joeb454 on 2007-10-14
I think that's what I'll do, or format it as a separate partition and move the My Documents folder there or something, similar to people having /Home on a separate partition

---

### Post by Sbarton on 2007-10-14
As a windows user as well, that's exactly what I have, a separate partition for 'My Documents' and it makes things easier.
regards

---

### Post by Norm24 on 2007-10-14
I'm still very new to this and need to remove Ubuntu.I some how have managed to screw things up.I actually have it installed twice and both don't work right because I played with settings I shouldn't have.I want to start from the beginning again.

My question is this:after starting Gparted from the Live Cd I don't know what partitions are the Ubuntu partitions.

I too am dual booting with XP SP2.

I'd post a screen shot but don't how with Ubuntu.

---

### Post by por100pre1 on 2007-10-14
> **Norm24 said:**
> I'm still very new to this and need to remove Ubuntu.I some how have managed to screw things up.I actually have it installed twice and both don't work right because I played with settings I shouldn't have.I want to start from the beginning again.

My question is this:after starting Gparted from the Live Cd I don't know what partitions are the Ubuntu partitions.

I too am dual booting with XP SP2.

I'd post a screen shot but don't how with Ubuntu.

The XP partitions should be NTFS partitions, Ubuntu partitions should be ext3 partitions.

---

### Post by Norm24 on 2007-10-14
> **por100pre1 said:**
> The XP partitions should be NTFS partitions, Ubuntu partitions should be ext3 partitions.

I was able to delete one but the other won't delete.It says that I have to unmount any logical partitions with a number higher than six of which there are three of them.I assume the little lock icon means its "mounted"?How do unmount them?

---

### Post by Sbarton on 2007-10-14
To post attachments! When you choose to reply, just under the dialogue box you will see 'Additional Options' & attach files, click on 'manage attachments ' and you will be given the opportunity to choose a file to upload, (the file /screenshot you wish to upload).When you choose your file click 'Upload' Submit your reply and the attachment should be added.
HTH
regards

---

### Post by mivo on 2007-10-14
> **Sbarton said:**
> As a windows user as well, that's exactly what I have, a separate partition for 'My Documents' and it makes things easier.
regards

It's not quite the same as a separate /home partition in Linux, though. There's the registry to consider, and Windows programs are frequently not very well behaved and save their stuff in "random" places. There is also nothing quite like Aptitude, or even the less powerful Synaptic.

---

### Post by por100pre1 on 2007-10-14
> **Norm24 said:**
> I was able to delete one but the other won't delete.It says that I have to unmount any logical partitions with a number higher than six of which there are three of them.I assume the little lock icon means its "mounted"?How do unmount them?

Right click them and click Unmount.

---

### Post by Sbarton on 2007-10-14
> **mivo said:**
> It's not quite the same as a separate /home partition in Linux, though. There's the registry to consider, and Windows programs are frequently not very well behaved and save their stuff in "random" places. There is also nothing quite like Aptitude, or even the less powerful Synaptic.
There are no programs in 'My Documents' so no registry entries,(Windows) only data! which goes where you send it and in my case that is a separate partition.
My understanding is that 'Home' in Linux, is a separate partition used for similar purposes.
regards

---

### Post by Norm24 on 2007-10-14
> **por100pre1 said:**
> Right click them and click Unmount.

Doesn't give me that option,its greyed out.

---

### Post by Joeb454 on 2007-10-14
in GParted you just choose to unmount them (I've found that you need to check if there's any other drives in a sort of sub-directory with the little plus sign), these are usually the swap partitions.

You can do it, I'd post screen shots, but I've not got my Ubuntu installation anywhere nearby atm

---

