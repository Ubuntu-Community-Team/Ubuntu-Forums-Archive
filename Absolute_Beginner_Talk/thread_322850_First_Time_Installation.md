---
title: "First Time Installation"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Ozysearcher on 2006-12-21
I was impressed with the Live CD enough to try and install. Unfortunately the hype about Ubuntu being easy was NOT true.

After using Windows for years I am familiar with words like: "install" but "mount?" I know a rider mounts a horse, but computers?

I searched these forums. Found similar questions to those I have but the answers given were useless. I tried them and they didn't work so they were useless.

The install program offers to partition automatically but I (now) have 4 partitions. Do not want to format over my existing data. I had one partition ready for Ubuntu. The installer would not accept it. So I used the installer to make 2 partitions. One for root and one for swap.

The installer would not recoginse the new small partition for swap. I had to use a Windows installation disk to format the new partition so Ubuntu installer would reconise it existed.

So even with two partitions I selected one for "/" an one for "swap" but the installer says NO ROOT PARTITION.

I want to give Linux a go. But with so many bugs in what is supposed to be an "easy" distro then I can understand why people shy away. I will also shy away unless someone can help a (hopefully soon to be "former") Windows user to install Ubuntu!

---

### Post by xpod on 2006-12-21
Easiest way i found to install Ubuntu those first weeks when windows was still around and on the same disk was to either re-install xp leaving whatever space you wanted to give to Ubuntu "unallocated" or re-size your xp partition but still just leave whatever space you were giving to ubuntu "unallocated"...

THEN.......once i had my unallocated space sorted out i would just put the cd in and point the installer to whatever free space i`d freed up and just let the ubuntu installer do the rest it self.
It should create it`s "/" & "swap" partitions as well as setting up your dualboot for you without any probs .......all you need to do is put your personal details in then sit back and wait:D 

Im sure others who know more will be able to give you much more detailed info but it`s really just as simple as that..
Of course on top of all that simplicity you still need to have a bit of time & patience to get your head round the different ways of doing stuff......especially if you`ve endured yeeeaars with that other thing;)

EDIT:i thought a "partition" was the panel in my hall that the water heater was kept behind not tooo long ago

---

### Post by Circus-Killer on 2006-12-21
> **Ozysearcher said:**
> I want to give Linux a go. But with so many bugs in what is supposed to be an "easy" distro then I can understand why people shy away. I will also shy away unless someone can help a (hopefully soon to be "former") Windows user to install Ubuntu!

so many bugs? no offense, but your limited knowledge of linux can not be considered a bug with the software. all i can really say is that you must give yourself and linux a chance. if you ever decide to switch from english to french, will you do so in a day? i think not. and its not simply about finding the exact equivilant, but rather how it indeed works. for example, if i take a simple sentence and try translate it, i dont just change the words from english to french, there are language rules that will need to be applied.

same thing goes when switching OS's. there is a lot of things that linux does differently to windows. it usually has nothing to do with linux being bad, its just that you've been tought the windows way for so long, that your mind needs time to wrap around the linux way of doing things. a perfect example of this is mounting, and trust me, after about half-a-year, you'll be mounting and wont even be thinking about it. in fact, you'll feel odd going back to windows and not unmounting stuff, i know i do.

so basically, to sum it up, its all about what you've been brought up with. if you were brought up to think burping is rude, when a person from a different culture burps out of gratitude, you brain still sais "gross". again, just give yourself and linux time, and i guarentee after a year, the way of doing things in windows will seem a lot more stranger.

---

### Post by Ozysearcher on 2006-12-21
Unfortunately it is not as simple as that.

I used the installer to resize one partition into two so I would have a partition for the root and one for swap. It couldn't see the new resized partition!

And before that I selected the partition I had made for Ubuntu. It refused to use it saying there was no root. I had selected it and then gone through every option in the window. 

I did check the disk to make sure the .iso burned correctly and the report was there were NO bad checksums.

So thank you for your reply. I appreciate it very much. But I went through that task before posting my question. Tried no less than SEVEN times

---

### Post by NewbieLearnLinux on 2006-12-21
"Mount" (Computer) could be stated simply is to assign a directory (folder) in your Computer with a device (partition) . 

