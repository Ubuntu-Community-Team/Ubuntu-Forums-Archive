---
title: "Installing ubuntu with windows"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Error47 on 2007-06-12
I am running on the live ubuntu feisty CD right now. I am trying to dual boot ubuntu with Windows XP. I clicked on the icon to install, but I have no Idea on how to resize the partition so that I can split my 120GB hard drive into two. I am using about 40 or 50 gigs in windows so I want ubuntu to get aprox 40 gigs. I am on step 4 of 7, titled prepare disk space. 

I have four options to choose from, guided - use entire disk ( I do not want to erase my windows XP)

Guided - Use the largest continuing free disk space.

and manual. 

I am a little stuck here, I want to get this running. what should I do. I tried searching for a guide or something to help me online but I can't find any help.

---

### Post by wreti on 2007-06-12
Select manual and select the size of the partition you want. Suggest defragmenting windows first.

---

### Post by trent dillman on 2007-06-12
...

---

### Post by Error47 on 2007-06-12
Thanks for the reminder for defraging. I was going to do it but totally forgot. I just got two external hard drives so everything is backed up. I am going to do that first then.

---

### Post by Error47 on 2007-06-13
wreti, I kind of need a more detailed explanation. I clicked manual, now I am in "prepare partitions" 

I have   dev/sda1/ is 120023 mb and 365000 is used. 

Say I want to create the linux partition with 45 GB. What should I do???

---

