---
title: "home in another partition"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by bashhelp on 2005-11-30
I heard that it is a good idea to put create my home directory in another partition.  So when I reformat or something happens to root, my files would still be okay since its on another partition.

I am about to do a clean installation.  During the installation I would be asked if I want to do a manual partition.  How would the partitions look like if I want the above done?

---

### Post by aysiu on 2005-11-30
How big is your hard drive?
Are you dual-booting with Windows?

---

### Post by bashhelp on 2005-11-30
13 GB.  Not dual booting.

---

### Post by gord on 2005-11-30
i do that myself, i have it set up like

hda1 - ntfs (windows)
hda2 - reiserfs (/home)
hda3 - extended
    hda6 - reiserfs (root)
    hda5 - linux-swap


you might be able to put the /home partition in the extended partiton, but i didn't bother trying it. 

if your not dual booting you can just not bother with the ntfs part. the installer is pritty easy with that stuff though so you shouldn't have too many problems..

---

### Post by AndyCooll on 2005-11-30
When it comes to the manual partition section, choose (as you say) "manually partition". 

Decide what size you want you partitions before you start (and remember to include space for a swap file which it is recommended should be about twice the size of your RAM).

First delete your current partitions, and then create your new ones. The partitioning tool will guide you through it.

Essentially, you create a partition (say 8gb), part of the choice should include choosing the mount point. There are a selection of comon ones used. Choose "/", i.e. root. Make it primary partition and the default file structure is ext3. Then say you have finished completing that partition. 

Now set up a second partition (say 4gb) and repeat the process but select /home for your mount point. This can be either a primary or logical partition, and either at the beginning or the end.

Now with the remainder create a swap file (say 1gb). I can't remember exactly how you create it, but essentially you select the section where it includes ext2, ext3 etc. One of those choices is swap file.

When you're done say create them!

:cool:

---

### Post by bashhelp on 2005-11-30
Okay, so it will be something like this:

#1 2.75 GB for / (root)
#2 10 GB for /home
#5 250 MB for swap

But how do I tell the installation to install the /home in #2?  Because by default it will install it into #1.

Also, what is the difference between logical and primary?  I would like to know which is best for my /home partition.

---

### Post by aysiu on 2005-11-30
2.75 seems a bit skimpy for /
I use 4.5 GB of my / partition, and I don't have *that* many programs installed (I don't have a minimal install either, though).

I'd do something more like

5 GB **/**
7.75 GB **/home**
the rest **swap**

---

### Post by bashhelp on 2005-11-30
Why is root taking up so much space (5 GB)?  The average distro installed is more or less 2 GB.  I am not going to install mass programmes.  In fact, I will be stripping some programmes that comes installed since many stuff there is useless to me.

Questions from my previous post still needs answering.  If someone could help, please do.

---

### Post by gord on 2005-11-30
a computer can only have 4 (i think) primary partition, a logical partition is a primary partition that you can put more partitions inside, i don't think there is a realisic limit to how many partitions you can put inside a logical partition. 

and its good to give root a nice ammount of space, if i were you id look into upgrading your harddrive though, memory can be quite cheep these days.

---

### Post by bashhelp on 2005-11-30
I don't want or need a larger HDD.  I am fine with the 13GB I have.  It's just there to surf the Net and do some newbie programming.

So it should go something like this?:

#1 root (primary)
#2 home (logical)
#5 swap (logical)

That correct?

The question of how to get the installation to install /home in #2 still needs answering.  If someone has done this before or know about it, please answer.

---

### Post by gord on 2005-11-30
i don't really see the problem your having there, you should be able to set up home wherever you want.

---

### Post by bashhelp on 2005-11-30
Okay, let me be more clear.

The instation will install everything into one partition.  I would like to have the /home in another partition.  How do I get the installation to install /home in another partition?

