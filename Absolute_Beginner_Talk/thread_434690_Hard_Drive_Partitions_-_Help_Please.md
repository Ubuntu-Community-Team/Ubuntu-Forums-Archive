---
title: "Hard Drive Partitions - Help Please"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Aquabuntu on 2007-05-06
Installed Feisty to dual boot with XP last night and everything working well :guitar: 

There's always a but.

But, I think I was a bit too hasty in creating my partitions and need advice. I have a 320GB SATA2 HDD and GParted displays the following partitions:

Partition..........F/System     .....Mountpoint............Size.........Used.........Unused......Flags
/dev/sda1             ......NTFS                           .........../media/disk...........19.53GB....4.38GB.....15.15GB.....boot
/dev/sda2             ......ext3............../media/disk-1........5.58GB......1.99GB.....3.59GB
/dev/sda3.......extended...................................10.71GB
/dev/sda5.......linux-swap.................................1.39GB
/dev/sda6.......ext3............./media/disk-2..........9.32GB.....299.63MB..9.02GB
unallocated.....unallocated.................................292.26GB

/dev/sda1 is my WinXPSP2 installation and I assume the MBR has the GRUB config as it's flagged as boot.

When I did the Ubuntu install I wanted a Main ext3 partition for my install, a swap drive and then another partition for my files and settings so that I can reinstall whenever I need to and leave all my files and settings untouched.

I always store my files, mp3's, movies, downloads etc on a different partition to the main OS drive for the same reason but normally made several partitions so that defrag doesn't take 3 days to complete :) 

So, my questions are:

1) I never intended to have the /dev/sda3 partition and must have created it by mistake. Can I and/or How do I safely delete this partition? The fact that the 2 partitions below it are listed exactly as above (with the indent) also confuses me. Are the /dev/sda5 and /dev/sda6 partitions somehow dependent on the /dev/sda3 partition so that I cannot delete it?

2) Based on the space used I assume that /dev/sda2 is my main drive and  /dev/sda6 is for my files and settings. Is that smell from the inside of my @ss :mrgreen: or is my assumption correct ?:-k 

3) What I want to end up with is an XP install partition 20GB, Ubuntu partitions (incl SWAP, main etc) totalling about 20GB and then 2 large partitions (preferably NTFS) for storage, 1 for MP3's and 1 for Downloads, Movies etc. But it won't allow me to create more than 1 partition in the space that's left. There's a limit on how many you can create on a single drive and I need 1 for XP, 3 for Ubuntu and 2 for storage, which is 6. How do you advise  I go about this? :-k 

Both installs are new and shiny and I have a custom unattended install disk for XP so I have no problem starting from scratch and reinstalling XP and Ubuntu if that's the best solution. Because I'd rather get it setup perfectly now so that I can invest time in customising and tweaking both OS's properly. Ya know, do it right first time ;) 

In the stickies they said "Give info", so, I gave info  
I just hope it's not too long to read 8-[. Thanks for taking the time, I'll appreciate your input.

---

### Post by Bachstelze on 2007-05-06
Could we have a screenshot of the GParted window ?

---

### Post by junjan on 2007-05-06
In the Gnome Partition Editor (GParted) you can create and remove partitions as you like.  Your main partition where the system is installed should have a "/" mount point.

You should read this about how to [modify your Fstab]("http://ubuntuforums.org/showthread.php?t=283131")
You have a nice explanation on NTFS partitions management [here]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G").

:)

---

### Post by raja on 2007-05-06
You should have your extra partitions set up under one extended partition. I think the best way to go about it without disturbing the install is to first delete sda3,sda6 and sda3. Now you should have one large contiguous empty space. Create your swap first in this space. The make all the remaining as an extended partition. Under this, create a 10 GB /home. Then the remaining space can be split into two and formatted as NTFS for your data.
I hope it is clear.

---

### Post by Aquabuntu on 2007-05-06
Yeah, sorry, I surf on my work notebook and my main PC has no net connection, so a screenshot is a bit of a hassle. I used spaces and it looked all neat until I posted it and all the spaces were taken out :oops: . Not sure how to do it so I just edited my post and used punctuation to space the partition info so it's easy to see.

