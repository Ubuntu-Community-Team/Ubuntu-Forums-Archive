---
title: "Upgrade or no?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-04-28
I have ubuntu 6.10 running ok with my ATI Radeion 9550 graphics care (took me several weeks and a lot of exploring to find a solution to the non-optimum resolution message that displayed whenever I launched 6.10).

So, now, I read that there is a bug affecting ATI x-series cards (is that mine?).  Should I bother to upgrade or not?

Thanks.

Caruso

---

### Post by Outrunner on 2007-04-28
No you're card isn't part of the X series(those are the X1300, X1600, etc). If you feel adventurous, you might like to upgrade. If not, and Edgy works for you then I guess you don't need to upgrade.

---

### Post by seetho on 2007-04-28
If it ain't broke don't fix it. I learnt it the hard way many many times.

I found somethings not working for me in feisty so I'm back to dapper now.  Everything works and I'm happy.

---

### Post by NyteGeek on 2007-04-28
> **carusoswi said:**
> I have ubuntu 6.10 running ok with my ATI Radeion 9550 graphics care (took me several weeks and a lot of exploring to find a solution to the non-optimum resolution message that displayed whenever I launched 6.10).

So, now, I read that there is a bug affecting ATI x-series cards (is that mine?).  Should I bother to upgrade or not?

Thanks.

Caruso

I would recommend sticking with edgy and waiting a while to install feisty unless you are adventurous like myself and don't mind configuration tweaking.

---

### Post by carusoswi on 2007-04-28
Thanks for the reply.  What made me hesitate was that when I boot from the CD, I get that same message about non-optimum resolution.

I'd like to upgrade to see if that will solve some of my connectivity issues (have had no success getting Samba to properly see other resources on my network).

Have tried to upgrade from the 'net without success so far - am tempted to clean install and just reload all my aps, etc.  Hate to lose my virtual machine, however.  Was a pain to get that going (VMware).

Thanks for your reply.

Caruso

---

### Post by overdrank on 2007-04-28
> **seetho said:**
> If it ain't broke don't fix it. 

I agree  keep with what works!:guitar:

---

### Post by Irony on 2007-04-28
You can always make a direct copy of your current installation;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

If the installation doesn't work copy your old one back. This is also a direct way of making backups and moving your installation to another partition.

---

### Post by sailor2001 on 2007-04-28
having problems with vmware in feisty, so wait a while to upgrade.......I've always found it quite easy to upgrade rather than fresh install.......but usually a new upgrade takes a few months to calm down........by the way, you can't "skip" an upgrade, the upgrade must be done one release at a time.....

---

### Post by carusoswi on 2007-04-28
Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-386/packages.bz2](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-386/packages.bz2) Sub-process bzip2 returned an error code (2)

The above is the message I get when the 6.10 to 7.04 upgrade stalls.

What is going wrong?

Thanks.

Caruso

---

### Post by carusoswi on 2007-04-28
> **sailor2001 said:**
> having problems with vmware in feisty, so wait a while to upgrade.......I've always found it quite easy to upgrade rather than fresh install.......but usually a new upgrade takes a few months to calm down........by the way, you can't "skip" an upgrade, the upgrade must be done one release at a time.....

Are you adding the "can't skip" info as a general FYI message?  I don't believe I am skipping any upgrades.

Caruso

---

### Post by vanadium on 2007-04-28
I did not have issues with an ATI Radeon Mobility X600 using the proprietary drivers, and upgrading from Edgy to Feisty. However indeed, it is good to ask yourself whether you need the upgrade. It could be better to keep a well running system for a good time, then upgrade though a fresh install.

---

### Post by carusoswi on 2007-04-28
> **vanadium said:**
> I did not have issues with an ATI Radeon Mobility X600 using the proprietary drivers, and upgrading from Edgy to Feisty. However indeed, it is good to ask yourself whether you need the upgrade. It could be better to keep a well running system for a good time, then upgrade though a fresh install.

I am game to try the update, but cannot get it to work.  It stalls.

Caruso

---

### Post by carusoswi on 2007-04-28
> **Irony said:**
> You can always make a direct copy of your current installation;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

If the installation doesn't work copy your old one back. This is also a direct way of making backups and moving your installation to another partition.

Irony:
Could you talk me through this?

sudo mkfs.ext3 /dev/sda3 (1)

sudo mkdir /mnt/usb (2)

sudo mount /dev/sda3 /mnt/usb (3)

sudo mkdir /mnt/ubuntu (4)

sudo mount /dev/hda6 /mnt/ubuntu (5)

sudo cp -ax /mnt/ubuntu/. /mnt/usb/. (6)  

mdfs - what does that stand for?  Looks like "make file system".  "/dev/sda3"  What is dev - a required directory or what.  "sda3" also a required directory or could be any name?

mkdir - this directory is named as you have it necessarily or I make up any name - usb could be something else or no?

Same for the other commands.

I would like to try it but know that the commands apply to my setup before executing them.

Also, if I use these commands, do I risk damaging data stored elsewhere on the drive?  Win data, for example?

Sorry to be so dense, but, if I knew I could easily restore 6.10 exactly as I now have it, I could just pop in the 7.10 live cd, load the new version and take a stab at getting it going from scratch.

The upgrade for me is not working.

Thanks for your informative reply.

Caruso

---

### Post by Irony on 2007-05-02
Sorry for late reply;

   1. Format device sda3 - in this case as ext3 in my external drive.
   2. Make a directory called usb in /mnt (you can make the directory anywhere you want and name it what you want).
   3. Mount device sda3 in the /mnt/usb directory - you should see in nautilus that there is a solitary lost+found folder indicating that you have formatted it.
   4. Make a directory to mount your device hda6 ubuntu partition (the one you want to back up).
   5. Mount your ubuntu partition.
   6. Copy exactly the contents of your ubuntu partition to /mnt/usb directory - note the dots in the command.

Note to get a list of your drives do;

[PHP]sudo fdisk -l[/PHP]

Thus the exact instructions of the 6 steps depend on what devices/partitions you want to mount are and what folders you want to mount them in. In the example I chose to copy the contents of hda6 to sda3.

Thus I named a folder ubuntu and mounted hda6 to it and then I named a folder usb and mounted sda3 to it.

You could just as easily do much of it graphically just right click on the Live CD desktop and choose Create a folder and give it a name - create two folders on the desktop and then mount the devices to them by going to System > Admini > Disks .... its just that in my example it is easier to write everything as command line.

---

