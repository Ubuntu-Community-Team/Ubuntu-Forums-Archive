---
title: "First post/Help w/Partitioning"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-07-27
Hello everybody, name is Doug, and I'm a complete noob to Linux in general. A few years back, I attempted to have a go at Red Hat and Suse, but I don't think I was ready for the necessary work it takes to learn something new. 

Being that I'm totally frustrated w/Windows, I thought I'd give it another whirl, and so far, I'm finding myself very plesantly surprised with what Ubuntu has to offer. It's actually installed on my Windows box, but on a separate (smaller than master) HD. I'm in Windows at the moment, becuase I need to re-install Ubuntu for a couple of reasons. First, a description of my specs, what I did w/the install, and my plight: (forgive the length of my post, I tend to be detail oriented to the best of my anal/retentive abilities ! ;)  )

System:
AMD Sempron 1.5Ghz (2200) 512 MB Samsung RAM; (1) Maxtor 160 gb (1) Maxtor 5200 RPM 20 gig HD (slaved)
Turtle Beach Santa Cruz Sound Card/Nvidia MX400 Graphics card.  All running off of Win XP SP2
__________________________________________________________
Here's what I did to install Ubuntu. I thought that it would be best to put Ubuntu on the slaved HD with 20 gigs, this way, it woudln't have to be directly next to Win. But I still want Linux to be my main OS, so I needed to allocate space on the primary HD just for Ubuntu. 

I basically gave Ubuntu the entire 20 gigs for the install, and let it automatically put the swap on the same drive. I did not however, make any other partitions on that 20 gig, which I think is what I should have done, but am not familiar with how the file structure is set up on Linux, so things such as "home" and the other directory, I guess were left to their own devices...

On the 160 gig drive, I gave Win the first partition, which is 20 gigs, for software installation etc.. 14 gigs is probably more than enough though, perhaps less. Then, I decided to give Win another 60 gig partition, in order to store my music and video files, as well as whatever rogue downloads I may have come up with. 

That leaves about 74 gigs unformatted, just for Ubuntu. Problem is of course, Linux doesn't (natively) read or write to NTFS. I THOUGHT however, that it WAS able to read/write to FAT32 file systems. So partitioned the 74 gigs as 2 x 32 and a left over 12 gig partition. I then formatted them all to FAT32, which **apparently** was a waste of time, becuause I can't mount those drives from Ubuntu. 

Now I'm thinking I should just (and this is where I need approval or other ideas if this is a bad one) delete all of those partitions, and reformat so that:
The 20 gig drive goes to Windows for whatever. I'd rather use it for Ubuntu, but if it can't read it, what's the use ? I've heard that there's a patch which enables Linux to see NTFS, but don't know enough about it yet to test this out. 

Then, I'd reformat the 160 gig drive, re-install Windows,(MAYBE)with less HD space (sine I'm only going to use it for a couple of Music editing programs like Ableton Live/FL Studio/Cakewalk) 
and then give Ubuntu the bulk of the space. 

What I'm thinking is:

Windows main Partition gets 20 gigs for all installations/programs. It also gets the slave 20 gig HD to put the Page file on it as well as some music to listen to while on it..maybe. 

That leaves a bit under 140 gigs for Ubuntu. **_[SIZE="2"][COLOR="Red"]This is also given that Windows will play nicely with Ubuntu sitting next to it on the same HD (will it?).[/COLOR][/SIZE]_** If it will, then my next question is, how would any of you suggest I partition that remaining space ? Remember, I'm not quite savvy with the lingo, so if any examples are given, could it please be done so in the context of how Ubuntu runs one through the actual installation process ? 

I've read in some Linux fourms that it's a good idea to have a pretty small partition for root, like say 5-10 gigs. I've also read contradictory statements in regard to how much should be allocated to the swap. Some have said don't to over 512 MB, while others have said to double your memory.

I think that's a good enough place for me to start on this forum, and you guys seem a nice bunch, so I'll spare you all from any other questions (for now). Thanks to those who've been patient enough to read this and whom is willing to offer up some help. 

Best regards, 

Doug

---

### Post by aysiu on 2006-07-27
Ubuntu can natively read NTFS and read/write FAT32. You just have to mount the partitions properly. To do so, follow these directions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

