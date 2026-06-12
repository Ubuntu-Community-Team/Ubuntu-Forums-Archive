---
title: "[SOLVED] Ubuntu ---&amp;quot;user friendly&amp;quot;....yeah right"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-13
Ok let me explain first.

I have installed version 6.10. I am trying to updrade to version 7.04 via update manager.  Whenever i try i receive the message : 

"The upgrade aborts now. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed:

This has hapened several times and it is extremely frustrating.

This is about the 15th complication (no exaduration) i have had with my ubuntu install.  I am tired of it.  I wouldnt be so angry if everyone didnt brag about how user friendly the software is. I am not computer illiterate.  I am in my 4th year of school as a Computer information systems major.  This will be my life!  I just dont understand how this can be so difficult for me, if the average "joe" is supposed to be able to use this.  PLEASE HELP!!!

---

### Post by locke.dragon on 2007-06-13
why don't you just burn a live cd of the newest version, back up your data and settings, delete your current ubuntu partitions, re-install in the "largest contiguous space," and start over?  that's what i do when something goes wrong (i mess with settings and other stuff and have to re-install quite often).

---

### Post by click4851 on 2007-06-13
yeah I have to agree with dragon, I tried the upgrade route but had trouble with nvidia video drivers, and sound issues. So I backed up my /home partition and just downloaded 7.04 and formatted the drive, fresh load, done in 20 min. give it a shot, can't be worse than what you have now. Don't beat yourself up over and over.

---

### Post by locke.dragon on 2007-06-13
i love it when i'm right!  :P

---

### Post by mgh on 2007-06-13
Same advice here.  I am complete NOOB to Linux, but was advised to do a clean install instead of upgrade and it did work for me.

Good luck.

---

### Post by TeraDyne on 2007-06-13
"User Friendly" doesn't mean perfect. You can have this sort of problem upgrading a piece of software in Windows as well.

Anyway, do as they said. Back up and install using a burned CD. I myself didn't have a problem, so I can't help too much beyond that advice.

---

### Post by mgmiller on 2007-06-13
Usually, there are upgrade problems when someone goes outside the standard Ubuntu repositories for video drivers and things like that.  I have also heard that using Automatix or easy ubuntu can create problems on upgrades.  Also, did you do the approved method for updating using update manager   ```
gksu "update-manager -c"
```.  If you tried changing the entires in sources.list and then did command line sudo apt-get update, etc.  This could also create problems as the update manager does things differently to avoid these kinds of issues.  As you can see from my sig, I have upgraded Ubuntu a lot and I have found, especially with this last 6.10 to 7.04 upgrade, that it was damn near seamless.

---

### Post by ryanVickers on 2007-06-13
I would never trust the update manager to do an upgrade like this!  I once was just upgrading from 6.06 to 6.1 (MINOR CHANGE) and it did this!  Never mind to 7.04!  I would just burn a new disk.

---

### Post by FleetAdmiral74 on 2007-06-13
I am sorry you did not have a good experience, I think it is for the most part extremely user friendly and intuitive. Just stick with it.

---

### Post by testube_babies on 2007-06-13
I'd have to agree that this is one aspect of Ubuntu that's never quite fallen together as it should.  As soon as you install a software package from outside the official repositories, a dist-upgrade is likely to fail.  

Unfortunately, this is a problem that can only be fixed by putting more software packages in the repositories!

Other than this, however, I have to say the Ubuntu is extremely user-friendly, and by far the most user-friendly linux distribution I have ever used.

---

### Post by RichPicker on 2007-06-13
I second that -  hang in there. It's quite a learning curve, but worth it.

---

### Post by nukkariffic on 2007-06-13
I wouldn't be so hard to judge... think about it... would you be able to upgrade from XP to Vista without a CD?  95 to 98? I know that's a bit of a stretch, but it's an analogy.  If you can't do that, think about when XP went from SP1 to SP2.  There were countless people who had enormous problems.  At least w/ Ubuntu, installing is a breeze and hardly takes any time.  In fact, I did a fresh install today on my *lunch break.*  It was up and running again with everything I needed before I had to be back at school.  Try that w/ Windows.

just hang in there and keep on learning.  It'll get easier as you figure more things out. :D

---

### Post by ITdrummer on 2007-06-13
> **testube_babies said:**
> 

Unfortunately, this is a problem that can only be fixed by putting more software packages in the repositories!

how do i do this?

---

### Post by locke.dragon on 2007-06-13
that's not something YOU do.  it's something the ubuntu developers do.  they add more over time.  your best bet is to burn the new cd.

---

### Post by hummingbird59 on 2007-06-13
May I ask a really dumb question?  I don't have a home partition so what is the best way to back up my settings, ie desktop background, thunderbird, firefox bookmarks etc... for when a fresh install becomes necessary? Thanks!?

