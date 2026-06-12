---
title: "Losing Hope"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by RedGecko on 2007-07-29
[COLOR="Red"][SIZE="5"]Warning: Long and whiny post. [/SIZE][/COLOR]

Great.. I have to type this all again because nothing wants to save, when I try to save the program shuts down. That's fine. I'll type it again.

I'm getting really angry and frustrated. I don't really know what to do. I want to give this OS a chance, I want to let it work for me because so many other people love it and say how great it is. I want to try, but Ubuntu doesn't want to let me. I've installed and re-installed Ubuntu several times now. Shoot, I could probably go through the install with my eyes closed.

Now let's see.. What all has gone wrong.
Well first I tried to install Ubuntu's AMD64 version. Cool! It works fine, everything is just fine. I like it, I decide I'll keep it. Until I realize that the AM64 version doesn't support flash. Okay... Well I don't need a 64-bit version. I re-install Ubuntu with the 32-bit version. I was excited about Ubuntu and started to customize things. I had everything working just fine, all of the software was exactly what I needed, I even got Beryl to install and was super-excited about this fun feature.
Cool.. So one day I start up my computer, and and the Update Manager lets me know that I need to update. Okay, I do. The computer asks me to reboot, so I do. When I reboot, I get new options in my GRUB. Alright, along with the original "Ubuntu, kernel 2.6.20-15-generic" I now have "Ubuntu, kernel 2.6.20-16 generic"
At the time I had never seen anything like it. I figure it's normal and I select the first option (the new kernel "16") ... After several problems, I post to the forum
Here is that post, it goes through all the problems I had that time: [http://ubuntuforums.org/showthread.php?t=458548](http://ubuntuforums.org/showthread.php?t=458548)

As you see in that thread, I decided in the end to just re-install Ubuntu, and this time just not make the same mistakes I must have made the first time.
I did that, assuming everything would be the way it was before. It wasn't... It hasn't been. I'm going to only go over the problems I'm having THIS time, because I'd really love to NOT have to re-install it again. I'd love to just keep this install and go on with my life using Ubuntu the way everybody else does. I know I don't know a lot about Ubuntu, or linux for that matter, but this is something I want to learn about..

So let's begin... I have two hard drives. One (the 150gb master) contains WinXP, while the other (the 200gb salve) is meant to be home to Ubuntu.
I decide this time to go back with the AMD64 version.. I figure it's NOT a big deal to not use flash, and there may be a future fix to this problem. I try to install it with the disk I had originally used. The install would go about half way and then lock up. I figured I'd make a new disk, because I assumed the old one had been damaged in some way (because it worked at one point)
Okay, the new disk had the same problem, so I figured to continue sticking with the 32-bit version I was using (that I had stable for a while)

I installed it on the slave drive, and rebooted when it told me to. It brought up the GRUB I had before, the one that said "Ubuntu, kernel 2.6.20-15-generic"
Okay, I start that one up, and I log in like I always do.

From the get go I get an err. This is an entirely new one, and I don't know what caused it (because this is the same install I used before, and I haven't even done anything to the system yet.
Here is that error:
"There was an error starting the GNOME settings Daemon. Some things, such as themes, sounds, and background images may not work correctly. The last error message was: Message did not receive a reply (timeout by message bus)
Gnome will still try to restart the Settings Daemon next time you log in."

Oooookay, I figure that can be fixed and I dismiss the message box.
I go to my Update Manager, because it alerts me that I need to update my system. Sounds normal. It tells me I have 100 updates, still fairly normal I suppose, so I tell it to DL and install them. My update manager gives me an error at the end of the install. I wish I had written it down because I can no longer cause the error. It basically told me that I had corrupted downloads.. The ones that were corrupted (there were 5 I think) were all something to do with openoffice.org and language packages... I have no idea though.
After this, my computer asks me to reboot, and I do. After the reboot, my GRUB displays the new option(Ubuntu, kernel 2.6.20-16-generic). I feel wary of this new option because of what happened last time, but I select it anyways. It brings me to a black screen with white text. The text says:
"Starting up...
[ 49.085748] crc error
[ 49.086304] kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)
[ 49.086334]"