Windoze usually mount your partitions automatically with special folders whose names are Latin letters: A for small floppy, B for big floppy, C is usually the Win partion, D, E... for more...

In Linux, you may have to mount your devices manually sometimes. Most of desktop distributions nowadays can mount automatically, but sometimes (like when you first install Linux), you may make some mountings. 

Mounting in Linux installation is not so hard. The main partition you install the distro should be mounted to " / " (root) folder. Every Linux's distro need another small partition (about 150 - 500 MB) to be mounted with "swap" folder, to perform better. Ubuntu just need two partition like that to run properly, some other distributions may require a boot partition (called " /boot ") for recovery/boot actions... 
(Of course you can mount more directory, as much as you wish...)

The problem you have may be from the file system format, in other words, the partition formats. 

Popular formats for Linux partitions (including root partition) is ext2 or ext3 , but swap partition may have special format. If you use some partition tool to "format" you partitions properly before installing, things will get easier. But you can also do it while installing also, as long as you know the format required for the partitions.

see also about "mount":
[http://en.wikipedia.org/wiki/Mount_%28computing%29](http://en.wikipedia.org/wiki/Mount_%28computing%29)



In short, you need to format the partitions (2 are enough) properly. Then show the installation which one is for "/" (root) and which one is for "swap" . Swap partition size is proportional to your RAM size. Their file system (formats) should be ext2 or ext3. You may read some manuals or HowTo for more details.

btw, I am also a Linux newbie so correct me if I'm wrong.

---

### Post by Ozysearcher on 2006-12-21
Hey, your reply does start to seep through my thick skull.

Because the Ubuntu installation program would not "see" the partitions I used a Windows install disk to format them with NTFS. Then the Ubuntu install program saw them.

When I selected one for "/" then the smaller one for "swap" and then ticked the little boxes indicating that I wanted the install program to format the drives it still refused to proceed saying I had not selected a root, which I had.

So when you say the "format" of the selected drives may be the fault I think you may be right. But I would have thought Ubuntu would have the capacity to format a partition to suit its needs. Apparently not.

I suppose I must try and find some other program to format these partitions then try the Ubuntu install again?

---

### Post by NewbieLearnLinux on 2006-12-21
> I had to use a Windows installation disk to format the new partition so Ubuntu installer would reconise it existed.
Oh, M$ tools would format the partition to VFAT (FAT32) or NTFS !

FAT32 is somehow associated with Linux, but NTFS is surely NOT. If you try installing Linux on a NTFS partition, the installer may complain "can't find root" or something like that. (You can understand why ;) , just another M$ policy )


You may use the GParted, Disk Druid, or the Linux's fdisk (note: different from M$'s fdisk) tool ... to format the partitions to ext3 or ext2 properly. I recall the Ubuntu live-CD has them...

You may also use some commercial software like Partition Magic to format, of course...

---

### Post by whoismilan on 2006-12-21
[QUOTE=Ozysearcher]I suppose I must try and find some other program to format these partitions then try the Ubuntu install again?[/QUOTE]
To be honest, gparted (the program you use when installing Ubuntu), is about as good as it gets.

If you don't format any extra partitions before, they will just be empty space. Then you can use the Ubuntu partitioner to change/make/delete partitions ("Manually edit partition tables" or something like that). You can see all space on the disks in Ubuntu's partition editor, Windows' partition editor is useless when it comes to Linux.

---

### Post by xpod on 2006-12-21
I sympathise with you m8 as i had just as many problems during my few months with windows....
re-installing it especially.](*,) 

New OS`s can be a right royal pain in the butt eh.;) 

If your having all these issues with the live cd then you could always give the "alternate cd" a shot, which can work a lot better in many cases.
No live session to try with it as it`s only for installing but it too can save a lot of headaches in some cases.

At least if one way of installing is failing in Ubuntu there are just so many other ways to try....

You could try the "alternate cd" which is a text based installer with no live sessions to load and it can make the job of installing so much easier for many people...

This site may help a bit with that course of action

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Theres also a "gparted" live cd you can get which can make pre-partitioning a lot easier in some cases.It`s basically the same as the live cd version but it can be a lot less problematic for many people
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Again though, as has been alluded to there is just so much for you to re-learn and although it really isn`t as hard as it may first seem it`s still something that will take "time & patience" and if you dont have that time or  aint the most patient of people then  it`s going to be a battle:D 

