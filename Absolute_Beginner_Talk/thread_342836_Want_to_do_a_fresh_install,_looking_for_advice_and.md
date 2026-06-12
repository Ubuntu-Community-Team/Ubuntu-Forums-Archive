---
title: "Want to do a fresh install, looking for advice and tips please."
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by stoer on 2007-01-20
Hi all,
ok, i've been trialing Ubuntu for a few months now and i like it very, very much.
Good community, good software and an OS that almost meets all my needs.

Present set up:
Jewel laptop
intel 1.6 GHz mobile processor. 1.5 Gb ram
80Gb hd:  Partitioned. Windows  16 Gb,  windows data 30 Gb, FAT32 10Gb, The rest for Ubuntu.
Intel pro wireleless 2200BG: Realtek RTL8139/810 ethernet NIC: ATI  mobility Radeon 9700 256Mb.

I've been trawling the forums for weeks looking at this, there is loads out there but so spread out, no real 'how to's' or definitive 'must do's' / 'Don't do's'.

What i want to  do is the following.
Reinstall, why? Because...

1) Windows is bloated and needs refreshing. I can lose alot of things presently installed that will be replaced with Ubuntu/Kubuntu also making a smaller partition for Windows to use than the present setup.
2) I've been experimenting with Ubuntu and various apps for more than 3 months.  I've had a  go at installing all sorts of stuff, tried alot of different software trying to find what i liked and didn't like.  generally experimenting and enjoying myself and I now have a feeling that my Ubuntu system is also unecessarily bloated, theres a fare few things i could now do without.

Windows has to stay.
I download from usenet (alot) using Newsleecher (doesn't  work in wine/crossover office) and i can't find a replacement in linux that comes even close. (HELLANZB is great but not completely reliable/sparse on functions). GAMES - my kids are 4 and 1, my boy lives and breathes games, linux offers too little or has still too many problems to make this a real prospect at this point. ( I am also way too inexperienced to get alot of stuff to work! ](*,) ).
Webcam - just doesn't work well in Ubuntu - Gnome/KDE. (Driver & manufacturer issues not a linux problem)

Questions:
1) Is there a way of keeping some of my settings, is it worth for example making a copy of my home folder? Or is it better to go with a complete fresh install (i'll be keeping my personal stuff, pictures and doccuments etc.)  Guess what i'm asking is, is there a way of reinstalling and keeping some of the installed stuff that i now have and still want without having to redo the whole thing over; ati drivers (working), mounts, mulitimedia etc.

2) If in the future i need to reinstall again, and i'm assuming this will be the case, what can i do in future to ensure that each new install is as painless as possible - Home on a separate partition? Personal settings (can these be saved and reinstated on a new install?) also in a special folder?

3) Edgy or not? Is it worth trying now or is it still better to wait for the next release? I can't quite make my mind up there.

4) The best set up, partitions for ubuntu - size? special (home on it's own), others?

5) How do you do all this?  Starting  from fresh each time seems such a long winded process.  In windows, i'd make an image from a clean install with the basics all installed and ready to use and buildon that, in Linux?

Any tips and advice will be really appreciated, i'd like to do this well and as efficiently as possible.  The system i now have works (if it works - why f**k with it... is something i hold  dear, but i still know the difference between works and works well :lolflag: )

I know i'm asking alot - but i know that the most people here on the forums are doing this regularly, (=D> ) my question is thus, how?
Please keep it relatively simple and understandable.

---

### Post by rai4shu2 on 2007-01-20
You should try the latest beta version of Pan. [http://pan.rebelbase.com/](http://pan.rebelbase.com/)

1) A DVD writer would be ideal for that purpose. You can usually find old deb files in /var/cache/apt/archives for later reinstall. To install them later, you simply go to a console and type:

sudo dpkg -i <filename>.deb
sudo apt-get -f install

2) Your /home folder really ought to be on a separate partition. That way, you can avoid having to format it any time you reinstall. Personal settings are usually in the /home folder (for example /home/yourname/.mozilla usually has your Firefox settings).

3) That's where a separate partition for /home really comes in handy. Try it, if it doesn't work out for you just clean install Dapper again.

4) I take all the space I'm willing to use for Ubuntu and divide it into thirds. 2/3 for /home and 1/3 for the / partition, leaving 2 GB for swap. Divide it up however you want.

