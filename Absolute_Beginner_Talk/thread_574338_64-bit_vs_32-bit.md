---
title: "64-bit vs 32-bit"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-12
it there any major advantage of using the 64-bit instead of the 32-bit.  the main programs i will be using is:

FireFox
Eclipse C++
Eclipse PHP
Wine
Open Office
VirtualBox

That is about it.  shoudl i use the 64-bit version or just stay with the 32-bit version?

---

### Post by marshall.robert on 2007-10-12
from what i gather, 64 bit hasnt really taken off on a massive scale yet, so your more likely to find your programs in 32 bit, but the mainstream programs should have a 64 bit version. as for the actual advantages,  i don't know.

persoanlly i'd stick with 32 bit for now.

-rob

---

### Post by om1 on 2007-10-12
i really have had the same question.... havent really seen a straight forward answer.... i just know you can have bad issuse trying to install certian applications and alot of time cannot find 64 bit applications...
i suggest sticking with 32 bit.... unless you find a good reason to use 64 bit edition

---

### Post by rsambuca on 2007-10-12
Whoa, whoa, whoa, whoa.  Where are you guys getting this dis-information from?  The differences in packages from the 32bit to the 64bit repositories is less than 1%, so unless you are going to be using some very obscure piece of software, there is no issue.  Most programs will not be any different.  Some programs will give you a 30%+ performance gain by using the 64bit OS and program.

The previous posters are not giving you current information, just FUD.

---

### Post by jayson.rowe on 2007-10-12
I agree with rsambuca - I wouldn't even THINK of installing a 32 bit version of Linux on a 64 bit system - the same would not be true however with Windows :)

I had been running x64 on my desktop for some time, and I tried going back to 32 because of an obscure font smoothing issue, and I couldn't believe the difference, quickly formatting, and re-installing the x64 version, and then compliling the font packages by hand...

For 99.9999999999% of the packages, you will find the x64 version in the repo, and see no difference other than a speed increase...especially if you have more than 3GB of memory.

---

### Post by r4ik on 2007-10-12
Perhaps but, that is the only thing, it needs a little bit more 'handling"
But if you are wiling or able to do do that i see no probs.

---

### Post by r4ik on 2007-10-12
> **jayson.rowe said:**
> I agree with rsambuca - I wouldn't even THINK of installing a 32 bit version of Linux on a 64 bit system - the same would not be true however with Windows :)

I had been running x64 on my desktop for some time, and I tried going back to 32 because of an obscure font smoothing issue, and I couldn't believe the difference, quickly formatting, and re-installing the x64 version, and then compliling the font packages by hand...

For 99.9999999999% of the packages, you will find the x64 version in the repo, and see no difference other than a speed increase...especially if you have more than 3GB of memory.

Imo you do not need 3gigs  to run a 64b system.

---

### Post by jayson.rowe on 2007-10-12
I never said you needed 3 gigs or more, I just said that is when the differences really started to shine (memory addressing issues on a 32 bit system over 3 gb)...

I DID say however, that I wouldn't run a 32 bit Linux system on x64 hardware (and that means regardless of memory size).

---

### Post by r4ik on 2007-10-12
> **jayson.rowe said:**
> I never said you needed 3 gigs or more, I just said that is when the differences really started to shine (memory addressing issues on a 32 bit system over 3 gb)...

I DID say however, that I wouldn't run a 32 bit Linux system on x64 hardware (and that means regardless of memory size).

I do not understand why you mentioned the amount of memory then.
Anyway whe do seem to agree for different reasons.

---

### Post by arvevans on 2007-10-12
> **rsambuca said:**
> Whoa, whoa, whoa, whoa.  Where are you guys getting this dis-information from?  The differences in packages from the 32bit to the 64bit repositories is less than 1%, so unless you are going to be using some very obscure piece of software, there is no issue.  Most programs will not be any different.  Some programs will give you a 30%+ performance gain by using the 64bit OS and program.

The previous posters are not giving you current information, just FUD.

===============

I routinely use Ham Radio and Electrical Engineering software on my computer.  When I upgraded to an AMD 2X 64-bit 3200 system I installed the 64 bit version of Ubuntu 7.04.  I agree with the earlier post that most of the 32 bit applications on Ubuntu's repository are also available in 64 bit form.  Where I found problems was in the non-Ubuntu supported applications that were specific to Ham Radio and Electrical Engineering.  Many of these are not available in 64-bit form.  Some had source code available and could be compiled to 64 bit, but some did not.  I also spent an inordinate amount of time tracking down include-files for supporting those 64 bit compiles that I was able to do.

As a result of all this, I am now running the 32-bit version of Ubuntu 7.10 on my 64-bit AMD X2 system.  It may not be the perfect solution, but now I am able to run some of that obscure software that i find necessary to pursue my work and hobby interests.

