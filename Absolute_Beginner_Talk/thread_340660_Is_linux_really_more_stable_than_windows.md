---
title: "Is linux really more stable than windows?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-01-17
For years I always heard how stable linux is and how linux users would come down on window's bluescreen of death.  Well with that being said I recall the blue screen of death often with windows 95,95, and ME.  I've been using Windows XP for 5 years and I can only remember one time that it frooze that I had to power it off completely.

Now linux has frozen on me twice on two completely different machine, running two completely different programs.  It's crashed so bad that I'm forced to push the power button.  The first time I thought it was just a weird uncommon thing that happened, but just recently my family member told me it happened to him on even a third machine.   So it makes me wonder, how stable is linux?

The last time if crashed, I was running kubuntu and I had swiftfox running and I only went to a website when the entire system locked up.  I honestly just expected linux to be more stable than what I'm experiencing.

---

### Post by SunnyRabbiera on 2007-01-17
well sometimes linux does conk out... have you inspected your hard drives though?
have you actually opened your computer up and see if dust and debris have built up?
This is another reason why computers kill out, as your computer needs to breath and with dust and stuff it can easily overheat...

---

### Post by ComplexNumber on 2007-01-17
**bone2006**
2 questions:
do you  tinker a lot with linux? do you tinker a  lot with windows?

---

### Post by SunnyRabbiera on 2007-01-17
really no OS is perfect, I have had linux freeze up on me and kill out... but its mostly from what I have done then the fualt of the OS.

---

### Post by Perfect Storm on 2007-01-17
If you want more stable then roll back to 6.06 (dapper) LTS. There's a reason why Edgy is called edgy ;)

Honestly I have never one crash on my linux machine, only the one(s) which a coursed by me when I'm messing around with stuff or if I use an alpha applications that I'm aware can make trouble.

Other than that KDE is more "unstable" is my experience. Try give Gnome or XFCE a go.

---

### Post by milton1 on 2007-01-17
I notice that you are using edgy. Edgy is not the most stable release of ubuntu, and as such is is prone to some problems. In general, though, linux is more stable due to the cleaner dependancy structure of unix-based operating systems. You have, I am sure, encountered the repeated "restart your computer now" messages that come with every upgrade to windows. These are necessary because every program in windows is tied in some funny way to every other program or service. This is why one crashing program can bring down the whole system with ease. A good linux system does not suffer from this problem. If you are continuing to have problems with edgy, try installing dapper instead. It is much more stable.

---

### Post by SunnyRabbiera on 2007-01-17
well I had dapper kill on me too, but it really depends on what you do and all that...

---

### Post by K.Mandla on 2007-01-17
For what I've seen, either OS can be kneecapped rather quickly, if you know what you're going. That being said, I had far more random crapouts on Windows than I ever do with Linux (of any variety, Ubuntu or not). 

I think it's going to depend on the same things it always depends on: Your hardware, your usage patterns, your workload and your degree of expertise. If you throw together incompatible parts, or make heavy demands on your machine, or if you just don't know what you're doing (in either OS), you run the risk of a crashtastic machine.  

