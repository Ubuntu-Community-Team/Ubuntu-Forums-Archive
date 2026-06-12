---
title: "3 Q's: 32bit vs 64bit, LiveCD problem, and hardware question."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by arcooke on 2007-06-14
I just have a few questions. Figured I'd cram them all into one topic.  This is my first time to give Linux a chance in the past 15+ years, so keep that in mind.

1.  I have a 64-bit processor.  I'm just wondering if there are any cons to using the 64-bit version of Ubuntu that I should know about, and does it have full support for 32-bit apps or will I be running into problems?

2.  I tried running the LiveCD (ubuntu-6.06.1-desktop-i386) to give it a test drive, and ran into some issues.  It got to the main menu, but when I try to actually run the OS, it ended up stalling at "mounting root file system".  After waiting about 2 or 3 minutes, the screen cleared and some I/O errors started to pop up every few seconds.  I took a picture: [http://i18.tinypic.com/67yt6k1.jpg](http://i18.tinypic.com/67yt6k1.jpg)  They just kept coming, so I ended up rebooting.  I burned the image in Nero 6 using the appropriate "burn an image" mode.  My ram is working just fine and I have plenty of it (2GB), so I'm not sure what it's complaining about.

3.  Just looking for an opinion here.  I'm considering running XP and Ubuntu as dual boot.  I have a 500GB SATA hard drive so space is plentiful.  I also have some spare 40+ gig IDE drives laying around.  Would you recommend I install Ubuntu on a partition of my main drive, or use a completely separate drive?  Ideally I'd use a 2nd computer, but I'm short a spare ATX case.


Thanks ;)


One last not-so-important question:  Would the latest version of Ubuntu run OK for testing on a 450mhz P3 with 256MB ram?

---

### Post by tgm4883 on 2007-06-14
> **arcooke said:**
> I just have a few questions. Figured I'd cram them all into one topic.  This is my first time to give Linux a chance in the past 15+ years, so keep that in mind.

1.  I have a 64-bit processor.  I'm just wondering if there are any cons to using the 64-bit version of Ubuntu that I should know about, and does it have full support for 32-bit apps or will I be running into problems?

2.  I tried running the LiveCD (ubuntu-6.06.1-desktop-i386) to give it a test drive, and ran into some issues.  It got to the main menu, but when I try to actually run the OS, it ended up stalling at "mounting root file system".  After waiting about 2 or 3 minutes, the screen cleared and some I/O errors started to pop up every few seconds.  I took a picture: [http://i18.tinypic.com/67yt6k1.jpg](http://i18.tinypic.com/67yt6k1.jpg)  They just kept coming, so I ended up rebooting.  I burned the image in Nero 6 using the appropriate "burn an image" mode.  My ram is working just fine and I have plenty of it (2GB), so I'm not sure what it's complaining about.

3.  Just looking for an opinion here.  I'm considering running XP and Ubuntu as dual boot.  I have a 500GB SATA hard drive so space is plentiful.  I also have some spare 40+ gig IDE drives laying around.  Would you recommend I install Ubuntu on a partition of my main drive, or use a completely separate drive?  Ideally I'd use a 2nd computer, but I'm short a spare ATX case.


Thanks ;)


One last not-so-important question:  Would the latest version of Ubuntu run OK for testing on a 450mhz P3 with 256MB ram?

