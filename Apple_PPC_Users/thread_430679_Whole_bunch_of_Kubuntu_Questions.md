---
title: "Whole bunch of Kubuntu Questions"
date: 2007-05-02
forum: Apple PPC Users
---

### Post by megabenman on 2007-05-02
Hi.  I'm a mac user, with a 20" 2nd Generation iMac G5, 2.0 GHz, 512 mb of RAM (I need to upgrade....).  Anyway, I know a decent amount about computers, and I can help most people with their problems.  The only thing I don't know is programming and Linux.  I've always learned best by just doing things myself, so I wanted to install Kubuntu onto my iMac.  I know PPC Linux isn't nearly as good as x86 Linux, but this is supposed to be a learning experience.  So, now onto my enormous list of newbie questions (for Kubuntu Feisty Fawn):

1.  I want to be able to dual boot OSX and Kubuntu.  I know you have to resize your HFS+ partition to do this.  On the Desktop CD, I saw a program called GTParted (or something like that).  So, my questions are:  Can this program resize the HFS+ partition with no problems (I will back it up)?  Once I do that, will there automatically be another partition with free space that I can install Kubuntu on (there were already 2 partitions with free space, one with barely any space and one with 186 mb, so will it create another partition using the space stolen from the HFS+ partition)?  If not, what should my next step be to installing it?

2.  Kubuntu never shuts down right.  I always have to hold the power button.  Will a restart work?

3.  Will PPC Linux help me learn about x86 linux, or are they completely different in every aspect (installing programs, changing the interface, etc.)?

4.  What the hell is a respitory (sp?)?

5.  Is there a website listing PPC Linux Applications?

6.  How do I get airport extreme to work?

7.  How do I get my bluetooth mouse and keyboard to work (the apple ones)?

8.  Thanks.

---

### Post by DJ_Max on 2007-05-02
If you really want to get a grip on Linux, you should mess around with Ubuntu's kernel, or at least read up on it. Since most people confuse a distribution with Linux.

Anyway, I've been dual booting Ubuntu and OS X since the beginning, and I wouldn't say Linux PPC isn't as nearly as good as Linux on the x86 architecture, it's come a long way, even Linus himself runs Linux on the PPC arch. Only a few things are lacking, mainly a few codecs.

1.) I've never re-sized a partition, it was flaky around the time I needed to install Ubuntu, so I re-formated the HD, one with HFS+ and the other half as free space.

2.) This is new to me, but I've been out of the Linux scene for sometime now.

3.) Linux in itself will help you learn about computers in general, as a user of a Linux distribution, you are more involved with your computer. The only difference between a Linux kernel on the PPC, SPARC, x86, etc.. is the low level processes. Everything else is indifferent, with very few exceptions (Installation of the initial distribution for example)

4.) A repository is a only server with software (mostly free & opensource) for your OS. Usually a interface (for Ubuntu it's APT) makes use of it for installing, and upgrading your software packages.

5.) Probably, but most software is cross-platform, so most of what runs on x86 will run on PPC with no problem, providing it's compiled on the target platform.

6.) [https://wiki.ubuntu.com/iMacG5revC](https://wiki.ubuntu.com/iMacG5revC)

7.) [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

8.) No problem.

Mind you I have no experience with Bluetooth or Airport Extreme.

---

### Post by SycloneMedia on 2007-05-02
Kubuntu is an excellent choice. When I used Ubuntu (Gnome) on my G4 Powerbook, it was a decent experience, but "something" was missing. Then I noticed that most of the apps I liked and will use were KDE, so I installed Kubuntu and will never go back to Ubuntu. If you are good with computers and like to customize the "feel" of your computer, you'll love Kubuntu. I wish more people (especially Mac users) would try Kubuntu, I think it feels much better coming from Mac than Ubuntu. I have a dual-boot (Mac/Kubuntu) G4 Al Powerbook.

Anyways...

1. I wrote specific, detailed instructions on how to set-up dual-boot Mac and *buntu, with a shared partition as well. Are you willing to erase your hard drive and reformat? Let me know if you are, I'll post the instructions for you, or better yet, search my couple posts and I've already posted the instructions.

2. It should shut down right, unless if you're talking about when shutting down from the Live CD. In that case, yeah, it does that, don't worry about it.

3. Yes, learning linux on any distribution, will teach you linux. Learning the terminal/command line is the way to learn linux. All the things you do, expect machine specific settings are the same from PPC to x86. Only the actual packages (which are the program or application files) are different in some cases.

