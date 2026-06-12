---
title: "Installation/disk partitioning"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Angelo DePalma on 2007-10-10
I am trying to install Ubuntu on a brand new Dell desktop running Windows Vista. I would like to keep Vista, mainly so I can continue to use my chess software.

When I get to the disk partitioning step I'm completely lost. The Ubuntu directions seem to gloss over this step; the pages that come up in my install do not even look like the ones in the online documentation. 

I have no idea how to set the disk partitions. My installer "sees" what appear to be three disks, or three partitions. I'm not sure (I only have one physical HD drive on the machine). 

I'm not sure if I need to resize all three, or only one, how to judge how much space to give Ubunto, or how that will affect Vista's performance.


Angelo DePalma

---

### Post by Paqman on 2007-10-10
OK, basically you need to create at least two new partitions for Linux. One gets formatted to Ext3 and the system gets installed there. The other is a very small partition called a swap.

You need to create space for these new partitions by shrinking Vista's main partition down. You should do that from within Vista using it's own partition tool. Once you've made enough space for Ubuntu (about 10GB or so) you can shut down Vista, run the Ubuntu installer and make the Ext3 and swap partitions.

Hope that makes sense!

---

### Post by Angelo DePalma on 2007-10-10
Thanks for trying, but I have never partitioned a disk. I don't even know, beyond the very basics, why I would want to do this. The instructions are non-existent.

The web site you referred to does not explain exactly what must be done and how, nor does it illustrate the (undoubtedly) extremely common situation of installing Ubuntu but keeping an MS operating system (e.g. Vista). It  devotes as much space to the screen for filling in user name as it does to partitioning! 

I hate to sound ungrateful, but yikes. 

Most people who try Linux are probably keeping their old OS, at least temporarily. And most are probably not very technically savvy. 

Try to put yourself in our position. "You have to decide which partitions..." is a deal-killer for 99% of computer users!! You're losing 10s of 1000s of potential Linux users -- most of whom don't post to forums -- because of these funky disk partitioning issues.

Angelo

---

### Post by Pumalite on 2007-10-10
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Duck2006 on 2007-10-10
This may help

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by hyper_ch on 2007-10-10
And use the Vista Partition resizing tool to make your existing one smaller.

---

### Post by Angelo DePalma on 2007-10-10
My installation does not show those screens or those instructions. I am using the "Amd 64" version. Does this make a difference?

---

### Post by dptxp on 2007-10-10
No need to resize the main Vista partition, the so-called C-drive.
You can use other partitions.
You can use GParted (download and make live CD) to make your partitions.
6-12 GB for root. 1 GB SWAP.

---

### Post by perixx on 2007-10-10
Hi Palma...

Although that's no Vista (*puke* - sorry, but this had to be :) thread, and I'm no Vista expert - what you're looking for should be: RUN (from 'Start') > diskmgmt.msc (Vista's partitioning / HD managing tool). Since NTFS file format is proprietary MS development, I would think it's better to let them do this job (resizing NTFS partitions) by themselves - although NTFS support by Linux has become quite good by now!

After you've made up some free space, I'd also say it's a good idea to use Linux' gparted for making the ext3 and swap partitions in that space. 

If booting works like it did in XP, you can use the boot.ini and a 'pointerfile' to the Ubuntu partition for booting Ubuntu with Vista's bootmanager (don't know if this still works, though). If you need more info on that, I'll have to look up for the corresponding procedures - quite a while since I did this...    


perixx

---

### Post by Angelo DePalma on 2007-10-10
Once again I sincerely thank you for trying to help me.

The only problem is I don't understand a word you or your previous poster wrote. And nobody seems to understand my problems here:

1) the instructions don't match what I'm seeing during installation

2) there is no guidance I can see for choosing the partitions or sizing them

I can do all the re-sizing in Vista that I like, but I still have to deal with the indecipherable Ubuntu partitioning menu.

