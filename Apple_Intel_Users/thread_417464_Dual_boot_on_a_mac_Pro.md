---
title: "Dual boot on a mac Pro"
date: 2007-04-21
forum: Apple Intel Users
---

### Post by regine's on 2007-04-21
Hi all
 I do want to intall 7.04 on a dual Xenix Mac Pro, on a second disk of course
what I do have to do to get it work..Up to now I did hada dedicated Opteron system, 
but it has to go. As the Mac pro is so silent 
would be nice to have both systems and as max OS X is not 64 bit ready 
Ubuntu could be a much more open choice.

Maybe vented a million time,s reading and reading found nothing.
Windows will be via VMware on the Ubuntu sytem.

The Graphics card will be a 8800
my monitor is a Sony 24 classic tube :guitar:

---

### Post by ronocdh on 2007-04-21
> **regine's said:**
> Hi all
 I do want to intall 7.04 on a dual Xenix Mac Pro, on a second disk of course
what I do have to do to get it work..Up to now I did hada dedicated Opteron system, 
but it has to go. As the Mac pro is so silent 
would be nice to have both systems and as max OS X is not 64 bit ready 
Ubuntu could be a much more open choice.

Maybe vented a million time,s reading and reading found nothing.
Windows will be via VMware on the Ubuntu sytem.

The Graphics card will be a 8800
my monitor is a Sony 24 classic tube :guitar:
What do you mean when you say that OS X is "not 64-bit ready"? So you know, I've heard very good things about Ubuntu being run in [VMWare fusion]("http://www.vmware.com/products/beta/fusion/"), but if you want to run it natively on its own drive, I understand.

I recommend that you just download the Feisty (7.04) 64-bit CD and have a crack at it. Some will caution against 64-bit, saying it requires more setup, but with the help of Kilz's scripts, you'll be up and running in no time flat. And you won't get the most out of your hardware with the i386 build.

And in case you're really starting from the beginning, make sure to grab [rEFIt]("http://refit.sf.net"). That allows you to dual boot your system, and is necessary because Ubuntu doesn't really understand the EFI makeup yet (think of EFI as the successor to BIOS).

Install rEFIt in OS X, it's a convenient little package, and it's got a beautiful interface. You can use the Boot Camp visual partition tool to set up your drive, or just partition it using the terminal in OS X. I recommend the latter because it's quick and painless, but if you're uncomfortable with command line work, the GUI version might be easier for you.

OK, I'll shut up now. Good luck, and post back with results!

---

### Post by DucentiVigintiDuo on 2007-05-31
> **ronocdh said:**
> And in case you're really starting from the beginning, make sure to grab [rEFIt]("http://refit.sf.net"). That allows you to dual boot your system, and is necessary because Ubuntu doesn't really understand the EFI makeup yet (think of EFI as the successor to BIOS).

Hey, **ronocdh**, Are you saying that there's no way one can dual boot OS X from Ubuntu?
I deleted OS X having Ubuntu as my single OS right now, but trouble with recording software will probably make me install OS X again (Garageband's intuitiveness and features are unmatched by any Linux software I've attempted to use- nothing seems to work!).