### Post by samuraiCat on 2007-06-13
Before you do anything, go through this entire tutorial: [http://www.easy-ubuntu-linux.com/dual-boot-ubuntu-guide.html](http://www.easy-ubuntu-linux.com/dual-boot-ubuntu-guide.html)

This page, in particular: [http://www.easy-ubuntu-linux.com/resize-windows-partition.html](http://www.easy-ubuntu-linux.com/resize-windows-partition.html)

---

### Post by Error47 on 2007-06-13
I don't know what is going on here, am I running a different version or something? 

I took a screen shot, it is attached to this post. Please tell me what to do from there.

Why am I seeing a completely different screen than the one from the screen shot in the link you gave me??

---

### Post by Error47 on 2007-06-13
Ok, so I thought I got it after I clicked on "edit partition" to create another one. I chose the right size that I wanted, then I went through with it. It started loading then it got the the point where it said   

"An error occurred while writing the changes to the storage devices.

The resize operation is aborted."  

What should I do now, or did I do it wrong?

---

### Post by wreti on 2007-06-13
You could try this freeware tool to resize your windows partition.
[http://www.cutepm.com/](http://www.cutepm.com/)
Then reinstall Ubuntu. When you get the point where you're asked which partition to install to, choose the "Guided - Use the largest continuing free disk space" option and the rest should fall into place. Hope this helps!

---

### Post by samuraiCat on 2007-06-13
> **Error47 said:**
> I don't know what is going on here, am I running a different version or something? 

I took a screen shot, it is attached to this post. Please tell me what to do from there.

Why am I seeing a completely different screen than the one from the screen shot in the link you gave me??

Okay, you'll notice that what you posted is "Step 4 of 6", and the screen shot in the tutorial is "Step 5 of 7." It appears you aren't there yet. It also appears that the tutorial is for an earlier distro of Ubuntu. Sorry I couldn't be more helpful. Did you go through the tutorial anyway?

---

### Post by Error47 on 2007-06-13
Why would feisty be harder to insatall? I remember installing ubuntu 6 and I had absolutley no problem dual booting. So why was I able to do this in the older version, can't I do it in 7.10 ?? I did go through most of the tutorial, but it was really about alot of other things. Does anybody have any suggestions that would help me install this? Should installing ubuntu be that hard?

---

### Post by wreti on 2007-06-13
> **Error47 said:**
> Ok, so I thought I got it after I clicked on "edit partition" to create another one. I chose the right size that I wanted, then I went through with it. It started loading then it got the the point where it said   

"An error occurred while writing the changes to the storage devices.

The resize operation is aborted."  

What should I do now, or did I do it wrong?

What size partition were you trying to create at this step? Also (hate to beat a dead horse) you may need to defrag a couple more times in windows.

Bottom line, if you're having this much trouble partitioning via the Ubuntu install, you should really try a different route such as partitioning through XP with a third party program. It may save some time and frustration. Try a search for "free partition manager, XP".:)

---

### Post by samuraiCat on 2007-06-13
> **Error47 said:**
> Why would feisty be harder to insatall? I remember installing ubuntu 6 and I had absolutley no problem dual booting. So why was I able to do this in the older version, can't I do it in 7.10 ?? I did go through most of the tutorial, but it was really about alot of other things. Does anybody have any suggestions that would help me install this? Should installing ubuntu be that hard?

Actually, I read that tutorial very carefully, and it all made sense to me. It claims to be up to date with Fiesty. Since I haven't actually done it yet, I'm not quite an authority. When my new system is put together, I may be in the same spot as you when I attempt to partition!

---

### Post by Error47 on 2007-06-13
Instead of restarting into windows and looking for a partitioning program, I tried to use the program that comes with ubuntu, I think it's called gparted. The information it is giving me is wrong. First of all it says that it is formated in ext3, it also says that the capacity is 111Gb and I only used 1 gb of it, when in Windows I have it about 30 gb used.

---

### Post by Error47 on 2007-06-13
Wow... What a disaster. For some reason somehow, windows got erased, more like my whole hard drive got formatted. I don't know what I did wrong here. I didn't have any of these problems with the older version of ubuntu, why is it doing this with the newer version? I lost so much stuff that took me alot of time to get. 

So now I have to start all over. I need Windows so I am guessing that I have to install windows again first, then try attempting to install ubuntu all over again.  Can anyone tell me why feisty is harder to install than the previous version?

Any suggestions on what I should do now?

oh and is it possible to install ubuntu now, and install windows later?

---

### Post by Tyke91 on 2007-06-13
try downloading the gparted live disk iso ( [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828) ) and burn it to a cd. I've found that gparted works differently on its own than it does on the ubuntu cd.


steps for installation RIGHT from the CD should be easy

get to the partiton editing step

select manual

select your windows hard drive, shrink it down to however much you want.

select the free space created and check the little format box next to it, make it ext2 or 3 (preferably 3)

hit go :)



if you need to partition first, then just use the gparted live disk to create free space, then select guided with largest continuous free space


EDIT:        GAH! sorry man... just saw your last post... at this point, all you can do is re install windows and then ubuntu after it (if you are still interested)

it's a bad idea to install windows second because it will erase your grub menu (the thing that lets you switch between operating systems on reboot) and then you will have to go through the long process of getting it back :(

---

### Post by wreti on 2007-06-13
If you go the route of installing XP first (recommend, otherwise XP will install it's MBR over GRUB) specify the partition size you want during the installation process. This will ensure a partion left over for your Ubuntu installation. Then once you get to the partition selection screen in the Ubuntu install, select "Guided - Use the largest continuing free disk space".

---

### Post by Error47 on 2007-06-13
Ok, I re-installed windows, I downloaded partition magic, and split my windows 120 GB partition into two. One NTFS one ext3. I go back to the ubuntu live cd, and try to install. This time I got a different screen (Attached). 

I don't want to mess anything up again. I was planning on choosing the option you guys told me about - Guided - use largest continuous disk space, but I do not see that option any more.

---

### Post by Error47 on 2007-06-14
I am trying to install right now, what should I do?

---

### Post by bren on 2007-06-14
edit - oops wrong advice

since you already have 2 partitions choose manual

bren

---

### Post by OldTimeTech on 2007-06-14
I personally would go with manual, because it then shows you which is your ntfs and which is still free and also shows you your swap file, you did do a swap file right

---

### Post by gn2 on 2007-06-14
By far the easiest way to create a dual-boot Windows + Ubuntu set-up on one hard drive (from scratch) is to install Windows first.

During the install, delete ALL partitions on the drive (presuming everything's been backed up...?)

Then create the partition to install Windows to, and specify what size you want it to be.

Leave unallocated space at the end of the drive.

Install Windows to it's partition.

Next, install Ubuntu, and select "Largest continuous free space" to install to.

Ubuntu will create it's own partitions and install.

You an always change things later, but I find this is the easiest way to get started.

---

### Post by Error47 on 2007-06-14
Ok, I am still a little confused. I have attached a new screen shot of what the manual screen looks like. I do not know what to do.

---

### Post by por100pre1 on 2007-06-14
I think for you the best option is to go guided then chose the Largest continuous free space option

---

### Post by Error47 on 2007-06-14
For some reason I don't have that option anymore. The menu for the setup keeps changing.
Here are my options before manual. (attached)

---

### Post by por100pre1 on 2007-06-14
first stop the installation then delete the ext3 partition with Gparted

---

### Post by Error47 on 2007-06-14
How do I do that? I have the option to delete the ntfs partition but I very well need that. Next to the other partition is a little lock sign, and I can't delete the partition. But first someone told me to split my drives and create an ext3 partition. Now I am hearing a different story?

---

### Post by por100pre1 on 2007-06-14
That beacuse some users like to edit their partition before installing; others, like me, like it simple: let the installer do the job. Now check on the desktop if there's a disk in use and right-click and dismount volume

---

