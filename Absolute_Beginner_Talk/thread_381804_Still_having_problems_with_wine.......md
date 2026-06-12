---
title: "Still having problems with wine......"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-03-11
Hello.
Well ive been trying for a couple of weeks now to get wine to run under edgy, and still no luck, the same thing happens every time, basically it just locks the system everytime, and it doesnt matter what you do, so i thought i would ask if there are any issues like this running wine under edgy, and if there is a way to resolve this problem, other than that i am more than happy with ubuntu, bee running it for over a month and had no problem at all.
i only want to get wine to run to try and see if i can get games to run with it and also i have a tesco internet phone and i want to be able to use it under linux, i know you can run skype, so there must be a way.
if i can get wine to run and then run games with it and use my phone then i can do away with the windows xp install ive got on another hard drive for good.
cheers

---

### Post by Xyhthyx on 2007-03-11
This might help:

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine)

I think you misunderstand how wine works. You don't get wine to run under edgy, you use wine to try and get windows binaries to run under edgy.

---

### Post by euler_fan on 2007-03-11
Thanks for posting the link to the howto. I have been wondering how it works for a while now.

---

### Post by techno-mole on 2007-03-11
i think i should have gone into a little more detail.
ok, for around 3 weeks i have tried every how to and set of instructions on how to install wine, and everytime i get the same result, it locks the system up, it will not run on my machine, ive tried the how to you put the link to (thanks) and the same thing happens, and as i said i have tried various others and no joy.
so i am at a loss as to what is wrong (much head scratching) 
i know wine is for running windows stuff on linux, but you cant run windows stuff under linux if you cant get wine to install and configure it.
cheers

---

### Post by diatribe on 2007-03-11
what command are you trying to execute when the system crashes?

---

### Post by techno-mole on 2007-03-11
it doesnt matter what command i use, all the commands do the same, you can enter any command and things look ok for about 30 seconds, then everything just stops, the system locks up and the only way to get out is to press the reset button.
ive tried leaving it and seeing what happens, and after half an hour (the longest i waited for) the system is still locked and there is no activity from the hard drive (at least it seems that way as the hd led doesnt do anything) 
:confused:

---

### Post by Delvien on 2007-03-11
if you have not already, do the followiing 

```
sudo apt-get install wine
```

If you have already done so, please do the following 

```
winecfg
```

and tell us what happens.

---

### Post by techno-mole on 2007-03-11
ok, done that.
used the commands posted and the system locks up, and i have to press the restart button to get out.
cheers.

---

### Post by Delvien on 2007-03-11
> **techno-mole said:**
> ok, done that.
used the commands posted and the system locks up, and i have to press the restart button to get out.
cheers.

do this then

```
sudo apt-get remove --purge wine
```

then

```
sudo apt-get install wine
```

---

### Post by techno-mole on 2007-03-11
i thought i would try the how to again (i tried this particular one a couple of weeks ago) but i can only get as far as downloading the wine tools application, i think maybe the server where the download is located maybe down, or very busy.
just for the record though, if you install wine with automatix, it tells you to run winecfg after it has finished installing wine, and it locks the system up, like ive said it doesnt seem to matter how i install, or what commands i use the end result is the same.

---

### Post by Delvien on 2007-03-11
> **techno-mole said:**
> i thought i would try the how to again (i tried this particular one a couple of weeks ago) but i can only get as far as downloading the wine tools application, i think maybe the server where the download is located maybe down, or very busy.
just for the record though, if you install wine with automatix, it tells you to run winecfg after it has finished installing wine, and it locks the system up, like ive said it doesnt seem to matter how i install, or what commands i use the end result is the same.


DO NOTE USE AUTOMATIX TO INSTALL ANYTHING, it will break your system. 

this is probably your problem.

---

### Post by techno-mole on 2007-03-11
i would agree if it wasnt for the fact that when i first installed ubuntu, i did it all with command lines (didnt know about automatix then) and i got the same results with wine then as i do now.
everything else on my system works perfectly by the way.

---

### Post by Delvien on 2007-03-11
> **techno-mole said:**
> i would agree if it wasnt for the fact that when i first installed ubuntu, i did it all with command lines (didnt know about automatix then) and i got the same results with wine then as i do now.
everything else on my system works perfectly by the way.


have you used the commands i told you to, with purge?

---

### Post by techno-mole on 2007-03-11
sudo apt-get remove --purge wine did this first,
then did this - sudo apt-get install wine
all that went fine, but the minute you try and do anything with it, it locks the system, so for example when wine creates the required files and such like, it locks the system, if you type winecfg system locks, and any other command.
i have tried the commands you posted and in the order you stated, but no joy im afraid, it just will not have any of it.

---

