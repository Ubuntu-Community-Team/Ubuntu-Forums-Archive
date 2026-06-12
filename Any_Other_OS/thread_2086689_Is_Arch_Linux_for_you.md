---
title: "Is Arch Linux for you?"
date: 2012-11-21
forum: Any Other OS
---

### Post by COMECON on 2012-11-21
Hi!
I just finally installed Arch Linux... After a year of decisions, I finally did it! After installing it on VM, where all looks gorgeous, a few times, I decided it! I removed Fedora, which I installed this week-end (poor Fedora), and I took 4 hours installing, configuring, doing other stuff and doing homework with it. 
It's very nice to see that you can install a system without a graphical interface, and install a DE later (such as XFCE, as I did). But... according to the KISS definition, Arch has nothing. I thought it wasn't a problem, as you can just do **pacman -S packagename** and install something, like **pacman -S firefox**. But... Not only happened with applications, of course. I stayed... 2 hours of those 4 to configure the WiFi network and doing odd scripts for systemd, and discovering that neither NetworkManager nor Wicd worked, I saw another problem... The sound, how the hell I configure the sound. And the printer. And the multimedia keys. And all!
It's not a problem if you have a lot of time, and it's very... educational, I probably learnt more this afternoon that in the last month. But I don't have a lot of time, and I can't just... doing configure things all the time, I have work to do! 
So, for me, I think it's not for me! I like its KISS philosophy, and specially the rolling release, but I preffer more things out-of-the-box. I like it, and I'll keep it on my sda8 partition (thanks to god I divided a 30GB partition where Fedora was into 2 15GB partitions) and I'll install some other thing in the other. And, of course, I'll keep Ubuntu 12.04 as my main system :)
What about you? Have you tried Arch? Did you like it?

---

### Post by Tibuda on 2012-11-21
I have been an Arch users for years, and yes I feel your pain.

A bare minimal system is not an "advantage" of Arch, as you can do [the same thing with ubuntu minimal disk]("http://www.psychocats.net/ubuntu/minimal"). Their real advantage is the rolling release packages. They are not even too lightweight, as [pacman packages are very bloated]("http://www.youtube.com/watch?v=flmX9GYwyiI&feature=plcp").

I'd like Arch to have some pre-installed DE's or WM's isos, but they are going the opposite way and [dropped AIF]("https://www.archlinux.org/news/install-media-20120715-released/")! There are some nice projects for a preinstalled Arch like [Chakra]("http://www.chakra-project.org/"), [ArchBang]("http://archbang.org/") and [Manjaro]("http://blog.manjaro.org/").

---

### Post by LinuxMan92 on 2012-11-21
I've never been that impressed with it. It lets you set up everything from scratch but finding drivers can be a pain. To me the trade off between speed/time it takes to set everything up isn't worth it.

---

### Post by cecilpierce on 2012-11-21
I like Chakra but it has its own repos and is only KDE.
Manjaro is the best arch ive tried so far...:)

---

### Post by snowpine on 2012-11-21
I've tried Arch a few times but haven't been impressed by the "rolling release" style of updates.

---

### Post by smellyman on 2012-11-21
I have run Arch on all my systems for years.  After installing core and KDE, 99% of it is up and running.

everytime I try another distro and find their packages already way behind Arch I have to stay with Arch.

What drivers are a pain to find?  because if it isn't in the Arch repos or AUR it probably doesn't exist.

---

### Post by LiamOS on 2012-11-21
I never liked Arch, but I can understand why people might.
I only tried installing it briefly, when a friend suggested it. At that point, I'd used Gentoo briefly, and the entire installation and initial configuration made me :confused:

Arch seems to make half of your decisions for you, and leave the rest phenomenally open, which just seems a bit baffling. It gives you a preconfigured kernel, no choice of init system(But we all wanted systemd anyway :rolleyes: ), no method of controlling optional parts of programs... And then things break when you -Syu. I suppose that this is ideal to some; you get a lot of system control without having to delve into anything low level.

Maybe I've just been spoiled by Gentoo.

---

### Post by Moose on 2012-11-21
It took you a year to decide whether or not to install Arch on VM Ware? It sounds like your new to Linux.

---

### Post by Chdslv on 2012-11-21
> **Tibuda said:**
> I have been an Arch users for years, and yes I feel your pain.

A bare minimal system is not an "advantage" of Arch, as you can do [the same thing with ubuntu minimal disk]("http://www.psychocats.net/ubuntu/minimal"). Their real advantage is the rolling release packages. They are not even too lightweight, as [pacman packages are very bloated]("http://www.youtube.com/watch?v=flmX9GYwyiI&feature=plcp").

I'd like Arch to have some pre-installed DE's or WM's isos, but they are going the opposite way and [dropped AIF]("https://www.archlinux.org/news/install-media-20120715-released/")! There are some nice projects for a preinstalled Arch like [Chakra]("http://www.chakra-project.org/"), [ArchBang]("http://archbang.org/") and [Manjaro]("http://blog.manjaro.org/").

