---
title: "still can't install but CDs good md5 sum"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by kchukchukchu on 2006-04-14
hello, everyone,

I hope you don't think I am just whining, but I have checked sum for both installer CDs AFTER it's burned and the sums are the same as the one on the website, but the installation stopped at "installing base system" so I am just asking for suggestions here, other than physically moving the computer around as suggested here [http://www.ubuntuforums.org/showthread.php?t=113925&page=2](http://www.ubuntuforums.org/showthread.php?t=113925&page=2), which I will try when I get home.

I have burned the iso at 8x too.  but I thought the check sum being ok meant that the CD's are ok...

But it is funny because during the installation, when I "checked integrity" of CD, the test failed.  So does that mean my hardward is not ok?

Thanks for your help in advance again, I'm so glad you are here:),
K

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=kchukchukchu]hello, everyone,

I hope you don't think I am just whining, but I have checked sum for both installer CDs AFTER it's burned and the sums are the same as the one on the website, but the installation stopped at "installing base system" so I am just asking for suggestions here, other than physically moving the computer around as suggested here [http://www.ubuntuforums.org/showthread.php?t=113925&page=2](http://www.ubuntuforums.org/showthread.php?t=113925&page=2), which I will try when I get home.

I have burned the iso at 8x too.  but I thought the check sum being ok meant that the CD's are ok...

But it is funny because during the installation, when I "checked integrity" of CD, the test failed.  So does that mean my hardward is not ok?

Thanks for your help in advance again, I'm so glad you are here:),
K[/QUOTE]
Try burning at 4x. Then it should work.

---

### Post by confused57 on 2006-04-14
Don't know the specs of your computer, but have you tried downloading and trying a LiveCD, which just runs off ram memory(don't know if you have enough ram or not)?   I use Nero, which won't burn as an image lower than 8X and haven't had any problems installing with any iso's I've downloaded and burned, maybe just lucky.  May want to try the LiveCD, if you haven't already. Good Luck.

---

### Post by kchukchukchu on 2006-04-15
Hello, masterchief and confused,

Thank you for your quick responses!  

I also have the problem that my mac doesn't burn below 8x, and haven't tried a live CD.  (I only have 128Mb ram)   but I just found out that I can burn an image as a "Cd/DVD Master" using Mac's disk utility, so I'll try that first as well as moving my computer (my floor is not very level) to see if it succeeds.  

Thanks for your suggestions,
hope you're doing well
K

---

