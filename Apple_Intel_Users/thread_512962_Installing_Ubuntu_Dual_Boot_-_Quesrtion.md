---
title: "Installing Ubuntu Dual Boot - Quesrtion"
date: 2007-07-29
forum: Apple Intel Users
---

### Post by greenz on 2007-07-29
Im trying to install Ubuntu on powerbook I used boot camp to partition 10gig for linux out of 70. My issue is on this step

"At step 4, "Prepare disk space", choose Manually edit partition table and click Forward. Delete /dev/sda3 (and /dev/sda4 if it exists) from /dev/sda. Create an ext3 partition taking up all but 512MB of the disk and mount it on /, and create a swap partition taking up the remaining 512MB. Click Forward."

when i create the ext3 partition for 512mb (/) and swap for 512mb (s) that is 1 gig total for linux. Where is the rest of my 9 gigs going to go? Do i set 9500mb for (/) and the rest in the swap? Also is the swap used for moving files between mac os x and linux?

thanks for the input

---

### Post by cilynx on 2007-07-30
I've not done this particular setup myself, but yes, you should be safe giving 9.5G to (/) and ~512M to swap.  The swap is not used for file transfer.  It is only used as "auxiliary, really slow RAM" when Linux is running.

---

### Post by ronocdh on 2007-07-30
Greenz,

Please link to the guide you're using. It sounds a bit complicated, and needlessly so. Dual booting (with Feisty, anyway) is as simple as partitioning your drive and popping up in the Ubuntu disc, then installing to the new partition. The default configuration generally works excellently; you don't actually need swap space, and you can add a swap file at any point after installation, should you wish to.

---

### Post by russo.mic on 2007-07-30
I don't think ubuntu can be installed on a partiton of less than 3 gigs, can it?  Anyway, the swap is a place where the swapfile lives, and it's related to the way your system handles paging and RAM.  it's essentially space that you don't use, but the OS does.  I've always understood that you want to have a swap partition as big as the amount of ram you've got. 

I've got 5 gigs dedicated to /, as that's where the system lives, 2 gigs (or however much ram you've got) for swap, and the rest for your /home, as that's where you'll want to keep all your files and stuff.  Although you don't HAVE to create a seprate partition for your /home, I recommend it so if/when you upgrade or reinstall, you can keep all your personal stuff.  

ronocdh is right, this howto seems like it's not very descriptive, or your reading it incorrectly.

---

### Post by Greenwizard88 on 2007-07-30
> **russo.mic said:**
> ronocdh is right, this howto seems like it's not very descriptive, or your reading it incorrectly.
The how-to is a mess. It talks about opening terminal, partitioning via terminal, and isn't helpful about much of anything. Sure it's easy enough to follow, but coming from an OS X world where everything just works with a few mouse clicks, it can be quite intimidating.

---

### Post by cyberdork33 on 2007-07-30
whether swap is needed or not, and how much you have is a widely debated subject. Swap is used as temporary storage by OS. there are no 'files' stored here. It is used during memory intensive processes, and for other things such as storing the state of your session when using suspend-to-disk functions.

It is highly regarded as best practice to have a swap area although you don't HAVE to. how much is another story. Some say 2x RAM, some say 1x RAM, etc. I actually have only 1GB of swap (w/2GB RAM) because I don't plan on using the swap much for the things I do. If you plan on doing a lot of processor-intensive work with graphics, video, etc, you might want more swap, if you are just checking email, surfing the web, playing some games and listening to music, you do not need as much. I think that 1GB is a good size for most considering the state of machines today.

---

### Post by greenz on 2007-07-30
> **ronocdh said:**
> Greenz,

Please link to the guide you're using. It sounds a bit complicated, and needlessly so. Dual booting (with Feisty, anyway) is as simple as partitioning your drive and popping up in the Ubuntu disc, then installing to the new partition. The default configuration generally works excellently; you don't actually need swap space, and you can add a swap file at any point after installation, should you wish to.

The thing of it is that the guide is easy to follow but when it talks about partition its going off the assumption that most users will partition more than half of there drive for linux. So they can use the second option which uses the most free space. In my setup out of my 70 gig i just want 10g for linux. So my steps are a bit different. So what yall are telling me is if i used bootcamp to partition 10 gig for linux. 

When i get to step 1 under this wiki for 7.04 [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

I delete the /dev/sda3 - 10gig partition. make an ext3 for 9.5 then a swap for 512mb and then a /home for 1 gig? also i looked in another article and is said not to mount the efi partition. How do i dismount the partition in that partition dialog box?

---

### Post by cyberdork33 on 2007-07-30
> **greenz said:**
> I delete the /dev/sda3 - 10gig partition. make an ext3 for 9.5 then a swap for 512mb and then a /home for 1 gig? also i looked in another article and is said not to mount the efi partition. How do i dismount the partition in that partition dialog box?

Your setup adds up to 11GB. Also, you probably want more space for /home (personal storage and files, i.e. music, pictures, documents, etc), and less for / (main OS). Maybe a 5GB /, 1GB swap and 4 GB home?

And to NOT mount the EFI patition, while you are installing, in the partition editor, you can select the partition, and tell it not to be used. If there is nothing in the 'mounted on' column (or something like that) of the table, then you are good.

---

### Post by greenz on 2007-07-30
> **cyberdork33 said:**
> Your setup adds up to 11GB. Also, you probably want more space for /home (personal storage and files, i.e. music, pictures, documents, etc), and less for / (main OS). Maybe a 5GB /, 1GB swap and 4 GB home?

And to NOT mount the EFI patition, while you are installing, in the partition editor, you can select the partition, and tell it not to be used. If there is nothing in the 'mounted on' column (or something like that) of the table, then you are good.

Thanks Cyberdork and all others for explaining this too me. I now have ubuntu installed and working correctly.

---

