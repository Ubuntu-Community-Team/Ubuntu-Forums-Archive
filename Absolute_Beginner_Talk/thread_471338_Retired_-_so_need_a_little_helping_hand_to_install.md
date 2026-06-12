---
title: "Retired - so need a little helping hand to install ubantu"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Living_Legend on 2007-06-11
Hi Readers, I'm having a little difficulty getting Ubantu to install. My progress accords with the Ubantu documentation and instructions and are described here:-
 
1 Downloaded iso file - ***_ubuntu-7.04-desktop-i386.iso _***- no problems
2 Checked out dat integrity of download using winMD5sum and checked with UbantuHashes - Ok
3 Download,  installed ran Infra Recorder - no problems 
4 Burnt ubuntu-7.04-desktop-i386.iso to a brand new 7.4 G Disk - burnt Ok.
5 Manually changed Bootlog sequence/priority from Hard Drive to CD ROM
6 Re-Booted machine with Burnt Disk installed in CD ROM.
7 Ubantu Screen display appeared with list of 6 or so options
8 Chose to run  memory check - Ok
9 Selected boot up start.
10 Green boot up message appeared then screen went blank and a moment later a screen dump appears at bottom of screen as follows:-

Int 14 CR2 f8000000    err 00000000    EIP c020c384   CS 00000060    Flags 00100007  
Stack c00f8050  c03f129b  c0371d8c  00000002   c00f8059   000f8050   00000000   00000000   

The system then locks up.

My Machine is run by Intel Celeron 2.6 G; Win XP SP2; Graphics is ATI 9500. No bugs and runs well under XP SP2.

Hope the above is sufficient info for someone to help me...so in anticipation thanks to everyone who responds :p:p:p:p

---

### Post by ramjet_1953 on 2007-06-11
A few things to double check here:

1. You definitely burnt the image as an iso image, not just a data disk?

2. If you burnt it any faster than 4 X you will probably have problems.

3. iso images require high quality media. Cheap stuff often cause problems.

If all of the above are OK, the suggestions below may help.

I did notice on your post that you have an ATI video card. ATI do not produce open source drivers and sometimes they do not play nice with Linux.

However it is not insurmountable.

What I suggest that you do is to download the alternate CD. It is a text-based installer that should work fine with your ATI card in legacy mode. Even though it is text-based, it is very intuitive and shouldn't post a problem for you.

After the install, you can then use the restricted drivers option and / or get help from this forum to get your screen resolution set-up OK.

Regards,
Roger :cool:

---

### Post by Rocket2DMn on 2007-06-11
That's very strange because I saw that same error just a few hours ago.
[http://ubuntuforums.org/showthread.php?t=471190](http://ubuntuforums.org/showthread.php?t=471190)
We thought it was the CD, but I then suggested it was a memory or CD drive problem.  Not sure if this matters, but why did you burn it to a DVD-R (7.4GB = dual layer DVD)? It should be burnt to a CD-R which is only 700MB.
It's good that you checked the md5sum, that's usually the best place to start troubleshooting.  Why don't you try burning the .iso file to a cd-r at 4x speed.  Slower burn speeds seem to work better.

---

### Post by p_quarles on 2007-06-11
I can only think of a couple things, but maybe it's one of them.

1) Memory. You have to have at least 256 MB to run the Live CD, but I'm guessing that if XP SP2 runs fine, you have more than that already.

2) ATI graphics cards might require some tweaking before they work. I don't have one, though, so maybe someone who does could comment?

Anyway, the bottom line is that some systems, for various reasons, can't use the Live CD. You can still install the system using the Alternate CD (which is a better installer, but doesn't give you the test drive option). You can use it to install on the full disk or to create a new partition for a dual-boot. 

Let me know if I can help you further.

---

### Post by jerrylamos on 2007-06-11
If you got the boot options, then the .iso is burned O.K.
I find the memory test a bit boring and long.  I'd rather run Ubuntu.

Choose "run or install ubuntu".

If for some reason (there are a few) the X window screen support has some problems, then try with "safe graphics mode".

Post back here how you make out.

---

### Post by malathia on 2007-06-11
> **p_quarles said:**
> I can only think of a couple things, but maybe it's one of them.

1) Memory. You have to have at least 256 MB to run the Live CD, but I'm guessing that if XP SP2 runs fine, you have more than that already.

2) ATI graphics cards might require some tweaking before they work. I don't have one, though, so maybe someone who does could comment?