If I just created 1 primary (#1), 1 logical (#2), 1 swap (#5), then the installation will just install everything (including /home) into #1, and I would have an empty #2.

How do I get the /home to #2?  If I installed it normally, then I would have the above.  If I just simply moved /home into another partition.  The system isn't aware of what I did or wanted to do; it will just think the /home has been deleted since its missing.

So all those files that are automatically created in /home when I customise something, it have problems.  That is why I need to know how I can tell the installation to create /home in another partition so it is recognised by the computer.

---

### Post by aysiu on 2005-11-30
I echo gord on this: put /home wherever you want. It can be #1, #2, or #3.

---

### Post by gord on 2005-11-30
instead of just letting the ubuntu installer handle everything, choose to modify the partition table yourself, then you can create your own partitions wherever you want, including your home partition. i think your gonna be formating the whole drive yes? so it can't hurt to have a little mess around, its a good way of understanding :)

---

### Post by super on 2005-11-30
linux can't install itself to '/home'. the installation will always be to '/' (thats why it's called 'root')  '/home' is a subdirectory of '/' (root)

the way you have your patitions setup is fine. but if i were installing, i would enlarge '/' by at least 1gb.

all your user files will be kept in '/home' so if you reformat you will not lose your data.

---

### Post by harisund on 2005-11-30
Ok.. here is a quick run down on partitions.. 

