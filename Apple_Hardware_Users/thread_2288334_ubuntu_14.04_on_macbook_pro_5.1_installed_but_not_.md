---
title: "ubuntu 14.04 on macbook pro 5.1: installed but not booting"
date: 2015-07-26
forum: Apple Hardware Users
---

### Post by paula3 on 2015-07-26
hi there,

after some hours fiddling with burning bootable usb drives, refind, nomodeset... i managed to get live ubuntu 14.04 to install on my macbook pro 5.1. installation went fine but now i don't manage to boot it. 

it freezes in a purple screen very quickly. i tried removing 'silent splash' options from the boot to try to see what was going on, but to no avail, only purple screen.

recovery mode freezes at [0.882541] ehci-pci 0000:00:04.1: irq 22, io mem 0xdf489200, but i attach a photo of the screen, in case someone sees a enlightening message.

help???
many thx in advance

---

### Post by este.el.paz on 2015-07-29
> **paula3 said:**
> hi there,

after some hours fiddling with burning bootable usb drives, refind, nomodeset... i managed to get live ubuntu 14.04 to install on my macbook pro 5.1. installation went fine but now i don't manage to boot it. 

it freezes in a purple screen very quickly. i tried removing 'silent splash' options from the boot to try to see what was going on, but to no avail, only purple screen.
help???
many thx in advance

Paula:

I have LM 17.1 installed on my MBPro 5,4 . . . didn't need any boot params . . . .  How did you run your install? Dual boot?  You did install refind?  Do you use "automatic" or "manual"??  Did you check the md5sum number of the iso?  Possibly, try to run the install again???  General wisdom seems to be do dual boot . . . didja go that way?

e..

---

### Post by paula3 on 2015-07-31
Lucky you :), i tried 4 different distros before i managed to enter install  (including LM, though I confess I don't remember the version but I bet it was the last one; it didn't even enter install and stopped with a blinking cursor in a black screen). I only managed to enter the installation process with Ubuntu 14.04, after I added nomodeset to the boot parameters, which hints me the linux distros I tried disliked my graphic card. 

Yes I did install refind and it is dual boot. I don't understand your question about "automatic" vs. "manual". If you mean the installation, after I added nomodeset everything else was automatic. After trying with 4 different distros and not managing, you can guess i'm not that fond of the idea of simply running the install again, i rather prefer to understand what is going on (graphic card incompatibility?)... As the OSX boot is running fine, I didn't tried the Linux boot again since then[COLOR=#000000]*.  *[/COLOR]

---

### Post by Votlon on 2015-07-31
I had this same issue, 

I installed 15.04 with nomodeset and it fixed it.

---

### Post by este.el.paz on 2015-08-01
> **paula3 said:**
> Lucky you :), i tried 4 different distros before i managed to enter install  (including LM, though I confess I don't remember the version but I bet it was the last one; it didn't even enter install and stopped with a blinking cursor in a black screen). I only managed to enter the installation process with Ubuntu 14.04, after I added nomodeset to the boot parameters, which hints me the linux distros I tried disliked my graphic card. 

Yes I did install refind and it is dual boot. I don't understand your question about "automatic" vs. "manual". If you mean the installation, after I added nomodeset everything else was automatic. After trying with 4 different distros and not managing, you can guess i'm not that fond of the idea of simply running the install again, i rather prefer to understand what is going on (graphic card incompatibility?)... As the OSX boot is running fine, I didn't tried the Linux boot again since then[COLOR=#000000]*.  *[/COLOR]

@p3:

What graphics card?  Also upon further reflection I also have had some "issues" with the "ubuntu" flavor, so consequently I use Xubuntu, or Lubuntu, or in LM I use the MATE flavor . . . it might be that "ubuntu" is a tad demanding on resources, so I would try for Xubuntu . . . there might be a "mac" version, but possibly the "amd64" for "64 bit" system might be right for MBP??  And, then you didn't answer about the md5sum number to check if the downloaded file is clean or corrupted.  