Not trying to tell you that you should be running 32 bit software on your 64 bit machines...just that it is possible (both CPU's are operational and speed is acceptable).  If there is a specific piece of software that you must have, and it is not available in 64 bit mode, and if you cannot get it to compile into 64 bit mode, then running the 32 bit operating system may be your only solution.

Arv
_._

---

### Post by r4ik on 2007-10-12
Agreed.
Still i think with the development of the dual/quad, and the trippel core,there should be some developer's work to do.
Oke it wont be me.

---

### Post by Joeb454 on 2007-10-12
I tried the 64-bit live CD of Gutsy earlier, was very impressed, ran quicker than my 32 bit system that's properly installed!! (although this pc has a dual core and twice as much RAM).

Only problem I had is that I can't seem to enable support for AAC files, or some AVI files which I could with 32 bit with the xine back-end, it won't install in 64 bit

---

### Post by avik on 2007-10-12
With 32-bit, you're limited to 4GB memory.  Not a problem for most people, but you can go much higher with 64-bit.

Personally, I don't see why you wouldn't take advantage of your hardware if you have it.  At least with Ubuntu, there's pretty much *nothing* you'll miss out on in terms of software support.

---

### Post by RyanZec on 2007-10-12
yea, I will give it a try and hope all my software works, if not i will just go back to 32-bit.

---

### Post by Joeb454 on 2007-10-12
Thats my plan, lol

---

### Post by jayson.rowe on 2007-10-12
> **r4ik said:**
> I do not understand why you mentioned the amount of memory then.
Anyway whe do seem to agree for different reasons.
I do think you have "Selective Reading Syndrome" my friend...

I only (I'll type it again in case you didn't catch it)...

I ONLY mentioned the memory because a 32 bit OS has trouble accessing memory over 3GB, and simply CAN'T address more than 4. That was my only reason for mentioning it...

OK, one more time...

THAT was my only reason for mentioning it...

As I said, 3 posts ago, I would only run a x64 Linux os on a x64 system, and (I'll rephrase it here so you can better understand), as it's a x64 based system, you get a "double-bonus" of sorts, as it will allow you to address more physical memory...(again, more clarification for you), not that extra memory is NEEDED by any means, it's just that if you have more than 4GB of main system memory, a 32 bit OS will not address it, and you MUST use a x64 OS to see it all. Although a 32 bit system will see memory between the 3GB and 4GB levels, it has trouble accessing all that ram, and can contribute to other problems, that would only surface as unexplainable instability. Again, I'm not saying that you need that much RAM to use a x64 system, I'm only saying that's where the true benefit of such a system starts to show itself, and it becomes needed to run a x64 system to truly cap into the capabilities of your system....

God, I hope that makes it clearer for you.

As a side note, for me, I really like Ubuntu, as it was a natural progression from Debian, providing basically a means to run a more up-to-date system than Debian Stable without the "rolling-releases" of Testing (Lenny) and Unstable (Sid). I DO need to stop reading these forums, because all I ever see here it seems is FUD both by the veterans and the newbies alike. Everyone here is so quick to argue in fear of either (I'm assuming here), being proven wrong, or having someone devalue their choices, and in turn shrink there e-ego...it is a freakin computer operating system for gods sake...it's a tool...a means to get a job done. Nothing more, nothing less. I almost feel like that last sentence will make someone cry themself to sleep tonight once they come to grips with both reality and the realization that I'm right.

---

### Post by DarkDancer on 2007-10-12
64-bit Feisty was nice. 64-bit Gutsy is AWESOME.

---

### Post by r4ik on 2007-10-13
> **jayson.rowe said:**
> I do think you have "Selective Reading Syndrome" my friend...

I only (I'll type it again in case you didn't catch it)...

I ONLY mentioned the memory because a 32 bit OS has trouble accessing memory over 3GB, and simply CAN'T address more than 4. That was my only reason for mentioning it...

OK, one more time...

THAT was my only reason for mentioning it...

As I said, 3 posts ago, I would only run a x64 Linux os on a x64 system, and (I'll rephrase it here so you can better understand), as it's a x64 based system, you get a "double-bonus" of sorts, as it will allow you to address more physical memory...(again, more clarification for you), not that extra memory is NEEDED by any means, it's just that if you have more than 4GB of main system memory, a 32 bit OS will not address it, and you MUST use a x64 OS to see it all. Although a 32 bit system will see memory between the 3GB and 4GB levels, it has trouble accessing all that ram, and can contribute to other problems, that would only surface as unexplainable instability. Again, I'm not saying that you need that much RAM to use a x64 system, I'm only saying that's where the true benefit of such a system starts to show itself, and it becomes needed to run a x64 system to truly cap into the capabilities of your system....

God, I hope that makes it clearer for you.

As a side note, for me, I really like Ubuntu, as it was a natural progression from Debian, providing basically a means to run a more up-to-date system than Debian Stable without the "rolling-releases" of Testing (Lenny) and Unstable (Sid). I DO need to stop reading these forums, because all I ever see here it seems is FUD both by the veterans and the newbies alike. Everyone here is so quick to argue in fear of either (I'm assuming here), being proven wrong, or having someone devalue their choices, and in turn shrink there e-ego...it is a freakin computer operating system for gods sake...it's a tool...a means to get a job done. Nothing more, nothing less. I almost feel like that last sentence will make someone cry themself to sleep tonight once they come to grips with both reality and the realization that I'm right.

i read you loud and clear.
I did not meant to step on you're toes and if i did i am sorry.

---

### Post by zyg0t3 on 2007-10-13
For all those running 64 Gutsy. Are you running it on desktops or laptops? Reason why i ask is i can't, for the life of me, get my broadcom 4311 wifi running after spending 2 days working on it. I'm giving on up the 64 and i'm going to see if the 32 will get it going. Any help would be appreciated. In my search i've found that it seems to be a 64 bit problem. I also tried Sabayon 4.3f, thats a no go as well. I heard that pclos works out of the box.

---

### Post by Joeb454 on 2007-10-13
I tried the 64 bit Gutsy live CD on a laptop, and everything worked out the box, so I'll be partitioning my drive sometime soon :) - Probably when Gutsy final is released

---

### Post by 1danjack on 2007-10-13
i thought in windows you could run a 32bt application on a 64bit system.
is this not the case in linux?

---

### Post by jayson.rowe on 2007-10-13
You can in both 1dan, I think (personally) that Linux handles it better than windows (Which uses WoW - or "Windows on Windows" - however, it varies from Distro to Distro how they handle it - Ubuntu and openSUSE handle it the best in my opinion. If you install Fedora (amd64), and then run a system update, you'll see it downloading i386 and x64 veresions of everthing - Ubuntu (Debian) and Suse don't do that.

---

### Post by RyanZec on 2007-10-13
i ust got my new laptop and was installing a few thing on vista before i started to install unbuntu 64-bit.  I noticed that it says amd6 when i load the cd, do i have to have an AMD processor to run 64-bit on ubuntu cause i have an Intell?

---

### Post by om1 on 2007-10-13
no you dont have to have amd.

---

### Post by Kilz on 2007-10-13
> **om1 said:**
> no you dont have to have amd.

No, any 64bit intel emt64 processor like the core2duo, celeron D (64bit versions) will also work.

---

### Post by om1 on 2007-10-13
thats what i meant by that sorry if it wasn't clear

---

### Post by Billy_McBong on 2007-10-13
[COLOR="Blue"]its good to hear there isn't many problems with running 64-bit. i think thats the version im gonna download on Thursday[/COLOR]
> **jayson.rowe said:**
> .it is a freakin computer operating system for gods sake...it's a tool...a means to get a job done. Nothing more, nothing less. I almost feel like that last sentence will make someone cry themself to sleep tonight once they come to grips with both reality and the realization that I'm right.[COLOR="Blue"]*lays on the floor in the fetal position and starts crying*[/COLOR]

---

### Post by Frak on 2007-10-13
If you have a 64-bit system, go for a 64-bit OS. The bridge between 32 and 64 is almost complete, even though only 1% of the apps that need said bridge are super obscure.

Flash with nspluginwrapper runs fine.

---

### Post by RyanZec on 2007-10-13
i tried to install using the live cd but when i select start the screen just goes blank.  my speces are:

Intel 2.2GHz 64-bit
GeForce 8600 GT Go 512MB Video card
BUILT-IN AC 97 SOUND

not sure it anthing matters, shoudld i be able to install witht he alternate 64-bit cd?

---

### Post by Frak on 2007-10-13
> **RyanZec said:**
> i tried to install using the live cd but when i select start the screen just goes blank.  my speces are:

Intel 2.2GHz 64-bit
GeForce 8600 GT Go 512MB Video card
BUILT-IN AC 97 SOUND

not sure it anthing matters, shoudld i be able to install witht he alternate 64-bit cd?
Could you give the model of your Intel?

---

### Post by RyanZec on 2007-10-13
> **Frak said:**
> Could you give the model of your Intel?

this is all i knowabout my CPU:

Intel(R) Core(TM) 2 Duo Mobile T7500 Dual-Core Processor @ 2.20GHz 800FSB 4MB L2 Cache 64-bit

---

### Post by RyanZec on 2007-10-13
I just tried to install in with the alternate cd but the partationer just sat at 0% for like an hour.  anyone know a tool for resize partations in vista?

---

### Post by rsambuca on 2007-10-13
Ooo, if you are going to resize Vista partitions it is definitely best to use the Disk Manager from within Vista.  Shrink the Vista partition and then install Ubuntu into the empty space.

---

### Post by misfitpierce on 2007-10-13
You can run 32 bit programs in the 64 bit and the 64 bit has speed increases for file copying etc as well as programs.

---

### Post by bsalt on 2007-10-13
I've been asking this question for a while now, as I'm using a Pentium D 3.0 ghz process that is EM64T ready. I'd love to take advantage of the 64-bit aspect of it, but I don't do anything intense enough on my computer to ever need it. In Linux, I only use Pidgin, Rhythmbox, Firefox, Evolution, and some Open Office. With 3ghz dual-core in Linux, it is just not needed for me to use 64-bit, and yes, it still is not quite as needed for me still.

---

### Post by Frak on 2007-10-13
> **bsalt said:**
> I've been asking this question for a while now, as I'm using a Pentium D 3.0 ghz process that is EM64T ready. I'd love to take advantage of the 64-bit aspect of it, but I don't do anything intense enough on my computer to ever need it. In Linux, I only use Pidgin, Rhythmbox, Firefox, Evolution, and some Open Office. With 3ghz dual-core in Linux, it is just not needed for me to use 64-bit, and yes, it still is not quite as needed for me still.
Your system will probably boot up faster and work just a bit faster on a 64-bit OS.

My 64-bit machine boots firefox in 0.3 seconds, and boots up in 3 seconds. (My Mac is my 64-bit machine for anyone wondering)

---

### Post by 1danjack on 2007-10-14
> **misfitpierce said:**
> You can run 32 bit programs in the 64 bit and the 64 bit has speed increases for file copying etc as well as programs.

Do you know why it is that I cannot install realplayer from [here?]("http://ubuntuforums.org/showpost.php?p=2720883&postcount=4")

Or even when it's downloaded from the realplayer website, as discussed [here.]("http://ubuntuforums.org/showthread.php?t=571358")

---

### Post by skewbie on 2007-10-18
Hi I have a Dell Optiplex G620 with an Intel Pentium D Dual core 3.2GHz (EM64T) processor with 2GB (2x1GB) of Crucial Ballistix memory.

I have downloaded the 64-bit Gutsy today and tried to run off the live cd to do an install. However, when I boot off the cd and get to the install menu, my keyboard no longer works. Also when the install countdown gets to zero, it doesn't boot it just hangs there.

This only happens once I have booted off the CD as I can still hit F2/F12 to enter BIOS etc.

Does anyone know if there is a problem with 7.10 64-bit and the above processor or is this something else...? :confused:

Thanks.

---

### Post by rsambuca on 2007-10-18
That should work fine with your system.  There are a few things to check:

Did you check the md5sum prior to burning?
Did you burn the cd a very slow rate to avoid single bit errors?
Did you run the CD check prior to booting up?

---

### Post by skewbie on 2007-10-18
Hi rsambuca, thanks for the quick response.

In answer to your questions...umm...no, no and.... ah no.

How do I run the CD check prior to booting up?

thanks again :)

---

### Post by bsalt on 2007-10-18
Yeah, like rsambuca said, it could be a bad cd you burned (I've had corrupt downloads happen on more than one occasion. If you download and burn an .iso, it's a safe bet to not use DownThemAll or some other download accellerator. Just download it plain and when it is done, check the md5sum, burn it, and try again. Also, you could try downloading an Ubuntu Alternate .iso for AMD64 edition and try that.

---

### Post by bwallum on 2007-10-18
Hi

Just to let you know my rig runs fine with Gutsy and the eye candy. It is also quicker than 32 bit. I would go 64bit if you have the choice. OpenOffice, Firefox, Evolution, MPlayer all work fine. The only thing that has given me any clitches is Fish Fillets, but these things get fixed quick enough.

Go 64bit!

---

### Post by rsambuca on 2007-10-18
> **skewbie said:**
> Hi rsambuca, thanks for the quick response.

In answer to your questions...umm...no, no and.... ah no.

How do I run the CD check prior to booting up?

thanks again :)

There should be a selection at the main menu.  I can't remember for sure, but I think it says something like 'cd integrity check'.  My guess is a bad burn.

---

### Post by Hexaphim on 2007-10-18
I'm looking to try out Ubuntu on a dual-boot with Vista. I have an AMD Athlon 64 X2 5000 processor and 2 GB RAM, and I'm currently running Vista Home Premium 64 bit.

I'm a bit unsure about whether to install the 32 bit or the 64 bit version. I want to be able to access my Windows NTFS partitions, and if possible to play World of Warcraft (through some sort of emulator, I saw a recipe somewhere). From what I've been able to gather from a quick Google search, both of these things should be possible on a 32 bit installation, but can the same be said for the 64 bit version? 

Thanks in advance. :)

---