For partition planning, read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by bensexson on 2006-07-27
I dual boot on my laptop with only 1 HDD.  I have four partitions on this drive ~28 gig NTFS for XP, ~20 gig ext3 for Ubuntu, 7 gig FAT32 to share, and 513 meg for swap.  This works great.

---

### Post by Paerez on 2006-07-27
Hello Doug!

First, Ubuntu can most certainly mount Fat32 partitions and read/write to them, but there are some tricky options for mounting to allow users to mount and read/write to them.

Windows will not even know ubuntu is there, it is delightfully ignorant of linux.

Swap should be at least equal to your ram (except in situations where you direly need HD space). The swap is the same as the windows page file, so more is helpful. I have a laptop with 1 gig ram and it pretty much never touches the swap. But it should be equal to ram in order to hibernate.

The downside of Fat32 is that I have lost data because its a very simplistic and crappy filesystem. 

Here is my suggestion:
Primary HD:
16g Ubuntu Root
110g+whatever is left Home
32g Fat32 Sharing

Slave HD:
Windows

Then you can share files between windows and linux using the fat, and in windows there are tools to read Ext3 partitions, so you could read your home.

Excellent post, details will get your problems answered much faster. (although if it gets too long people get scared :D)

---

### Post by jimbren on 2006-07-27
I'm not in front of my ubuntu installation, so I won't get all of the details precisely in my answer, but I think I can give you some good general information.  If no one else steps in to clarify, then I will send a follow up message later.

First off, linux can mount your FAT32 partitions Read\Write permissions, but you will probably need to put entries for them in your /etc/fstab file before you can make this happen.  Make sure you backup the file before you make any changes.  Messing this up is a Bad Thing.  You can get information on how to edit the file by reading the man page, and I can send you an example later if you like.

Secondly, Windows and linux will play nicely together, but you have to do it in a specific order.  Install Windows first, THEN install linux.  If you do it in reverse order, windows will overwrite GRUB and then you have to restore it.  Doable, but a moderate pain in the ***.  

As far as partitioning goes, there's no reason you can't put windows and linux side by side on the same physical drive, so don't be afraid of that.