It would be really helpful if the instructions gave a real-world example from a real-world MS operating system. You know, "let's say you have WinXP and a 200 Gb hard drive and you want to keep XP. This is what you do...."

It would also be very helpful if the images in the help files resembled the screens I see during my Ubuntu installation. 

I hate to overstep my welcome here, but how on earth do you guys expect the average computer user to switch to Ubuntu when the Linux community cannot put coherent installation instructions on the web?

If this is any indication of what's ahead for me and Linux I am wasting my time.

adp

---

### Post by jpittack on 2007-10-10
I hope that I can better help you understand.  I too have a dell.  From what I hear, do not delete any of the partitions that you already have.  You will need to shrink windows so that you may install ubuntu in the space that you create.

By right clicking Computer and going to manage, you can find a way to create this new space.  say yes to the UAC control.  on the left is disk management.  click this.  find the main vista partition in the middle window. right click and shrink the volume.  keep in mind that 4096 mb = 4 gb.  I personally use 5.3 gb right now in ubuntu.  this is a base of the operating system.  if windows will only be for chess, then shrink windows to 21 gb.   If you plan on doing more, keep more space there. I will let you do the math.  1024 mb = 1 gb.

Next go to install ubuntu.  I suggest using the alternate install cd.  click the box below download when you get the cd.  use md5sum to check the download. use infra recorder to burn the iso.  all documentation and downloads can be found after downloading the alternate cd.

When you first boot of the cd, check it for defects. then you can go about installing ubuntu.   follow the steps.  when you need to partition, use manual.  Make the unallocated space /   root.  I did not set up a swap file.  Hopefully someone else can help you on this.  I am in the current process of setting one up after I have installed everything and may know how to in a few days.