4. You get all your packages from repositories which are specific locations (servers) which hold the specific packages for your particular install. So there is a server that holds Edgy packages which your install points to when it looks for or updates the packages, and there is another one for Feisty, etc... There are "official" repos from Canonical which can only offer certain packages, and there are third-party ones for other packages. You can point your install to "add" repos to your list to have access to whatever packages you may need.

5. Most apps which are for Ubuntu, will run on PPC or x86. Remember, you are running linux as an OS, and the program is written for linux. In some cases however, the program MAY be platform-specific and they will always state that in their documentation. There are a few out there, ie, Wine. What I did was search for apps on google or whatever and read through other users favorite ubuntu apps lists... I was turned on to some good apps that way.

6. For Feisty, all you have to do is download/install the package named "bcm43xx-fwcutter" and then do a few more steps... there's a few threads in this forum.

7. I don't have experience with those.

8.:guitar:

---

### Post by SycloneMedia on 2007-05-02
Oh yeah, and when you do install packages and stuff from the terminal, always use "aptitude" not "apt-get"...

when you see instructions anywhere to type: "sudo apt-get......", just use aptitude instead like "sudo aptitude.........".

They both do the same thing (look up the repositories and download/install/remove packages) for you, but aptitude keeps a list of package dependecies (which are other packages that are necessary to co-install with the package you are requesting) and if for some reason you need to uninstall that package for example, it will uninstall whatever came with it as well automatically (unless it's being used by something else). Apt-get doesn't do that automatically. The other reason for using aptitude exclusively is that you can't get something with apt-get and then expect aptitude to cleanly remove it all for you.

:popcorn:

---

### Post by megabenman on 2007-05-02
Thanks DJ_Max and SycloneMedia.  Hopefully with your answers I can get Kubuntu running.  I don't mind reinstalling OS X and losing everything.

Just a few more questions that I just remembered a little while ago.

1.  Besides the GUI, are their any other differences between Ubuntu and Kubuntu?  If I want to make Kubuntu look like Vista or OS X, will it be harder than on Ubuntu?

2.  I didn't get the extended warranty when I bought my iMac G5 1.5 years ago and now I'm paying the price....  Two months ago my computer started shutting off randomly, and I got it repaired for free with one of apple's worldwide programs, made for fixing 2nd Gen iMac G5's power supplies.  Then, a month later, the same problem happened again and I got it fixed.  I got the computer back yesterday.  Because I don't have the extended warranty, they will keep fixing it for free, but not permanently it seems, and they won't give me a new computer after 3-4 repairs for the same problem, like they do with computers under warranty.  So, my question is, if I take my computer in, and they see Linux on it, will they not fix my computer?  I'm not sure they look at my harddrive, since both times I sent it in everything was intact (except the first time I got it back sometimes changed the brightness).  All I know is that they do make sure it works before they give it back to me.

3.  When a program says you have to compile it, how do you do that?  I know what compiling is but I don't know how to do that if I'm just given random source code.

4.  If I screw up, can I just put the OS X install CD into my computer?  Will it fix everything completely?

---

### Post by stmiller on 2007-05-03
> **DJ_Max said:**
> If you really want to get a grip on Linux, you should mess around with Ubuntu's kernel, or at least read up on it. Since most people confuse a distribution with Linux.



What?!?!?! You don't need to mess with the Linux kernel to understand or learn Linux.

> 

6.) [https://wiki.ubuntu.com/iMacG5revC](https://wiki.ubuntu.com/iMacG5revC)



That wiki is out of date, and in all counts wrong. I think I will try to remove it, or at least edit out the wrong information.

And airport extreme works now with Feisty. Just apt-get install bcm43xx-fwcutter

---

### Post by SycloneMedia on 2007-05-03
> **megabenman said:**
> Thanks DJ_Max and SycloneMedia.  Hopefully with your answers I can get Kubuntu running.  I don't mind reinstalling OS X and losing everything.

Just a few more questions that I just remembered a little while ago.

1.  Besides the GUI, are their any other differences between Ubuntu and Kubuntu?  If I want to make Kubuntu look like Vista or OS X, will it be harder than on Ubuntu?

2.  I didn't get the extended warranty when I bought my iMac G5 1.5 years ago and now I'm paying the price....  Two months ago my computer started shutting off randomly, and I got it repaired for free with one of apple's worldwide programs, made for fixing 2nd Gen iMac G5's power supplies.  Then, a month later, the same problem happened again and I got it fixed.  I got the computer back yesterday.  Because I don't have the extended warranty, they will keep fixing it for free, but not permanently it seems, and they won't give me a new computer after 3-4 repairs for the same problem, like they do with computers under warranty.  So, my question is, if I take my computer in, and they see Linux on it, will they not fix my computer?  I'm not sure they look at my harddrive, since both times I sent it in everything was intact (except the first time I got it back sometimes changed the brightness).  All I know is that they do make sure it works before they give it back to me.

3.  When a program says you have to compile it, how do you do that?  I know what compiling is but I don't know how to do that if I'm just given random source code.

4.  If I screw up, can I just put the OS X install CD into my computer?  Will it fix everything completely?

Yes, if you can wipe your HDD and re-install, do follow my instructions in my previous posts on how to manually partition for dual-boot. I only have a handful of posts so far so it won't be hard to find. :)

1. Ubuntu is Gnome desktop which is written in C, Kubuntu is KDE desktop which is written in C++, so there are fundamental differences in how things run, transparent as they are. Ubuntu is not recommended for those who like to configure/customize their desktops too much, although you could opt to install Beryl/Emerald to theme. Still though, Kubuntu is much more customizable (from my experience) without having to use a themer, which you still could if you wanted. From your comments, I'd suspect you'd enjoy Kubuntu. Other than that, some apps are made/optimized for one or the other. You could run those apps on either install with the other install's appropriate library, and I've heard the performance hit is negligible in most cases. You can switch back and forth by just logging out and logging into the other (assuming you install the other desktop first.)

2. You know, they'd probably love to have a reason to deny you service and blame all the problems on the "alien" operating system you have on there... but why don't you call in anonymously and just ask them if it's a problem.

3. Compiling is something I haven't done yet... I haven't had to install anything that requires it. I've read a few notes on how to though... just search "how to compile in ubuntu".

4. Yes! It'll once again wipe the entire hard drive and clean install your osx system if you want.

---

### Post by 3rdalbum on 2007-05-03
I think the easiest way to describe things is like this:

If a program is open-source, it's likely to be able to compile on PowerPC as well as on x86. If it is closed-source, it almost certainly won't be available for PowerPC.

Of course, some open-source software doesn't work on PowerPC - Songbird and Xara are two. But mostly they do. The repositories contain software that has been compiled for PowerPC, so you don't need to worry about compiling really.

If you do want to compile, it's not too tough once you've done it a couple of times.

Basically, open a terminal into the directory that contains the source code. Run the command:

```
./configure
```

The configure script will run and tell you if you're missing anything, then you go to the repositories and download the thing you're missing, then run Configure again. For instance, if it says the following when installing a video playing app:

```

Looking for Cairo... not found.
Please install the Cairo development headers.

```

You would go to the repositories, do a search for "cairo" and you'd find "libcairo2" and "libcairo2-dev". You'd install both of them - the regular package so the compiled program will run, and the -dev package so the program will compile. Once they're installed, run ./configure again.

When the Configure script runs successfully to its completion, then run the command "make". This actually compiles it. Finally, once that is done, run "sudo checkinstall" which creates a Debian package from the compiled program (you need to install the checkinstall program first).

That's it. Well, there can be more to it - some programs can be customised by passing additional parameters to the Configure script, which is great for bleeding-edge features among other things. But that's usuallly all you need to know.

---

### Post by DJ_Max on 2007-05-03
> **stmiller said:**
> What?!?!?! You don't need to mess with the Linux kernel to understand or learn Linux.


How do you figure that? How can you learn Linux without learning Linux. Linux is nothing more than a Modular monolithic kernel, with basic functions. Whether it's version 2.6, 2.8 or whatever, Linux is the kernel. Just because you use Ubuntu, doesn't mean you know Linux, you just know how to use certain software, GNOME, OpenOffice, etc.. Knowing Linux involves using the actual kernel, writing drivers, extensions and such.

The correct statement would be "You don't need to mess with the Linux kernel to understand or learn **Ubuntu**.

---

### Post by megabenman on 2007-05-03
This post is mostly aimed at SycloneMedia, but if another person knows they answer then please post!

SycloneMedia, I read your guide and I have a few questions (hooray, more questions...)

1.  Before I read your guide I tried to resize my OS X partition from 232 GB to 200 GB with QTParted.  It told me it was mounted (I was using the Kubuntu CD, so that doesn't make sense) and failed.  OS X still works but for some reason it thinks that my HDD is only 200 GB.  QTParted says that my OS X partition is 232 GB, and so does disk utility and the iPartition demo.  If I use your guide, will the computer realize that it is 232 GB again?

2.  When you say boot with your OS X CD, you mean the two DVD's that came with your computer, right?  OS X Install disk 1 and 2?  If so, I use install disk 1, right?

3.  When I installed OS X, I don't think it asked me what partition to install it on.  Will it automatically install on the biggest partition (which will be the OS X partition) or will it give me options?

4.  You say to use GParted, but since I'm using Kubuntu, will QTParted work as well?  Are there any differences that mean I have to use different instructions?

Thanks again.  I ask too many questions.

Edit:  One last question.  Do I need to change the permissions for Macintosh HD?

---

### Post by SycloneMedia on 2007-05-04
Hey, questions are not a problem... that's what the forums are here for!

1. Yes, Whenever you erase/wipe your entire drive, it will see all space again. You can't ever "lose" actual physical hard drive capacity.

2. Correct. Yes, disk 1, and then use Disk Utility from the menubar.

3. If you have no partitions, it won't ask you. If you have partitions and only one partition is hfs-partitioned, it should ask but it will only allow you to install on that partition or if you want to wipe the entire drive and clean install.

4. QTParted should be fine. However, since Feisty does not come on a Kubuntu CD for PPC, use the Ubuntu CD (which would have the GParted), and then just install Kubuntu on top.

5. No you don't need to change anything.

Feel free to keep asking... let's make it work for you! I'm on here learning as much as I can too.

---

### Post by megabenman on 2007-05-05
Ok, now I have a problem.  I realized that there wasn't much point to manual partitioning, because I didn't have a bootstrap error message.  So, I booted into the install CD, and repartitioned differently.  I gave 180 GB to OS X as an HFS+ filesystem, and then made the other 50 GB free space.  I installed OS X, which worked fine.  Then, I booted using the Kubuntu Install CD (which, yes, there is a PPC Version.  In one of the sticky threads in this forum it gives you a link to where to download it).  I clicked install, and I told it to install to the largest free space.  Then, I waited patiently for the progress bar to load.  Wating.... Waiting.... After maybe 45 minutes it finished and said the installation was complete, and how I should restart my computer and bla bla bla.  I looked at QTParted and a whole bunch of new partitions were there, two with Tux the Penguin next to them.  So I turned off the computer, and turned it back on.  It booted into OS X.  I restarted again and it keeps booting into OS X.  Why doesn't it give me an option to go to Kubuntu?  Did yaboot not install right?  Do I need to press a key down?


Edit:  Ok, I kinda figured it out.  If you hold down the option key at startup, then the fans will go to their max and you will get this grey screen.  It will have two arrows, one that looks like an enter error and one the points right.  Then, there are two squares side by side.  One shows a picture of a harddrive with the Finder/Mac Face on it, and the other shows a harddrive with Tux on it.  If you click the one with Tux, it will open yaboot, which lets you pick Linux, Max, and another option I forget.  Then, when it reaches the Kubuntu screen with the loading bar the fans slow down and become normal.  But that's not right... Isn't it supposed to run yaboot on startup, without having to hold down the option key?  How do I change this to make it boot yaboot instead of OS X?

---

### Post by SycloneMedia on 2007-05-05
megabenman:

Thanks for the Feisty Kubuntu CD tip... it must be new (5 days ago.) Awesome... I'm going to download it now. I won't have to sort through the Ubuntu apps any longer.


Regarding your boot sequence...

You didn't use the actual manual partitioning method and instead chose the free space way, it configured it in it's own way, and you _must have the bootstrap partition first_ for the computer to recognize it.

Try it with my instructions, it'll work the way you want with yaboot starting up. The partitions you need to think about before hand. Write them down like in my guide You'll need the first partition for the bootloader (yaboot), 1 partition for your main linux system, 1 partition for the linux swap (which usually should be twice the size of the ram in your computer), 1 partition for your main osx system, and if you want to share your music or whatever files then 1 partition to share. So split up your hard drive space accordingly. Follow my guide and you'll get your yaboot to start! :)

---

### Post by megabenman on 2007-05-05
Well, I was going to use your guide, but I decided not to when I couldn't find any flags in QTParted.  Stupid question but can I just boot into Ubuntu and change the flags, then boot into kubuntu and install it instead?

---

### Post by megabenman on 2007-05-05
Ok, there is a huge problem.  Disk Utility only has a few formatting options.  It has Mac OS X Extended (Journaled), Mac OS X Extended, Mac OS X Extended (Case Sensitive), Mac OS X Extended (Something I forget), Unix File System, and Free Space.  How am I supposed to make the bootstrap partition Mac OS X Standard if there is no option for it?  Did you have an option for it?

---

### Post by SycloneMedia on 2007-05-05
> **megabenman said:**
> Well, I was going to use your guide, but I decided not to when I couldn't find any flags in QTParted.  Stupid question but can I just boot into Ubuntu and change the flags, then boot into kubuntu and install it instead?

Yes, good idea, you can boot into Ubuntu, set up the partitioning flags and apply everything, then just cancel out, boot with Kubuntu and you should be good.

---

### Post by SycloneMedia on 2007-05-05
> **megabenman said:**
> Ok, there is a huge problem.  Disk Utility only has a few formatting options.  It has Mac OS X Extended (Journaled), Mac OS X Extended, Mac OS X Extended (Case Sensitive), Mac OS X Extended (Something I forget), Unix File System, and Free Space.  How am I supposed to make the bootstrap partition Mac OS X Standard if there is no option for it?  Did you have an option for it?

Oh, OK, then just use the regular Mac OS X Extended.

Yes, I had an option for Standard, then again I have the Jaguar/Panther install set... probably with Tiger they discontinued support for it. But regular Extended should work then. I made my guide from what definitely works for sure. I'll change it to include Extended after it works for your install, which I don't see why it shouldn't.

EDIT: I had used Standard because I originally read somewhere to format bootstrap with that. It worked, but that's not to say Extended won't. We'll see. However, Extended (Journaled) supposedly will NOT work for sure since Linux is not supposed to be able to deal with the journaling.

---

### Post by megabenman on 2007-05-05
Ok, so then I'll just make everything OS X Extended, except for the OS X partition, which will be OS X Extended (Journaled).

I'll tell you what happens.

---

### Post by megabenman on 2007-05-05
Ok, I just finished partitoning and reinstalling OS X.  Now, on my desktop, it shows all four partitions, not just Macintosh HD.  I'm guessing this is because it's not journaled.  It this supposed to happen?

---

### Post by megabenman on 2007-05-05
I give up.  I did everything the guide said.  I made the first partition the bootstrap, the second the swap, and third linux, and the fourth OS X.  I installed OS X and the put the proper flags and formats and used manual partitioning with the install.  But still, it continues to load OS X, and not Yaboot.  What is going on?

---

### Post by DJ_Max on 2007-05-06
I've never had to do anything but make two partitions in Disk Utility, one HFS+ for OS X, and one Free space for Linux. Because when you install Linux, it will make new paritions with whatever free space you have.

In OS X run
```
echo L | sudo pdisk
```

You weren' t booting Yaboot, because Apple's bootloader was probably ahead of Yaboot, when you really no longer need Apple's bootloader. OpenFirmware searches for the first bootable partition on the disk, in your case, Apple_Bootstrap partition. You can easily change the order of the partitions. I believe Ybin should do this, or at least "bless" your system folder. If you changed something in yaboot.conf, you must run the command
```
ybin -v
```

---

### Post by megabenman on 2007-05-06
echo L | sudo pdisk gave me this:

```
Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:          Apple_Free Extra                   262144 @ 64        (128.0M)
 3:     Apple_Bootstrap Apple_HFS_Untitled_1   1835008 @ 262208    (896.0M)
 4:          Apple_Free Extra                   262144 @ 2097216   (128.0M)
 5:     Apple_UNIX_SVR2 swap                  40131608 @ 2359360   ( 19.1G)
 6:          Apple_Free Extra                   262144 @ 42490968  (128.0M)
 7:           Apple_HFS Apple_HFS_Untitled_3  82361440 @ 42753112  ( 39.3G)
 8:          Apple_Free Extra                   262144 @ 125114552 (128.0M)
 9:           Apple_HFS Apple_HFS_Untitled_4 363020456 @ 125376696 (173.1G)
10:          Apple_Free Extra                       16 @ 488397152

Device block size=512, Number of Blocks=488397168 (232.9G)
DeviceType=0x0, DeviceId=0x0


Partition map (with 512 byte blocks) on '/dev/rdisk1'
 #:                type name                  length   base     ( size )
 1: Apple_partition_map Apple                     63 @ 1       
 2:  Apple_Driver_ATAPI*Macintosh                  8 @ 64      
 3:           Apple_HFS Mac_OS_X            11763576 @ 72       (  5.6G)
 4:          Apple_Boot Apple Hardware Test    94746 @ 11763648 ( 46.3M)
 5:          Apple_Free                           10 @ 11858394

Device block size=512, Number of Blocks=11858404 (5.7G)
DeviceType=0x0, DeviceId=0x0
Drivers-
1:   4 @ 64, type=0x701

```
I'm pretty sure 3 is yaboot, 5 is swap (which doesn't work), and 7 is the actual Linux system.  9 is OS X, and I have no idea what 1 is, maybe the apple bootstrap?  Also, dev/rdisk1 I think is the OS X Install Disk #1, it just happened to be in my computer when I was running the command.

Also, ybin -v didn't work for me in OS X.  This is what it spit out in Kubuntu:

```
ybin: /dev/sda3: Permission Denied
ybin: /dev/nvram: Permission Denied
Warning: nvram will not be updated
```

What should I do?  Thanks.

---

### Post by DJ_Max on 2007-05-06
Sorry,
```
sudo ybin -v
```

From looking at your dump

1 is the actually Apple map, which is always 1.
2. just free space
3. Apple bootloader
4. free space again
5. is a parition for Linux, even though you named it swap, I doubt you have a 19Gig swap size, so I'm guessing that this is your Linux filesystem.
6, 8 & 10 are free space, yet again.
7 is a OS X parition, sine Linux doesn't boot in HFS+
9 could also be  OS X

You went though too many steps to dual boot as your setup looks way to complicated. When you go into Ubuntu, do a 
```
cat /etc/fstab
```

My iMac disk looks like
```

Top level command (? for help): /dev/rdisk0  map block size=512
   #:                 type name                 length   base     ( size )
   1:  Apple_partition_map Apple                    63 @ 1       
   2:      Apple_Bootstrap boot                   1954 @ 39100152
   3:            Apple_HFS Apple_HFS_Untitled_2 38820536 @ 262208   ( 18.5G)
   4:           Apple_Boot eXternal booter       17408 @ 39082744 (  8.5M)
   5:      Apple_UNIX_SVR2 Linux              37562501 @ 39102106 ( 17.9G)
   6:      Apple_UNIX_SVR2 swap                1500753 @ 76664607 (732.8M)
   7:           Apple_Free Extra                262144 @ 64       (128.0M)

```
3 is apple bootloader, but it's not in use. 4 is yaboot

---

### Post by megabenman on 2007-05-06
No, actually partition 7 is my linux system, and 5 is the swap.  I don't know why it's called HFS, but for some reason it is.

Anyway, I'm going to reinstall everything, and just install Linux using free space to see if it can be less complicated for you to help me.

---

### Post by SycloneMedia on 2007-05-06
> **megabenman said:**
> Ok, I just finished partitoning and reinstalling OS X.  Now, on my desktop, it shows all four partitions, not just Macintosh HD.  I'm guessing this is because it's not journaled.  It this supposed to happen?

Yes, anything that is a HFS partition and mounted will appear on the desktop. You can edit your View or Finder preferences if you don't want to see them.

---

### Post by SycloneMedia on 2007-05-06
> **megabenman said:**
> No, actually partition 7 is my linux system, and 5 is the swap.  I don't know why it's called HFS, but for some reason it is.

Anyway, I'm going to reinstall everything, and just install Linux using free space to see if it can be less complicated for you to help me.

Whoa... looking at your partition table, it looks out of control. 

1. My first question is where in theh world are your "ext3" partitions??? Your Linux partitions should not be showing up as Apple formats. After you readied the Linux partitions as HFS Extended, did you go into GParted and reformat them to ext3? They should only be HFS until you go into GParted so that GParted can recognize them. You have to apply the changes after you have them selected to be "ext3."

2. The other problem that can happen, and I experienced this, is that the OS X Disk Utility will take any "free space" you have allocated and try to throw it all around and in between your legitimate partitions. It's a possiblity, if you had a large amount of free space left over during your disk utility partitioning. I had to redo my partitions a bunch of times to get that part right.

3. The HFS Extended might have a caused a problem?

I tried to post my partition table, but my konsole didn't recognize "pdisk" so I can't show you what my map looks like yet.

There's something that's being overlooked it seems. The steps in the guide I used at least about a half dozen times with success.

Hmm....

---

### Post by SycloneMedia on 2007-05-06
Just to make sure we're talking about the same guide too.... I'll just repost it here so it's easier to reference:

> It took me a couple days of online research and about 7 complete wipe/reinstalls to get my Powerbook to dual boot OSX and Ubuntu. Don't give up...

If you are not willing to, or can't erase your hard drive and re-partition it, then letting Ubuntu install itself with the available freespace might be easier.

If you can erase and start from scratch, here's what you need to do:

1. Don't forget to offload and back up all the data that you want to keep.

2. Boot up from your OSX System CD (holding down C) at bootup, and open up Disk Utility, select your hard drive and the 'partition' tab.

-You can divy up your space however you want, but you need at least 4 partitions. (bootstrap, linux swap, linux system, osx system) You can add any other partitions you need depending on your hd size. With the exception of the bootstrap partition, make ALL the others in HFS+ (extended). More details below. Don't forget to write down how many partitions and what sizes they are... try to stagger the sizes a little because you'll need a way to identify the partitions later WITHOUT relying on the names.

-The very first partition MUST be the bootstrap and it can be a very small partition. Now you'll find posts that say make it "100 MB" or so, but I just couldn't get Disk Utility to go that small and actually do it. So I made it a 1 GB partition. IMPORTANT: THE KEY IS TO MAKE THIS BOOTSTRAP PARTITION "HFS" (standard), NOT "HFS+" (extended).

-The rest of the partitions should be HFS+. You'll change the Linux partitions later.

3. Install OSX onto the partition you designated for it. You must install OSX first, Ubuntu second. I've found that if you install or reinstall OSX after Ubuntu is already on it, it will take over the bootstrap and default boot into only OSX and designate itself as the startup partition. Not what you want.

4. Boot up with Ubuntu CD, and before you start the Ubuntu install, we need to change some things...

-Open up the GParted (gnome partition editor) from the System menu. The layout of the partitions WILL look different, don't worry. You need to visually identify which partition is which by the available sizes, etc... Shouldn't be too hard if you wrote down the partition sizes you created. The names will not show up.

-Select the bootstrap partition you created earlier. The ONLY thing we need to do here is set a "boot" flag. You'll see the appropriate menu to assign flags, and select "boot". Apply the changes (click apply). That's it, your bootstrap should be ready for action.

-Now select the rest of your linux partitions (swap, system, etc) and choose to reformat them to "ext3" format using the menus. Also, go ahead and assign a flag for your linux swap partition as "swap" using the same menus as for the bootstrap. Apply changes. We're ready to roll.

5. Install Ubuntu with manual partitioning... do the normal question and answer things and when it opens up GParted again, don't change or do anything as we've already set it up... just continue to that last step. Here it should automatically have selected your swap partition as the designated swap, and make sure the linux system partiiton you created is designated as the main install partition. They should both be checked off for reformat, no problem.

Now when you hit continue, or install or whatever, it should go ahead and have no problems with the bootstrap and you'll be good to go...

When you start up your computer, it should give you the option to boot into either, and the default will be linux (if neither is selected). There's good threads around here on how to change that to default into osx if you need.

The only problems I've had is with occassional kernel panics during bootup into both, and that could be because I have bad ram, or something else.

Happy Dualing!
:guitar:

---

### Post by megabenman on 2007-05-06
> **SycloneMedia said:**
> Whoa... looking at your partition table, it looks out of control. 

1. My first question is where in theh world are your "ext3" partitions??? Your Linux partitions should not be showing up as Apple formats. After you readied the Linux partitions as HFS Extended, did you go into GParted and reformat them to ext3? They should only be HFS until you go into GParted so that GParted can recognize them. You have to apply the changes after you have them selected to be "ext3."

2. The other problem that can happen, and I experienced this, is that the OS X Disk Utility will take any "free space" you have allocated and try to throw it all around and in between your legitimate partitions. It's a possiblity, if you had a large amount of free space left over during your disk utility partitioning. I had to redo my partitions a bunch of times to get that part right.

3. The HFS Extended might have a caused a problem?

I tried to post my partition table, but my konsole didn't recognize "pdisk" so I can't show you what my map looks like yet.

There's something that's being overlooked it seems. The steps in the guide I used at least about a half dozen times with success.

Hmm....
1.  I did format them as ext3, using QTParted (yes, I clicked commit).  I guess it's just the names they were given.

2.  Yes, I'm using the guide you posted.

---

### Post by DJ_Max on 2007-05-06
Looking at your guide why do you need 4 partitions? 

I've just poped in the OS X install disk, created one partition named 'osx' with HFS+ for OS X. Mind you, Disk Utility will create the needed Apple bootstrap. I then left the rest "free space", which isn't really a partition.

After I installed OS X, I booted my Linux disk, and told the automatic installer to use the free space, and it then set up the needed partition (it will basically delete the "free space" and create it's paritions with the space it had used.) The auto installer should set Yaboot correctly.

---

### Post by megabenman on 2007-05-06
Ok, I just finshed reinstalling OS X and Kubuntu (of course OS X first).  Here's what I get with that command:

```
Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:     Apple_Bootstrap untitled                  1954 @ 356515904
 3:           Apple_HFS Apple_HFS_Untitled_1 356253696 @ 262208    (169.9G)
 4:     Apple_UNIX_SVR2 untitled             128943360 @ 356517858 ( 61.5G)
 5:     Apple_UNIX_SVR2 swap                   2935950 @ 485461218 (  1.4G)
 6:          Apple_Free Extra                   262144 @ 64        (128.0M)


```

I can't find yaboot on there.  I know 1 is the map, 2 is apple's bootstrap, 3 is OS X, 4 is my Linux system, 5 is the swap, and 6 is ... free space.  Where's yaboot?  When I restart my computer and hold down option, if I click the picture with the harddrive and tux on it then it loads yaboot.  But I can't see yaboot on the partition map.

---

### Post by megabenman on 2007-05-06
Holy crap!  That sudo ybin -v really worked!  It boots yaboot at startup now!  Thanks guys.

And be ready for a ridiculous amount of questions by me.....

Edit:  Wait... now it doesn't show yaboot anymore.  It keeps booting back into OS X.... How many times do I have to use this ybin command?

---

### Post by SycloneMedia on 2007-05-07
> **DJ_Max said:**
> Looking at your guide why do you need 4 partitions? 

I've just poped in the OS X install disk, created one partition named 'osx' with HFS+ for OS X. Mind you, Disk Utility will create the needed Apple bootstrap. I then left the rest "free space", which isn't really a partition.

After I installed OS X, I booted my Linux disk, and told the automatic installer to use the free space, and it then set up the needed partition (it will basically delete the "free space" and create it's paritions with the space it had used.) The auto installer should set Yaboot correctly.

I don't think Disk Utility creates a bootstrap that Ubuntu can use. When you use the free space option, I think it sets it up that you have to use the option key to select. Plus, if you go into the manual partitioning option, it'll tell you that there is no usable newworld bootstrap.

Not sure who you are directing your question of 4 partitions at... me or megabenman?

If you're asking me, there's a whole lot of reasons why you would want to set up many partitions and use the manual partitioning during installation. It gives you way more control over your physical system setup.

One reason is disk access and speed. Another is fragmentation and such. Another is system software upgradability. It's very easy to do (once you get the hang of it) and the rewards are nice.

By default, you absolutely have to have a minimum 4 partitions (whether YOU set them up, or let the Ubuntu installer do it).... Your OSX partition, your bootloader partition, your Linux partition, and your Linux swap partition. In my system, I also have an OSX swap partition for my Photoshop and Illustrator scratch discs. You don't want to have to use your main system partition for that if you can help it. Manually, you can set the size of the Linux swap (to twice your ram) instead of relying on the installer to do it.

Also, manually, you can set the first partition as your bootloader (yaboot).

Lastly, I set up another (the largest) partition as a shared media volume for my music, files, documents, photos, etc so that I can share those between OSX and Linux and keep the system partitions alone.

The guide works great. I wish I could help megabenman troubleshoot in person to get to the bottom of his trouble.

megabenman: pm me if you want to give it a shot over the phone tomorrow (Monday).

---

### Post by DJ_Max on 2007-05-07
I know the reasons for multiple partitions, I was just wondering why you needed to do this in Disk Utility, when the Ubuntu installer does this.

One thing about Disk Utility, Apple changes it so much, each versions has different options than the last, which makes it hard to write a guide because what may work with 10.2, may not work with 10.4 and so on.

With your problem, it seems like OS X is voiding any changes you make to the boot sequence, as OS X really doesn't like other OS's ahead of it's own. Sorry I can't be of more help, I haven't dabbled with computers like I should in a while, college has been kicking my butt.

---

### Post by megabenman on 2007-05-07
Well right now I ran your ybin command again and it seems to be working.  I've tried restarts and shutdowns from both OS X and Kubuntu and it still loads yaboot.  In fact this is my first startup in 7 hours (school) and it booted up yaboot again.  I think it is working, but I hope something won't go wrong.

---

### Post by stmiller on 2007-05-07
> **DJ_Max said:**
> How do you figure that? How can you learn Linux without learning Linux. Linux is nothing more than a Modular monolithic kernel, with basic functions. Whether it's version 2.6, 2.8 or whatever, Linux is the kernel. Just because you use Ubuntu, doesn't mean you know Linux, you just know how to use certain software, GNOME, OpenOffice, etc.. Knowing Linux involves using the actual kernel, writing drivers, extensions and such.

The correct statement would be "You don't need to mess with the Linux kernel to understand or learn **Ubuntu**.

Think about the parent poster. He said, "I want to learn about Linux." Followed by questions like, what is a repository. 
You say, "you must get inside the Linux kernel." I think you are misunderstanding the perspective of the poster. He is new to Linux. A better reply may be, 'try Gnome and KDE, try K3B, synaptic, grip, banshee, etc.'

No one needs to write kernel drivers to 'understand Linux.'

I think after messing around with Ubuntu a good way to learn Linux if you have the time is to go through a Gentoo install, following their docs. This lets you set up an install from the ground up, creating your own fstab and such. Good times... :)

---

