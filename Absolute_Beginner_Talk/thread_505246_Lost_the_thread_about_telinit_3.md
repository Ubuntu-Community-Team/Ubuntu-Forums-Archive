---
title: "Lost the thread about telinit 3"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by msgmurph on 2007-07-20
Hello Everyone!!  I have been dabbling with Ubuntu for the last several months and I love it. However I do have a few issues to resolve to get everything working properly. Fortunatly I finally have some free time to try and fix things. I have a ton of questions and I don't know if I should ask them all in one post or split them up into separate posts. 
So my first question involves booting up. I have never been able to get Ubuntu to boot directly to the splash/login screen. Booting by turning on the computer causes the system to hang.  I found a post shortly after installation that advised booting into recovery mode and then running telinit3. Running telinit3 gets me to the login screen and  hen I can log in  normally ( at least I think thats what the normal login looks like.=)  At the login screen I can choose between Gnome, KDE, etc. The problem is I can't find the post that led me to the solution!  I'm going to keep searching for solutions in the Forums but if anyone has some pointers I would appreciate them.

After I get the boot process working properly I stlll have some issues.  
1 Get sound to work
2 Get DVD burner to work
3 Get multimedia to work ( I realize I might have issues as my CPU is an AMD64)

Some additional questions.


1 If I install an additional Hardrive how hard is it to make a backup partition to store my data on so that if I do break my system I can at least, hopefully, salvage my data?

2 Would it make sense to try the solutions on the previous versions of the kernel I have installed? I have been through 3 upgrades so the Grub Menu gives me 3 Kernels and 3 Recovery Modes to boot into.

Well I guess this is long enough. I look forward to a long and fruitful association with Ubuntu, both the Distro and the Community.

Boatdrinks
M=)

---

### Post by AlexenderReez on 2007-07-20
> **msgmurph said:**
> Hello Everyone!!  I have been dabbling with Ubuntu for the last several months and I love it. However I do have a few issues to resolve to get everything working properly. Fortunatly I finally have some free time to try and fix things. I have a ton of questions and I don't know if I should ask them all in one post or split them up into separate posts. 
So my first question involves booting up. I have never been able to get Ubuntu to boot directly to the splash/login screen. Booting by turning on the computer causes the system to hang.  I found a post shortly after installation that advised booting into recovery mode and then running telinit3. Running telinit3 gets me to the login screen and  hen I can log in  normally ( at least I think thats what the normal login looks like.=)  At the login screen I can choose between Gnome, KDE, etc. The problem is I can't find the post that led me to the solution!  I'm going to keep searching for solutions in the Forums but if anyone has some pointers I would appreciate them.

After I get the boot process working properly I stlll have some issues.  
1 Get sound to work
2 Get DVD burner to work
3 Get multimedia to work ( I realize I might have issues as my CPU is an AMD64)

Some additional questions.


1 If I install an additional Hardrive how hard is it to make a backup partition to store my data on so that if I do break my system I can at least, hopefully, salvage my data?

2 Would it make sense to try the solutions on the previous versions of the kernel I have installed? I have been through 3 upgrades so the Grub Menu gives me 3 Kernels and 3 Recovery Modes to boot into.

Well I guess this is long enough. I look forward to a long and fruitful association with Ubuntu, both the Distro and the Community.

Boatdrinks
M=)

it is seems you are having critical problem with booting...hm...when you boot directly which switching it on,is there any error show when it hang?...

about sound, sometime this problem cause by alsa mixer...you can check by typing 
> alsamixer 
to terminal..
multimedia to work?have you install gstream?
> sudo aptitude install gstream*
menu,right click ,edit menu..enable sound under applications---> sounds and video--> sound..then enable all sound setting...if still doesn't work ...give a try this-->
> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
for dvd burner,i'm using k3b...even this is kde application...it has more option compare to gnome baker and few others gnome burner application..so i choose it.if you install additional hard disk and want to make auto mount for it,see the attachment:)

for kernel,if all previous kernel are having same problem,i suggest you to remove all of it..there is backup kernel in /boot/ folder name initrd.img-2.6.22-8-generic.bak..copy that to somewhere else and rename /boot/initrd.img-2.6.22-8-generic.bak to /boot/initrd.img-2.6.22-8-generic...copy back and paste to /boot/ folder..so it will replace current kernel that give problem..you can remove previous kernel by searching in synaptic kernel image,and remove old kernel...

---

### Post by msgmurph on 2007-07-20
Wow AlexenderReez !!
That was quick and a lot to digest/contemplate.=) Thank You 

I accessed grub and edited and took out quiet per Rui Pais's suggestions here [http://ubuntuforums.org/showthread.php?t=364314&highlight=hangs](http://ubuntuforums.org/showthread.php?t=364314&highlight=hangs)

The last thing I saw before screen blanked and keyboard froze was "Starting Gnome Display Manager"
Also I noticed that some of the messages DID NOT have an ok next to them.

Additionally the initializing screen looks something like this
[http://www.mymac.com/img/features/boot1-6-11-06.jpg](http://www.mymac.com/img/features/boot1-6-11-06.jpg)
Except that not all of the messages had 'OK' by them, they were just blank.

Is it a problem that my sysinfo says I am running Ubuntu ( when I boot into recovery mode and then telinit3) and yet when I boot by pressing the power switch the initializing screen says Kubuntu?

I'm going to see if I can find an error log on my system from the previous boot and see if that has any useful information

Again Thanks

Boatdrinks
M=)

---

