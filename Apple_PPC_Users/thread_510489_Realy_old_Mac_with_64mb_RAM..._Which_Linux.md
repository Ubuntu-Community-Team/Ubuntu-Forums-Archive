---
title: "Realy old Mac with 64mb RAM... Which Linux?"
date: 2007-07-26
forum: Apple PPC Users
---

### Post by waggygee on 2007-07-26
I have a realy old Mac, it ran OS9... It has 20gb HDD... oh, and 64mb RAM.
I tried OpenBSD and YellowDog4.1 but for some reason they did not boot (both had successfully installed)... Any suggestions on what distro of linux I could try? I basically would like to use the computer for web browsing and instant messeging

---

### Post by gvigorus on 2007-07-26
My 2 cents would be to try Xubuntu. They say it's really good on old hardware:  [www.xubuntu.org](www.xubuntu.org)

Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

---

### Post by madmetal on 2007-07-26
> **waggygee said:**
> I have a realy old Mac, it ran OS9... It has 20gb HDD... oh, and 64mb RAM.
I tried OpenBSD and YellowDog4.1 but for some reason they did not boot (both had successfully installed)... Any suggestions on what distro of linux I could try? I basically would like to use the computer for web browsing and instant messeging

debian with minimal installation or xubuntu? 
what about cpu ?

---

### Post by waggygee on 2007-07-27
> **madmetal said:**
> debian with minimal installation or xubuntu? 
what about cpu ?

