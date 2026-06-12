---
title: "[SOLVED] Display help!!!"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-02-05
Im absolutely new to this so please bear with me....

Having been brought up on DOS and Windows since I care to remember, I decided to have a go with Linux and see what its all about - I know nothing about it other than what I have read on these forums and in magazines and its all Chinese to me so far.

I downloaded Ubuntu 6.10 ISO and burned it.  I tried to boot and got the Ubunto menu screen selecting the first option to run/install etc.  At this point everything looks normal but after the orange bar has finished doing its thing, I just get a screen of green and purple lines and a message on my monitor saying "Out of range".  Ive tried all the screen options by pressing f4 at the menu, none of which make any difference.  I cant think what else to try as I cant seem to change any other settings.  My monitor sets its own resolution so I cant change that - its an Asus VW192s LCD screen and im running a GeForce FX5800, AMD 64 3700+ on a gigabyte KN8 Nforce4 board.  

I really dont know what else to try so any help getting over this unpromising start to my Linux adventure would be really appreciated.  I have looked through the threads on here for similar problems and no one seems to have the one I have, at least, they all have some sort of desktop which they can play about with - I cant even get that!!  There is also no match on google for this.

any ideas welcome!

---

### Post by tocleora on 2007-02-05
Aaah it's been a while so I hope I don't misinform you, but I believe there's a way to run the install in text mode.  If I'm reading this page correctly you'll need the alternative CD to use it:

[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu)

With this you should be able to get Ubuntu installed... Not sure if this will help as you may continue to have the problem past that, but at least this would get you a little closer. ;)

---

### Post by ed-j on 2007-02-05
> **MikeSz said:**
> Im absolutely new to this so please bear with me....

Having been brought up on DOS and Windows since I care to remember, I decided to have a go with Linux and see what its all about - I know nothing about it other than what I have read on these forums and in magazines and its all Chinese to me so far.

I downloaded Ubuntu 6.10 ISO and burned it.  I tried to boot and got the Ubunto menu screen selecting the first option to run/install etc.  At this point everything looks normal but after the orange bar has finished doing its thing, I just get a screen of green and purple lines and a message on my monitor saying "Out of range".  Ive tried all the screen options by pressing f4 at the menu, none of which make any difference.  I cant think what else to try as I cant seem to change any other settings.  My monitor sets its own resolution so I cant change that - its an Asus VW192s LCD screen and im running a GeForce FX5800, AMD 64 3700+ on a gigabyte KN8 Nforce4 board.  

I really dont know what else to try so any help getting over this unpromising start to my Linux adventure would be really appreciated.  I have looked through the threads on here for similar problems and no one seems to have the one I have, at least, they all have some sort of desktop which they can play about with - I cant even get that!!  There is also no match on google for this.

any ideas welcome!

Reply from aNovice!

The only time I have seen "sync out of range" is when I've installed Ubuntu on a system with an Internet connection and then transfered the hard-drive to a system with no Internet connection. Is your Net connection directly from your motherboard or from a PCI card?

---

### Post by MikeSz on 2007-02-06
Hi There, thanks to the replies so far - il try the alternative CD out and see how that goes - On the subject of the net connection, I have a broadband connection that links by ethernet to a router.  None of the hard disks or network (physical) configurations have changed, I was simply going to install directly to an 8Gb partition (that is usually my Windows partition / C drive) that I set aside for my OS.  I have additional hard disks for storage of all my other stuff and they wouldnt have been affected anyway.  I tried Ubuntu 6.06 as well and got the same thing.  Il give the alternative CD a go and see if that makes any difference!

Thanks again and if anyone has any more suggestions I would really appreciate it!

---

### Post by ed-j on 2007-02-06
> **MikeSz said:**
> Hi There, thanks to the replies so far - il try the alternative CD out and see how that goes - On the subject of the net connection, I have a broadband connection that links by ethernet to a router.  None of the hard disks or network (physical) configurations have changed, I was simply going to install directly to an 8Gb partition (that is usually my Windows partition / C drive) that I set aside for my OS.  I have additional hard disks for storage of all my other stuff and they wouldnt have been affected anyway.  I tried Ubuntu 6.06 as well and got the same thing.  Il give the alternative CD a go and see if that makes any difference!

Thanks again and if anyone has any more suggestions I would really appreciate it!