Anyway, the bottom line is that some systems, for various reasons, can't use the Live CD. You can still install the system using the Alternate CD (which is a better installer, but doesn't give you the test drive option). You can use it to install on the full disk or to create a new partition for a dual-boot. 

Let me know if I can help you further.

Yeah, I think number 1 is a possibility, although I'm not sure about 2. I've never had an issue getting rudimentary video performance with my ATI cards under ubuntu. DRI may not work, and GLXgears may be pitifully slow, but it still renders Gnome and boots into xserver fine.

I'm trying to remember back to what my error was with my laptop... I think it was a bit different using the LIVE CD install option. I have a t22 with 256 mb ram, which is enough to run the live CD but if you go to install from the Live CD it fails, and fails hard. 

Perhaps if you have much less than 256 mb ram?

I'm thinking memory or a CD burn issue. I'd recommend going with the burning the img as an iso to a CD-R at 4x as your next step.

---

### Post by Living_Legend on 2007-06-11
Hi There - ramjet-1953
                 Rocket2Dmn
                 p-quarles
                 jerrylamos
                 & Malathia
Well you have all taken me by surprise by responding so quickly to my plight. It is surprising how much we can help each other when we want to (human race that is). So to answer some of the questions and queries raised by you all I submit the following additional information to see if we can get it sorted:-

1 I have plenty of memory installed (1.75G) and also I do not use Windows Paging file set-up (I cannot imagine this would cause any problem - but will check it out) 

2 I selected ALL options from the ubanto menu and each ends up with the screen dump I refer to INCLUDING ubiquitos safe graphics mode.

3 The iso file was burnt ok, as I noticed my write speed did not exceed 4x during the write process (a reccolection not a deliberate observation on my part) 

4 There was a previous posting referring to problems with X series of ATI cards - which, although My card is 9550  could still be a problem. 

5 p-quarles -  What is the alternate CD? 

FINALLY - thanks TO ALL OF YOU for all your efforts 
- I know that between us  we'll get my little machine on the Ubantu road - Yes!!:p:p:p:p

---

### Post by steveneddy on 2007-06-11
> **Living_Legend said:**
> Hi Readers, I'm having a little difficulty getting Ubantu to install. My progress accords with the Ubantu documentation and instructions and are described here:-
 

It's spelled Ub**u**ntu

some of your commands if you are typing them in may come out wrong if you are spelling them incorrectly

---

### Post by p_quarles on 2007-06-11
The Alternate CD is an .ISO that is better at installing itself on difficult systems. You can get it by going to the normal Ubuntu download page:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Directly underneath the "Start Download" button there's a check button that asks if you want the Alternate CD. I've managed to install Ubuntu this way on a couple systems that wouldn't work with the Live CD.

---

### Post by Living_Legend on 2007-06-11
Hi There everyone

Firstly - apologies for my incorrect spelling of Ubuntu. No defence. Free cups of coffe all round....

One thing I am going to try is formatting the disk to NT format and re-burning the iso file - I Will of course let you all know through this thread - iif this works. Also I have the same problem as another Compaq presario owner refered to by one of you kind people and have sent him a note too.

Regards to all and continued thanks

Living_Legend  :p:p:p:p:p

---

### Post by p_quarles on 2007-06-11
I don't see why you would need to format any disks. Ubuntu is more than capable of reading any file system that Windows uses. 

Anyway, just try the alternate CD, and install it on an unused portion of your hard drive (at least 10 GB, but preferably a lot more than that). I'm willing to bet that that will work for you.

---

### Post by jackiecanev2 on 2007-06-12
this is a shot in the dark, but try 6.10; i had edgy first, played with my partitions, wiped everything, and went to clean install feisty in a dell with an ATI card and the darn thing just won't play nice with my system. it couldn't get past first base with my video card to even boot the liveCD, let alone install. so i just went back to my old edgy cd, which ran fine, and then updated and upgraded to feisty.

---

### Post by Living_Legend on 2007-06-12
Hi There everybody who responded to this post.....

Well I've done and did just about everything to get started and to boot (excuse the pun) I have not been short on receiving well intentioned advice - but now I have decided that there is just too much effort and work to input and so little to show for the effort - reminds me of microsofts early days when we were all prancing around with MSDOS 3.4 etc etc. I do not mind using command line instructions at all (I also do write c++ programs) but it seems to me that at present running linux is just a tad too much of a pain (reminding me of the early days in computing. Perhaps a couple of years will be the right time for me to re-enter)

However even though it was a very brief stay it was non the less a  pleasant one.

Thanks for those well intentioned helping hands.

Living_Legend :p:p:p:p:p:p:

---