Good luck either way m8.
You just got the best xmas pressie you could ever wish for imho...
Have fun with it

---

### Post by nsleiman on 2006-12-21
> **Ozysearcher said:**
>  First Time Installation
I was impressed with the Live CD enough to try and install. Unfortunately the hype about Ubuntu being easy was NOT true.

After using Windows for years I am familiar with words like: "install" but "mount?" I know a rider mounts a horse, but computers?


My dear,
'mount' is not 'install'! a drive can be mounted in order to install on it, so windows also use this terminology. (yes! they talk like professionals sometimes!).

After you read some articles in this forum, i bet you will drop the XPjsajkja... hierarchy :)

---

### Post by Ozysearcher on 2006-12-21
Thanks for the reply, but: "You can see all space on the disks in Ubuntu's partition editor" was not correct, in my case at least.

I used the installer to resize a partition but it would not "see" the new space made by the new small partition. That is why I tried a Windows install disk to format it in an attempt to get the Ubuntu partition tool to see it.

So it sounds like Ubuntu install can't format so I will have to format the two partitions with some other program and try to install again.

Since the install disk won't format the partitions (or at least, it does not show any option to allow me to other than the boxes I already ticked which did not work) I will try and find a program to format them. Which should I aim for: ext 2 or ext3 (I'll try and learn what this means once I have Ubuntu installed and running!)

---

### Post by LookTJ on 2006-12-21
To point out that 1 GB equals 1024 MB.

---

### Post by Ozysearcher on 2006-12-21
I know one gig equals 1024.

Well I tried the Ubuntu live install disk again to delete the two partitions I had and remade new partitions with the install program. No matter how many times I rebooted and tried again the install program refuses to use the partitions or format them in any way.

I have selected all sorts of options which are logical and should work then I tried any silly combination in case I was at fault. No, it wasn't me. The install program won't use the spare space on the hard disk to install Ubuntu.

Should a released distro be this flawed?

---

### Post by NewbieLearnLinux on 2006-12-21
Well, looks like you DIDN'T TELL the installer which MOUNT POINT is root and which is swap.

You should have clicked the dropdown-listbox and have selected MOUNT POINTS like this picture:

[img]http://img205.imageshack.us/img205/2085/selecttb7.jpg[/img]

If you leave it (i.e. do not select the " / " in the combobox for any MOUNT POINT), then an error message "No Root Partition" will appear.


Well, I'm pretty sure Ubuntu is not flawed in this case ;) 

hope this helps,

---

### Post by Ozysearcher on 2006-12-21
Thanks NewbieLearnLinux for your assistance.

When I said I tried all the logical options then even silly ones I meant every word. I DID specify in the drop down boxes which partition should be the root (the larger) and which should be the swap (the smaller partition).

In other words, I selected everything the installer could possibly ask for, in as many combinations as I could after successive reboots to try and get past the problem.

So when I DO follow the instructions and prompts during install and when that fails reboot and go back and try as many combinations as possible then I am bound to accidentally get the right one eventually.

But after so many reboots and attempts the install won't go past that screen you posted. (Hey, posting a screen shot like that is a great idea!).

So I tend to think if following the installers own instructions then it must be broke! (flawed)

No wonder some of my friends gave up on Linux (they tried Fedora and others).

I thought Ubuntu was meant to be an improvement.

Despite this obvious flaw (bug or whatever) I am still interested in installing and giving it a go. Can't give it a go unless it will let me install first!

---

### Post by xpod on 2006-12-21
> Should a released distro be this flawed?


