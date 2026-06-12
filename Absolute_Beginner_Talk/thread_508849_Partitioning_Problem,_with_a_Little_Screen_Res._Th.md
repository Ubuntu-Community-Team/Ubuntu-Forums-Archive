---
title: "Partitioning Problem, with a Little Screen Res. Thrown in"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by InflammatoryWin.Apologist on 2007-07-24
Hey guys, I was on here about twelve hours ago, asking some questions. I just bit the bullet and popped in the disk, but I already have two problems: the screen resolution in so low that I can't see or use the "Forward" button on the installer. I looked around and found where to change it, but the only other option is even lower. I managed to get around this by using the "Enter" key, but I'm assuming the clicking I'm going to have to do on the next step will put an end to the effectiveness of that little trick.

And two, I want to dual boot it with XP, using [this guide.]("http://www.acpmag.com/6101/dualboot_windows_xp_and_ubuntu") Problem is, that partition option doesn't come up. Here's what does:

[IMG]http://img509.imageshack.us/img509/526/screenshotpj5.png[/IMG]

Anything you guys could tell me here would be awesome. 

Thanks.

---

### Post by LaRoza on 2007-07-24
Move the panels, delete the bottom and put the top on the side.

OR

hold "alt" and click in the window and move it.

After this, you will just have to install the correct drivers, usually very easy.


For the partitioning, you might want to make one before hand, if you have a "recovery" partition, you could delete that, then the resize option will come up.

If you have the recovery partition, and want to keep it, you will have to create a new partition by shrinking the Windows partition, and installing to the free space.

---

### Post by InflammatoryWin.Apologist on 2007-07-24
You're the man. The effectiveness ever literally all of your res. solutions made me slap my forehead. Man, I really didn't want to have to figure out the partition thing myself. I have PartitionMagic, should I use that, or is something else easier/better? Also, Do I need to create all those swap partitions and all that jazz?

And I assume that the rescue partition is the one that holds me Windows install file and whatnot? If so, yes, I do have one. 

Thanks.

---

### Post by InflammatoryWin.Apologist on 2007-07-24
Which of these file system types on the pull-down should I be using?

[IMG]http://img511.imageshack.us/img511/4517/partitionshotew0.png[/IMG]

Also, any other helpful tips here would be appreciated.

---

### Post by 56seeker on 2007-07-24
To install ubuntu you'll need at least a swap ans a root (/) partition; although you can specify more if you like. The swap partition (which I believe should be 3 x your RAM size must be in Linux swap; every thing else should be in Linux EXT3

---

### Post by LaRoza on 2007-07-24
I recommend using GParted to shrink current partition, your Windows partition. Then using GParted to create a large partition, with EXT3 and a 512 MB partition with Swap.

Swap doesn't need to be bigger than that! People say it should be 2 or 3 times your RAM, but that is false, it is not necessary to make it larger than 512 MB.

When you install, install / to the EXT3 partition, and swap will be mounted as swap.

---

### Post by alienexplorers on 2007-07-24
Since you are creating new partitions why not through in a /home partition also.  No extra work, but it can be a god send if you ever have to reload ubuntu.

---

### Post by InflammatoryWin.Apologist on 2007-07-24
> **LaRoza said:**
> I recommend using GParted to shrink current partition, your Windows partition. Then using GParted to create a large partition, with EXT3 and a 512 MB partition with Swap.

Swap doesn't need to be bigger than that! People say it should be 2 or 3 times your RAM, but that is false, it is not necessary to make it larger than 512 MB.

When you install, install / to the EXT3 partition, and swap will be mounted as swap.

I have no idea what most of that means. Talk down to me. Also, do I load Ubuntu to use GParted, or do I download it in Windows?

---