Its a G4 (PCI) 400mHz..... To tell the truth, I think there is a problem with my yaboot (but I'm not sure) is there anyway of 'testing' if its running proberly?

---

### Post by pxwpxw on 2007-07-27
If you are seeing a yaboot text menu and boot prompt at restart,  there are some things to try.
If not, then there may have been a problem with the install.
Using a server or command line installation (no graphics) will use minmum RAM, but 64MB is a bit light for graphics desktops, but you can be selective about what install. Booting to a root console here in ubuntu uses about 37MB memory (text only), desktop is using around 400MB.  An old mac with 140MB ram works - slowly.

---

### Post by waggygee on 2007-07-27
> **pxwpxw said:**
> If you are seeing a yaboot text menu and boot prompt at restart,  there are some things to try.
If not, then there may have been a problem with the install.
Using a server or command line installation (no graphics) will use minmum RAM, but 64MB is a bit light for graphics desktops, but you can be selective about what install. Booting to a root console here in ubuntu uses about 37MB memory (text only), desktop is using around 400MB.  An old mac with 140MB ram works - slowly.

I dont think I'm seeing the yaboot text, I think it doesn't start yaboot up. I see that Mac logo changing into a question mark and back again in a blue folder in the middle of the screen, then a few seconds later text comes up in the top left corner some Openwire stuff and instructions to boot Mac by typing 'mac-boot' or reboot. The installs say they were successful but I noticed when Yellowdog was finishing up some text popped up saying 'frame buffer ioctl. failed' but it continues.
I noticed when I boot of my Ubuntu Feisty LiveCD I get a list of things I cant do (install, memtest, boot of first harddrive or something like that), what I would like to know is do I get that screen with the Xubuntu liveCD as well? I ask this so I can use the  liveCD to boot since at appears as if yaboot is "sick"

---

### Post by ajmctaggart on 2007-07-27
You may wanna check out my post on how I got a pretty quick desktop out of an old Powerbook Pismo I had...still w/ 64MB ram, that'll run slow either way, but this is as barebones as you can get...

[http://ubuntuforums.org/showthread.php?t=511293]("http://ubuntuforums.org/showthread.php?t=511293")

---

### Post by ev5unleash1 on 2007-07-27
You cannot install Ubuntu on any Power PC processor it has to be intel based. I'm not sure what will happen if you try it but i know that for a fact.

---

### Post by ajmctaggart on 2007-07-27
ev5unleash1, you're nuts...

PPC and ubuntu do work, just not x86 specifics like ndiswrapper, picassa, etc...

PPC is being supported now by the Ubuntu Community, I've got about a half dozen different Feisty Disks burned right now, with Kubuntu, Ubuntu, Xubuntu, Server...

Just though you should know...

---

### Post by ajmctaggart on 2007-07-27
I'm sorry, it just dawned on me that this is the Apple PPC Users Forum, what in the name of...well Ubuntu, would make one think that you can't install Ubuntu on a PPC chip?


You can install Ubuntu onto a PS3 if you are willing...you can install it onto a HP Ipaq pda, you can install it on many other platforms.

Where did this Computer/Server/C++# builder get this notion from...

Im done, sorry...

---

### Post by waggygee on 2007-07-27
> **ev5unleash1 said:**
> You cannot install Ubuntu on any Power PC processor it has to be intel based. I'm not sure what will happen if you try it but i know that for a fact.

I know your trying to be helpful... but are you sure about this? because I have read otherwise from numerous other threads and forums

---

### Post by ajmctaggart on 2007-07-27
> I know your trying to be helpful... but please read up a bit

Like the name of the forum...

---

### Post by stmiller on 2007-07-27
> **ev5unleash1 said:**
> You cannot install Ubuntu on any Power PC processor it has to be intel based. I'm not sure what will happen if you try it but i know that for a fact.

Rumors that everyone thinks, sadly enough. There were countless news articles incorrectly stating that 'Ubuntu DROPS PowerPC!' which should have said, 'Ubuntu drops paid commercial tech support for PowerPC.'

Oh well what can you do?  :(

---

### Post by ajmctaggart on 2007-07-27
As if I don't have a hard enough time getting my macs to do what I want to w/ ubuntu...now we gotta explain in the PPC Forum that you can install Ubuntu onto one!

Exactly, what can you do?  Ill just bury myself deeper into the PPC Forums, since Ubuntu is for PPC.  They don't make it for x86, do they? :)

Oh how I love Friday in the forum...

---

### Post by Midwest-Linux on 2007-07-27
> **ev5unleash1 said:**
> You cannot install Ubuntu on any Power PC processor it has to be intel based. I'm not sure what will happen if you try it but i know that for a fact.


I cannot install Ubuntu/Kubuntu PPC desktop and alternate CDs on my G3 Mac blue tower 300 Mhz 3.6 HD 384 ram, Mac OS9.0, its been nearly a week, many burned ISOs, countless command prompts, 3.6 battery change, time and date update, software update, many late hours,many days,many nights and of course many posts. Mac OS 9.0 works fine, the CD-ROM works fine, it even connects to the internet. Install ubuntu/Kubuntu ? Cannot do. 

I know others have successfully installed it, I must have one of those machines that will not take it.

---

### Post by waggygee on 2007-07-27
Huh.... Fellow Linuxians.... I think this topic is straying from it's original purpose.... I believe all well informed people know Ubuntu can run on a PPC.... my question was which can run on a PPC with only 64mb RAM, Im looking into Xubuntu now, Ill update this forum as soon as I found anything

---

### Post by waggygee on 2007-07-27
> **Midwest-Linux said:**
> I cannot install Ubuntu/Kubuntu PPC desktop and alternate CDs on my G3 Mac blue tower 300 Mhz 3.6 HD 384 ram, Mac OS9.0, its been nearly a week, many burned ISOs, countless command prompts, 3.6 battery change, time and date update, software update, many late hours,many days,many nights and of course many posts. Mac OS 9.0 works fine, the CD-ROM works fine, it even connects to the internet. Install ubuntu/Kubuntu ? Cannot do. 

I know others have successfully installed it, I must have one of those machines that will not take it.

This is the definition of forum poaching! Anyway, earlier in this thread I was told to try Xubuntu. Maybe you can try it too. What happens with you? Does it boot up the LiveCD? and what happens when you try install? Have you got yaboot or bootX?

---

### Post by pxwpxw on 2007-07-28
When you install using the Desktop (Live) CD, it gives very little feedback and control over the installation. Sometimes there is a problem with installing yaboot at the end of the installation. The install is completed except for yaboot, so restart fails, and there is little indication of what happened. One way to sort this out is by re-running the install CD in rescue mode.

If you do the install using the Alternate or Server version, you  have more control and information during the install, making it easier to avoid or see problems. You can still do a rescue using either the Alternate CD or the Live Desktop CD if you can run it.

The Alternate CD also comes with /Doc - Ubuntu Installation Guide

---

### Post by bodycoach2 on 2007-07-28
> **ev5unleash1 said:**
> You cannot install Ubuntu on any Power PC processor it has to be intel based. I'm not sure what will happen if you try it but i know that for a fact.

Wow! I thought I had two iMac G3 333 MHz running Xubuntu. I thought they ran pretty well. I guess it was completely my imagination. I will seek mental health counselling.

---

### Post by webaake on 2007-07-29
Got Ubuntu 7.04 running fine on an Apple Macintosh Powerpc G4, with a RISC processor by Motorola, (intel outside).

But, to be seriuos, if you need more RAM search Ebay for PC100(100Mhz) SDRAM 168-pin, preferrably 'single sided'. They're cheap and easy to insert. The more RAM the better!

---

### Post by waggygee on 2007-07-30
Ok... I successfully installed and booted Ubuntu Feisty Fawn Sever Edition, I am installing all of the basic windows managers and web browsers and the like.... Thanks everyone!!!!!!!!!:guitar::)

---

### Post by ajmctaggart on 2007-07-30
Waggypee, Congratulations!  I am glad we could have helped you...Let me know what your setup is, as far as desktop managers and apps you are gonna use...I'd like to know how well the iMac responds,,,


Thanks,
ajm

---

### Post by Midwest-Linux on 2007-07-30
> **waggygee said:**
> This is the definition of forum poaching! Anyway, earlier in this thread I was told to try Xubuntu. Maybe you can try it too. What happens with you? Does it boot up the LiveCD? and what happens when you try install? Have you got yaboot or bootX? Forum poaching?  I was looking for solutions for trying to install ubuntu on my G3, been attempting installation for over a week.... I am going to shelve this project...I wasted enough of my time....

---

### Post by ajmctaggart on 2007-07-30
Midwest_Linux,

I'm sure it was just a joke, please, if you need help, just start a thread w/ as much info as you can supply, and we will all try to help you...


Please let us know how we can help,
ajm

---

### Post by ajmctaggart on 2007-07-30
Midwest_Linux- 

Just read your other posts, sorry we couldn't have helped you more.  To be honest, everyone has issues w/ old macs, I think it's all in the way/type/speed one burns the disk...Just my opinon


If you ever want to try again, let me know...

There are ways to install through a network too, so if you ever wanted, we could point you in the right direction...


thanks,ajm

---

### Post by waggygee on 2007-07-30
Midwest, the forum poaching thing was a joke. Im sorry to hear you having problems with your install and I really hope you don't give up, I would suggest you start a new thread and explain in full the problem you've got (Im no expert but I believe your Mac is Old World so it would need bootX instead of yaboot). Iread a little about old Mac installations and I would suggest you look into Yellowdog3 (I havent tried it though), I hear that starts with bootX, best of luck

AJM, I hav'nt installed much just Firefox, IceWM, Fluxbox, Synaptic, XDM and XFCE (the file manager, Im not sure if thats right).......... As you can see I have IceWM and Fluxbox, I just trying out different things till I find something that feels right. Oh, and how do I get the flashplayer9 installed for Firefox? I downloaded it already

---

### Post by ajmctaggart on 2007-07-30
Don't know about Flashplayer, other than a lot of people talking about Gnash...maybe some googling and another Ubuntu Forum?

Glad to hear things are going well...


ajm

---

### Post by Auria on 2007-07-30
There is no adobe flash player 9 for PPC linux

See PPC FAQ, you can use gnash wich works approximately okay for some websites and most ads, and you can get videos from youtube and similar sites using firefox extensions

---

