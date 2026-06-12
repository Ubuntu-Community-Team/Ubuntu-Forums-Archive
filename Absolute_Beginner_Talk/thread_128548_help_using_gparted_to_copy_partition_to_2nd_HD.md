---
title: "help using gparted to copy partition to 2nd HD"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-02-11
Hello All,

I have a laptop with a 20 gig hard drive running Ubuntu and XP dual-boot. I want to copy the Ubuntu partition to another 40 gig hard drive that I would use with this same laptop. But don't get confused: these two hard drives cannot both be installed at the same time. I am going to swap one for the other. 

People on this forum recommended using a live cd with gparted.

I tried to use gparted to copy my Ubuntu partition to an external 80 gig hard drive (sda1) I have. This is what I did:

I resized the external disk so there was about 7 gigs of spare space.

Then I tried to copy the hda2/ext 3 partition (the root partition for Ubuntu) onto the unallocated space on the external hard drive. This hda2 partition is about 5 gigs. I tried it 3 times and it always failed. 

My plan was to copy the partition to external drive then remove the 20 gig hard drive from the laptop and replace it with the 40 gig drive and then use gparted to copy the Ubuntu partition from the external drive to the new 40 gig drive, thus restoring my old Ubuntu system onto the new drive.

Can I do this? What could I be doing wrong. I am pretty green so I don't really know what I am doing. Any ideas would be greatly appreciated. Thanks!

---

### Post by plors on 2006-02-11
please try this again using the latest [gparted livecd]("http://gparted.sourceforge.net/livecd.php").

These versions (0.2 and above) have superior error-reporting and will most likely tell us what's going wrong.

---

### Post by gigi1234 on 2006-02-11
Yes, I am using version 0.2 but there is no error report that would lead me to a reason why the copy is failing. However, I could never find any kind of instruction manual so I was just blindly going through the process by intuition.

Any other thoughts? Thanks again!

---

### Post by gigi1234 on 2006-02-11
Okay when I try to do the copy I can see an error message. It looks like the process is hanging up on creating an empty partition. But I have no idea why. Do I need to create a disk label? I am a little nervous about that since I get a message saying this will erase all data on the external drive. I do have important information on this external drive that I do not want to lose. What next?

---

### Post by gigi1234 on 2006-02-12
I still have had no luck. Does anyone know why gparted would fail on trying to create an empty partition on my external drive? Once again I am trying to copy a partition to an external hard drive so I can then copy it to another hard drive. Thanks!

---

### Post by Herman on 2006-02-12
Well I'm not too sure what you mean by 'create an *empty partition*'.
When I am copying and pasting partitions around on a single hard drive, I make sure there is some *free space* there which is at least a little bit larger than the partition I want to put there. Sometimes I need to resize and/or move one of the other partitions to make enough free space.
Then I r-click on the partition I want and click 'copy', then r-click on the area of free space I have available, and click 'paste'.
Is that what you are doing already ?
You don't need to create a new partition yourself, GParted will do that for you, I'm not sure I'm understanding you right. Maybe you are doing that already and getting an error message it can't create a new empty partition?
I wish I had an external drive so I could try it too and find out for myself. :-D (Herman)

---

### Post by gigi1234 on 2006-02-12
Sorry this is confusing.

I freed enough space on the external drive (and then some) for the partition I want to copy onto the drive to fit. So there are about 10 gigs of empty unformatted space on the external drive. Using GPARTED, I have tried to copy hda2 (my Ubuntu root partition) from my laptop HD and then paste it into the unformatted space on the external. I have tried it numerous times and each time I get an error and it seems the process is terminating at a step called "create empty partition." So, I am not trying to create a partition, the program is. In fact, if I try to create a partition on the external drive I can do it no problem. I was wondering if it could be some kind of permissions problem. But truth is I just haven't the foggiest.

Seems like this should be simple.

---

### Post by Herman on 2006-02-13
>  Seems like this should be simple. You're right, it is simple, but I am sorry it didn't work for us as simple as I thought the first time.

I am pretty sure I have it figured out now! :D 
I thought I didn't have an external hard drive to play with and test this, but it turns out I do, I just didn't know it. It's my wife's mp3 player.
It already had some mp3s in it. It's far too small, of course, to copy a partition from my computer into it, so I tried testing how to copy in the other direction, by making some free space on my hard disk, and copying the mp3 disk to the free space, (exactly the opposite of what you want to do). The result was the same error that you got....