### Post by InflammatoryWin.Apologist on 2007-07-24
Okay, I'm going to take a guess here:  I'm shrinking my main partition (the Windows one) to make room for a new linux one, which I'm supposed to make file system type EXT3. Then, also, I'm making a 512MB partition, file system type unclear, for the swap, which during installation I'm supposed it somehow designate using a a slash. Tell me how much of this is wrong, and clear up the parts that I seem unsure about, talking to me like I'm six. 

Thanks for all the help.

---

### Post by InflammatoryWin.Apologist on 2007-07-24
I hate to seem pesky and annoying, but is there maybe a good thread on here that could help me, at least?

---

### Post by logos34 on 2007-07-24
> **InflammatoryWin.Apologist said:**
> Okay, I'm going to take a guess here:  I'm shrinking my main partition (the Windows one) to make room for a new linux one, which I'm supposed to make file system type EXT3. Then, also, I'm making a 512MB partition, file system type unclear, for the swap, which during installation I'm supposed it somehow designate using a a slash. Tell me how much of this is wrong, and clear up the parts that I seem unsure about, talking to me like I'm six. 

Thanks for all the help.

Use gparted (system>admin) to shrink windows.

Then install using 'manual' option and create partitions and mount points thus:

**/swap **       ---> ext2   swap (512mb -1 gb)
**/**               ---> ext3   root partition
**/home**       ---> ext3   home (optional but highly recommended)

Other recommends: get ntfs-3g and ntfs-config so you can write to windows.  Get fs-driver to add ext3 read/write to windows side.

For future reference: for the graphics problem using the livecd you had initially you can just run
[B]
sudo dpkg-reconfigure xserver-xorg [/B]

to adjust the resolution, then hit ctrl+alt+backspace to restart desktop.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> Use gparted (system>admin) to shrink windows.

Then install using 'manual' option and create partitions and mount points thus:

**/swap **       ---> ext2   swap (512mb -1 gb)
**/**               ---> ext3   root partition
**/home**       ---> ext3   home (optional but highly recommended)

Other recommends: get ntfs-3g and ntfs-config so you can write to windows.  Get fs-driver to add ext3 read/write to windows side.

For future reference: for the graphics problem using the livecd you had initially you can just run
[B]
sudo dpkg-reconfigure xserver-xorg [/B]

to adjust the resolution, then hit ctrl+alt+backspace to restart desktop.

Thanks a lot, and I think I can figure this out from here, but if you don't mind, I'd feel super comfortable if you walked me through it just a little more moronically, I'm in GParted, I selected the drive, and click Move/Resize.

Now, I have this:

[IMG]http://img504.imageshack.us/img504/9949/screenshotzl3.png[/IMG]

I guess I scale "NEW SIZE" back to something like 100gigs, do I do anything else with the rest of the options there? And then what can I expect?

---

### Post by logos34 on 2007-07-25
> **InflammatoryWin.Apologist said:**
> Thanks a lot, and I think I can figure this out from here, but if you don't mind, I'd feel super comfortable if you walked me through it just a little more moronically, I'm in GParted, I selected the drive, and click Move/Resize.

I guess I scale "NEW SIZE" back to something like 100gigs, do I do anything else with the rest of the options there? And then what can I expect?

Remember, windows needs at least 15% free space for defrag to run, so 100 gigs means you won't have room to add any more files.  Leave windows a little more.  

This link will walk you thru the install:
**[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)**

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> Remember, windows needs at least 15% free space for defrag to run, so 100 gigs means you won't have room to add any more files.  Leave windows a little more.  

This link will walk you thru the install:
**[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)**

Thanks for the link, but I keep reading things like that, and it usually only serves to confuse me. I'm really not very smart. If I get too annoying, tell me off, but if people will keep helping me, I'd rather just keep asking questions here.

I think I'm going to only to the bare necessity for now, (the swap and the EXT3). Does freeing up around 15-17GBs sound right?

---

### Post by logos34 on 2007-07-25
> I think I'm going to only to the bare necessity for now, (the swap and the EXT3). Does freeing up around 15-17GBs sound right?

That's plenty for linux.

Post back if you need help.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> That's plenty for linux.

