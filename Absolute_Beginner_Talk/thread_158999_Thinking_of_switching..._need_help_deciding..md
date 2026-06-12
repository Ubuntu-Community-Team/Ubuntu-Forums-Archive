---
title: "Thinking of switching... need help deciding."
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by mrchrisblau on 2006-04-12
Alright, so right now I'm dual booting between xp (I do it for the games, honest!) and Fedora Core 5. I've had my FC5 install for about a week now and I'm getting pretty decent at the basic command line stuff (I am, of course, profiecient in the regular GUI navigation). So far I'm really happy with FC5: it recognizes everything, runs smoothly, and is pretty straight forward in terms of plain usablity. 

However, I've been browsing around quite a few Linux help/How-to sites getting my bearings in linux and I keep seeing Ubuntu this and Ubuntu that all over. After a bit of researching I found that a lot of people seem to swear by Ubuntu. So I wan't to give it a shot.

Heres the catch. I only want to run 2 OS's (3 is far to many for me). I know i need xp (EVE Online, Call of Duty 2, BF2, HL2, CS:S) and I know I want some form of linux (for everything else). My question is this: should I try to fix something that is not broken (ie, wipe FC5 and install ubuntu) or should I just stick with what works so far (FC5). 

Additionally, is Ubuntu newbie friendly? FC5, while lacking in the community side in my opinion, is a really straight forward OS (from install to command line to GUI). The Ubuntu community seems to be much stronger (and thus more people to ask questions of), but I'm not to sure about Ubuntu's newbie-freindly factor (as I havn't used it). 

So here are some questions I have for current Ubuntu users (in addition to the newbie-friendly question):
- How does one go about installing Ubuntu? Is it an easy graphical installation like FC5? Or is it pure command line? In between?
- Does a basic Ubuntu installation come with some stock programs? FC5 comes with openoffice.org, some games, firefox, etc. Does Ubuntu?
- Is it easy to install programs in Ubuntu? This is the part with FC5 I'm having the most trouble with. Is it easier or the same (or even harder) im Ubuntu?
- Finally, would Ubuntu run on my system? ECS mobo w/ AMD64 proc. nVidia GeForce 6600 graphics card. 120gb SATA drive (40gb windows, 70gb linux). 512mb PC3200 RAM.

If you have made it this far I salute you. Thank you so much.

mrchrisblau

---

### Post by Sef on 2006-04-12
> - How does one go about installing Ubuntu? Is it an easy graphical installation like FC5? Or is it pure command line? In between?

Graphical.  Read this excellent tutorial on dual booting it:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

> Does a basic Ubuntu installation come with some stock programs? FC5 comes with openoffice.org, some games, firefox, etc. Does Ubuntu?

Yes, it comes with those and more.  Is there a particular program you are looking for?

> - Is it easy to install programs in Ubuntu? This is the part with FC5 I'm having the most trouble with. Is it easier or the same (or even harder) im Ubuntu?

Yes it is easy to install via Synaptic Package Manager: a gui front end for apt-get. Also there is Add Applications, which is even simpler, but more limited.  Plus you can use apt-get via the command line.

> - Finally, would Ubuntu run on my system? ECS mobo w/ AMD64 proc. nVidia GeForce 6600 graphics card. 120gb SATA drive (40gb windows, 70gb linux). 512mb PC3200 RAM.

Yes, just get the AMD 64 bit version.

---

### Post by Darkriser on 2006-04-12
answers from linux (ubuntu) newbie (that's me:mrgreen: ):
- installing ubuntu - the front-end is text-based graphics, very similar to windows install (sorry for this comaprison:twisted: ). anyway, I (as a totoal linux newbie) was able to install Ubuntu with NO problems (I'm very experinced with MS, but n00b in linux world)
- Ubuntu comes with lot of software installed by default (yes, firefox included), but uses only "free" (GPL) software. so you'll probably miss some tools in your default configuration. however, read the next point:
- software installation - ubuntu uses debian packages (.deb). it also uses "repositories" - it's kind of software archive. this software is maintained by comunity, comprehensively tested and stable. yes, and there are really thousands of packages. the best point? software installation (or uninstallation) from repositories requires only mouse clicking. no command line. ok, if you wish (like me;) ), you can do it from command line. but you are not required to do so. As a newbie, I also mastered to compile my own Ralink drivers for wireles adapter from source files, install it, etc.
- your system specs? they are far behind ubuntu requirements;) 

ok...and one more thing. i never saw such a great comunity of people willing to help each other...only here. my advice? go for it....

---

### Post by mrchrisblau on 2006-04-12
Thanks so much! That answered a lot of questions. I think I'm sold on Ubuntu right now.

One last question that went unanswered: I have FC5 and XP right now and GRUB automatically boots and lets me pick which OS i want to boot.. if i install Ubuntu will it still have GRUB boot first and let me pick? Would I need to reinstall windows? The OSs are on seperate partitions but ya never know...

---

### Post by sadjack on 2006-04-12
mrchrisblau

I jumped from FC 4 to ubuntu a few weeks ago. It started off as a lets just see what its like, but now I would not go back. I like the concept of 'sudo' instead of  su to root, I like how things just seem to work and in my view 'apt-get' is probably better then 'yum'.

I have found that ubuntu has recognised my wireless cards without a problem whereas in FC4 it was a bit of a fudge.

An initial install gives you pretty much waht you need, however a great little automated script 'automatix' downloads and installs all kind of usefull stuff like windows codecs and dvd players, a great plus for ubuntu in my view.

Why not download the live cd and play for a while, you might just like it...

I have thought about trying FC5 but can't bear to lose breezy!

---

### Post by Sef on 2006-04-12
> One last question that went unanswered: I have FC5 and XP right now and GRUB automatically boots and lets me pick which OS i want to boot.. if i install Ubuntu will it still have GRUB boot first and let me pick? Would I need to reinstall windows? The OSs are on seperate partitions but ya never know...

Yes, it will let you pick.  The default will be Ubuntu, and just highlight Windows if that is what you want.

No, you don't need to reinstall Windows.

---

### Post by nanotube on 2006-04-12
[QUOTE=mrchrisblau]Alright, so right now I'm dual booting between xp (I do it for the games, honest!) and Fedora Core 5. I've had my FC5 install for about a week now and I'm getting pretty decent at the basic command line stuff (I am, of course, profiecient in the regular GUI navigation). So far I'm really happy with FC5: it recognizes everything, runs smoothly, and is pretty straight forward in terms of plain usablity. [/quote]

> However, I've been browsing around quite a few Linux help/How-to sites getting my bearings in linux and I keep seeing Ubuntu this and Ubuntu that all over. After a bit of researching I found that a lot of people seem to swear by Ubuntu. So I wan't to give it a shot.

hehe, nice.

> Heres the catch. I only want to run 2 OS's (3 is far to many for me). I know i need xp (EVE Online, Call of Duty 2, BF2, HL2, CS:S) and I know I want some form of linux (for everything else). My question is this: should I try to fix something that is not broken (ie, wipe FC5 and install ubuntu) or should I just stick with what works so far (FC5). 

much as i like ubuntu, i'd say, if fc5 works for you with no troubles, then stick with it. that is, if your goal is to just have a system that works well, and you already have one now, why mess around with it? if your goal is to play with something new, then you can consider ubuntu.

> Additionally, is Ubuntu newbie friendly? FC5, while lacking in the community side in my opinion, is a really straight forward OS (from install to command line to GUI). The Ubuntu community seems to be much stronger (and thus more people to ask questions of), but I'm not to sure about Ubuntu's newbie-freindly factor (as I havn't used it). 

i'd say ubuntu is very newbie friendly. especially for someone who is coming from another linux, and is familiar with the concept of running an occasional command in a terminal, ubuntu is a piece of cake. :)

> So here are some questions I have for current Ubuntu users (in addition to the newbie-friendly question):
- How does one go about installing Ubuntu? Is it an easy graphical installation like FC5? Or is it pure command line? In between?

it's a pretty simpre graphical install process. it will ask you a couple of questions when you install, and then do everything automagically. about the nicest install process i've ever seen. 

> - Does a basic Ubuntu installation come with some stock programs? FC5 comes with openoffice.org, some games, firefox, etc. Does Ubuntu?

yes, it comes with OOo, firefox, games, gimp, gaim, irc, etc. a very usable system from the get go.

> - Is it easy to install programs in Ubuntu? This is the part with FC5 I'm having the most trouble with. Is it easier or the same (or even harder) im Ubuntu?

just about everything is available in the repositories, in which case it's just a simple "sudo apt-get install packagename" away. (or you can use the excellent graphical package manager called Synaptic to do the same). software installation on ubuntu beats anything else i've seen hands down.

> - Finally, would Ubuntu run on my system? ECS mobo w/ AMD64 proc. nVidia GeForce 6600 graphics card. 120gb SATA drive (40gb windows, 70gb linux). 512mb PC3200 RAM.

don't see why it wouldn't - but if you are really up to installing, you should try booting with a livecd first, to see if all hardware is working. 

> If you have made it this far I salute you. Thank you so much.

mrchrisblau
have fun. :) but remember, if you just want a working system, and fc5 is good for you, then i wouldn't mess around with a good thing. :)

---

### Post by Darkriser on 2006-04-12
[QUOTE=mrchrisblau]Thanks so much! That answered a lot of questions. I think I'm sold on Ubuntu right now.

One last question that went unanswered: I have FC5 and XP right now and GRUB automatically boots and lets me pick which OS i want to boot.. if i install Ubuntu will it still have GRUB boot first and let me pick? Would I need to reinstall windows? The OSs are on seperate partitions but ya never know...[/QUOTE]

GRUB is great. if you already have some OS installed (even M$:mrgreen: ), GRUB will recognize it during install (just select to install it to your MBR) and modify the /boot/grub/menu.lst file automatically so that you can choose what OS to boot at start-up.

---

### Post by nanotube on 2006-04-12
[QUOTE=Sef]

Yes, just get the AMD 64 bit version.[/QUOTE]

in fact, it would probably be better to get the 32bit version, because i've been seeing people have problems with the 64bit...

---

### Post by helpme on 2006-04-12
Well, if FC5 works for you, I'd stay with it.

You shouldn't be giving to much credit to what you read on the net about distros. Much of it is just uninformed, rather childish ramblings, praising one distro and bashing others like the one was made in heaven, while the other comes straight from hell.

That said, if you want to give Ubuntu a try, I'd recomend checking out the LiveCD first. That way, you will get an impression of what it's all about, without having to install it and as you are not going to hose your computer with it, you might even check out the latest development release:
[http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-6/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-6/)

---

### Post by mrchrisblau on 2006-04-12
Yep, I'm sold now. Thanks guys!

I've downloaded the 5.10 iso and its waiting to be burned. I'd do it now but the CD-Rs are in the other room and I don't dare wake the other (normal) people trying to sleep at this hour (2:15AM). 

One question: should I install the 5.10 release or the 6.06 (i think thats the number) release? 6.06 I assume is newer.. but is it stable? I heard that upgrading Ubuntu is easy so I figure i will install the 5.10 and upgrade later to 6.06 (or whatever). Is there any reason why I should install the 6.06 now?

And in response to the people saying that if FC5 works, don't fix it: My desktop (the xp/linux box) is purely for messing around. I have a laptop that I have all my important stuff on.. so sure it works, but i've got nothing to lose if Ubuntu decides not to work (which I doubt it will anyway).

Thanks again guys. Great community it seems. Expect to see me around more! :cool:

---

### Post by Darkriser on 2006-04-12
Ubuntu Breezy (5.10) is the latest stable version released for public use.
Ubuntu Dapper (6.06) is development version, that will be released on july 1st. There might be some bugs, but I don't expect major ones. You have to decide;) .

Anyway, I'm running 5.10 and will upgrade for Dapper once it's released public.

---

### Post by IUFLA on 2006-04-12
[QUOTE=mrchrisblau]
- Finally, would Ubuntu run on my system? ECS mobo w/ AMD64 proc. nVidia GeForce 6600 graphics card. 120gb SATA drive (40gb windows, 70gb linux). 512mb PC3200 RAM.

If you have made it this far I salute you. Thank you so much.

mrchrisblau[/QUOTE]

I have almost the exact same hardware configuration as you do, and Breezy 64 runs really well on it...

[Here's a really good "How-to" on installing the NVidia drivers](http://www.ubuntuforums.org/showthread.php?t=75074)

I find myself more and more booting into Ubuntu rather than XP for everyday tasks...Good to try new things and experiment with...

---