The above reply about the "/ " confuses me because during the install I marked /dev/sda2 as the "/ " mount point.

---

### Post by Aquabuntu on 2007-05-06
> **raja said:**
> You should have your extra partitions set up under one extended partition. I think the best way to go about it without disturbing the install is to first delete sda3,sda6 and sda3. Now you should have one large contiguous empty space. Create your swap first in this space. The make all the remaining as an extended partition. Under this, create a 10 GB /home. Then the remaining space can be split into two and formatted as NTFS for your data.
I hope it is clear.

GParted shows all my partitions with a lock and it won't just let me delete them. You said I should delete sda3,sda6 and sda3, but I assume you meant sda3, sda5 and sda6 ?

Your answer makes sense but I'm nervous because sda6 has some used space (299.63MB).

1) Will t be OK to delete sda6?
2) How do I delete the partitions when it shows them marked with a padlock and the delete option is greyed out?
3) Will XP be able to read the storage partitions if I create them as per your suggestion?

PS: Yeah, I know there is loads of info about this on the net and I'm not too lazy to research it, but I'm new to the community and would rather hook up with some real, live fellow Ubuntu-ists on the forums to discuss my problem ;)

---

### Post by Aquabuntu on 2007-05-06
> **Aquabuntu said:**
> GParted shows all my partitions with a lock and it won't just let me delete them. You said I should delete sda3,sda6 and sda3, but I assume you meant sda3, sda5 and sda6 ?

Your answer makes sense but I'm nervous because sda6 has some used space (299.63MB).

1) Will t be OK to delete sda6?
2) How do I delete the partitions when it shows them marked with a padlock and the delete option is greyed out?
3) Will XP be able to read the storage partitions if I create them as per your suggestion?

PS: Yeah, I know there is loads of info about this on the net and I'm not too lazy to research it, but I'm new to the community and would rather hook up with some real, live fellow Ubuntu-ists on the forums to discuss my problem ;)

About my above post, have just worked out that I can delete them if I just unmount them, BUT I still need an answer on questions 1 and 3.

Ta!

---

### Post by antoz on 2007-05-06
If you are in Ubuntu it is easy to take a screen shot click Application->accessories->take screenshot
Take the shot in gparted as HymnToLife sugested

---

### Post by Aquabuntu on 2007-05-06
> **antoz said:**
> If you are in Ubuntu it is easy to take a screen shot click Application->accessories->take screenshot
Take the shot in gparted as HymnToLife sugested

Hi Antoz,

As I said above, I'm surfing on my XP notebook from work, I have no net connection on my main PC. But, I just tried out my flash drive and it works ba-yoo-ti-fully, so here is the screenshot (see attachment)

---

### Post by Aquabuntu on 2007-05-06
As per above advice, I have a solution to the partition question, the only thing I still need to know is if I can safely delete sda6 because it has data in it. Will I break Ubuntu if I delete it.

---

### Post by junjan on 2007-05-06
Sorry about my "/" comment... 
In all my linux installations the system was mounted on "/". Looks like you have mounted it in "/media/disk-1". Hence you can erase and recreate your other partitions as raja suggested.
Maybe I am mistaken though.. :confused:

---

### Post by dptxp on 2007-05-06
Your SDA3 is the extended partition, it includes SDA5 and SDA6, and will include the unallocated partition once you format and mount it (if it is in extended as I think).

The extended partition holds all other partitions in the extended. DO NOT touch it.

REINSTALL UBUNTU.

Your installation is recent, do not play with fstab.

Do not leave any partition unallocated, that space goes waste otherwise.

Set Format in FAT32  (or EXT3, XP shall not read EXT3 as such) during install. Make it Disk-3.

Make more partitions in it if you want. But let them be formatted too.

REST is FINE.

---

### Post by Happy_Man on 2007-05-06
To unlock the partitions, run the following code in the terminal while booting off the LiveCD:
```
sudo umount /dev/sda
```

Then you will be able to delete.

---

