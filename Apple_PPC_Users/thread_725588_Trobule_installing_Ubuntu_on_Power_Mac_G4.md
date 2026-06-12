---
title: "Trobule installing Ubuntu on Power Mac G4"
date: 2008-03-15
forum: Apple PPC Users
---

### Post by Belfielder on 2008-03-15
Hey,

Hoping someone might be able to help me! I have an old Power Mac G4 "Quicksilver", 800Mhz, 512 RAM, OSX 10.2.8. It's been passed down to me without any passwords or original installation discs. My grand plan is to wipe it and install a newer Mac OS. To do that, I've been advised to install Ubuntu as a second operating system, which could then wipe OSX 10.2.8 and then wipe itself (is that correct?).

I've downloaded Ubuntu 6.06 but for the life of me cannot get the Mac to boot it. I've searched around the forums for advice (notably: [http://ubuntuforums.org/showthread.php?t=65122](http://ubuntuforums.org/showthread.php?t=65122)). I've done the Apple-Alt-P-R sequence while rebooting and the damn computer still won't boot from the Ubuntu CD. Any advice on how to install Ubuntu would be most welcome!

---

### Post by ljonesj on 2008-03-15
i was the same way you are just continue hit c. it should boot hope your cd/dvdrom is newer mine did not like the disk unless i used one of my drives out of my other ubuntu machine that is x86.
also if you want to run 7.10 do what i did i used 7.04 installed the programs i wanted and dvd playback installed xubuntu with it then did the upgrade after all my updates and i got mp3 playback working. it rebooted and did not have any problems like others have had dont know why either was ready to make changes to get it to work

---

### Post by Belfielder on 2008-03-15
I've tried rebooting and hitting c over a dozen times now, and the cd still isn't booting! Any other suggestions?

---

### Post by ljonesj on 2008-03-15
if you have a newer cd/dvd drive change that out i find most of my problems come from trying to use the older optical drives

---

### Post by Belfielder on 2008-03-15
I don't have another CD/DVD drive to use. I think it's recognising the CD fine. When Mac OS boots up and I insert the CD, it opens it in Finder and I can see all the files. The computer just won't boot from the CD. I put the CD into a Dell PC, and it worked perfectly there, began the installation process and all. I'm completely stumped!

---

### Post by ljonesj on 2008-03-15
that was my problem the old drive saw and opened the disk in os9.2.2 but it would not boot it so i changed the drives and now it booted when i hit c i hate tell you this but either get another optical drive or borrow the one from the dell if you can and put it in the apple for a test

---

### Post by Belfielder on 2008-03-15
Thanks for your help - I'll see if I can scrounge an optical drive from somewhere

---

### Post by Belfielder on 2008-03-15
Ah! I got it working. Apparently I had downloaded the incorrect version of Ubuntu for my Mac - sorry! Such a stupid mistake that's cost me hours of head-scratching!

---

### Post by ljonesj on 2008-03-15
no problem it can happen i had never used the newer types of apple last apple i used was the old apple 2 and the first macs that came out this is my first powerpc apple and i had no idea how to boot it to cd at all untill iasked 3 days ago

---

### Post by Belfielder on 2008-03-15
Dammit, I've another problem now. I had downloaded Kubuntu, and it (apparently) installed successfully. However, when it goes to boot, the loading bar doesn't move at all and after a few minutes it changes to a black command-prompt type screen. I'm in way over my head here! Any ideas???

---

### Post by ljonesj on 2008-03-16
yeah i do try these comands from known problems
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

this should help u i got mine working by upgrading through 7.04 i did updates then installed the dvd playback then the different codecs for different video and mp3 playback vlc media player then i installed xubuntu-desktop then i upgraded the distro through the upgrade manager and it worked its way through the upgrade it then rebooted it just worked i tried it before and got the same problem u did but i think the xubuntu install done the trick dont know for sure

---

### Post by Kasa on 2008-03-23
when booting hold down 
Option+apple+o+f

once in that prompt (also if that wont boot try not touching a mouse or moving the mouse)

type in 
```
boot fw/node/sbp-2/disk:,\install\yaboot
```

I am not sure, if that will help but I dont know the root location of the internal CD drive :?.
but when in the openfirmware prompt maybe try boot cd :?

I dont know play about with it, something should work.

---

### Post by slacka-vt on 2008-03-25
can you get to a terminal ?
if so,
try to install the default ubuntu desktop like such:
in terminal type:

sudo apt-get update
sudo apt-get install ubuntu-desktop

happy to help more if need be
~s

an alternative which may be advisable for your system configuration is
installing the Xubuntu desktop, it uses less cpu and ram

sudo apt-get update
sudo apt-get install xubuntu-desktop

~s

---

### Post by blg on 2008-03-26
I have a recently acquired G4 "Digital Audio", 533MHz, ATI Rage 128

Was having similar problems installing xubuntu-7.10-desktop-powerpc. It just wouldn't work.
Tried xubuntu-7.10-alternate-powerpc, it started the install then hung for a while, I let it sit for an hour or so and it finally finished the install.
I rebooted, it looked like it was going then hung with a black screen.  I let it sit there for about 10 minutes then was rewarded with a BusyBox prompt, with which I had no clue what to do.

This evening I found help here:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Basically, I booted back to my BusyBox prompt and ran:
```
modprobe ide-core
exit
```

as suggested and am now proud owner of a G4 running xubuntu.

---

### Post by stream303 on 2008-03-27
> **blg said:**
>  I let it sit there for about 10 minutes then was rewarded with a BusyBox prompt, with which I had no clue what to do.

This evening I found help here:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Wow, that is interesting that it took that long for it to give up and give you a busy-box prompt.  Good to know, and glad you had the patience!  I probably would have written it off too soon.

---

