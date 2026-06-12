---
title: "Comparing Ubuntu and Fedora"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by vairoj on 2006-06-14
I am new to Linux and would like to selected a distribution for use as desktop and/or server. What I am curious about is the difference between distros. Let's bring up Ubuntu and Fedora Core as an example in this discussion.

I know that Ubuntu is based on Debian and Fedora is based on Red Hat, but what does that means to the users?

I heard that Debian has a better package management. But I don't know what does it means in terms of "better". Does it means comparing between dep and rpm?

What about other aspects? For example, some says that for server, they prefer Fedora, anyone know the reason that makes Fedora better for server?

---

### Post by firetux on 2006-06-14
Short:

Do you want to learn something about how linux/compters/os works?
=>fedora
Do you just wanna use it without learning what makes your compute tick?
=>ubuntu
(ubuntu bores me, nothing wants to break, not even when runnig the development version)

About the package manager, yum is theoretically better but slower than apt-get in real life. (you can replace it with smart package manager, wich is even better than both.)

Edit: you don't have to believe this, it's just an opinion.

---

### Post by ember on 2006-06-14
I recently tested Ubuntu Dapper, Fedora Core 5 and OpenSuSE 10.1 and to make it short:

Dapper installation was a real pain to me (somethings wrong there with my USB controller and its driver), but the system was quite smooth and attractive.

Fedora installation was smooth - I like the option to test and change my sound driver (as well as some others), yet I don't like the Redhat desktop style. Also the upgrading system was very fragile (which I noticed in earlier Fedora and Redhat versions, too) and crashed a lot. Furthermore it felt a little less snappy than dapper.

For OpenSuSE I only tested the live CD which went very smooth - I know the installer from earlier version, so I can say it's the best I know on Linux. I like the standard icons and desktop theming best of all three and it was very stable, yet the least responsive of the combatants.

For server purposes all are equally suited - yet maybe you will want to give standard Debian a try for a server.

---

### Post by localzuk on 2006-06-14
The differences with package managers come down to dependency calculation (so if you ask for a package you get all its dependencies without hassle etc...). In my experience, apt-get has always been better - as in less hassle, quicker and generally more effortless.

It comes down to personal taste though. What are you comfortable with? Personally, I have moved completely from RPM based distro's over to debian and ubuntu.

So, at the moment, I would say use Debian stable for a server and Ubuntu Dapper for a desktop.

I think the 'fedora for server' attitude comes from the days when a lot of people were running Redhat on the server as it was a good distro. I think it has slid into instability and is a pain to maintain now in its Fedora core guise.

---

### Post by vairoj on 2006-06-14
So basically does it means that most difference between distro are in "details", such as hardware supports, responsiveness, etc. Which must be experiment by myself to see what works better for me?

For server, what are the differences between Debian and Ubuntu Server? Why do you recommend standard Debian over Ubuntu Server?

---

### Post by echo $USER on 2006-06-15
why not just try them all?  you'll thank me.

---

### Post by aragorn2909 on 2006-06-15
[QUOTE=echo $USER]why not just try them all?  you'll thank me.[/QUOTE]

This is excellent advice.  Limiting yourself to these three flavours (Debian/Ubuntu, Red Hat/Fedora, Suse) is like walking into Baskin Robbins and limiting yourself to either vanilla, chocolate, or strawberry.  Pull a chair up to the buffet that is Linux distributions, and try something youve never had before, you might find something you really like.

---

### Post by localzuk on 2006-06-15
Debian stable has been developed for (IIRC 4 years or something close) so all the packages are stable and more likely not to break.

Ubuntu, even though it is excellent, is only developed in short bursts with major package version increases regularly. This adds to instability.

Most linux distro's will have very similar hardware support as they are all based on the Linux kernel where most hardware support is dealt with. The only places you may find differences is with things such as wireless cards, proprietory graphics drivers and whether the particular kernel was compiled with your particular hardware support built in.

---

### Post by anaconda on 2006-06-15
Well.. I have to say, that I dislike Fedora.. Too many CD:s, and too many problems with my hardware, and I dont like .rpm:s...

With ubuntu I havent had (much) problems. Hardware was automatically detected correctly, and I like the community, and synaptic and different flavors (Xubuntu) and.. and...
And it comes in 1 CD, which is always a plus.. it means that ubuntu isn't too bloated.... (maybe a little)

---

### Post by xenblend on 2006-06-16
I would actually say its the other way around.  If you just want something that works out of the box but is all proprietary so you cant change/update/break anything, then go with Fedora Core.  If you want to customize, change source code, or anything else fun, go with ubuntu.

---

### Post by firetux on 2006-06-16
[QUOTE=xenblend]I would actually say its the other way around.  If you just want something that works out of the box but is all proprietary so you cant change/update/break anything, then go with Fedora Core.[/QUOTE]
Fedora is 100% free and 0% propietary, as is ubuntu. If you want propietary go with linspire, xandros or pclinuxos.

 [QUOTE=xenblend] If you want to customize, change source code, or anything else fun, go with ubuntu.[/QUOTE]
I don't agree on that one, its ubuntu that is coming with a gui for everthing and makes users believe the command line is unnecessary by providing a (limited) gui for every little thing you could change. 
Fedora is also more cutting edge than ubuntu.

DISCLAIMER: Everything I write is merely an opinion, and is not personal(how could I get personal, I don't even know you guys)(You probably also noticed english is not my native language, so some things may appear more 'direct' than they are meant to be.)

Very very personal and somewhat elitistic: I think a lot of distros are going the wrong way trying to make everything easier, its exactly what happened to windows, we wouldn't want that to happen with linux, do we? Linux is for hobbyists who want to learn how their computer works.

---

### Post by bruce89 on 2006-06-16
[Linux Distribution Chooser]("http://www.zegeniestudios.net/ldc/index.php"), may help you choose.

---

### Post by darkhatter on 2006-06-16
if you want a server distro use slackware, you'll have fun setting up but after that its smooth sailing. Desktop you may want to go with Fedora Core 5 it was the least buggest distro this year (this is what was said on distrowatch, this is comparing ubuntu, fedora core, suse)

I would say go with breezy and wait for a fixed installer for the new ubuntu

---

### Post by vairoj on 2006-06-20
Thank you all guys. I am currently installed Ubuntu 6.06 and I think I might also installed Fedora Core 5 to compare them side by side, desktop purpose first.

the Linux Distribution Chooser is very imformative. Thanking for letting me know.

---