---

### Post by TeraDyne on 2007-06-13
> **hummingbird59 said:**
> May I ask a really dumb question?  I don't have a home partition so what is the best way to back up my settings, ie desktop background, thunderbird, firefox bookmarks etc... for when a fresh install becomes necessary? Thanks!?

DVD+\-Rs. Backup everything in your home directory. That's as far as I usually go.

---

### Post by hummingbird59 on 2007-06-13
Thanks - that's the answer I was hoping for but wasn't sure:D

---

### Post by Gmbrdilos on 2007-06-14
1. User friendly doesn't mean easy exit that requires ZERO input. 

2. Try a fresh install with fiesty

3. 0MG L1nuX r0x0rz FTW!111oneone (yeah that last one came out stupid)

---

### Post by ITdrummer on 2007-06-14
> **nukkariffic said:**
> I wouldn't be so hard to judge... think about it... would you be able to upgrade from XP to Vista without a CD?  

Ha, i still like windows but i wouldn't switch to Vista if Microsoft payed me!
I understand there is a learning curve, but in all my years of experience, I have NEVER been this frustrated with the OS......call me crazy...

---

### Post by OldTimeTech on 2007-06-14
Not crazy, just frustrated and many of us as newbies had the same frustrations and yelled and screamed alot, but take a breather and then back everything you want to keep up and use a new cd and reload ;)

---

### Post by ITdrummer on 2007-06-14
I dont have anything to back up. It is a freshly formatted Hard Drive.  I have tried with a cd several, several times and that is the reason why i am trying to upgrade via the update manager. I got tired of making coasters! lol

---

### Post by Cypher on 2007-06-14
I think only those of us "lucky" enough to have dealt with Linux at it's various stages of maturation can truly appreciate how "user friendly" Ubuntu is. For most novices, new to Linux, it can be a very different and frankly difficult OS.

Back in the day, installing Linux always meant that you first got the base system installed which got you to a command prompt. From there, you'd need to the XFree installed and then run through the configuration to get it setup. Along the way you'd have to go through and recompile the Kernel and get some specific modules. Tweak a few more configuration files and finally you'd be in a windowing environment. And THEN you'd need to get your window manager configured and so on..

Now compare that to Ubuntu's Live CD..pop a CD and in MOST cases, within 5 minutes you're sitting at a Gnome desktop with fully access to the web through Firefox, email through Evolution, a handful of games, you can read your PDF files, print them if you wish, listen to your music and check out all your pictures.

Believe me when I say, every time I look at this, I just smile, nod and say, WOW! 

This might all sound a little boring, and might remind you of those "Back when I was a young boy.." stories from your father/grand-father, but it's important.

Having said all that..Ubuntu/Linux isn't perfect. For many people, it works 100%, the first time. For most others it works about 80-90% and needs some tweaking.

Now you might have fallen into the lower percentage of people for whom there are more issues, but if you persevere, I'm sure you'll manage to get Ubuntu functioning like a champ..

---

### Post by ITdrummer on 2007-06-14
I am new to the implementation of linux.  Although, i have talked to people who are long time linux users and i do fully appreciate what we/I have available.  I just am having a hard time understanding why version 6.10 installed NO problem, but 7.04 is being stubborn.  Im sorry if i have offended anyone with my frustrations. I understand what type of product i have available to me, i just want to use it!! ha ha  Anyway, i will keep trying: because afterall, windows sucks.

---

### Post by wpshooter on 2007-06-14
> **ITdrummer said:**
> I dont have anything to back up. It is a freshly formatted Hard Drive.  I have tried with a cd several, several times and that is the reason why i am trying to upgrade via the update manager. I got tired of making coasters! lol

This is the reason I have some good quality CD-RWs.  NO, coasters just erase them and use over & over & over again.

---

### Post by ITdrummer on 2007-06-14
What is a "good quality" RW ?  I just buy memorex

---

### Post by lazyart on 2007-06-14
> **ITdrummer said:**
> Ha, i still like windows but i wouldn't switch to Vista if Microsoft payed me!
I understand there is a learning curve, but in all my years of experience, I have NEVER been this frustrated with the OS......call me crazy...


Liinux != Windows, therefore
Windows experience != Linux experience

All your years of experience mean there is more to unlearn.  This is not a knock on you at all, but the sooner you can let go of the "If I can't do this, how can the average Joe" sentiment, the easier it will all come.  Besides, the average Joe never installs or upgrades an OS.  They just buy a new machine and it's done for them.... right?

I've personally been through TRS-DOS, CP/M, MS-DOS, Commodore, Apple ][, Windows and Linux.  Things are just different platform to platform.  Maybe back in the day we all realized this and it was easier to move from each machine because you knew it would be different.

