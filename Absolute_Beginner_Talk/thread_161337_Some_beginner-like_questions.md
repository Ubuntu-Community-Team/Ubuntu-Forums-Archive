---
title: "Some beginner-like questions"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by nalmeth on 2006-04-16
I am house sitting for my folks over the weekend, and have been trying to use their Windows computer for some very simple things, and it is quite apparent that since I was last here, this computer has become more than dis-functional.
By logging into my sister's account, I am bombarded by pop-ups for windows update, aol, 3 different messengers, and all kinds of other services that aren't needed. After shutting all of them off, this computer is laggy as hell, and no disc-clean up, defrag, anti-virus scan has helped anything. ARG as I speak AOL keeps nagging me to update it!! I can't download anything, as the progress just stops, while the window sits there as if nothings wrong. I couldn't even type into the text field here in firefox.
This computer has a large harddrive for windows, and a 30 gig drive for backup/data.
I want to install ubuntu on this PC, but I don't want it to get in the way of their normal windows routine. My Mom will need her outlook contacts emails etc, and my sister needs only media use, browsing, and instant messaging. Perfect Ubuntu Candidates I think.
I figure that if they can use Ubuntu for most of the stuff they do, Windows will function better when they really need it for a special hardware device, or simply something that requires Windows.
 
My concern's in doing this are (in order of greatest to least importance):
1. Windows has to be default on GRUB
2. All Outlook Data must be imported
3. Need a decent messenger with as much functionality as possible
4. Need to be able to share files between windows and ubuntu.
 
What I have learned is this (with questions):
1. Can easily be done, just requires editing grub list. 
2. Install Thunderbird on windows, covert .pst files, and put them on Ubuntu partition, import into Evolution/Thunderbird. Is this correct? Any other ways?
3. Amsn has audio/video and other features, but not the nicest looking app. Mercury looks good, would anyone suggest this before amsn?
4. This is a little more tricky. Ideally, I would like to mount /home on a fat32 partition, so that I can fully share from windows, but I have heard there is problems with linux permissions, and this won't work.
I think it might become confusing to put all data from Ubuntu (ext3) onto a fat32 data partition, and then to access that data from ntfs. (Reinstalling windows with fat32 not an option).
 
With all this in mind, I think this would be fairly easy to setup. 
Please share your thoughts.

---

### Post by htinn on 2006-04-16
I'd put a /share folder in a FAT32 partition rather than /home.

---

### Post by nanotube on 2006-04-16
[QUOTE=nalmeth]
3. Amsn has audio/video and other features, but not the nicest looking app. Mercury looks good, would anyone suggest this before amsn?
[/quote]
i use gaim - comes by default on ubuntu. used it on windows too, before i switched. no fancy camera stuff, but all i need is chat, since i dont have a cam anyway.

> 4. This is a little more tricky. Ideally, I would like to mount /home on a fat32 partition, so that I can fully share from windows, but I have heard there is problems with linux permissions, and this won't work.
I think it might become confusing to put all data from Ubuntu (ext3) onto a fat32 data partition, and then to access that data from ntfs. (Reinstalling windows with fat32 not an option).
 better to make a separate partition for your shared fat32 files, rather than to use /home. that's what i do. whenever you want to access some file from win, just shove it onto your fat32 partition before reboot.

---

### Post by aysiu on 2006-04-16
House-sitting for the weekend?
Get a Knoppix live CD and make a persistent /home
Don't install anything to their computer.

---

### Post by nalmeth on 2006-04-16
[quote=aysiu]House-sitting for the weekend?
Get a Knoppix live CD and make a persistent /home
Don't install anything to their computer.[/quote]
I did actually download a Knoppix live CD, but to my amazement, it did not like the Philips flat screen monitor. Knoppix has been the failsafe distro in my linux experience, and this is the first time it didn't work. I am trying to download a pclinuxos iso but it's taking AGES, and I've had to restart it when it goes idle.
I've considered setting up something like that, even a /home on a usb stick, or on the 30 gig drive, but I figure that the best way to go is a full install, so they can get a full linux experience, but not to intrude on their XP dependencies. After all, the extra drive just has a bunch of old data they already have backed up on CD's.

