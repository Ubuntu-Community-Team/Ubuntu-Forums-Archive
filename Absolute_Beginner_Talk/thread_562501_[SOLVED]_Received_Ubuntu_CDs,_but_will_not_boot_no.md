---
title: "[SOLVED] Received Ubuntu CDs, but will not boot no matter what"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by teabuntu on 2007-09-28

Hello,
I received my set of CDs (Ubuntu, Kubuntu and Edubuntu) yesterday from Canonical.  I followed instructions for doing a one time boot with my laptop (Dell Inspiron 640M) to run a Live CD, and also, placed the CDs in to run it from Windows because it says on the package that came with the CDs that you can do that to look at the Windows version of some of the programs on the CDs, but my CD/DVD drive just keep on doing something over and over again in a loop till it stops completely.

I have also allowed the CDs to run without specifically setting up my laptop to booting from the CD.  According to instructions on running a Live CD, you just pop the CD in, and restart the computer.  I did that first, but since that did not work, I set up my computer to do a one time boot from the CD/DVD drive.  But as I mention above, that did not work either, no matter how many times I tried. 

The strange thing is, my package was first sent to Iran of all places.  I live in Canada, and there was this stamp saying: "Missent to Iran."  None of the CDs work and it seems that they may be all defective in some way.  My CD/DVD player is doing fine, since it works when I put in other discs aside from Ubuntu CDs.

Any advice on this strange experience would be greatly appreciated.  
Thank you,
Teabuntu

---

### Post by thiebaude on 2007-09-28
Are you trying to install ubuntu from windows?

---

### Post by Dr Small on 2007-09-28
Maybe you could try downloading the ISO and burning it to cd ?

---

### Post by brennydoogles on 2007-09-28
> **teabuntu said:**
> Hello,
I received my set of CDs (Ubuntu, Kubuntu and Edubuntu) yesterday from Canonical.  I followed instructions for doing a one time boot with my laptop (Dell Inspiron 640M) to run a Live CD, and also, placed the CDs in to run it from Windows because it says on the package that came with the CDs that you can do that to look at the Windows version of some of the programs on the CDs, but my CD/DVD drive just keep on doing something over and over again in a loop till it stops completely.

I have also allowed the CDs to run without specifically setting up my laptop to booting from the CD.  According to instructions on running a Live CD, you just pop the CD in, and restart the computer.  I did that first, but since that did not work, I set up my computer to do a one time boot from the CD/DVD drive.  But as I mention above, that did not work either, no matter how many times I tried. 

The strange thing is, my package was first sent to Iran of all places.  I live in Canada, and there was this stamp saying: "Missent to Iran."  None of the CDs work and it seems that they may be all defective in some way.  My CD/DVD player is doing fine, since it works when I put in other discs aside from Ubuntu CDs.

Any advice on this strange experience would be greatly appreciated.  
Thank you,
Teabuntu

Ok, so let me make sure I understand the issue... when you insert the cd while booted into windows, nothing happens, and when you reboot with the disk in the drive nothing happens either? It sounds to me like either a bad burn, or somehow the disks were damaged. If you have a program on windows to burn ISO images to disk (most cd burning apps will), you can download [this]("http://ubuntu.cs.utah.edu/releases/feisty/ubuntu-7.04-desktop-i386.iso") ISO and burn it to a disk and try that (by the way, this is the 32-bit live cd that should work for most computers. If you need something else, you can find it and download it [here]("http://www.ubuntu.com/getubuntu/download")) I hope that helps!!

p.s.- try exploring the cd in windows explorer. Sounds unlikely, but maybe you somehow got sent blank disks??

---

### Post by teabuntu on 2007-09-28

Hello,
Thank you for your replies.  No, I'm not trying to install it, I'm trying to run the LiveCD so that I can at least take a look at what Ubuntu is all about.  This is my first time venturing into the world of Linux and as for downloading the ISO image, I do not have the means to do so, which is why I requested the CDs.

Thank you.

---

### Post by brennydoogles on 2007-09-28
> **teabuntu said:**
> Hello,
Thank you for your replies.  No, I'm not trying to install it, I'm trying to run the LiveCD so that I can at least take a look at what Ubuntu is all about.  This is my first time venturing into the world of Linux and as for downloading the ISO image, I do not have the means to do so, which is why I requested the CDs.