---

### Post by OldTimeTech on 2007-06-14
Plus make sure your burning an iso image and not just burning a regular image, that's what makes coasters

---

### Post by wpshooter on 2007-06-14
> **ITdrummer said:**
> I am new to the implementation of linux.  Although, i have talked to people who are long time linux users and i do fully appreciate what we/I have available.  I just am having a hard time understanding why version 6.10 installed NO problem, but 7.04 is being stubborn.  Im sorry if i have offended anyone with my frustrations. I understand what type of product i have available to me, i just want to use it!! ha ha  Anyway, i will keep trying: because afterall, windows sucks.

Itdrummer:

I have a couple of machine on which I have had 2 different Ubuntu O/Ss installed on (Dapper & Edgy) and both machines ran fine.  

But when I try to install what is supposed to be a newer and improved Ubuntu (namely Feisty), these same 2 machines that ran ran Dapper & Edgy fine, will NOT run Feisty properly because every time I attempt to go into the terminal I start getting endlessly repeating error messages generated and displayed in the terminal.

Logically you would think if a computer would run on an older version of an O/S, then it should run at least as well if not better on an improved/later version of that same O/S.

I can see your point that this is somewhat frustrating.

Good luck.  Hang in there.

---

### Post by ITdrummer on 2007-06-14
Well the "coasters" i have made will boot, bring me to the initial screen with the options:

1) run or install ubuntu
2) check the cd for defects
.
.
.
.
.(dont quite remember all the choices)

I select "check the cd for defects" and it runs its scan" and when its finished, there are no errors.
So i then choose to "run or install ubuntu".
It runs through the install (i disabled the spash and quiet mode) then it just stops.
Right in the middle of running....it just stops.
I was told just to wait it out, be patient.
I left it alone for 2 hours and it hadnt moved.  My computer is old, but not THAT old.

---

### Post by wpshooter on 2007-06-14
> **ITdrummer said:**
> What is a "good quality" RW ?  I just buy memorex

I prefer Imation.

---

### Post by wpshooter on 2007-06-14
> **ITdrummer said:**
> Well the "coasters" i have made will boot, bring me to the initial screen with the options:

1) run or install ubuntu
2) check the cd for defects
.
.
.
.
.(dont quite remember all the choices)

I select "check the cd for defects" and it runs its scan" and when its finished, there are no errors.
So i then choose to "run or install ubuntu".
It runs through the install (i disabled the spash and quiet mode) then it just stops.
Right in the middle of running....it just stops.
I was told just to wait it out, be patient.
I left it alone for 2 hours and it hadnt moved.  My computer is old, but not THAT old.

How much memory does your computer have ?  Have you used the memtest on the menu to verify the integrity of your memory ?  Have you tried booting with safe graphics mode parameter.  More than likely this hanging is related to either memory or more likely a video card problem.

---

### Post by arvevans on 2007-06-14
The update manager obviously needs some work (UBUNTU TEAM TAKE NOTE).  It has been the subject of many many complaints.  I installed a pure 6.10 system and then tried to use Update Manager to go to 7.04...it failed with complaints about missing files in the repository.  I tried different repositories...same result.

As a result I finally gave up and did as many have suggested.  I download and burned an ISO image CD of the 7.04 installation...backed up my /home onto a CD...installed new from the ISO image, and then copied my /home back into the new system.**[COLOR="Red"] It is not that this process is all that difficult, it is just that the "Upgrade" window pops up but then does not work.  That is frustrating.[/COLOR]**

Of course, on the flip side of that coin...Microsoft does not support any sort of FREE on-line automated upgrade to the next OS version.

I have used some form of Linux from the earliest days of Slackware and finally about 3 years ago converted to 100% Linux on my home computers.  Even with my background and experience it was a bit traumatic at first but now I have found Linux applications that do everything I used to do using Microsoft.  I did have to learn to use Gimp, SAG-CAD, Eagle-CAD, and some of the differences between MS-Office and Open-Office, but it has been worth the effort.  I have not encountered a computer virus in the last 3 years, and my spam email is now detected and effectively handled automatically.  Upgrades have been free and relatively easy to implement.  Incremental updates to the installed OS are set up to be automatic and do not require my intervention.
_._

---

### Post by ITdrummer on 2007-06-14
> **wpshooter said:**
> How much memory does your computer have ?  Have you used the memtest on the menu to verify the integrity of your memory ?  Have you tried booting with safe graphics mode parameter.  More than likely this hanging is related to either memory or more likely a video card problem.

I have 512 mb ram.  I have run the memtest (0 errors). I have tried booting in safe graphics mode.  so it must be a video card issue.  Is there anyway around this other than buying a new video card?