Automatic or manual are the choices you make when you decide to do the install, "install alongside" is the "automatic" OR "something else" is the "manual."  So, if you aren't getting a "GRUB" window to show up in the boot process then even if it said "install successful" . . . it isn't.  If you did "automatic" and it didn't set up GRUB properly, then . . . two things, find the "Supergrub2" iso and burn it to CD and try to use SG2 to boot your install--you might be able to "repair GRUB."  If that doesn't work, try Xu or Lu . . . LiveDVD (check md5sum) and run the install as "manual" and then use GParted to set up at least 3 partitions, small 10MB labeled "bios_grub" . . . whatever you want for "home" flagged as "/" and formatted as "ext4" . . . and then 1-2x RAM for swap . . . and run the install again . . . after wiping the previous install.  

After install, shut down the computer (did you do that after your first install?) and then on reboot you should get rEFInd window showing you the options, select "windows" or whatever is showing penguin . . . and then it should take you to GRUB window, and then the splash . . . .  It doesn't take too long to do a "nuke n pave" and sometimes saves time rather than "trying to find out what the problem is" . . . .

As far as what "volton" said about 15.04, that may be right, but I still prefer LTS version (14.04) so that you don't have to go through the install process in 6 months or whenever support ends . . . with LTS you have years of support.

e..

---

### Post by paula3 on 2015-08-01
> What graphics card?

MBP 5,1 comes with 2 graphics cards: NVIDIA GeForce 9600M GT 512 MB and 9400M. In OSX I use the first one as it is more performatic. I don't know which one Linux will pick you when trying to install, I only guess (but would be happy if someone could confirm or correct) that it uses whichever card OSX has set up.  

> And, then you didn't answer about the md5sum number to check if the downloaded file is clean or corrupted. 

it was clean.

> Automatic or manual are the choices you make when you decide to do the install, "install alongside" is the "automatic"
 
it was automatic.

> So, if you aren't getting a "GRUB" window to show up in the boot process then even if it said "install successful" . . . it isn't. 
 
oh I did get a GRUB window, which was very annoying because it overwrote refind and I couldn't boot either in linux nor in OSX, both ended up broken. I've read some posts of corrupted GRUB installations on Macs but the fixes I've found didn't work for me. I had to burn a boot-usb with refind to have my MBP alive again... After that I could boot on both systems but Ubuntu would hang on the purple screen.

> After install, shut down the computer (did you do that after your first install?) 

Well, yes I did. I said the OSX boot was doing fine :). 

>  It doesn't take too long to do a "nuke n pave" and sometimes saves time rather than "trying to find out what the problem is" . . . .

I've already spent quite some time trying the several distros blindingly. I doubt that reinstalling a version that didn't work will save me time ;), I'd rather go with other suggested distros/versions then.

So with both your suggestions, I sum up that I should try:

- 15.04
- [X/L]ubuntu 
- LM Mate

I'll give it a try and report back! Thanks.

---

### Post by este.el.paz on 2015-08-01
> **paula3 said:**
> > What graphics card?

MBP 5,1 comes with 2 graphics cards: NVIDIA GeForce 9600M GT 512 MB and 9400M. In OSX I use the first one as it is more performatic. I don't know which one Linux will pick you when trying to install, I only guess (but would be happy if someone could confirm or correct) that it uses whichever card OSX has set up.  

oh I did get a GRUB window, which was very annoying because it overwrote refind and I couldn't boot either in linux nor in OSX, both ended up broken. I've read some posts of corrupted GRUB installations on Macs but the fixes I've found didn't work for me. I had to burn a boot-usb with refind to have my MBP alive again... After that I could boot on both systems but Ubuntu would hang on the purple screen.

> After install, shut down the computer (did you do that after your first install?) 