I have my old system running UBUNTU 5.1 on 1 HD and WIN98 SE on a 2nd HD. I use the direct Motherboard Ethernet connection for UBUNTU, and the PCI NIC (Network Interface Connection) for WIN98 SE (This means changing the Ethernet cable from one to the other whilst the system is turned off). On my new system I use the Ethernet NIC on my Motherboard and run UBUNTU 6.1 exclusively. In theory, with the versions of UBUNTU, this should make no difference, but this has worked for me with no problems.

All the best!

---

### Post by tocleora on 2007-02-06
> **MikeSz said:**
> Thanks again and if anyone has any more suggestions I would really appreciate it!

I hate to recommend this, but this distro is about "people"... I've tried other distros from Red Hat to Fedora to Knoppix to even BSD (since 1997 I've been playing with Linux) and Ubuntu was the one that worked the best for *me* in the long run.  I've heard other people say the opposite though that Ubuntu didn't work for them but [insert distro here] did.  I've heard really good things about SUSE you may look at it as a second option if you can't get Ubuntu working.  And I have Fedora running on one of my servers (although all of my other servers are now Ubuntu).  So you might try one of those, but make sure you can't get Ubuntu working first! Hah! :)

---

### Post by MikeSz on 2007-02-07
Hi tocleora and thanks for the help!

Unfortunately im still no further forward - the link in your previous post is a really helpful explanation on how to go through the text install and I will refer to it when I try, however, there doesnt seem to be anywhere on this site where you can acquire the alternative install CD - the download section simply links back to the main ubuntu site for you to chose either 6.06 or 6.10.  Ive downloaded and burned both of these iso's and they both give me the same display problem.  Am I missing something really stupid?  

I have been playing around with the mini version of Sabayon 3.2 just to get a feel and its really hard to do anything with it so I would love to get ubuntu working - from what I have read its the best one to start off with for those, like me, who know nothing about Linux and have been brainwashed by DOS & Windows systems!!!! 

Any help (please bear in mind that I am a linux idiot) would be much appreciated!

---

### Post by ske1fr on 2007-02-07
No, you're not missing something really stupid, there is a bit of an oddity about the download page when I view it too.  No UK sources.  I went to the Kubuntu pages as they're more familiar and managed to navigate down to the sources, then back up the directories.

The UK source is [http://gb.releases.ubuntu.com/6.10/](http://gb.releases.ubuntu.com/6.10/) for Gnome Ubuntu.  The list of actual iso's is down the page.  This should get you what you want, although I'd be inclined to suggest you try Dapper Drake (6.06) for stability.  If you're playing with Sabayon then stability might not be your priority.  You shouldn't have any huge problems with straightforward X settings, I use an nVidia Force 4 board at home with no issues, but then I'm avoiding Beryl...

---

### Post by tocleora on 2007-02-07
> **ske1fr said:**
> The UK source is [http://gb.releases.ubuntu.com/6.10/](http://gb.releases.ubuntu.com/6.10/) for Gnome Ubuntu.  The list of actual iso's is down the page. 

Aaah yes, there it is, but he's right, I could have sworn they used to have an option for the alternate CD on the front page of ubuntu.com.  But yeah navigating down you do eventually end up at an option for the alternative CD.

---

### Post by Brendantb on 2007-02-07
Hi, 

Just wanted to check something: if your AMD is 64 bit, have you downloaded the 64 bit version of Ubuntu?

---

### Post by ed-j on 2007-02-07
> **Brendantb said:**
> Hi, 

Just wanted to check something: if your AMD is 64 bit, have you downloaded the 64 bit version of Ubuntu?

No, I was sent a 32bit copy of 6.1 from someone in Scotland, and I installed all my drivers from in Ubuntu without going to either Nvidia or Asus (my motherboard) for any drivers. However, when I check my OS in "Hard Info", which I added through Add/Remove, it tells me that my OS is "Linux 2.6.17-10-generic (i686). My system is working fine and I have yet to look into this.

---

### Post by MikeSz on 2007-02-07
Thats a good point and I seem to have missed the Alternate CDs on the main page.  I have downloaded the PC x86 version (was going for the 64 version but it says to use the x86 version if you are unsure - as I am in a permenant state of unsure-ness I opted for this :)  )

Il have a go with several different versions (might as well burn a few of them and see what happens), fingers crossed I will be able to get at least to a desktop!!

Thanks to everyone who has offered help - your all great and this is a really cool forum!  If anyone has any other suggestions then I will of course welcome them.

---

### Post by ed-j on 2007-02-07
> **MikeSz said:**
> Thats a good point and I seem to have missed the Alternate CDs on the main page.  I have downloaded the PC x86 version (was going for the 64 version but it says to use the x86 version if you are unsure - as I am in a permenant state of unsure-ness I opted for this :)  )