I was wondering if I could do it painlessly without having to do yet another format (Ubuntu Studio really disappointed me so now I'm back to normal Feisty), using GRUB to boot into either OS X or Ubuntu.

Is that possible in any way?

Or more importantly, to avoid creating two new topics, do you know of any recording software on Ubuntu that actually works with a first-gen Macbook? :(

---

### Post by ronocdh on 2007-05-31
> **DucentiVigintiDuo said:**
> Hey, **ronocdh**, Are you saying that there's no way one can dual boot OS X from Ubuntu?
I deleted OS X having Ubuntu as my single OS right now, but trouble with recording software will probably make me install OS X again
No, you can definitely dual boot! I was recommending that if you do, use rEFIt to do it. It's pretty than Apple's Boot Camp bootloader.> I was wondering if I could do it painlessly without having to do yet another format (Ubuntu Studio really disappointed me so now I'm back to normal Feisty), using GRUB to boot into either OS X or Ubuntu.
I'm not optimistic about this. I think you should back up your data, wipe your drive completely, and install OS X. Once that's done you can create another partition for Ubuntu, then install Ubuntu.> Or more importantly, to avoid creating two new topics, do you know of any recording software on Ubuntu that actually works with a first-gen Macbook? :(
Hm, what have you tried so far? My primary obstacle has been getting the sound *hardware* to work, rather than software. Audacity has always served me well, and Rosegarden is well respected. I'm sure you'll get a better list if you post in the Multimedia forum, because I'm really blanking now. I've found several really slick looking ones through StumbleUpon, but unfortunately I haven't bookmarked them.

---

### Post by DucentiVigintiDuo on 2007-06-01
> **ronocdh said:**
> I'm not optimistic about this. I think you should back up your data, wipe your drive completely, and install OS X. Once that's done you can create another partition for Ubuntu, then install Ubuntu.

I see...I was kinda hoping I could save myself from yet another deletion of Ubuntu now that I've set everything up again but I guess it can't be avoided.

I only want to use OS X for recording in Garageband and editing graphics in Photoshop.
I'm going to be using Ubuntu as my main OS. Do you think 20GB is enough for OS X to.."breathe" considering I'll only be doing the aforementioned things on it?

My hard drive's 60GB (well, 55.6 or so really).

If you have any links to analytical guides as to how to install Ubuntu from OS X using reFIT, that'd be very helpful.

> **ronocdh said:**
> Hm, what have you tried so far? My primary obstacle has been getting the sound *hardware* to work, rather than software. Audacity has always served me well, and Rosegarden is well respected. I'm sure you'll get a better list if you post in the Multimedia forum, because I'm really blanking now. I've found several really slick looking ones through StumbleUpon, but unfortunately I haven't bookmarked them.

Now that you mention this, it might be hardware problems for me too, but - in contrast to the other problems I've had with Ubuntu - I'm completely lost when trying to research sound related problems on my Macbook. I've tried browsing all the relative sections on this forum and I've even posted on a couple of topics but my calls for help have been ignored.
My main problem is that the JACK server doesn't work as it's supposed to...the sound crackles all the time and when I try to record in ardour I get skippy sound.

It's really frustrating because (even though I still think OS X is a great operating system) I like Ubuntu so much I never wanted to go back to dual booting. If I could find a decent recording solution that works, I could make myself get used to it as a Garageband replacement. GIMP is always a good candidate for a Photoshop replacement.

---

### Post by ronocdh on 2007-06-01
> **DucentiVigintiDuo said:**
> I see...I was kinda hoping I could save myself from yet another deletion of Ubuntu now that I've set everything up again but I guess it can't be avoided.

I only want to use OS X for recording in Garageband and editing graphics in Photoshop.
I'm going to be using Ubuntu as my main OS. Do you think 20GB is enough for OS X to.."breathe" considering I'll only be doing the aforementioned things on it?
I do, yes. With only a 60GB HD, I think a 20/40 split should be reasonable. Remember that when you're installing OS X, there'll be a tucked away "Options" button which will allow you to configure what exactly is installed. If you want to trim down the installation size, you can remove certain foreign languages you don't see yourself using, even some iLife apps, if you want (though I know you said you like GarageBand). If you find that you took too much off and change your mind later, I believe anything can be added later by inserting the installer DVD and booting into it.
> If you have any links to analytical guides as to how to install Ubuntu from OS X using reFIT, that'd be very helpful.
It's a very trivial process, actually. Once OS X is installed, install [rEFIt]("http://refit.sf.net"), partition your drive (I recommend using the terminal command **sudo diskutil resizeVolume**, but the Boot Camp GUI tool will work perfectly, too), then boot to the Ubuntu disc and install that on the newly created partition. Don't create a separate partition for a swap file; it'll bug you, but say you know what you're doing. You can always create a swapfile later.

The sole caveat in my mind about using the Boot Camp partitioning tool is that it really only allows for the creation of one extra partition, i.e. for Ubuntu. But if you're serious about never wanting to install Windows, then hey, go for it! I'm still triple booting like a goon myself.
> Now that you mention this, it might be hardware problems for me too, but - in contrast to the other problems I've had with Ubuntu - I'm completely lost when trying to research sound related problems on my Macbook. I've tried browsing all the relative sections on this forum and I've even posted on a couple of topics but my calls for help have been ignored.
My main problem is that the JACK server doesn't work as it's supposed to...the sound crackles all the time and when I try to record in ardour I get skippy sound.
IIRC, you have a regular MacBook (C2D), right? I'm sorry, but I have very little experience getting sound recording to work in Ubuntu on the Macs. I'm very interested to have it working... one would think the Ubuntu Studio community would have made contributions to this effort, but perhaps I'm misreading them. We'll see in time, hopefully. In the meantime, all progress toward getting recording working, or using JACK, should be posted in the forums!
> It's really frustrating because (even though I still think OS X is a great operating system) I like Ubuntu so much I never wanted to go back to dual booting. If I could find a decent recording solution that works, I could make myself get used to it as a Garageband replacement. GIMP is always a good candidate for a Photoshop replacement.
Glad to hear it, although I recommend you retain OS X at least on a tiny partition: it'll be necessary for any firmware updates down the line, and plus, Ubuntu's power management is absolutely horrid, no? My battery life is half that of what it is in OS X! :-P

---

### Post by DucentiVigintiDuo on 2007-06-01
> **ronocdh said:**
> Don't create a separate partition for a swap file; it'll bug you, but say you know what you're doing. You can always create a swapfile later.The sole caveat in my mind about using the Boot Camp partitioning tool is that it really only allows for the creation of one extra partition, i.e. for Ubuntu. 

I've dual booted from OS X into Ubuntu before but it was with bootcamp, and it was really easy to create an extra partition for the swap partition. If I use reFit and the terminal command will it be too hard for me? I'm even more of a n00b at the Mac terminal than I am at the Linux one.

> **ronocdh said:**
> But if you're serious about never wanting to install Linux, then hey, go for it! I'm still triple booting like a goon myself.

That...confused me. Serious about never wanting to install Linux? You mean not wanting to format and reinstall it again?

> **ronocdh said:**
> IIRC, you have a regular MacBook (C2D), right? I'm sorry, but I have very little experience getting sound recording to work in Ubuntu on the Macs. I'm very interested to have it working... one would think the Ubuntu Studio community would have made contributions to this effort, but perhaps I'm misreading them. We'll see in time, hopefully. In the meantime, all progress toward getting recording working, or using JACK, should be posted in the forums!

No, it's a first-gen Macbook. Core Duo. I guess I'll just install OS X after all and get done with it. It's too much trouble for my musician side. My geek/programmer side can get its fill with other problems to solve and other things to customize. :P

> **ronocdh said:**
> Glad to hear it, although I recommend you retain OS X at least on a tiny partition: it'll be necessary for any firmware updates down the line, and plus, Ubuntu's power management is absolutely horrid, no? My battery life is half that of what it is in OS X! :-P

True, and true. But I still like Ubuntu more :D Especially since I don't use the laptop without its power supply that much. Still, do you think something will be done about that terrible power management in the future?

By the way, a huge ***thank you*** to you for replying and helping me out. :)
I really appreciate it.

---

### Post by ronocdh on 2007-06-01
> **DucentiVigintiDuo said:**
> I've dual booted from OS X into Ubuntu before but it was with bootcamp, and it was really easy to create an extra partition for the swap partition. If I use reFit and the terminal command will it be too hard for me? I'm even more of a n00b at the Mac terminal than I am at the Linux one.Go ahead and use Boot Camp, no problem there. All rEFIt does is provide you with a bootloader, and it just so happens to be much prettier than Boot Camp's! You can also remove it at any time. It is not necessary to use rEFIt to dual boot OS X and Ubuntu; however, as I understand it, Ubuntu will be represented with a greyscale Windows XP logo, instead of a colorful Tux the Penguin icon. ;)
> That...confused me. Serious about never wanting to install Linux? You mean not wanting to format and reinstall it again?Dude, very sorry. I meant that if you were serious about never installing **Windows**, you'd be fine to use Boot Camp. (I have edited the original post to save anyone else confusion.) As I said, Boot Camp is really only good for one extra partition... if you want to triple boot, you'd need two extra.

> No, it's a first-gen Macbook. Core Duo. I guess I'll just install OS X after all and get done with it. It's too much trouble for my musician side. My geek/programmer side can get its fill with other problems to solve and other things to customize.Great. Just remember to use the 32-bit version, blah blah blah (I repeat that here in case anyone else is reading, because there've been many questions about it lately). Sorry Ubuntu Studio didn't treat you well. I had high hopes, with the project leader having the MetalMusicAddict!

> Especially since I don't use the laptop without its power supply that much. Still, do you think something will be done about that terrible power management in the future?Be careful with always leaving your computer plugged in. My sister did that with her PowerBook G4 and the battery actually died, so badly that unplugged the computer meant it shut off (she recently purchased a new battery and all's well). This has to do with the way lithium ion batteries work; [see here for more info]("http://www.apple.com/batteries/notebooks.html").> By the way, a huge ***thank you*** to you for replying and helping me out. :)
I really appreciate it.Any time, man. This is quite a thread!

