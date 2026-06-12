---
title: "Screwed Again!"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by pappapump on 2007-05-27
This new OS is steadily driving me crazy with all the re-installs.
I try using frostwire and for a few days all is well then bam it goes haywire and wont open.
I try Azureus and all is well with that too then bam it's useless too.
I don't know diddley about Ubuntu but one thing i CAN say is that i'm sick to death of having to 
reinstall it over and over just to get my fav programs to work.
In all other respects the os is fun and easy to use but there is no easy way to fix broken apps.
If my new program is dead, I can't just uninstall it and reinstall it and make it work.
I even tried the orphan finder and used that with 0 success.
I tried the synaptic manager and tried fixing things with that and no amount of install uninstall or reinstall helps.
So I tried the console using directions on the webpage and still nothing.
As of the date of this letter I have had to remove and reinstall Ubuntu 7 times just to get the basics to work.
By basics i mean Seamonkey, azureus and frostwire.
The bittorrent program included is so basic in functionality that it's close to useless.
File association from the browser (FireFox) is just about impossible.
If I find a torrent I like I have to copy the url, start the torrent program and manually paste it in.
The biggest pain in the *** is that I'm STILL windows dependant if I want to play any of my favorite games.
That I can deal with just as long as my Ubuntu is reliable and I can stay in that the majority of the time.
All of the common things you would expect to find in windows is there and then some, but User Friendly isn't part 
of the package when it comes to trouble with apps.
My windows Azureus has bugged out on me before but was easy to fix.
Frostwire is similar to limewire and with limewire I have had next to no problems.
Then the problem I have with this root password BS is really pissing me off.
It's my PC My chosen programs and all of the hardware is mine.
I really dont need some lameass program telling me im limited access to certain folders on the Native ubuntu hard drive.
I DONT want to be restricted access to my root drive, I can see the reason for not being able to alter base prog files but when I try to do a backup, 
the default backup folder is locked out so I am forced to use one on the desktop to save a backup in.
Windows XP has a restore option which starts with the system and I would hope that something like that is available with Ubuntu.
Just trying to use the simple backup is confusing, then theres the other backup apps which aren't much easier.
Another problem I have had is with beryl and my Nvidia card.
The linux community as a whole seems to deem hi end Graphics and Audio hardware as a waste.
I have read many articles stating that you really dont need to use all that cool stuff.
Maybe if I was a open source geek who does nothing but write code, manipulate Linux apps and never try to have fun with my os i'd be fine.
But I'm a windows and DOS geek who has no clue about linux, and basically I'm as virginal with this as the newest noob.
I pretty much have to trash years of training from dos 2.0 and up and start all over just to find my way around Linux.
Maybe if I didn't mix my own music, play online games or otherwise use my PC as an entertainment system as well as a PC there wouldn't be a problem.
For an operating system to truly replace Windows it needs to meet todays demands for apps games etc.
In other words it should be able to do what windows does in it's own way.
After all, almost everybody is Linux illiterate.
Do I want to screw with a terminal window and learn code?
Oh HELL no!
By the time you recieve and reply to this bug letter I will have begun yet again to try to get this Ubuntu to work right.
By then I'll have even more gripes to be sure, but I love this OS so I'll keep trying till It finally does what I want it to.

---

### Post by hyper_ch on 2007-05-27
Wow, that is hard to read... I split it up a bit...

(1) If one app doesn't work or doens't work correctly, you don't have to reinstall the whole system....

(2) You said you used frostwire and azureus... there are a couple of other torrent clients available. I have used so far KTorrent and I'm very happy with it....

(3) Uninstallation is quite simple... at least if you did install it through adept/synaptic/apt-get/aptitude... basically in adpet/synaptic it's unchecking the box of that programm.... in apt-get/aptitude you would enter:
```

sudo apt-get remove PROGRAMM

```

However that will normally not remove the config files created by the programs... for them to also remove use:
```

sudo apt-get --purge remove PROGRAMM

```

(4) What does not work with the file association? For me it all works perfectly well...

(5) Well, games is a pain but that's not the fault of ubuntu... tell that to the game companies that they should also make linux versions....

(6) I tend to say Ubuntu is more user friendly than Windows... you are just unfamiliar with Ubuntu and expect all things to be the same... have a read here:  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

(7) What problem do you have with root password? As said before, Linux is different than Windows and Linux is a true multi-user system... while in Windows you normally login as administrator in order to actually be able to use the system, this is not the case in Linux... this add a great deal of security... in windows if you catch a virus it will have then admin rights... in linux it has not... it will first need to get those... as soon as you do something from the gui that requires root priviledges you will be prompted to enter the password... in windows, if you are a limited user, you are required to log-off as that user, login as administrator... do that stuff... logout, log backin as limited user... that's way too complicated...

(8) You can change the ownership of that backup folder... that's up to you... however if it is associated with a program and stuff... you may want first to consider that intensly...

(9) Linux is not windows... what do you need a restore option for?

(10) I have written my own backup solution with about 40 lines of code... most of them just assigning paths and variables... I haven't seen any simpler method on windows...

(11) Well, you don't say what problems you have with Beryl/nVidia... however nVidia is quite good supported.....

(12) Linux has everything to replace windows... the only thing is games... but I don't play games... and at work in companies you aren't supposed to play games either but be productive...

(13) I can do what windows does and in many ways it does it better..

(14) You may not want to use terminal but it's also an efficient way... you forgot, Windows Vista Server has now this super-cool-new-power-terminal-feature.... after all that GUI doctrine M$ also reverts to a terminal? Ask yourself why...

---

### Post by seetho on 2007-05-27
> For an operating system to truly replace Windows it needs to meet todays demands for apps games etc.
In other words it should be able to do what windows does in it's own way.


Ubuntu (Linux) is not meant to replace Windows OS.  Just like Mac OSX is not a replacement for Windows (or vice versa).  If you start of using it with the expectation that everything will work in the same way and you get everything exactly the same as before you will be in for a very big disappointment.

Ubuntu (Linux) has it's strength just like any other OSes out there.  Important thing is you choose what serves you the best.  If you find Windows to be useful for most of your needs then you should stick to it.  You can 'play' with Ubuntu to find out what it is capable of.

It took me more than 10 years of 'playing' with Linux and BSD to be get to the point now that I almost never use Windows.  Although there are times that I need to use it - I still keep a PC around that can boot into Windows XP.  I think that just 1 or 2% of the time.

Take your time to learn it and you will find it very rewarding.

Good luck.

---

### Post by dptxp on 2007-05-27
It takes time to get used to new OS and programs.
Linux is still young on desktops but the growth is real fast.

If my kids prefer to boot with Linux (Ubuntu) there must be some charm
in it.

As for as I am concerned, I like the freedom.

I am too looking for replacements for programs as ARES Galaxy, Wavepad. I shall use dual boot till I
get all I want, Ubuntu is set as default.

---

### Post by Celegorm on 2007-05-27
Re-installing the OS is seldom the best way to fix a problem, you might be a little less frustrated if you posted individual problems on the forums, with enough details that people can help you out.

A lot of people have problems with Beryl, myself included. It's not really stable yet. If you get frustrated when it crashes, don't use it.

Try to be patient in learning how to use ubuntu, it's new, so it's not going to come all at once, or necessarily easily. Don't expect it to be the same as windows. It's not.

> Do I want to screw with a terminal window and learn code?
Oh HELL no!
There's no need to learn any code in order to use the command line. Most things can be done without ever touching the command line, but it's very powerful if you take a little time to learn it.

> Maybe if I was a open source geek who does nothing but write code, manipulate Linux apps and never try to have fun with my os i'd be fine.
I'm an open source geek who does nothing but write code and and have **fun** messing with my OS :biggrin: Windows can't even touch the customizability of linux. I'm sorry you've had such a bad experience with it so far, and I've got to admire you a bit for still sticking with it. Once you get more familiar with it and have fixed the most major problems, maybe you will have fun with it too ;)

---

### Post by AAM on 2007-05-27
What can one say to your diatribe? I can't see why you are even trying Ubuntu, not if Windows is as good as you make out. Obviously you don't have Vista yet with its DRM working!

Pappapump , you should be ashamed of yourself. Why don't you ask us about your problems in a calm and even tone, like you are asking for help? My instinctive reaction to your writing is "go back to Windows". The fact that **hyper_ch** took the time to do the work you should have done is a reflection of the help you have available to you here. Don't abuse the service.

To assume that the OS you have just installed 5 minutes ago will be as transparent as "years of training from dos 2.0 and up" on another OS is ridiculous. Just plain ridiculous! Put in the hard yards and learn Linux like you learnt DOS/Windows. Attempt to discover its logic. If you want to run your whole system as root all the time, it's possible but you'd then be ignoring every user's advice in all OSs - which would make us all wrong, and you right? 

Like **hyper_ch**, my Azureus works flawlessly. The ATI and nVidia cards on the 7 computers at home all work. Never heard of Frostwire though.

Sincve you are on the learning curve, my suggestion is to take one problem at a time in the following order:
1.a. calm down and get rid of the aggro
1.b. get a notepad and write down what you are doing
1.c. look at some Ubuntu books for help in using Linux (if you were good on DOS, lots of this will come back to you quickly then) - look here - [http://ubuntuforums.org/showthread.php?t=451725&highlight=ubuntu+books](http://ubuntuforums.org/showthread.php?t=451725&highlight=ubuntu+books)
2. get the video card working first (with nVidia this should not be hard)
3. use Synaptic Package manager (or the CLI command 'sudo apt-get install azureus') to install Azureus and get it working.
4. then install Frostwire from a repository or DEB file and trouble shoot it.

---

### Post by TheWizzard on 2007-05-27
to the op:
1) please read [http://ubuntuforums.org/showthread.php?t=58017](http://ubuntuforums.org/showthread.php?t=58017)
2) stop whining. if you don't want to learn, use windows. if you want to learn, then open your mind for a completely **different** OS and ask for help if you're in trouble. people in the forums are willing to help!

---

### Post by STREETURCHINE on 2007-05-27
something is a bit fishy here,you have had all these installs ,and all these problems but you have not once asked for help.
it seems strange does it not.
all your troubles a fixable but to me you seem like you may just be a troll.(if not prove me wrong)
ask about your problems one at a time and in a coherant manner ,some one will help they always do

i must have reinstalled 15 times when i first started to learn about ubuntu linux,mostly my fault but i asked questions and learnt from my mistakes and from what people told me,i have been using ubuntu for about 6-8 months and no reinstalls for the last 5 i reckon.

so if you want to learn linux stop whinning and get on with it if not use windows no one is forcing you to use ubuntu.

---

### Post by moredhel on 2007-05-27
Responding to trolls isn't helpful.

---

### Post by mlentink on 2007-05-27
> **pappapump said:**
> This new OS is steadily driving me crazy with all the re-installs.

