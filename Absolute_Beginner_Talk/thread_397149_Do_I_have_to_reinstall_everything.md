---
title: "Do I have to reinstall everything?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by zdevil26 on 2007-03-30
I am on Windows right now, and am thinking of making the switch over to Linux. First of all, how does it work? From what I have read it seems like getting Ubuntu is just like installing a program. Usually, when you install a new OS (from my experience) it wipes everything that was on the computer, unless you have a different partition or whatever. My question is, when I install Ubuntu, will I have to reinstall all my games and stuff? Or does that still stay in my C:\Program Files\ folder, and can I use programs in that folder when I have Ubuntu?

Thanks in advance! -Zach

---

### Post by rich.bradshaw on 2007-03-30
Yes, Ubuntu is an OS, so it will erase everything on your disk - if you install it.

However, the disk is a live-cd, so you can run it from a cd without installing it.

When you do want to install it, you will probably want to repartition your harddrive, to make space for Ubuntu. This will involve backing up all your files and then putting them back.

I would recommend trying out the live-cd first so you can see if you like it.

There are many tutorials about how to burn the cd so that you can boot from it on the internet try searching the wiki on this site for help.

Ubuntu (Linux in general) doesn't call your C:\ drive C:\ either, it will probably be called hda1, and the whole layout of the system is different. Try the Live-Cd. If you can't work it out your self, shipit can send you a copy for free.

---

### Post by Arby on 2007-03-30
That question requires quite a long answer to answer it properly. It might be a good idea to start by reading this page from the wiki [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows?action=show&redirect=SwitchingFromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows?action=show&redirect=SwitchingFromWindows) that gives a good introduction to the migration process.

The short answer is yes you will need to reinstall a lot of stuff. Particularly with respect to games, not all windows games will work under Linux. It could save you a lot of trouble later if you do some searching on these forums and the web in general to see what experience others have had with your games under Linux. If any of them won't run and you want to keep windows around for gaming then you might consider dual boot. More top info from the ubuntu wiki on that topic [https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28Dual%29%7C%28Boot%29](https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28Dual%29%7C%28Boot%29) Also check the Tutorials and Tips section of these forums, there are dozens of guides on this topic. 

Hope that helps. If you have more questions ask away and we'll do our best to answer.

Arby

---

### Post by openix on 2007-03-30
Basically Windows and Ubuntu are non-compatible with each other. Your Windows games will not work with Ubuntu, except if you install the WINE package but this is not perfect. File systems are different too, no c:\ drive etc.. [Linux uses mount points]("http://www.freeos.com/articles/3102/").

I would suggest a full backup of your data and [take a look at this guide]("http://www.pcmech.com/show/os/903/"). The guide makes use of a second hard drive in a machine should you have one installed so you can dual boot thus retaining your Windows OS.

Good Luck

---

### Post by girard on 2007-03-30
isn't it that the installation process of the live cd provides an option to use only the free space available on the drive to use for ubuntu? if i'm not mistaken, it will partition the drive and create space, from the free space you have, for ubuntu. so that doesn't mean you'd have to install everything that is windows.

is that right? i'm just about 70% sure.

---

### Post by thelinuxguy on 2007-03-30
> **zdevil26 said:**
> I am on Windows right now, and am thinking of making the switch over to Linux. First of all, how does it work? From what I have read it seems like getting Ubuntu is just like installing a program. Usually, when you install a new OS (from my experience) it wipes everything that was on the computer, unless you have a different partition or whatever. My question is, when I install Ubuntu, will I have to reinstall all my games and stuff? Or does that still stay in my C:\Program Files\ folder, and can I use programs in that folder when I have Ubuntu?

Thanks in advance! -Zach

While installing an OS, you can select whether you want the OS to wipe out the entire hard disk and install fresh or preserve existing data and install to a partition. So it really depends on what you want.

You can have both Ubuntu and Windows on the same hard disk in different partitions. However, you cannot run the programs that you have currently installed under Windows. You will have to install Ubuntu "equivalents" of those programs. Some Windows programs can also be run under Ubuntu using Wine, which provides an environment for running Windows programs and games under linux.

And then there is also the option of virtualization. If you don't want to keep rebooting to Windows and Ubuntu, you can install virtualization software like VMWare. You can then install a "virtual" Windows, which can be run from within Ubuntu. This may seem complicated if your are new to the idea. But it is easy once you get going.