---

### Post by DucentiVigintiDuo on 2007-06-01
> **ronocdh said:**
> Go ahead and use Boot Camp, no problem there. All rEFIt does is provide you with a bootloader, and it just so happens to be much prettier than Boot Camp's! You can also remove it at any time. It is not necessary to use rEFIt to dual boot OS X and Ubuntu; however, as I understand it, Ubuntu will be represented with a greyscale Windows XP logo, instead of a colorful Tux the Penguin icon. ;)

Yeah, I did a very partial/bad install of rEFIt once and I liked its icons.
What I'm trying to say about bootcamp is, it would just create two partitions, OS X + Empty, and then when I installed Ubuntu, the ubuntu installer/partitioner would create a sub-partition for the swap partition on its own. I'm guessing the same thing could be done by only creating one partition with the terminal command as well? If you'd be willing to give me some help with that over AIM when the time comes I'd appreciate it immensely.


> **ronocdh said:**
> Dude, very sorry. I meant that if you were serious about never installing **Windows**, you'd be fine to use Boot Camp. (I have edited the original post to save anyone else confusion.) As I said, Boot Camp is really only good for one extra partition... if you want to triple boot, you'd need two extra.

It's ok. Yeah, I'm pretty serious about not installing Windows ever again. I hate it so much. Only reason I'd see myself doing that would be to play games, and that will only happen if I either get a Macbook Pro or a separate machine for gaming (integrated graphics card on MB sucks as you probably know). I mean the Macbook was my initial attempt to leave Windows behind, and a very pleasant one at that. :D