Post back if you need help.

Thanks, I think it's about half done.  I assume my next step is to create the new partitions? Anything simplified you or anyone can tell me in advance that could convince me to use any of your other recommendations ("/home" and whatever that other thing was that would allow me to save to and from Windows [I didn't realize that I couldn't already do that. Will I be able to play my pre-existing video files without doing this?]) would be greatly appreciated, along with all your other help.

Thanks.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
Also, how long should the resizing take? It seems like the unallocated section has been stuck at 15.63GBs (out of 16) for a long time.

Edit: 

Edit that last edit, I  never clicked apply.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
Edit. Nevermind, I'm stupid.

---

### Post by logos34 on 2007-07-25
no, it's usually very quick, and when you get to the install part that takes only ~30 min.  

If there's one thing you should read through, it's the ubuntu section at that psychocats.net site I gave you. It's very accessible, very easy to understand.

You'll be able to play all your audio-video material on your windows partition using the default media players in gnome or kde.  As long as you have the codecs.  The first thing I'd do is read through the Restricted Formats page.  The easiest way to install all of them is through automatix2.

---

### Post by logos34 on 2007-07-25
> Should I quite this and use a a program in Windows?

Did you defrag windows first?  Maybe there are scattered files or some 'unmovable' files at the end of the disk.
If it's taking a really long time to shrink, quit and go into windows, defrag and temporarily turn off hibernation and paging/virtual memory.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
Thanks again for the help. I'm still determined to do this, but I'm doing to regroup and try it again in the morning. I think I'll resize with Partition magic in Windows. Unless there's some reason I shouldn't.  I'll post again tomorrow. 

(I actually keep DiskKeeper running most of the time.)

---

### Post by InflammatoryWin.Apologist on 2007-07-25
Alright, I finally made some kind of progress. I resized the partition down to something like 128.5 gigs, and now have 16+ unallocated. Do I just start the install now, and do the other partition in that, or do I manually create all these? 

Thanks in advance, and I know this really isn't saying much, but I wouldn't have even gotten this far without all your help.

---

### Post by logos34 on 2007-07-25
Yes, you can begin the install now--you can let ubuntu create the partitions out of the unallocated space for you, or manually create a 512 MB - 1 GB swap partition (ext2) mounting at '/swap', and then give the remaining ~15 gigs of unallocated space to root (ext3) mounting at '/', and away you go.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> Yes, you can begin the install now--you can let ubuntu create the partitions out of the unallocated space for you, or manually create a 512 MB - 1 GB swap partition (ext2) mounting at '/swap', and then give the remaining ~15 gigs of unallocated space to root (ext3) mounting at '/', and away you go.

Thanks. It's really a life-saver that I can still access the internet to get help from you guys while in the install mode. Otherwise this would be hell. Off I go.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
Alright, again, I think I could figure this out, but it would be really awesome if someone walked me through this last thing here, because I terrified. I chose "Manual" for the partition type, selected the "free space," clicked "Create New Partition..." well, here's a screen shot:

[IMG]http://img503.imageshack.us/img503/9886/screenshoter9.png[/IMG]

logos, could you just tell me exactly what to put in each field for your partition scheme? I know my questions are really repetitive, but I really appreciated your patients.

Thanks.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
I have the first one reading:

(For type) Primary (Do I want "Logical?")

(Size) 512