---

### Post by Papa-san on 2006-04-16
Honestly, If you want to really do them a favor, download, install, run, and uninstall Adaware...lol That'll clean up the spyware that is the most likely problem...

go to [www.lavasoft.de](www.lavasoft.de) for the right one... If you search for it, you will find a hundred other things that will actually install spyware...

But, The RIGHT thing to do is follow aysiu's advice... leave it be, and talk to them about it FIRST!

---

### Post by nalmeth on 2006-04-16
[quote=Papa-san]Honestly, If you want to really do them a favor, download, install, run, and uninstall Adaware...lol That'll clean up the spyware that is the most likely problem...
 
go to [www.lavasoft.de]("http://www.lavasoft.de") for the right one... If you search for it, you will find a hundred other things that will actually install spyware...
[/quote]
Even when I do that, and it works, they will still have the thing crammed up within a week. It's not a very effective solution as far as I can see. I'm not going to become their windows tech everytime they follow the scams that get their computer infected. Again, considering their computer needs, I think Ubuntu can fully accomodate them, and again, if they can log into windows for only a few important things, then they will be able to use windows functionally again.
> leave it be, and talk to them about it FIRST!
Naturally. I don't think that going behind their backs will give them any confidence in using the software. 
Beyond what is wrong with their windows system, I personally just want them to know what linux is. What it can do, and what it stands for in terms of the rights they have to the personal use of their own computer. 
Even if it is NEVER booted into, the drive I want to put it on is used to hold obsolete, and (already backed-up) old data that they don't even need anymore. 
I don't see the benefit in going halfway and making them throw in the liveCD everytime they are curious about it. Linux can be confusing enough, and I think I can do a lot to simplify the experience for them, knowing their needs wants and tendencies.
 
Thank you for your thoughts guys, please add anymore input you have

---

### Post by big joe on 2006-04-16
Spybot S&D from [http://security.kolla.de/](http://security.kolla.de/) has an "immunize" function that works pretty well for Win-aholics. Just remember to d/l the latest update file before you run it.

I would be really leary of installing a new OS unasked.

---

### Post by ohwir on 2006-04-17
[QUOTE=big joe]Spybot S&D from [http://security.kolla.de/](http://security.kolla.de/) has an "immunize" function that works pretty well for Win-aholics. Just remember to d/l the latest update file before you run it.[/QUOTE]

Spyware Blaster [http://www.download.com/SpywareBlaster/3000-8022_4-10196637.html](http://www.download.com/SpywareBlaster/3000-8022_4-10196637.html) was recommended to me as a good Windows 'babysitter'.  (I never had a chance to try it-  XP was fatally crashed by something nasty picked up by my partner, and I had no  Windows discs, so have ended up going the whole hog with Ubuntu - but the person who recommended it is a reliable tipster for this sort of thing).

Ad-Aware is fabulous - people will think you're some sort of genius for clearing up their machine when all you've done is install & run Ad-Aware ;)

---

### Post by nalmeth on 2006-04-17
I've used both SpyBot and AdWare in the past, and they are great windows apps, but I'm not interested in being a Windows Repair Man. I will install them, but I think using Ubuntu is a more useful solution. The family arrives later tonight, and I will talk it all over with them..
Really there's nothing to lose with an extra unused drive, and I think a lot of things will actually be easier for them.
I bought them a DVD-burner and 50 DVD-R's for Christmas, and they haven't even burned one yet! They don't know how!
I think that Nero's interface might be a little confusing to them. Creating a data DVD isn't as obvious as it should be, like in K3B or GnomeBaker.

---

### Post by ncappel1 on 2006-04-18
I'd just like to sat that I was laughing hysterically at your description of the "more than dysfunctional" computer. I can't tell you how many times I've gone through the exact same thing with my girlfriend's, my family's, and my friends computers. I feel the pain just reading the post about your struggle, reaching out towards the ubuntu community. "There...must....be..a...b-b-.....better...way!"


cheers

---

