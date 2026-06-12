---
title: "Is linux bad at managing CPU?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-06-01
Alright, I've been running Xubuntu 7.04 for like 2 days now, and it's really running like crap. I used a fresh install CD (it was running fine after I installed it), and I've done the following things since I've installed it:

Configured my Intel video card using the xserver-xorg-video-intel (or something like that)
Installed Pidgin
Installed Swiftweasel and removed firefox
Installed VLC Player
Installed KTorrent
Installed Cedega and tried emulating Ragnarok Online, but I gave up on that for now.
Installed Java Runtime Environment 6

I might have done a few other things - I can't remember, but that's the most important that I've done. Now, here are my system specs:

Intel P4 2.0ghz processor
256mb RAM
onboard video and audio
1152x864 resolution with 75hz refresh rate.

Anytime I execute a command or open up a program, my CPU meter JUMPS to 100% instantly. Whenever I'm not doing anything, it remains at around 0%,

Why is it doing this? Running multiple programs is a pain in the ***. I even tried loading a java application through swiftweasel and my computer nearly died.

Can somebody help me?

---

### Post by bone43 on 2007-06-01
> **Exershio said:**
> Alright, I've been running Xubuntu 7.04 for like 2 days now, and it's really running like crap. I used a fresh install CD (it was running fine after I installed it), and I've done the following things since I've installed it:



I might have done a few other things - I can't remember, but that's the most important that I've done. Now, here are my system specs:

Intel P4 2.0ghz processor
256mb RAM
onboard video and audio
1152x864 resolution with 75hz refresh rate.

Anytime I execute a command or open up a program, my CPU meter JUMPS to 100% instantly. Whenever I'm not doing anything, it remains at around 0%,

Why is it doing this? Running multiple programs is a pain in the ***. I even tried loading a java application through swiftweasel and my computer nearly died.

Can somebody help me?

Go to System>preference>control center>system monitor and under the proccess tab check out your memory usage my guess is with only 256MB
you could use more.

Opps sorry should be System>preference>control center>system monitor and the Resources tab!
Also as a note mine with just firefox open is using 288.5MB of Ram

---

### Post by louieb on 2007-06-01
With 256MB ram for speed Ubuntu is easy to beat. xUbuntu will be faster. or boom pop type of speed get a hold of  Puppy Linux.

---

### Post by southernman on 2007-06-01
Just to address the question in your thread title... NO.

Linux is much better at managing your processor. The problem isn't with Xubuntu, the problem lies (99% of the time) with hardware resources... or lack thereof.

You also loose a little pep (eating ram resources though mild they be... be none-the-less) by having onboard schtuff... I believe that's correct.

---

### Post by rillip on 2007-06-01
> **louieb said:**
> With 256MB ram for speed Ubuntu is easy to beat. xUbuntu will be faster. or boom pop type of speed get a hold of  Puppy Linux.

He's using Xubuntu.

But really, 256 mb of ram on a 2 gig processor system?  You're not going to run any modern OS well.  Win 2k might be managable, but XP will crawl.  Ubuntu is no different.  You need an OS optimized for low ram usage like louieb suggested, such as Puppy, Damn Small Linux, etc.  Or upgrade.

---

### Post by Hendrixski on 2007-06-01
> **southernman said:**
> Just to address the question in your thread title... NO.

Linux is much better at managing your processor. The problem isn't with Xubuntu, the problem lies (99% of the time) with hardware resources... or lack thereof.

You also loose a little pep (eating ram resources though mild they be... be none-the-less) by having onboard schtuff... I believe that's correct.

I'm not sure if it is actually better than how windows manages the CPU.  I think that's on par... the power management of the CPU is terrible in Ubuntu... though, they're going to fix this with Gutsy.  Thanks in  a large part to the technologies discovered while working on OLPC, such as a tickless kernel, etc. etc.

---

### Post by Lucifiel on 2007-06-01
Huh... 256 mb ram with 2.0 ghz processor?! That's a very strange setup.

Edit: Uh oh... "onboard video and audio". Want to guess it's likely sharing memory with his already meagre ram??!

Wow... no wonder why everything's hanging. 