### Post by Aquabuntu on 2007-05-06
> **dptxp said:**
> Your SDA3 is the extended partition, it includes SDA5 and SDA6, and will include the unallocated partition once you format and mount it (if it is in extended as I think).

The extended partition holds all other partitions in the extended. DO NOT touch it.

REINSTALL UBUNTU.

Your installation is recent, do not play with fstab.

Do not leave any partition unallocated, that space goes waste otherwise.

Set Format in FAT32  (or EXT3, XP shall not read EXT3 as such) during install. Make it Disk-3.

Make more partitions in it if you want. But let them be formatted too.

REST is FINE.

OK so gut feel was correct about the way it displayed with an indent in GParted. Solid advice, thanks. 
But, I was a bit impatient and went ahead and deleted sba3-6 because I needed to copy all my files from a network share and it takes ages. I only got your reply now after the fact :oops: 

NEway got more than one piece of Ubuntu back :lol: so reinstalled and created ext3 7GB mount / and swap 2GB, install was quick. Back to my desktop, dual working great. Busy creating ext partition in remaining and then will do ext as spec'd by u.

Thanks 4 the help.

---

### Post by dptxp on 2007-05-06
You should have made all partitions during reinstall.
Life would have been simpler.
But you can manage. You will have to edit to mount the new partitions.

---

### Post by Aquabuntu on 2007-05-06
OK will remember next time. So, current config is Primary NTFS 20GB, Primary / and Primary swap and then in remaining space created ext part and within 3 log part = 10GB FAT32, 110GBNTFS and 150GBNTFS

Formatting 110 and 150 in XP and will boot to live to format the 10GB and mount it. Assume all will be well.

Will be back to discuss if I have issues. Thanks.

---

### Post by Aquabuntu on 2007-05-06
Oops, forgot to ask.

Any particular drive letter allocations I need to know about?

---

### Post by Happy_Man on 2007-05-06
Linux doesn't use drive letters, everything is under the / directory. Your other partitions can be set to mount in /media, your settings and files are in /home, etc. It's a bit hard to get used to at first, but it becomes second nature very quickly. :)

---

### Post by Aquabuntu on 2007-05-06
I can't stop giggling.

Can't believe I'm actually telling you either. I should just slink off quietly.

Using GParted thinking I'm fiddling with my ext part, brainwarp here managed to change the disk label thereby killing everything. \\:D/ 

Soooo, begin @ the beginning. Slowly & carefully take your hands OFF the red button Mr Smith ](*,)

---

### Post by Aquabuntu on 2007-05-06
Thought I should let you know that I have it set up properly now with all partitions the way I want.

GParted confused me by only having the option to create primary or logical partitions, so when I wanted to create the ext part for the 3 logical drives I didn't know how so booted into XP and made one, then booted live and made the 3 logic parts.

See attached screenshot

Mental note to be careful when using live CDs and Ubuntu. It puts more power in your hands than you're used to :-k

---

### Post by dptxp on 2007-05-07
Congratulations.
But LInux shall not be happy with your NTFS partitions.

---

### Post by Aquabuntu on 2007-05-07
> **dptxp said:**
> Congratulations.
But LInux shall not be happy with your NTFS partitions.

Thanks man.

I copied over loads of files from my network drive and Ubuntu sees them and I can browse the files so it seems to be OK. I only need to be able to read multimedia files from those partitions, I don't want write access. Very nervous that I'll make another sudden move and toast something on my XP install without fully knowing what I was doing.

Is write access what you're referring to or is there a more obscure reason why they won't play nice together?

---

### Post by raja on 2007-05-07
> **dptxp said:**
> Congratulations.
But LInux shall not be happy with your NTFS partitions.
Why so ? As read-only, it will work perfectly. And even for write-access, I have been using NTFS partitions in Ubuntu for about more than 6 months at both work and home and not had a single problem so far.

---

### Post by Aquabuntu on 2007-05-07
> **raja said:**
> Why so ? As read-only, it will work perfectly. And even for write-access, I have been using NTFS partitions in Ubuntu for about more than 6 months at both work and home and not had a single problem so far.

Thats cool. If I need write access I'll enable it but for now scaredy cat will stick with read access only.

Thanks!!

---