1.  Read this first.  Many people will post their opinions on this issue and will try to influence you one way or the other (myself included)  I use 64-bit, and it works great for me, everything works just fine just like it did on 32-bit.  Some people will say do 32-bit since your new, but I disagree.  Read this before making a decision. [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

2.  Don't know

3.  My opinion would be to run XP in a virtual machine.  It's there at a moments notice, and IMO will help ween you off Windows.

LQ, Should work fine, you can use Xubuntu which is a version for older hardware.

---

### Post by loserboy on 2007-06-14
I'm by no means an expert....

I ran 64-bit for a while, I went back to 32-bit.... when I was running it most programs and such werent compiled for 64 so you had to do it yourself or find someone who has already.
I know I'm gonna catch heat for this but it's easier for now to run 32, although 64 has come a long way and the OS itself worked perfect for me back at 6.06 so I imagine it's pretty sweet now.

so for 1. if you wanna get your hands a little dirty for the 64-bit, if you're feeling lazy go with the 32-bit

2. not much i know about the error, I think "hdc" would be referring to the hard drive, do you have 3 different drives installed because usually it goes 
hda = 1st drive 
hdb = 2nd drive
hdc = 3rd drive
could be a loose cable on the drive I think that was the error i got once?

3. i think it's just a preference thing, I'd say just use the SATA

lastly, it **should** run, it meets the minimums, pretty much anything with 256 megs of ram should run

edit: oh whoops someone answered you while i was typing

---

### Post by jimrz on 2007-06-14
> **arcooke said:**
> I just have a few questions. Figured I'd cram them all into one topic.  This is my first time to give Linux a chance in the past 15+ years, so keep that in mind.

1.  I have a 64-bit processor.  I'm just wondering if there are any cons to using the 64-bit version of Ubuntu that I should know about, and does it have full support for 32-bit apps or will I be running into problems?

2.  I tried running the LiveCD (ubuntu-6.06.1-desktop-i386) to give it a test drive, and ran into some issues.  It got to the main menu, but when I try to actually run the OS, it ended up stalling at "mounting root file system".  After waiting about 2 or 3 minutes, the screen cleared and some I/O errors started to pop up every few seconds.  I took a picture: [http://i18.tinypic.com/67yt6k1.jpg](http://i18.tinypic.com/67yt6k1.jpg)  They just kept coming, so I ended up rebooting.  I burned the image in Nero 6 using the appropriate "burn an image" mode.  My ram is working just fine and I have plenty of it (2GB), so I'm not sure what it's complaining about.

3.  Just looking for an opinion here.  I'm considering running XP and Ubuntu as dual boot.  I have a 500GB SATA hard drive so space is plentiful.  I also have some spare 40+ gig IDE drives laying around.  Would you recommend I install Ubuntu on a partition of my main drive, or use a completely separate drive?  Ideally I'd use a 2nd computer, but I'm short a spare ATX case.


Thanks ;)


One last not-so-important question:  Would the latest version of Ubuntu run OK for testing on a 450mhz P3 with 256MB ram?

Welcome

1. there are some issues with 64-bit vs some applications, i believe flash and firefox are among them, and think i saw some reference to some driver issues, as well. unless you actually need to use some 64-bit apps i would suggest the 32-bit version. that is what i am using on my core2duo E6600 box, and it runs very nicely and blazingly fast. 

2. that image looks like it is having issues with your cr-rom. 
   a- did you do an md5sum check on your download and/or run the "check cd for defects" option on your burned disk? +  what speed did you burn your disk at? many experience probs with cd's burned @ high speed use 2x      or 4x or the lowest speed your burner will support and you will get better results. 
   b. i once got similar errors when trying to install to an older box for a friend. turned out it was a bad cd-rom drive. if your cd-rom is functioning normally for other uses, it is probably  a corrupt "live cd" either from a bad down load or burning at too high a speed.

3.  i have 2 dual boot machines 1  with single drive and 1 on separate sata2 drives. dual boot works equally well on both. there used to be issues try to mix sata and ide drives using the "j-micron" controller, but i beleive these have now been resolved.

4.   yes it will run it, but you are pretty near the minimum specs. for that machine you will find that Xubuntu will likely run much better than Ubuntu with the gnome desktop/software packages. Xubuntu uses xfce window manager and some lighter weight apps in the default packages.

---

### Post by Kilz on 2007-06-15
> **arcooke said:**
> I just have a few questions. Figured I'd cram them all into one topic.  This is my first time to give Linux a chance in the past 15+ years, so keep that in mind.

1.  I have a 64-bit processor.  I'm just wondering if there are any cons to using the 64-bit version of Ubuntu that I should know about, and does it have full support for 32-bit apps or will I be running into problems?

Unless you are running some oddball application (one that would give you problems on 32bit) you should have no problems running the 64bit version.  There is a less than 1% difference in packages according to launchpad. Some (less than 5) applications might require you to follow a cut and paste howto (same in 32bit), or run a simple setup script(same as 32bit). But you may not want or need those applications.
There is not full support for 32bit applications if you mean are there 32bit packages in the 64bit repositories. You may not need to install 32bit applications, but you can get them installed if you do. The number of 32bit applications people do install can be counted on the fingers of one hand. For those install scripts and howtos are available. Look in my signature for links to 2 popular scripts.
I suggest making this post [in the 64bit section,]("http://ubuntuforums.org/forumdisplay.php?f=134") what you are going to get in this section are responses from people running the 32bit version. They will have no idea, but some will respond with old , outdated information in a misguided attempt to help you.


> **jimrz said:**
> Welcome

1. there are some issues with 64-bit vs some applications, i believe flash and firefox are among them, and think i saw some reference to some driver issues, as well. unless you actually need to use some 64-bit apps i would suggest the 32-bit version. that is what i am using on my core2duo E6600 box, and it runs very nicely and blazingly fast. 


I see that FUD is alive and well in the absolute beginners forum. I see that everyone chips in to try and convince people to use a 32bit operating system on their 64bit hardware.
Flash and firefox are not problems for 64bit. They havent been since Dapper when I wrote my first script. Sadly those that dont use the 64bit edition seem to think that information 3 versions old still holds true.

---

### Post by arcooke on 2007-06-15
Thank you all for your responses. 

1.  I suppose I should have been more clear about this question.  I know the linux community doesn't like being compared with MS in any way, but hear me out.  I attended a MS webcast pre-Vista and they were mostly talking about 64-bit computing.  They said in the 64-bit version of Vista, there will be some sort of module (or emulator?) that will run all 32-bit applications on a 64-bit platform.   So say, for example, I download a 3D game for linux that doesn't list any downloads for a 64-bit platform, will said game run on 64-bit ubuntu or will it start spitting out errors?  I'm just wondering if Ubuntu has any sort of feature like this.  Is this making any sense?

2.  It very well may have been the burn speed.  I did download the LiveCD directly from this site, but I also did burn it at maximum speed.  Not only that, but since I don't have any 700MB blank cds (just DVDRs and old 650MB cds) I had to burn the ISO to a DVD.  The option to do that was available in Nero when I burned it.


What really bothers me is that I'm not even sure I have any reason to use linux in the first place.  Just about everything I do the computer is completely reliant on Windows software.  I'm a graphic designer, and I use Photoshop, Illustrator and Quark pretty much daily.  When I'm not doing graphics, I'm either playing computer games or just screwing around on the internet.   Unfortunately the only thing I'm really able to do on linux in my situation is screw around on the internet.  So is there even any real reason for me to mess with Ubuntu in the first place?  I don't know.  The part that bothers me is that I'm so incredibly anxious to finally make the switch.. but I'm not sure it will be worth it because I'm forced to stick with MS for 99% of what I do due to the software I use. ](*,)  (<--- what an appropriate emote.. MS is the brick wall, the yellow guy is me)

I swear, if one BIG software company (like Adobe), and one BIG game compaing (like UBISoft) would start supporting linux, it would change the world.  People would follow. 

Anyway, I guess I'm going to have to figure that out on my own.  

Thanks again guys.

---

### Post by Wynne G Oldman on 2007-06-15
I'm a complete newbie, but I'd recommend the 64 bit version. On my PC it worked better than the 32 bit version. You'll probably have minor issues with both versions, but they're curable with the help of this excellent forum, so you might as well go for the performance boost that the 64 bit version has to offer.

---

### Post by loserboy on 2007-06-15
making the switch is completely up to you, but I would definately recommend dual booting for a while and see if it can fit your needs. some people find that they like the alternative software better...and some don't.  Theres also a program called wine that supports alot of windows apps [www.winehq.com](www.winehq.com) look at the appDB maybe some programs that you have can be used through wine.

you're going to see new commercial software become available for linux at a progressive rate, already I see good stuff almost everyday.

you'd have to ask kilz or someone with more experience than me on the other question

---