This baffles me. I using Ubuntu since just before Dapper. In just a little over a year I've upgraded the machine I'm typing this on to Dapper, to Edgy and recently to Feisty without a hitch. I have ***never*** had to reinstall the operating system

> **pappapump said:**
>  don't know diddley about Ubuntu but one thing i CAN say is that i'm sick to death of having to 
reinstall it over and over just to get my fav programs to work. 
I don't claim to be an expert, but it seems to me that if an application doesn't work, you start by checking why it doesn't, and then perhaps reilnstalling the* application* (not the OS). Re-installing the OS seems to me to be like replacing your car because you can;t find out why your windshield-wipers won't work
> **pappapump said:**
> If my new program is dead, I can't just uninstall it and reinstall it and make it work. 
Why not? Unchecking a box doesn't seem all that difficult to me. Pappapump, uninstalling software is one of the things that are a whole lot* easier* in Ubuntu then they are in Windows
> **pappapump said:**
> I tried the synaptic manager and tried fixing things with that and no amount of install uninstall or reinstall helps.
What error messages did you get? What did you try and did not work?
> **pappapump said:**
> As of the date of this letter I have had to remove and reinstall Ubuntu 7 times just to get the basics to work.
By basics i mean Seamonkey, azureus and frostwire.
Obviously, people could differ in what they consider 'basic' I never use any of these programs, but then I don't download an awful lot.> **pappapump said:**
> The biggest pain in the *** is that I'm STILL windows dependant if I want to play any of my favorite games. True. Windows is, at present, a better OS for Games because more games are made for it. For many other things, however...
> **pappapump said:**
> Then the problem I have with this root password BS is really pissing me off.
It's my PC My chosen programs and all of the hardware is mine.
Sure. That's what you think. Unfortunately there are those who think otherwise. Unix/Linux was set up with that in mind, Windows wasn't. You may think that everything in your house is your property, and yours to do with as you see fit, but nevertheless you lock the doors and close your windows, don't you? Windows let&#347; you lock your front door, giving you a false sense of security, and at the same time leaves many, many backdoors open. 
> **pappapump said:**
> I really dont need some lameass program telling me im limited access to certain folders on the Native ubuntu hard drive. Better stay away from Vista, then. ;-)> **pappapump said:**
> 
Windows XP has a restore option which starts with the system and I would hope that something like that is available with Ubuntu. So it does. Unfortunately, I've had to use it a number of times. Did it ever occur to you why that options is even in there?> **pappapump said:**
> 
Another problem I have had is with beryl and my Nvidia card.
The linux community as a whole seems to deem hi end Graphics and Audio hardware as a waste.
I have read many articles stating that you really dont need to use all that cool stuff.
Pappapump, that simply ain't true, and you know it. If you&#341;e in to eye-candy, Linux can give you everything that&#347; in Vista or Tiger and then some. Check it out.> **pappapump said:**
> 
But I'm a windows and DOS geek who has no clue about linux, and basically I'm as virginal with this as the newest noob.
I pretty much have to trash years of training from dos 2.0 and up and start all over just to find my way around Linux.
I'm starting to think that this is where your main problem is. You thought you knew all there is to know about computers.
> **pappapump said:**
> !
By the time you recieve and reply to this bug letter I will have begun yet again to try to get this Ubuntu to work right.
By then I'll have even more gripes to be sure, but I love this OS so I'll keep trying till It finally does what I want it to.
I know Ubuntu does what I want it to do, does it reliably, and does it with far fewer resources than XP needs to do the exact same thing.

---

### Post by Drakkor on 2007-05-27
I have a "system restore" function, it's called Acronis True Image, it will make a perfect backup of your whole Ubuntu system, and in case of catastrophic failure, no need to re-installed anything, just restore the image,and you're  usually back up like nothing happenned in 10 minutes !! :D

---

### Post by wataboutbob on 2007-05-27
> **Drakkor said:**
> I have a "system restore" function, it's called Acronis True Image, it will make a perfect backup of your whole Ubuntu system, and in case of catastrophic failure, no need to re-installed anything, just restore the image,and you're  usually back up like nothing happenned in 10 minutes !! :D

hmm... 700 euros for the Arconis software. Seeing how my company isn't going to provide for it, I guess it'll have to be good old Partimage for me.

---

### Post by Drakkor on 2007-05-27
I briefly looked into partimage,but correct me if I'm wrong, that will backup partitions,but not the complete OS,with grub and all ?
BTW, if your company doesn't like a lot of downtime, then ATI is the way to go !  (Not a paid shill for the company,and hold  no 
stocks , or intrests,thereof,lol).  I just love their software.

---

### Post by wataboutbob on 2007-05-27
you're correct. Partimage will make backups of partitions but not of the MBR or the entire HDD. As far as ATI is concerned, I'll pass it on to the resident tech guru. Thanks for the tip.

---

### Post by Drakkor on 2007-05-27
I dual boot Ubuntu/XP, and have each on a separate hdds. and when I make a backup image , I image the whole Ubuntu drive completely. Sure saves a lot of time to just restore the whole working environment,rather than having to start at square 1 again !  :p

---

### Post by pappapump on 2007-05-27
Troll? I had a feeling I'd get flamed for posting and you wonder why you haven't seen me post before? I was smart enough to read what happens to others who dare to air their spleen in frustration.
As I expected I was told to go back to windows. Blah Blah Blah.
To those of you who have no patience with noobs lie me, may I suggest that you keep your responses to yourself.
I have been working with, repairing and upgrading PC's for years and still own a computer shop.
For that SAME length of time I have utterly detested and despised Microsoft and all it stands for.
In the meantime I have been steadily been looking for an alternate OS to replace windows with.
As a result I became quite proficient with Apple/Mac as well but that single mouse button drove me nuts. I have installed and played with every Linux distro that came out and was most impressed with Mandrake for sheer look appeal but still ran into loads of problems.
I'm a huge fan of ubuntu for a number of reasons, but no amount of repair gets my failed apps
working again.
(1) If one app doesn't work or doens't work correctly, you don't have to reinstall the whole system....
[B][COLOR="Navy"]Ok, like I said I have tried everything to get the apps up and running again, I read studied and read some more.
Uninstaling with all 3 available methods has yielded 0 results and NO error messages.
The program briefly flashes on then crashes and dissapears.[/COLOR][/B]

(2) You said you used frostwire and azureus... there are a couple of other torrent clients available. I have used so far KTorrent and I'm very happy with it....
[B][COLOR="Navy"]Ktorrent sux wind compared to Azureus and dont work so well in debian for me.
Azureus lets me completely control the torrents behavious easily.[/COLOR][/B]

(3) Uninstallation is quite simple... at least if you did install it through adept/synaptic/apt-get/aptitude... basically in adpet/synaptic it's unchecking the box of that programm.... in apt-get/aptitude you would enter:
Code:
sudo apt-get remove PROGRAMM
However that will normally not remove the config files created by the programs... for them to also remove use:
Code:
sudo apt-get --purge remove PROGRAMM
[B][COLOR="Navy"]Sudo? Ok this looks like a terminal thing, Why not a simple uninstaller that does that for you?
This is the major turnoff for those wanting to make the switch and at some point in the future I want all my new ready to sell PC's to be completely user friendly so that I dont have to spend countless hours with the PC I sold last week on my desk because something went buggy.[/COLOR][/B]

(4) What does not work with the file association? For me it all works perfectly well...
**[COLOR="Navy"]Ok, example, I find a torrent I like and Firefox says how do we handle this file etc, then I have to locate the bittorrent client I use which I can never seem to locate so I have to copy and paste the url in azureus.[/COLOR]**

(5) Well, games is a pain but that's not the fault of ubuntu... tell that to the game companies that they should also make linux versions....
**[COLOR="Navy"]I agree, Microshaft and their direct-x BS has completely polluted the industry so that we are limited to Winblows only for any of the cool graphically intense games I like. Thats about all the use I ever get from windows anyway.[/COLOR]**
(6) I tend to say Ubuntu is more user friendly than Windows... you are just unfamiliar with Ubuntu and expect all things to be the same... have a read here: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[B][COLOR="Navy"]Ubuntu IS more user friendly than windows in almost every way, but the program repair/removal is too problematic. 
Like I said, I LIVE in ubuntu now and am absolutely Giddy with delight.
If I had to reinstall this OS every day, frustration or not I'd STILL use it over Microshaft products.[/COLOR][/B]
(7) What problem do you have with root password? As said before, Linux is different than Windows and Linux is a true multi-user system... while in Windows you normally login as administrator in order to actually be able to use the system, this is not the case in Linux... this add a great deal of security... in windows if you catch a virus it will have then admin rights... in linux it has not... it will first need to get those... as soon as you do something from the gui that requires root priviledges you will be prompted to enter the password... in windows, if you are a limited user, you are required to log-off as that user, login as administrator... do that stuff... logout, log backin as limited user... that's way too complicated...
**[COLOR="Navy"]This problem arose with simple backup and restore where the default folder was in a directory that wouldn't allow me access because I didnt have root priveledges.[/COLOR]**
( You can change the ownership of that backup folder... that's up to you... however if it is associated with a program and stuff... you may want first to consider that intensly...
(9) Linux is not windows... what do you need a restore option for?
[B][COLOR="Navy"]The million dollar QUESTION! We ALL need a restore option if our apps fail!
Why wouldn't we? No, linux isn't windows, but at least with windows you can go back to when your system had no problems and figure out what went wrong with that last install.
How can you not see the need for a restore option?[/COLOR][/B]
(10) I have written my own backup solution with about 40 lines of code... most of them just assigning paths and variables... I haven't seen any simpler method on windows...
[B][COLOR="Navy"]You havent? Then you've been away from windows a real long time.
The basic backup bundled with windows covers it all with a single floppy.
Write 40 lines of code? Why would i want to become a programmer?
I didnt get an OS so that I could be a programmer, I got it so I could have fun with my PC.
I'm really glad that some of you think that the essence of a PC is in the typing of code and creation of programs, without you Linux wouldn't have survived at all.
However, for Linux to kick Microshafts but and make that megalomaniacal empire fall like it should have done years ago, linux or some other OS needs to be as good or better than Winblows. No newbie to PC's wants to have to learn code to get something as basic and simple as backup to work, they want to click and go.[/COLOR][/B]
(11) Well, you don't say what problems you have with Beryl/nVidia... however nVidia is quite good supported.....
**[COLOR="Navy"]Quite simple, I use the Nvidia restricted driver so my screen isn't so slow to refresh and all is well till I use beryl, so I stopped using it.[/COLOR]**
(12) Linux has everything to replace windows... the only thing is games... but I don't play games... and at work in companies you aren't supposed to play games either but be productive...
[B][COLOR="Navy"]Ok that made no sense, sounds like you're chiding me for wanting to play games with my PC.
Unfortunately for your arguments sake, we don't all use our PC's at work, and if you never played a game with a PC then it's your loss, and a big loss it is. No console game will ever be as good as a PC on graphics OR sound, not to mention controllability.[/COLOR][/B]
(13) I can do what windows does and in many ways it does it better..
[COLOR="DarkRed"]**Absolutely NO argument on that point.**[/COLOR]
(14) You may not want to use terminal but it's also an efficient way... you forgot, Windows Vista Server has now this super-cool-new-power-terminal-feature.... after all that GUI doctrine M$ also reverts to a terminal? Ask yourself why...
[B][COLOR="Navy"]Yet the common user never has to even see it, and it's the day to day consumer that Microshaft appeals to isn't it? I don't have to ask why since the programs are usually written in VB and terminal is usually invisible during install or removal.
Oh and BTW VISTA is why Microshaft is no longer an option for me.
In fact VISTA is so bad that people are LOOKING In Linux's direction NOW!
Besides you are referring to an OS I will never use, VISTA Server?
Why in the world would I EVER want to run a server?
No I didn't forget, I simply have no use for a server, and neither will most of the PC owners of America, and WE are the prime market today.[/COLOR][/B]
__________________

---

### Post by Celegorm on 2007-05-27
I think getting flamed has a bit more to do with your attitude than expressing your dislike of problems. You also seem to be allergic to the command line. Are you refusing to use it on principle or something? What is user-unfriendly about copy-and-pasting a command verbatim from a tutorial or someone's advice? And I'm curious, which other distros did you try besides mandrake, and what sort of problems did you have with them?

> Ok, like I said I have tried everything to get the apps up and running again, I read studied and read some more.
Uninstaling with all 3 available methods has yielded 0 results and NO error messages.
The program briefly flashes on then crashes and dissapears.

Exactly what version of which programs are you using? Every time you run them they just crash?
> This problem arose with simple backup and restore where the default folder was in a directory that wouldn't allow me access because I didnt have root priveledges.
Did you try changing which folder it backs up to? Or possibly using sudo (or gksudo for graphical programs) to run it?
> The million dollar QUESTION! We ALL need a restore option if our apps fail!
Why wouldn't we? No, linux isn't windows, but at least with windows you can go back to when your system had no problems and figure out what went wrong with that last install.
How can you not see the need for a restore option?
Personally I'd like an option to fix an installation on the LiveCD (there may be a way to do it, but I haven't found it) Would have come in handy that one time I wiped my MBR while trying to install a second OS.
>  all is well till I use beryl, so I stopped using it.
What happens exactly when you use beryl?
> Oh and BTW VISTA is why Microshaft is no longer an option for me.
If you're having so many problems with linux, you could always look into other free operating systems, like BSD. Here's a whole list of different [free operating systems]("http://www.freeos.com/download.php")