(Location) Beginning (Do I want "end?"

(Use as) EXT2 ("Swap" is also an option)

(Mount Point) "/swap"

Does that look right? should I do one of the other partitions first for any reason?

---

### Post by logos34 on 2007-07-25
just make a primary ext2 for swap at 'beginning' with mount point '/swap'.  Then make another primary at beginning on the remaining with mount point '/'.  

You could make an extended partition and put linux inside (which would save one primary--you can only have a total of four on a disk), but I think you better just go the easiest way for now.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> just make a primary ext2 for swap at 'beginning' with mount point '/swap'.  Then make another primary at beginning on the remaining with mount point '/'.  

You could make an extended partition and put linux inside (which would save one primary--you can only have a total of four on a disk), but I think you better just go the easiest way for now.

Thanks, you're awesome.

Next thing: I don't really know how to specify which one is swap and whatnot from here. I assumed it would be an option on the next screen, but I get this:

[IMG]http://img228.imageshack.us/img228/2448/screenshotqm4.png[/IMG]

What do I do next (I hope I gave you enough info to answer this)?

---

### Post by InflammatoryWin.Apologist on 2007-07-25
Anyone Know how to do this?

---

### Post by logos34 on 2007-07-25
go back and and edit hda3 so tha tthe **type** is 'linux swap' or 'linux swap/solaris'.  It will be formatted as ext2.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> go back and and edit hda3 so tha tthe **type** is 'linux swap' or 'linux swap/solaris'.  It will be formatted as ext2.

My only options are:

ext2

ext3

reisersf

jfs

xfs 

fat16

fat32

swap

dontuse.

---

### Post by logos34 on 2007-07-25
choose 'swap'

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> choose 'swap'

Thank you, thank you, thank you, thank you! It's alive!

I'm sure I'll have a million more annoying questions, and I'll have to figure out how to fix my resolution, but I just so thrilled that I finally have it up and running. I've been trying to do this for months, and I never would've done it without your help.

I have some playing around to do.

---

### Post by logos34 on 2007-07-25
install the kernel updates first off then install the graphics driver using Automatix (third-party) or applications>add/remove.  that'll fix your resolution problems

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> install the kernel updates first off then install the graphics driver using Automatix (third-party) or applications>add/remove.  that'll fix your resolution problems

How do I ge the kernal updates, and then how do I get Automatrix (I read it was a must)?

Any other programs or packages you think I would need or want? This is the first I've used any Linux distro, so I have to feel my way around.

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **InflammatoryWin.Apologist said:**
> How do I ge the kernal updates, and then how do I get Automatrix (I read it was a must)?

Any other programs or packages you think I would need or want? This is the first I've used any Linux distro, so I have to feel my way around.

Bump?

---

### Post by logos34 on 2007-07-25
make sure all the repos are enabled:

system>admin>software sources

download all the updates

then open a terminal (or system>admin>synaptic)
[B]
sudo apt-get install automatix2[/B]

READ THIS:
[COLOR="Red"]https://help.ubuntu.com/community/[/COLOR]

ANOTHER NEAT LINK:
[COLOR="Blue"]http://ubuntuguide.org/wiki/Ubuntu:Feisty[/COLOR]

---

### Post by InflammatoryWin.Apologist on 2007-07-25
> **logos34 said:**
> make sure all the repos are enabled:

system>admin>software sources

download all the updates

then open a terminal (or system>admin>synaptic)
[B]
sudo apt-get install automatix2[/B]

READ THIS:
[COLOR="Red"]https://help.ubuntu.com/community/[/COLOR]

ANOTHER NEAT LINK:
[COLOR="Blue"]http://ubuntuguide.org/wiki/Ubuntu:Feisty[/COLOR]

I tried using the terminal, but when I try to enter the password, I can't type anything. And no thing comes for automatrix in Synaptics. Help?

---

### Post by logos34 on 2007-07-26
oops, forgot exactly how that worked--you install the deb pkg first and it THEN it adds the automatix to the third-party repos in synaptic

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

 You want this deb pkg I believe:
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.11-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.11-7.04feisty_i386.deb)

After you dowload it just right-click on it and let the debi installer take it frm there

---

### Post by InflammatoryWin.Apologist on 2007-07-26
> **logos34 said:**
> oops, forgot exactly how that worked--you install the deb pkg first and it THEN it adds the automatix to the third-party repos in synaptic

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

 You want this deb pkg I believe:
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.11-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.11-7.04feisty_i386.deb)

After you dowload it just right-click on it and let the debi installer take it frm there

