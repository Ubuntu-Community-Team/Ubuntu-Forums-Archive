---
title: "Backing up Ubuntu"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2007-04-08
Hello Everybody,

Back in the bad old days when I used a certain OS from Redmond, I used an excellent backup program called Norton Ghost to back up my entire computer to an external USB hard drive. Is there an equivalent to Ghost in Ubuntu? The only backup programs I can find are somewhat unfriendly looking command line programs.

Thanks.

---

### Post by Gina on 2007-04-08
There's **partImage** but I haven't tried it.  It's supposed to be very similar to Ghost.  Backs up entire partitions.

---

### Post by laidback on 2007-04-08
I use Gparted Live CD to copy my 10Gb Ubuntu 6.06 onto my USB hdd. I have 3 versions which get cycled around in the usual way. This is not the most space efficient method as the copy requires the same space as the original regardless of how much space is actually used up. But, the copies can be used to create clones and I can have them online and fully accessable via the USB hdd. Handy if I'm looking for the odd file I've lost. They appear exactly as the orginals, file structure and directories are all intact. I'm pleased with the system anyway, and since my USB hdd is 250Gb 30Gb for backups is hardly a problem now is it.

---

### Post by Keith Hedger on 2007-04-08
I use dump/restore to backup my sysytem and have never had any problems with it, I run it from a rescue partion, I've tried partimage but it seemed very unstable after the first use.:)

---

### Post by battleshipterry on 2007-04-15
I have been trying to make a bootable image of my linux hard drive so if I need to restore I would just restore from that image. Problem is I am using partimage and when you boot from the system rescue cd which contains the partimage software and try to make image I get stuck at the part where you enter the (Image file to create/use) line on partimages first screen.if I do get it to work it runs out of space quick will not backup entire partition ends up running out of space with in a minute. so I think my file path under (Image file to create/use) is incorrect not sure how to point it towards a spot on my hard drive to leave the image .My hard drive is a 39 gig and I am backing up only 12 gig has lots of space for bakup.

[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---

### Post by thefoolisme on 2007-04-15
Charlie, 

I'm taking from your post that you don't have a dual-boot system.  If you do, you can still use Norton Ghost to make a copy of the whole system.  I had to replace hard drives, so I used Ghost in XP to clone the whole disk (XP and Ubuntu partitions), boot sector and all, made the backup the primary disk, and had my dual-boot system up and running on the new hard drive.

---

### Post by wieman01 on 2007-04-15
I also recommend Partimage... See the HOWTO in my signature.

---

### Post by ramjet_1953 on 2007-04-16
There is a stand-alone iso that you can burn to CD, called Ghost for Linux (G4L).

It is self contained and boots from the CD.
If you are familiar with Norton Ghost, you will feel comfortable with this.

Here's a link to download it.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

ps Don't forget to burn it as an iso

Regards,
Roger :cool:

---

### Post by hyper_ch on 2007-04-16
I just backup my essential files using cron, rsync and hardlinks :)

So if the system breaks total I do a clean install (doesn't take long), then I can restore my files and then I let my "install.sh" script run which fetches my preffered appz from the repos and installs them...

---

### Post by Charlie Chick on 2007-04-20
Thanks to everybody for your suggestions. It looks to me as if backing up my computer (which isn't a dual boot system) is still a bit difficult. I'll put an easy backup program on the wish list for the next version.

---

### Post by Campingman on 2007-04-20
I too give a thumbs up for partimage, using the howto it is very easy to use.  I am a relative noob and recently backed up and restored my entire edgy back up with no problem. You can use the live cd to back up.  I used a usb flash drive with knoppix installed to do the same job.

---

### Post by tech9 on 2007-10-01
> **Charlie Chick said:**
> Hello Everybody,

Back in the bad old days when I used a certain OS from Redmond, I used an excellent backup program called Norton Ghost to back up my entire computer to an external USB hard drive. Is there an equivalent to Ghost in Ubuntu? The only backup programs I can find are somewhat unfriendly looking command line programs.

Thanks.

tar

---

### Post by hsweet on 2007-10-01
Check out Clonezilla at [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/) .. It uses Partimage among other things, but is easy to run.   You can set up a server if you have lots of computers to image and multicast.  That is image a bunch at once, quickly.

Or for one or 2 you would use the clonezilla live cd.   I've used it for my school lab.  works, the live cd is easy.  

My only complaint is that the instructions are badly translated from chinese.

---

### Post by tech9 on 2007-10-02
> **hsweet said:**
> Check out Clonezilla at [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/) .. It uses Partimage among other things, but is easy to run.   You can set up a server if you have lots of computers to image and multicast.  That is image a bunch at once, quickly.

Or for one or 2 you would use the clonezilla live cd.   I've used it for my school lab.  works, the live cd is easy.  

My only complaint is that the instructions are badly translated from chinese.


Clonezilla works good too

---