You've got a lot of space to play with, so there's no reason you shouldn't be generous with yourself.  I would think about doing it like this:
On the 160GB drive--
~60GB as FAT32 for your music and windows page file
~10-15GB as EXT3 for /root
~1GB for /swap (i usually stick to the 2x RAM rule of thumb)
~256-512MB for /boot (I think 512 is way more than you need, but I can't remember the recommended size.)

On the slave drive, just give it all over to Windows.

When you are doing your windows installation and it wants to deal with the 160GB drive, I would just have the installer remove all of the partitions and only deal with the 20GB drive in Windows.  The windows installer can do funky things with drive lettering when there's more than one disk involved and you're not installing on the primary, and it's just a pain in the *** to deal with.  Linux handles it all much better.

Also, a piece of advise...limit what you do in windows as much as you can.  Don't use both installations for email or for documents.  Use windows only for what you absolutely need it for, while at the same time actively looking for 'nix solutions to the Windows software you use.  It is out there, and it is probably better--you will have to force yourself to use it, though.

I say that because you will get lazy and fall back on using windows more because it is what you know.  There are times when you don't want to read a man page or hunt for software just to burn a CD or something stupid like that, and you will go to Windows because it is familiar.  And then you'll find yourself using linux once a week for a few hours, and be frustrated when you run out of space in windows.

I decided to make the jump about two years ago and just wiped Windows from my system, and it made all the difference in the world.  I'm by no means an advanced user, but I know my way around fairly well and know where to look for good answers.  These forums, for example.  :)

Anyway...you thought you were long-winded...

Good luck.

jim

---

### Post by jimbren on 2006-07-27
I hate it when I lag in replying...when I started my reply, this message was listed as one minute old.  I'm at work and the bastards actually expected me to deal with work, and by the time I got done, there were two posts more detailed and helpful than mine.

bah...

---

### Post by Paerez on 2006-07-27
stupid work, always getting the way of toodling around the ubuntu forums all day.

I would have read your post sooner if it wasn't for my department celebrating a new employee. They made me eat pie! it was horrible :D

---

### Post by Sweet Spot on 2006-07-27
You guys are great, thank you so much ! I actually just got back from getting a hair cut, and wasn't expecting answers so quickly, surprise surprise eh ?  I have yet to read each message thoroughly enough in order to extrapolate what I feel would be the best course of action for me. 

I have gotten out of them however, the point that I should keep /home on a separate partition, and that reading/writing permissions are possible w/FAT32. That's fantastic. Now all I have to do is re-install Windows and then Linux thereafter. 

[quote=jimbren]First off, linux can mount your FAT32 partitions Read\Write permissions, but you will probably need to put entries for them in your /etc/fstab file before you can make this happen. Make sure you backup the file before you make any changes. Messing this up is a Bad Thing.[/quote]

I have no idea of what you just said other than Linux can mount FAT32 partitions ! :p  And don't worry about not posting first, it's the thought which counts, and you've done more than enough to try and help, for which I'm greatful. 

Ok, I'm off to try and assimilate all of this info, plus some from my home page (MisticRiver), where an Ubuntu user there is also lending me a hand. I think that between all that's been said here (especially with the helpful links from aysiu (thanks a lot), I should be able to hook myself up pretty decently in a short enough time. 

Thanks again all. 

Doug

---

### Post by aysiu on 2006-07-27
I still don't see why you need to reinstall. If you want a separate /home partition, follow this tutorial:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by Sweet Spot on 2006-07-27
> **aysiu said:**
> I still don't see why you need to reinstall. If you want a separate /home partition, follow this tutorial:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

Yeah, I know it seems like a waste of time but, I think it would make me feel as if everything was fresh/clean. This might sound wierd but, last night as I was installing Ubuntu, the process failed a few times either because of my physical CD drive, or maybe because the disc wasn't as pristine as the first time it was used. It stalled a few times, making me start over, and it also registered an fail message during installation. 

Finally, as it got past all of the checks, I didn't see the actual instal take place. All I saw was a small squarish icon in the middle of the screen, and I guess that it WAS installing in the background, but never did I see any measurement of where it was in the install. So it left me feeling a bit insecure about the whole thing. 

In any case, I'm going to re-think exactly how much space I want allocated for what, and where I want things. In that regard, I may find that a re-install is exactly what I want to do anyway. 

I certainly will check out that link and take all things into consideration. It's just that being a bit green, makes me paranoid about working around things, rather than just starting from scratch. I'm sure you can understand that. 

Regards, 
Doug.

---

### Post by Paerez on 2006-07-27
if you create the fat partition and format it BEFORE installing ubuntu, it will be detected automatically and will be in the Computer place in ubuntu.

---

### Post by Sweet Spot on 2006-07-27
Ah... Awesome answer. Thanks !

---

### Post by Sweet Spot on 2006-07-27
Tell me if I'm missing something here. I think I was stressing myself for nothing, especially considering that I want to use Ubuntu as my main OS... Here's what I am going to do, unless you think it's stupid/not possible etc..

So :
HD #1 has 160 gigs
HD #2 has 20 gigs

I'll delete all current extended partitions on HD 1, leaving only the master windows XP boot one.

I'll then create another partition using all the remaining space and format to NTFS

I'll then delete the partition on HD #2 which Ubuntu now resides on, and then format it to FAT 32.

That will allow me, when installing Ubuntu, to reformat the 140 gig NTFS partition, and partition it as has been suggested.

I'll use what, 10 gigs for /root ? Then perhaps 60 for /home and another 70 gigs for /data ? On top of that, I'll also have the 20 gig fat32 partition on which to do whatever, should I ever need it.

Sound about right ?

Doug

---

### Post by OU812 on 2006-07-28
I followed this link from aysiu

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

I noticed it suggests doing root, home, and swap. Usually I do root, swap, and home. And once I experimented with swap, root, home. Is there really andy difference between the three? Thanks.

john

Also, when picking a file system, I would like to use ext 3 so windows can see it. But is it prone to fragmentation? If so, how would you defrag it? Thanks.

---

### Post by Paerez on 2006-07-28
"Fragmentation" is so windows. I like reiserfs because I feel cooler using a non default fs. But neither ext3 nor reiser have ever lost my data (fat has).

Sometimes on real old systems, root has to be first. I would suggest root swap home or swap root home, because then if you are ever accessing swap the disk head will be relatively near you kernel and application data, which is most likely to swap out. Very minor performance gain, but if you're gonna pick an order, may as well base it on something. I think I have it set up as [root|swap] on mine just cause thats default.

---