edit- on second thought, sorry i bumped your thread, people still seem to be reacting badly to the first post :(

---

### Post by TheWizzard on 2007-05-27
what's your problem? few comments:
- yes, you do behave like a bad mannered troll
- no, solving problems in linux with windows reflexes doesn't help a bit
- wrong, program management is much easier in linux. as long as you solve problems the linux way
- no, there's no restore option in linux because it's not needed. you can always repair your system easily. remeber: linux is not windows
- please go back to windows

cheers


ps. PC owners of America are NOT the prime market today.

---

### Post by AAM on 2007-05-27
1. solve your install/uninstall blues, use the simple software provided - USE SYNAPTIC PACKAGE MANAGER FOR EVERYTHING
2. solve your back-up issue - USE NAUTILUS IN *'SUDO'* MODE (GET THE SCRIPT INSTALLED FROM **AUTOMATIX)** TO CHANGE THE DIRECTORY PERMISSIONS
3. politely ASK THE COMMUNITY HOW TO ADD FILE ASSOCIATIONS IN FIREFOX - specifically bittorrent in **Azureus**
4. stop whinging about the OS you think is much better. NONE ARE PERFECT, BUT YOU HAVE MADE THE CHOICE. I'D LIKE TO HELP YOU BUT I (AND WE) ARE NOT INTERESTED IN YOUR RANTS ANYMORE.
5. tell me where you sell computers - CAUSE I WON'T GET ONE FROM YOU, YOU SEEM TO HAVE NO PEOPLE SKILLS AND YOU APPEAR NOT TO LISTEN.
6. take the specific advice offered - GO AND ADDRESS THE PROBLEMS INDIVIDUALLY, **ASK** FOR HELP NICELY (that means writing questions that start with "Can anyone please help me with the problem of gaining access to a directory that only lets root in?") AND STOP ACTING LIKE A 'TROLL' AND WASTING PEOPLE'S TIME (you are obviously not a troll, but stop impersonating one).

---

### Post by southernman on 2007-05-27
A computer and it's operating system are only as good as the operator... period!

What kind of response did you expect to get, coming in here and basically flaming the entire linux and open source community? You didn't really think people would take kindly to it... did you?

Go to a M$ forum and flame their OS. Bet you get some of the same responses... some gentle and some not.

I'm guilty of posting on forums with the description of a problem at hand, providing as much detail as possible, and asking if someone explain it to me like I'm a 2 year old... not acting like one!

If you don't want to play in ubuntu's sand box... nicely, then don't play atall! But for gripes sake, don't stomp your feet on your way out.

If you do want to play, then by all means read the forum guidelines and play fair.

---

### Post by pappapump on 2007-05-27
> **TheWizzard said:**
> what's your problem? few comments:
- yes, you do behave like a bad mannered troll
- no, solving problems in linux with windows reflexes doesn't help a bit
- wrong, program management is much easier in linux. as long as you solve problems the linux way
- no, there's no restore option in linux because it's not needed. you can always repair your system easily. remeber: linux is not windows
- please go back to windows
cheers
ps. PC owners of America are NOT the prime market today.

If you believe that wizz then you're completely lost, they are the only real market that matters.
Or are you one of those that thinks that big business is the only pc customer available?
No I don't behave like a bad mannered troll, this post is my error report sent to the dev team.
Expect some frustration with any linux distro especially with newbs, it happens.
People like you with your attitude contribute a whole lot to the problem not the solution.
Right, program management is much easier for the Linux educated than the windows educated in Ubuntu.
You can always repair your system easily? How? With what?
And the trite and true to your ego reply will always be (please go back to windows).
After all you ARE the linux elite aren't you?
Can't fix problems in linux with windows skills? Probably so, but the similarities are there so the responses will be the same, click it to fix it.
Sure I object to having to type in a terminal, more because it means that the base functionality in that little window is not only completely unfamiliar to me but to ANY new user of Linux today.
Am I mistaken or was Ubuntu designed to be for the masses and also designed to be as user friendly as possible?
Will you also be as crass and offensive to the new Dell system owners when they come here with their Ubuntu problems and frustrations?
What Dell has done with these new PC's is open a whole new way of thinking to people who have never even heard of Ubuntu.
Before this all they had in the way of a Linux ready PC was the lame Lindows boxes sold by Walmart.
Freespire and Linspire aren't much better since they limit a load of Deb based apps from running and pretty much force you to use their own software, a lot of which isn't free.
People like you Wizz pretty much stand in the way of progress instead of helping it along, and your response will always come back to (Go back to windows).
Why? Because you simply have no answers to give.
In the mean time you toss a rock in the road when a user has a complaint and Heaven forbid that you even consider allaying any fears or concerns a newbie has with this new os, you just wont be bothered will you?
I apologized for my earlier comments of frustration since I was worried that they may tend to cause other newbs to stop trying.
As it stands, Ubuntu is the freshest and best alternative to Windows I have ever used and I KNOW that it will only get better over time.
Having been at the forefront of the Beos movement and also a contributor to the initial work with a tidy cash outlay, many years ago I realized that making a nice competitive OS which is as good as or better than Windows is not only difficult but also a battle which Microsoft will gladly fight.
Go back to Windows? 
Not an option!
You first.

---

### Post by RomeReactor on 2007-05-27
Hi. pappapump, I can only imagine the level of frustration you are experiencing now, but that is no reason to just unleash it on those that are only trying to help you; if you could please organize the issues you are having and post them here in as much detail as you can, one by one, I'm sure we'll be glad to help you. If, on the other hand, you only want to vent your dissatisfaction, please do so on an [appropriate]("http://ubuntuforums.org/forumdisplay.php?f=11") [section]("http://ubuntuforums.org/forumdisplay.php?f=121") of these forums.

---

### Post by Drakkor on 2007-05-27
Yep, your posts actually make my eyes  burn !! Seems like you've bottled it all up, and headed to bust a blood vessel in your head ! ;)
Slow down and breathe.

---

### Post by pappapump on 2007-05-27
My only frustration post is here, there are no more.
Feisty is reinstalled and I will try yet again.
I have spend the last month and a half with very little rest, working with Ubuntu.
If you read the initial post in it's entirety you will see it's definitely NOT a flame to ubuntu, just a tired old man venting his spleen.
Sure I resent the fact that all of my microsoft training is essentially useless now.
Sure this is all new and a bit tuff to learn, but looking back, MS was way harder.
The original post is simply a culmination of all my frustration built up from the last month.
Today, I am wiser than yesterday simply because the first reply to my post answered a few questions.
There is no real manual for this OS but the support is a lot more in depth than a book.
I'll get there, no doubt, complete with a few new gray hairs.
> **Drakkor said:**
> Yep, your posts actually make my eyes  burn !! Seems like you've bottled it all up, and headed to bust a blood vessel in your head ! ;)
Slow down and breathe.
Roger that, I'm breathing again.
Remember that my frustration isn't at My beloved, cherished and adored Ubuntu.
It's all directed at me, I used to be the guy with all the answers lmao!
Now I'm just another clueless newbie!
Now that I look at it, thats a bit liberating.

---

### Post by Drakkor on 2007-05-27
I just re-read your original post, and probably the way to have went is dual boot, XP/Ubuntu to ease the total 
culture shock to Ubuntu and Linux,  I still use XP , though very rarely now, having been with Ubuntu since
Dapper/June 06 but there are some programs that still have value to me on XP. Another observation is the
Beryl thing, you realize it is beta and has been know to cause all kinds of issues , I had it for awhile, and it's
some nice eye-candy for a short time, but it does get old fairly quick !  ;)

---

### Post by Pizzarth on 2007-05-27
lol I felt the same exact way when I started here. My main problem was the x server, but that fixed itself( wait no it didn't, I installed ubuntustudio, and when that didn't work, I reinstalled it 8 times or so) :P but that's ok

> It took me more than 10 years of 'playing' with Linux and BSD to be get to the point now that I almost never use Windows. Although there are times that I need to use it - I still keep a PC around that can boot into Windows XP. I think that just 1 or 2% of the time.