...right. That sucks. I have no idea what this means, and I cannot type anything into this screen. I reboot because there is nothing else I can do. I select the new kernel again, same error.. Okay, reboot. I select the old kernel, it goes through a crap-ton of rapid white text ona black screen. Just flowing through a bunch of stuff I cannot even read (because it is going so fast)
It ends on a screen that looks entirely like my terminal. And only my terminal. Right.. I'd fuss with it and all, it's just I don't really know THAT much about my terminal yet. Still need to learn that. I reboot and select the old kernel again, this time the rapid text doesn't come, it loads up the Ubuntu screen like it should....okay. That's good, I think. I don't know why it didn't want to load before, but at least it does now.

I log in again. I get the GNOME settings Daemon err again. I figure I'll deal with that when I have a chance. My update manager again pops up in the corner. I click on it, only to receive an err message box.
"Software index is broken. It is impossible to install or remove any software. Please use the package manager "synaptic" or run  "sudo apt-get install -f" in a terminal to fix this issue at first"

Okay... I figure at this point that I should get some help... I hunt though forums, becoming increasingly frustrated, as my firefox continues to vanish. Let me point out that even when I had ubuntu stable, firefox was not. I don't know what the problem is. I'll just be reading down some text, or clicking on a link, and it will just vanish. I'll open a new browser and sometimes it will re-vanish, and sometimes it will work. ... I dunno, firefox is also pissing me off, but I figure..fix the system first, the browser second.

After becoming fed up with both firefox crashing and being unable to find muc on my problems, I decide I should try what the Update Manager told me to try.
It tells me "You have 1 broken package on your system! Use the "Broken" filter to locate it."

And I do. And the package listed as broken is: Openoffice.org-style-human. Okay.... I check the box for re-install, and it errs with:
"E: /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb: corrupted filesystem tarfile - corrupted package archive" .. I dismiss the err and the synaptic package manager vanishes.. just like firefox.. awesome.

Okay..I have no idea what THAT means, but I'm sure you can tell me that, too...
Since that didn't work, I decided to go into the terminal and put exactly what the Update Manager told me to put...

```
jessica@pookie:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-common
Recommended packages:
  openoffice.org-style-industrial openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-andromeda
  openoffice.org-style-hicontrast
The following packages will be upgraded:
  openoffice.org-common
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
20 not fully installed or removed.
Need to get 0B/12.0MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
```