> **ronocdh said:**
> Great. Just remember to use the 32-bit version, blah blah blah (I repeat that here in case anyone else is reading, because there've been many questions about it lately). Sorry Ubuntu Studio didn't treat you well. I had high hopes, with the project leader having the MetalMusicAddict!

Is that 32-bit version of OS X?  I'm just installing from the packed OS-disk that came along with the Macbook so I think I'm safe there. Sorry if that's a stupid question but as far as I know Ubuntu Studio's only out as a 32-bit version.

As for Ubuntu Studio failing me, I guess I can't have it all yet...hopefully in a few years' time hardware compatibility will increase and software will be less buggy, allowing me to fully run Ubuntu.

> **ronocdh said:**
> Be careful with always leaving your computer plugged in. My sister did that with her PowerBook G4 and the battery actually died, so badly that unplugged the computer meant it shut off (she recently purchased a new battery and all's well). This has to do with the way lithium ion batteries work.

Thanks again for the advice man, I know about lithium ion batteries and maintenance issues. I'm supposed to do this whole discharge-charge cycle every once in a while but I haven't been really paying attention to that. I thought of removing the battery but on the Macbook the battery itself is the cover below so I'm not sure it would be safe for the computer to be exposed like that.

If worse comes to worst I guess I'll just buy a new battery (if I need to use the laptop in places with no power plugs, that is) ;)

Thanks again :popcorn:

---

### Post by ronocdh on 2007-06-01
> **DucentiVigintiDuo said:**
> Yeah, I did a very partial/bad install of rEFIt once and I liked its icons.
What I'm trying to say about bootcamp is, it would just create two partitions, OS X + Empty, and then when I installed Ubuntu, the ubuntu installer/partitioner would create a sub-partition for the swap partition on its own. I'm guessing the same thing could be done by only creating one partition with the terminal command as well? If you'd be willing to give me some help with that over AIM when the time comes I'd appreciate it immensely.Of course I'd help; I have AIM posted in my profile on these forums, although we'd probably have to work out a mutually convenient time. The Feisty GUID installer will probably attempt to have create a swap partition, which you could let it to, if you want. The primary argument against this is for triple booters who run into the partition limit due to GPT wonders (because the Mactels are EFI-based); since you have no interest in Windows, I guess the creation of a swap partition is logical (no pun intended).
> Is that 32-bit version of OS X?  I'm just installing from the packed OS-disk that came along with the Macbook so I think I'm safe there. Sorry if that's a stupid question but as far as I know Ubuntu Studio's only out as a 32-bit version.I meant 32-bit Ubuntu. As I understood it, I thought you were leaving Ubuntu Studio and switching to regular Feisty. I guess I was mistaken.

Hell of a thread we had going here!

---

### Post by DucentiVigintiDuo on 2007-06-01
> **ronocdh said:**
> Of course I'd help; I have AIM posted in my profile on these forums, although we'd probably have to work out a mutually convenient time.

Sure, no problem. It'll probably be a week and a few days until I go back home and get recording so I'll PM you when the time comes.

> **ronocdh said:**
> I meant 32-bit Ubuntu. As I understood it, I thought you were leaving Ubuntu Studio and switching to regular Feisty. I guess I was mistaken.

Oh, I see. You weren't mistaken, it's what I've done already (already formatted from Ubuntu Studio and just went back to regular Feisty) and what I'll do again. I'm using a great version from Linux Format magazine that comes with pre-installed packages, more "just works" functionality right there. ;) You can blame this misunderstanding on me, I'm very tired as I'm studying for my last final that is in... *checks clock* 9 hours and 4 minutes. Tomorrow I'll be free as a bird, only having to pack and stuff....

..which probably means scratch the "in one week" comment I mentioned before. I'll probably install Mac OS X before I go back home so expect a PM soon :P

> **ronocdh said:**
> Hell of a thread we had going here!

Indeed!

---

