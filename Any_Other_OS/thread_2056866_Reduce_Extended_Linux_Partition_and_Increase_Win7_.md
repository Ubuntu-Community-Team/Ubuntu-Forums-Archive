---
title: "Reduce Extended Linux Partition and Increase Win7 Partition"
date: 2012-09-12
forum: Any Other OS
---

### Post by Image0fman on 2012-09-12
Hello, 

I have a dual booted system running win7 & bt5. I installed win7 first then installed bt5 so I think grub is installed to the MBR but windows7 has the boot flag (as shown in gparted). I am using gparted to try and reduce my bt5 partition and add more space to my windows 7 partition. The bt5 is an extended partition, I used the shrink option in gparted and now have some unallocated space but don't know how to add it to the windows partition without effing it up. When I click new on the unallocated space I have the option of creating a logical partition, it needs me to enter where to start it but I am not sure what to do here.. any help is greatly appreciated thanks!

---

### Post by cottfcfan on 2012-09-12
you don't need to add the space to your win 7 partition.
What you need to do is to click on your Win 7 partition & extend it into the unallocated space.
 It should be the arrow button 3rd in from the left in gparted (resize/move)
A pic of your partition table would be useful though.

---

### Post by oldfred on 2012-09-12
Moved to otherOS.

You may have to move start of extended partition, so then the unallocated is in the primary space next to the Windows partitions. If Linux partition is at beginning of extended then you have to move it right first.

I am not a believer in large system partitions. I prefer smaller system partition for both Linux & Windows and large data partitions. If you want to share between Windows & Linux you can just create another NTFS partition in the unallocated space.

---

### Post by bhuvneshdave on 2012-09-12
it may increase risk of data lose and hard disk errors

---

### Post by Mark Phelps on 2012-09-12
Messing around with Win7 partitions using Linux tools is asking for trouble.  IF there is unallocated space between the "end" of the Win7 partition and the "start" of the Extended partition, all you should have to do is the following:
1) Boot into Win7
2) Open the Disk Management utility
3) Select the Win7 partition next to the Extended partition
4) Use the option to Extend Volume

It might have to reboot to do that, but when done, your Win7 partition will be larger -- and you won't be risking filesystem corruption doing it this way.

---

### Post by Image0fman on 2012-09-12
Hey everyone thanks for the replies, appreciate it. Here are two pix from both windows and backtrack. Just so everyone knows I took two pix on the backtrack side. One is of what I mentioned in my original post (created unallocated space) and the other I added the unallocated space back to the way it originally was. I was not able to extend space from windows or backtrack using your suggestions. The backtrack partition is an extended partition. Any Help is greatly appreciated thank you.

---

### Post by oldfred on 2012-09-12
You have to move the Linux partition right so the unallocated is in the left side of the extended, then move extended start right to move unallocated out of the extended partition. 

Then with unallocated next to Windows  as Mark Phelps use Windows to add the unallocated to the Windows partition. When you reboot Windows it will want to run chkdsk to see its new size.

---

### Post by Image0fman on 2012-09-14
> **oldfred said:**
> You have to move the Linux partition right so the unallocated is in the left side of the extended, then move extended start right to move unallocated out of the extended partition. 

Then with unallocated next to Windows  as Mark Phelps use Windows to add the unallocated to the Windows partition. When you reboot Windows it will want to run chkdsk to see its new size.

Hey thanks for the help everyone! Love this forum. 

Anyways I followed the above instructions from oldfred and I believe I followed them correctly. I got the unallocated space moved to the left of the extended partition. Booted into windows and tried "extending" the volume but it was grey out.. Do I need to make it a dynamic disc (kinda hesitant) .. Also I formatted the space and made an ntfs partition but still couldn't extend. Anyways I'm booting back into gparted to see whats up.. thanks again!

---

### Post by critin on 2012-09-14
Unallocated space means do not format to anything.

---

### Post by Image0fman on 2012-09-14
> **critin said:**
> Unallocated space means do not format to anything.
uh ok..

---

### Post by Image0fman on 2012-09-14
@**oldfred**  SUCCESS!

I forgot to move the unallocated space OUT of the extended partiton. Thanks again everyone who helped me get this solved, I now feel more comfortable with my dual-boot setup & partitioning! 

Thanks!

---