5) In Windows I also prefer to clean install, but maybe that's just me. :)

You might want to write some of these helpful things down if you aren't already.

---

### Post by stoer on 2007-01-20
> **rai4shu2 said:**
> You should try the latest beta version of Pan. [http://pan.rebelbase.com/](http://pan.rebelbase.com/)

1) A DVD writer would be ideal for that purpose. You can usually find old deb files in /var/cache/apt/archives for later reinstall. To install them later, you simply go to a console and type:

sudo dpkg -i <filename>.deb
sudo apt-get -f install

2) Your /home folder really ought to be on a separate partition. That way, you can avoid having to format it any time you reinstall. Personal settings are usually in the /home folder (for example /home/yourname/.mozilla usually has your Firefox settings).

3) That's where a separate partition for /home really comes in handy. Try it, if it doesn't work out for you just clean install Dapper again.

4) I take all the space I'm willing to use for Ubuntu and divide it into thirds. 2/3 for /home and 1/3 for the / partition, leaving 2 GB for swap. Divide it up however you want.

5) In Windows I also prefer to clean install, but maybe that's just me. :)

You might want to write some of these helpful things down if you aren't already.


Even better, just copied it to my Home file ;)

PAN - tried an earlier copy of it without NZB support, the new version looks spiffy!
Newsleecher has 'supersearch of course, hard to replace that- saves reading ten gazillion headers in from a large group (film/music) - but so does a nzb.  I'll give it another shot.

When installing - how do you set up the option for a seperate home partition?

A clean install of windows (from an image) super easy, A clean install of Ubuntu means setting 'everything' up again - recompiling ati drivers, re-mounting partitions, etc. Nice if you could create an image of your ready to use (preconfigured) setup... would save a big chunk of time.  Doesn't help of course when installing a new version, unless you can import such settings into said new version.  Being new to this it just seems to take so long, but then that's what being new is all about i guess, do it 10  times and the experience counts :) 

Thanks for your tips - their now top on my list.

---