Now i could just as easily say that about windows........but as i only used it for a few months i would`nt dream of making such outrageous statements:-\" 

Nothing wrong with ubuntu m8:D

---

### Post by NewbieLearnLinux on 2006-12-21
Would you give us some more information: Your HDD (brand, size, SATA,...)? and partitions (size, format, primary/logical, active/bootable...)? and it's also good to describe your steps installing too .

well, some ScreenShots of the installation would be great ! 
(If you can not take screenshots while installing, a virtual machine software or a digital camera will do it easily.)

Anyways, this "bug" is really strange, and some more information might help us solve it.

---

### Post by Ozysearcher on 2006-12-21
Hey NewbieLearnLinux, thanks for your reply and patience with a complete stranger to Linux. I do really appreciate your assistance.

"Virtual Machine Software"???? Hey, lets stick to English, this I don't understand.

A friend of mine (sympathetic to Linux but a Windows 2000 user and MCSE) in ICQ said something might be blocking the install routine from accessing the partitions or empty disk space if I try and use that instead.

My HDD is: a WDC WD1200 JD-00FYBO SATA 1 which had two partitions.

The first partition is around 20 gig for Windows XP so called Professional. The second partition is also NTFS of approximately 78 gigs leaving the rest (about 20 gigs) for Linux.

At this point in time I am so new I need the Windows horror to keep going until I learn Linux. I have been planning this for the last two years.

I am trying to install version 6.10 which I recently downloaded and checked the CD for errors before going ahead.

After several boots and following all the prompts I rebooted many times and tried all sorts of silly options, selecting different things because following the prompts in a normal logical way didn't work.

But I still get no root selected error even though I have, just as in your screen shot.

If I took a screen shot it would have looked just like yours only the error message at the bottom would be different.

This is frustrating but I expect an "easy" installation will not be easy. Still, I am getting a lot of grey hair out of this!

---

### Post by 3rdalbum on 2006-12-21
I don't know why Ubuntu has that Ubiquity installer (the one on the Live CD, that you're trying to use)- I haven't used it to create a dual-boot setup before, but that above screenshot confuses the hell out of me (and I've been using Linux for almost a year).

I second the suggestion that you download the Alternate CD and use that to install. It's a sort of "textual graphical" installer, and it looks rather primitive, but it's very powerful and it seems to be easier to use than Ubiquity.

(Other distributions have much easier-to-use GUI installers than Ubuntu, don't worry about that).

---

### Post by NewbieLearnLinux on 2006-12-21
well, so the partition you intended to install Ubuntu were NTFS. That filesystem were a pain for Linux users the old days, but now Linux community has gotten over it. The SATA could be a little problem, but in your case it's very likely that the NT FileSystem is the culprit.

Actually the M$'s format tools cannot format the NTFS back to FAT32 (or FAT16), so you probably were installing Ubuntu on a NTFS partition. Impossible then. 

If you can convert the NTFS partition back to FAT32, then the Ubuntu's installer may convert the FAT32 to ext3 or ext2. But in order to keep the data after converting, you'll need either Partition Magic, or [qtparted](http://en.wikipedia.org/wiki/Qtparted) or [GParted](http://en.wikipedia.org/wiki/Gparted) CD...


Maybe you should use a partition tool (not from M$) to resize the big partition and make 2 new partitions? That way can keep the data, and easier to format the new partitions to ext3/ext2. For Example: 

**Before:**
partition C: 20GB (NTFS) , partition D: 80GB (NTFS)

**After:**
part C: 20GB (NTFS), part D: 60GB (NTFS), part E: 19.5GB (FAT32/unformatted), part F: 500MB (FAT32/uf)

then you can convert E: and F: to ext3/ext2 filesystem (better say, format them to ext3 since these partitions are supposed to contain no data) , using any of the Linux's partition tool. Then they will be root and swap partitions.


The last thing that might be problem is SATA HDD. Some big SATA HDD may have some problem with a few distro, my friends say that. It is unlikely in this case, though.


EDITED: My quick Googling:
[http://www.linuxforums.org/forum/linux-newbie/52309-changing-ntfs-ext3-without-losing-any-data.html](http://www.linuxforums.org/forum/linux-newbie/52309-changing-ntfs-ext3-without-losing-any-data.html)
(not tested)

---

### Post by steve.horsley on 2006-12-21
I always recommend that you don't make partitions for Ubuntu. Uas Partition Magic or similar to shrink an existing partition and leave unused/unpartitioned space. Then let the Ubuntu installer use the free space. It will make its own partitions (systen and swap) and format them appropriately. 

You say you have 4 partitions. If they are all primary partitions, you have a problem because hard disks can only have 4 primary partitions. You will need a new hard disk, or delete one of the primary partitions and replace it with an extended partition (which can then contain multiple logical partitions).

---

### Post by Ozysearcher on 2006-12-21
Thank you everyone for being so very helpful. I really do want to get Ubuntu up and running so I will cut my losses on trying to install to partitions on my sata 1 drive.

After re-reading all the suggestions by everyone and carefully considering what the installation routine was (and was not) doing my strong gut feeling is it just could not handle the sata 1 drive for some reason. It could not "see" unpartitioned space and when it could see a partition, even when unformatted, it would resize the partition but otherwise not work with it.

So I have reformatted the single third partition into an NTFS partition and given it back to windows.

As soon as the computer finishes moving some files for me I'll rip open the case and install another hard drive. This time a normal old fashioned IDE drive. Then I'll try and install again. Hopefully I'll have an installation going in an hour or so!

Thanks again everyone. I'll let you know if installing to a totally separate drive works.:confused:

---

### Post by steve.horsley on 2006-12-21
AAARGH!!!

Don't mix SATA and IDE drives. All SATA or all IDE is fine. If you mix the two types, you will likely find that the machine cannot boot at all after installing Ubuntu. There is a problem with the installer that points the bootloader at the wrong drives when you mix types. It is possible to fix if you know exactly what the bootloader is doing, but I don't think it's an ordeal you're ready for.

However, I still think you would get a good install if you would only clear some free space and allow the installer to then use that free space to make its own partitions. Remember, you don't have to use Linux to create the partitions for Windows to install onto. Similarly, you don't have to use Windows to make the partitions for Linux to install onto, and in fact windows can't do it.

---

### Post by Ozysearcher on 2006-12-21
OOPS!

Hey, thanks for the warning about mixing drives and dual booting.

The only reason I planned to mix drives is because I tried so many times to get Ubuntu to install to a partition on C drive. Whether I set up two partitions UNFORMATED or formatted, or a single partition formatted or unformatted, it refused to proceed any further after I checked the appropriate options for root and swap.

So if I should not use a mix of drives then that is it. I already tried to allow Ubuntu to use the free space itself but it then didn't see the free space at all so I couldn't select it.

Now it looks like I have ran out of options unless I have the funds to build another computer entirely.

---

### Post by Get_Ya_Wicked_On on 2006-12-21
All you need/ed to do is get a copy of the alternative install cd.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso)

And follow these instructions:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The text partioner is very clear. You resize a partion. Give the space to another. And so on.

---

### Post by carloslosgrande on 2006-12-21
Hi, I've used the partitioning in the Live CD which works well up to a point but to really be able to setup your partitions exactly how you want then I highly recommend the GParted CD. Works like a dream!
I use AFTER I've installed Ubuntu.

---

### Post by steve.horsley on 2006-12-22
> **Ozysearcher said:**
> OOPS!

Hey, thanks for the warning about mixing drives and dual booting.

The only reason I planned to mix drives is because I tried so many times to get Ubuntu to install to a partition on C drive. Whether I set up two partitions UNFORMATED or formatted, or a single partition formatted or unformatted, it refused to proceed any further after I checked the appropriate options for root and swap.

So if I should not use a mix of drives then that is it. I already tried to allow Ubuntu to use the free space itself but it then didn't see the free space at all so I couldn't select it.

Now it looks like I have ran out of options unless I have the funds to build another computer entirely.

You're not listening. 
Leave free space on the disk. Unpartitioned space. That partition you made for Ubuntu to go on - well delete it. Don't just re-format it to whatever filesystem you think Ubuntu might happen to like, delete it completely. If there's a partition there, it's not free space - it's a partition containing something and the installer doesn't know what. Leave **free space** and **let the installer create the partitions it wants**. Again - you don't use Linux to make windows partitions when installing Windows, so don't use windows to make Linux partitions when installing Linux.

I know you're trying to help the install along, but you are tying its hands. You are probably trying to get it to install on a filesystem type that it cannot use (you don't say what system type you labelled the partition as). Just give it som unused disk and let it do its own thing. Stop fighting against it.

Best of luck.

---

### Post by maniac_X on 2006-12-22
Several people here have suggested the [GParted CD]("http://gparted.sourceforge.net/livecd.php")! Speaking from my own newbieness in Linux, I must 
agree. Being a huge fan of Partition Magic, I can say that no longer does anyone need to pay for Part.M. 
The [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") is awesome!

I still have my own problems to deal with(passwords) but the partitioning was 
a snap with the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). On a scale of 2 hands, I give it **[COLOR="Red"]3 thumbs up[/COLOR]**!!! ;)

---

### Post by steve.horsley on 2006-12-22
While I agree that Gparted is just fine for the job, here we have someone who clearly distrusts Linux, to the point that he doesn't want to allow the installer to do its own partitioning. When someone is that distrustful, I see two reasons to suggest that they use PM:

1) They will feel more comfortble with it, while doing something quite scary. This may improve their chances of getting it right.

2) If they screw it up, they can't go around telling everyone that Linux screwed their system.

---

### Post by Ozysearcher on 2006-12-23
Thanks to all who offered help for my first time installation.

The concern for me was caused by too many years of Windows thinking for me when doing something because it would so often NOT do what I wanted. So I formed a habit of trying to maintain control when doing things.

The Ubuntu automatic install didn't confirm to me just what it was doing in a way that I could understand it so I was worried about my existing data on the Windows partitions. To use the manual option only caused me grief. I finally bit the bullet and trusted the automatic install after backing up as much data as I could.

So now I have a dual boot system with Ubuntu apparently running well. Took me just a couple of minutes to find out how to add support for watching DVD etc. No problems there.

Now I have something to tinker with to get full functionality out of. My next little project will be to try and install the same fonts I normally use in my documents.

So thanks to all for your help. For the record the automatic install worked fine. My knees have stopped shaking now that I have confirmed my existing data is still intact!

Looking forward to learning as much about Ubuntu as I can.

Thanks all.:D

---

### Post by riven0 on 2006-12-23
> **Ozysearcher said:**
> 
Now I have something to tinker with to get full functionality out of. My next little project will be to try and install the same fonts I normally use in my documents.


To install microsoft fonts like arial and times new roman do:

> sudo apt-get install msttcorefonts

Or search for it in synaptic package manager and install it from there.

---

### Post by ratchetr on 2006-12-23
> **Ozysearcher said:**
> 
So I have reformatted the single third partition into an NTFS partition and given it back to windows.

As soon as the computer finishes moving some files for me I'll rip open the case and install another hard drive. This time a normal old fashioned IDE drive. Then I'll try and install again. Hopefully I'll have an installation going in an hour or so!


Yikes...all this partitioning and formating stuff sounds way too complex just to try out Ubuntu...or any other distro.

Why not just install under a virtual machine in Windows? VMWare works well. The server version is free and (though not 'officially' supported) can be run on XP.

---

### Post by spockrock on 2006-12-24
oh man I would never ever, ever, ever, suggest anyone use partition magic, I had one bad experience with it resizing a windows partition made it that windows couldn't even read the filesystem.  

Gparted would like a dream however, both the live disc and the ubuntu live disc version.  Best part is gparted live disc is free.......

---

### Post by LameBMX on 2006-12-24
> **Ozysearcher said:**
> Hey, your reply does start to seep through my thick skull.

Because the Ubuntu installation program would not "see" the partitions I used a Windows install disk to format them with NTFS. Then the Ubuntu install program saw them.

When I selected one for "/" then the smaller one for "swap" and then ticked the little boxes indicating that I wanted the install program to format the drives it still refused to proceed saying I had not selected a root, which I had.

So when you say the "format" of the selected drives may be the fault I think you may be right. But I would have thought Ubuntu would have the capacity to format a partition to suit its needs. Apparently not.

I suppose I must try and find some other program to format these partitions then try the Ubuntu install again?

well sir .. what you have experienced was things done right ... tools that recognize other operating systems filesystems, and wont write to them so it wont mess them up. backing up is always your best bet but so far in my experience *nix tends to error on the side of safety with other other operating system ... install windows to the first partition -edit- the normal windows installation -edit- ... and if your nix (including the bootloader) goes belly up ... all you have to do is put in your windows cd ... recovery console ... type fixmbr .. hit enter and reboot .... since you are new you may want to jot that down so you can make it onto the web easily to see how you botched your *nix OS up ... now that you actually have real control of your computer your prolly gonna fry it ... face facts .. backup .. backup often ... and dont fear it because every install you will learn a little bit but more importantly understand more how your computer works (not too mention figuring out how to resurrect it :) ) 

so far from what ive experienced (used gentoo a while back) ubuntu has the clearest documentation for a beginner (like me too)

---