from the first page. My response: really? it took me about 2 minutes, I go on windows only for photoshop. Sorry, gimp just doesn't cut it for me.

back to pappapump, yea you're not a troll. I can't imagine why your install kept messing up that many times, and consistantly too.

as for visual uninstaller, synaptic. don't wanna use command line? sure, don't have to. Well unless your x-server dies, but it seems like it hasn't yet. 

Linux is a different kind of beat, but doesn't take too long to get used to if you're open to it. Thinking about it, almost everybody would agree it's much more intuitive and organized than windows is, but until then the windowsed propaganda and conquest stops them for seeing it like that, and just as "different". Glad to see that you've understood that. yes I did just make up the word windowsed. 

I know how it feels to be the guy with the answers who doesn't anymore, but I like it this way better, and am learning so much faster than I was about windows.

I consider myself linux-only(minus photoshop, which I havent gotten wine to take yet) and vehemently oppose windows, but I barely know c++, can get around but not do anything really serious or worthwile with the shell, and I'm not currently a part of any huge open-source projects. don't have to be.

this forums is a great place, I actually just hang out here. helping where I can, and actually... [whisper] learning...[/whisper] when I can't. good luck

---

### Post by STREETURCHINE on 2007-05-27
ah good now we seem to be getting somewhere.
the best way to learn is to ask questions,then ask them again till you  have it set in your brain.

and space your sentences a bit makes it easier to read

---

### Post by diatribe on 2007-05-27
The thing about ubuntu is that while it is one of the easier-to-use distros of linux, it still requires ar least a slightly moderate knowledge of computers. There are people that can barely use windows trying to migrate to linux, and then they say that the OS is the problem.  Sometimes it is the user who makes a program diffcult to use, and not the program itself.  Readng back this is kind of rude; but I've read enough of these types of posts that I am kind of sick of seeing them ;p

---

### Post by Happy_Man on 2007-05-27
Glad to see you've calmed down, buddy. Now then, what's going on with that install? What are your problems? Just list 'em off, one by one. The answers will come, as if by magic. Trust me. ;)

---

### Post by pappapump on 2007-05-27
I just did a reinstall in like what 25 minits?
Pffft! cant do THAT with winders!
I spose it all boils down to me adopting a new way of thinking.
Same thing I did with mac os's, and you know, I tend to experiment and try new things.
So crashing shouldn't be such a surprise to me.

Ok im adding a space here
Alright I have this question, wth is sudo? What does it mean?
I have no complaint about using the term window, I eventually need to learn it but the abbreviations mean zip to me.

Now the problems with Azureus and Frostwire quite simply boiled down to Java errors.
Apparently the appropriate java and dependencies NEEd to install with the apps or at least get checked during install.

Fortunately the accessible Azureus install loads from the add remove panel now when it didn't before (Let me check that real quik) yep there it is.
OMG that was fast. Installed! Anyway, on to limewire vs frostwire.
Frostwire just went lame in comparison, the new limewire dont crash like frostwire does so now I'm set.

Ok now I took a look at the available peer 2 peer apps and wow I need to read more, Tv on my pc in a stream format? This just blows me away.

No more Nero, MS Office, or any of those other expensive lame apps like power DVD, adaptec, toast etc. If for no other reason, the bundled apps alone would be all I ever needed to switch and never go back.

Basically what I'm learning from all this input is that to truly make the switch I need to be immersed in Ubuntu completely, and truth be told thats what I'm gonna do since I just can't tolerate any time spent in windows.

I deleted my XP install and went back to Win2K since all the bundled MS spyware was so hard to get rid of. I lost a lot of software when i did that including 3 of my new novels, but I have a backup of those stored on a CD minus about 20 pages.
Ok now to the questions.

What is best to run some of the windows based games with besides wine which absolutely wont work with any of my mmorpg's?
If I had the answer to that one question then I could simply delete Windows and be carefree forever.

Question 2, is there a Terminal instruction manual of any kind for dummies?

Question #3 I tried the new mozilla SeaMonkey and absolutely LOVE it, but I cant get it to run unless I make a shortcut from the directory to my desktop, and even then it brings up a dialogue window and runs perfectly after that. Problem is that I get no Icon and it wont place the shortcut in my Internet Apps tab.

Question #4 Is there a total backup program which will save this install of Ubuntu so I don't have to go back and reinstall all my fav apps all over again?

---

### Post by Pizzarth on 2007-05-27
> Alright I have this question, wth is sudo? What does it mean?
I have no complaint about using the term window, I eventually need to learn it but the abbreviations mean zip to me.

sudo is what you use to temporarily act as root. meaning to temporarily have all permissions, giving you access to well... everything. you can see how obviously dangerous that is.

the abbreviations aren't too hard to learn, there's 12 or so basic ones, pretty much all you need to get around. yay google.

> Now the problems with Azureus and Frostwire quite simply boiled down to Java errors.
Apparently the appropriate java and dependencies NEEd to install with the apps or at least get checked during install.

synaptic took care of it for me, don't know, sorry

> Ok now I took a look at the available peer 2 peer apps and wow I need to read more, Tv on my pc in a stream format? This just blows me away.

that might just blow me away too, what's the program name?!

> No more Nero, MS Office, or any of those other expensive lame apps like power DVD, adaptec, toast etc. If for no other reason, the bundled apps alone would be all I ever needed to switch and never go back.

yep :) same here. K3b, openoffice. 

> Basically what I'm learning from all this input is that to truly make the switch I need to be immersed in Ubuntu completely, and truth be told thats what I'm gonna do since I just can't tolerate any time spent in windows.

I deleted my XP install and went back to Win2K since all the bundled MS spyware was so hard to get rid of. I lost a lot of software when i did that including 3 of my new novels, but I have a backup of those stored on a CD minus about 20 pages.

bold move, but not a bad one. good luck, and you write novels? what kinds


EDIT: UPDATED QUESTIONS:
> Ok now to the questions.

What is best to run some of the windows based games with besides wine which absolutely wont work with any of my mmorpg's?
If I had the answer to that one question then I could simply delete Windows and be carefree forever.

Question 2, is there a Terminal instruction manual of any kind for dummies?

Question #3 I tried the new mozilla SeaMonkey and absolutely LOVE it, but I cant get it to run unless I make a shortcut from the directory to my desktop, and even then it brings up a dialogue window and runs perfectly after that. Problem is that I get no Icon and it wont place the shortcut in my Internet Apps tab.

Question #4 Is there a total backup program which will save this install of Ubuntu so I don't have to go back and reinstall all my fav apps all over again?

2) the terminal uses bash(bourne-again shell). in wikipedia or google you'll find a list and tutorials of the basics.
3) right click-> edit menus. after you click on the internet tab, click on new item, and add the command/location.
4) yes, but it's not hard to reinstall so I don't really find them worth it. I'd just manually copy over the config files. or when you get ok at bash, write a script to do it everyday. not too hard

---

### Post by Happy_Man on 2007-05-27
"sudo" means "super user do." Basically, it's a safety precaution. In most Linux distros, there is a root user, who has unlimited access to the computer. They can do whatever they want, whenever they want. Like Admins in Windows. Ubuntu locks this root account by default, and instead uses sudo for things that would normally require superuser. 

Glad you got your azureus issues resolved. The same thing happened to me as a newb, don't worry. :razz:

And you're damn right, you can't install Windows over again in 25 mins. That is an honor for Linux alone. Woohoo!

---

### Post by southernman on 2007-05-27
> **pappapump said:**
> 
Alright I have this question, wth is sudo? What does it mean?
It gives you root privileges. As you've noticed perhaps, Ubuntu doesn't setup a root account by design... it's a security thing.

If your in a terminal, I think it will keep you as root (sudo) for up to 15 minutes... unless your constantly hacking at the terminal. If you (as root) set idle for longer than that time frame, you'll be denied doing root things until you "sudo insert command here" again. (That may not be totally correct, but it's my limited understanding of it at this point)

When you do a sudo command, you'll be prompted for the password. By default, it's the same password as the user account setup during installation.


Glad to see some normal color coming back into your face now. ;)

---

### Post by Pizzarth on 2007-05-27
yep, it's 15 minutes, you can also do sudo -s to log-in to root, but only in terminal as far as I know


answers to the other questions above

---

### Post by Happy_Man on 2007-05-27
> **southernman said:**
> Glad to see some normal color coming back into your face now. ;)

heh, yeah. I was imagining you as all red-faced and irate, bashing at your keyboard in frustration. Now the red's going away, a bit.

---

### Post by southernman on 2007-05-27
> yep, it's 15 minutesThanks for confirming this and expanding on it.

FWIW, I've deleted my XP install also, earlier this week. The only thing I really needed it for was office. I am trying to get a handle on OOo so that I am not a dependent child of gates any longer. *sighs*

---

### Post by pappapump on 2007-05-27
Questions answered and now I have notes.
My novels are all Sci-fi and adventure types.
When I complete the first one I'll post a link for a pre-read if you like.

Ok now, thats twice someone has said i dont need a backup since repair is so easy.
Can you outline the steps to repair?
I really see that I'm still thinking like a windows geek and just assumed that backup/restore was the preferred way, but if there is an easy way to simply repair instead then id rather do that.

My Ubuntu on an Imac install was a total failure but more on that later, (Sold the Mac).
 That streaming prog is called GnomeCast and there are several others.
Just type peer in the search window on add/remove.

My presentation PC needs some hardware adjustments also since its using edgy to make it a Media Center PC. That can be addressed later, but my hope is that a MCE type setup will also be available on Feisty later on, as is it works quite nicely in edgy minus the ATI tuner which is incompatible.

---

### Post by qamelian on 2007-05-27
> **wataboutbob said:**
> hmm... 700 euros for the Arconis software. Seeing how my company isn't going to provide for it, I guess it'll have to be good old Partimage for me.

Wow, that doesn't sound right. Acronis True Image is only $50 Canadian. I highly doubt that it costs 700 euros which would be, I think, more than ten times as expensive.

---

### Post by southernman on 2007-05-27
> Ok now, thats twice someone has said i dont need a backup since repair is so easy.Regardless of which OS you use... backups are always important. You could do it via the command line, or use a GUI instead. Someone directed another poster the other day to grsync which you can find in the add/remove programs under applications. For more info on it... google it. I am not familar with it or I'd share my thoughts of it.

> Can you outline the steps to repair?Repairing a busted system will be specific to what has gone wrong with it. There isn't one explanation of how to do it, that covers everything... not that I can explain anyhow. Bottom line, it would require using the terminal, or a console.

My suggestion is to keep regular backups either off site or on a seperate hard drive to be safe.

