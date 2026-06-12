---
title: "Confused about manual partitioning"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zibeezibeehey on 2007-08-14
I have a strange problem and I am a complete noobie. My Windows XP crashed last week and tells me i need the Windows recovery disk to fix it. I dont own the disk so I download the ubuntu live cd and used that for the last week or so.

I went out and bought a new external hard drive to bring all my files from my computer to it, however the live cd of ubuntu doesnt let you do such a thing.

So I tried to install it but im affraid of it erasing my files. So what I want to do is be able to make sure my files are safe and I think I ave to manually partition my drives but I need step by step help.

The whole thing I want to do is install ubuntu in a small partition that wont effect my files. Then move all my files over to the external hard drive. Then completely reforat my computers hard drive and install ubuntu on the clean drive.

Here's what i have n step 4 of 7 in the installation.

/dev/hda
/dev/hda1  fat32  /media/hda1  3150mb used 1700mb
/dev/hda2  ntfs    /media/hda2   18251mb used ?
/dev/hda5  ntfs    /media/hda5    18654mb used ?

I previously had my 40gb hard drive partitioned in XP and all the files i want to keep safe i beleive are on the hda5 so i dont want it to be touched.

PLEASE PLEASE PLEASE somebody help in noobie terms, i am stressing out here, sorry for the long post.

---

### Post by armandh on 2007-08-14
IMHO the best way to recover files from a crashed XP system is take that hard drive to a good running XP computer [without anything important on it] and install it on the secondary ide line. then you will be able to transfer all your files to CD/DVD/another hdd. 

or pull that hdd, install a new one, install Ubuntu. then the same as above. except you are using ubuntu as the clean system.

---

### Post by gn2 on 2007-08-14
To guarantee safety of your files, remove the internal hard drive, fit a new one to istall Ubuntu on then put the old drive in a USB enclosure and copy the files across.

---

### Post by PCFascist on 2007-08-14
Why can't you use the LiveCD?  Are you unable to read the windows partition? Or are you unable to see the external Hard Drive when you plug it in?

---

### Post by zibeezibeehey on 2007-08-14
Yeah but i already spent a bunch of money on an external hard drive. Is there anyway that I can actually do what i mentioned before. In my head it makes sense but i dont know how these things work to well.

Cant i just install ubuntu without it wrecking my files and then move my files to the external hdd?

---

### Post by zibeezibeehey on 2007-08-14
When I use the live cd with out installing ubuntu it wont let me move stuff from my hard drive to my external hard drive. I read that its so the live cd trial doesnt mess up your computer or something.

---

### Post by zibeezibeehey on 2007-08-14
Yeah when i try to bring my files to the external hard drive using the live cd its says error you do not have permissions to write to this folder???

---

### Post by jmnormand on 2007-08-14
Two things that will help us help you are 1: can you see your data from the ubuntu live cd? and 2: can you see the usb drive?  depending on the external you bought you may be able to swap your existing drive with the one in the external and install to that.  then put the old drive in the enclosure and get your data.  if not and you really want to be sure a new drive at newegg is $60 for a lot more space than your current one.

additionally based on your drive info i can pretty much guarantee hda1 is boot, hda2 is windows and hda5 is general storage, though who knows what important stuff may be on the windows partition still...

---

### Post by zibeezibeehey on 2007-08-14
Ok 1. I can see the data from the live cd and 2. I can see the usb drive. I can open the external hard drive using the live cd but it wont allow me to move files to it.

I bought the new seagate freeagent go 120gb and it pretty solid in there I dont fee like messing with it really.

And my windows drive (hda2) I really dont care what happens to it, I always put all of the files that I want to keep on the general storage part.

So is this doable, can I instal over top of the windows drive or on a piece of the windows drive so that i can leave my sensitive files untouched until fully installed and then use the ubuntu os to move my sensitive files to the external hard drive? please say yes.

---

### Post by jmnormand on 2007-08-14
sounds like your external drive is ntfs, meaning linux cant write to it just read it.  you need to format it as ext3 or fat32, use fat32 if may want to use it on a windows machine as well, other wise use ext3.  then you should have no problem copying your files to the external.

and if you do manual partitioning when setting up ubuntu you can tell it to install to hda2 and not touch hda5.  just make sure the format option for hda5 is set to not format (this should be the default but does not hurt to double check).  though your better off transfer your data first just in case something goes wrong.

ps could also just be a permission issue try a sudo chmod 777

---

### Post by zibeezibeehey on 2007-08-14
ok ill give it a shot. oh how do i format my external hard drive to fat 32

---

### Post by jmnormand on 2007-08-14
[http://www.skullbox.net/newsda.php](http://www.skullbox.net/newsda.php) should help.  not sure if there is an easier way in live cd.  youll need to unmount then follow the info on the site to set up the drive, format and remount.

---

### Post by zibeezibeehey on 2007-08-14
Thans Ill give this a shot.

---

### Post by antoz on 2007-08-14
I would partition that external drive first and use about half as Fat 32, remember that Fat 32 only supports files up to 4 GIG so if you ever wanted to back up a whole partition on there it will not be possible.

---

### Post by zibeezibeehey on 2007-08-14
Yeah I have like 16 gigs worth of file I want to put on the external hard drive. So ts best to do that before I install ubuntu. Now how do I do that. So far ive been told that it is possible, i just have to reformat my external hard drive to fat 32 then the live cd will allow me to move my 16 gigs of files over to it. Then i an go ahead and run an install on my computer ad not worry about what gets erased during the install. Now if this sounds all ok please tell me how to do it, please.

---

### Post by Rul on 2007-08-14
Can you see your external drive with the gnome partitioner?

If you can see it then you can format it to ext3 using the gnome partitioner

---

### Post by zibeezibeehey on 2007-08-14
yeah i can se it and ive tried to use the gnome partioner to change it to fat32 but it gives me an unable to open /dev/sda unrecognised disk label error. How do i get around this?

---

### Post by zibeezibeehey on 2007-08-14
ok i tried the ext3 and it worked but for some reason the fat32 didnt, i did the exact same thing for both, weird. Any idea why?

---

### Post by zibeezibeehey on 2007-08-14
After all that it still wont allow me to move my files from one hard drive to the external hard drive using ubuntu live cd and i think its because they say that the live cd part wont alow you to mess with the hard drives. Its just a trial so you dont screw your computer up

---

### Post by antoz on 2007-08-15
I am not sure why you should not be able to move those files? maybe you need to mount
your partitions first before you can access the files.
As to creating a Fat 32 partition resize the existing external drive first then rightclick the unalocated space and create an extented partition and then format to Fat 32.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 
These are links

---

### Post by Rul on 2007-08-15
have you tried copying the files instead of moving them? maybe you don't have permission to erase the disk but you can copy its content

---

### Post by zibeezibeehey on 2007-08-15
when i tried to copy then moved over to theexternal drive therewere nopaste commands not even i edit

---

### Post by jmnormand on 2007-08-15
can you get a copy of pclinuxos live cd?  i know when i was setting up my dell 1420, which did not play well at all with ubuntu live cd, pclinuxos had no problems copying files and setting up and recognizing all the drives.   perhaps it will work better on your system.

---