For trying out Ubuntu, you can always opt for running it using the LiveCD which lets you experience Ubuntu without modifying anything on your hard disk. When you are ready to make the switch, you can install it to your hard disk.

The links posted above by Arby should answer any other questions that you may have.

---

### Post by rocknrolf77 on 2007-03-30
If you like playing windows games I recomend having a dual boot. Windows on one partition and linux on another. Have a look here : [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  :)

---

### Post by girard on 2007-03-30
> **openix said:**
> Basically Windows and Ubuntu are non-compatible with each other. Your Windows games will not work with Ubuntu, except if you install the WINE package but this is not perfect. File systems are different too, no c:\ drive etc.. [Linux uses mount points]("http://www.freeos.com/articles/3102/").

I would suggest a full backup of your data and [take a look at this guide]("http://www.pcmech.com/show/os/903/"). The guide makes use of a second hard drive in a machine should you have one installed so you can dual boot thus retaining your Windows OS.

Good Luck
isn't it also, that you can partition the free space you have now with windows, in such as way as to create a partition that would allow for linux and windows to "communicate" - a place where you can save files that would be accessible to both OS (the FAT32 file type).

nevertheless, backing up should be the first step... all the time.

---

### Post by Arby on 2007-03-30
> **girard said:**
> isn't it that the installation process of the live cd provides an option to use only the free space available on the drive to use for ubuntu? if i'm not mistaken, it will partition the drive and create space, from the free space you have, for ubuntu. so that doesn't mean you'd have to install everything that is windows.

is that right? i'm just about 70% sure.

Yes that's an option of you want to go the dual boot way. I would still back up your windows stuff first just in case.

---

### Post by daynah on 2007-03-30
Here's what's going to happen, sweetie.

First you're going to burn what's called an "iso" This is a special type of cd, like an image. 

Then you will first boot into your bios. Since you've installed an OS before, you probably know how to do this. I do it, on my laptop. On my desktop, I don't know how to do it, so I just press every non letter key and magically it pops up and says "What the heck are you doing you crazy?!" (not really). Then you tell your bios to boot first to your CD drive. If you have that one, remember to choose the one you're going to put that Ubuntu cd in. :)

Now reboot and really super-speed put in the ubuntu disc! Phew! That's the hardest part. Good. Now ubuntu's going to ask you what keyboard you use. This isn't installing it. This is what is called the "Live CD." It's a cd that's  living and takes over your computer.

I make really awful jokes.

Ubuntu, at this stage, literally runs off of the CD and does not touch your hard drive at all! It'll keep going and you'll get to see a ubuntu desktop and fiddle around and all that stuff. I don't think you'll get to save (where will you save it too? It doesn't touch your hard drive! :) ) but you get a little preview of what Ubuntu is like.

If you like what you see, you'll notice a little icon on the desktop that says "Install." That's where you, duh, install Ubuntu. Click on that and it'll take you through the very pretty installation. Surprisingly prettier than Window's installation (and this is supposed to be ugly Linux, whodathunkit).

Now, you don't have to clean your computer off before you do all this, or I woulda told you to way up at the top. If you want Ubuntu to be the only thing on your harddrive, Ubuntu will eat your old OS up (yum yum!) and be king of the castle. But Ubuntu also plays nicely with others and comes with a partition wizard, which is very easy. You just tell ubuntu how much to leave for the other OS, and Ubuntu will do just that, and will install itself on the free space that's left. If you're not sure how much space to do each OS, I always like around about 50% idea, unless you know you have a LOT of stuff stored on that other OS.

(PS, when you go to reboot that other OS, it's gonna kinda freak out and do a disk check. You'd freak out too if one day you woke up and suddenly you were smaller. Don't worry, after the desk check everything will be okay).

Ubuntu will install itself either on the full HD or the free space, and everything will be honky dory. If you did a dual boot (that's what it's called when you have two operating systems on the same computer), then you will have what's callled a Grub when you boot up. A grub is a sorta ugly screen (You can make it pretty though) that lets you pick between which operating system you want to boot to. Love the grub. :) The grub is good.

So whatever way you go, Ubuntu is good, and Ubuntu is easy! :) Have fun and come back if you need anymore help or advise.

---

### Post by zdevil26 on 2007-03-30
Wow, thanks guys the LiveCD sounds great! I will have to try that out.

---

