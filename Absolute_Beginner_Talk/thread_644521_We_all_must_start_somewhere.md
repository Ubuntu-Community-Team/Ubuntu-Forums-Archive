---
title: "We all must start somewhere"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by lasthand on 2007-12-19
Well, I am new to all this stuff and I thought I would try Ubuntu.I've been using Windows since Windows 95. I figured I would step out of my Windows box. My computer is a Gateway 507GR. It has a 200Gb harddrive. It has 1 gig of DDR-RAM. It is an Intel Pentium 4 processor with Hyper threading. It is clocked at 3.00Ghz. I haven't over clocked it yet. I have a Nvidia 5500. I am currently running Windows XP SP2. I got a live CD of Ubunto 7.10 Desktop, which i will burn in a minute. What do I need to do to run a live CD? I don't want to lose any data of off my current hard drive. I don't have the money for another hard drive.

---

### Post by spiderbatdad on 2007-12-19
the great thing about the live cd is it doesn't change a thing...just pop it in and see what happens...make sure your bios is set to boot from cd as first option

---

### Post by Old *ix Geek on 2007-12-19
Just pop the live CD into the drive and reboot.  (Assuming, of course, that your computer is set to boot from the CD drive.)  That's it!  You'll have a working Ubuntu box for as long as you're running the CD; it has no effect whatsoever on your hard drive.  Take it out and reboot...you're back to windoze (but why would you want to be?!).

---

