---
title: "What is automatix2?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-07-05
I have 2 linux pc's on my network .  I'm trying to set up one of them as a dedicated torrent box and a guide suggested that i install azureus using automatix2 rather than installing it from theone that comes with the ubuntu build.  So installed  automatix2  and got prompted that there are several illegal codecs that can be obtained using this progran.  On my main linux box i have not installed automatix2 i have been using synaptic to install programs.  What is the difference between synaptic and automatix2?

Thx,
VC

---

### Post by user1397 on 2007-07-05
> **videocheez said:**
> I have 2 linux pc's on my network .  I'm trying to set up one of them as a dedicated torrent box and a guide suggested that i install azureus using automatix2 rather than installing it from theone that comes with the ubuntu build.  So installed  automatix2  and got prompted that there are several illegal codecs that can be obtained using this progran.  On my main linux box i have not installed automatix2 i have been using synaptic to install programs.  What is the difference between synaptic and automatix2?

Thx,
VC
The synaptic package manager is the default tool to install or remove ubuntu programs; it comes pre-installed with ubuntu.

the [automatix project]("http://getautomatix.com") develops a third-party program, that supposedly eases the installation of several programs that are rather difficult to come by or install in ubuntu.  I personally think that this was the case in the earlier versions of ubuntu, but since then many improvements have been made in ubuntu to ease the installation of the programs that are commonly installed by automatix.

note: automatix installs software from its own software "repository", or "online warehouse" of sorts, while synaptic (and the add/remove utility located in the applications menu) uses ubuntu's default software repositories, or "repos" for short.

---

### Post by misfitpierce on 2007-07-05
Easy way to set up most common used pieces o software on net... Auto installs and does everything... I recommend for sure

---

### Post by dfreer on 2007-07-05
For a dedicated torrent box, I'd check out torrentflux (requires php and mysql). I'm a huge fan, it's pretty amazing.

---

### Post by coolen on 2007-07-05
Automatix is a script to install extra pieces of commonly requested software.
I don't like it, personally. I used it once, and it didn't seem to stick to repositories. It also broke my system, but I think that was just a fluke.
It was most useful for installing codecs and drivers in earlier versions of Ubuntu, but the Ubuntu team has largely removed the need as of Feisty.
I'd stick to the repos wherever possible. Unless it downloads a version of Azureus with major bug fixes, don't bother.

---

### Post by scheuri on 2007-07-05
Well, I would like to repeat a few things already mentioned and add some warnings.

Ubuntu (like Debian or any other Linux distribution) comes on CD. However, most of those distrubutions have thousand of software packages which they officially support and offer to be installed. It is impossible to put all of those packages on a CD, so they offer them to be downloaded and installed easily through tools like synaptic, adept, aptitude or apt-get.
Those packages are in the official repositories. Those repositories are mentioned in a configuration file (/etc/apt/sources.list).

Now, a few things (mainly multimedia) are a little bit difficult to be installed and configured if you use the official tools and you surely need a little manual to help you with it.
Those manual are usually easy to read, straight forward and available under help.ubuntu.com ([https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)) with the possibility to search for keywords (such as movie, dvd, sound, repository, repositories, multimedia, codecs, etc.).

Well, as open source is about choice and being able to change software, some people decided to write a (non-official) program which helps you with installing certain multimedia application and software.
While this is very good idea, it unfortunately does not use the official repository to get the software and tools needed. It uses its own repository which is not officially supported.
That is not bad, however if something goes wrong you might have a hard time to find people able to help you. Furthermore, if you upgrade from one version of Ubuntu (eg 7.04) to the next one (eg 7.10) you definitively run into troubles as unsupported and unofficial software is installed which might not get upgraded correctly.

Well...
I for one would suggest you use the manuals and take 5 minutes more time to get thins running. This might take more time, on the other hand you have a conistent and supported Ubuntu and it is very likely that people can help you if you run into troubles (because you use the official stuff instead things people probaly do not know about).

I am sorry if this sounds bad for Automatix and the like. I really like the idea of scripts and tools which helps people to get software and codecs and stuff easily. However, by using 3rd party repos my purism comes through and I can not easily recommand those tools.

Thank you.
Scheuri

---

### Post by videocheez on 2007-07-05
Thanks guys a lot of good info.

---

### Post by carusoswi on 2007-07-05
Each to his/her own opinion.  In my personal experience, it was Automatix2 that finally allowed me to sort out problems that I had been unsuccessful in sorting out on my own.  For someone familiar with programming or some folks who just naturally progressed through their installation without problems or perhaps had system setups that were more conducive to a smooth Ubuntu install, then, they may see no need for Automatix.

I experienced problems setting up Ubuntu - during one install, my networking would worked like a charm, then, in an attempt to fix something else, my networking would become unusable.

Get that fixed and something else would not be working.

This forum is an absolutely wonderful source of support.  Unfortunately, you can also follow well-intentioned advice that gets your system tied up in knots, either because you didn't clearly express your problem or because someone trying to help you did not understand, or, in a few instances, simply gives you the wrong information.

For me, an example of the above was my struggle to get my N1 Belkin wireless adapter to work.  I had a devil of a time getting ndiswrapper working when I followed all the suggestions offered here on the forum.  It could be that I am a dunce, it could be that I followed advice for the wrong setup, stumbled ignorantly onto outdated info, etc.

The point is that I installed and re-installed Ubuntu in an attempt to get that to work.  When I used Automatix2, the install went off without a hitch.  Automatix2 also configured my NTFS drives for read/write with little effort on my part except to click with my mouse to accept the changes.  To this day, I would not be able to make those changes "manually."  Now, I like to tinker as much as the next person - and Ubuntu/linux offers you plenty of opportunity for that.  As for configuring/mounting NTFS drives, I could care less if I ever learn the underhood process.  I just want that stuff to work.

Automatix2 is one application that will perform those tasks for you.

I have experienced no problems at all with that software or with the applications I have downloaded from their site.  I consider their repo to be yet another source of software for my machine.

. . . and I experiment with my ubunutu without concern that I might break something that I will never be able to figure out again . . . because I know that Automatix2 can reconfigure me in those areas where I have problems again and again if necessary.

I am puzzled why, among those who do not use Automatix, there are so many who talk it down as a machine-breaker or worthless or express concern for the integrity of the downloads available from the site.  To be fair, the comments in this thread have been more objective and balanced.  The one mention of breakage in this thread conceded that it was probably a fluke.  But, if you read a number of threads, you will find comments that characterise Automatix as a waste, junk, unsafe/unstable, something to be avoided, etc.

I would imagine that most of us have managed to "break" our installations at one time or another.  If it occured during the use of Automatix, we naturally would ascribe the cause to Automatix.  OTOH, you won't see many non-Automatix users stating that Ubuntu broke their Ubuntu installation - even though most of us at one point or another have managed to goof up our system with AND WITHOUT the use of Automatix.

I don't rely totally on Automatix - it's just one more tool to which I can turn when I am having problems.  Fortunately, Ubuntu 7.04 includes features that make its use (especially its installation and configuration) easier than previous versions, and, for those of us who simply want to use the OS rather than "learn it," the future only looks brighter.

I would suggest that you try Automatix out for yourself.  You will not hurt anything.  I predict you will be presently surprised.

Caruso

---