No, Arch is not for me, when there is a mini.iso from Ubuntu. Arch doesn't even have maintainers for their applications, and the majority of them are not supported community ones. Ubuntu also has ppas, but the Luanchpad is owned and maintained by Cannonical, and very rarely a ppa broke.

Archbang's original developer had also left the project. If you need a working distro derived from Archbang, even though that distro's developer won't say it, try Bridge Linux.

Arch is an operating system, not a distribution. It becomes a distribution, when you install the base and work your day and *nerves* with it.

I have built it from scratch, just to find out how it works, and whether it is that super. it works, but it breaks too. For the last 5 months, the Arch devs had released it five times. There is something definitely wrong with their top guys and repos.

When you can do anything with the Ubuntu mini.iso, why bother with unsure future OSs...:)

Even, if you take any Oneiric, Precise based Ubuntu-clone, or even further down Natty-based, you can bring it all the way to Raring and have a rolling distro!:)

Check my other posts.

Good day!

---

### Post by MadmanRB on 2012-11-22
Well if I ever become a computer super coder it might be.
Seriously I think arch is needlessly complex to install, you have to read so much, print so much and learn so much just to install a base system, man if I wanted this kind of complexity I would try linux from scratch.
And at least linux for scratch has an excuse, its purpose is right in the title for petes sake, its a hard coders distribution.
And for those who may say "well you are just too stupid"
No, I am just lazy, I have better things to do then hardcode in hexidecimal just to install just a basic windowed interface.
Heck I did install debian pure more then once, the only reason why I dont use it on a constant basis is again all down to personal laziness.

---

### Post by Linuxisfast on 2012-11-22
Unlike in Ubuntu where Samba is a breeze, a matter of simple right click and tick share, for all my best efforts I can't get Samba work in Arch or its variants Chakra and Manjaro.

---

### Post by lykwydchykyn on 2012-11-22
> **MadmanRB said:**
> 
No, I am just lazy, I have better things to do then hardcode in hexidecimal just to install just a basic windowed interface.


I don't remember having to hardcode in hexadecimal to do anything in arch.  Mostly it was just running some pacman commands.

Arch is interesting, I give it a spin every year or so to remind myself why I never switched to it.  I guess I never saw that much compelling about it, and I eventually messed up the system to where it couldn't be updated.

---

### Post by mips on 2012-11-22
I reckon Arch is awesome, if you are new to it you are probably gonna struggle a bit and take some time to setup a system. Once you know it setting up a system is pretty fast (well relatively speaking). Their wiki documentation is second to none and I even use it when using other distros (same goes for gentoo).

I no longer use Arch though reason being the frequent updates which eat into my limited data plan.

So along came Manjaro which is Arch but with more stable repos and less frequent updates. They take the Arch stable repos and move them to Manjaro testing repos, only after a while of testing etc do they move their testing to stable. I still however do a netinstall with Manjaro as I prefer building my own system but for those that don't you can download their full distro iso images. Their main focus is on XFCE but they also have Gnome, KDE & LXDE versions.

Arch, Slackware, Gentoo etc is not for everybody, use what works for you and what you are comfortable with ;)

---

### Post by Metallion on 2012-11-22
I use Arch both at home and at work. I need the beginner's guide when installing it but then it's a breeze to use. I did put Mint back on my old computer recently but it just bothers me that there's so much on there that I don't want.

I just like installing my system from scratch and having nothing in there that I didn't explicitly get. I really like the rolling release thing too. It's much easier to fix things if updates come in bite size and I don't like reinstalling every 6 months.

Actually I have a much easier time finding drivers etc. in Arch than I did in Ubuntu or Mint. Pretty much everything is either in the repos or in AUR.

---

### Post by Aaron Christianson on 2012-11-22
If you can read, you can use Arch. It does take more time to set up than Ubuntu, but generally seems to be more flexible afterwards, especially if you need weird drivers or something.

---

### Post by Chdslv on 2012-11-22
> **Aaron Christianson said:**
> If you can read, you can use Arch. It does take more time to set up than Ubuntu, but generally seems to be more flexible afterwards, especially if you need weird drivers or something.

Yes, of course!
If you can read, you'd use that time to read a book.:)

You can learn a lot by installing your Ubuntu from the mini.iso, not just installing that or this desktop. The other thing is that the Ubuntu applications are very sure, while Arch ones might break as the Arch devs might do something "strange" waking up. 

There were five releases every month, and who knows what they'd come up next. 

Not every distro maker installs Arch from scratch, for example, Bridge Linux was worked off Archbang. Well, if you are an Arch user, you'd know how I found that out. When you are installing Arch from scratch, there is a point, when you might want to change the host name, and that's the place the Bridge Linux guy had forgotten to remove the Archbang name. I have that iso.:)

So, not even the distro makers want to build Arch from scratch, when there are some ready-made ones.

You want a sure Arch installation? Install Archbang and go for it. Time and nerves saved. Even better, you can install Bridge Linux and go from there. Manjaro is forking out, because the Manjaro devs don't want to be at the mercy of Arch top guys. The same was with Chakra. 

Good luck, fight it out.
Take care!   :)

---