To the threadstarter: go bring your pc to a shop and ask them to put in 1 gb more of ram. Trust me, ram is cheap these days. Or if your pc is branded, ask them how much it'll take to put in 1gb more of ram.

Trust me, otherwise your pc will be almost useless with such a decent processor.

---

### Post by drowner on 2007-06-01
> **Lucifiel said:**
> Huh... 256 mb ram with 2.0 ghz processor?! That's a very strange setup.

Edit: Uh oh... "onboard video and audio". Want to guess it's likely sharing memory with his already meagre ram??!

Wow... no wonder why everything's hanging. 

To the threadstarter: go bring your pc to a shop and ask them to put in 1 gb more of ram. Trust me, ram is cheap these days. Or if your pc is branded, ask them how much it'll take to put in 1gb more of ram.

Trust me, otherwise your pc will be almost useless with such a decent processor.

Mine is 256 ram with a 2.4ghz processor.

Its not that strange, really.

I run normal ubuntu, i have no trouble with speed unless i try and run system hogs like SOngbird,. Otherwise no problems.

---

### Post by southernman on 2007-06-01
> **Hendrixski said:**
> I'm not sure if it is actually better than how windows manages the CPU.  I think that's on par... the power management of the CPU is terrible in Ubuntu... though, they're going to fix this with Gutsy.  Thanks in  a large part to the technologies discovered while working on OLPC, such as a tickless kernel, etc. etc.Thanks for that info Hendrixski. :)