Thank you.

Ok, have you done anything in BIOS to allow your computer to boot from CD?? Also please list your computer's specs (processor speed and ram if you can, but mostly ram) and let's see if we can get you up and running!!

---

### Post by teabuntu on 2007-09-28
brennydoogles,
Thank you for your reply.  I did 2 things with the CD: first, while in windows, I put the CD in, then did restart.  The computer jsut ignored the CD and booted to Windows.  So, I followed the instructions on my owner's manual for my laptop that tells you have to do a one time boot from a disc.  To do this, you start with the computer turned off completely, but with the disc inside the optical drive.  You turn on the computer, and hit F12 when the Dell logo comes on, and you select boot from CD/DVD, then instead of booting from the CD, the computer went balnk for a while, and then booted from Windows.  I tried a number of times, but I always got the same result: booting to Windows.

As for checking out the disc, I can not even do that.  The moment I pop the CD in while in Windows, the optical drive goes into a loop, making the same sounds over and over to a point I think the optical drive is going to break.  Then, it stops completely.  But it takes a long while to stop completely.  All the CDs that I received to that.  So yes, I do think there's something wrong with the CDs.

Forgive me for being suspicious, but since the CDs first went to Iran, could they have rendered the discs inoperable somehow?  Can any kind of X-ray scans or scans of any kind render CDs inoperable?  

I guess that would mean that the CDs are permanently damaged and can not be used?  Or is there some other way? 

Thank you for any advice or help on this matter,
Teabuntu

---

### Post by Drakkor on 2007-09-28
> I set up my computer to do a one time boot from the CD/DVD drive
As far as I know , you have to set the CD to boot in the bios, and it will boot to the CD always, unless you change it back to the hard drive boot.

---

### Post by teabuntu on 2007-09-28
No, I have not gone and changed anything in the BIOS, which is why I used the one time boot method that is the same as changing the BIOS, but without permanentely doing so.

As for my processor speed, well, I have Intel 2.0GHZ, Centrino duo, RAM is 512MB.  Does this help?

Thanks.

---

### Post by Drakkor on 2007-09-28
Re-reading your comments, are you sure that the optical drive itself is good ?
If it won't boot from it. I would go into the Bios and have it boot only from the CD, not anything else. and see what happens.

---

### Post by Drakkor on 2007-09-28
Your specs are exactly like mine and should run, no problem.

---

### Post by bodhi.zazen on 2007-09-28
You need to change your BIOS to boot from the CD drive first ...

This will not harm your installation.

Other then that, I am not sure about your exact version of BIOS ...

---

### Post by brennydoogles on 2007-09-28
> **teabuntu said:**
> No, I have not gone and changed anything in the BIOS, which is why I used the one time boot method that is the same as changing the BIOS, but without permanentely doing so.

As for my processor speed, well, I have Intel 2.0GHZ, Centrino duo, RAM is 512MB.  Does this help?

Thanks.

Ok, here is my first recommendation: Without the disk in the drive, restart your computer, and press F12 (or whatever it says will boot you into BIOS) Somewhere in your BIOS, there will be an option to change the boot order of your computer. Set this to your optical drive. What this will do is allow you to boot from CD whenever there is a bootable disk in the drive, and when there is no disk, you will go straight into windows (or hopefully soon Ubuntu if you install it). Now restart, put the disk in, and restart again. Remember to save the changes to your BIOS, or else you will get the same issues. Hopefully, this will have you in a working LiveCD environment. If it doesn't, then I would assume that the live CD's are damaged in some way. As for their side trip to Iran, I don't think there is much they could have done to them other than mishandle them and break them, so it must just be a coincidence. Hope everything goes well!!

---

### Post by handydan918 on 2007-09-28
One other possibility comes to mind. Some laptops seem to not do a full reboot when you select "restart" in windows. i think you should try 
a) actually changing the boot order in the BIOS, and 
b)doing a "hard" shudown of the machine prior to attempting to boot the live cd.
luck!

---

### Post by teabuntu on 2007-09-29
Yes, the optical drive is working perfectly.  I don't know much about computers, and so I'm quite reluctant to fiddle around with the BIOS especially, which is why I used the method that allows for what's called a "one time boot" from the CD/DVD drive that works jsut as htough you're changing the BIOS, but not permanently.