### Post by Flying caveman on 2007-12-19
Make sure you know how to burn an .iso properly.  I like BurnCDCC for windows [http://burncdcc.en.softonic.com/](http://burncdcc.en.softonic.com/)   Its virtually fool-proof.

---

### Post by lasthand on 2007-12-19
Quite fascinating. I will try it very soon. It is like an early xmas gift.

---

### Post by aysiu on 2007-12-19
> **lasthand said:**
> My computer is a Gateway 507GR. It has a 200Gb harddrive. It has **1 gig of DDR-RAM.**>  **I don't want to lose any data of off my current hard drive.** I don't have the money for another hard drive. You sound like a perfect candidate for [installing Ubuntu as a virtual OS inside Windows XP](http://www.psychocats.net/ubuntu/virtualbox). Try that instead of burning the live CD.

---

### Post by carverj on 2007-12-19
Yeah just stick it in, have a fun look and decide if you want to go Linux. I have used Linux (debian) for 3 or 4 years and highly recommend it. I suggest you keep Windies on your first partition and place linux and swap partition (at end of disk) on second and third partition. Have the best of both worlds (although I am using Vista, I don't really recommend it over XP)

Ho, ho, ho I can hear in the distance!!

---

### Post by RomeReactor on 2007-12-19
Hi. As has been said, just set your BIOS to boot from the CD. When Ubuntu loads, you'll see an "Install"  button on the desktop; don't press it **unless you want to permanently install Ubuntu**. If you're having trouble burning the .ISO image, [try this]("https://help.ubuntu.com/community/BurningIsoHowto").

Welcome to the community!

---

### Post by nwadams on 2007-12-19
nero shoudl burn it just fine if you have that

---

### Post by lasthand on 2007-12-19
My gf has vista on her laptop and i hate it.... I'm burning the Live Cd with nero 7 burn rom...

---

### Post by lasthand on 2007-12-19
Well, that didn't get me very far.... I boot into the live cd I ran the integrity check  and it said there was one error, so i reboot and I told it to install/start ubuntu. It gave me the line that goes back forth and it had an error ant froze and put parts of the line at top.

---

### Post by shadow-of-sin on 2007-12-19
Did you burn the CD with a low-speed? If you burn at a slow speed you are more likely to get a good CD without errors.Also, did you check the MD5 sum of the image you downloaded to see if it is not corrupted?

---

### Post by lasthand on 2007-12-19
> **shadow-of-sin said:**
> Did you burn the CD with a low-speed? If you burn at a slow speed you are more likely to get a good CD without errors.Also, did you check the MD5 sum of the image you downloaded to see if it is not corrupted?

how do i check the md5 sum? I download ubuntu from the official site. I burn the disk at 32x i'm gonna burn slower this time.

---

### Post by LaRoza on 2007-12-19
> **lasthand said:**
> I burn the disk at 32x i'm gonna burn slower this time.

That is much too fast, try 2x.

[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

### Post by aysiu on 2007-12-19
Please do consider installing Ubuntu as a virtual OS inside Windows. It may save you a lot of trouble down the road.

---

### Post by lasthand on 2007-12-19
> **LaRoza said:**
> That is much too fast, try 2x.

[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

Well, I am trying 8x that is as slow as nero 7 goes.....

---

### Post by aysiu on 2007-12-19
It's also possible that the CD image (.ISO) itself is corrupted, in which case it won't matter what speed your burn it at.

Did you do a checksum on the image before burning it?

More details here:
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

### Post by hyper_ch on 2007-12-19
if the cd image is corrupted, download it again but this time I recommend you to do it with BitTorrent.

---

### Post by lasthand on 2007-12-19
My md5 sum is d2334dbba7313e9abc8c7c072d2af09c. How do i check if it is right?

---

### Post by rsambuca on 2007-12-19
That is the correct hash.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by lasthand on 2007-12-19
ok, It matsches. I am gona try that Virtual box thingy, you guys where talking about. Thanks! :)

---

### Post by aysiu on 2007-12-19
Yes, please do.

With 1 GB of RAM and no data backup, it's your safest bet!

Plus, you don't have to waste a burnt CD.

---

### Post by jken146 on 2007-12-19
> **aysiu said:**
> You sound like a perfect candidate for [installing Ubuntu as a virtual OS inside Windows XP](http://www.psychocats.net/ubuntu/virtualbox). Try that instead of burning the live CD.

To me it sounds like you're jumping the gun a bit.  How is that easier than booting from a live CD?  For a start, a live CD is less risky.  That also assumes that the OP has enough HD space to spare and wants to install Ubuntu in the first place.  In addition there's a performance hit from running a virtual machine.

I think the best advice is to try out the live CD first, see if you like the OS, and then if an install is desired, see about the best way of doing that for your situation.

---

### Post by aysiu on 2007-12-19
> **jken146 said:**
> To me it sounds like you're jumping the gun a bit. Given the circumstances with the OP, I disagree. > How is that easier than booting from a live CD? As you can see, the OP is having quite a bit of difficulty getting the live CD to work. > For a start, a live CD is less risky. How is it less risky? As a matter of fact, with the live CD, you can mount the hard drive and erase everything. The virtual installation can affect only itself. > That also assumes that the OP has enough HD space to spare and wants to install Ubuntu in the first place. The OP has a 200 GB hard drive. And a virtual installation can be easily removed. As a matter of fact, you can use VirtualBox to run the live CD and don't even have to do a virtual installation. > In addition there's a performance hit from running a virtual machine. But the OP has 1 GB of RAM. That's why I suggested a virtual installation: [list][*]The OP has 200 GB of hard drive space. [*]The OP has ample RAM (1 GB). [*]The OP has no backup for data. [*]The OP is having trouble burning the live CD properly.[/list] This screams "ideal candidate for a virtual installation." I am not jumping the gun at all.

---

### Post by Niniel on 2007-12-19
Apart from the little issue of getting a VM installed and then installing into that. IMO, that's not as trivial as running a live CD.

---

### Post by aysiu on 2007-12-19
> **Niniel said:**
> Apart from the little issue of getting a VM installed and then installing into that. IMO, that's not as trivial as running a live CD.
Really? The OP would probably disagree: [quote=person who is having problems running the live CD]Well, that didn't get me very far.... I boot into the live cd I ran the integrity check and it said there was one error, so i reboot and I told it to install/start ubuntu. It gave me the line that goes back forth and it had an error ant froze and put parts of the line at top.[/quote]

---

### Post by Niniel on 2007-12-19
You are - deliberately? - confusing burning a CD and booting from a CD. 
The first step will have to be performed regardless since without a proper, error-free CD no installation to a VM will be possible. At least none that I'm aware of (last time I saw somebody here mention the Ubuntu Windows installer it was to say that it wrecked his Windows installation).

You are also assuming that he has at least one VM software already or knows where to get one, and is knowledgeable in setting it up correctly. 
Not exactly the situation the average newbie is likely to be in.

---

### Post by aysiu on 2007-12-19
> **Niniel said:**
> You are - deliberately? - confusing burning a CD and booting from a CD. 
The first step will have to be performed regardless since without a proper, error-free CD no installation to a VM will be possible. At least none that I'm aware of (last time I saw somebody here mention the Ubuntu Windows installer it was to say that it wrecked his Windows installation). No, I'm not confusing anything. Even if the .ISO download came in intact (with a verified md5sum), the .ISO can be corrupted during the burn process (which is why someone earlier in the thread mentioned burning the CD at possibly 2x instead of 32x). With a virtual installation, you don't need to burn the CD at all.

**Virtual installation risk of corruption**: [list][*]Corruption during download[/list]
**Live CD booting risk of corruption**: [list][*]Corruption during download[*]Corruption during CD burn[/list]

As you can see, there is more risk of corruption with getting an error-free CD.

> You are also assuming that he has at least one VM software already or knows where to get one, and is knowledgeable in setting it up correctly. 
Not exactly the situation the average newbie is likely to be in. No, I'm not assuming anything. I posted a link to a step-by-step tutorial with screenshots.

The only assumptions that have been made in terms of instructions is that the OP knows how to keep an .ISO intact, check its integrity, burn at a slow speed, and set the BIOS to boot from CD. I've made no such assumptions.

---

### Post by tech9 on 2007-12-19
> **lasthand said:**
> Well, I am new to all this stuff and I thought I would try Ubuntu.I've been using Windows since Windows 95. I figured I would step out of my Windows box. My computer is a Gateway 507GR. It has a 200Gb harddrive. It has 1 gig of DDR-RAM. It is an Intel Pentium 4 processor with Hyper threading. It is clocked at 3.00Ghz. I haven't over clocked it yet. I have a Nvidia 5500. I am currently running Windows XP SP2. I got a live CD of Ubunto 7.10 Desktop, which i will burn in a minute. What do I need to do to run a live CD? I don't want to lose any data of off my current hard drive. I don't have the money for another hard drive.


LiveCD is a preinstalled environment running off of Memory and your CD... it will not affect you current system unless you physically make a change inside LiveCD
example: deleting files

---

### Post by Niniel on 2007-12-19
Ok, you do have a point, Aysiu.

Still, with a CD you can test-drive Ubuntu on your actual hardware, and not some abstraction of it. I suppose for just checking out the OS for it's look and feel it doesn't matter; I wouldn't want to run Ubuntu permanently in a VM though.

---

### Post by aysiu on 2007-12-19
> **Niniel said:**
> Ok, you do have a point, Aysiu.

Still, with a CD you can test-drive Ubuntu on your actual hardware, and not some abstraction of it. I suppose for just checking out the OS for it's look and feel it doesn't matter; I wouldn't want to run Ubuntu permanently in a VM though.
The OP is in a particular situation, though.

Running the live CD is fine (except that lasthand is having trouble doing so). And since lasthand does not have a way to back up data on the hard drive, the usual line of "If you like the live CD, then you can install Ubuntu" is not appropriate. The partitioner for Ubuntu is pretty reliable, but I wouldn't resize a partition that is not backed up.

I do not advise everyone to install a virtual OS, but this situation seems to call for it--a lot of hard drive space, a lot of RAM, no way to back up all the data, difficulty running the live CD...

---

### Post by loudnlownoma on 2007-12-19
> **jken146 said:**
> In addition there's a performance hit from running a virtual machine.


I think the rest of the points were accounted for - but is there much of a difference in the performance hit when running virtually as opposed to running from the Live CD?  If the hardware has the means to run the virtual OS without trouble, as the OP's sounds to,  I don't think it would be much different at all, unless being more favorable in the virtual state than from the Live CD.  Granted, the hardware mismatch will be a difference - in that the OP won't be able to tell directly about the hardware working.  But it will give them a good view of Ubuntu in working form, to tell if it is worth it to them to have the hassle of trying to get the live CD to work.  If Ubuntu looks like a viable alternative, the OP can take the necessary precautions for backing up their data, work out whatever trouble is occurring with the LiveCD, then boot to it for further investigation of the hardware and how well it will work from there.

---

### Post by jken146 on 2007-12-19
Aysiu, you have some good points.  What surprised me at first was how quick you were to suggest a VM install (before there was any sign of trouble with the live CD).  Granted, the case for a VM install bulit up as time went on, but really I was curious to know why you suggested it so soon.  The phrase "perfect candidate" struck me as odd too.  As I say, I was just surprised, and I didn't mean to belittle your suggestion.

I still think the live CD is the best way to go, mainly because it lets you test out Ubuntu on your hardware.  Of course, if you can't get the live CD going, a VM is not such a bad idea.

Thanks for your posts guys; that discussion was an interesting read.

---

### Post by aysiu on 2007-12-19
> **jken146 said:**
> Aysiu, you have some good points.  What surprised me at first was how quick you were to suggest a VM install (before there was any sign of trouble with the live CD).  Granted, the case for a VM install bulit up as time went on, but really I was curious to know why you suggested it so soon. Thanks for asking. I'm usually not so quick to offer it up, but this part of the original post (in addition to the RAM and hard drive specs) got me moving in that direction very quickly: [quote=lasthand]I don't want to lose any data of off my current hard drive. I don't have the money for another hard drive.[/quote] If the OP has no easy way to back up all the important data, a virtual installation of Ubuntu is a better choice than running the live CD, because people usually use the live CD as a test run before doing an actual installation. Well, what's the point of doing a test run if you aren't going to install? And, if you are going to install without backing everything up first... well, that's a very bad idea.

So that's how I got quickly to suggesting a virtual installation. The fact that the OP had difficulty with the CD burn/corruption only added to my conviction that it was a good choice.

---

### Post by rsambuca on 2007-12-19
> **aysiu said:**
> ...And, if you are going to install without backing everything up first... well, that's a very bad idea.

Actually, I think it is a very bad idea to not back everything up, period.  Hard drives have an 8% failure rate per year.  Approximately 25% of hard drives fail within the first three years, according to the study conducted by Google on their systems.

---

### Post by jken146 on 2007-12-19
> **aysiu said:**
> Well, what's the point of doing a test run if you aren't going to install?

Surely it's to see if you can install?  And want to.


Going totally off topic now, but is IceBuntu just a theme (all I could find on it was an IceWM theme that looked like the Dapper Human theme for Gnome)?  Or are you just saying that you use IceWM?

---

### Post by jken146 on 2007-12-19
> **rsambuca said:**
> Actually, I think it is a very bad idea to not back everything up, period.  Hard drives have an 8% failure rate per year.  Approximately 25% of hard drives fail within the first three years, according to the study conducted by Google on their systems.

Wow, that's much higher than I would have thought.  I guess I have been vey lucky with my maxtors.  I still have a 12GB one from 9 years ago -- very noisy but otherwise OK.

---

### Post by loudnlownoma on 2007-12-19
> **jken146 said:**
> Surely it's to see if you can install?  And want to.

Which could be another plus for the VM install, since you can get a lot better feel for using the OS itself and doing some more advanced stuff than you can do in a single session on the live CD, to give it a good run-through.  Granted, the hardware matchup would still require the live CD when you are ready, but if setting up a VM is just as easy, why go through the hassle of making the live CD work properly just yet.  Would be a waste of time if the OP finds out that it's not quite what they want, or doesn't meet their standards they expect from another distro or the like.  For me, I tend to always do an install in VMWare or Virtualbox before doing anything.  As nice as the live CD is(and I do use them frequently as well, don't get me wrong), I have always had much better performance running it virtually than from the live CD.

---

### Post by jken146 on 2007-12-19
Yes, I agree -- the performance on live CDs is generally not that good, although I find it is comparable to many an installation on Windows.  Hey ho, each to their own.

---

### Post by aysiu on 2007-12-19
> **jken146 said:**
> Surely it's to see if you can install?  And want to. Yeah, but that only makes sense if you *might* install it. Given that the OP has no way to back up files, installation is a very bad idea. It's like having no money and attending an open house to see if you can buy a house. You can't buy a house. You have no money.

> Going totally off topic now, but is IceBuntu just a theme (all I could find on it was an IceWM theme that looked like the Dapper Human theme for Gnome)?  Or are you just saying that you use IceWM? IceBuntu is just my shorthand way of saying I'm using IceWM with Ubuntu.

---

### Post by jken146 on 2007-12-19
Ok

---

### Post by Presto123 on 2007-12-19
With that graphics card...might I suggest running it in "Safe Graphics Mode"? (If you haven't tried this already) I got that freezing on my desktop with a Nvidia GeForce card, did the "Safe Graphics" and viola, no problemo. It installs correctly, though.

---

### Post by discoade on 2007-12-19
Sorry to stir the pudding here! but if you install via virtualbox doesn't that use the host systems drivers? surly if this is the case its not a very good hardware compatibility test? Kick me in the *** if im wrong!

---

### Post by jken146 on 2007-12-19
No, you are right, discoade.

---

### Post by loudnlownoma on 2007-12-19
> **discoade said:**
> Sorry to stir the pudding here! but if you install via virtualbox doesn't that use the host systems drivers? surly if this is the case its not a very good hardware compatibility test? Kick me in the *** if im wrong!

Yes, but it would be a good way to get your feet wet with the OS.  And in most cases, I have had very good luck with installing Ubuntu or Kubuntu this way and having just about everything working.  This way you can get a good feel of the OS, without having to fix four or five hardware incompatibilities right off the bat.  Then if you are enjoying it, and wish to install it, you can jump to the Live CD and make sure the necessary stuff works for you on your own hardware.  If you already know that you want to install it but want to check hardware, then the LiveCD would be the way to go.

---

### Post by aysiu on 2007-12-19
> **discoade said:**
> Sorry to stir the pudding here! but if you install via virtualbox doesn't that use the host systems drivers? surly if this is the case its not a very good hardware compatibility test? Kick me in the *** if im wrong!
How many times do I have to say it? Hardware compatibility doesn't matter, because hopefully *lasthand*, who does not have a way to back up data, will **not** be installing Ubuntu in the regular way.

---

### Post by discoade on 2007-12-20
i know when i first ran ubuntu one of the first things i wanted to know was is my hardware compatible! As lasthand states he hasn't the money to replace hardware so i personally would like to know if i was going to need to change anything to get my system running! As it is i cant get all the features of my cannon printer scanner working as there's no drivers available for it! ok ive got a basic printer and a less than impressive scanner going by using drivers for a different model but functionality is very restricted and will need to change my printer eventually to get full functionality!
Don't get me wrong im not dissing virtualbox i use it myself to run xp in linux and its very good but its not a good way of testing the machine although it may be a good way of getting a feel of the os.

> How many times do I have to say it? Hardware compatibility doesn't matterhmm interesting yes i agree that ubuntu does support a lot of hardware but i think i would like to know how much of mine it supports!

> hopefully *lasthand*, who does not have a way to back up data, will **not** be installing Ubuntu in the regular way.So what's the point? you cant get everything out of ubuntu unless you install it! ok vm or live cd give you a feel for it but its not until you install it to your hdd that it really comes alive! what does it cost to back everything up? half a dozen dvdr's or cdr's? jees you can get a dvd rw drive for a tenner! but im guessing as he's burnt a live cd he already got one!

He's been running windows since w95, as long as he can get his head around the "windows" mentality i guarantee he'll love ubuntu and want to install it!

---

### Post by lasthand on 2007-12-20
Thanks for the help guys. I got it running in the Virtual Box. Any must install programs out there for Ubuntu? I would love to do a full convert to linux, but this I have to share my computer with my family. I got a lot of good games and I don't know if they would run. Personally I want to switch over to a duel boot  setup.

---

### Post by discoade on 2007-12-20
if your games wont run in linux dual boot is the way to go! theres plenty of tutorials available on doing this..

[http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

theres a couple to be going on with

---

### Post by jimmj43 on 2007-12-20
I'm seeing a lot of "Go!" "Go!" "Go!" here, with little if no "think".

He's been  Windows user since '95. Chances are he's visited YouTube. 

YouTube recently upgraded to a newer version of flash format. Alas! That new version doesn't PLAY WELL with the resident installer. Jump through hoops to make it work.

I'm reminded, for instance, of model airplane enthusiasts. Crash-and-burns happen. Rebuilding, repairing, re-engineering is part of the passtime.

Some folks just want the plane to fly. Reliably. Every time. They find no "fun" in crash-and-burns.

It's nice to be able to install or uninstall lights/bells/whistles according to personal preferences at will.

It's an entirely different thing to ASSUME that the user is prepared to drudge through learning a foreign language in order to apply a favored magnet to his fridge door.

Click this or click that to make a selection? Fine. Write a few lines of code from another planet? Not so much.

I don't intend to take anything away fom the "crash-and-burn' model airplane enthusiasts. More power to 'em. Goferit!!

But it should be born in mind that there's chocolate and there's vanilla: What's "fun" for one guy might be misery for another.

An invitation to "Jump in!" should be issued only after due consideration.

Now then? Any chance I can get released early for good behavior for preaching with neither a license nor a permit?

---

### Post by discoade on 2007-12-20
Ahh but these days you can install an autopilot on your model plane so if you release the sticks it will fly its self!

And no i don't see any chance of an early release!

ps whats the problem with u tube! im having no problems!?

---

### Post by aysiu on 2007-12-20
> **lasthand said:**
> Thanks for the help guys. I got it running in the Virtual Box. Any must install programs out there for Ubuntu? I would love to do a full convert to linux, but this I have to share my computer with my family. I got a lot of good games and I don't know if they would run. Personally I want to switch over to a duel boot  setup.
I don't see what you would gain from a dual-boot, to be honest.

Right now, you have Ubuntu installed in a virtual machine and Windows still at your fingertips (all you have to do is press the right Control) button.

If you set up a dual boot, you risk (a small risk, granted) losing all your data (the data you can't back up right now), and every time you want to switch between Windows and Ubuntu, you have to reboot your entire computer.

You say you have to share it with your family? Picture these scenarios.

**VirtualBox** (what you currently have set up).
You're using Ubuntu, in the middle of organizing some photos in F-Spot.
A family member comes up and says, "Hey, can I use the computer?" (Let's assume this family member has to use Windows for something)
You say, "Sure. One second."
You press the right Control key and minimize the VirtualBox Ubuntu window and step away from the computer.

**A Dual Boot** (what you say you want).
You're using Ubuntu, in the middle of organizing some photos in F-Spot.
A family member comes up and says, "Hey, can I use the computer?" (Let's assume this family member has to use Windows for something)
You say, "Sure. Come back in three minutes."
You close F-Spot. Go to the log out menu and select Quit.
Then you select Restart and wait for the computer to restart.

Why is a dual-boot desirable for you?

---

### Post by rsambuca on 2007-12-20
> **aysiu said:**
> I don't see what you would gain from a dual-boot, to be honest....
How about performance?

---

### Post by lasthand on 2007-12-20
> **rsambuca said:**
> How about performance?

What performance do I need in Ubuntu? The only thing you really need performance in is gaming.

---

### Post by rsambuca on 2007-12-20
> **lasthand said:**
> What performance do I need in Ubuntu? The only thing you really need performance in is gaming.

No, apparently the only thing ***you*** need performance for is gaming!  Depending on your system specs, running two systems can just be too slow.  Also, not all peripherals work properly in a virtual environment, and not all programs do either, for that matter.

---

### Post by aysiu on 2007-12-20
> **rsambuca said:**
> No, apparently the only thing ***you*** need performance for is gaming!  Depending on your system specs, running two systems can just be too slow.  Also, not all peripherals work properly in a virtual environment, and not all programs do either, for that matter.
Please take a look at the bolded word in your post.

This is a *support* thread, so the only person whose needs and habits are relevant are lasthand's--not yours or mine.

If lasthand needs performance only for gaming, then a virtual Ubuntu may be a fine solution (leaving Windows for gaming). There may be some obscure program that doesn't work in a virtual environment (Can you give examples? I can't think of any), but I think almost all of them should. If lasthand runs into a program that doesn't work in VirtualBox, there is always the option to create another support thread.

---

### Post by rsambuca on 2007-12-20
I agree that as the OP, lasthand's needs and habits are the ones that are relevant.  I was just correcting a blanket statement that "the only thing that you really need performance in is gaming", which isn't a true statement.  It should have been 'the only thing I really need performance for is gaming'.

EDIT:  Skype for Windows doesn't work properly in the Virtual world, by the way.

---

### Post by roaldz on 2007-12-20
> **aysiu said:**
> Please take a look at the bolded word in your post.

This is a *support* thread, so the only person whose needs and habits are relevant are lasthand's--not yours or mine.

If lasthand needs performance only for gaming, then a virtual Ubuntu may be a fine solution (leaving Windows for gaming). There may be some obscure program that doesn't work in a virtual environment (Can you give examples? I can't think of any), but I think almost all of them should. If lasthand runs into a program that doesn't work in VirtualBox, there is always the option to create another support thread.

Maybe he wants to see the beauty and usefulness of Compiz Fusion? As far as I know thats an obscure program that won´t run in VirtualBox.. Does it?

Roald

---

### Post by aysiu on 2007-12-20
> **roaldz said:**
> Maybe he wants to see the beauty and usefulness of Compiz Fusion? As far as I know thats an obscure program that won´t run in VirtualBox.. Does it?

Roald
Yes, if lasthand wants the beauty of CompizFusion, that'd have to be a full install. The added usefulness is debatable, though.

---

### Post by roaldz on 2007-12-20
> **aysiu said:**
> Yes, if lasthand wants the beauty of CompizFusion, that'd have to be a full install. The added usefulness is debatable, though.

Well, in that debate, I would state that it actually IS a very useful interface to be more productive on a desktop. You only have to get used to it. 

Just lost my 2 cents..

---

### Post by discoade on 2007-12-20
ok aysiu just to break the thread for one moment if i may!? you seem to know a bit about vb im running xp on vb can i install my nvidia graphics drivers from the nvidia cd into vbox as if i was installing xp directly to my hdd? vb is only giving me 8 meg graphics

---

### Post by lasthand on 2007-12-26
If I may ask....What is CompizFusion?

---

### Post by overdrank on 2007-12-26
> **lasthand said:**
> If I may ask....What is CompizFusion?

HI and this link may help
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