Okay, the result:
```
(Reading database ... 99885 files and directories currently installed.)
Preparing to replace openoffice.org-common 2.2.0-1ubuntu3 (using .../openoffice.org-common_2.2.0-1ubuntu4_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

that looks very familiar...
Hmm...
So I open a text editor to type all this up.. Well, I made it about half-way through when I decide to save it, because I know my system is unstable. I click save, and the text editor vanishes... I throw a fit, and nearly start to cry, because nothing seems to be going right! After I compose myself, I decide to go through all the other programs to see what does and doesn't want to work. I am currently typing this up in a gmail draft, because that auto-saves into my email every 2 minutes, ..at least I can save this.. sigh..
So back to all the other messed up programs.
Gaim won't even stat. I click it, it doesn't start.
Solitaire works! Yay!
Well.. To be honest, I don't want to open every program I have, but you get the idea, a lot of them won't even start.

Opeoffice word processor will load up, but also refuses to save. It closes itself.
The movie player won't start.
The musicbox won't start...
The sound recorder won't start..
Solitaire works! YES!!!! I'd like to use my computer for more than Solitaire...

I went to the restricted drivers, and decided to see what happens when i enable my nvidia driver, it errors with "you have 4 broken packages" etc...


... I'm honestly feeling quite hopeless. I just don't know where to start and what to do. Maybe someone can help me, because these types of problems just keep happening. I can't seem to get my Ubuntu system stable... And I'm not even doing anything strange with it!

---

### Post by moore.bryan on 2007-07-29
*did you install dapper (6.10) or feisty (7.04)?*

---

### Post by RedGecko on 2007-07-29
> **moore.bryan said:**
> *did you install dapper (6.10) or feisty (7.04)?*
I'm using feisty

---

### Post by Apocalypse on 2007-07-29
> **RedGecko said:**
> [COLOR="Red"][SIZE="5"]Warning: Long and whiny post. [/SIZE][/COLOR]

Here is that error:

"Starting up...
[ 49.085748] crc error
[ 49.086304] kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)
[ 49.086334]"



I have the same problem here, with feisty. My "solution" was to disconnect the windows drive and reinstall ubuntu. If I need to do something in windows, I change the hd, and use a fat32 partition in the slave hd for shared data.

And, after that second message, if you log in another console, you can enter to x with the standard startx and use the system. I had to use my pc this way for 2 weeks. Why this happens, I have no idea.

---

### Post by moore.bryan on 2007-07-29
*have either of you tried making the slave the windows drive and ubuntu the primary?*

---

### Post by aysiu on 2007-07-29
[Someone had that same kernel panic problem on Breezy and got it solved.](http://ubuntuforums.org/showthread.php?t=27709) Not sure if the solution would work for you as well.

---

### Post by Paul820 on 2007-07-29
And for your flash problem, kilz made a howto here: [http://ubuntuforums.org/showthread.php?t=202537&highlight=flash+64bit]("http://ubuntuforums.org/showthread.php?t=202537&highlight=flash+64bit")

---

### Post by cmnorton on 2007-07-29
First, on which kind of system are you installing both 32-bit and 64-bit versions of Ubuntu? 

Second, I'd like to suggest that you tackle these problems one at a time. I got Ubuntu 6.06 LTS installed a second time, by using safe mode to boot the live disk. After that, I could successfully install. 

I got a strong interest in Linux, when I started my current job 3 1/2 years ago. I inherited the sustaining and db/sysadmin responsbilities for four "home-grown" systems, written in C, Informix 4GL, and shell scripts. They were running on SCO, and needed porting to Linux.  

Learning all this stuff takes time, and it does not hurt to embrace the chaos.

Good luck!

---

### Post by RedGecko on 2007-07-29
> **cmnorton said:**
> First, on which kind of system are you installing both 32-bit and 64-bit versions of Ubuntu? 

Both on the same system. I always install over the other version, so I do not have both versions on my system (currently the 32-bit)

My processor is AMD Opteron 144 (1.80 GHz)
1.0 GB DDR RAM (Crucial Ballistix 512MBX2)
ASUS A8N-E Motherboard
I know my graphics card is EVGA Nvidia, and I can't specifically remember

---

### Post by RedGecko on 2007-07-29
> **moore.bryan said:**
> *have either of you tried making the slave the windows drive and ubuntu the primary?* 
When I tried to install Ubuntu on the master it wouldn't even install.


> **aysiu said:**
> [Someone had that same kernel panic problem on Breezy and got it solved.](http://ubuntuforums.org/showthread.php?t=27709) Not sure if the solution would work for you as well.
I tried what that post suggested, it didn't work.

---

### Post by Dark Seraphim on 2007-07-29
maybe you could remove the package and reinstall it.

---

### Post by DeusEx on 2007-07-29
Hello!

```
[ 49.086304] kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)
```

I would assume here GRUB tries to load linux from hd(0,0) which means (primaryharddisk,firstpartition). this obviously isn't correct because your ubuntu disk is slave.

For the orher problems: Perhaps running an LTS version would be more stable, like 6.06.
And just for being sure: are both your harddrives 100% ok?

You could read detailed (error-)logs by typing in the terminal:
```
dmesg
```
and
```
cat /var/log/syslog
```

Side note: you tell us you're not experienced. That means you probably will have to learn by making mistakes and having patience. So take small steps and enough breaks :)

---

### Post by ugm6hr on 2007-07-29
I know that reinstalling is the last thing you want to do, but it may actually save time in the long run.

But a question first:
Did the Ubuntu7.04 LiveCD run without any problems?  If so - there should not be major problems with installing it, unless you have a hardware problem.

Then restore the Windows bootloader (to ensure that wiping Ubuntu is not going to leave you without a working computer:
[http://ubuntuforums.org/showpost.php?p=3070095&postcount=7](http://ubuntuforums.org/showpost.php?p=3070095&postcount=7)

Then just wipe the slave drive completely with:
[http://www.killdisk.com/](http://www.killdisk.com/)

Then reboot with the LiveCD (whichever you want i386 / AMD64), and install again.  Then perhaps use it *without* any of the updates for a bit.  And stay away from any beta software (e.g. Beryl etc) for the time being.

The updates *shouldn't* be the cause of the problems - unless it's the new kernel update - so just steer clear of that until you know what you're doing.

---

### Post by russo.mic on 2007-07-30
I'd be willing to bet and eyebrow that you didn't format the partitions you HAD created to install ubuntu on the first time.  you've reinstalled over the old install.  THAT CAN CAUSE problems.  

I think the original problem here was uninstalling 64-bit ubuntu because flash won't work.  Mainly because it will.  these forums are your friend.  check here first.  a quick search of Flash in the 64-bit section would have given you step by step instructions on what to do.  

Don't lose hope.  you'll be up soon enough.  Just be calm, and tackle these problems one by one.  Remember, no matter how obscure your problem might be, there has probably been someone else who has sat behind there computer and gotten just as frustrated at the exact same thing.  Just hope they posted.  

Good luck!

Russo

---

### Post by asmoore82 on 2007-07-30
have you tested the RAM in this machine

---

### Post by RedGecko on 2007-07-30
First, I'd like to thank you all so much for your help!

I did wipe both harddrives completely before re-installing the last time. 
I'm not sure what more formating my HD needs before re-installing Ubuntu (I figured It'd format itself in the install)

I tested my memory and it is corrupted (good idea, thanks)
It's a good thing Crucial offers a lifetime warranty on my memory...
My new memory is on the way. :)

I have some questions though, for when I do the re-install. Why should I steer clear of kernel updates? What more should I know before updating this? What other types of updates do I need to know about? I assumed that suggested updates from the Update Manager would all be safe. I suppose that assumtion was wrong, so what do I need to know about before updating?

A little bit after I made my last post, my computer became completely unstable and nothing I clicked on would work, or really do anything. 

I've re-installed ubuntu and left it as-is. (I'm on my work computer right now)
If anybody has any suggestions as to what I should do differently this time, please tell me! I don't want this to happen again.
THANKS!!!

---

### Post by F_r_e_d on 2007-07-30
Maybe you should try some other flavor of Linux.  I have had, and continue to have, frustrating times with Ubuntu, but the more I learn, the easier it gets to solve problems.

I have 2 hard drives, one of which is loaded with XP.  The other is loaded with Ubuntu.  XP is still my main workhorse (sigh); when I can, I work in Ubuntu and try to give myself as much time as needed to resolve problems.  I don't put myself on a timetable, and it helps to ease the frustration.  Give Ubuntu/Linux as much time as it needs.  If it takes a couple years to learn, then give it that much time.  Take some classes in Linux if they are offered locally.  Go the to library and get books on Linux.  Join a local Linux group.  In the meantime, keep working with Windows too.

Don't rush Linux.  Remember, you are learing a new language -- a new way to do things.  Think how long it took you to learn and use Winblowz.  At least give Linux equal time!!  Some day, you and I will both have the confidence to say goodby to Winblowz forever!

---

### Post by Logical Dream on 2007-07-30
> **F_r_e_d said:**
> 

Don't rush Linux.  Remember, you are learing a new language -- a new way to do things.  Think how long it took you to learn and use Winblowz.  At least give Linux equal time!!  Some day, you and I will both have the confidence to say goodby to Winblowz forever!

WORD !

---