I am not a CS major, I was just speaking of my experience with XP, 2000, and 98SE (which I don't do any longer) and Ubuntu.

Ubuntu on the same system is noticeably faster.
Asus A7N8X VM/400
Athlon XP 2800
1GB DDR 3200

Besides, the question I answered so boldly was: Is "Linux" bad at managing CPU?

---

### Post by Lucifiel on 2007-06-01
> **drowner said:**
> Mine is 256 ram with a 2.4ghz processor.

Its not that strange, really.

I run normal ubuntu, i have no trouble with speed unless i try and run system hogs like SOngbird,. Otherwise no problems.

Yes but he's likely having the onboard video eating like 32 mb to 64 mb of his ram or even more! Not to mention his onboard sound. Most of such onboard parts rely on shared ram and this does not look good. 

This means that he won't even be able to use WinXP lol. I don't even know if Puppy or any other Linux O/s will be able to load on less than 150 mb of ram. 

Basically, what's going on is that because his sytem keeps running out of memory, his cpu is choking constantly as his system is stressing out his memory and cpu. Now, this is not good because from experience, it will slowly wear down the cpu and even possibly the hard disk as well.

---

### Post by Exershio on 2007-06-01
Honestly guys, I've been able to run Windows XP VERY well with my current system. I've multitasked with Winamp, Visual Studio .NET, Mozilla Firefox, and Pidgin on XP and it ran just fine (mostly really responsive). Xubuntu doesn't seem to be as generous however.

---

### Post by Lucifiel on 2007-06-01
Okay, what's the model of your computer? I assume it's a brand name computer, right?

Post it and we'll be able to look further into this issue.

---

### Post by Exershio on 2007-06-01
It's a Compaq Evo computer. I'm not sure what model exactly, but I know it's an old computer (prob from around 2001 I believe)

---

### Post by Lucifiel on 2007-06-01
Come on! There's got to be a sticker on your computer casing or somewhere else on your monitor. 

Hmmm... how about this? Can you try installing aida32 in WinXP? Then, post the output information from Aida32. 

[http://www.majorgeeks.com/download181.html](http://www.majorgeeks.com/download181.html)

---

### Post by Exershio on 2007-06-01
I'm reinstalling a copy of Windows XP on a seperate partition in roughly 20 minutes. I'll install that and give you the information once I have it set up if you wish to wait.

Other than that, I don't have a sticker on the casing. There probably used to be, but it's torn off by now.

---

### Post by Lucifiel on 2007-06-01
Errr... WinXP has to be installed BEFORE ubuntu in order for WinXP to be able to boot properly. 

Yeah, sure... but I wonder if WinXP will run. :p

---

### Post by Exershio on 2007-06-01
who knows lol. If it all ends bad, I'll just reinstall Xubuntu afterward. However, I'm getting a little skeptical with linux. I'm really open minded to new things and all, but Windows XP was performing much better for me than linux is. I'll give linux a little while longer, and if it doesn't satisfy my needs, I'll revert back to XP permanently.

---

### Post by drowner on 2007-06-01
> **Exershio said:**
> who knows lol. If it all ends bad, I'll just reinstall Xubuntu afterward. However, I'm getting a little skeptical with linux. I'm really open minded to new things and all, but Windows XP was performing much better for me than linux is. I'll give linux a little while longer, and if it doesn't satisfy my needs, I'll revert back to XP permanently.

Weird, you know.

EVERYONE i have spoken to with a dualboot setup says linux is typically much faster than windows, especially if you have multiple windows open, and such.

Weird.

---

### Post by Lucifiel on 2007-06-01
> **Exershio said:**
> who knows lol. If it all ends bad, I'll just reinstall Xubuntu afterward. However, I'm getting a little skeptical with linux. I'm really open minded to new things and all, but Windows XP was performing much better for me than linux is. I'll give linux a little while longer, and if it doesn't satisfy my needs, I'll revert back to XP permanently.

In Linux, try installing htop .

In Terminal (Applications ----> Accessories ----> Terminal), type:  

> sudo apt-get install htop

Then, run htop from Terminal or Applications ----> System Tools. 

Then we can see what's consuming your resources. Because it could have been a bad installation: it happens even with Windows XP, things start crashing right and left even though the install seemed to have gone perfectly right. 

Furthermore, I don't want to be mean but it could also be the user too. Most new users tend to bork up their installations of Windows and Linux because they haven't yet adjusted to learning how to properly use it. That is: they accidentally install stuff that borks up their system, accidentally modify their system files without knowing and also, accidentally run commands on their computer that mess with their system resources. 

My point? Give Linux some time. It's difficult because you've to learn everythng all over again.  :) And if I were you, why don't you ordering the LiveCd from  [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) so you can reinstall Ubuntu?  

Or if not, try burning the cd again but at a slower speed. And check for md5 checksum. 

Because it could have been a bad install, or even a corrupted cd. Yes, I've tried slipstreaming WinXP before but accidentally ended up with a corrupted cd. Oh, the installation went well but a few days later, everything was crashing and I couldn't even shut down the pc properly.

---

### Post by Feba on 2007-06-01
I agree that it's probably your video sharing Memory with your CPU. Have you tried getting a graphics card? You can get a cheap GeForce (Don't buy ATI) for rather cheap, and that will at least offload your graphics from the RAM, which could be a bigger help than you think. Heck, I was able to get a 128MB 6200LE for 30$ by scavenging in my local shop's clearance/open box bin. It's been working great.

You should have 1MB of RAM for every MHz of processing power though, at least in single core systems, to take best advantage of it. Your 2GHz CPU will work best with 2GB of RAM, and nowadays, RAM is very cheap, you should give it a shot. The only reasons I don't upgrade my 2.4GHz from 512MB RAM to 2GB is because my new computer should be replacing this one...when ASUS ships me a working motherboard.. and i'm not sure how much this old (off brand name) computer's motherboard can hold.

EDIT: And please don't give up on Linux on Xubuntu's part. Like people have suggested, try something like DSL or Puppy. Like people have said before, puppy is advertised as being lightweight, but it's still very capable of being used as a desktop OS everyday.  You can't read these forums for more than a few days without hearing people talking about how horrible one or two or more distros were, but then they tried one and it Just Work'd, and they kept with that. In a lot of cases, it's Ubuntu, in others though it's something else entirely.