### Post by hadrons123 on 2012-11-22
There is a reason why you guys don't use Arch, gentoo or for that matter Debian.
There is a list why you wont want arch.
>  You may **not** want to use Arch, if:  
[LIST]
[*] after reading [The Arch Way]("https://wiki.archlinux.org/index.php/The_Arch_Way"), you disagree with the philosophy.
[*] you do not have the ability/time/desire for a 'do-it-yourself' GNU/Linux distribution.
[*] you require support for an architecture other than x86_64 or i686.
[*] you take a strong stand on using a distribution which only provides free software as defined by GNU.
[*] you believe an operating system should configure itself, run  out of the box, and include a complete default set of software and  desktop environment on the installation media.
[*] you do not want a bleeding edge, rolling release GNU/Linux distribution.
[*] you are happy with your current OS.
[*] you want an OS that targets a different userbase.
[/LIST]
 

The best thing about Arch is the wiki.  This above quotes are from wiki too!

---

### Post by COMECON on 2012-11-22
> **AnarchyTech said:**
> It took you a year to decide whether or not to install Arch on VM Ware? It sounds like your new to Linux.
It took a year to install Arch on my real hardware, mainly because I didn't want to mess it all up... But I think it'll took a week to uninstall it :P

---

### Post by nothingspecial on 2012-11-22
> you believe an operating system should configure itself, run out of the box, and include a complete default set of software and desktop environment on the installation media.

 I did install Arch once a few years back to see what all the fuss was about. After about 3 hours I looked up at my screen and saw that I had set it up to look and behave exactly like I had Ubuntu set up. There was no discernable difference when going about my normal daily stuff.

So what was the point of those 3 hours ?

---

### Post by kevinmchapman on 2012-11-22
> **Chdslv said:**
> Yes, of course!
There were five releases every month, and who knows what they'd come up next. 


You have been told before that you clearly don't understand the iso release system, and you repeat your error. This is why reading is so important.

---

### Post by kevinmchapman on 2012-11-22
> **nothingspecial said:**
> I did install Arch once a few years back to see what all the fuss was about. After about 3 hours I looked up at my screen and saw that I had set it up to look and behave exactly like I had Ubuntu set up. There was no discernable difference when going about my normal daily stuff.

So what was the point of those 3 hours ?

Take your pick:

"you believe an operating system should configure itself, run out of the box, and include a complete default set of software and desktop environment on the installation media."

"you are happy with your current OS."

"you want an OS that targets a different userbase."

---

### Post by vasa1 on 2012-11-22
> **Aaron Christianson said:**
> If you can read, you can use Arch. It does take more time to set up than Ubuntu, but generally seems to ....
allow Arch users plenty time to hang around on the Ubuntu Forums ;)
But many of the Arch wikis are really well put together.

---

### Post by 2F4U on 2012-11-22
> **Chdslv said:**
> 
There were five releases every month, and who knows what they'd come up next. 


Why don't you stop posting false claims, if you don't understand the concept behind Archlinux?

> Regular ISO snapshots are planned on a monthly basis.

From:
[https://www.archlinux.org/news/install-media-20120715-released/](https://www.archlinux.org/news/install-media-20120715-released/)


I am just realizing that this provides you each month with the opportunity to post your wrong assumptions. However, this is probably easier than trying to understand the concept.

> **Existing Arch Users**

      If you are an existing Arch user, there is no need to download a new ISO     to update your existing system. You may be looking for     [an updated mirrorlist]("https://www.archlinux.org/mirrorlist/") instead.


From:
[https://www.archlinux.org/download/](https://www.archlinux.org/download/)

---

### Post by COMECON on 2012-11-22
> **2F4U said:**
> Why don't you stop posting false claims, if you don't understand the concept behind Archlinux?



From:
[https://www.archlinux.org/news/install-media-20120715-released/](https://www.archlinux.org/news/install-media-20120715-released/)


I am just realizing that this provides you each month with the opportunity to post your wrong assumptions. However, this is probably easier than trying to understand the concept.



From:
[https://www.archlinux.org/download/](https://www.archlinux.org/download/)

Yep... ArchLinux ISO's (like 2012.11.02 for example) are just a snapshot of the package repository on this day... So, if you installed Arch with the "2012.12.02" (I don't know if it exists or not) and you do **pacman -Syu** the 2/11/2012, you'll have exactly the same than a user who has installed with 2012.11.02 ISO... The only point what may change is the installer, but of course it doesn't affect an existing user as he has installed Arch already ;)

---

### Post by Aaron Christianson on 2012-11-22
> **vasa1 said:**
> allow Arch users plenty time to hang around on the Ubuntu Forums ;)
But many of the Arch wikis are really well put together.
I use and enjoy both >8^p.  I dual boot between Arch and 12.04 on this laptop.

---

### Post by Aaron Christianson on 2012-11-22
> **nothingspecial said:**
> I did install Arch once a few years back to see what all the fuss was about. After about 3 hours I looked up at my screen and saw that I had set it up to look and behave exactly like I had Ubuntu set up. There was no discernable difference when going about my normal daily stuff.

So what was the point of those 3 hours ?
Depends on your situation. Possibilities include:

* you want new software as soon as it is released upstream
* you want access to more obscure software projects via your package manager(if it's out there, it's in the AUR)
* you want no-hassle installation of weird drivers (AUR, again)
* you are interested in optimizing your system and cutting down services you don't use (also possible in Ubuntu, but is the "default behavior" of Arch, though not to the extent that it is in Gentoo)

If you are not interested in any of that, then there was no point to those three hours.

> **Chdslv said:**
> You can learn a lot by installing your Ubuntu from the mini.iso, not just installing that or this desktop. The other thing is that the Ubuntu applications are very sure, while Arch ones might break as the Arch devs might do something "strange" waking up. 

There were five releases every month, and who knows what they'd come up next. 

Not every distro maker installs Arch from scratch, for example, Bridge Linux was worked off Archbang...
eh... nothing your saying is really making any sense. Arch applications do not break. They only put out release-quality software. Software upgrades may break compatibility with older versions, but that is an upstream issue.  If it causes a serious problem, they always post about it on the front page of their website, and the fix usually takes five minutes (the switch to systemd being the exception, but it had to be done, and Arch users can handle it with minimal whining, for the most part; whereas half of ubuntu users scream and cry if you move a button).

---

### Post by NikTh on 2012-11-22
Well, for me , Arch Linux is a learning course. I describe Arch Wiki like the Ultimate Linux Learning resource. 
For me it was and it will be a learning course. I've  learned recently about systemd , how to write my own services ..etc. Yes , Arch Linux needs reading all the time. 

The bleeding edge thing... hmm is a bit dangerous, yes. I use Arch with LXDE and I haven't any particular problems , but when I used gnome.. hah! .. desktop was breaking  almost at every update (I'm speaking especially for themes , Gnome 3.6.3). 

