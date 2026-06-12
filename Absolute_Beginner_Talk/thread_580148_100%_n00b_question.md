---
title: "100% n00b question"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Thumper! on 2007-10-18
right ok, I'v downloaded ubuntu 7.10, this is going to be my first time of formatting and reinstalling ubuntu (i'm on xp pro at the moment). What the best way to format my xp pro computer and install ubuntu...any guides would be helpful. I'v already burned ubuntu onto a disc just ready when you are to format.

Thanks sooo much

Tom :)

---

### Post by Hobo Joe on 2007-10-18
The installer can format for you. :)

---

### Post by Thumper! on 2007-10-18
so let me get this right....i'm in xp, i put the ubuntu cd in and let it do the magic? sorry about this just i'm a total n00b :(

---

### Post by mivo on 2007-10-18
Consider making a separate partition for /home.  10 GB for / (that is where the system files and programs go -- it is larger than it seems to someone coming from Windows), the rest for /home (this is where all your personal files will be, and settings), and 1-2 GB for swap. The advantage of a setup like this is that you can easily re-install the system without losing any of your personal files or settings. :) Personally, I would get the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") (it is only 50 MB) and delete the existing partitions (if you really want to use the entire disk) and partition the disk. Then in Ubuntu you will only have to select the mount points (/, /home, swap), which may be less confusing. File format for / and /home should probably be ext3.

Edit: You need to boot from the Live CDs. It does not work from within Windows. (Well, there are ways, but let's keep things easy :))

---

### Post by Hobo Joe on 2007-10-18
> **Thumper! said:**
> so let me get this right....i'm in xp, i put the ubuntu cd in and let it do the magic? sorry about this just i'm a total n00b :(

Yeah, you put the CD and restart your computer, it will load up Ubuntu(It will take a while, after all, it's loading from a CD. :)), then if you want you can mess around for a bit to see if you like it, then when you want to install there is an icon on the desktop.

It'll give you a few options, and when you get to the part about partitioning just select 'use entire disk'. It'll wipe your harddrive and automatically partition how it needs too, and install.

We were all noobs once. :)

---

### Post by onelife151 on 2007-10-18
OK no one is a noob just because your new doesn't mean your stupid!! have you used ubuntu before on that computer?? yes or no? ask yourself that. If you have then just install it over the previous install you did. If you haven't. I would suggest backing up all your important data to dvd. hope you have a dvd burner. Then once you boot to the live cd check out gparted to have ubuntu resize your windows partition. I am curious to find out how large is your harddrive?? If its say about 80gig or so you could resize the windows partition to 20gigs and leave the remaining 60 gigs to ubuntu and then let ubuntu find those partitions and use that extra space for ubuntu. If you have any guestions you can send me a message or post on here and I will get back to you.

---

### Post by p_quarles on 2007-10-18
> **Thumper! said:**
> so let me get this right....i'm in xp, i put the ubuntu cd in and let it do the magic? sorry about this just i'm a total n00b :(
That's basically correct, but there's a little more to it than that. 

Yes, the installation disk will allow you to resize the Windows partition and create a new filesystem for Ubuntu.

Before you do that, however, you should back up all sensitive data on your hard drive, anything you can't afford to lose. 

Second, to minimalize the risk of corrupting or losing files on the Windows partition, defrag the hard drive *twice*. 

Here's a more detailed guide:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

EDIT: I assumed you wanted to set up a dual-boot. If this is incorrect, disregard this post.

---

### Post by MatthewPlanchard on 2007-10-18
Here, check out the info on this page:

[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

good guides for pretty much anything you need install wise.

---

### Post by Thumper! on 2007-10-18
Thanks guys...nah i'm just gunna chuck EVERY thing away as the computer is virus filled..nothing i need on there and i got a laptop and my main computer spare so it's just a test really..so here's what i'm guna do

Put disk in, Restart, and install it ;)

Thanks sooo much for your help guys

---

### Post by Duck2006 on 2007-10-18
Click the install icon and, when it comes to partitioning tell it to use the hole drive.

---

### Post by Thumper! on 2007-10-18
ok not going to good...put disc in, restated my pc and same old windows loaded back up :( any ideas..god i hope i burned it right

---

### Post by p_quarles on 2007-10-18
Enter your BIOS menu and check the boot order. Most modern PCs have the ability to boot from the CD drive, but it's not always enabled by default.

Entertaining your other question, though: how did you burn it?

---

### Post by Duck2006 on 2007-10-18
Have you set in the BOIS to boot from the CD first?

---

### Post by Hobo Joe on 2007-10-18
Usually the BIOS will boot from the CD if there is a bootable disk in the drive. I'm guessing you didn't burn the CD as an ISO image. 

What program did you use, and what settings was it at?

---

### Post by dougleduck on 2007-10-18
Do you not need to press F2 (maybe another F, F12 if not F2?) to get the boot menu as the computer is just turned on? Then you can choose to boot from CD.

---

### Post by Thumper! on 2007-10-18
is there any other way other than having to burn it to cd as this old pile of S*** won't burn to the disk...windows keeps giving me that my disc is corrupted or what ever and it's brand new :(

i used infra recorder (the one in the tutorial)

and my drive is deffo reqritable drive

---

### Post by p_quarles on 2007-10-18
The page I linked to in my first post also gives a few options for no-CD installations. 

If none of those work, there's always Shipit.

---

