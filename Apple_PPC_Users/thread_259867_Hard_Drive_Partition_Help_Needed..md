---
title: "Hard Drive Partition Help Needed."
date: 2006-09-18
forum: Apple PPC Users
---

### Post by kgregc on 2006-09-18
I'm a new Ubuntu user, running it on a Core 2 Duo Intel powered iMac with a 160Gb HD. I am using Parallels, and have a VM to install Ubuntu.

I started with a 20Gb HD partition, and somehow got the partitions set as shown. (only the Partition 1 and the Swap Partition initially). Partition 1 is 18.81Gb and the Swap partition is only 729Mb... Partition 1 is also of the FileSystem "Extended 3 (ext3). I'm not sure how this FileSystem, or the small size of the Swap Partition happened...maybe just new and hit the wrong keys... 

Ubuntu loaded fine, and works well. I have Internet, mail and other programs work. My problem is the size/structure of the partitions.

[[IMG]http://img.photobucket.com/albums/v165/kgregc/Parallels/th_FinderScreenSnapz002.jpg[/IMG]](http://img.photobucket.com/albums/v165/kgregc/Parallels/FinderScreenSnapz002.jpg)

[[IMG]http://img.photobucket.com/albums/v165/kgregc/Parallels/th_FinderScreenSnapz003.jpg[/IMG]](http://img.photobucket.com/albums/v165/kgregc/Parallels/FinderScreenSnapz003.jpg)

I wanted to enlarge the Ubuntu partition, so using Parallels Tools, I enlarged the .hdd to 40Gb...but it seems to have just created a new partition of 20Gb, "unpartitioned" Free Space!!! :confused: 

[[IMG]http://img.photobucket.com/albums/v165/kgregc/Parallels/th_ParallelsDesktopScreenSnapz001-3.jpg[/IMG]](http://img.photobucket.com/albums/v165/kgregc/Parallels/ParallelsDesktopScreenSnapz001-3.jpg)

So here is what I think I need to do.  Somehow, get the 20Gb free space created with Tools, to be part of Partition 1. Confirm if Extended 3 is correct File System, and if not change it. Expand the Swap Partition to at lease 2Gb, taking away some of Partition in necessary. (I thought I read that was what it should be...#-o )

Any help in correcting my mistakes, and hopefully without having to start all over from scratch, would be very much appreciated. Please just remember, I am a reeeaaal newbie a Linux.

Thanks,

Greg

---

### Post by aysiu on 2006-09-18
I don't know what's going on, but it appears your swap partition is wedged between the Ubuntu partition and the empty space.

One easy way to "solve" this would be to format the 20 GB of free space as Ext3 and create a separate /documents partition you can use as storage space.

The first 20 GB should be plenty for all your settings and programs (in fact, settings and programs probably won't get above 4 GB).

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) might help.

---

### Post by kgregc on 2006-09-18
Thanks for the reply...the small Swap file was that way before I expanded the .hdd from 20 to 40Gb (it was part of the initial 20, and somehow I just made it too small to begin with.) How do I make the Swap file bigger?

Is the Extended 3 File System OK? Is that what it should be?

How would I go about formating the second 20Gb partition, and how do I direct documents and things to it instead of Partition 1?

Thanks,

Greg

---

### Post by aysiu on 2006-09-18
You can use GParted to create an Ext3 filesystem out of it: ```
sudo aptitude update
sudo aptitude install gparted
gksudo gparted
``` Right-click the empty space and create a new partition out of it.

After that, refer to this link for how to mount it:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by kgregc on 2006-09-18
Thanks for the reply, but please understand I am brand new to this... I Googled gpated and downloaded it in Ubuntu.

This is what I have:
[[IMG]http://img.photobucket.com/albums/v165/kgregc/Parallels/th_FinderScreenSnapz001-1.jpg[/IMG]](http://img.photobucket.com/albums/v165/kgregc/Parallels/FinderScreenSnapz001-1.jpg)

Clicking on the icon "GParted" brings up an error message:There was an error launching the application Details: Failed o execute child process "gparted" (No such file or directory).

I'm kinda lost as to what to do to get Gparted installed... Any suggestions?

---

### Post by kgregc on 2006-09-18
Wait... ! I found Synaptic and was able to download Gparted and the other tools needed. I'll try the next steps you outlined..

Tnx.

Greg

---

### Post by kgregc on 2006-09-18
OK, I have created the partition, and put a space between it and the Swap file...now I can't seem to get it mounted. Where do I type the "code" shown on the page you linked? 

[[IMG]http://img.photobucket.com/albums/v165/kgregc/Parallels/th_FinderScreenSnapz002-1.jpg[/IMG]](http://img.photobucket.com/albums/v165/kgregc/Parallels/FinderScreenSnapz002-1.jpg)


Tnx.

---

### Post by aysiu on 2006-09-18
> **kgregc said:**
> Where do I type the "code" shown on the page you linked? [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by kgregc on 2006-09-18
aysui,

Thank you! I have it mounted now. =D> 

Now, is there a way to expand the Swap file from 729Mb to about 2Gb...the size I believe it should be, without destroying anything stored there?

Next, how do I direct things to hda3 (storage) while working within Ubuntu?

I really appreciate your help and patience with me...

Greg

---

### Post by kgregc on 2006-09-18
Double post

---

### Post by aysiu on 2006-09-18
As far as I can tell, based on what I've read and experienced, there's never any reason to have a 2 GB swap partition.

Swap is generally twice the RAM, but if you have 1 GB, you shouldn't ever need swap.

---

### Post by kgregc on 2006-09-18
Ok, thank you for all your help. 

Only one last question...how do I direct things to hda3, Storage, as opposed to it going into Partition 1. Also, what type of things should I put there instead of them going into Partition 1.

Tnx

---

### Post by aysiu on 2006-09-18
Well, you're basically going to create a shortcut to /dev/hda3

Right now it's mounted somewhere, right? /data or /storage or /documents... something like that?

Well, you can just go into the /data folder and put stuff there. Or, if you want it to show up in your home directory, you could do ```
ln -s /data /home/kgregc/data
```

---

### Post by kgregc on 2006-09-18
Yes, it's "storage"...right?

[[IMG]http://img.photobucket.com/albums/v165/kgregc/Parallels/th_FinderScreenSnapz001-2.jpg[/IMG]](http://img.photobucket.com/albums/v165/kgregc/Parallels/FinderScreenSnapz001-2.jpg)


By typing "ln -s /data /home/kgregc/data" in the Terminal, will this direct all data etc to dev/hda3 (/storage), and no longer put anything in dev/hda1? (/dev/.static/dev)?

Tnx

---

### Post by aysiu on 2006-09-18
I guess I'm not sure what you mean by "all data."

This would be for putting pictures or music or documents... or whatever you need to store.

For programs and settings, your first 20 GB partition will be more than sufficient.

---

### Post by kgregc on 2006-09-18
Alright, I just created a letter in OpenOffice word processor (I assume the program, Open Office, is in hda1). When I select save, my options are the Desktop, File System, or a folder with my login name. I don't see where I can choose hda1 or hda3... (I have not typed in the code you posted yet). 

Tnx

---

### Post by aysiu on 2006-09-18
If you link it to within your /home folder, you can see it within that folder: ```
ln -s /storage /home/kgregc/storage
```

Alternatively, you can actually make the entire partition your home folder: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by kgregc on 2006-09-18
"ln -s /storage /home/kgregc/storage" gives the following: 

bash: In: command not found

---

### Post by aysiu on 2006-09-18
You seem to be typing capital *i* instead of lower-case *L*.

Also, I just said */home/kgregc/storage* because your username on these forums is *kgregc*. You should substitute in your actual computer username (*greg* or *bigkahuna* or whatever you use to log into your Ubuntu machine).

---

### Post by kgregc on 2006-09-18
hmmm I typed the code in, using a lower case "L", and got no error messages, just a return to the prompt.. I assume that means the command "took".

Next, I created a document in OO, selected to save it, and got the 3 options again. Chose "kgregc" and then looked to see where it went.

[[IMG]http://img.photobucket.com/albums/v165/kgregc/Parallels/th_ParallelsDesktopScreenSnapz001-5.jpg[/IMG]](http://img.photobucket.com/albums/v165/kgregc/Parallels/ParallelsDesktopScreenSnapz001-5.jpg)

Seems to not be in storage... (when you open storage, all that's there is a folder called "lost+found)

---

### Post by aysiu on 2006-09-18
The way we mounted it, it's *inside* kgregc. It isn't kgregc

When I say things like /home/kgregc/storage, that means that / is the top-level directory. 
Within /, there's a folder called home. 
Within /home, there's a folder called kgregc.
Within /home/kgregc, there's a folder called storage.

It's sort of like how in Windows, C:\Documents and Settings\kgregc\Application Data means C:\ is the top-level directory.
Within that, there's a folder called Documents and Settings
Within that, there's a folder called kgregc
Within that, there's a folder called Application Data

If you want the second partition to be /home/kgregc, you'll have to follow this tutorial:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Otherwise, when you save an OOo document, just double-click kgregc, and you should see storage within that.

---

### Post by kgregc on 2006-09-18
aysui,

You have been super helpful...thank you! =D> 

I would have never been able to do it without our help. How do you learn all this stuff??? :confused: :lol:  Is there a book you could recommend? (I think there might be some info on the ubuntu home page too), but from your experience.....?

BTW, when saving a letter in OO, I had to select "Browse for other folders" to bring up storage, but it worked fine then. 

I come from the Mac world, so all the "/" and "\" things are not that familiar...we just drill down by icon. This is an education for sure!!!:roll: 

Again, thanks.

Greg

---

### Post by aysiu on 2006-09-18
If you're coming from Mac OS X, it's actually *very* similar. Apple has just hidden the directory structure from you (something I think Ubuntu should adopt as well).

In Mac OS X, launch terminal.app from Applications and you'll see you start in /Users/kgregc. All the same *nix commands work, and the structure is almost exactly the same. You have a /boot and a /usr and a /lib. All your settings are stored in /Users/kgregc. The only differences are that Mac OS X uses /Users instead of /home and /Volumes instead of /media.

The forward slashes are for *nix, indicating a path to a subdirectory: /home/kgregc/storage/document1.odt

The backslashes are for Windows, indicating a path to a subdirectory: C:\Documents and Settings\kgregc\My Documents\document1.doc

A book to recommend...? Well, believe it or not, the book that first made Linux accessible to me was one called *Point-and-Click Linux*, which is about Mepis, not Ubuntu. They two distributions (Mepis and Ubuntu) are pretty similar.

I'd also recommend *Desktop Linux Garage* for a general overview of getting familiar with desktop Linux.

There's also a book about Ubuntu... something about *novice to professional*, and that's good for novices.

---