### Post by confused57 on 2006-04-15
Just a note, you do MD5 checksums on the iso that you downloaded; I don't know if you can do it after the CD is burned.  Checksum just tells you that the iso you downloaded matches the MD5 checksum from the site you downloaded the iso from and downloaded successfully(not corrupted).
    I rather doubt that Breezy will run very well with 128 mb of RAM.  After you get a LiveCD iso downloaded, do MD5 checksum, and burn image to CD; if it doesn't work on your computer, you may want to try it on another computer(a friend's maybe) to rule out possible problems with your CD burner(the LiveCD doesn't install to the HD).  Back to your system memory, you may want to check out some threads about installing Xubuntu, which doesn't require as much system memory resources.  Basically, you'd end up doing a server install, then at the command prompt type in something like:  sudo apt-get install xubuntu-desktop(not sure exactly).   I'm just a newbie too, but I'd like to see you succeed in getting Ubuntu installed, it's a pretty decent OS.   Hopefully,  someone who really can lead you in the right direction will see this thread and give you some expert instructions.

---

### Post by confused57 on 2006-04-15
I should have mentioned, if you're just wanting to try out Linux; you may want to look at PuppyLinux.  It's a small download(62 Mb, I think), a liveCD that you can try without having to download a larger distro LiveCD.  May be helpful in troubleshooting some of your problems.

---

### Post by kchukchukchu on 2006-04-15
Hey, thanks for your quick reponses and pointer to the xubuntu and puppy linux. I was planning to do a server install of ubuntu (I dont' know the difference really the server version of ubuntu and xubuntu) and then install fluxbox, as I have read that it is quite minimal.

The thing with the CD is, I did copy the image back onto the harddisk and check sum AFTER it's burnt and the sum is the right!  So, I 'm not even sure if it's the CD. But then during the install, I used the "checked CD integrity" function on the installer and there was an error then.  I don't understand this.

just for the record: the thing I figured out about burning a CD/DVD master on MAC was actually for creating a CD master image from files rather than an already existing image, so that didn't do what i wanted. 

I do want to install ubuntu because my friend recommended it and because ppl here are so nice and helpful. (I am truely impressed).  but I am just feeling quite tired and frustrated cuz it's been more than a whole week!

I will try moving my computer around (that's my only hope at the moment for ubuntu) to see if the angle at which the CD drive is sitting makes any difference.

Thanks for wanting my installation to succeed, I want it to too!
and thanks again for your help,
K

---

### Post by therunnyman on 2006-04-15
Hi guys,

That's a great thread...That may work, I don't know, but I do believe you should try everything.

Here's something that'll happen with prefab machines (such as Mac and Dell and whatnot): they'll screw the optical drive in with all 4 screws.  This can distort the drive, and cause all manner of problems.  My suggestion: pull all but three screws.  That fixes that.

What I'm guessing, ku, is that you've done everything correctly; your drive is at fault.  The sectors you're taking about (the "broken" item) are clear way out on the disc, which indicates to me you've got some kind of buffer-underrun protection enabled.  Buffer-underrun - someone ought to sue these guys - is repurposed in high-speed drives (that is, anything above 16x capability).

The laser stops writing whenever buffer-underrun technology is invoked.  This is bad, for a lot of reasons, not the least of which being this is exactly what used to produce coasters back in the day.

A possible solution: locate "enable BURNProof" or "JustLink" or even "buffer-underrun protection" in your software and disable it.  Typically you'll see it among burn options at the burn dialog ("burn DAO,"  "Burn TAO," Speed: 16x" and so on.  Then burn at a maximum of 12x.  That's good policy for all burns; if you don't have the patience for 12x, let me know, and I'll alert the FBI that you're not to have firearms.

therunnyman

---

### Post by bubi73 on 2006-04-15
I also had problems installing Ubuntu after burning it 8x (on a PC with Nero however). Then I tried to burn the image with Alcohol at full speed and had no problems installing.

Also, there is also another small distro call DSL ([www.damnsmalllinux.org)](www.damnsmalllinux.org)). It is roughly 50 MB and can even be run on a USB stick. The website claims that it can be run on 128 MB. Might want to give it a shot too.

---

### Post by Goatee on 2006-04-15
In K3B you just select verify written data.
It will compare the images MD5 sum and the burnt disk's.
Nero won't, mine didn't work from Nero.

Hope that helps8)

---

### Post by kchukchukchu on 2006-04-16
Hello, runnyman, bubi73 and Goatee,

I didn't even know that you responded until now!  Thanks for replying and suggesting things for me to try.

 I am going to try unscrewing the screws when i get home . 

But I don't see any buffer-underrun protection ( you mean in the burning software right?)  I chose the lowest speed (8x) and I burnt it using the Mac Disk Utility.

I just checked sum again for the 2 CDs that I have (downloaded the images from the CD and checksummed), and they both turned out correct. I am going to check again on this windows machine for the sum and then see what happens.   

I don't understand what's happening really. so you think it's my CD drive's problem?  I am suspecting that and it seems like there have been other ppl who changed their CD drives and then it worked. (but I don't have any CD drive to change to)

Then I have looked through many thread and there are these other suggestions (in case someone also have the problem):
1. enable DMA (I checked my DMA setting is in Mode 2 in my BIOS i dont know what that means but I couldn't change it there)
2. turn off acpi
3. take off extra components inside the computer and dust it
4. try burning another CD with another make and software (but I dont' get it, my CD images have good checksums, just not on the machine that I am installing in! )
5.  some people also have solved the problem by changing the video card driver/selecting a time zone matching with their machine's time zone. etc.  

I wil give these CDs more checks right now to see if it checked out ok on both window's machine and Mac machine, just to figure out if it's the CD's or not..

THANKS AGAIN, I hope you're doing great. AND I HOPE MY THING WORKS SOON!!!!!! I have been frowning for it for a whole week..

Kay

---

### Post by kchukchukchu on 2006-04-16
hello, everyone, 

Just an update that I just used isobuster windows to double check the CD's MD5 sums and they both turned out correct.  So I think it's not my CDs' problem(?). although during the install, the CD faild the integrity check on the installer.

Here is another thread that has the same problem as i do [http://ubuntuforums.org/showthread.php?t=136048&highlight=isobuster](http://ubuntuforums.org/showthread.php?t=136048&highlight=isobuster)

If you have any ideas for me, I'd really appreciate it. 

I'm going to try all the different things tonight.

THANKS for your hand so far!!!

Kay




[http://ubuntuforums.org/showthread.php?t=136048&highlight=isobuster](http://ubuntuforums.org/showthread.php?t=136048&highlight=isobuster)

---

### Post by kchukchukchu on 2006-04-18
Hello, all,

just an update that I have tried enabling DMA as suggested by different people, by opening a console (ctrl-alt-f2) after it scanned CDrom and load from CDRom and doing hdparm -d1 /dev/hdc.  

but when I do that, the error nothing will even start loading, the error became " CDrom not detected" something like please ensure that the breezy install CD is inserted.  

I have no idea what's going on.

I also checked the errors that I have when the DMA is not enabled. It seems to basically say "cp: read error: input/output error" during install base-system. and it would fail at different point.
 
Again, I recopied the iso from burned CD and the checksum turned out good using two machines and two software.  Do I still need to suspect the quality of my CDs?

Thanks for your help in advance,  I certainly hope that someone could help me out,
Kay

---

### Post by starchildmom on 2006-04-18
What brand of CD are you using and is it CD-R or CD-RW? I had the exact same problems you are describing. Good checksums, but disc after disc that would not work. I was using Memorex CD-RW. I tried burning it on two different machines with different burners at every speed. The problem was the brand or type of disc. I bought a spindle of Maxell CD-Rs. Burned a new disc at 4x from the same download that I had burned before and it worked great on the first try.

I spent two days trying to diagnose the problem, when in the end it was as simple as trying a different type of CD. If you have not already tried switching brands of media, I would suggest giving it a try.

---

### Post by kchukchukchu on 2006-04-18
Hey starchildmom,
Thanks for your reply and sharing of experience!

But do you mean that you also had good checksums FOR the burnt CD images as well?  I dont' mean the sums for the downloaded image, but the image that is copied back from the CD.  Did you have good check sum for the CD images when you copied back too for the bad brand disk?
I'd be happy if you'd let me know, thanks:)
K

---

### Post by starchildmom on 2006-04-18
I only checked the checksums before I burned them. The disc integrity check in the installer did fail on the bad discs, at least the ones that I could get that far.

---