Ubuntu can be a learning course also , if you install only the core (mini.iso).
You can build the Environment as you want , with the packages you want , but the difference between Arch Linux and Ubuntu is that Arch Linux has not even the packages which on Ubuntu are considered as standard . eg: bash-completion , sudo. 

Arch Linux is my alternate distribution 
but of course Ubuntu will remain my main OS ( I believe that is more stable) :)

---

### Post by sffvba[e0rt on 2012-11-22
I have done the Arch thing a few times and as has been stated, the wiki is awesome.

It isn't for me however, but more power to those that choose it :)


404

---

### Post by mips on 2012-11-22
Seems there's some bashing going on here. If you need a press and click distro to install then go for it but don't bash Arch for what it is because you lack in skills.

Some might say you can do the same install using the ubuntu minimal install iso image but that is simply not true imho. Yes I've tried them all.

---

### Post by Aaron Christianson on 2012-11-22
> **NikTh said:**
> The bleeding edge thing... hmm is a bit dangerous, yes.
"Dangerous" is quite relative. The worst that usually happens is you might loose the ability to use X until you do something about it (usually something that takes a couple of minutes). 

Arch isn't any more likely to cause data loss than any other system. Indeed, if anything, the constant updates to kernel and disk utilities mean your data is always as safe as possible, not to mention that, if you follow the beginners wiki, you have an independent /home partition, which is much better for preserving data than using a single partition (though it is a slightly less efficient use of space).

Arch doesn't shield users from upstream changes like Ubuntu does, but it doesn't hang you out to dry either.

---

