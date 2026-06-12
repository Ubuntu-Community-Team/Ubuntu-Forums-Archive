---
title: "Does Linux slow down like Windows over time"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by ICEcoffee on 2007-11-16
Hi all, does anyone know FOR SURE, if over time, Linux slows down as with windows?

I know from being a long time Windows user, that adding and removing software over time things slow down, as it does with the more you have on your system, then there is the defragmentation of data on the hard drive (which I think Linux avoids).

I'm just wondering if I have to be cautious with the amount of new Linux programs (I am unfamiliar with), I download to try out on my system.

---

### Post by svalding on 2007-11-16
Nah, your good. Linux will of course slow down over time, but this takes much much much longer than a windows machine with the absence of fragmentation, viruses, spyware and the like.

---

### Post by FuturePilot on 2007-11-16
Absolutely not. :)
It's great. You could load it up with as much software as you want, won't slow down. Don't need to defrag either. Linux kind of takes care of itself. ;)
The install on my laptop is about 6 months old now and it's still as fast as the day it was installed. Even after an upgrade too!

---

### Post by timcredible on 2007-11-16
> **svalding said:**
> Nah, your good. Linux will of course slow down over time, but this takes much much much longer than a windows machine with the absence of fragmentation, viruses, spyware and the like.

no, linux systems do not slow down over time - I've had systems running for 3 years 24x7, and no slowdown.  no, you don't run into fragmentation problems in linux with any of the modern filesystems like ext3.

---

### Post by Joakim Stokland on 2007-11-16
Also, there is no registry to be bloated like in Windows. I have now installed Gutsy, but my previous install (Feisty) was running for about six months too, without slowing down.

---

### Post by sports fan Matt on 2007-11-16


I concur..one of the reasons why I switched from windowze was cause i could never get my system fast and stay fast ..plus spyware and viruses....etc.  I love how people hate linux cause theyre so needing their apps with that bloated os..and refusing to seriously try it...

---

### Post by mivo on 2007-11-16
Well, you do collect garbarge over time. How much and how easy it can be removed depends on the distro. In Ubuntu's case, if you use Aptitude to install and remove software, unused dependencies will be removed when you uninstall a package (only if the packages were installed via Aptitude). This is not done if you use Synaptic to insteall/remove programs. (There is apt-get -removeall, but this can have undesired side-effects.

There are other distros, like Arch, that are more efficient at avoiding garbage than Debian-based distros, but with disk space being really cheap these days, it's probably no real concern whether a few extra MBs are used by unneeded packages/dependencies.

Linux doesn't slow down the way Windows does. Just sometimes check what auto-start programs and daemons you have running and clear out caches.

---

### Post by Frak on 2007-11-16
It will slow down, but it takes MUCH longer than Windows, and can be fixed with some freely available defragmentation software. You are then renewed for another couple of years or so.

---

### Post by newlinux on 2007-11-16
As the previous poster stated, it can. It really more depends on you. In Linux it is easier to fix and tune (remove unused packages etc, stop startup daemons, etc..) whereas in windows you'll probably get to a point where the only solution is to reinstall.

---

### Post by tech9 on 2007-11-16
> **ICEcoffee said:**
> Hi all, does anyone know FOR SURE, if over time, Linux slows down as with windows?

I know from being a long time Windows user, that adding and removing software over time things slow down, as it does with the more you have on your system, then there is the defragmentation of data on the hard drive (which I think Linux avoids).

I'm just wondering if I have to be cautious with the amount of new Linux programs (I am unfamiliar with), I download to try out on my system.

not as bad as windoz... good question though

---

### Post by sports fan Matt on 2007-11-16
excellent points guys..:)  mine was just to say "not as much" imo.  One thing is for sure..you cant necessarily "break" linux that easily and the forum offers genuine help, of that im grateful..

---

### Post by insane_alien on 2007-11-16
linux can slow down, but that only happens if you fill the drive up to about 95% full with stuff like torrents, then fragmentation can become an issue as the built in prevention mechanisms can't function with so little space.(this would happen on ANY filesystem and is often unavoidable.) this only really applies if it is the root partition though, if your root partition is clean then it'll stay fast bu accessing documents on your /home partition will be slow-ish.

but under normal usage, linux could run till the year 2036 without experienceing any problems(2036 is unixtime wrap around, we'll have fixed it by then, c'mon 64-bit)

---

### Post by Joakim Stokland on 2007-11-16
> **mivo said:**
> Well, you do collect garbarge over time. How much and how easy it can be removed depends on the distro. In Ubuntu's case, if you use Aptitude to install and remove software, unused dependencies will be removed when you uninstall a package (only if the packages were installed via Aptitude). This is not done if you use Synaptic to insteall/remove programs. (There is apt-get -removeall, but this can have undesired side-effects.


What's the difference between apt-get -removeall and apt-get autoremove then?

---

### Post by FuturePilot on 2007-11-16
> **Frak said:**
> It will slow down, but it takes MUCH longer than Windows, and can be fixed with some freely available defragmentation software. You are then renewed for another couple of years or so.

Yes, you might eventually need to do some defragging. Even the most fragmentation resistant file system, such as EXT3, will eventually start to fragment, but it's nowhere near like it is in Windows.

---

### Post by jaybombalous on 2007-11-16
like anything else, linux can get bloated if the user lets it get bloated.


Linux does not have a registry, so cleaning out config files and folders is easier then in windows and no need for third party programs to search out and destroy bad registry keys.