Follow the steps. after wards.  here is a great resource that include screen shots.[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

Please, Please, please ask me any questions.  I am happy to go into further detail.  If something is unclear, let me know!  I am here to help!  Just remember, don't delete dell!

---

### Post by totalnub on 2007-10-10
I've installed ubuntu on a 100g hd with a dual boot with windows XP
what you know as the C:\ drive is a "partition" or space on the physical hard drive.
you understand that you have to shrink something down to make room on the physical hard drive for ubuntu. (by default, windows partitions fill the disk, whether or not the space is actually being used)
my setup:
out of 100GB drive

/dev/hda1 69GB WINDOWS XP formatted NTFS
/dev/hda2 30GB LINUX UBUNTU formatted ext3
/dev/hda3 1GB LINUX SWAP formatted linux-swap

now when you run your ubuntu disk, it comes time to partition, and there are a few different options. I don't know the exact terminology, but I've always gone with the manual config option.
when you're there, you should see your "C:\" as probably /dev/sda2 or something along those lines. It's going to be the largest one with ntfs file type. if you resized this in vista, you should also see some free space. 
in this free space you are going to want to put your ubuntu partition.

create a new partition and set the mount point to "/" select ext3 as filesystem type
leave about 1Gig for your swap space and create a swap partition next filling that space up.
I hope i have somewhat pointed you in the right direction.
GL!!

---

### Post by corowakid on 2007-10-10
I struggled like you to come to terms with "Linuxese", and everything seemed counter to what I'd experienced in Windoze.

FWIW, I found my salvation here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It speaks in terms MS users can understand, its very comprehensive, and you can easily print out any material you think you might need in the future.

Hope this helps.

---

### Post by Angelo DePalma on 2007-10-11
Ok, I think we're making progress here. Thanks for this great info.

I assume that the "Vista partition" is the largest one (146 Gb). The others are like 15 and 6. Right?

Also, you say to use the "alternate install CD". I have already downloaded the "standard" and "64 bit AMD" versions and was trying to install the latter; I am now downloading the alternate install as per your directions. Question: What is the difference between the alternate and other downloads?

Thanks,

Angelo


> **jpittack said:**
> I hope that I can better help you understand.  I too have a dell.  From what I hear, do not delete any of the partitions that you already have.  You will need to shrink windows so that you may install ubuntu in the space that you create.

By right clicking Computer and going to manage, you can find a way to create this new space.  say yes to the UAC control.  on the left is disk management.  click this.  find the main vista partition in the middle window. right click and shrink the volume.  keep in mind that 4096 mb = 4 gb.  I personally use 5.3 gb right now in ubuntu.  this is a base of the operating system.  if windows will only be for chess, then shrink windows to 21 gb.   If you plan on doing more, keep more space there. I will let you do the math.  1024 mb = 1 gb.

Next go to install ubuntu.  I suggest using the alternate install cd.  click the box below download when you get the cd.  use md5sum to check the download. use infra recorder to burn the iso.  all documentation and downloads can be found after downloading the alternate cd.

When you first boot of the cd, check it for defects. then you can go about installing ubuntu.   follow the steps.  when you need to partition, use manual.  Make the unallocated space /   root.  I did not set up a swap file.  Hopefully someone else can help you on this.  I am in the current process of setting one up after I have installed everything and may know how to in a few days.

Follow the steps. after wards.  here is a great resource that include screen shots.[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

Please, Please, please ask me any questions.  I am happy to go into further detail.  If something is unclear, let me know!  I am here to help!  Just remember, don't delete dell!

---

### Post by Angelo DePalma on 2007-10-11
Thanks!

Questions: I have a much larger HD than the one you mentioned. I'd like to devote about 1/2 to Vista and 1/2 to Ubuntu. Of the three partitions you describe below, does any one NOT benefit from being larger? In other words, with all the disk space in the world, how large would you make the swap partition?

Best,

Angelo

> **totalnub said:**
> I've installed ubuntu on a 100g hd with a dual boot with windows XP
what you know as the C:\ drive is a "partition" or space on the physical hard drive.
you understand that you have to shrink something down to make room on the physical hard drive for ubuntu. (by default, windows partitions fill the disk, whether or not the space is actually being used)
my setup:
out of 100GB drive

/dev/hda1 69GB WINDOWS XP formatted NTFS
/dev/hda2 30GB LINUX UBUNTU formatted ext3
/dev/hda3 1GB LINUX SWAP formatted linux-swap

now when you run your ubuntu disk, it comes time to partition, and there are a few different options. I don't know the exact terminology, but I've always gone with the manual config option.
when you're there, you should see your "C:\" as probably /dev/sda2 or something along those lines. It's going to be the largest one with ntfs file type. if you resized this in vista, you should also see some free space. 
in this free space you are going to want to put your ubuntu partition.

create a new partition and set the mount point to "/" select ext3 as filesystem type
leave about 1Gig for your swap space and create a swap partition next filling that space up.
I hope i have somewhat pointed you in the right direction.
GL!!

---

### Post by Angelo DePalma on 2007-10-11
Thanks! I'll check it out. -- adp

> **corowakid said:**
> I struggled like you to come to terms with "Linuxese", and everything seemed counter to what I'd experienced in Windoze.

FWIW, I found my salvation here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It speaks in terms MS users can understand, its very comprehensive, and you can easily print out any material you think you might need in the future.

Hope this helps.

---

### Post by HackCoders on 2007-10-11
You should use partition magic, I use it and it's very easy to use :)

---

### Post by Angelo DePalma on 2007-10-12
Thanks again for all your posts.

As much as I hate Vista, I can see that switching is going to be too much trouble. 

Some really ominous signs:

1. the instructions for a software package have screen shots that do not match those in the software itself

2. the need to screw around, hands-on, with partitions

3. the need to download numerous drivers post-installation

4. the feeling that there is no foundation for me to stand on as I make the change, other than this user group

5. user groups where posters do not understand that 1-4 above are problems. I don't mean to insult anyone who has tried to help me, it's just reality.

[removed trolling part]

---

### Post by Perfect Storm on 2007-10-14
Thread closed - As it seems that OP is trolling the board.

---