So, I selected the free space, and created a new partition there and formatted it with a file system. In this instance, fat32. At the same time I noted the partition information from GParted. I clicked on the black rectangle down in the lower right corner for a terminal. Then I used this command:```
dd if=/dev/sda1 of=/dev/hda6
```It worked, my hard drive led light winked and blinked for quite a long time before it was all copied, but it worked.
So all you need to do now is apply the same operation in reverse.
That is, create your new partition in your external drive and format it as ext3 if that what is applicable, and type something similar to the following, substituting your own specific drive letters and numbers where necessary. I will attempt a guess anyway, but just check and see if there's something you'll need to alter:
```
dd if=/dev/hda2 of=/dev/sda2
```That is presuming your new ext3 partition you will make on your external sda drive will be sda2.
This should do the trick for you, just check it all twice to make sure the numbers are right. Good luck! :D (Herman)

---

### Post by gigi1234 on 2006-02-13
YES!

I think this is going to work. At least, so far, I have copied my Ubuntu partition to the external. It took FOREVER, maybe 3 hours?? Should it take that long?

Anyway, Herman, you are the best for taking the time to figure this out for me. How ingenious to try using an MP3 player as the external!

I'll let you know if it worked. I think I'll have to re-load GRUB too.

Thanks a million...

---

### Post by Herman on 2006-02-14
I have been doing more research and learning about the 'dd' command. 
It's an extremely useful command, and can do a lot of neat tricks, and is also very powerful so isn't really recommended for beginners normally. Usually, it's safer to use the partitioning software to apply it the command for us, but in our case we needed to apply it manually this time.

The main thing is not to get the 'if' (input file) side of it, and the 'of' (output file) side of the command the wrong way around. Apparently some people do and instead of copying their data to the empty partition they do the opposite. 
I don't think that's likely in this instance, as one is 'sda' and the other is 'hda', in your case, and besides, the data will still be backed up on the original disk.
The command you would be using to copy from the external sda drive to the new hda internal drive when it is fitted will be the the reverse of the one we used to copy it to the externel drive the first time. That is, something similar to:>  dd if=/dev/sda2 of=/dev/hda1 That should work if you already have a partition created on your new hard disk named 'hda1', or if not then replace 'hda1' with the name of the partition you want to copy to otherwise.
>  I'll let you know if it worked. I think I'll have to re-load GRUB too. Let me know when you are okay, or if you need any more help, I'm starting to worry, it's been a while.
 I have work to do, that takes me away from my computer though. I hope everything is going well for you.

---

### Post by gigi1234 on 2006-03-03
Sorry to be away. Let me know if you are still following this thread Herman. 

I was out of town and away from my computer, then got sick, and haven't had time to work more on this project.

I was able to copy the partition. But when I copy it onto the new hard drive I can't get it to work. I reinstalled GRUB too but something wasn't right and the only operating system that was recognized was Windows.

Thanks for the hints about the dd command. I have read other threads where people have apparently reversed the order and lost all their data.

I may give this another try but I must admit I have gotten really frustrated. But I still want to learn how to do this (copy a partition from one machine or hard drive to another). I hate having to start from scratch all the time. 

Also, I have been wondering, when Ubuntu releases a new version, do you have to  reconfigure everything when you install it, or can you somehow save all your settings and added packages?

Thanks again for all your help Herman.

---

### Post by Herman on 2006-03-03
I'm still here, I'm glad you are back.:-D

I think probably your partition is getting copied okay and grub should be able to find it again. One of the special features of grub is that it can find our partitions by thier partition number and kernel name, not by the disk goemetry information, so moving the partition around should be okay. Re-installing Grub should have worked though, that's what I need to do when I re-arrange my partitions and the partition gets a different number. Hmmm:-k. Quite likely you are very close to achieving your goal, maybe just try again, or try a slightly different method. 