A computer hard disk can have only 4 partitions, called *primary partitions*. Linux numbers them hda1 through hda4 (the a part comes from the hard disk number. For example, if you were to, let's say, buy another IDE hard disk and attach that, it would become hdb. Else, your CD ROM drive is most likely to be hdb.. you get the picture, right? :smile: )

This restriction of only 4 partitions comes from the way the master boot record is structured and so on.. so let's not get into that.. 

Here comes the concept of *extended partitions.* Think of primary partitions  as boxes which can not be further divided, and extended partitions as boxes that hold tinier boxes in them. 

So an extended partition is made when you want more than 4 partitions. Once you make an extended partition, you then have to go about creating *logical partitions* inside that, which are the tinier boxes I mentioned earlier. Linux numbers these logical partitions as hda5 and beyond, hence you will not see hda2, hda3 and hda4 if you have one primary partition and rest all are logical. 

Note: A logical partition will never have a number of hda1 through hda4. All logical partitions always start from hda5 only !

I too have a 13Gb harddisk. (Was your computer bought from ebay, by any chance ?? ;-)

Ubuntu takes up 5Gb, you say? That's surprising.. 

Anyway, here is what I did.. 

3Gb - hda1 - Primary partition - mount point /
9.7 Gb- hda5  - Extended partition - mount point /home
0.3 Gb - hda6 - Extended partition - Use as Swap.. 

When you come to the partitioning portion of the installation, opt for the manual partition.

Then go ahead and say create new partition, call it primary, allocate 3gb for it, and there will be certain interesting options ... 
1. Mount point. Choose this and select /. This says that / (the main file system) will be installed in this drive. 
2. Format. here you can choose whether you want to format the partition (if so, you can select your file system here, such as ext3, reiser, etc) or whether you don't want to format it at all (you would do this for your /home). You can also say use as swap here. 

Then create your swap and home in the remaining space. If you are going to have only the above 3 mentioned partitions, I would suggest not bothering with extended / logical partitions, since you can have upto 4 primary partitions anyway. 

Hope this helps. 

Regards, Hari

---

### Post by bashhelp on 2005-11-30
To Super:

I have no idea how did you get the idea that I am trying to install Linux into /home.

I want all the files and directories that is suppose to install in root to be in root (/).

I would like home to be installed elsewhere; in a seperate partition.

The problem is: How do I get the OS to understand that I would like my home to be in a seperate partition.  If home missing from root is not possible, how do I link it together?  In otherwords, the real files and directory will be in #2, but a link to home will be in substituted in #1 (root).

> all your user files will be kept in '/home' so if you reformat you will not lose your data.
I have no idea what you are trying to say here.  Reformations erases all data.  I have reformated over distros of the same name, and my old data is never kept.

This is why I want my home to be in a seperate partition, so I don't have to keep backing it up on CDs when I do new installation.  Some people have done this, and I would like to know how they did it.

---

### Post by harisund on 2005-11-30
I hope my previous (lengthy!) post was clear.. 

anyway, you need not be worried about linking your home partition along with the rest of the file system.. Linux does it for your.. For example,if you ask it to mount /home in a logical partition (say hda5) then during boot up it will automatically execute the following command: 

mount /dev/hda5 /home 

Then you can reformat your primary partition (the hda1, on which / is installed) as many times as you want without the need to touch the data on logical partition (the hda5, on which /home is mounted) ..

---

### Post by gord on 2005-11-30
using the installer, when you set up a linux partition (ext3, reisorfs n the like) it will ask you where you want it to be mounted, you jsut have to select home. it will automatically set it all up for you.

---

### Post by aysiu on 2005-11-30
When you reinstall, you should pick the "Manually Edit Partition Table" option.

For every partition (in your case, just / and /home), you get to decide how the Ubuntu installer will handle it.

So for **/**, you'll choose to **Use as Ext3**, format **Format**, and mount **/**

For **/home**, you'll choose to **Use as Ext3**, format **Do not Format**, and mount **/home**

---

### Post by Qrk on 2005-11-30
You can do that in the ubuntu installer. Go to custom partitioning, make two partitions, and tell the installer to use one as /, and the other as /home. It doesn't matter to ubuntu where /home is. 

Myself, I like to keep my /home on the same partition as root. I have 

/ 10 GB, (including /home)
/home/user/documents 130 GB 

Because when you install a new distro and ask it to use the /home from a previous one, it can have a few problems. I also like to start fresh at each dist-upgrade.

---

### Post by bashhelp on 2005-11-30
Okay, I am very thankful everyone is trying to help.  But I am getting confused here...

Okay, during a clean installation.  After hardware detection, it would be in the **!! Partition disks** screen.

The selections are:

Configure software RAID
Configure the Logical Volume Manager
Guided partitioning
Help on partitioning

I choose Guided partitioning.  Then it gives me 3 options:

Erase entire disk
Erase entire disk and use LVM
Manually edit partition table

I picked the first one; Erase entire disk.

Then it gives me a default partition list:
```

#1 primary   XX.X GB * :) ext3   /
#5 logical  XXX.X MB   :) swap   swap

```
Okay, here is where I don't know what to do.  Along with the funny symbols.  Where the "*" is, it is not suppose to be an *, but a broken arrow.  I have no idea what that broken arrow means (boot?).  And what the happy face is suppose to mean.

What do I do from here?  Or just tell me how the list is suppose to look if I want to to do what I wanted, and I will try to figure how to get it to look like that.

---

### Post by harisund on 2005-11-30
First, do not choose "Erase entire disk." Instead choose "Manually edit partition table." 

Do know more about the symbols, I would suggest reading the guide. When you go into "Manually Edit Partition Table" you should be able to see the guide option.

There you can understand the symbols. Basically, if you are formatting then you will see one kind of a smiling face, and if you are not formatting, you will see another kind of smiling face. 

And I think the boot partition has an arrow (also called the active partition).

Everything is intuitive. Check it out and post back for more help. 

Hari

---

### Post by firenurse4 on 2005-11-30
[QUOTE=bashhelp]
The selections are:

Configure software RAID
Configure the Logical Volume Manager
Guided partitioning
Help on partitioning

I choose Guided partitioning.  Then it gives me 3 options:

Erase entire disk
Erase entire disk and use LVM
Manually edit partition table

I picked the first one; Erase entire disk.

[/QUOTE]
Instead of picking erase entire disk, use the Manually edit partion table option.  After you select that, you can set up your three partitions.

**harisund**--Looks like we were on the keyboard at the same time.

---

### Post by bashhelp on 2005-11-30
I am not getting what you guys are trying to tell me.  This option:

Manually edit partition table

Leads to this menu:

Configure software RAID
Configure the Logical Volume Manager
Guided partitioning
Help on partitioning

From where, where do I go?  If Guided partition, it will just take me back where I started, which is this menu:

Erase entire disk
Erase entire disk and use LVM
Manually edit partition table

In other words, **Guided partitioning** and **Manually edit this partition table** takes me in circles.

---

### Post by harisund on 2005-11-30
Hmm... The menu you are seeing is correct 

Configure software RAID
Configure the Logical Volume Manager
Guided partitioning
Help on partitioning

I would suggest you first choose the "Help on partitioning" part and read it. In other words, RTFM !!! Just kidding... 

Anyway, once you read that, you should be (hopefully atleast) having a general idea of what you need to do. 

Right below the 4 options that you listed, you will see the various partitions on your hard disk. 

Under that, there will be the option of create partitions etc. 

See if you are able to figure it out. If you can't, I will take some photographs and post it somewhere you can see. But that will have to wait, since I am at school right now and I will have to go home and take the photographs.

---

### Post by bashhelp on 2005-12-01
I have read it.  And it says:

> Select a device to remove all partitions in it and create a new empty partition table.

But you guys are tell me not to erase the entire disk and choose Manually edit partition table, which takes me back to the beginning.

So now I am stuck in the partition menu.  What is going on here!?

---

### Post by firenurse4 on 2005-12-01
Ok, I found the the link I was looking for.  It has good instructions for doing just what you are looking to do complete with screenshots.

[Create New Partitions to add Ubuntu to an Existing Windows ME Machine]("http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsme.html")

There is also another guide if your windows box is NTFS as well.  I hope that this is more helpful for you.

---

### Post by bashhelp on 2005-12-01
To firenurse4:

HUH!!!?  :huh: x100

Why are you giving me instructions on how to partition a HDD with an existing Windows OS?

I did **not** say I want to keep Windows.
I did **not** say I even had Windows installed.
I did **not** say I plan to install Windows.

So where did you get the Windows from?

In fact, I was very clear in the beginning.  Starting with Post 1.

> I am about to do a **clean** installation.
[http://ubuntuforums.org/showpost.php?p=533884&postcount=1](http://ubuntuforums.org/showpost.php?p=533884&postcount=1)

Then Aysium asked:
> Are you dual-booting with Windows?
[http://ubuntuforums.org/showpost.php?p=533901&postcount=2](http://ubuntuforums.org/showpost.php?p=533901&postcount=2)

Which I replied:
> 13 GB. **Not** dual booting.
[http://ubuntuforums.org/showpost.php?p=533971&postcount=3](http://ubuntuforums.org/showpost.php?p=533971&postcount=3)

If I am not dual-booting, that means I am not having 2 OS/distros.  Meaning the one I am about to install is the only one.

So where did you get the idea that I have Windows installed or planning to install and planning to dual boot with Linux?

Are you other guys thinking the same thing as firenurse4?  Because I am not.  I thought I was very clear on what I wanted to do.

Don't tell me in the last 3 pages, I have been given wrong directions.

---

### Post by firenurse4 on 2005-12-01
[QUOTE=bashhelp]
To firenurse4:

HUH!!!?  :huh: x100

Why are you giving me instructions on how to partition a HDD with an existing Windows OS?

I did **not** say I want to keep Windows.
I did **not** say I even had Windows installed.
I did **not** say I plan to install Windows.

So where did you get the Windows from?

In fact, I was very clear in the beginning.  Starting with Post 1.
[/QUOTE]

If you read the link and the screenshots, you will find out how to resize your existing partition. I doesn't mater if you are dual booting or not.

[QUOTE=bashhelp]
#1 primary   XX.X GB * :) ext3   /
#5 logical  XXX.X MB   :) swap   swap
[/QUOTE]

Based on this I am assuming you want to resize the the #1 partition.  Following the guide I linked to you would scrool down to the line 
> 
#1 primary xx.x GB* :) ext 3  /

And press enter.  From there it will give you the option to resize the space and give you a non numbered partition with the available free space.  Scroll down to that and press enter an you will be able to set that partition up.

---

### Post by aysiu on 2005-12-01
[QUOTE=bashhelp]
**Guided partitioning** and **Manually edit this partition table** takes me in circles.[/QUOTE] The only time I've seen this happen is when I ran the install CD off of Qemu inside of Gnome.

It probably means the partitioner can't even see your hard drive or isn't recognizing it correctly. Unfortunately, I don't know what the fix for this is.

---

### Post by bashhelp on 2005-12-01
Thanks for the guide, but it was too confusing for me since I wasn't doing the same thing in it.

So I played around and got this.  If anyone know how to partition well would please tell me if I did it right?  Here are the detailed partitions I made:
```

#1
Use as:         ReiserFS journaling file system
Mount point:    /
Mount options:  defaults
Label:          /
Bootable Flag:  on
Size:           3.0 GB
-----------------------
#3
Use as:         ReiserFS journaling file system
Mount point:    /home
Mount options:  defaults
Label:          /home
Bootable flag:  off
Size:           9.75 GB
-----------------------
#5
Use as:         swap area
Bootable Flag:  off
Size:           250.0 MB

```
Here is the outline:
```

#1 primary    3.0 GB * :) reiserfs  /
#3 primary   9.75 GB   :) reiserfs  /home
#5 logical  255.0 MB   :) swap      swap

```
It's my first time doing this.  Please let me know if it is okay.  If not, let me know what changes I need to make.

I don't know why it goes from #1 to #3 instead of #2.  But at this point, after spending 3 hours on it, I just want it to work.

---

### Post by super on 2005-12-01
those partitions look totally fine!
the numbering of the partitions doesn't matter at all.

sorry if i misunderstood you earlier.
i think aysiu was right. it sounds like your partitioner menu system was screwing up.

---

### Post by SickTwist on 2005-12-01
[QUOTE=bashhelp]Thanks for the guide, but it was too confusing for me since I wasn't doing the same thing in it.

So I played around and got this.  If anyone know how to partition well would please tell me if I did it right?  Here are the detailed partitions I made:
```

#1
Use as:         ReiserFS journaling file system
Mount point:    /
Mount options:  defaults
Label:          /
Bootable Flag:  on
Size:           3.0 GB
-----------------------
#3
Use as:         ReiserFS journaling file system
Mount point:    /home
Mount options:  defaults
Label:          /home
Bootable flag:  off
Size:           9.75 GB
-----------------------
#5
Use as:         swap area
Bootable Flag:  off
Size:           250.0 MB

```
Here is the outline:
```

#1 primary    3.0 GB * :) reiserfs  /
#3 primary   9.75 GB   :) reiserfs  /home
#5 logical  255.0 MB   :) swap      swap

```
It's my first time doing this.  Please let me know if it is okay.  If not, let me know what changes I need to make.

I don't know why it goes from #1 to #3 instead of #2.  But at this point, after spending 3 hours on it, I just want it to work.[/QUOTE]

That looks perfect and 3 GB sounds like an excellent size based on your expected usage that you expressed earlier. When one selects a mount point (like you did) during the partitioning stage of the installer, the installer will automatically put the files on the appropriate partition during the rest of the installation.

For example, if you were to create separate partitions for /usr, /var, and /tmp, as long as you set the moint points (/usr, /var, /tmp) for these partitions, the rest of the installation will put the correct files on each partition. When you reboot, everything will run seamlessly and you will not even realize that the system is spread across separate partitions. The trick is just to make sure that each partition is large enough to hold the data that will be stored there and in all of that mount point's subdirectories (unless of course they are also moint points).

For future reference, when you come to the partition stage of the installer and you see the existing partion table displayed:

[B]/dev/hda
#1 primary    3.0 GB * :) reiserfs  /
#3 primary   9.75 GB   :) reiserfs  /home
#5 logical  255.0 MB   :) swap      swap
[/B]

If you select (highlight then press Enter) the hardware device that the partitions are on ( /dev/hda in this example) then all of the partitions will be removed at once so that you may start fresh.

Otherwise you can select and remove the partitions one-by-one. (Select a partition, the next screen that comes up will give you an option to remove it).

Another good thing to note: None of these actions are written to the disk until after the confirmation screen which appears after you are done partitioning. Only if you accept what you see on the confirmation screen will the actual changes be written to the disk.

Regarding the little icons in the partition utility: The little zig-zag arrow indicates that the boot flag has been set on a primary partition. Your BIOS will boot whichever partition has the flag set on it. There are two smiley faces: black and white. I *think* that one means a partition is getting formatted and the other means that the data on a partition is being used (without formatting). Don't ask me which is which. :)

The partition numbers are assigned as follows: 1-4 are reserved for primary and extended partitions. 5 and up are for logical partitions (which are inside the extended partition). These numbers are appended to the device file in /dev. So in the example above, you would see the following files for your HDD in the /dev directory:

hda
hda1
hda3
hda5

I hope that you do not feel bad about your partioning...adventure. The partition utility that is part of the installer has *severe* usability issues and it is *not* intuitive. Hopefully this will be less of an issue in future releases when the graphical installer is finished. I've heard that its partitioning section will be based on gparted--that would be swell :)

If you need me to clarify anything that I've mentioned here just ask.

---

