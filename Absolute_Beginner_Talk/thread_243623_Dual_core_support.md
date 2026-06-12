---
title: "Dual core support"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by jrjr on 2006-08-25
.

---

### Post by Iarwain ben-adar on 2006-08-25
Hi,
the only thing i know about that, is that you'd normally use a SMP kernel (don't know what it stands for either :D )

So if your kernel is not an SMP type of kernel, you'd have to change it. 
(i don't know how to do that either, just trying to explain a liiiiitle bit :D )


Iarwain

---

### Post by jrjr on 2006-08-25
.

---

### Post by Iarwain ben-adar on 2006-08-25
Hi,
thanks :D

Well, i don't know if it's in the repo's, but you could always have a look for "smp kernel".

Normally you'd have to use the 2.6.15-26-[COLOR="Red"]686[/COLOR] i think...

But as always, i'm just saying, i THINK :D

If i were you, i'd wait for someone with more expertise on this subject ;)


Iarwain

---

### Post by jrjr on 2006-08-25
.

---

### Post by dca on 2006-08-25
...symmetric multiprocessing...  I want to say the Ubuntu 6.06 Server Ed offers SMP...

---

### Post by muep on 2006-08-25
Yes, it is.

It won't break. The package management system will install the new kernel beside the old one, so you can select the one you want at boot time.

After applying, reboot the computer. I think it should default to the SMP kernel, but if not, you need to select it when the computer boots.

---

### Post by jrjr on 2006-08-25
.

---

### Post by bulldog on 2006-08-25
I have an AMD X2 4600 and set a new kernel by this HowTo and no problems.

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

Maybe you can benefit from it too?

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by Iarwain ben-adar on 2006-08-25
Yes,
with a new kernel, you have to reinstall your gfx drivers etc.

It's a pain sometimes, but you can learn quite the thing while (re-)installing :D


Iarwain

---

### Post by Frank Golden on 2006-08-25
> **jrjr said:**
> I was unable to get my video working correctly with the 686-smp kernel. I went back through ATI config and all the procedures I normally do when I install. No joy.I had the big desktop... but the mesa drivers would not leave me alone!!

Booting back into the 386 kernal makes it work again.

Any thoughts?
Use this, the second method listed, follow exactly.

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Every time you change kernels you need to do this.
Hope you can get fixed the smp kernel is better. BTW the latest is 2.6.15.26 686smp so update before recompiling "fglrx".

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by Bachstelze on 2006-08-25
Well, basically all you need to do is get a 686-smp kernel installed and then reinstall your graphics driver. If you managed it once, I guess it won't take as much time the econd time ;)

---

### Post by jrjr on 2006-08-25
.

---

### Post by Bachstelze on 2006-08-25
Oh, my bad, I should have read the thread more carefully...

I can just tell you this : to get the latest 686-smp kernel, you have to install the **linux-686-smp** package.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by Frank Golden on 2006-08-25
> **jrjr said:**
> :confused:
Again,is the method you use to install the ATi drivers the one I linked you to? The latest kernel is the one I mentioned. You have
to refresh Synaptic and or update manager. Can you post your /etc/apt/sources.list file. If you have the correct entries in your sources.list your computer should have auto updated to the latest kernel by now. As a matter of fact I'm expecting a new
kernel any day now. If you want to use hardware acceleration (ATi
not Mesa) you have to install the drivers following the directions in the tutorial I linked you to. The second method listed uses the very latest drivers available. The code you posted is indeed the compiling part. There is a note there about
having to recompile after every kernel change. I have done this at every kernel update with no problems using this tutorial.
Make sure your restricted and universe repositories are available
like the tutorial tells you at the begining. If you follow
the directions to the letter you should't have any problems.
Basically copy and paste each command to the terminal in turn.
Pressing enter after each. 
You are using Ubuntu and not Kubuntu right?

---

### Post by jrjr on 2006-08-25
.

---

### Post by Frank Golden on 2006-08-25
> **jrjr said:**
> It is very similar. I spent many many hours finding something that worked for me. Finally I put together 2 different how tos that that makes my system work. I do not compile anything though... if that is what yours says to do. Thats why I asked. 

Here is what I have to do
[http://www.ubuntuforums.org/showpost.php?p=1310552&postcount=13](http://www.ubuntuforums.org/showpost.php?p=1310552&postcount=13)


Like I said before, I refreshed Synaptic and that was the one shown. 2.6.15.24



```
## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
# deb http://archive.ubuntu.com/ubuntu dapper-backports main
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

# deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# deb http://archive.ubuntu.com/ubuntu dapper-backports universe
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

# deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb http://www.getautomatix.com/apt dapper main

## created by automatixrepo3
```







Yes thats correct, Ubuntu
I guess I can try your video method but nothing else has ever worked for me in the past. If I wind up having to reinstall the OS though..... well guess I will face that when I get to it. 

Thanks for coming back and helping!

Check out this 

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

It is a tool to generate a sources.list based on you system setup. Cool.

Below is my sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) dapper main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates universe main restricted multiverse

I don't use Automatix but I do use EasyUbuntu. Read too much negative about
Automatix. Really today I either use Synaptics or will seek out a tutorial if I need something not in Synaptic. I have become more comfortable with
the command line in spite of my self.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by Frank Golden on 2006-08-25
> **jrjr said:**
> Even my original kernel is messed... video is wacked, fire fox quit working, lucky I had Opera installed....

What should I do?  Please!!
I wish I could tell you more. The ATi tutorial works for me always. From the details of your broken package it looks like you
tried to create a fglrx 386 kernel instead of the 686 one.
Also it appears that you at least have the latest 386 kernal (2.6.15.26 i386). You may have other issues with your Ubuntu install that is preventing you from installing ATi. Remove the broken package in Synaptic. Did you see errors while you were using tutorial. If you did you should have stopped and aborted. That is probably why the broken package.  If your going to format
try a fresh install of Ubuntu first and after updating and changing to the the 686smp kernel, try the ATi wiki method 2 again. Don't use Automatix first.

---

### Post by cjm5229 on 2006-08-25
Whenever you change Linux-images you also need to install the correct linux-headers and the linux restricted modules. if you search in synaptic for "linux" one of your choices should be "linux-686-smp" that should install all the modules with it. Once that is done reboot and set up your drivers and they should work.

---

### Post by dude051 on 2006-08-25
You are not compiling the kernel, you are compiling a kernel module. Big difference indeed.

Make sure and update to the latest 686 SMP kernel, by download the following packages using Synaptic Package Manager:
```

linux-image-2.6.15-26-686
Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP

linux-headers-2.6.15-26-686
Linux kernel headers 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP

linux-restricted-modules-686
Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.

linux-restricted-modules-2.6.15-26-686
Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
```

After this reboot into the new kernel image and goto [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") As Frannk and many other have said, this is the best guide around, use Method 1 if you dont want the latest drivers... although I strongly recommend Method 2. Follow it exactly step by step and it should go fine.

---

### Post by jrjr on 2006-08-26
.

---

### Post by jrjr on 2006-08-26
.

---

### Post by jrjr on 2006-08-26
.

---

### Post by jrjr on 2006-08-26
.

---

### Post by jrjr on 2006-08-26
.

---

### Post by jrjr on 2006-08-26
.

---

### Post by jrjr on 2006-08-26
.

---

### Post by dude051 on 2006-08-26
First off, you need to stop being so sarcastic and ungrateful to everyone here who are taking their time out to help you in spite of your rude and uncalled for replies to them. If you are so annoyed with our help, that is on behalf of our time, then go somewhere else, but please do not double post to another forum area. If you want to, move to another distro. Seeing your earlier comments you may just be happier on Windows XP.

Secondly, there was nothing wrong with your kernel install on your second hdd for Ubuntu. Oviously it was something on your part that you did wrong. 

> 
Well I tried your method. Now I have a broken package and messed up video.
How do I correct a broken package?

It's also obvious that there must have been errors at some point during any of these times you tried to install your ati drivers. Yet none were posted, except that you had broken packages. As Fred said, you need to give us more info.

> Even my original kernel is messed... video is wacked, fire fox quit working, lucky I had Opera installed....

What should I do? Please!!

This is because the linux kernel is a single component in a linux distro, only the kernel images themselves are independantly updated during the process. If you install a new kernel, and you screw up the drivers while using the new kernel, it screws up the drivers in the whole system. Updating your kernel is not an entire new install, just an update. This is also why you need to re-install the drivers after you update the kernel.

> What is the difference? Why did one work and not the other or how can I find out??????

Who knows? Based on the information provided, it can be taken as some incorrect packages mixed with user error that caused the broken packages on your Ubuntu install on the second hdd. Truth is, based soley on what you have posted with no error messages or indication to exactly what you have done, it is very hard to tell at all for certain...

If you feel the need to make more unnecessary lude comments to anyone else or me, try to keep them to yourself please.

---

### Post by jrjr on 2006-08-26
.

---

### Post by Frank Golden on 2006-08-26
> **dude051 said:**
> First off, you need to stop being so sarcastic and ungrateful to everyone here who are taking their time out to help you in spite of your rude and uncalled for replies to them. If you are so annoyed with our help, that is on behalf of our time, then go somewhere else, but please do not double post to another forum area. If you want to, move to another distro. Seeing your earlier comments you may just be happier on Windows XP.

Secondly, there was nothing wrong with your kernel install on your second hdd for Ubuntu. Oviously it was something on your part that you did wrong. 



It's also obvious that there must have been errors at some point during any of these times you tried to install your ati drivers. Yet none were posted, except that you had broken packages. As Fred said, you need to give us more info.



This is because the linux kernel is a single component in a linux distro, only the kernel images themselves are independantly updated during the process. If you install a new kernel, and you screw up the drivers while using the new kernel, it screws up the drivers in the whole system. Updating your kernel is not an entire new install, just an update. This is also why you need to re-install the drivers after you update the kernel.



Who knows? Based on the information provided, it can be taken as some incorrect packages mixed with user error that caused the broken packages on your Ubuntu install on the second hdd. Truth is, based soley on what you have posted with no error messages or indication to exactly what you have done, it is very hard to tell at all for certain...

If you feel the need to make more unnecessary lude comments to anyone else or me, try to keep them to yourself please.
Looks like he deleted all his posts. We must of upset him. Thanks for what you said. I only post about my experience. Folks should know that
"your mileage may vary" as the old car ads say. I can't control
the way the user takes direction either. 

BTW, I don't see where he double posted. Did he?

---

### Post by dude051 on 2006-08-27
I mean no harm as another user to him, it just irritates me thats all. It's all good.

And yes, he started two other post on this same topic about a day ago, even less on one, but has deleted those post too.

[http://www.ubuntuforums.org/showthread.php?t=243541](http://www.ubuntuforums.org/showthread.php?t=243541)
[http://www.ubuntuforums.org/showthread.php?t=244436](http://www.ubuntuforums.org/showthread.php?t=244436)

---