When Dapper comes out I'll probably just re-install, personally. That's better for me. However, you can just open your /etc/apt/sources.list and replace every mention of the word 'Breezy' with 'Dapper', then you type ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
```I wouldn't recommend anyone do so yet though, until they tell us it's ready and then some. :-D (Herman)

---

### Post by dvarsam on 2006-03-04
Hello guys!

I just read this thread & it was awesome!

I am also concerned with doing Backups!

I only have 1 OS installed in my Hard Drive & that is ONLY Ubuntu.
The other 2 Partitions (on the same Hard Drive) are empty.

Isn't there a way to Backup ALSO the GRUB part?

OR

We always have to re-install the GRUB, every time we Backup Partitions?


Thanks.


P.S.1> Dear Herman: the trick you did with the ".mp3" drive was very clever!
           Bravo man!!!
           That was awesome!!!

P.S.2> Dear "gigi" good work.
           When you finally make it, please inform us, cause I would really like to know 
           too!

---

### Post by Herman on 2006-03-04
Hello dvarsam ,and gigi,  thanks for the encouragement! :D 
 You are doing a very good job with making some great tutorials yourself, dvarsam! And gigi it's an interesting project you are doing. I can hardly wait to read that you have succeeded!

For doing a backup of my entire installation, dvarsam, my favorite method is to use the latest GParted livecd and resize the whole installation to as small a size as possible. (Perhaps 3 or 4 GB for example.) Then I simply copy it and paste it to some free space right at the end of my disk.  That's it - simple!-

Then I resize the installation I'm using again and use it. When I get a few updates and make some other improvements that I'm happy with, I delete the back up and replace it with a fresh updated copy. 
If I conduct an experiment that fails and does some damage to the installation that I don't feel like bothering to repair, I just delete the whole installation partition and paste the back-up copy in its place.

For me this makes it possible to have a nice installation all set up the way I like it, with automatix and all my favorite settings and the like in my test computer. I do have a few files in it, not very many, and nothing very important. I keep those on some other partitions I have mounted in directories in my home folder, so they are out of harm's way.

The back-up copy of the installation isn't bootable, (as the partition numbers have changed). I could make it bootable if I wanted,  by re-installing grub and edtiting /etc/fstab.
However, by leaving it alone, it will have the right partition numbers again when I paste it back where it came from after deleting the broken one.
It is a feature of Grub that it does not rely on disk geometry to find the partition to boot it, but rather the file name (and number). Therefore partitions will be unbootable when copied somewhere else on the same disk the first time due to the partition number being changed. Then when you delete the original and copy it back, it gets its old number back again, so grub will find it, and boot it.
I have done this many times on a single hard disk, and it works very well for me. For my purposes it is a better idea than having a seperate /home partition, since this way the whole thing gets replaced but my data.

To try what gigi is doing I would need more equipment. I can only read about it for now. I have read something more about it too, I found this [great link for 'dd' commands.]("http://www.linuxquestions.org/questions/showthread.php?t=362506")
It is a little hard to read the way it is. I copied it to an  O' Office .org Writer page and did lots of formatting to it to make it easier to read. I made the headings bold, spaced out the topics into paragraphs and commands blue, and that sort of thing.
There are some important things there that might interest you, gigi, and some improvements that can be appended to the commands we used. It would be well worth reading and studying. The best thing is the information that applies to your project, gigi, is right near the top of it! :-D (Herman)

---

### Post by dvarsam on 2006-03-05
Dear Herman:

Thank you for your reply & for your nice comments.

I am still at "beginner's" stage, but it nice to hear that my Tutorials seem good.
I try to write them in a simple step-by-step procedure, cause sometimes I read some other people's Tutorials & they are NOT step-by-step & sometimes hard to follow...

...at the same time, some people's Tutorias teach "HowTo" do complicated stuff, when some other people (like me) were just trying to learn the basics... 
... NOT to mention some Tutorials that start like this:

<How to Install Program "Foo">

1. Do this...
2. Do that...
3. Do next...
4. Do after...
5. After this...
6. Next...

DID they EVER mention what the Program "Foo" is?
Cause I really wonder... @#$^%@#$^

IF it is supposed to be a Tutorial, they better first explain what the program does...

... and THEN tell you how to make it work...

_Result_:
Since I did NOT find anything to help solve the small (easy) stuff, I thought to write some articles about it...
... cause I learned it the HARD WAY... (e.g. posting questions, asking friends, etc...)


I want to try out your suggestion using "gparted LiveCD", soon.
I have downloaded the "gparted LiveCD" & have written it on a CD.

Hopefully, when finished, I will try to write a nice Tutorial.

But first, I am trying to learn as much as possible from this (beginners) Forum to be able to feel more comfortable with my Ubuntu...

I have learned a lot, but still can't reach your LEVEL!!!

You are Ubuntu's SUPERman !!!

Thanks.


P.S.> Dear gigi, don't forget to tell us how it worked for you, man.

---

### Post by gigi1234 on 2006-03-09
Hello awesome Ubuntu buddies!

I feel so left behind!

I have been spending all my computing time recovering from a virus that destroyed every data file on my hard drive on a work computer running XP.  WOW I really hate Windows!!! :twisted: 

I am hoping to make another stab at this project soon. Things are a little crazy for me right now.  I am in the final stages of finishing a Ph.D. and they are really making me jump through the hoops.

You guys are great. 

I need to get the details of what I am trying to do back in mind. I have succeeded, thanks to Herman, in learning how to copy the Ubuntu hda2 partition to an external hard drive. I have another hard drive I can put in my laptop that is running a dual boot with XP and a fresh install of Ubuntu. I would like to replace the fresh Ubuntu hda2 with the one I copied from my other hard drive. 

I have tried using Gparted to delete the fresh hda2 and replace it with the copied version. Then I tried to reinstall GRUB (details of the best way to do this might be helpful). But then when I try to boot GRUB only sees the WIndows partition.

So that is where I think I am at. Is anyone still following this thread? I love chatting with you guys! I am looking forward to the Dapper release!

---

### Post by gigi1234 on 2006-03-09
Oh and FOR SURE if I ever succeed I will absolutely chime in and let you know!

---

### Post by gigi1234 on 2006-03-09
dvarsam:

I love your idea of writing tutorials that are geared toward newbies and thus are totally step-by-step. I can't tell you how many times I have found how-tos that say "do this" but I lack the background to "do this" or to even understand what it refers to. The tutorials that are most helpful are totally explicit and don't gloss over anything. I applaud your efforts and would love to see what you have done.

---

### Post by Herman on 2006-03-10
Gigi, I have just updated the [GRUB Page]("http://www.users.bigpond.net.au/hermanzone/p15.htm") of my website with some new info on how to use command line GRUB. (Just press your 'c' key from the GRUB menu for the command line, and'Esc' for the GRUB menu again).
 The information I hope might help you to get GRUB to find and boot your partition is under fig3 on that page. (After that it might just be a matter of editing your menu.lst with the correct partition numbers and you'll be laughing).
You might be able to just try the same commands as given in the example, but you might need to modify them a little by replacing the partition numbers with one to suit your set-up. There are some extra command that might come in handy under 'Discovering the Magic..', particularly this one: ```
grub> find /vmlinuz
``` (The output from that should help you check or confirm the kernel's location). It's odd that GRUB didn't already find it when you installed Grub. Below is my whole collection of links for re-installing GRUB in case any of those might be useful to you, I guess everyone has their own favorite method.

[COLOR=#000000][FONT=Arial]From the Official Ubuntu Wiki[/FONT][/COLOR][COLOR=#0000ff][FONT=Arial]: [/FONT][/COLOR][https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=(MBR)]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29") [LEFT][COLOR=#000000][FONT=Arial] 
Swiss2K thread:                       [/FONT][/COLOR][http://www.ubuntuforums.org/showthread.php?t=114332]("http://www.ubuntuforums.org/showthread.php?t=114332")[/LEFT]
  [LEFT][COLOR=#000000][FONT=Arial] 
Arnieboy thread:    [/FONT][/COLOR][http://ubuntuforums.org/showthread.php?t=76652]("http://ubuntuforums.org/showthread.php?t=76652")[/LEFT]
  
 [LEFT][COLOR=#000000][FONT=Arial]vnbuddy2002 thread:[/FONT][/COLOR][http://www.ubuntuforums.org/showthread.php?t=24113]("http://www.ubuntuforums.org/showthread.php?t=24113")[/LEFT]
 
I hope that might help you a little. :D (Herman)

---