[edited][http://www.opbyte.it/grsync/]("http://www.opbyte.it/grsync/")

---

### Post by pappapump on 2007-05-27
Ok so I added the backup/restore progs and found the tool for enabling me to write to my larger windows ntfs drive, so now basically all i need to do is save the backup there right?

---

### Post by southernman on 2007-05-27
I suppose you could save it to your windows partition. My question for you would be.... Why?

Although you can now read/write to ntfs partitions, it isn't the most reliable thing to use for important files.. such as a ubuntu backup. I've read files can be corrupted, even with the ntfs app

In your ubuntu, did you set up a seperate /home partition? If so, that's where I would put it if there were no other partitions/hdd's you can use... or you don't have webspace/server at a different physical location.

Bare in mind now, I am no expert at this stuff. IT;s why my replies only concern things I am somewhat familar with... others I simply leave alone for the more versed in those areas.

I think [Gparted]("http://gparted.sourceforge.net/") (also available through add/remove or synaptic - which ever your preference is) can shrink/resize partitions if you need to do so. You can install it on the system or download the Livecd which is only 40 something mb).

---

### Post by linfidel on 2007-05-28
Your manner of writing is very combative, and not very conducive to getting positive help; maybe that's what you want, but if not, try making your posts easier to deal with.  One suggestion I'd make is to ask one question per post.  Some people will help with unanswered questions, but if they see your post has replies, they may not bother sifting through it to see if each question was answered - too confusing.

But, I do understand your frustration; I too am an experienced Windows and DOS user from way back, and I've had my share of hard times with Linux in the past.  But it's gotten a lot better, and I've finally learned enough to survive.

One suggestion I'd make is to learn how to organize your files.  Think of your home directory as the same as with Windows "Documents and Settings"/<your login>".  You can then create a "My Documents" folder in your home directory if you want, and "My Pictures", etc.  You have full permission to everything there.  Don't think of restrictions on other files as being a bad thing.  Even in Windows, you don't have full authority if you're not logged in as Administrator, which really should not be done, even if it is your computer.  If you don't have permission to install a program, then a virus can't install itself either.  In fact, if you don't run as Administrator in Windows, you probably can get along without antivirus software.

Next, I'd suggest learning the command line a little.  You really don't need it that much, but it is helpful.  You can use add/remove programs, or the graphical synaptics to install software, but the command line is there to make it easier.  It's much easier to paste one command into a terminal session, than to read directions for what program to open, what menu to choose, then what command to pick, then what options to check, etc.

Using a command line in Linux is easy.  If you don't know anything else, you should know that the tilde is an alias for your home directory.  Entering "cd ~" changes to your home directory.  The up arrow recalls previous commands, even from previous logins.  The tab key will fill in filenames and directories in commands. But unlike DOS, case matters; also, the current directory isn't automatically searched, so sometimes you need to enter "./" in front of a command.

And remember, Linux is not maintained by a company with billions of dollars to spend; it's made up of people who do it for love or glory, not money.  And they may not care whether unappreciative new users like it better than windows. So, don't just bitch about things not working the way you think they should.  Act like you appreciate their efforts, and try to ask questions in a positive way.

---

### Post by seetho on 2007-05-28
> **Pizzarth said:**
> 



from the first page. My response: really? it took me about 2 minutes, I go on windows only for photoshop. Sorry, gimp just doesn't cut it for me.


Hahaha.  It really doesn't help if, like me, you work for companies that make it a policy that only Windows be used.  I actually got my first exposure to Unix on an NCR Tower 24 years ago - those of you here still not sucking on their pacifiers may know what I'm talking about.  Most of that time I used some flavour of Unix, Linux, BSD at home (more of experimenting) and also to setup servers for people who have the wisdom to adopt something other then Windows.  I would not say that Linux is better than Windows or for that matter any OS is better than any other OSes out there.  They were alll made to do a job.  I use what works for the job the best.

It is only the last few years that Linux has matured enough to appeal to the average user - not just the geeks.  However many like papapump will find it frustrating (especially if you're in my age group) to make the move.  I think not because there are problems with Linux but more of the shock of change from something we have been used to for decades.

Personally I choose to use Ubuntu now because of this forum!

---

### Post by linfidel on 2007-05-28
> **pappapump said:**
> Question #3 I tried the new mozilla SeaMonkey and absolutely LOVE it, but I cant get it to run unless I make a shortcut from the directory to my desktop, and even then it brings up a dialogue window and runs perfectly after that. Problem is that I get no Icon and it wont place the shortcut in my Internet Apps tab.How are you installing these programs?  Do you use Synaptics?  I ask because I searched for SeaMonkey, and didn't find much, but there were lots of packages for Thunderbird (main program, tray notification, etc).  If you install it that way, it usually adds it to the menu in the right place.

For terminal help, try (at the terminal prompt) "man bash".  The bash shell is the default, although some people run other shells.  You could also google for "bash shell".  Whether you use a simple xterm or a more elaborate gnome terminal, bash is the shell.  Also, take a look at the file .bashrc in your home directory - it is where you can put aliases, etc.

It's similar to DOS, but not exactly, and with different commands.  Don't make the mistake of thinking it's the same. :)

---

### Post by southernman on 2007-05-28
> **seetho said:**
> 

It is only the last few years that Linux has matured enough to appeal to the average user - not just the geeks.  However many like papapump will find it frustrating (especially if you're in my age group) to make the move.  I think not because there are problems with Linux but more of the shock of change from something we have been used to for decades.

Personally I choose to use Ubuntu now because of this forum!

If I give you my dad's phone number, would you call him and tell him about Ubuntu! Bahahah

Seriously though. He's a veteran of computers for only 6 years or so now... yet still a windows noob!!! I did manage to get him on Ubuntu for a brief period (only because his was toasted and we were waiting on parts to fix it), then it was right back to the hellufied windows world he went.

It's problem after problem with his puter... primarily cause of what he does with it (which is a topic for a different kind of forum all together). 

Anyhow... life goes on!

---

### Post by seetho on 2007-05-28
> **southernman said:**
> If I give you my dad's phone number, would you call him and tell him about Ubuntu! Bahahah

Better yet get him on to this forum.

> It's problem after problem with his puter... primarily cause of what he does with it (which is a topic for a different kind of forum all together).

Trying a dual-boot.  Show him how to use whatever that he's doing with the PC.  In no time you'll find him booting into Ubuntu more and more.  By the way that's what I'm planning to do for my wife's notebook.

---

### Post by southernman on 2007-05-28
> **seetho said:**
> Better yet get him on to this forum.Tried that... he's stubborn



> **seetho said:**
> Trying a dual-boot.  Show him how to use whatever that he's doing with the PC.  In no time you'll find him booting into Ubuntu more and more.  By the way that's what I'm planning to do for my wife's notebook.Same thing... Tried that.

Set it up so that Ubuntu was first in the boot menu. When he powers the machine up now, has one finger waiting to pounce on the down arrow key. rofl at him!

I suppose in due time, all things come to an end, good and bad!

---

### Post by TheWizzard on 2007-05-28
> **pappapump said:**
> If you believe that wizz then you're completely lost, they are the only real market that matters.


actually i tried to tell you the world is larger than just america. nevertheless, ubuntu is not the easiest for people migrating from windows. you may want to try pclinuxos ([http://www.pclinuxos.com/](http://www.pclinuxos.com/)). 


> **pappapump said:**
> 
People like you Wizz pretty much stand in the way of progress instead of helping it along, and your response will always come back to (Go back to windows).
Why? Because you simply have no answers to give.


the tone of you posts were rather unfriendly and you were not really asking questions. you did now and you can see people respond rapidly with answers. 
i can give you some general advice.

1) get rid of windows habits. 
reinstalling a program only helps if a binary is corrupt, which is rarely the situation. quite often problems have to do with settings and these are not altered by reinstalling a program. 
broken systems are often easy to fix. and fixing problems teaches you more than reinstalling the os. 

2) backup both your /home and /etc folders. all system settings are stored in the /etc folder. all user settings are stored in hidden files in the user's home folder. 
it's also good to make a list of installed software. you can do this with this command:
```
dpkg --get-selections | grep -v deinstall > /backup/installed-software.log
```
if you really messed up your system and need to do a reinstallation, you can put everything back in space with this command:
```
sudo dpkg --set-selections < /backup/installed-software.log
```
also: make installation notes. 

3) stop worrying and learn to love the command line. since you're from the dos-days it shouldn't be too hard.
use aptitude to install software because aptitude also removes dependencies when you're removing the software. 
use the history command to see what you did. this becomes handy when tracking down problems. you can save your history to a file with this command: 
```
history > history.log
```
every command has a manual. read the manuals! e.g. ```
man history
``` gives you the manual of the history command. 

4) don't mess around with software that's not in the repo's unless you're familiar with your system. 

5) linux is not windows. accept the difference. 
ubuntu maintenance requires a zen state of mind (just like motorcycle maintenance). this requires time and effort. 

6) make a test user account to try stuff that messes up your account. 

7) here's a good manual:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by hyper_ch on 2007-05-28
Ok, here's what I use to make my backups. All you need to install for using this is a program called rsync. Rsync does synchronize folders and with this script I make complete backups at any time the script runs... as I run it every 6h it will make a full backup of my files every 6h back for 90 days...

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=*****
MYSQLHOST=localhost
MYSQLBACKUPDIR=/mysql_backup
EXCLUDES=/backup/backup_exclude        # File containing exludes
DAYS=90         # After how many days shall the backups be deleted?

# PATH VARIABLES
CP=/bin/cp;
MK=/bin/mkdir;
DATE=/bin/date;
RM=/bin/rm;
GREP=/bin/grep;
MYSQL=/usr/bin/mysql;
MYSQLDUMP=/usr/bin/mysqldump;
RSYNC=/usr/bin/rsync;
TOUCH=/bin/touch;
FIND=/usr/bin/find;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING CURRENT DATE / TIME
$MK $BACKUPDIR/current
$MK $BACKUPDIR/old
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
MKDIR=$BACKUPDIR/old/$NOW/
$MK $MKDIR

# CREATE MYSQL BACKUP
# Remove existing backup dir
$RM -Rf $MYSQLBACKUPDIR

# Create new backup dir
$MK $MYSQLBACKUPDIR

#Dump new files
for i in $(echo 'SHOW DATABASES;' | $MYSQL -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST|$GREP -v '^Database$'); do
  $MYSQLDUMP                                                    \
  -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST                         \
  -Q -c -C --add-drop-table --add-locks --quick --lock-tables   \
  $i > $MYSQLBACKUPDIR/$i.sql;
done;

# RUN RSYNC INTO CURRENT
$RSYNC                                                          \
        -avzp --delete --delete-excluded                        \
        --exclude-from="$EXCLUDES"                              \
        /                                                       \
        /$BACKUPDIR/current ;
# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current