---

### Post by wpshooter on 2007-06-14
> **ITdrummer said:**
> I have 512 mb ram.  I have run the memtest (0 errors). I have tried booting in safe graphics mode.  so it must be a video card issue.  Is there anyway around this other than buying a new video card?

Just for curiosity what is the brand/chipset of the video card ?  Is it ATI or Nvidia ?

After what you have tried, the next logical step is to download, burn, verify and install from the ALTERNATE(text based) CD version of Ubuntu.

---

### Post by ITdrummer on 2007-06-14
Im pretty sure i have an intel chipset (i know, crappy, but the computer was a freebie)  I have tried the alternate cd but found it a little confusing for my noobness. I will try again though as i really like ubuntu.

---

### Post by wpshooter on 2007-06-14
P. S. - Do you have any other O/S already installed on this computer or are you trying to install JUST Ubuntu on a cleanly WIPED drive.

I personally do not like Dual booting.  And I prefer to have my hard drive cleanly WIPED with [www.killdisk.com](www.killdisk.com) before I start an install.

---

### Post by ITdrummer on 2007-06-14
the only other OS i have installed is a clean version of ubuntu 6.10

---

### Post by NeoLithium on 2007-06-14
You can find out the video card with this command in terminal ```
lspci
```
Chances are, once you install you just need to install the xserver-xorg-video-intel package from the repositories :)

---

### Post by ITdrummer on 2007-06-14
sounds easy enough, but thats the problem, i cant get it to install!

---

### Post by NeoLithium on 2007-06-14
I'm not sure if you've been able to boot with the safe video mode, though personally I use the alternate install, do it all through text and configure it that way, makes it quite easy to get around video card problems as you can confiugure it and not need to worry about the LiveCD environment.

---

### Post by locke.dragon on 2007-06-14
what speed are you burning the disk at?  i remember that i had trouble with the loading because i burned it at a speed that was too fast.  try burning it as somewhere around 5x.  ;)

---

### Post by eveljkov on 2007-06-14
I don't know about upgrading ubuntu, but I could write a book on the issues I've had updating various versions of windows.  I ALWAYS do a clean install.  

I'm only on day 2 of my linux adventure and I already appreciate the flexibility of it.  Even though it's been giving me hell! But thats because I'm trying to integrate it with Active Directory.

---

### Post by ITdrummer on 2007-06-14
Every time i have tried to burn it, i burn at 1X.

---

### Post by ITdrummer on 2007-06-14
Ok i have a rather easy question.  If i wanted to do a painless format/wipe of my hard drive, is killdisk user friendly. Because i get sort confused around partitions. lol

---

### Post by ITdrummer on 2007-06-14
Which brings me to another point.  At the install when it is asking you how you want the partitions sized....i have no idea what to do.  I have a 10 Gb hard drive with 512 mb of ram.  I want it to run smooth(and/or quick) and i dont really plan on saving a whole helluva lot of data on it.....any suggestions?

---

### Post by abn91c on 2007-06-14
dude, first run the dpkg command the upgrade told you about in a terminal, then try sudo apt-get dist-upgrade

---

### Post by ITdrummer on 2007-06-14
ok good news, i downloaded and installed the alternate cd.  NO PROBLEMS!!!!!  i guess i just had luck!  

ok at the end of the install when it tells you the install was complete..the screen was full of intermittent black bars vertically down the screen.
I rebooted the computer(without the cd) and the OS boots and runs fine.
Does this mean that i still need to download the video driver update?

---

### Post by BLTicklemonster on 2007-06-14
> **TeraDyne said:**
> "User Friendly" doesn't mean perfect. You can have this sort of problem upgrading a piece of software in Windows as well.

Anyway, do as they said. Back up and install using a burned CD. I myself didn't have a problem, so I can't help too much beyond that advice.

"User Friendly" should mean a user can use it, though. I agree. Ubuntu drives me crazy a lot, but I love it. Don't get me started on getting a folder to share to a windows machine without having to enter a password. "User Friendly" is nothing I think anyone will ever use to describe networking in linux.

---

### Post by ITdrummer on 2007-06-15
Well i originally started this thread because i was having multiple issues installing Ubuntu.  Due to the advice and suggestions of users in this forum, I am running the current version of Ubuntu with no problems.  Thanks for everyones help!

---

### Post by wpshooter on 2007-06-15
Glad you got it running.

Now as you gain more knowledge, please help out by passing some of it along by helping other beginners.

Since you are working on becoming a "computer PRO", you should eat this stuff up with a spoon.

I wish I could roll the clock back a few years, I would be joining you on your quest, but too much water under this bridge now for that to happen.

Good luck.

---