### Post by rccharles on 2007-01-20
> **stoer said:**
> 
4) The best set up, partitions for ubuntu - size? special (home on it's own), others?



I think reinstalling is for windows. Just uninstall the packages you do not want.


You can resize your Ubuntu partition and create a separate partition for the home directories. You can copy all the home directories to this new partition and put in a symbolic link to the new partition.

I have to run, so I'll let you research the details.

Robert
:-\"

---

### Post by Sklasko on 2007-01-20
3. I recommend staying with Dapper and waiting until the next LTS release. Edgy lives up to it's name and has a few too many bugs for me to be comfortable with.

For example, I couldn't ever log out in Edgy without the screen going black and permanently hanging there, so I had to cut the power. Plus the new version of Alacarte crashs randomly and very often. Not to mention the numerous other problems you'll hear about here on the forums from other people.

Of course a lot of these are specific to that user, but none the less, I would stay with Dapper if I was you. Safer and much more stable in my opinion.

---

### Post by rai4shu2 on 2007-01-20
> **stoer said:**
> When installing - how do you set up the option for a seperate home partition?

If you use the "desktop" live CD installer, you just use the "manual" option for partitioning. I usually have partitions set up before this step.

When you get to the next step, there should be a list of your partitions with checkboxes and drop-down menus and such. The drop-down menus let you set mount points like "/" or "/home" or wherever you want a partition mounted.

Make sure you do *not* format your "/home" partition if it already contains data. You will need to format the "/" partition.

---

### Post by deethree on 2007-01-20
is there a way to re-partition your current setup to add a seperate part for /home and then copy all your data there before you re-install?

I have been looking at "downgrading" from edgy to dapper, I'm finding too many issues and I'm just too new to find workarounds by myself. All the ideas I've written down for my next go at it :) 

d3.

---

### Post by stoer on 2007-01-21
Hi all,
many thanks for your replies and advice.
I guess that i've automatically assumed that by planning a 'reinstallation' of windows that a reinstallation of Ubuntu is sort of guarenteed - i expect that a new windows would have all sorts of consequences on my current Ubuntu install, probably more than i want to or am capable of dealing with...
If i reinstall windows, can i then do some preperation for installing Ubuntu from within windows; partition (using either partition magic/Acronis disc manager) setupfor example?
I'll keep to the same sort of setup i have now, just with more room for Ubuntu and less for windows. eg
Partitions:
1-Windows 10Gb / 2-Windows data 20 Gb /3-Fat32 10 Gb (shared data) /4-Ubuntu 10 Gb / 5-seperate partition Home 30Gb  
I guess i could lose the fat32 all together, seeing as i rarely use it now.

Edgy - I guess i can wait untill this is more stable/reliable, Dapper meets most of my requirements still (no sd card support, but windows does).

A fresh Ubuntu install / or a major tidy up. A fresh install still appeals more, and it'll force me to decide one way or the other for KDE or Gnome - currently have both and i don't like  having both menu options intertwined.  I guess it really is a windows thing, but reinstalling still seems easier (with all the work) than combing through my system looking for bits and bobs i don't want.

If i take my time, maybe the next stable release  will be here - mind you that would really be taking my time :roll: , don't think i'm patient enough for that. (Could always go try it out on my pc first - 2 hd's and arround 500 Gb disc room to play with, he he he.)

Anyway, thankyou for the tips so far, more advice and wise words are also more than welcome, I know there's many people out there that have done this x times already and it's always good to hear what worked and didn't.  Appreciate it. Cheers.

---

### Post by rai4shu2 on 2007-01-21
Setting up partitions should be handled by parted/Linux fdisk or something similar. Never use a Windows-based tool for this.

Always do the Windows install first, then reinstall Linux. That way Windows can overwrite the MBR, then Linux can re-overwrite the MBR for GRUB.

---

### Post by stoer on 2007-01-21
> **rai4shu2 said:**
> If you use the "desktop" live CD installer, you just use the "manual" option for partitioning. I usually have partitions set up before this step.

When you get to the next step, there should be a list of your partitions with checkboxes and drop-down menus and such. The drop-down menus let you set mount points like "/" or "/home" or wherever you want a partition mounted.

Make sure you do *not* format your "/home" partition if it already contains data. You will need to format the "/" partition.

Ok...
Let me get this straight.
Reinstall windows and set the necesary patitions (for windows and windows data), and leave it  so.
Reinstall Ubuntu, setting up the partitions from within the live cd set up.  I can from within this set up process decide on size and location of a seperate Home partition. 
question.
if i leave the current home in place and unformatted - then during the set up choose for a new Home partition - i can then copy (old home ) to (new Home) after/or during  the install? maybe easier to copy home to a dvd, right? and copy it over afterwards- erasing (old home) in the process.
I'm sure i'll figure it out ;)

---

### Post by haiku99 on 2007-01-21
I did something similar a few weeks ago and it worked out well and was worth the trouble, reinstalled XP to a smaller partition and did a clean install of Edgy, had been using Dapper.  I definitely prefer Edgy and it has not been any more troublesome than Dapper, but as you know it doesn't go this way for everyone...

---

### Post by Frank Golden on 2007-01-21
> **stoer said:**
> Hi all,
many thanks for your replies and advice.
I guess that i've automatically assumed that by planning a 'reinstallation' of windows that a reinstallation of Ubuntu is sort of guarenteed - i expect that a new windows would have all sorts of consequences on my current Ubuntu install, probably more than i want to or am capable of dealing with...
If i reinstall windows, can i then do some preperation for installing Ubuntu from within windows; partition (using either partition magic/Acronis disc manager) setupfor example?
I'll keep to the same sort of setup i have now, just with more room for Ubuntu and less for windows. eg
Partitions:
1-Windows 10Gb / 2-Windows data 20 Gb /3-Fat32 10 Gb (shared data) /4-Ubuntu 10 Gb / 5-seperate partition Home 30Gb  
I guess i could lose the fat32 all together, seeing as i rarely use it now.

Edgy - I guess i can wait untill this is more stable/reliable, Dapper meets most of my requirements still (no sd card support, but windows does).

A fresh Ubuntu install / or a major tidy up. A fresh install still appeals more, and it'll force me to decide one way or the other for KDE or Gnome - currently have both and i don't like  having both menu options intertwined.  I guess it really is a windows thing, but reinstalling still seems easier (with all the work) than combing through my system looking for bits and bobs i don't want.

If i take my time, maybe the next stable release  will be here - mind you that would really be taking my time :roll: , don't think i'm patient enough for that. (Could always go try it out on my pc first - 2 hd's and arround 500 Gb disc room to play with, he he he.)

Anyway, thankyou for the tips so far, more advice and wise words are also more than welcome, I know there's many people out there that have done this x times already and it's always good to hear what worked and didn't.  Appreciate it. Cheers.
Hi stoer,
 If you are willing to spend a little money this is what I would do.
Purchase a replacement HDD for your laptop and an external (USB) drive enclosure.
You should be able to get this stuff for arount $100.00 or less.
Mount the drive in the enclosure temporarilly. Use Windows diskmanager utility to 
activate your new drive and create a NTFS partition the size you want for XP.
Create a second Fat32 partition for sharing files between Ubuntu and XP. Leave the rest
of drive unallocated. An example partition arrangement is on a 80GB drive 15 GB for XP,
55 GB Fat32 for sharing and the rest unallocated for Ubuntu.

After doing this swap out the new drive for the old one and install XP and any needed drivers to the first partition (the NTFS one). Customize as needed. When you are satisfied
use the Ubuntu CD and install to the largest free space (unallocated). Ubuntu will automatically install itself there and create a small swap partition as well.

See the following for much info about dual booting.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

There is info there about automatically mounting your Fat32 shared partition at boot and placing a shortcut to it on the desktop.

There is tons of other info there as well. Kinda like everything you want to know about dual booting. Herman's tutorial uses the altenate CD but he links you to Aysiu's excelent
how-to for the LiveCD as well.

This is quite similar to the setup I use. The shared partition is accesible from XP and Ubuntu read/write. I have all my MP3's on the shared partition as well as a partimage
image of my working Ubuntu install. If I mess up Ubuntu I can restore this image in a few minutes using the System Rescue CD version of partimage. Making and saving a recovery image using partimage is especially quick when you use the Fat32 shared partition
to save the image to.

On my setup it takes about 5-6 minutes (including booting SysrescCD) to create a complete image of Ubuntu.
It takes about the same amount of time to restore. See the following about using the
version of partimage included with the System RescueCD.

First where to get System RescueCD.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Next info on using partimage from Sysresccd.


[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

and

[http://www.ubuntuforums.org/showthread.php?t=287522](http://www.ubuntuforums.org/showthread.php?t=287522)


When you are done you can place your old drive in the enclosure you bought.
Use XP to delete the partitions on it and reformat it to NTFS or Fat32 and use it as an external storage drive.

---

### Post by stoer on 2007-01-21
Hi Frank

"....

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

First where to get System RescueCD.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Next info on using partimage from Sysresccd.


[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

and

[http://www.ubuntuforums.org/showthread.php?t=287522](http://www.ubuntuforums.org/showthread.php?t=287522)
...."

A Gold Mine - can't thank you enough for these links and tips.
There'senough here to keep me reading for the night, cheers!):P 

A thought....
I have an external USB 250Gb drive from Lacie, use it mostly for backing up the dvd's from the kids, they still find it fun to bite them, skate on them and use them as plates etc. Other than that i store a few window's images there aswell as photo's.
Any way of incorporating this into the equation, other than as an image bank...not really sure if i see any advantages or not.  The biggest draw back is for the wife and my son who would then have to cope with an external drive aswell as the laptop. Bit too much to expect from a 4yr old. (guess i was wondering aout  booting from the usb drive - which works for me but not for the family). 
I like your set up
Windows - fat32 - Uuntu, makes more sense than my win/win data/fat32/uuntu
and naturally i can do the suggested installs all without an extra disc and still use the Lacie 250 as external stoorage - juggle/juggle/juggle - much to mull over methinks....

---

### Post by Aazn on 2007-01-21
I reccomend giving Windows the space it needs, and making 2 partitions for Ubuntu.

[list]
[*]/ - Root, where all your files are stored
[*]/home - Your files and configuration
[/list]

If you do this, then you could switch distributations or re-install Linux without losing all your files. 

You have 80 GB, so do this:

Windows - 16 GB - NTFS
swap - 1.5 GB - LINUX-SWAP
/home - 35 GB - FAT32
/ - 27.5 GB - EXT3

That way you can store your stuff in /home from Windows and Linux both, read it, write it, etc. You can switch operating systems (or upgrade to dapper, check it out, then erase / and go back to Dapper... like I did) without losing your /home.

I reccomend a large swap size... just incase. This is what mine is at.

---

### Post by r4ik on 2007-01-21
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck !

---

### Post by stoer on 2007-01-21
Hi,
aaZn....
like the format, i'll keep it in mind. Thanks alot.

R4ik....
The noobs bible, trust me it sits high up in my bookmarks.

Beste mensen/Good people.
It's late here and time for bed, you've given me alot to look at, think about and naturally, very good advice. Many thanks one and all.  I'm working alot for the next few days, so if i'm not arround to reply thats why.  Please feel free to add more words of wisdom - i really appreciate it, cheers!

---

### Post by rai4shu2 on 2007-01-21
> **Aazn said:**
> /home - 35 GB - FAT32

The downside to FAT32 is that your files in /home would have a 4 GB size limit, plus they will become fragmented in a relatively short period of time. I suggest you use a more standard format (like ext3 or xfs).

---

### Post by stoer on 2007-01-22
> **rai4shu2 said:**
> The downside to FAT32 is that your files in /home would have a 4 GB size limit, plus they will become fragmented in a relatively short period of time. I suggest you use a more standard format (like ext3 or xfs).

Good point, most of the files i work with are either 700mb, 4.5Gb or even 8Gb.  (film, obviously).
Therefore, again the ugly question of sharing arises. 
I think i need to give this some serious thought, otherwise i'm looking at a compromise solution.

Thanks for pointing this out, i totally missed it](*,)

---

### Post by ramjet_1953 on 2007-01-22
For what it's worth, here's my two cents worth!

1. Laptop hard drives are cheap. Buy a new one and do a clean install on that! That way, if there is something vital stored on your old OS, you can always go back to it. I have 3 HDD's for my laptop. Dapper, Edgy and Feisty.

2. If you want to use a webcam, stick with Dapper. For some unknown reason, they left support for Logitech webcams (and others, I believe) out of Edgy. It has re-appeared in Feisty.

3. Feisty is very much still in development, so unless you are prepared to put-up with crashes, freezes, etc, stay away. Also Automatix2 is not yet available for Feisty, making codec and other goodie install more difficult.

Regards,
Roger :cool:

---

### Post by Frank Golden on 2007-01-22
> **stoer said:**
> Good point, most of the files i work with are either 700mb, 4.5Gb or even 8Gb.  (film, obviously).
Therefore, again the ugly question of sharing arises. 
I think i need to give this some serious thought, otherwise i'm looking at a compromise solution.

Thanks for pointing this out, i totally missed it](*,)
Hi stoer, there is a neat program for XP (free) called ext2ifs.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

When installed on your XP partition it places a control in your Control Panel.
When you click on it it allows you to assign an Explorer drive letter to your ext3
partitions. You can then explore it read/write. Be careful not to messup your Ubuntu
install if you choose to explore Ubuntu from XP. I think using it access a ext3
data storage drive/partition might be safe.

---

### Post by stoer on 2007-01-28
Hi Frank,
sorry it's been so long, a busy week i'm afraid...
An interesting solution, ext2ifs. It sounds very good reading the web page, have you tried this yourself? I was wondering how reliable it really is in practice? Anything that offers a chance to  work with data within a dual boot system without having to login and out of different os's has an attractive ring to it.  I'm thinking that this is something i'd like to try, but that i might try it out for a while on my old pc first before applying it to my laptop.

Everyone telling me to buy a 2nd hd.
I  agree, a nice easy and relatively cheap solution.  Except with the purse strings being so tightly drawn at the moment; building work on the house this year, kids, holidays to plan and pay for etc. etc. etc. I really can't justify the cost - at least not to my wife!:rolleyes: 

I think i'm going to go with giving windows a little more room (i can then accomodate the occaisional large file), and making a nice "fat" /home (fat32) partition.
If i try to concentrate my large file work (downloads and ripping) to my pc then i shouldn't have to many problems. Just need to do some work on reinstalling the pc (sighs...).

If i can eventually convince myself to give up windows then i'll be making my life alot easier.  If Ubuntu carries on improving at the rate that it is and if i carry on "learning" at the same rate, then who knows. I do hope so.

this might work for me...
Windows - 20 GB - NTFS
swap - 1.5 GB - LINUX-SWAP
/home - 30 GB - FAT32
/ - 27.5 GB - EXT3

---