### Post by Delvien on 2007-03-11
> **techno-mole said:**
> sudo apt-get remove --purge wine did this first,
then did this - sudo apt-get install wine
all that went fine, but the minute you try and do anything with it, it locks the system, so for example when wine creates the required files and such like, it locks the system, if you type winecfg system locks, and any other command.
i have tried the commands you posted and in the order you stated, but no joy im afraid, it just will not have any of it.


Well im not sure what else to do. do a memtest ( through grub ) and also do a fsck

---

### Post by misha680 on 2007-03-11
I don't think you are alone in this problem actually. wineprefixcreate seems to never finish on my computer since I updated my edgy system last week (using both git and 0.9.32) and it used to work fine before and wineprefixcreate will be run if you don't have a ~/.wine directory before any wine commands, so this would explain your problems. I had not updated my system for quite some time tho, so it was like 42 updates, and I am quite busy right now writing a grant so I'm honestly not sure I'll be able to look at into the problem further right now, but just wanted to let you know others are having this problem.

Misha

p.s. btw, you certainly don't have to reboot when it does this. You can press Ctrl-C or just go into System Monitor and kill the rundll32.exe process.

---

### Post by jackrobinson on 2007-03-11
> **Delvien said:**
> DO NOTE USE AUTOMATIX TO INSTALL ANYTHING, it will break your system. 

this is probably your problem.
DO NOT LISTEN TO CRAPPY ADVICE. 
do the following:
```
sudo rm -rf ~/.wine
```
and run
```
winecfg 
```
again

---

### Post by linuxian on 2007-03-11
I've tried using Wine to run a couple of Windows apps, unsuccessfully. The apps I was trying to run were Corel Draw 8 and a wargame called WinSPMBT (Steel Panthers Main Battle Tank).

I find Wine is not very intuitive or easy to use - that is, if an app won't run under Wine, how do you remove it?

---

### Post by Fíona on 2007-03-11
I just started using wine yesterday, so I'm no expert!
Which version of wine are you using?

command line wine --version

I noticed that installing via the normal Ubuntu repository, I got an older version which didn't work.
I followed the howto:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
" Newer versions of wine (not recommended)".

Then I was able to install programmes via wine.

Good luck!

---

### Post by jackrobinson on 2007-03-11
> **linuxian said:**
> I've tried using Wine to run a couple of Windows apps, unsuccessfully. The apps I was trying to run were Corel Draw 8 and a wargame called WinSPMBT (Steel Panthers Main Battle Tank).

I find Wine is not very intuitive or easy to use - that is, if an app won't run under Wine, how do you remove it?

```
cd ~/.wine/drive_c/Program\ Files/
```
after you navigate to this directory, you will see the different directories for programs installed. (if you do a 
```
ls
```)
go to the directory of your choice and you should see an uninstall executable there.
run the uninstall executable with wine
such as:
```
wine uninstall.exe
```

---

### Post by misha680 on 2007-03-12
Since your problem sounds like mine (wineprefixcreate was hanging, so nothing wine-related would run) it seems like it was a font problem for me (I am using mlind's repositories). Yesterday, he posted some new debs and a:

```

sudo aptitude update
sudo aptitude dist-upgrade

```

Fixed it for me.

Misha

---

### Post by zgoda on 2007-05-12
> **linuxian said:**
> I've tried using Wine to run a couple of Windows apps, unsuccessfully. The apps I was trying to run were Corel Draw 8 and a wargame called WinSPMBT (Steel Panthers Main Battle Tank).

I had no luck with "pure" SPWAW 8.20 either. Tried wine, tried cedega, still no joy. Program installs then I receive "DirectX initialization error" message and application quits.

---

### Post by techno-mole on 2007-05-26
could it really be something as simple as i dont have the right fonts installed, or im not using the right fonts ?
it would figure that it will turn out to be something like this.
cheers

---

### Post by Big_Kiwi on 2007-05-26
Hi techno-mole 
have you tried totaly uninstalling wine, shutting down your system totaly for a minite or two then restart and re install, If that dose not work go to [www.winehq.com](www.winehq.com) and look for an aulturnitive version of wine progam that one may not work under the system you currently have

---

### Post by techno-mole on 2007-05-26
yes ive completely removed wine, and tried re-booting and starting again, ive also tried using different version of wine and all the the same end, basically the system lock up ive mentioned.
its a puzzle because i have no idea why it wont run and i cant see what could be stopping it from running, unless its something to do with needing root access to the file system in order to create what it needs to ? clutching at straws here.
it has to be something on my system though, i dont know how its possible from all the guides ive tried for one of them not to have worked, i dont think its anything to do with the version of ubuntu im using as im running the 32 bit version, so in theory the wine version you can install through synaptic should run ok, but it doesnt.
still i shall keep researching it, might find an answer.
cheers

---