Just my $0.02 (and it's probably not worth much more than that ;) ).

---

### Post by irish_flu on 2007-01-17
I'm not really sure what you're asking (or if it's rhetorical), but I'll add my own expreriences, if it helps; I have two Linux boxes, a Windows XP box, and a laptop with XP running at my house.  None of them hardly ever experience a "crash"  (although the laptop occasionally hangs on shutdown).

Most folks who are informed enough to make a choice pick the operating system they feel best serves their needs, and works the best for them.


You're having problems with Linux, and that stinks.  If you tell us what went down, somebody here might be able to help.

I'm glad your experience with XP was good, mine generally has been too, but I'm sure you realize that some people *do* have problems with their XP box (given the number of people whose job it is to support Windows, if nothing else).

---

### Post by bone2006 on 2007-01-17
SunnyRabbiera:  One of the systems is less than 6 months old and another one is only a few weeks old.  The one that I'm referring to crashing recently is probably 5 years old.   I'm not seeing a correlation with the hardware and reason for it crashing, especially if windows can handle it, I expect to use an operating system as well.

milton1: I'm not sure if you are referring to older versions of windows, but in windows XP there are software that you have to reboot to install, so that's true.  But in 5 years of using Windows XP I really can maybe recall it crashing 1 single time, if that.  I spend 8 hours a day on windows XP for work and to say it's not stable I think is crazy.  These claims seem to come from maybe linux users who used windows 95,98 or ME.

---

### Post by mcduck on 2007-01-17
Linux itself is very stable, but that doesn't mean that all software running on Linux is stable. Firefox/Swiftfox has some issues, and some extensions and plugins can make it even worse.

Btw, the reason why people get less BSODs with XP than with previous windows versions is that older windows versions used bluescreen for almost all errors while XP only BSODs for more serious issues and usually just uses some popup error message instead..

So with older windows versions you could often just alt-tab out of the blue screen and continue working when in XP bluescreen usually means that you need to reboot.

---

### Post by Maki_doda on 2007-01-17
I only have problems whit ubuntu when i tinker to much and i do something wrong.
Also you need to check your hardware,i have problem booting up ubuntu and after an hour i find out that my network card was broken

---

### Post by aidanr on 2007-01-17
windows bluescreen is more common than a kernel panic, a linux box can look to have frozen up completely, but usually a few keystrokes can get you up and running without restarting the box

for example you can switch to another tty (ctrl + alt + F#) and kill the offending process
or restart the x sever, ctrl + alt + backspace
or if that doesn't work alt + sysreq + s,u,k should work in all cases but a kernel panic

---

### Post by SunnyRabbiera on 2007-01-17
are you a "power user"?
I think maybe the others are right and you should downgrade to dapper...

---

### Post by Shatrat on 2007-01-17
I think most problems come from applications rather than the operating system.  In linux it is easier to kill an application using top or xkill, or if that doesn't work just restart the X server using ctrl alt backspace.  In windows if the screen stops responding you usually need to reboot.

Also, you can run linux for years without rebooting at all, as long as you dont change the kernel itself.  This isnt a big deal for Joe Sixpacks laptop, but for a file server or something it is certainly nice to have.  If you consider security to be part of stabilty then linux looks even better.

---

### Post by riven0 on 2007-01-17
Well, I just had to say that one of the reasons I switched over to Linux is because XP - yes, XP! - kept gave me the BSOD every morning. This is not a joke. I'm still not completely sure what the problem is, but I'm guessing it was hardware related. I was running XP on a comp I built from the ground up. It has an AMD 3000+, ATI 9200, Western Digital 40GB and 512Mbgs of Kingston RAM. So I'm not really sure what was causing instability problems, but it was bad.

Of course, I got fed up and now I've completely converted over to Linux. The only crashes I've experience is when I tweak something that causes Gnome to freeze up. In that case, though, I just do CTRL + ALT + Backspace to get to the login screen and all is well. 

So everyone's experience is different, but my five year experience with XP has been particularly horrendous.

---

### Post by aysiu on 2007-01-17
Instability and freezing could have something to do with not having the proper drivers. I'd experienced some random (unrecoverable) freezing in the past because of using the *nv* drivers instead of the *nvidia* drivers. Now that I'm using *nvidia*, I've yet to have an unrecoverable freeze-up.

The other thing someone mentioned earlier--Linux (the kernel) is extremely stable. X (the graphical interface on top of it) and KDE and Gnome and the applications associated with those environments are not necessarily stable, though.

---

### Post by rabid emu on 2007-01-17
To quote HAL 9000 from 2001: A Space Oddyssy: "the problem can only be attributed to human error."  That is to say, if something crashes, it's almost always the user's fault in some way. They're either using alpha software that they have no right to complain about, or they tinkered, or something like that.  Even if it's a case of some lib files or other dependencies missing, or something like that, it's not hard to find out what's wrong from a terminal and correct it without ever shutting down the computer.  When it gets to the point that the computer seems to be hung, you could have definately done something better.  Now I'm not saying you're a noob or anything like that because I fall prey to all of these faults too; I've had several linux distros crash on be before, but each time it was because I didn't know what I was doing at the time, and I used the experience to learn more.  Plus I love using alpha software because it's new and great :P  In fact I'm typing this on Feisty Herd 2 which is remarkably stable so far, although bootup takes a minute 20 seconds for Kubuntu which is really slow.

For example, if the system appears 'hung' (like an XP system would) it's often not the OS itself that is dead but just the X server.  ctrl + alt + delete restarts X, and you can also go into a virtual terminal (ctrl + alt + f1-6) and kill X and restart it, or even do 'dpkg-reconfigure xserver-xorg' (that command has bailed me out a lot while configging graphics cards and resolutions).  Also, in a virtual terminal you can open 'top' and see what program you think is hung, and kill it.  Or you can safely restart the system from the terminal with 'sudo shutdown -r now' so you won't cause any undue damage from a hard reboot.

Ubuntu is probably a little less stable than some other distributions of Linux due to the fact that it uses more recent software.  If you want a rock-solid system, go for slackware or even Debian 3.1, but these are markedly harder to configure.  My point is, Linux isn't to blame.  The kernel is extremely stable.  If your system is unstable, you ought to be able to figure out why and fix it with a little research (unlike winblows)

---

### Post by old_geekster on 2007-01-17
> **bone2006 said:**
> For years I always heard how stable linux is and how linux users would come down on window's bluescreen of death.  Well with that being said I recall the blue screen of death often with windows 95,95, and ME.  I've been using Windows XP for 5 years and I can only remember one time that it frooze that I had to power it off completely.

Now linux has frozen on me twice on two completely different machine, running two completely different programs.  It's crashed so bad that I'm forced to push the power button.  The first time I thought it was just a weird uncommon thing that happened, but just recently my family member told me it happened to him on even a third machine.   So it makes me wonder, how stable is linux?

The last time if crashed, I was running kubuntu and I had swiftfox running and I only went to a website when the entire system locked up.  I honestly just expected linux to be more stable than what I'm experiencing.
I have found the same to be true.

I began using WinXP in 2001.  I have it on two rigs.  I have yet to have a BSOD that I didn't cause.  Yes, as an enthusiast, gamer, I do a bunch of tweaking.  For this reason, I figure a BSOD once in awhile is acceptable, but I simply don't have them.  My computer doesn't boot when I have the settings incorrect, but I reboot into the BIOS and change them.  It does freeze periodically, when a game has not been patched.

I have used SuSE 10 (dual-boot same drive) and now Ubuntu 6.10 Edgy (dual-boot different drives) and have had freezes with both, but no BSOD.  As for tweaking, I am far too new to Ubuntu to do anything but try to survive the learning curve.  You can see from my sig that I have a fairly high-end system.  Ubuntu recognized all of my componets and set them up so they are workable.  I say workable because several of the peripherals (Logitech Mx700 Duo) don't have all of the functions that are built-in to them.  Hopefully, I will find some fixes once I know my way around.

With that said, I would definitely be using Linux as my primary OS, however, if it wasn't for gaming.  My number one reason for wanting to use Linux? --- the PRICE!!  How can you beat it.  

Considrering that it is being develoved by folks who are some of the best in the world, it is amazing to me.  They are definitely people with principles.

To say it is more stable, is not necessarily true for me.  Do I enjoy the challenges it provides, yes!

---

### Post by PhilJ on 2007-01-17
I have only had it happen to me once using Dapper and I did it , but I could crash windows no problem. Blue screen of death?  many many times, many  many times:twisted: 

Phil

---

### Post by chick penguin on 2007-01-17
I use XP at my work on a custom made box. I spent a great deal of time doing the best I could to make it secure and practice safe surfing and etc. I have found it stable compared to W98se and I really have not had problems with it crashing or freezing up. Basically I have enjoyed my XP experience though some of the ways in which it works I find a bit annoying. I run as a limited user and that has some issues as far as I am concerned. 
I am experimenting with Dapper on an old old AsusP5A-B Amd K6 2/500 and so I cannot really do a proper comparison. I like the way I do not have to reboot and hey I am getting into the terminal..I hope its not fatal!:)

---

### Post by Hendrixski on 2007-01-17
> **ComplexNumber said:**
> **bone2006**
2 questions:
do you  tinker a lot with linux? do you tinker a  lot with windows?

That's a good point!  Most people don't tinker with windows as much as they with Linux.  I get a BSOD in Windows all the time because as a Systems Consultant (aka 'traveling software developer') I have to tinker with my environment.  I chose to work on Linux whenever I'm not working on operating system specific code.

---

### Post by josys36 on 2007-01-17
There has only been one time where my Ubuntu install had to be hard shutdown. Now I can also say the same thing for my VMWare image of XP. So more stable is a debate that I feel will run on until the Sun has turned all of it's Hydrogen into Helium. With Visa this may change.

Who knows? I hear this go back and forth all the time. Oh my XP sucked and Linux is cool. Then I also here I hate Linux back to Windows for me. I guess it all depends on your situation and your experiences. Mine have been good in both areas, but I know that there have been problems in both. 

Jason

---

### Post by Crakie on 2007-01-17
I've been having many crashes and freezes with Ubuntu, much more than XP, which I consider to be very stable. The thing is, I have pretty new hardware and Linux does not support it very well. Not that I would expect it to; the developers do what they can. Slowly but surely, I've learned to configure my system (a parameter in grub here and an automounted swap drive there... ) and it's really stable now... although some updates tend to screw it up.

I cannot afford to remove Windows altogether from my computer... I need it to go on the internet to find out what to do when things go wrong. (Yes I know, I could use the LiveCD for that as well...)

On a side note... I can reinstall Ubuntu from scratch and restore to the way it was within an hour or two ;)

---

### Post by davebgimp on 2007-01-17
Yeah... it's more stable. If a program on the Desktop freezes or boggles X, you can fire up a terminal or shell in and kill and restart processes. If one thing is mucking up, it doesn't necessarily mean the whole box is screwed. I mess with my Linux installs often and naturally screw things up regularly, but instead of having to reboot or reinstall, I kill processes. A few freezing programs does not define an OS.

---

### Post by phr0ze on 2007-01-17
I hate to say it but I believe XP is more stable. Yes, ubuntu crashes can be attributed to beta software, bad drivers and such, but the same can be said for anyone who has experienced crashes in Windows.

I blame the hardware manufacturers for not providing decent linux drivers and support, but no matter who's to blame or what causes it, you will find a lower percentage of windows users have problems compared to ubuntu or linux.

---

### Post by matt_risi on 2007-01-17
In my experience, Mac OS X is the most stable desktop environment. I'm an avid user of Mac OS, Windows, and Linux as well. Linux crashes on average maybe twice a month for me, while Windows crashes slightly more often. I do tinker with any desktop environment I use however, so that may be why.

---

### Post by Pobega on 2007-01-17
> **Artificial Intelligence said:**
> If you want more stable then roll back to 6.06 (dapper) LTS. There's a reason why Edgy is called edgy ;)

Honestly I have never one crash on my linux machine, only the one(s) which a coursed by me when I'm messing around with stuff or if I use an alpha applications that I'm aware can make trouble.

Other than that KDE is more "unstable" is my experience. Try give Gnome or XFCE a go.

It's possible to do that? I'd love to downgrade my system to Dapper without messing anything up, it would be awesome if there were instructions or something on how to do it (I've been having a lot of crashes recently on Edgy)

---

### Post by mattgaunt on 2007-01-17
TO be honest i agree with what most people have said, it depends on what you do to your machine that determines how well it runs

I have been using ubuntu for cpl of months, and i love it, its legal, its free. its fully customisable, and everyone is here to help you.

In my opinion i think linux is rediculously stable, considering what it can do compared to windows, its amazin and im doing alot of programmin since doin a university degree in computer science and i couldnt imagine doing it in windows. It would crash and definately be capable of things i would want it to do

Also linux has a whole team of users who are willing to help each other out

I can have a problem, post it in a forum and someone somewhere will have an answer and i love it

So yes linux will crash yes, but u hav alot more people to help you find out why and solve it, but no matter what you cant deny the fact that you can do more in linux than windows, and you have alot more help with linux than windows

But thats just lil old me's view

Matt

---

### Post by Perfect Storm on 2007-01-17
> **Pobega said:**
> It's possible to do that? I'd love to downgrade my system to Dapper without messing anything up, it would be awesome if there were instructions or something on how to do it (I've been having a lot of crashes recently on Edgy)

When I said downgrading I meant installing dapper instead of edgy.

But if you have seperated /home from the rest of your Ubuntu install it should be quiet painless to wipe Edgy and install dapper and still have all your stuff.

---

### Post by jvc26 on 2007-01-17
In my opinion linux has been more stable inherently than windows - my windows went through periods where it broke on a regular, and unacceptable basis. However, I know other people who've never had an issue with the XP OS. My only issues have been with linux when I've tweaked it too much, I've taken a kernel compile too far in a random mission to make my boot the fastest I can or Ive been trying (as someone else posted, I do apologise I can't remember exactly who it was could well have been Artificial Intelligence.) Alpha software. Dapper was more stable and (is) more stable than edgy, but thats because it is LTS and isnt 'edgy' :)
Il

---

### Post by bone2006 on 2007-01-17
I really would have to disregard anybody's comment that said that windows crashed on them often or monthly, of course unelss they are referring to something before windows XP.  Maybe the title should be changed.  I must have used over 30 different systems and over 5 years with windows XP and I'm on a computer at least 12 hours a day and if windows XP has crashed, I really can't remember.  I remember very very well before XP, but I've never seen it where I've had to push the power.  I'm 200% positive I've never seen the BSOD in windows XP, but I don't run anything funky, just one HD, one DVD/CD burner.

I guess people don't like when you call everything linux.  I can tell you, I tried to get a friend to install ubuntu and two systems he had 3 harddrives installed, both systems grub wouldn't make it past the boot stage.  It's kind of hard to convience somebody to use an operating system and to at least give it a try, when they can't even boot up.  

I personally love how easy ubuntu was to install and how it did a non-destructive partition and rebooted with grub and I could select ubuntu or linux, but lucky for me I only have 1 HD as my friend is still upset at me for telling him how easy ubuntu was and how much I like it.

As others have posted, I did try Clt+dlt and backspace, but nothing happened.  I read comments about things you can do to kill the offending software, but not sure what to do.  I'm really not sure what 
(ctrl + alt + F#)  means?  is that F3 or F and then shift 3 to get the pound?

I'm not trying to upset anybody, I love this forum and believe it or not I'm running ubuntu and kubuntu on every system I have.  I didn't decided to give linux a try, because I was unhappy with XP, it's because of the way MS treats their customers and everything they are planning on doing with Vista and selling it for 200 dollars a pop makes me sick.  While linux is just as good and as others can verify even better in some aspects and it's FREE.  I'd rather send in 20 bucks a year to contribute to linux and the community than to send anything to MS that exploits the users as the company already has 95% of the world.

---

### Post by sn0m on 2007-01-17
Well the reason why i have swithced mostly to Ubuntu ( some software refuse to work in linux, wine or not, so till then.....), was that my computer complained that he felt he was a convict of a big prison caalled xp, same shiti yellay/greenish Start icon, like the stripy uniforms of inmates, windows checkin on me on daily basis to see if my copy was legitime or not, well screw that, i love the freedom of linux. At least you're like a free bird, well sampling different plants, getting diarrhea and voiting now and then, but flying high and enjoying the view rather then being force fed in dull boxes called windows.
I had many blue screens with xp, for a reason or the other, but i had none with ubuntu, unless i mess it up.

---

### Post by bone2006 on 2007-01-18
The system I had problems with last freezing with a fresh install with kubuntu, I wanted to give an update.  Yesterday I had to do something in windows, so I rebooted the machine in windows and did what I had to do and came back a few hours later and I got the BSOD, which  really has to be the first time I've seen it.  I tried the alt-tab as somebody mentioned and there's no go.  The blue screen referred to something about bad memory.  Later on I rebooted the machine and while in kubuntu the system locked up again and I figured out it's locking up at the sametime.  It's when I'm uploading a png file while in swiftfox to another messageboard that I run.  As soon as I start the upload it's when it crashes and no keyboard function seems to work.
But I wanted to post this also to clarify that the problem seems to be hardware related and not the OS.  It was I guess a coincidence that I just installed linux and I'm having hardware failures.

---

### Post by tdrusk on 2007-01-18
I have only had one freeze up that i had to controll+alt+backspace out of. I just didn't feel like killing the process. What is the key shortcut to the terminal? I love how I can run Ubuntu and never have to restart it. btw, I have heard that claim many times before, the one about never having to restart it, but does it still eat up all of your RAM. I remember with Windows after about 1 week all my RAM was used up and I had to restart. Will that happen in Linux?

---

### Post by Delkster on 2007-01-18
> **bone2006 said:**
> But I wanted to post this also to clarify that the problem seems to be hardware related and not the OS.  It was I guess a coincidence that I just installed linux and I'm having hardware failures.

Although I can't provide any backing for the claims, I've heard that Linux can sometimes be more sensitive to memory errors (in hardware) than Windows. Things like that may come down to how different operating systems organize the memory usage and whatever, and the reasons can be quite obscure. It's not very difficult to believe that hardware errors can just happen to cause actual symptoms in one operating system more often than in another because of the different patterns in memory use etc.

Other than that, aysiu got it right once again: Most hard crashes in Linux and, indeed, also in modern versions of Windows, can be attributed to driver problems. In Linux device drivers generally run in kernel mode and can mess everything up if they've been written hastily and without respect for proper use of the kernel resources and interfaces. I'd say that nearly all BSODs in Windows (2k/XP/whatever NT-ish), perhaps excluding some really exotic situations, are also caused by badly behaving drivers.

Things also tend to be complex enough that you may just be unlucky and happen to hit an obscure bug that bothers only a handful of people, perhaps because you have a very interesting setup or something. This probably applies to both systems.

Just having the X Window System freeze is probably different from a technical standpoint although to the end user it may be just as annoying as having the entire system (including the kernel) go to a vegetative state. Usually the kernel and other lower layers of the system are doing just fine, and sometimes that can save the day because if your keyboard still works, you may be able to switch to a text console, kill the offending application and possibly recover control of your session. Applications *shouldn't* be able to freeze the entire X Window System, but I'm sure X.org isn't without bugs.

On the other hand, display drivers may have at least a part in many of the cases where an application somehow manages to freeze the entire X Window System. I've had that happen with ATI's proprietary drivers in the past, scrolling something in OpenOffice.org or Opera. Things are probably better now although I haven't used the ATI driver in a while.

Not all applications on Linux are very stable, and that *is* significant, particularly if the applications or tools are integral to the desktop and thus considered part of the entire operating system environment. Yes, I know that has nothing to do with the stability of the kernel, and I also know that the base operating system consists of the kernel, some base libraries, userland tools and some kind of a user interface, but in a *desktop operating system* you expect to have a working GUI as well, so the stability of its integral components is part of the stability of the desktop operating system even if they have no effect whatsoever on what happens in other parts of the system.

What many people miss, however, is that if the entire system or even just the whole GUI freezes, the problem isn't the possible instability of the application that triggers it (and I mean the case where the application is a normal desktop application, not a 3D game or something). The problem is that the application somehow manages to freeze the entire GUI, which it shouldn't be able to do, and that isn't just a problem with the application.

---