EDIT2: see [http://ubuntuforums.org/showthread.php?t=461332](http://ubuntuforums.org/showthread.php?t=461332)

---

### Post by Nekiruhs on 2007-06-01
I have a compaq from around 2000 and its runs Xubuntu just fine.

---

### Post by blackspyder on 2007-06-01
Im running a Dell 650-700MHz PIII with 25MB RAM with Xubuntu. It runs fine for me (A little slow but arent all PIII's)

 I noticed you were using KTorrent (which is designed for KDE i think) so your having to keep the KDE and Gnome Apps running all the time (alot of the stuff for Xubuntu is based on GTK)switching to BitTorrent or BitTornado would probably speed things up.

---

### Post by jaybuntu on 2007-06-02
I'm running Ubuntu 7.04 on a 1.8 Ghz processor and 512 MB of RAM and I'm constantly amazed at how much faster it is than Windows.  I agree - bump up the RAM as a first step.  If that doesn't help I suspect that there is some other issue with your specific configuration, not a general issue with Ubuntu or Linux design.

---

### Post by louieb on 2007-06-02
> **Exershio said:**
> .... with Winamp, **Visual Studio .NET**, Mozilla Firefox, and Pidgin on XP ....

Really! I used VS.net(v-2005) for Visual Basic and asp.net programming  on a PC w 384 MB ram for a while. Talk about a ram hungry dog. I wouldn't even think about running something else at the same time.  lol.  but a new PC w/a gig ram solved that.

---

### Post by stalkingwolf on 2007-06-02
To the original poster:  look at the  bottom righthand corner of your display.  You should see the model number
there mine is a N410c.   My Evo specs are +-1.5gb processor with 512 mb ram.  It is dual boot xp/fiesty
and runs fine, at present it is hooked through the docking station to a 15" monitor and ps2 keyboard and mouse.

I have another laptop a Toshiba Tecra that only has 256 ram and it runs the same dual boot config fine in both OS's.  I agree with others, you have some kind of "resourse Vampire" running that is sucking the life out of
your system.

I had less trouble with fiesty on the laptops than Ive had on my desktops.  Using the Check CD option on the
live CD every downloaded CD I have of fiesty shows at least 1 corrupted file.   I have just ordered the CD from Ububtu. ( hope it gets here soon my new box will be here next week).

---

### Post by dptxp on 2007-06-02
2 firefox windows open, one totem media player open, rhythmbox running, 128 MB RAM and 108 MB SWAP being used.
CPU 10 % .

The desktop has 192 MB RAM + 64 MB shared Video. 2 GB SWAP. AMD Sempron 2500+ 64 bit but running 32 bit.

No problems.
Installation was not easy with low RAM. With SWAP, all went fine.

I do not run BERYL/COMPIZ.

Windows XP too runs fine.

---

### Post by Feba on 2007-06-02
> 2 GB SWAP.This could be it, OP, do you have a swap partition? And are you running desktop effects (compiz)?

---

### Post by eljalill on 2007-06-02
And as an additional thought, because you probably set up a swap while installing: somtimes stand by or hibernate erase the swap signature form that partition. So if you are using stand by or hiberante frequently youmay have to reformat the swap partition.
you can check your swap/Ram usage with the free command (just type "free" into a terminal and read the output.)

---

### Post by khardbored on 2007-06-02
> **Exershio said:**
> Honestly guys, I've been able to run Windows XP VERY well with my current system. I've multitasked with Winamp, Visual Studio .NET, Mozilla Firefox, and Pidgin on XP and it ran just fine (mostly really responsive). Xubuntu doesn't seem to be as generous however.

I hope I'm not the only one who is finding this hard to believe? Especially those of us who have used VS .net.
It sounds to me like part of you really doesn't want to migrate to Linux. But if I'm wrong then the issue is your ram, pure and simple.

---

### Post by argie on 2007-06-02
Hmm, this is very possible, actually. Ubuntu installed from the very same CD on similar configurations acts differently. It's probably something strange eating up the CPU. 

To the OP: Does moving around windows also cause 100% CPU usage? 

I'm sure it's got something to do with the hardware or drivers for the hardware because I use a 2.93Ghz processor with 256MB RAM and 32MB shared for on-board graphics and I have on-board audio and it's still fast.

---

### Post by the_it on 2007-06-02
ubuntu doesn't give you any warnings when you're running out of ram/swap, it'll just magically seem slower and be very unresponsive.  I think it's a swap issue.

TRANSLATION:
Windows has this thing called a pagefile.  When your system cannot fit its stuff onto its ram, it goes into its pagefile.  This is a hidden system file that can grow to a couple of gigs in size.  When your pagefile cannot grow anymore, and your system magically needs more ram, your windows will just start coughing.
Linux has something similar called a swap file.  It is usually kept on a dedicated partition called a swap partition.  If you set up linux by yourself, you probably should have at least heard of it.  If not you may not have any swap partition OR you may have done something to bork your swap partition.

Here are some things you could have done to bork your swap partition.
1) You really didn't install a swap partition.
It happens sometimes.  To tell if you have a swap partition, open a terminal and copy paste the following command:
```
cat /etc/fstab|grep swap
```

If you see a line saying something like /dev/sda3 none swap sw 0 0, you should be fine.  If you don't see any output at all, you didn't install a swap partition.  You'll need to make a swap file.

2) You installed a swap partition, you tried the hibernate, but you didn't resume your hibernate.
What happens here is that your hibernated session gets saved into the swap partition and Linux doesnt use the swap because the format of a hibernated session is different from a swap partition.
Try reformatting your swap partition.