---

### Post by Inxsible on 2007-11-16
> **insane_alien said:**
> linux can slow down, but that only happens if you fill the drive up to about 95% full with stuff like torrents, then fragmentation can become an issue as the built in prevention mechanisms can't function with so little space.(this would happen on ANY filesystem and is often unavoidable.) this only really applies if it is the root partition though, if your root partition is clean then it'll stay fast bu accessing documents on your /home partition will be slow-ish.

but under normal usage, linux could run till the year 2036 without experienceing any problems(2036 is unixtime wrap around, we'll have fixed it by then, c'mon 64-bit)I dont think that is true for Linux in general, just 32 bit Linux/Unix.

and its Year 2038 not 2036. Here's the [wiki link]("http://en.wikipedia.org/wiki/Year_2038_problem")
I already use 64 bit, so I am good for 3000 years or so ;)

---

### Post by newlinux on 2007-11-16
> **Joakim Stokland said:**
> What's the difference between apt-get -removeall and apt-get autoremove then?

> **mivo said:**
> Well, you do collect garbarge over time. How much and how easy it can be removed depends on the distro. In Ubuntu's case, if you use Aptitude to install and remove software, unused dependencies will be removed when you uninstall a package (only if the packages were installed via Aptitude). This is not done if you use Synaptic to insteall/remove programs. (There is apt-get -removeall, but this can have undesired side-effects.

There are other distros, like Arch, that are more efficient at avoiding garbage than Debian-based distros, but with disk space being really cheap these days, it's probably no real concern whether a few extra MBs are used by unneeded packages/dependencies.

Linux doesn't slow down the way Windows does. Just sometimes check what auto-start programs and daemons you have running and clear out caches.

[http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude)

aptitude vs. apt-get is largely irrelevent post-Dapper. And I believe synaptic uses apt-get.

---

### Post by nae5 on 2007-11-16
So what are the steps I can take? I know it's kind of an incomplete question since it depends on what and how i have previously installed..

Often users (me, at least) install packages with terminal sudo apt-get install and synaptic as well.  Ive also installed some .bin files like google earth.  I haven't used aptitude once.. for no reason other than that forums/howtos/nsuch  usually say apt-get.  

However the link in the post above this says that since 6.10 apt-get/aptitude differences are largely irrelevant since both will uninstall unused dependencies when uninstalling an application. 

what about packages i have installed then uninstalled in synaptic?  For example when i set this 7.10 computer up i installed java 5 and 6 in synaptic accidentally, then uninstalled 5 since 6 is newer..

also i uninstalled through add/remove some of the original preinstalled games i dont use and the bluetooth analyzer since this computer does not have bluetooth.  were the files deleted or simply uninstalled?

And the java 5 dependencies? Not that these instances slow my computer, actually i have to agree with above posters that a linux box will stay faster cleaner longer than any windows, simply from personal use and experience.

i did some look and found something about ```
sudo apt-get autoclean
```  but the explanation was hard for me to understand..

---

### Post by Inxsible on 2007-11-16
Follow this [tutorial]("http://ubuntuforums.org/showthread.php?t=140920&highlight=removing+junk+packages") on cleaning up.

However, be careful with the debconf part of it since it can cause havoc if not used carefully. Also it removes some of the gstreamer plugins (at least it did for me in Feisty) and then you won't be able to play some of your media.

---

### Post by SunnyRabbiera on 2007-11-16
well linux can get bogged down yes as the more applications you wish to load at startup can add up like in windows... but I so far have not seen any linux take more then one or two minutes, in windows this is an entirely different matter.
heck even with my modest specs of 252MB of ram I can run compiz during the load and even if it slugs me down a bit I still beat windows...
My husbands computer with 512 of ram loading XP takes waaaaaaaaaaay slower then my compy, hes even got a better processor then me and its still friggin slow as molasis

---

### Post by nae5 on 2007-11-16
That guide is very helpful thnx for the link.  tip #1for synaptic removed the uninstalled games, java, and bluetooth packages as well as the emerald package after i didn't use it. perfect.

---

### Post by stchman on 2007-11-16
> **ICEcoffee said:**
> Hi all, does anyone know FOR SURE, if over time, Linux slows down as with windows?

I know from being a long time Windows user, that adding and removing software over time things slow down, as it does with the more you have on your system, then there is the defragmentation of data on the hard drive (which I think Linux avoids).

I'm just wondering if I have to be cautious with the amount of new Linux programs (I am unfamiliar with), I download to try out on my system.

Not very much.  Mine has slowed down a little but but I have added programs to start up in the Sessions Manager.  If I did not do that then it would be faster.

It has been my experience that Windows XP slowdowns are in large part attributed to spyware and questionable surfing.  

I dual boot and my XP install still runs pretty zippy.  I don't use IE, I use AVG and a lot of streamlined open source apps.  I also make all accounts limited and only use Administrator when absolutely necessary.  It is my opinion that if M$ would make XP accounts default to limited there would be FAR less problems.  Vista has the UAC, but it is WAY too easily bypassed.  One day M$ will take system security seriously.

I have not booted into XP in some time as Ubuntu does 95% of what I need.  I only use XP for games.

---

### Post by Inxsible on 2007-11-16
> **nae5 said:**
> That guide is very helpful thnx for the link.  tip #1for synaptic removed the uninstalled games, java, and bluetooth packages as well as the emerald package after i didn't use it. perfect.

You are welcome. Glad to help :)

---