---

### Post by teabuntu on 2007-09-29
Thank you all for your comments, I just read the ones that were posted prior to my one just above.  I have done a hard shut down and then tried booting the Live Cd, but to no avail.  I think one of the posters above mentioend that perhaps the CD is blank?  Have you heard of anyone else having a similar issue in the past?  Thank you for your time and help on this matter.

---

### Post by bodhi.zazen on 2007-09-29
Well, if your optical drive is working you can look at the contents of the disk from windows.

---

### Post by teabuntu on 2007-09-29
As I mention in one of my posts, I've tried to look at the CD while in Windows, but not able to.

---

### Post by Frank Golden on 2007-09-29
Hi teabuntu,
   What version of Ubuntu are you trying to run? I don't have Kubuntu or Edubuntu .iso's downloaded, but I do have Ubuntu 6.06.1 LTS (dapper), Ubuntu 6.10 (edgy) and Ubuntu 7.04 (feisty), both Live CD and alternate. I can make bootable disks of these for you and send them to you or prepare a DVD on a DVD+RW with the .iso's on them that you can burn yourself .if you want the DVD with the raw .iso's I will check the MD5 
hashes on each one to make sure they copied correctly to the DVD.
If you want already burned CD's I will make sure they at least boot from my drive for you. If they boot for you and you want to install you can check the integrity of the disk from the disk startup menu. Sorry the disks from Cannonical seem to be bad. I have all three versions of Ubuntu installed on an external HDD as well as Feisty permanently installed on my laptops internal drive. PM me with your address if you are interested. I will try not to send to Iran. LOL. At least you will get them faster than from Cannonical. It is my hope that you can at least get the Live CD to work so you can see if your hardware vwill behave with Ubuntu (most does) or install it to your hard drive. It is quite easy to install dual boot, on the same drive as windows. I you choose to do a dual boot the tutorial linked to below can help immensly.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

Sorry for the bad experience you seem to be having, don't give up on Ubuntu. It really is worth it.

---

### Post by kmg_12 on 2007-09-29
Even though you are using the one time boot method (F12) so you don't need to change the bios, I'd suggest changing the Bios just in case. Also watch out as text might appear on the screen asking you to press a key to boot from the CD.

---

### Post by vikasmk on 2007-09-29
ya, like the guy above me. reset boot priority to cd rom. and then try booting

---

### Post by brennydoogles on 2007-09-29
> **teabuntu said:**
> Yes, the optical drive is working perfectly.  I don't know much about computers, and so I'm quite reluctant to fiddle around with the BIOS especially, which is why I used the method that allows for what's called a "one time boot" from the CD/DVD drive that works jsut as htough you're changing the BIOS, but not permanently.