Cool. Thanks. How do I find that driver to fix my screen res.?

---

### Post by logos34 on 2007-07-26
what kind of graphics card do you have?  nvidia, ati, intel, via???

---

### Post by InflammatoryWin.Apologist on 2007-07-26
Also, what's the best video player for Ubuntu? For Windows I always liked BSPlayer, and WMP wasn't far off.

(This is cool. I tried to play a file, but didn't have the right codec. Ubuntu automatically found it for me.)

---

### Post by InflammatoryWin.Apologist on 2007-07-26
> **logos34 said:**
> what kind of graphics card do you have?  nvidia, ati, intel, via???

99% sure that it's nvidia.

What's an easy way to be sure? I don't know my way around well enough to check from here on my own.

---

### Post by logos34 on 2007-07-26
well, if it's nvidia automatix will install that.  Just run it and select everything (including the all-impoortant multimedia codes) you think you will need.  The nvidia binary driver (9762 or 9755 i believe) is there too.  Then after you install it run (from a terminal):

**sudo nvidia-glx-config enable**

Restart.  'nvidia-settings' should appear under apps>system tools.  Or run in a terminal 'nvidia-settings'.

Adjust your resolution and refresh rate under 'X server display config' heading.  Save to file to xorg file.  Don't worry about what it indicates under system>prefs>screen resolution (it will be wrong). 

Best video player? To tell you the truth I'm not satisfied with any of them...Some swear by VLC, other Mplayer, and they curse totem, but totem and gxine seem to cover all the bases for me at least (I also like Kaffeine for dvd viewing even though its kde).

---

### Post by logos34 on 2007-07-26
> What's an easy way to be sure? I don't know my way around well enough to check from here on my own.

from terminal:
[B]
sudo lshw[/B]

---

### Post by InflammatoryWin.Apologist on 2007-07-26
> **logos34 said:**
> well, if it's nvidia automatix will install that.  Just run it and select everything (including the all-impoortant multimedia codes) you think you will need.  The nvidia binary driver (9762 or 9755 i believe) is there too.  Then after you install it run (from a terminal):

**sudo nvidia-glx-config enable**

Restart.  'nvidia-settings' should appear under apps>system tools.  Or run in a terminal 'nvidia-settings'.

Adjust your resolution and refresh rate under 'X server display config' heading.  Save to file to xorg file.  Don't worry about what it indicates under system>prefs>screen resolution (it will be wrong). 

Best video player? To tell you the truth I'm not satisfied with any of them...Some swear by VLC, other Mplayer, and they curse totem, but totem and gxine seem to cover all the bases for me at least (I also like Kaffeine for dvd viewing even though its kde).

I'm having the same problem where it won't let me type anything for the password.

---

### Post by InflammatoryWin.Apologist on 2007-07-26
Is this a crazy problem?

---

### Post by InflammatoryWin.Apologist on 2007-07-26
I restarted anyway, and the resolution problem is fixed. I'm just a little curious why I can't use the terminal. I'm sure I'm doing something wrong.

---

### Post by logos34 on 2007-07-26
are you perhaps already running as root?  what about just leaving out 'sudo', can you run commands that way?  not sure what the problem could be.  But at least you solved the resolution issue.

---

### Post by meierfra on 2007-07-26
Just type your password and  press "enter".  

The password is completely hidden for security reason.

---

### Post by InflammatoryWin.Apologist on 2007-07-26
> **meierfra said:**
> Just type your password and  press "enter".  

The password is completely hidden for security reason.

Like it doesn't even show stars or anything? If so, that's it.

---

### Post by meierfra on 2007-07-26
It just feels and look like you are not typing anything. But the computer is registering your keystrokes.

---

### Post by meierfra on 2007-07-26
> like it doesn't even show stars or anything? I

Yes

---

### Post by InflammatoryWin.Apologist on 2007-07-26
Sorry guys, I've never used a command line or a terminal before.

---