# MAKE HARDLINK COPY
$CP -al $BACKUPDIR/current/* $MKDIR

# REMOVE OLD BACKUPS
for file in "$( $FIND $BACKUPDIR/old/ -maxdepth 1 -type d -mtime +$DAYS )"
do
  $RM -Rf $file
done

exit 0

```

The backup_exclude files contains folder that will not be backupped. It's good to not the backup folder witht he backup process as you may get into an infinite loop

backup_exclude
```

/backup/
/bin/
/boot/
/cdrom/
/dev/
/home/hyper/vmware/
/home/hyper/Exchange/OTR/
/initrd/
/initrd.img
/ionitrd.img.old
/lib/
/lost+found/
/media/
/mnt/
/opt/
/proc/
/sbin/
/srv/
/sys/
/tmp/
/usr/
/var/backups/
/var/cache/
/var/crash/
/var/local/
/var/lock/
/var/opt/
/var/run/
/var/spool/
/var/tmp/

```

Then, of course, a cron entry is needed to run it in a regular interval. I make this by creating a cron.txt file in /root (as sudo of course) with this content:
```

# Backup
0 3,9,15,21 * * * sh /backup/backup.sh

```

That will run backups at 3am, 9am, 3pm, 9pm
Just creating this file doesn't add the cron so you have to execute:
```

sudo crontab cron.txt

```
Now you have setup the cron scheduler... check it by entering:
```

sudo crontab -l

```

That's what I do my backups. I do put them on a seperate drive in my computer and once a day I use (almost) the same script to syncronize my backups on my remote location use rsync over ssh... (just to make sure I also have a backup at another location).

So much for backups.

Regarding re-installation of the system. Most of the software is available in repositories... in online collections where you just can pick and download software. Synaptic and adept are graphical installers for that... apt-get / aptitude are command line installers... since there are comand line installers you can, of course, automate a great deal of the install process (after basic install of the OS.

Your sources file and the keys are stored in /etc/apt/. So what I do is first backup them - when needed... if you do autobackups with the script above you always have backups...

And then you just put the backups back where they be and you use command line installers to download and install the software for you.

My script looks like this:

install.sh
```

#!/bin/bash

################ RESTORE SOURCES.LIST ###############

cp -f backup_files/sources.list /etc/apt/sources.list
cp -f backup_files/secring.gpg /etc/apt/secring.gpg
cp -f backup_files/trustdb.gpg /etc/apt/trustdb.gpg
cp -f backup_files/trusted.gpg /etc/apt/trusted.gpg

#####################################################

# Update the sources and get current versions of isntalled programs
aptitude update
aptitude -y upgrade

# Skype
aptitude -y install skype

# Java
aptitude -y install sun-java6-jre sun-java5-jre

# Postfix
aptitude -y install postfix

#KDE Appz
aptitude -y install kopete konversation konqueror k3b amarok krfb ktorrent
aptitude -y install kftpgrabber kate kontact kdepim-kio-plugins kgpg 
aptitude -y install akregator gdb

# Burn Programs
aptitude -y install gnomebaker
# GnuPGP Key Management
aptitude -y install seahorse file-roller

# aMSN
aptitude -y install amsn

# IRSSI / OpenSSH
aptitude -y install irssi openssh-server

# GnuMP3d
# aptitude -y install gnump3d

# OTR
aptitude -y install python-glade-1.2 python-gtk-1.2

# VmWare
aptitude -y install linux-headers-`uname -r` build-essential xinetd

# Browsers
aptitude -y install kazehakase opera flashplugin-nonfree

# Codecs
aptitude -y install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer

# VLC
aptitude -y install vlc

# Samba
aptitude -y install samba

# Midnight Commander
aptitude -y install mc

# UNRAR
aptitude -y install unrar

# GParted
aptitude -y install gparted

# CheckRootKit
aptitude -y install chkrootkit

# OpenOffice
aptitude -y install openoffice.org openoffice.org-gtk

# ImageMagic
aptitude -y install imagemagick

# Numlock & fonts
aptitude -y install numlockx msttcorefonts

# Timeserver
aptitude -y install ntp ntpdate

# HDD Encryption
aptitude -y install cryptsetup hashalot

# various
aptitude -y install whois phpmyadmin mysql-server mysql-client libmysqlclient15-dev adesklets d4x googleearth htop tracerout

#######################
#######################

# Restore other files

cp -f backup_files/sysinfo /usr/share/apps/konversation/scripts/sysinfo
cp -f backup_files/screenshot /usr/bin/screenshot

```

This will restore my chosen sources.list and according keys and then it will update the system with the current software and then it will start installing all my custom software. I did some grouping of stuff but that is not necessary....
At the end I just restore some modified files again...

So this will install the software and if you have still your /home folder intact (if it's on another partition or by any other means). Your computer is again setup like before.

---

### Post by poppers1957 on 2007-05-28
Hi And Welcome To Linux,

I also was frustrated at first about 4 years ago.   I tried several distros.  I have Fedora Core 6 and Ubuntu 7.04.  Have you tried Fedora Core 6?   Just curious, it has some qualities, and may be less bugged for you.  I can't say I have had the same problems, but I have had some.  The really amazing thing I have found with my distros is the support.  So far every problem I have encountered has been solved with the support of people willing to give their time for free.  To me that is the best part of the Linux adventure.  This is the way the whole world should be.   Like the word means, a person is a person through people.   I don't mention other OS because it is absolutely worthless typing.  I drive a Ford Pick-up, and my wife drives a Pontiac mid size car.   She can't haul a refrigerator, and I can't transport all the kids.  Apples and oranges.  
My suggestion to help would be to take a deep breath, erase your mind of comparing, and it may go smoother.  Keeping the other OS's in mind will hinder you.

---

### Post by poppers1957 on 2007-05-28
Just noticed my info says I am an edgy user.  I have never used that, only Feisty 7.04.  I think computers have some kind of weird stuff happen sometimes that just can't be explained, or can they....................................You think I'm all mixed up here again don't I?  :tongue:

---

### Post by AAM on 2007-05-28
** Question 2, is there a Terminal instruction manual of any kind for dummies?**

A useful book - Linux Pocket Guide, Daniel Barrett (O'Reilly Books), but usually some one on the forum will help with commands. Initially I found that I was just typing the commands verbatim and slowly began to understand what I was asking for.

These latter entries are much more reasonable. I apologise for shouting at you, but you were a screaming mess, and I don't know how to digitally slap someone across the face to get them to stop and listen. Some of my comment stand still, namely

1. solve your install/uninstall blues by using the simple GUI software provided (Synaptic Package manager), when ever I am tempted to install from source, I do another Google search for a DEB file, reconsider whether the software is that important, and then decide that it is not!
2. solve your back-up issue which related to permissions - open the terminal and type **sudo nautilus**, this will start Nautilus in super user mode. Automatix has an installable script to select this from a right click. Find the errant directory, right click and go to properties and then Permissions. Change them and close. Done.
3. I personally don't know how to change file associations in Firefox, although you can do this is GNOME and KDE much more easily. But someone in the forum will know.
6. take the specific advice offered, but as pointed out before address problems individually. As one previous poster intimated, some of the posters will confine themselves to less popular posts. Even if no one helps, post your trials to yourself so that some later gets help.

Do yourself a favour and put WINE off until you are happier with Linux operations. After your first Ubuntu posts, you will be contemplating suicide after WINE. If they put up directions on how to read the error messages and troubleshoot the installation, it would be more helpful. Still I have managed to get IE5, EndNote and Prism working. Haven't tried any games.

Other way to keep W2000 is to run VirtualBox or other virtualisation.

Once again I apologise for reflecting the aggro back, and hope that some of this is helpful.

---

### Post by DougieFresh4U on 2007-05-28
:p

---

### Post by Sethalos on 2007-05-28
You know, being a total Linux noob myself, I have yet to have a problem with anything except for installing my printer (which I still haven't managed to accomplish yet, lol).

Torrents I use Azureus and BitTornado. Both have been working stellar so far. I did have an issue with KTorrent though, my download speeds were less than stellar.

What caught my attention is that these applications seem to be crashing your OS totally. Perhaps it has something to do with something more fundamental with your OS install. Even when a program doesn't work for me, I have yet to have to re-install the entire OS. So perhaps it's something more sinister that is affecting all of your apps. Java install maybe?  

Seth

---

### Post by PhloxyFlowers on 2007-05-28
.[/QUOTE]
so if you want to learn linux stop whining and get on with it if not use windows no one is forcing you to use ubuntu

Holy cow buddy your brutal... . I know his letter was anything but sweet and lilting.. BUT he is frustrated out of his mind. The way you replied to him makes me think you've done the same thing but to someone’s face. Reminds me of my husband when he’s yelling at lousy drivers and he does the exact same thing! They say we detest in others what we detest in ourselves… hmmm 
I just get a kick out of the thread’s heading ,” Absolute help for Newbie’s“. Okay so one of us  shows exasperation and he’s jumped on. Maybe he/she was having a very bad day I myself have been known to have one and  I'm sure have you too!  
It’s feast or famine here come out swinging and a zillion people answer you or asked a questions calmly and no one even acknowledges you! 
Bottom line is we can all be more tolerant and empathize don't criticize ;-) ya know what I mean.

---

### Post by compmodder26 on 2007-05-28
> **DougieFresh4U said:**
> If your looking for 'sympathy', you will find it between 's**t' and 'syphilis' in the dictionary!

Did you just read the first post and decide to flame him, or did you actually read the rest of the thread?  My guess is the former.  Please read the rest of the thread and notice his tone has changed and he is actively discussing his problems.  No more flames please.

---

### Post by jmore9 on 2007-05-28
I have been using linux for several years now ( red hat, suse, mandrake, etc) and have found that someone somewhere has already had the problem that i was having at that time.  I just followed what they had done or not done and managed to resolved them.  All except one.  I have only been able to record with my WINTVPVR-PCI tuner card with errors.  The audio is not sync'd with the video so the mouths are moving but no noise !!  Or the the mouths are not moving and lots and lots of noise.  So i am still using windows to record tv because the people who built my tv tuner card refudes to write drivers for linux.  They still do that today.  

Other than the tv recording i have no use for windows, everything else in in linux.

---

### Post by omkarwagh on 2007-05-28
ya know even after reading the whole discussion one thing is certain when it comes to trouble with applications, windows RULES over ubuntu

(this despite the fact that i havent used windows except for playing warcraft in the past four months)

---

### Post by Pizzarth on 2007-05-28
I think it's pretty funny how this thread has been taken over by people who aren't the OP(original poster) they haven't posted in a while.

---

### Post by mgmiller on 2007-05-28
I just read through this entire thread and all I can say is......SIGH ](*,)

The first thing I thought of with the OP's  Azureus problem was a java issue.
A lot of folks here could have walked him through setting up his java correctly.

How many reinstalls and how much frustration would that have saved him?

Getting out of the Windows mindset of going somewhere else to download an installer for an application is a true paradigm shift for the Ubuntu newbie.  I think it's one of the most foreign concepts to someone coming from Microsoft.  For the new user, staying within the package management system is the best way to have a trouble free experience, but this basic concept is not spelled out for new users on a fresh install.  Maybe something as simple as putting a text file on the desktop with the heading "Read me...Important information for new users"  or some such.  Because the Ubuntu desktop is so clean, it would stand out and maybe a few people would actually read it.  It could contain basic information about how to use Synaptic and Add/Remove programs.  It could also advise on creating folders in the home directory, etc.  Include a few links to things like the documentation that is installed with the distro, these forums and the unofficial Feisty installer guide. It doesn't need a lot of stuff, just the basic things we Ubuntu/Linux folk take for granted that are totally foreign to people coming from Windows.  

Linux isn't Windows, but it is just as easy, (or often easier), to use, just different.  

I'm glad to see this thread finally settled down and the tone has gotten a lot more civil.

---

### Post by poppers1957 on 2007-05-29
Great job mgmiller.  I really admire your train of thought.  Can you give me some pointers on how we might get your idea of the text file on the desktop in first install to the Ubuntu distro writers?   It is a great idea IMHO.  By the way, I too am glad this thread calmed down.  Is it ironic, that the most recent release is called "Feisty" fawn?  Sometimes people get a little feisty.  So does my 7.04 sometimes. :D

---

### Post by mgmiller on 2007-05-29
> poppers1957  	Great job mgmiller. I really admire your train of thought. Can you give me some pointers on how we might get your idea of the text file on the desktop in first install to the Ubuntu distro writers? It is a great idea IMHO. 

Thank you poppers1957.
I have posted this on the Gutsy Gibbon Idea Pool:

[http://ubuntuforums.org/showthread.php?t=458009]("http://ubuntuforums.org/showthread.php?t=458009")

---

### Post by pappapump on 2007-05-30
I have received ( despite some mean responses) some quite useful tips from this post.
So guess what I did?
First of all I dumped azureus completely since after the newest update it fails completely, and decided to do what that one guy said about using k-torrent and all is well.
Turns out that azureus is just too weak to keep up.
The gui combined with the java is just too unstable in either OS.
BUT since I have the new K-Torrent running night and day I have actually been able to accomplish at least one of my goals, which is to host the Ubuntu and Kbuntu torrents 24/7 every day.
But a pleasant surprise came up while I was searching for the most popular Ubuntu torrent and it's this new Ubuntu guide book.
It's a PDF file and at first glance it's pretty complete.
What the flamers seem to have missed with all of the go back to winders comments is that I'm sticking with Ubuntu no matter what happens.
I was watching Veronica Mars last night where the computer geeks were bragging about Ubuntu and It caused quite a chuckle as I was downloading new apps for my copy of Ubuntu.
No doubt, Ubuntu is causing quite a stir when It actually makes it to a TV series.
I just can't tolerate windows any more, Ubuntu has me spoiled.

---

### Post by mgmiller on 2007-05-30
Pappapump;
I am glad things are working out for you.  I realized from even your earliest statements, that despite your frustration, you were not going to let this Linux thing beat you and you were determined to stick with it.  

Hosting torrents for Ubuntu and Kubuntu is a very nice gesture on your part.  Thank you.

I suspect that you will find things get progressively easier as time goes on.   You will have an interesting time reading the new Ubuntu guide book you found.  If you ever get stuck, after doing a little reading, just stop by here and ask.   The Ubuntu community is amazing and will often go out of their way to help you.  I learned a lot just by reading through posts and seeing how others solved problems.  After a while, I started to answer questions for others and learned even more in the process.  I would not be surprised if you did the same.

Just to assuage my own curiosity....

> First of all I dumped azureus completely since after the newest update it fails completely,

This is interesting.  I have not seen any updates to azureus in a while.  The one I am using is from the Ubuntu repositories and it plays very well with java also installed from the Ubuntu repositories.  I have used this combo for at least the last 2 years without incident.

This is really a moot point because you now have an application that runs fine and you are happy with it, which is one of the great things about Linux.  The software choice is pretty good.  

But I am curious, how were you installing Azureus?  Did you add a repository from the azureus people, did you download and install their version or did you install the one direct from Ubuntu?   Same question about your java install.

Finally, let me officially, (wait a minute, I don't have a badge or anything, I'm not really certified to "officially" do anything for you), welcome you to the Ubuntu Community.  ):P

---

### Post by pappapump on 2007-05-30
Thanx for the greets.
I used the base installer that comes with Ubuntu, I didn't get the freeze out untill the Ubuntu kernel update, the Azureus prog didn't get updated.
I just saw the little orange symbol saying I needed an update and clicked it.
This is after it did it's initial update from a fresh install.
I plan to print that whole book and make a users manual from it for my customers.
That way if anything happens before I become an Ubuntu officianado my new customers won't be totally clueless.

I have begun using the ntfs manager to be able to mount and save to my Serial Hard Drive so that I won't lose any pertinent downloads.

Heres a funny side note to Ubuntu

When I got this latest batch of parts and made this PC I had to hit F6 and use a floppy I made to be able to read from and write to my Serial Drive.
Ubuntu already came with the appropriate Drivers and this mobo is barely a year old.

---

### Post by Mo_lo_ko on 2007-05-30
[http://world6.monstersgame.co.uk/?ac=vid&vid=114156966](http://world6.monstersgame.co.uk/?ac=vid&vid=114156966)

u should look...

---

### Post by bone43 on 2007-05-30
> **pappapump said:**
> Thanx for the greets.
I used the base installer that comes with Ubuntu, I didn't get the freeze out untill the Ubuntu kernel update, the Azureus prog didn't get updated.
I just saw the little orange symbol saying I needed an update and clicked it.
This is after it did it's initial update from a fresh install.
I plan to print that whole book and make a users manual from it for my customers.
That way if anything happens before I become an Ubuntu officianado my new customers won't be totally clueless.

I have begun using the ntfs manager to be able to mount and save to my Serial Hard Drive so that I won't lose any pertinent downloads.

Heres a funny side note to Ubuntu

When I got this latest batch of parts and made this PC I had to hit F6 and use a floppy I made to be able to read from and write to my Serial Drive.
Ubuntu already came with the appropriate Drivers and this mobo is barely a year old.

Certainly good to see your getting along with Ubuntu pappapump.
 I re-visted this thread today as I was wondering how it all turned out.. for the better me thinks!
:D:D:D:D

---

### Post by mgmiller on 2007-05-30
When you say you used the base installer, I assume that means that you installed azureus and java from within synaptic package manager?  I haven't tried running azureus since the last kernel update, I wonder if mine is borked also?

On another note, you said:
> I have begun using the ntfs manager to be able to mount and save to my Serial Hard Drive so that I won't lose any pertinent downloads.

If this is an internal serial hard drive and you want to get away from all things Microsoft, then consider reformatting the drive in ext3, the native linux file system used by Ubuntu.  It is a full journaling file system and never needs to be defragged.  

You will need to install 2 packages from Synaptic.
The first is called gparted (gnome partition editor)
This is used to create and format partitions.

The second is called pysdm (python storage device manager).   
This is used to create the mount points for them.  

After they are installed, look in System>Administration>Gnome Partition Editor to use gparted and System>Administration>Storage Device Manager for the pysdm program.  

Both are nice GUI's that allow you to avoid the CLI for these tasks.

---

### Post by pappapump on 2007-05-31
The problem with that is that I keep having crashes with my Ubuntu for various reasons.
With no Win2k partition I will lose all my email.
Every time I crash with Ubuntu i also lose any emails I downloaded.
My current mmorpg's are also only playable with Win2k and up so I still need it to work properly.
As a side note, I also use my Infrared remote and win2k to read my text files so I can sit back and sip coffee as I read the Ubuntu pdf guide.
This isn't possible with Ubuntu yet since the Nvidia TV- Out driver shows me a blank screen no matter what I do.
My tuner is also incompatible with Ubuntu and let me tell you It was kind of pricey even with my dealer discount.
At present I sell 2 types of PC's.
One is an mce version which i hope to change to an Ubuntu MCE style PC using Myth and the rest of the Ubuntu MCE package.
And the other is an Ubuntu only PC with all the newest bells and whistles.
Problem is I need to change my hardware on all of them to Linux compatible.
I use a lot of wireless hardware and the current budget based types aren't linux compatible.
The good thing is that since I no longer have to BUY an operating system, that I can now apply the savings on the compatible components.

---

### Post by mgmiller on 2007-05-31
OK, I understand why you need to keep your ntfs partition.  This can work to your advantage here. 

> The problem with that is that I keep having crashes with my Ubuntu for various reasons.
With no Win2k partition I will lose all my email.
Every time I crash with Ubuntu i also lose any emails I downloaded.

You are not having a typical new user experience.  Ubuntu should not be crashing causing you to lose your data.   

When you have a "crash", since you still have win2k, come back here and ask someone for help.  (Of course you could just boot off the live CD and come here as well.)  You will accomplish a few goals this way.  
1) You won't lose all your data.
2) You will learn a lot more about how to troubleshoot and fix Ubuntu.  
3) Since you run a computer shop and will be selling these machines, you owe it to your customers to be able to help them quickly and easily.  I know I have helped people with their windows installs after the so-called official tech support told them they needed to do a complete reinstall that would wipe out everything.  These were usually malware issues.

As far as your IR remote control goes, it may require some reading and tinkering.  Some packages you will probably need to install through Syanaptic are:
lirc and lirc-x which provide basic IR remote support.  It's probably a good idea to also install x-fonts-75dpi if it's not already installed.

Another interesting package is irda-utils  This package contains userspace utilities to manage and handle infrared
devices. 

I haven't tried to set up IR support in Ubuntu yet, so I don't know how easy it will be, but at least this gives you a starting point.

> At present I sell 2 types of PC's.
One is an mce version which i hope to change to an Ubuntu MCE style PC using Myth and the rest of the Ubuntu MCE package.
And the other is an Ubuntu only PC with all the newest bells and whistles.

The MCE PC requires a fair bit more knowledge to set up and configure than the normal new user has.  However, since you are going to be selling these boxes, you will need to learn how to do this.  Since you are the "manufacturer", you will be setting up and configuring these machine to the end user has nothing to do other than turning it on and using it.  One of the things that makes Windows so easy for most new users is that the manufacturer has done all the hard work of making sure all the hardware is compatible, all drivers are installed and everything is toaster-oven simple.

Once you have reached this level of competency, you will be doing the Ubuntu-Linux-FOSS comunity a great service by getting these machines into the hands of "normal" users who can then enjoy the unworried (no viruses, no spyware, no defragging, etc.) computing  environment of Linux.

> Problem is I need to change my hardware on all of them to Linux compatible.



Quite right.  This is the single biggest thing you can do to make your life easier.  Check the mythtv website for compatible hardware.  My understanding is, if you do this right, everything "just works".  If not, you can spend an inordinate amount of time figuring out how to make it work.  I seem to remember reading somewhere that ATI 9600/9800 based AGP 8x all in wonder cards fell into this category.  I don't usually recommend ATI video cards for linux installs, but for TV stuff, they seem to work more reliably than nvidia, especially for s-video out. 

I had used both nvidia and ati with s-video on a 27" TV in my bedroom for a while, both just worked without any real confugurtion when I tried them, so I'm not sure why you can't see TV on yours.  I do know the TV has to be plugged into the s-video port and be turned on before you turn on the PC  or the video card won't enable the s-video out port.

I have since switched to a 37" LCD in that location which has  regular VGA and DVI computer monitor inputs.  There is an amazing difference in picture quality,  It's just a big 1366x768 computer monitor.  I use an IR ps2 keyboard/mouse combo that was plug and play, no drivers or configuration required.  I think I paid $15 for it at newegg.com.

---

### Post by MaXqUE on 2007-06-01
I know how he feels. I've used Linux since 1998, mostly as  a server. As a server it is matchless, on the desktop its another story. I have endless configuration problems. I can never get further than running Firefox or Gimp.

If I sit down at this computer, I can count on two hours minimum, without doing what I set out to do. I cannot save a screen resolution (editing xorg.conf is NOT a solution). Although things are supposed to be inter-operable on Linux, they really aren't. I gather I'd be able to save my screen resolution if only I'd use Gnome or KDE. The fact that I want a Window Manager that doesn't look like a Windows application means I use Fluxbox. I'm quite happy doing the hand tooling required to make it work. But the other things are just plain frustrating.

Now, Azureus is again not working. In Dapper it simply crashed on startup. It would run if I started it as root but I will **not** run an application on then net as root. This time with Feisty, I actually got it running. The first configuration error I made caused it to simply crash on startup. So I trashed the .azureus folder and started again, not making that mistake. But simply put, no configuration error in a GUI should be fatal to an application like that was. 

 I thought I was home free but came back two hours later to find Azureus not running. Again it crashes on start up. The log file it generates is huge. I cannot even begin to devine where its going wrong. I'm back to square one.

Now people, I know that the Java developers at Sun used Linux workstations to develop Java. That info comes from a reliable source. Why Azureus runs on Windows and Mac OS X but not on Ubuntu is beyond me.

No, I'm not a troll. Unlike a real troll, I want answers. Sometimes I get them but things on the whole never get much better. I have legacy hardware. It used to be state of the art, but its not now and Linux seems to run better on newer hardware from Dell etc.. and not so well on custom built legacy hardware. That isn't what Linux reputation has been built on.

The original poster might be tearing his hair out at this point. I'm long beyond that point. I simply expect that this is going to be the case. I may, or may not get any answers. When this one is solved, another one will pop up which will suck up just as much time. The system seems never to be stable even though I'm running very few applications. There's a lot of hype about Ubuntu, but for many people, it simply hasn't proven to be the case. Perhaps if I went back to running Red Hat installations things would be more stable. I haven't run Fedora Core yet so that might be an option.

I haven't yet read all the posts here. I typed in Azureus crashes and got  at least a page full of posts. Obviously many others have these problems.  I  may sound a little less angry, but I'm still tearing my hair out trying to make this system work the way a Desktop OS should work.

Cheers,
maxque

---

### Post by seetho on 2007-06-01
I've been using/programming/designing/building/selling/supporting/fixing computers and software since 1984 (hmmmm...), and experience has taught me a few important facts:

1. Software always has bugs in it.  Even those by design that others consider 'features'.
2. Hardware is never ever 100% reliable.  The older it is the worse it gets.
3. Users always (ALWAYS) make mistakes, and they always deny (or conveniently forget) that they can, will and probably did make mistakes along the way - just human nature.

Keeping these facts in mind you'd go a long long way in solving problems without the need to resort to hair pulling (or, nowadays, web-forum trolling) to relieve yourself of all your frustrations.

So you have problems with Azureus you say.  So is it a problem with Ubuntu, Linux, Azureus, or Java? ( Naturally this will be your first reaction.)  It doesn't work on your Ubuntu system - but the fact remains that it is working fine for the majority of others using it; so it can't just be a problem with the software.

Let's have a look at hardware now.  If you ask anyone with experience doing system support you would know that the first and most like thing to break in a PC is the HDD.  Most of the time when a system starts to act funny, the most likely cause is the HDD.  If you do a simple diagnostics you will not likely to find any faults.  To really make sure you'd have to do a low level check fo each and every bit of the HDD recording surface.  So HDD manufacturers provide such utilities for their products so you can check with the support or web-site.  A good generic alternative is Spinrite from [www.grc.com](www.grc.com).  It is not free - but worth the price in my opinion.

Another component that can cause problems is the RAM.  This is easy to test - the GRUB bootup menu give you the option to do a memtest.  This is a very extensive memory test and on many occasions has found memory problems that other non-free utilities fail to identify.

Other consideration would be whether you have some hardware components that is uncommon or is poorly supported or is unstable (I had a flakey USB webcam causing all sorts of problems one time - believe it or not).

The next thing you have to consider is the human element - this is the most difficult.  There are many things to consider here especially when you are dealing with Linux.
1. Did you check whether your Azureus runs on a standard config Ubuntu (Feisty?).  The best would be to test right after a fresh install.
2. Did you have other things installed on your system, especially things not from the standard repos that may have libraries, daemons or configs that intefere with your Azureus?  Most people install software that is marked 'unstable' without even taking a second to consider why they tagged it as 'unstable' in the first place.
3. Did you change your system configuration in any way that may cause this failure; e.g. fiddled with java settings etc?

I have a separate PC installed with Ubuntu to test packages that I think that may need to use but feel that they are suspect in some way.  Only if I find that it is running with no problems on this test system I will install it on my working PC.  You don't even need a separate PC - just a small separate partition with another install.  If things go wrong here you can always clear it out and reinstall the OS.

No one should claim that Linux will give us world peace and eradicate hunger and all desease from the face of this world.  In fact it has, since the beginning, been work in progress and it will always be this way.  You should expect things to break along the way, but in the long run progress is made and this to me is a good thing.

Help can be available here (or in other forums) only if you ask the right questions (politely).  Don't demand answers - everyone, including all the developers out there, is doing this purely on a voluntary basis - no one is obliged to give you anything.  It's just like when you buy someone you don't know a free lunch out of the goodness of your heart and the response you get is: "Hey, you forgot the beer.  How do you expect me to eat this without beer?"

Cheers.  I hope you have more luck in getting your system to work without loosing too much more hair.

---

### Post by linfidel on 2007-06-02
> **seetho said:**
> I've been using/programming/designing/building/selling/supporting/fixing computers and software since 1984 (hmmmm...), and experience has taught me a few important facts:
. . .I might have you beat, but not by much (unless I count my early days in college).  I started with an S-100 CP/M machine that I built from bare reject circuit boards that I soldered components to.  But I digress... :)

> **seetho said:**
> I have a separate PC installed with Ubuntu to test packages that I think that may need to use but feel that they are suspect in some way.  Only if I find that it is running with no problems on this test system I will install it on my working PC.  You don't even need a separate PC - just a small separate partition with another install.  If things go wrong here you can always clear it out and reinstall the OS.

Cheers.  I hope you have more luck in getting your system to work without loosing too much more hair.Since I don't have much hair left to lose, I have another way to test things.  If you have enough disk space and RAM, install virtual machine software and install a base Ubuntu in a VM.  Then, take a snapshot of the base system, to use for testing, and then revert back to the snapshot afterwards. I do this at work using VMWare for Windows, and when I get a new motherboard with more memory and power, I intend to experiment with something like that for linux.  Ubuntu ran very well in the Windows VMware.

---

### Post by linfidel on 2007-06-02
> **MaXqUE said:**
> I know how he feels. I've used Linux since 1998, mostly as  a server. As a server it is matchless, on the desktop its another story. I have endless configuration problems. I can never get further than running Firefox or Gimp.

If I sit down at this computer, I can count on two hours minimum, without doing what I set out to do. I cannot save a screen resolution (editing xorg.conf is NOT a solution). Although things are supposed to be inter-operable on Linux, they really aren't. I gather I'd be able to save my screen resolution if only I'd use Gnome or KDE. The fact that I want a Window Manager that doesn't look like a Windows application means I use Fluxbox. I'm quite happy doing the hand tooling required to make it work. But the other things are just plain frustrating.
...It's unfortunate that you have so much trouble.  I understand the part about spending a lot of time, although for me, it's not fixing things so much as learning new stuff, and I enjoy it.  Some people play games, some people watch TV, but for me, playing with a new system often sort of satisfies both of those.  But if I just need to get something done, I can always do it, even if I have to revert to my XP system (by pressing a couple of keys to activate my KVM switch).  

I'm not familiar with some of your software, but I wonder if you could possibly have the same video problem I had for a while.  Probably not, but just in case...   Do you have your monitor on when you boot up?  I found that, for most linux distros I've used, if my monitor wasn't detected, the system would boot in 800x600 mode, and I'd have to restart.  Fortunately, I learned to restart X by Ctrl-Alt-Backspace right at the login prompt instead of rebooting, which is quick. :)

---

### Post by seetho on 2007-06-02
> **linfidel said:**
> I might have you beat, but not by much (unless I count my early days in college).  I started with an S-100 CP/M machine that I built from bare reject circuit boards that I soldered components to.  But I digress... :)
I did use a time sharing CP/M system in those days.  Imagine 32 terminals all hooked up to a box with with just your humble Z-80 cpu running at 4MHz.  I still remember that you'd need pretty strong fingers to type on those steel encased terminals - even the keys are made of steel.  Ahhh... those were the good old days.

>  I intend to experiment with something like that for linux.
Linux, like it or not, is still pretty much for tinkerers to experiment on.  I find that I learn a lot more if I need to fix something that's not working or when I have to build it myself.  If you like this sort of thing then Linux is for you, otherwise your choices will be either OS X or Windows.

---

### Post by linfidel on 2007-06-03
> **seetho said:**
> Linux, like it or not, is still pretty much for tinkerers to experiment on.  I find that I learn a lot more if I need to fix something that's not working or when I have to build it myself.  If you like this sort of thing then Linux is for you, otherwise your choices will be either OS X or Windows.Tell me about it!  I just decided to upgrade my Linux box, from a two-year old P4 with 1/2 GB, and went for a Fry's deal with a AMD dual core 5600 and a free ECS MB with Nvidia 6100 that appears not to be very well supported by Ubuntu.

The amazing thing was that it booted, and after running dpkg-reconfigure, actually seemed to work well.  But I decided to reinstall anyway to make sure it was really recognizing the new resources.  I don't really know if that was necessary or not, but I'm pretty sure Windows would not have been able to boot at all.

---