I can see that you are a bit hesitant to change the boot order, but know this... boot order is about the safest BIOS option you can change... I have never heard of anyone having any problems related to boot order (other than the one you're having!!). If that's the only thing keeping you from changing it up, don't hesitate on that account, it really is safe.

---

### Post by bodhi.zazen on 2007-09-29
> **teabuntu said:**
> As I mention in one of my posts, I've tried to look at the CD while in Windows, but not able to.

If you can not read the contents of the CD then either the optical drive is not working or you have a defective CD.

---

### Post by teabuntu on 2007-09-29
Hello,
Thank you for your replies.  As for changing the BIOS settings, how would I go about in changing it back to the way it was.  I have looked at the BIOS settings, but I don't have any instructions to say do this and that.  Another reason for my reluctance in fiddling around my computer at this point: my computer is becoming unstable, I have lost the ability to use the Mediadirect button from the power off position, and since installing software for my USB keyboard, I can not use the button while in Windows either.  I've done a number of PC Restores by Symantec to revert my system back to the way it was when it was shipped late last year.  Anyway, I think the CD is likely to be defective, since I can not even get to look at the Windows version of programs on the CD, or look at the contents of the CDs.  Thanks guys for your help on this.  I think I will have to ask Shipit for another copy.

---

### Post by teabuntu on 2007-09-29
Hello Frank Golden,
I just sent you a PM, please have a look.  Thank you,
Teabuntu

---

### Post by teabuntu on 2007-09-30
I did a one time boot sequence using a different disc (windows related), and it works, so I think the Ubuntu CDs are somehow damaged or defective.  which means have to get another copy of the CDs.  Thank you to everyone who pitched in to help.  I appreciate all your help, and for spending your time to find a resolution to this issue.

---

### Post by brennydoogles on 2007-09-30
> **teabuntu said:**
> I did a one time boot sequence using a different disc (windows related), and it works, so I think the Ubuntu CDs are somehow damaged or defective.  which means have to get another copy of the CDs.  Thank you to everyone who pitched in to help.  I appreciate all your help, and for spending your time to find a resolution to this issue.

That's no problem at all. If you consider the issue resolved it is a good idea to go to thread tools (up top) and "mark thread as resolved". Good luck once you get new cd's!!

---

### Post by teabuntu on 2007-09-30
Thanks! Looks like someone did put the "solved" in the subject line.

---

### Post by Roaster on 2007-09-30
Just as an aside, on nearly all computers the boot order in the BIOS is; floppy(if it has a floppy drive) cd-rom, hard drive. When you put a bootable cd in the drive the computer looks for the first bootable media and will tell you to 'press any key to boot from cd'. In most cases it is not necessary to go into the BIOS and change anything, in my experience.

---

### Post by brennydoogles on 2007-09-30
> **Roaster said:**
> Just as an aside, on nearly all computers the boot order in the BIOS is; floppy(if it has a floppy drive) cd-rom, hard drive. When you put a bootable cd in the drive the computer looks for the first bootable media and will tell you to 'press any key to boot from cd'. In most cases it is not necessary to go into the BIOS and change anything, in my experience.

My Dell was shipped with the First hard drive being the first in the boot order, and I think the original poster said his was a dell also. It must be dell-specific.

---

### Post by bodhi.zazen on 2007-09-30
> **Roaster said:**
> Just as an aside, on nearly all computers the boot order in the BIOS is; floppy(if it has a floppy drive) cd-rom, hard drive. When you put a bootable cd in the drive the computer looks for the first bootable media and will tell you to 'press any key to boot from cd'. In most cases it is not necessary to go into the BIOS and change anything, in my experience.

In my experience as well, Not so much any more ...

This used to be the case, but I have seen a ton of exceptions over the last 6-12 months ...

My *guess* is people are becoming more conscious of the damage a live CD can do, so have changed the BIOS. Obviously it will slow down only the casual cracker ...

Just a guess ...

---

### Post by teabuntu on 2007-10-01
Hi,
You mention that Live CDs can damage a computer?  I thought it ddn't.  If so, how does it damage a computer?  Thanks.

---

### Post by antisocialist on 2007-10-01
compaq and toshiba both boot 
hdd->fdd->cd-rom drive
at least mine do, so its not just dell

---

### Post by brennydoogles on 2007-10-01
> **teabuntu said:**
> Hi,
You mention that Live CDs can damage a computer?  I thought it ddn't.  If so, how does it damage a computer?  Thanks.

Well, it's less that live CD's can damage a computer, and more that a person can use a live cd to bypass security on your computer if they can have access to it. The Live CD itself won't hurt your computer.

---

### Post by teabuntu on 2007-10-02
hmmmm... I'm not sure I follow what you mean by people bypassing their security on their computer.  Do you mean while using the LiveCD? Thanks.

---

### Post by candtalan on 2007-10-02
> **teabuntu said:**
> hmmmm... I'm not sure I follow what you mean by people bypassing their security on their computer.  Do you mean while using the LiveCD? Thanks.

Live CDs usually allow the user to 'install' the CD OS, which may cause many complications if the action is not done advisedly - not least possibly totally erase the existing OS!

It is also easy to mess with partitions, which, again, if done without knowledge, can cause big time disaster.
hth

---

### Post by bodhi.zazen on 2007-10-02
> **teabuntu said:**
> hmmmm... I'm not sure I follow what you mean by people bypassing their security on their computer.  Do you mean while using the LiveCD? Thanks.

Physical access = bad news. With a live CD you do almost anything you wish.

---

### Post by brennydoogles on 2007-10-02
> **bodhi.zazen said:**
> Physical access = bad news. With a live CD you do almost anything you wish.

Basically let's say this... If you had  naked pictures of your wife on your computer, but had a password on your windows box, I could pop in a live cd (if I were at your house), post the pictures on the internet, and make sure your wife sees them. THAT is the kind of damage a live cd can cause. Does that make sense?

---

### Post by teabuntu on 2007-10-03
wow, I did not know such a thing was possible.  So you're basically saying that using the LiveCd, you can break into the Windows password?

---

### Post by brennydoogles on 2007-10-03
> **teabuntu said:**
> wow, I did not know such a thing was possible.  So you're basically saying that using the LiveCd, you can break into the Windows password?

he he he.... Yes indeed. In fact, my most recent project has been helping a buddy of mine get some stuff back from his old computer that way by writing a bash script. Fun Times!!

---

### Post by Mr_JMM on 2007-10-03
I'm new to this but to pass on my limited experience...

The only way I could get my laptop to boot an Ubuntu CD was to make a bootable floppy disc with bcdl150z on it. You write this to a floppy using an image to floppy program, shut down the laptop/pc, insert floppy, if not already insert cd and turn on the laptop/PC.

You shouldn't have to worry about the BIOS. Literally just insert, turn on and go. After three days trying to get the Ubuntu CD to run, this worked first time.

This IS an Ubuntu / Linux thing as EVERY OTHER windows based software CD/DVD I have booted no problem first time everytime without the needing a bootable floppy.

I can't remember which thread I found this gem of info on but aothers are:
[http://ubuntuforums.org/showthread.php?t=465233&highlight=bcdl150z](http://ubuntuforums.org/showthread.php?t=465233&highlight=bcdl150z)
and
[http://ubuntuforums.org/showthread.php?t=81280&highlight=bcdl150z](http://ubuntuforums.org/showthread.php?t=81280&highlight=bcdl150z).

It's fairly easy but if you need help (getting the bcdl image onto the floppy is the hardest part requiring another program. I used rawritewin-0.7) then I'll try and run through the procedure. If we get really stuck I could do so via messenger or something and talk you through it but can't promise it'll be today.

---

### Post by teabuntu on 2007-10-03
Hello Mr_JMM, 
Thank you for your post.  I appreciate the offer, but the CDs that were sent to me are defective, and I'm waiting for Shipit to open so I can I ask them to send it again.  Thanks again for your kind offer.

---

### Post by teabuntu on 2007-10-03
Hi brennydoogles,
You make Ubuntu sound like a magic wand! I had no idea that you could do taht with the LiveCD, never crossed my mind.  Well, I am very new at this, but still.... it's a bit of a surprise to say the least.  So is there like a procedure that is posted somewhere on the internet for doing this?  I would guess that you don't jsut insert the LiveCD and it automatically cracks codes... I guess you would have to know some commands?  Does it mean that ANYTHING can be done to the computer while the LiveCD is in the computer?  Also, if the computer is connected to the internet while running the LiveCD, does this mean that someone can get into your computer and somehow use the LiveCD to do things to your computer?  
I realize I'm asking a lot of questions here, but this new piece of information about the LiveCD has got me quite curious....  Thanks for any advice on this.

---

### Post by brennydoogles on 2007-10-03
> **teabuntu said:**
> Hi brennydoogles,
You make Ubuntu sound like a magic wand! I had no idea that you could do taht with the LiveCD, never crossed my mind.  Well, I am very new at this, but still.... it's a bit of a surprise to say the least.  So is there like a procedure that is posted somewhere on the internet for doing this?  I would guess that you don't jsut insert the LiveCD and it automatically cracks codes... I guess you would have to know some commands?  Does it mean that ANYTHING can be done to the computer while the LiveCD is in the computer?  Also, if the computer is connected to the internet while running the LiveCD, does this mean that someone can get into your computer and somehow use the LiveCD to do things to your computer?  
I realize I'm asking a lot of questions here, but this new piece of information about the LiveCD has got me quite curious....  Thanks for any advice on this.

Think about it this way.... Your windows password is exactly that.... a password into windows. When you use a live cd, you are no longer in windows, so the windows password no longer applies. Hidden files are no longer hidden (unless they happen to have a . as the first character in the filename. It's not magic, just the advantage of a live cd. As for using a live cd over the internet.... not really something you need to worry about. If they can hack your computer that easily, you are safer in a live cd (which is Linux) than you ever were in windows.

---

