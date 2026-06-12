---
title: "Questions about Dual Boot and Partitions"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Mr_Bison on 2007-04-09
Hello everybody,

Couple of questions from a (hopefully) future Linux user. I have used Windows for most of my life (some DOS) and I'm thinking of switching to Linux for the new PC I'm about to order. I still want to use Windows so I'm going dual boot. I'm going to use Ubuntu for internet stuff and music, etc and Windows for games (but internet and music also).

This is how I think I'm going to set things up:

Make three partitions on one 300Gb HD; C:/, D:/ and E:/.

Put Windows XP or Vista (not sure yet) and my games on C:/, Ubuntu on D:/ and put all of my MP3's and large downloads on E:/ (so both OS's can play them).

Now, I'm thinking of giving Windows and my games 150Gb, and 100Gb for my music and downloads etc. That leaves 50 Gb for Ubuntu. Would that be enough? Or would you recommend me setting things up differently (Ubuntu on the largest partition for example? Or maybe 2 instead of 3 partitions? :confused: ) 

Alright, then a couple of more questions:

**1.)** Which OS has to be installed first, Linux or Windows?

**2.)** How long does it take to switch from Linux to Windows, and vice versa (for example if I'm in Linux and want to play a game and switch to Windows, how long do I have to wait)?

That's it for now. Thanks in advance. Ubuntu looks like it fits right into the "K.I.S.S. principle". The less actions a user has to undertake in order to do something, the better.

---

### Post by spin2cool on 2007-04-09
1) I usually give my ubuntu partition 15-20 gigs, because I store all of my data on other partitions, like you're planning to do.  I've never come close to running out of space. 

2) Install windows first - it will make your life much easier.

3) the time to switch OSes is the time that it takes to reboot your computer and log into the other OS.

4) I think you'll find that the only real reason to boot back into windows is for gaming.  Everything else you need is available through Ubuntu.  

Good luck, and have fun!

---

### Post by nixclusive on 2007-04-09
50 GB is more than enough for Ubuntu. Actually that's even more than the total hadd capacity I have!! ;-)

Install Windows first... after that install Ubuntu. You might wanna keep Ubuntu on E:\ i.e. the third partition. Make C: 150 D: 100 and leave the rest space free.

Ubuntu can figure out how to use that space. Good Luck.

---

### Post by Bachstelze on 2007-04-09
1) 50 GiB will be far more than enough for Ubuntu, aven 15-20 as suggesed above will leave you with plenty of unused space. Give it 10, and you will be safe.

2) Install Windows first if you can, it will make your life a tiny bit easier but if you want/need to install Ubuntu first, it's fine also.

---

### Post by Mr_Bison on 2007-05-11
Hi everybody!

Thank you very much for the answers. Sorry for not replying, I was busy.

Tomorrow my new system arrives so I'm going to install Windows first, and then Linux (as you said).

I still have a question though. If I'm not mistaken, you can choose how to setup your partitions... FAT, FAT32, NTFS, etc. How do I know which partition should get which? Do you think Linux and Windows should be on a FAT32? And the shared partition NTSF? I don't know a lot about this kind of stuff.

Thanks again! You're very helpful. :)

---

### Post by jputman01 on 2007-05-11
> **Mr_Bison said:**
> Hi everybody!

Thank you very much for the answers. Sorry for not replying, I was busy.

Tomorrow my new system arrives so I'm going to install Windows first, and then Linux (as you said).

I still have a question though. If I'm not mistaken, you can choose how to setup your partitions... FAT, FAT32, NTFS, etc. How do I know which partition should get which? Do you think Linux and Windows should be on a FAT32? And the shared partition NTSF? I don't know a lot about this kind of stuff.

Thanks again! You're very helpful. :)

give windows NTFS, give linux ext3, and you can give your third partition fat32 (that should be just fine, correct me if im wrong)

and i agree with everyone else above, 50 gigs is more that you will need if you store you larger files on seperate partition and install windows first

---

### Post by Mr_Bison on 2007-05-24
Hey everybody, I'm having some trouble doing this. 

It looks like I am only able to assign the NTFS filesystem to my partitions.

I have three partitions:

C:/ - this one is 100Gb, for Windows, games, downloads etc.
D:/ - 150Gb, for MP3, video editting, etc
E:/ - 50Gb, for Linux.

I have made these partitions during the Windows install. After install, I decided to format the D:/ and E:/ partitions using the function in Windows, but I could only choose NTFS. What's up?

Can I change D:/ and E:/ to the filesystem you guys recommended me? If so, do I have to format these partitions again?

Thanks.

---

### Post by godssiren on 2007-05-24
To re-do the partitions, I would suggest deleting the extra partitions(for ubuntu and swap and the shared files) using windows, creating just a big blank space area, then I would run the live CD of Ubuntu, and use GParted, which you can find in the System, Administration drop-down menu.
That way you can create the new partitions in that empty space and make them the correct file format. It's very simply done, even I was able to do this part, now if only I could get the install to work. ^_^

---

### Post by Mr_Bison on 2007-05-24
I'm going to try that this weekend. Thank you mate.

---

### Post by timmib on 2007-05-25
> **Mr_Bison said:**
> Hey everybody, I'm having some trouble doing this. 

It looks like I am only able to assign the NTFS filesystem to my partitions.

I have three partitions:

C:/ - this one is 100Gb, for Windows, games, downloads etc.
D:/ - 150Gb, for MP3, video editting, etc
E:/ - 50Gb, for Linux.

I have made these partitions during the Windows install. After install, I decided to format the D:/ and E:/ partitions using the function in Windows, but I could only choose NTFS. What's up?

Can I change D:/ and E:/ to the filesystem you guys recommended me? If so, do I have to format these partitions again?

Thanks.

fwiw, win automatically presumes any partition of 32gigs or more *must* be ntfs <s&g>

looking forward to reading your experience.

Be well

---

### Post by Mr_Bison on 2007-06-18
Here he is again, the bison that takes so awfully long to install Linux. ;) Hey, even bisons have a busy life!

I decided that I'm going to format and reinstall Windows.

This is how I think I should do it:

**1.)** Format (this automatically deletes partitions as well doesn't it?), creating one big empty space;

**2.)** Install Windows, but not choose partitions just yet;

**3.)** Run the Ubuntu Live CD and use GParted to make the partitions in their correct filesystems;

... and finally:

**4.)** Install Ubuntu on the partition I just made.

Correct?

---

### Post by mr32123 on 2007-06-18
Personally I think it would be much easier just to set up two different partitions in the first place instead of resizing partition tables after windows is installed which can be a major pain in the rear (from my experiences).

btw I saw someone mention that that the originator of this post should use FAT32, here I say use NTFS, ubuntu has now an add on in hte software updater that allows you to read from and write to NTFS.

---