Il have a go with several different versions (might as well burn a few of them and see what happens), fingers crossed I will be able to get at least to a desktop!!

Thanks to everyone who has offered help - your all great and this is a really cool forum!  If anyone has any other suggestions then I will of course welcome them.

Somewhere in the forum, you can request a shiny, new printed copy of any of the Linux OS's and they will send it to you for free!

---

### Post by MikeSz on 2007-03-01
Hi everyone!

Unfortunately, still having the problem.  Ive tried the advanced CD, which worked up to a point until I got to the stage where I was trying to load the desktop and then I got my usual lines down the screen.  Ive tried a different monitor (standard 17" CRT) just in case it was that and it did the same thing.

It just doesnt seem to want to work :confused: :( 

Im wondering if it is a problem with my motherboard or Graphics card. My motherboard is a Gigabyte K8N Nforce 4 board and my Graphics card is a PCI-E Asus GeForce 6600 512Mb.  Does anyone have any suggestions how I might be able to install and run Ubuntu in some sort of standard graphics setting or something where I can at least get to a desktop or have any other ideas?  Or am I doomed??

Although my CPU is an AMD 64 3700+ would the non AMD 64 ISO work?  i.e. could I just use the normal PC disc to try and install or would that mess things up?  So far I have just tried 6.06 & 6.10 and the advanced CD versions but have only used the AMD 64 ones.

Many thanks!!!!!
Mike.

---

### Post by MikeSz on 2007-03-01
Just a quick correction - meant the 'alternative' CD, not 'advacnced' CD as posted above :lolflag:

---

### Post by MikeSz on 2007-03-01
p.s. does the fact that I have nearley 2Gb of Ram in my system have anything to do with it?  Seem to remember reading somewhere that it might

---

### Post by Maestro23 on 2007-03-01
> **MikeSz said:**
> p.s. does the fact that I have nearley 2Gb of Ram in my system have anything to do with it?  Seem to remember reading somewhere that it might

I run 32-bit Edgy 6.10 on my dual-core AMD w/2Gig RAM.  Runs like a champ.  Other people say Dapper is more stable than Edgy, but I have never had any stability issues with Edgy on my machine.

Remember to burn the images at a slow speed (4x) worked for me.

---

### Post by tocleora on 2007-03-01
Do you have another graphics card or a friend with a PCI-E who would let you borrow it to test if it's the graphics card?  That would probably be my next step if it were me...

---

### Post by Industrial PhD on 2007-03-01
I'm having the exact same issue:

P4 3.2GHz
2GB Ram
NVidia 6600 256MB AGP 8X

---

### Post by Ken in Seattle on 2007-03-02
The message sync out of range is a video message. Narrow your search to card issues since you have tried a different monitor. Nvidia drivers did not work on any of my machines with nvidia cards though the default install worked ok with the 440 mx (laptop), the 5200, and the 5600.

I stumbled across this since I have my own video problems with an intel embedded video.

borrow or buy a cheap pci graphics card. I installed ok on a dell laptop with a neomagic 2m video.

---

### Post by MikeSz on 2007-03-02
OH JOY of JOYS!!!!!

Tried the technical support section and someone was having a similar problem.  The advice offered was to try typing FB=FALSE VIDEO=VGA16:OFF on the F6 more options line when booting from the CD.  I tried that and here I am typing this in Ubuntu for the very first time!!!!  Lets just hope I manage to install it now!

---

### Post by igknighted on 2007-03-02
I think the issue might come from using the DVI-adaptor.  I had my monitor (17" lcd) hooked up through one and it gave me that error, but when I went to the normal VGA output without the adaptor, no more error.  You solution works as well I guess, I didn't get that far.

---

### Post by MikeSz on 2007-03-02
Well I dont know what it was but it works now - ive managed to install it and its running a dream - Got plenty of reading up to do now!! (p.s. for any newbies out there like me, "moving to ubuntu linux by marcel gagne" is absolutely top notch.  Got it from the library but I might buy it its that good. 

On the issue of the monitor - you could be right, I didnt think of that, I did try a 17" CRT monitor but had it running through the adapter.

Thanks to everyone for their help - its very much appreciated!

---

### Post by Maestro23 on 2007-03-02
Good deal man.  Go back and mark your first post "Resolved".

Glad you got it working:)

---

