---
title: "x86 or 64bit?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by sleiborg on 2007-09-18
I'm about to install Ubuntu 6.06 LTS on a box with a Core 2 Duo Processor E6320 processor.
What version should I download?

1. Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
2. 64bit AMD and Intel computers


- Kim

---

### Post by Malibu Illusion on 2007-09-18
You have the option of running the 64-bit OS on your machine, however you can also go with the 32-bit version too if you so wished.

Generally you'll find more compatibility with 32-bit platform, although things can be made to run on the 64-bit platform also with a little tweaking by installing the necessary libs or creating a 32-bit chroot.  The advantage of running 64-bit is that you'll see increased performance in CPU intensive tasks such as compiling from source.

If you're fairly new, you would avoid some headaches by taking the 32-bit route.  If you want  a challenge and to learn more in some cases and install 32-bit libs or set up chroots, then you have the option of the IA-64 platform with that CPU.

Take care.

---

### Post by gshockxc on 2007-09-18
Malibu, sorry if this is a dumb question or out of place in this forum.  If I have an AMD processor in my PC, is it safe to assume that I should download the 64 bit OS?

---

### Post by LowSky on 2007-09-18
Only if its a AMD Athlon 64 processor.
dont use if its a Semphron or Duron

---

### Post by asmoore82 on 2007-09-18
There are 64 bit Semprons out there too now.

---

### Post by RomeReactor on 2007-09-18
Hi.

> **LowSky said:**
> Only if its a AMD Athlon 64 processor.
dont use if its a Semphron or Duron

It depends on the [Sempron core]("http://en.wikipedia.org/wiki/X86_64#Implementations"); I myself have a Sempron with a Palermo core, and am indeed running Ubuntu 64-bit.

---

### Post by dptxp on 2007-09-18
Semprons from August 2005 are more likely to be 64 bit. They are fully 32 bit compatible. Please check your part number.

A few minutes of work is needed for 64 bit (I think flash, check the 64 bit forum). You will find almost all programs in 64 bit.

I run 64 bit on my laptop, it is flawless so far. 

Many 64 bit users swear by 64 bit, I have not used enough to swear but I found my CAD packages too in 64 bit.

---

### Post by rsambuca on 2007-09-18
> **Malibu Illusion said:**
> You have the option of running the 64-bit OS on your machine, however you can also go with the 32-bit version too if you so wished.

Generally you'll find more compatibility with 32-bit platform, although things can be made to run on the 64-bit platform also with a little tweaking by installing the necessary libs or creating a 32-bit chroot.  The advantage of running 64-bit is that you'll see increased performance in CPU intensive tasks such as compiling from source.

If you're fairly new, you would avoid some headaches by taking the 32-bit route.  If you want  a challenge and to learn more in some cases and install 32-bit libs or set up chroots, then you have the option of the IA-64 platform with that CPU.

Take care.sleiborg,  Go ahead with the 64bit platform.  Virtually everything that malibu mentioned here is based on completely outdated information.  There are no extra 'headaches' by using the 64bit system.  People have developed scripts to do all the necessary installation of the proprietary java and flash plugins, so all you have to do is click on the file.  Certainly not a headache by any means.

Have fun, enjoy, and you may as well use your screaming hot rig up to its full potential!

---

### Post by sleiborg on 2007-09-18
Thanx rsambuca

Thats what I like to hear, I will go ahead with the 64bit platform :)


- Kim

---

### Post by LowSky on 2007-09-18
> **LowSky said:**
> Only if its a AMD Athlon 64 processor.
dont use if its a Sempron or Duron

Well I knew I was wrong..:lolflag:

I'm using 64bit Gutsy right now and most things work just fine...but I recommend using Fiesty until Gusty is released in October

---

### Post by Kilz on 2007-09-18
> **sleiborg said:**
> I'm about to install Ubuntu 6.06 LTS on a box with a Core 2 Duo Processor E6320 processor.
What version should I download?

1. Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
2. 64bit AMD and Intel computers


- Kim

Go with the 64bit version. Feisty is a great 64bit distro and your hardware is designed for 64bit. Installing the 32bit would be like buying a corvette and then pulling out 4 spark plug wires. Secondly, no version is perfect. The 32bit version is not flawless. Look at all the other sections of the fourm that are full of people with problems running the 32bit version.
Lastly, if you want good current information and help please visit the [64bit section of the forums.]("http://ubuntuforums.org/forumdisplay.php?f=134")

---

### Post by Malibu Illusion on 2007-09-18
> **rsambuca said:**
> Virtually everything that malibu mentioned here is based on completely outdated information.  There are no extra 'headaches' by using the 64bit system.  People have developed scripts to do all the necessary installation of the proprietary java and flash plugins!

This comment is short-sighted.

Looking beyond your typical installation of the 32-bit plugins for Firefox, there are many other applications out there that do not have 64-bit natives which will either require the 32-bit libraries or a chroot to run and these take time and research to set up correctly.

Whether you like it or not, there are instances that running a 64-bit platform will require additional steps on a user's part and this is what I was highlighting in my post.  This is inarguable.  In some more common cases, sure, there are scripts which can be used with moderate success rate but this far from applies in all instances.

Take care.

---

### Post by crjackson on 2007-09-18
> **sleiborg said:**
> I'm about to install Ubuntu 6.06 LTS on a box with a Core 2 Duo Processor E6320 processor.
What version should I download?

1. Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
2. 64bit AMD and Intel computers


- Kim

I'd go with #2 - I had more problems when using the 32-bit version on my machines vs. 64-bit.  If you have 64-bit hardware then give the 64-bit OS a spin.  Installing it and running the apps. are far less painful than some would have you think.  Just do it...

---

### Post by Kilz on 2007-09-18
> **Malibu Illusion said:**
> This comment is short-sighted.

Looking beyond your typical installation of the 32-bit plugins for Firefox, there are many other applications out there that do not have 64-bit natives which will either require the 32-bit libraries or a chroot to run and these take time and research to set up correctly.

Whether you like it or not, there are instances that running a 64-bit platform will require additional steps on a user's part and this is what I was highlighting in my post.  This is inarguable.  In some more common cases, sure, there are scripts which can be used with moderate success rate but this far from applies in all instances.

Take care.

When was the last time you ran the 64bit version of Ubuntu? Breezy? The claims you have are very outdated. It is not the truth. I dont know where you got it from since you only have 1 post out of 207 in the 64bit section. Please provide the list of applications you personaly have tried that forced you to install anything extra.

---

### Post by Digitallysick on 2007-09-18
64bit rocks, i had the 32bit and went for 64bit you see a great difference in apps, like gimp filters, etc plus everything works just as easy as 32 for the most part.

---

### Post by rsambuca on 2007-09-18
> **Malibu Illusion said:**
> This comment is short-sighted.

Looking beyond your typical installation of the 32-bit plugins for Firefox, there are many other applications out there that do not have 64-bit natives which will either require the 32-bit libraries or a chroot to run and these take time and research to set up correctly.

Whether you like it or not, there are instances that running a 64-bit platform will require additional steps on a user's part and this is what I was highlighting in my post.  This is inarguable.  In some more common cases, sure, there are scripts which can be used with moderate success rate but this far from applies in all instances.

Take care.Do you mind letting me know what some of these "many other applications" are?

---

### Post by Malibu Illusion on 2007-09-19
> **Kilz said:**
> I dont know where you got it from since you only have 1 post out of 207 in the 64bit section.

Ah, this must mean I know nothing about that platform since I don't explicitly post in that section on the Ubuntu forums.  My apologies(!)

> Please provide the list of applications you personaly have tried that forced you to install anything extra.

As of right now, the following have no 64-bit native releases and require the 32-bit libraries at best to run:

Skype
qmpd-client
Miro/Democracy Player

A lot of the applications in [this thread](http://ubuntuforums.org/showthread.php?t=191205) also still apply to this day as having no 64-bit support.  This is true for many more commercial companies releasing 32-bit binaries only as well; this applies in some cases in regards to hardware driver software too.

There might be scripts to install some of those, but it is still an additional step to take in order to get things working which is skipped on the 32-bit platform.

Some people seem to be trying to say here that running a 64-bit platform is completely without any additional steps.  This simply isn't the case and it's irresponsible to be trying to portray and justify that as fact.

64-bit support has thankfully undoubtedly received more attention from developers in recent times and that's a great thing.  Indeed it has come a long way from where it was, but it is still not entirely supported 100% and there are instances when additional steps are necessary.  I fail to see how anyone can argue this point when its quite clear that the 32-bit platform is just clearly more supported.

Just because the applications and hardware that you use are compatible with the 64-bit platform does not explicitly mean to say everyone prefers the same set of utilities and requires the same, supported, drivers.  You're, for sure, being short-sighted if you truly believe than 100% of all users will not run into issues purely because of their AMD64 platform selection.

---

### Post by misfitpierce on 2007-09-19
I have 64 bit cpu and have tried 64 bit ubuntu. It was nice altho setting up firefox with flash and such gave me a headache at first. I just use 32 bit now b/c havn't decided to reformat yet and 32 bit is fast enough with mostly everything app wise built for it and just working.

---

### Post by John.Michael.Kane on 2007-09-19
@Malibu Illusion
Skype=proprietary software which is out of Distro makers hands. If you want on your platform take the issue to the  program writers.

qmpd-client=Has not only a i386deb. but also the sourecode for compiling your own. Thus if you want it on your platform your free to compile it.

Miro/Democracy Player=Repos avilable for it, As well as the source you want it on your platform you free to compile it.

As far as I'm concerned the only vaild issue for a program that is not supported under 64bit would be skype,As the rest have source  for compiling your own.

---

### Post by rsambuca on 2007-09-19
> **SD-Plissken said:**
> @Malibu Illusion
Skype=proprietary software which is out of Distro makers hands. If you want on your platform take the issue to the  program writers.

qmpd-client=Has not only a i386deb. but also the sourecode for compiling your own. Thus if you want it on your platform your free to compile it.

Miro/Democracy Player=Repos avilable for it, As well as the source you want it on your platform you free to compile it.

As far as I'm concerned the only vaild issue for a program that is not supported under 64bit would be skype,As the rest have source  for compiling your own.
And there is a script for getting skype to work on 64 bit as well.  I have it running right now, so I am not sure what the problem is here.

---

### Post by dptxp on 2007-09-20
Those who can not, or shall not, should use the 32 bit.
Those who can, and shall, should go for the 64 bit.

---