Well, yes I did. I said the OSX boot was doing fine :). 

>  It doesn't take too long to do a "nuke n pave" and sometimes saves time rather than "trying to find out what the problem is" . . . .

I've already spent quite some time trying the several distros blindingly. I doubt that reinstalling a version that didn't work will save me time ;), I'd rather go with other suggested distros/versions then.

So with both your suggestions, I sum up that I should try:

- 15.04
- [X/L]ubuntu 
- LM Mate

I'll give it a try and report back! Thanks.

P3:

Yes, try those options, go with what "works" for your computer.  The "GRUB overwriting thing seems strange" . . . possibly indicating a "corrupt" GRUB install, which suggests trying "manual" install to provide a "place" for GRUB to call "home." 

Hard to say whether two graphics cards is causing a problem for linux . . . it was very complicated to get a running linux install on my '02?? iMac PPC because of possible ports for displays . . . needed an xorg.conf file set up.  So far I haven't needed an xorg.conf file for my '09 MBPro . . . but, if you can get to a GUI you might need to check "additional drivers" to get drivers for the cards . . . cart, horse, etc . . . .

In terms of "hours spent on linux" . . . yes . . . many hours can be thrown into it . . . it's all for sh**s and giggles . . . enjoy the process.  It does help the appreciation for the rock solid management of apple machines by OSX . . . but, that can be "boring" . . . .  Once you get a running linux install, check the "mactel threads" at the top of the aple sub-forum . . . you might need some "macfanctrl" to keep things cool . . . . 

e..

---

### Post by paula3 on 2015-08-01
For the sake of completeness, I report here my (failed :( ) attempts for today. 

Ubuntu 15.04 won't manage to start up the install, hanging in the process. At some point i noticed the error message was similar to my installed-but-not-booting 14.04 system. A bit of trial and error has shown me that the behaviour of the failed linux booting was different depending on which graphic card is set to be default in OSX. A bit more of googling and I located this:
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty) 
which indeed points to issues with the 9600 graphic card, and the need for some manual config in ubuntu that i didn't feel like facing. 