### Post by Pogeymanz on 2012-11-28
Arch seems to bring out some emotions from people. I've seen Arch FUD for years and I'm honestly surprised (I shouldn't be) that I still see some of the same stuff being said.

Before I begin my rant, I'd like to address those who installed Arch and then immediately uninstalled it. Um, duh? Did you expect Gnome or KDE to be different on Arch than on Ubuntu? I honestly have no idea why someone would evaluate a distribution based solely on the installation procedure. If that were the case, Windows would be the best OS by far.

Arch is a not a "programmer's" distro. Nor is it an "expert's" distro. There are various ways in which Arch differs from all other GNU/Linux distributions. If you like those differences, you should use Arch. If you don't, you should use one of the others. Allow me to list the most relevant differences.

1. _The installation:_
The installation process in Arch is probably the thing that people talk about the most, but to me is the least important of all. How many times during the day do you reinstall your OS? How many times per week? The installation is pretty easy for 90% of setups. Just follow the beginner's guide and you will have a working system within an hour (give or take download time for updates).

I have a desktop that has had the same Arch installation on it since 2007. Think about that. I have not reinstalled an OS on that machine in over 5 years. Yet, that machine has newer packages than one that has Ubuntu 12.10 installed. Furthermore, if I had been running Ubuntu since 2007, I would've had to reinstall (or dist-upgrade, which used to always screw my stuff up) 10 times.

Which brings me to...

2. _Maintenance/Administration:_
Keeping your Arch installation running smoothly is more involved than Ubuntu. Being a rolling release distro, Arch has to find a way to push big changes in updates without screwing up peoples' machines. Arch's package manager, pacman, is usually pretty good at aborting itself when it runs into a conflict. Then, you open your favorite web browser to the Arch homepage and there will be a message saying that updating package X requires you to manually do Y and Z before updating.

Now, Arch updates have always been smooth for me. However, in the last year, we saw some pretty big changes, such as the addition of /run and /var/run, the symlinking of /bin and /sbin to /usr/bin and /usr/sbin, the deprecation of Grub Legacy, and the switch to systemd. These updates caused some people headaches.

So, it has been a rough year for Arch users. Hopefully, the dust is settling and we'll get back to much quieter updates.

There is a bright side. Before undertaking scary updates like the ones mentioned above, you could pretend Arch is like Ubuntu and just wait for the next monthly ISO to come out and reinstall! It'll be just like the old days when you used to run Ubuntu or Fedora.

2.1 _Stability:_
So updates can rock the boat when it comes to changing the way the system does stuff. But what about bugs and crashes with all that fresh cutting-edge software? First of all, Arch does not package software that is not deemed stable by its developers*. For example, Compiz is at version 0.8.8 right now, in the Arch repos. That is because the 0.9.x branch was declared a testing version by the developers. The next stable version is supposed to be 1.0. So, you aren't running beta software. If you find a bug, complain to the upstream developers for making a crappy product. Second, all software goes through a testing repository until it is deemed stable by users brave enough to use the testing repository.

*e17 and WINE are both technically not the stable versions, but the WINE devs say that users SHOULD be using the non-stable version in most cases.

3. _Speed:_
There is a speed difference between Arch and Ubuntu. It's true. It isn't huge, and you aren't going to see it in any stupid Phoronix benchmarks, but it's there. Ubuntu patches their packages extensively. Especially GTK/Gnome based packages. This usually results in larger binaries and libraries, which translates into longer loading time for your applications and more memory consumed. Those of you using SSDs or just pretty new hardware wont notice. But if you load Arch and Ubuntu up on a five year old computer, with 1GB of RAM or less, and a mechanical hard drive, and install XFCE or Gnome Shell as your DE, you will be able to feel a difference. Here is an old post from K.Mandla's blog on Gnome2's memory needs on Arch vs. Ubuntu: [https://kmandla.wordpress.com/2010/03/19/a-clarification-gnome-on-arch/](https://kmandla.wordpress.com/2010/03/19/a-clarification-gnome-on-arch/)

4. _Apt vs. Pacman_
This is a matter of taste. I'm sure apt is more powerful and flexible than pacman. But in Ubuntu, at least the last time I used it, apt tries to install optional dependencies by default. I don't want that. It also automatically starts daemons after you install one. I don't want that either. I just want you to install stuff, I'll take care of actually starting it if I want it running right now. Why doesn't apt go ahead and launch Chromium for you after you install it? And in older Ubuntu's (I'm not sure about the last few versions), it would try to automatically update your grub menu for you when you did a dist upgrade. For some reason, it always messed it up for me and for family members who aren't computer savvy, but wanted to try an "easy" Linux OS.

5. _Man Power/Number of Developers_
Arch is a small project, yes. But I've had some moments with Ubuntu that made me wonder what excuses Canonical could make to explain some things (like the Grub menu update script mentioned above). Part of the reason that Arch can exist with such a small developer base is their K.I.S.S. philosophy. Arch delivers nearly-vanilla packages, so they don't need programmers to write a ton of patches to GTK, the way that Ubuntu does. They don't want an auto-install script on the ISO, so they don't need developers for that, either. And they aren't targeting the enterprise Linux users the way that Ubuntu is, so they don't need marketing people or sales reps or tech support. It's just not part of the deal.

So, there you have it. My insanely long-winded Arch post. I spent way too much time on this, so I hope somebody reads it.

The tl;dr of it all is that Arch is like a reliable older car that you have to maintain by changing the oil and replacing the filters, whereas Ubuntu is like leasing a new luxury sedan and driving it into the ground for a couple of years before you get a new one.

---

### Post by KiwiNZ on 2012-11-28
Linux has been around for over 20 years,one should not have to wrestle for hours to make a Distro  install and work. If it takes that then it's simply  unacceptable.

---

### Post by offgridguy on 2012-11-28
> **kiwinz said:**
> linux has been around for over 20 years,one should not have to wrestle for hours to make a distro  install and work. If it takes that then it simply is unacceptable. +1

---

### Post by viperdvman on 2012-11-28
I don't know a whole lot about it myself, other than it's a very stable rolling release distro. I know a lot of people who stand by it.

I myself am gonna give it a shot this winter break... utilizing my unused 3rd linux partition. It'll be an experience, that's for sure.

---

### Post by lykwydchykyn on 2012-11-29
> **KiwiNZ said:**
> Linux has been around for over 20 years,one should not have to wrestle for hours to make a Distro  install and work. If it takes that then it's simply  unacceptable.

I'm not an Arch user, but as someone who runs a considerably non-stock desktop setup, I can appreciate the value of an approach like Arch.  The reason I try it now and then is because I find myself having to remove, reconfigure, or backport enough from the standard K/Ubuntu install that it seems like it might be worth it to do the Arch thing instead.

In the end I find I just like APT and ubuntu's compatibility with stuff better.

If you're happy with the stock install, and need OS setups to take less than 20 minutes, no problem.  It's good that we have distros that can cover that.  

Nothing unacceptable about having a distro or two that caters to the picky crowd with time to invest.

---

### Post by smellyman on 2012-11-29
> **KiwiNZ said:**
> Linux has been around for over 20 years,one should not have to wrestle for hours to make a Distro install and work. If it takes that then it's simply unacceptable.
 
Quick install OS's have been around for years.  Not being able to customize it to my liking from the beginning is unacceptable.

---

### Post by LiamOS on 2012-11-29
> **smellyman said:**
> quick install os's have been around for years.  Not being able to customize it to my liking from the beginning is unacceptable.
+2

---

### Post by Linuxisfast on 2012-11-29
Hi, can any of the arch experts here can tell me how to setup samba with ease as I do in Ubuntu. I would truly appreciate it, the arch wiki way for samba server setup and sharing with KDE doesn't work for me in any way.

---

### Post by Pogeymanz on 2012-11-29
> **Linuxisfast said:**
> Hi, can any of the arch experts here can tell me how to setup samba with ease as I do in Ubuntu. I would truly appreciate it, the arch wiki way for samba server setup and sharing with KDE doesn't work for me in any way.

Hi,

Unfortunately, my Samba needs are very, very simple, so I just edit the main config file once and I'm done. I've never used a graphical tool because I just don't need the more advanced options. I hope that someone else can help you all the way, but maybe you can start with looking at mine?
```
[global]
   workgroup = HOME
   server string = Samba Server
   security = share
   load printers = yes
   log file = /var/log/samba/%m.log
   max log size = 50
   dns proxy = no 

[homes]
   comment = Home Directories
   browseable = no
   writable = yes

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
   guest ok = no
   writable = no
   printable = yes

[public]
   comment = Public Stuff
   path = /home/shared
   public = yes
   writable = yes 
   printable = no
```

This will give you pretty basic printer sharing and it shares all files placed in /home/shared. It is not very secure, as it doesn't require users to have an account on the machine or use a password, etc.

That's all I ever use Samba for, so again, I apologize for not being able to help you more.

Can you describe what steps you perform exactly and what goes wrong?

---

### Post by Linuxisfast on 2012-11-29
> **Pogeymanz said:**
> Hi,

Unfortunately, my Samba needs are very, very simple, so I just edit the main config file once and I'm done. I've never used a graphical tool because I just don't need the more advanced options. I hope that someone else can help you all the way, but maybe you can start with looking at mine?
```
[global]
   workgroup = HOME
   server string = Samba Server
   security = share
   load printers = yes
   log file = /var/log/samba/%m.log
   max log size = 50
   dns proxy = no 

[homes]
   comment = Home Directories
   browseable = no
   writable = yes

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
   guest ok = no
   writable = no
   printable = yes

[public]
   comment = Public Stuff
   path = /home/shared
   public = yes
   writable = yes 
   printable = no
```

This will give you pretty basic printer sharing and it shares all files placed in /home/shared. It is not very secure, as it doesn't require users to have an account on the machine or use a password, etc.

That's all I ever use Samba for, so again, I apologize for not being able to help you more.

Can you describe what steps you perform exactly and what goes wrong?


Thanks for the prompt reply, this is the exact smb.conf file I use with my Chakra which also has kde-network installed, try as I might, the kde shares don't stick, also my Ubuntu machines can't access the files in Chakra Arch machines although the Chakra can access all shared files in the Ubuntu machines. Do I need to change the permissions of the home folder?

---

### Post by ratcheer on 2012-11-29
I used Arch Linux for a long time. In general, I liked it very much, but I finally gave up on it a couple of months ago for several reasons.

I couldn't get it to handle my multi-device btrfs filesystem, properly. Yes, I followed the wiki instructions to load the btrfs scan hook. But it always failed to mount during boot-up; I would have to mount it manually, then boot would proceed to completion. Neither Ubuntu, Sabayon, nor Debian had this problem.

I don't like systemd. That's all I'm going to say about that.

There were continual upgrade glitches (by continual, I mean something every week or two). You have to read their news before upgrading every day, or you may get into some situation that is hard to work back out of. Other distros seem to handle these things better.

I settled on **Siduction Linux**, which is based on Debian sid. It is also a rolling release and in many ways is even more leading edge than Arch. It handles btrfs perfectly. Daily upgrades are much smoother. And it still uses SysV init. I'm sure it's not perfect for everyone, but it is the best I have found for me, so far. I have just about quit distro hopping.

Tim

---

### Post by pkadeel on 2012-11-29
nope. definitely not for an End User (not an End Admin) like me.

---

### Post by Pogeymanz on 2012-11-29
> **Linuxisfast said:**
> Thanks for the prompt reply, this is the exact smb.conf file I use with my Chakra which also has kde-network installed, try as I might, the kde shares don't stick, also my Ubuntu machines can't access the files in Chakra Arch machines although the Chakra can access all shared files in the Ubuntu machines. Do I need to change the permissions of the home folder?

I believe so, yes. I changed my /home/shared folder's permissions to 777 (read+write+execute for everyone).

---

### Post by Linuxisfast on 2012-11-29
> **Pogeymanz said:**
> I believe so, yes. I changed my /home/shared folder's permissions to 777 (read+write+execute for everyone).

I will give that a try then, thanks.

---

### Post by mamamia88 on 2012-11-29
> **COMECON said:**
> Hi!
I just finally installed Arch Linux... After a year of decisions, I finally did it! After installing it on VM, where all looks gorgeous, a few times, I decided it! I removed Fedora, which I installed this week-end (poor Fedora), and I took 4 hours installing, configuring, doing other stuff and doing homework with it. 
It's very nice to see that you can install a system without a graphical interface, and install a DE later (such as XFCE, as I did). But... according to the KISS definition, Arch has nothing. I thought it wasn't a problem, as you can just do **pacman -S packagename** and install something, like **pacman -S firefox**. But... Not only happened with applications, of course. I stayed... 2 hours of those 4 to configure the WiFi network and doing odd scripts for systemd, and discovering that neither NetworkManager nor Wicd worked, I saw another problem... The sound, how the hell I configure the sound. And the printer. And the multimedia keys. And all!
It's not a problem if you have a lot of time, and it's very... educational, I probably learnt more this afternoon that in the last month. But I don't have a lot of time, and I can't just... doing configure things all the time, I have work to do! 
So, for me, I think it's not for me! I like its KISS philosophy, and specially the rolling release, but I preffer more things out-of-the-box. I like it, and I'll keep it on my sda8 partition (thanks to god I divided a 30GB partition where Fedora was into 2 15GB partitions) and I'll install some other thing in the other. And, of course, I'll keep Ubuntu 12.04 as my main system :)
What about you? Have you tried Arch? Did you like it?
sound worked out of the box for me.  i feel your pain on network manager.   i gave up and used netcfg.   works great.   once you get the hang of it it's really not that difficult.  yest it can be time consuming but once you know exactly what you want it's easy.  what i did was make a list of everything i needed to install after install.  once install was done i typed pacman -S list of items and took my dog on a walk.   when i got home it was done.  Then after that all i had to do was copy .xinitrc to my home folder and uncomment the xfce line and configure slim then enable slim.service and reboot.

---

### Post by kevinmchapman on 2012-11-29
> **KiwiNZ said:**
> Linux has been around for over 20 years,one should not have to wrestle for hours to make a Distro  install and work. If it takes that then it's simply  unacceptable.

A bit like the arguments over Unity, no-one is forcing anyone else. Arch is there for those of us who want the extra control. Others pick Debian or Slackware for similar, but not quite the same, reasons. I believe several pages ago there was a list of those it was not aimed at...

There, I said all that without even mentioning some of the install horror stories I see on this forum :)

---

### Post by snowpine on 2012-11-29
It takes (average) a couple of hours to install Arch.
Maybe it only takes 20 minutes to install Ubuntu, but then a lot of users spend a couple of hours installing a whole bunch of PPA's to get the latest software that Arch would have given them by default, then troubleshooting malformed entries in their /etc/apt/sources.list (one of the most frequently-asked questions here on these forums).

---

### Post by Pogeymanz on 2012-11-29
> **snowpine said:**
> It takes (average) a couple of hours to install Arch.
Maybe it only takes 20 minutes to install Ubuntu, but then a lot of users spend a couple of hours installing a whole bunch of PPA's to get the latest software that Arch would have given them by default, then troubleshooting malformed entries in their /etc/apt/sources.list (one of the most frequently-asked questions here on these forums).

True. How many of us really just install an OS and leave it completely default anyway?

It would take me hours to set up a Windows or OSX machine too. I have to install the things I want, uninstall the things I don't want (if I can), change where the dock is in OSX, put words back in the taskbar in Win7, change all the sizes of everything in Windows, put the classic theme back, etc.

There are several videos on youtube of people installing Arch in five minutes. The install time doesn't matter. Unless something goes wrong, it probably takes close to the same amount of time for me to fully set up Arch or Ubuntu.

---

### Post by mamamia88 on 2012-11-29
> **KiwiNZ said:**
> Linux has been around for over 20 years,one should not have to wrestle for hours to make a Distro  install and work. If it takes that then it's simply  unacceptable.

it took me about 2 hours to get everything up and working and it was super easy because of a well written wiki page.   most of that time was downloading packages. how to install arch 1. partition with gparted live. mkdir /mnt/whatever that isn't root partition.  mount partitions, pacstrap base system, chroot into system and configure simple files,install bootloader, reboot,pacman -S everything you need (make a list),go take a shower,cp /etc/skel/.xinitrc /home/user,nano /home/user/.xinitrc and uncomment your DE, systemctl enable slim.service,reboot, login and enjoy.  sounds complicated but it isn't.

---

### Post by Bart_D on 2012-11-29
> **Pogeymanz said:**
> .....There are several videos on youtube of people installing Arch in five minutes. The install time doesn't matter. Unless something goes wrong, it probably takes close to the same amount of time for me to fully set up Arch or Ubuntu.

From my experience with installing Arch, once I figured out all the steps/problems, the installation time was not a problem. Installation was a breeze after that because I had memorized the steps from having to re-start the procedure so many times due to numerous errors/problems along the way. But with Ubuntu, I would have been able to do it the first time and get it right the first time...and the time required would have been a fraction of that for Arch. That's the difference.

> **kevinmchapman said:**
> A bit like the arguments over Unity, no-one is forcing anyone else. Arch is there for those of us who want the extra control.....

Yeah, but with that comes a hefty price in terms of more-frequent breakage. If you are a hobbyist and like fixing things all the time, then the extra control is worth it. If not, then I'm sorry but it just isn't.....and you know it.

This is, quite frankly, what a lot of* Arch users don't get when they say that the high degree of customizability is what makes Arch so great.......it might, for them, but not for the vast majority. Such a shame that this gets lost in the discussion, almost always.

* though not all

---

### Post by kevinmchapman on 2012-11-29
> **Bart_D said:**
> 
Yeah, but with that comes a hefty price in terms of more-frequent breakage. If you are a hobbyist and like fixing things all the time, then the extra control is worth it. If not, then I'm sorry but it just isn't.....and you know it.

This is, quite frankly, what a lot of* Arch users don't get when they say that the high degree of customizability is what makes Arch so great.......it might, for them, but not for the vast majority. Such a shame that this gets lost in the discussion, almost always.

* though not all

I shall merely point out that the thread title is "Is Arch Linux for you?", not "Is Arch Linux for everyone?"

---

### Post by KdotJ on 2012-11-29
Just to add in my experiences...

I installed Arch around 3 years a go and used it exclusively for  year or so. Their documentation is absolutely amazing, and you can find the answers and fixes for most of the problems that you run into. It was blazingly fast and pacman, in my opinion, is a fantastic package manager.

I had my breakages, as I had fully expected to get. Sometimes got frustrated with trying to fix things that broke as a knock on effects from other breaks, but the whole ride made me understand linux a lot more. 

In the end I moved away from using Arch, purely because I wanted to try something different and not because it forced me out. I now use Crunchbang and have been for a while. Maybe I am becoming lazy now, but it's nice to just have a system that works and I don't have to fix things that I didn't break.

I still fire Arch up in a VM though every know and then to have a little play.

As said by many, it's not for everyone, but I do think that if you have an interest in Linux and some spare time, it is very beneficial to play with, and also very rewarding when you get it all set up.

---

### Post by Rumor on 2012-11-29
> **Pogeymanz said:**
> So, there you have it. My insanely long-winded Arch post. I spent way too much time on this, so I hope somebody reads it.

That was a very good summary of the major talking points I see in different discussions about the various aspects of Arch.

I've been an Arch user for over five years and have used it both as a home desktop distribution and on production systems and servers. In that time I have had one system breakage, and only one. And that was due more to my own short-cutting attempts than to any shortcomings on the part of Arch.

Arch is what you make it, nothing more. It's a great distro for tweakers and it is also well suited to someone like myself who wants their OS to stay out of their way so they can go on about their work.

So yes, Arch is for me. But, every user's needs and expectations are different.

---

### Post by Aaron Christianson on 2012-12-01
While Arch is a bit more time consuming to install and maintenance requires a bit more intervention, you only have to install it once, and the amount of maintenance definitely amounts to less than what you'd be doing if you  reinstall Ubuntu every six months. Of course, there are things that can be trying on Arch, so my strategy is to put Ubuntu LTS on a 5GB partition and use it when something doesn't work properly on Arch (though I must say that I have an easier time doing most things on Arch than Ubuntu, and I could probably overcome almost anything If I used a desktop environment with Arch; something else I've opted to avoid).

---

### Post by viper250 on 2012-12-02
i installed cinnarch on my test machine successfully and its the first version i have had any luck with as far as installation issues
its a lovely os and does everything but dvd playback.
i will investigate it later to get the proper codec info

---

### Post by ratcheer on 2012-12-03
> **viper250 said:**
> 
its a lovely os and does everything but dvd playback.
i will investigate it later to get the proper codec info

Most likely, you just need to find and install libdvdcss2.

Tim

---

### Post by mamamia88 on 2012-12-03
well the arch wiki is so good that you don't really have to do any investigating.  just google whatever you need followed by arch wiki and there's a good chance it will show up. for the guy above very simple dvd playback install a few packages and add yourself to optical group.  source [https://wiki.archlinux.org/index.php/DVD_Playing](https://wiki.archlinux.org/index.php/DVD_Playing)

---

### Post by viper250 on 2012-12-03
thank you for the info guys
i will install it when i get the chance to 
between work and moderating other forums i usually don't have a lot of time left
damn spammers! grrrr.:frown:

---

### Post by VooDooSyxx on 2012-12-04
I'm just going to say it's definitely not for me these days. My desire to tweak minute system details and run the latest and greatest Linux apps as soon as they hit sourceforge was taken care of back in the late 90's and early 00's. Nowadays I need a stable system to get stuff done and just don't have the time for all that any more. 

That said, one of my roommates has been using it for years and loves it. About once a month or so, it breaks in new and exciting ways and I get to hear a stream of profanities for a couple hours while he fixes it up, but the next day he's right back to lovin it.

---