3) You installed some windows driver on your windows partition that can read your swap partition, and windows borked your swap.  It's happened to me.
Try reformatting your swap partition.


To reformat your swap partition, you first find the device file of your swap partition.  
```
markd@trixie:~$ cat /etc/fstab|grep swap
**/dev/sda3** none swap sw 0 0
```
The device file is the first word that appears in the list.  In my case, my swap partition is /dev/sda3.

run the mkswap command on the swap partition
```
sudo mkswap DEVICE-FILE-OF-SWAP-PARTITION
```
Please make sure that you were able to correctly identify the device file using the previous instruction.  If you type the wrong device file, you will bork some other partition.

activate the partition using swapon.
```
sudo swapon DEVICE-FILE-OF-SWAP-PARTITION
```

---

### Post by swoll1980 on 2007-06-02
I'm having simular problem with media player when ever i try streaming video. CPU jumps to 100%, but I still have 100mgs of ram left. Video gets choppy, computer slows down, so I have to close it. any ideas?

---

### Post by swoll1980 on 2007-06-02
I Ran cmd. "cat /etc/fstab|grep swap" and got "UUID=6c54f551-e171-415e-a066-1f33cefad0f0 none            swap    sw              0       0" what does this mean?

---

### Post by dptxp on 2007-06-03
> **argie said:**
> Hmm, this is very possible, actually. Ubuntu installed from the very same CD on similar configurations acts differently. It's probably something strange eating up the CPU. 

To the OP: Does moving around windows also cause 100% CPU usage? 

I'm sure it's got something to do with the hardware or drivers for the hardware because I use a 2.93Ghz processor with 256MB RAM and 32MB shared for on-board graphics and I have on-board audio and it's still fast.

32 MB RAM for Graphics gave me problems. Screen used to freeze.
Increased to 64 MB in bios. All went fine.

Check how your SWAP is getting used in System Monitor.

---

### Post by the_it on 2007-06-03
> **swoll1980 said:**
> I Ran cmd. "cat /etc/fstab|grep swap" and got "UUID=6c54f551-e171-415e-a066-1f33cefad0f0 none            swap    sw              0       0" what does this mean?

Oh I forget.  Modern ubuntus use UUID's instead of device file names in their fstab (just in case adding a hard disk moves around your device filenames).

For you, it should be okay.  It means that you have a swap partition, and its unique identifier is UUID=blablabla.  You'll need different commands to look for the device filename.  I can't remember what it is off the bat, but you can look up your partition device ids in system->preferences->hardware info.  You should see something like SCSI host adapter or IDE and under which you'll see an entry for your hard disk, and its partitions.  Under the advanced tab, somewhere near the bottom, there's an entry called volume.uuid.  This is the partition's unique id that should correspond to the UUID entry. You can compare thie UUID's of each partition with your the UUID of the swap partition you saw there, and the one that matches has the same device file as the UUID entry there.  The device file should be listed near the top, under an entry called block.entry, and it will look something like /dev/sda3 or /dev/hda3 or something like that.  (WHEW a cmmand line entry is  one liner)

Anyways, in case you do some playing around with your swap partition, it is THAT device file that you will be touching.

---