I gave LM another try, v. 17.2-cinnamon-64bit (because i already had the iso here). I was prepared for the problem with graphic card:
[http://jdlovering.blogspot.com.br/2013/10/installing-linux-mint-15-on-macbook-pro.html](http://jdlovering.blogspot.com.br/2013/10/installing-linux-mint-15-on-macbook-pro.html)

LM installed without issues, similar to ubuntu 14.04, but:
- LM installation also overwrote refind and OSX wouldn't boot anymore (*sigh*). 
- default LM boot hangs with some color stripes in the screen; nouveau.modeset=0 won't do the trick, it does load a bit more, I hear HD reading and a chime, then... black screen. 
So a similar behaviour to my installed-but-not-booting 14.04, which I guess is not surprising given that LM is Ubuntu-based.

I got my OSX alive again following the tip found here, [http://apple.stackexchange.com/questions/155814/grub-overwritten-refind-mac-bootloader-unable-to-boot](http://apple.stackexchange.com/questions/155814/grub-overwritten-refind-mac-bootloader-unable-to-boot), namely: 
In the grub menu hit c for command line. Just typed exit & immediately I was popped back onto refind. Immediately booted into OS X & reinstalled refind.

Enough of trying to install Linux on my MPB5,1 for some (several) days ...

---

### Post by este.el.paz on 2015-08-02
@P3:

Continue to endeavor to persevere . . . still remains "odd" that "rEFInd" is being "overwritten" if it is installed in OSX as per "rodbooks" instructions to "drag .sh file" to open Terminal window in OSX???? and hit return, which should give a folder in OSX side . . . which shouldn't be touched by linux install???  Indeed, any update to OSX will "break" the rEFInd "blessing" . . . and so it needs to be "re-blessed."

But, there has been some "issues" lately with "systemd" or something like that, or with the installer and that might be what is causing such problems, other than the two video cards.  I've sort of gone to giving the suggestion to use Parallels or VMFusionware as the **safest*** method to running linux . . . inside OSX, that way no worries about "over heating" and so forth . . . .

And, again, I didn't see any mention of Xu or Lu . . . and in the LM dept, no surprises on Cinn not really working, for my 09 MBPro Cinnamon has been very "Sid-like" . . . whereas MATE has been just fine . . . .  It'll all be there whenever you get around to messing with it.

e..

---

### Post by paula3 on 2015-08-02
thank you a lot for your attention @este, but I did run out of time for this right now. i have both linux and mac at work (separate machines) and this dual boot was only an experiment with an old laptop at home. the refind being overwritten is well known, just google "grub overwrite refind" for you to have an idea. I'm sorry but I doubt that variations of Ubuntu-based system will behave any different than what I experienced so far, the issue with the graphic card relates to drivers at the base system level. But fair enough, i haven't tried Xu nor Lu, i confess I don't have much patience for trial and error (and i did run out of time). if i have time for this later on i'll either try the detailed configuration at the ubuntu link I posted above (specific for mbp5,1), which I was lazy to face yesterday :-P, or I'll go for a hardcore debian distro, their community is pretty technical and should known how to handle the driver easier than our trial and error method (imho).

---

### Post by este.el.paz on 2015-08-02
P3:

No worries, I'm not holding my breath on it . . . as it does take time to play around with finding a system that will run.  On the "technical expertise of debian sites" . . . yes, the debian guys may be more "purist" and technically competent, but, that can be a double edged sword.  Over the last 4 to 5 years I've been kicking around on various forums while trying to find something to keep my old PPC computers running.  And, indeed you can find replies from people who can give very precise CLI fixes to your (mine) problems . . . but, they can also be "dismissive" to newbies as well, to the point of being insulting . . . from my personal experience and IMHO as a newbie.

Also, if your suggestion to not bother with various iterations of ubuntu based on "base system being the same" . . . that argument goes double for Debian, as, <drum roll plz> . . . ubuntu is based on Debian!!!!!  It seems that you are a knowledgeable computer person, and, generally I am not; but I have run a lot of installs on a range of systems and that is why I can comment about installs . . . .  But, I'm not reading all of your links, as I've posted the same basic info here many times--i.e., trying the "manual" install and setting up the "bios_grub" partition as a key point on getting GRUB properly installed . . . .  As all of linux is DIY, mostly we are on our own, and that is where the time consumption comes in . . . and that is why I lean to ubuntu Xu/Lu & LTS.  Generally if I could boot a LiveDVD w/o boot params the install should go OK . . . but again, try the "manual" option on one of those Xu or Lu or MATE flavors . . . .  

Finally, you can see that on the Apple sub-forum the speed of replies and depth of comments is far behind that of the main forum, and I have pointed that out on the forum comments sub-forum, but the mods keep moving any posts about apple hardware over to this forum . . . and seemingly the guys with the technical chops for most of the ubuntu issues aren't posting here . . . so you get moi.  : - 0  Might be something about your MBPro that might need special handling, and might have been found and talked about here before???  OR, search other iterations of linux to find the one that goes in easy, possibly OpenSUSE, or possibly straight Debian . . . someone on the Debian forums said that "BSD is the best for apple hardware" . . . but, the install is more "complicated" for a non-technical computer person like me, might be easy for you . . . I think you have to go into open firmware, and I tried I think "FreeBSD" one time and it did wipe out my linux install or something, so you have to have "back ups" . . . .  Enjoy your search.  


e..

[Edit: Thought about this later, but, you could go back and try 12.04 LTS, I'm still running 12.04 on my PM 3,1 and I just got some updates this weekend, so it's still getting "support."  12.04 installed very easily, no xorg.conf files, sound works . . . if it works then that is better than having a system that doesn't.]

---

