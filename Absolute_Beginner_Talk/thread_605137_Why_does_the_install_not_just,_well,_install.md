---
title: "Why does the install not just, well, install?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by scriptsales on 2007-11-06
:confused:
OK, I'm a lazy, lazy man who just fancied trying Ubuntu. Normally I use Windows but I do have some exposure to Linux for my Web Server. I downloaded the latest distribution for my architecture (the 32 bit x86 version) got a new hard disk, inserted the CD, booted up and watched. I got the boot options and chose to install Ubuntu, then the text "messages" during the boot up and then the monitor went into standby mode. 

I figured that maybe it is just taking some time to figure out my hardware configuration or something so I had a cup of tea and watched an episode of Family guy, came back and the screen was still blank. My first thought was "Oh well, I've got a nice new hard drive to put more windows stuff on" so I went to turn off the PC to put my drives back in order and in doing so knocked the desk. Lo and behold I was then greeted with the screen springing to life, a totally uncluttered desktop with an install icon.

Now, to get to the point, why does the selecting of Install Ubuntu not simply launch an installation program? I am figuring that the aim is to get people who have been using Windows forever to give it (Ubuntu) a whirl. Like me, they are Lazy, Lazy people and are just looking to have an install program do just that.

Secondly, I have been reading some posts in other forums where the users are apparently invulnerable. Recommending that there is no need for anti virus software. Is this true? Is Unix so good that there is no possibility at all of becoming infected with any kind of virus, also the built in firewall, is it any good? I mean you wouldn’t catch me using the Windows firewall for love nor money.

Not a rant, just my 2 pennies worth of opinion. Having said all of the above, it looks good and I am going to give it a real try this time as a desktop operating system.

---

### Post by skymera on 2007-11-06
ok anti-virus
i dont have it.

but you CAN get the,. the event of this is HIGHLY unlikely

---

### Post by Daveski on 2007-11-06
> **scriptsales said:**
> Now, to get to the point, why does the selecting of Install Ubuntu not simply launch an installation program? I am figuring that the aim is to get people who have been using Windows forever to give it (Ubuntu) a whirl. Like me, they are Lazy, Lazy people and are just looking to have an install program do just that.

Ubuntu is a LiveCD where Windows users can boot from the CD and try the OS and lots of apps before clicking the install icon. Sure the install is Linux based, and boots into full Ubuntu first - this is good to check all (well your most important) hardware works without any fiddling around.

> 
Secondly, I have been reading some posts in other forums where the users are apparently invulnerable. Recommending that there is no need for anti virus software. Is this true? Is Unix so good that there is no possibility at all of becoming infected with any kind of virus, also the built in firewall, is it any good? I mean you wouldn’t catch me using the Windows firewall for love nor money.

There are so little Linux viruses (at the moment) that you are simply at such a low risk the overhead of a virus scanner is considered too much for most users - that might change in the future though.

As for the firewall, Linux uses iptables which is what many of the 'hardware' firewalls that lots of corporate users have installed on their networks use. This can be tricky to setup properly unless you have a good understanding of networking and TCP/IP. There are some great front-ends which help with a simple setup. Generally though Ubuntu listens to no ports unless you install or activate certain services such as http, ftp, SSH etc. No services, no real need for firewall - especially if you are connected to the internet through a NAT router.

---

### Post by mivo on 2007-11-06
> **scriptsales said:**
> :confused:
...inserted the CD, booted up and watched. I got the boot options and chose to install Ubuntu, then the text "messages" during the boot up and then the monitor went into standby mode. 

In the Live CD menu where it asks if you want to start/install Ubuntu, check the disk, etc, press F6. At the bottom appears a string of commands and options. Here, remove "quiet" and "splash", and add "nosplash" (no quote marks). This should work now. If it does not, try the same again and add additionally "irqpoll" (plus "nosplash").

---

### Post by scriptsales on 2007-11-06
> **mivo said:**
> In the Live CD menu where it asks if you want to start/install Ubuntu, check the disk, etc, press F6. At the bottom appears a string of commands and options. Here, remove "quiet" and "splash", and add "nosplash" (no quote marks). This should work now. If it does not, try the same again and add additionally "irqpoll" (plus "nosplash").

Some great responses, the one above though illustrates my point about ease of use. Happilly I sorted my issue out but most people (OK, lazy windows users) simply wouldnt look to see if there is an F6 option and certainly wouldnt know what options to use nor bother looking for them.

Wouldnt it be nice if there was an install disk, you know one that just does what it says on the tin?

---

### Post by Daveski on 2007-11-06
> **scriptsales said:**
> Wouldnt it be nice if there was an install disk, you know one that just does what it says on the tin?

I think a 'Windows Installer' is being worked on where the initial installation takes place inside Windows and the installer is a Windows executable. This would give lazy Windows users a simple way to kick off an install. Personally I am tickled that I am able to browse the internet WHILE my OS is installing.

---

### Post by NotTheMessiah on 2007-11-06
> **scriptsales said:**
> Some great responses, the one above though illustrates my point about ease of use. Happilly I sorted my issue out but most people (OK, lazy windows users) simply wouldnt look to see if there is an F6 option and certainly wouldnt know what options to use nor bother looking for them.

Wouldnt it be nice if there was an install disk, you know one that just does what it says on the tin?

Because  you don't want to install something and discover after that it doesn't work and/or is crap.Simple

---

### Post by mivo on 2007-11-06
> **scriptsales said:**
> Wouldnt it be nice if there was an install disk, you know one that just does what it says on the tin?

There is one, it is the "Alternate Install CD". :) The one you used is the "Desktop Live CD". The former one only offers a text installer and gets right to it whereas the Live CD boots into a complete graphical system where you can try out Ubuntu before installing it.

Did the "nosplash" option work for you or was the solution different?

---

### Post by scriptsales on 2007-11-06
> **mivo said:**
> There is one, it is the "Alternate Install CD". :) The one you used is the "Desktop Live CD". The former one only offers a text installer and gets right to it whereas the Live CD boots into a complete graphical system where you can try out Ubuntu before installing it.

Did the "nosplash" option work for you or was the solution different?

My "Fix" was to accidentally knock the desk which brought the screen out of standby, the desktop was there waiting so I just did the install and everything is fine.

As for a text only installer, great for linux experts but all i want (and I suspect most Windows users looking to switch) is the ability to pop in a CD, have it fire up, ask me a couple of questions (Which, I must say the installer did just fine once I had it running) like where am I, what my keyboard layout was and then ask where to install it and how to partition my disk (Again, the installer did this very well once I had it running)

My main point is that if I hadnt knocked my desk at that moment I would have just plugged back my Windows Hard disk, used the new hard disk as storage and the Ubuntu Live CD as a coffee coaster :)
I am determined to give Ubuntu a good go this time. I did install redhat a couple of years ago as a desktop operating system, boy was that an experience. Installed it, tried to get on the internet, couldnt, gave up. Like I said earlier I am a Lazy, Lazy man :roll:

---

### Post by mivo on 2007-11-06
Ooh, I understand now. :) You are looking for a graphical installer that works like the alternate, text-based installer. Basically, a graphical system minus the Live CD part. The alternate installer really is quite like that -- it asks questions, lets you choose keyboard, name, etc -- it just uses text and ANSI "graphics", but it is really very simple and requires no expert knowledge. .

---

### Post by Daveski on 2007-11-06
> **scriptsales said:**
> 
I am determined to give Ubuntu a good go this time. I did install redhat a couple of years ago as a desktop operating system, boy was that an experience. Installed it, tried to get on the internet, couldnt, gave up. Like I said earlier I am a Lazy, Lazy man :roll:

Please do give some time to trying Ubuntu. You probably will get stuck at some point, and I beg you to spend the time asking questions on this forum before you give up on it.

---

### Post by scriptsales on 2007-11-06
> **NotTheMessiah said:**
> Because  you don't want to install something and discover after that it doesn't work and/or is crap.Simple

Why not, millions of windows users can't be wrong :)

No seriously, I had made the commitment, I had read about Ubuntu, I went and bought a new hard disk (lets face it for £30.00 I can use it again if I decide to cross back to the dark side), I wanted to install the thing, why not just have a nice, simple disk that you can pop in and install. I know I sound like I'm whining on about this but it seems that if you're trying to get people to install this operating system and wean them off Windows then it should be as simple a process as installing windows.

Believe me, the Vista install is a snap (OK so spending vast amounts of time and money making it anywhere near secure is a pain in the butt) but I put the disk in, told it what country I was in and 30 minutes later I had a fully working system (OK, people, especially Unix people would debate that one)

---

### Post by Barge on 2007-11-06
I enjoyed the install experience personally, given I stare at the WinXP white text on blue install screen too often for friends/family/etc. It was a different way of doing things sure, but something different is why I installed gutsy in the first place I guess. It did seem a little strange, but not at all difficult, so no complaint here.

As to viruses I understand ClamAV can be installed from the repos, and Firestarter is the gui I've been using for the built in firewall to open ports for WoW downloader, also in the repos.

---

### Post by mivo on 2007-11-06
> **scriptsales said:**
> ... t I put the disk in, told it what country I was in and 30 minutes later I had a fully working system (OK, people, especially Unix people would debate that one)

Ubuntu installed like this on my other desktop machine. :p Fedora installed this way on my current desktop (I think it took less than thirty minutes). This box, too, uses Ubuntu now, but needed some tweaking  (Which, to be honest, had to do with my hardware and the board's maker.)

When, or if, you have problems like getting wireless to work in Linux, you need to remember that this is the direct result of some hardware manufacturers not providing Linux drivers or even offering specs so that other people can develop drivers, for free. Windows had all of these problems too before it became the de facto standard desktop OS, and Vista has more driver issues than XP.

It's tempting to think: "My wireless is not working, Linux sucks!". In a way, it is even understandable. But it is more complex than this, and "My wireless is not working, the manufacturer sucks!" is probably much closer to the reason why it did not work out of the box. 

Most issues can still be resolved. Sure, you might have to search the forum or post about your trouble, but Ubuntu (as do many other distros) offers you a wonderful and helpful community. And you get all of this for free. :)

---

### Post by NotTheMessiah on 2007-11-06
> **scriptsales said:**
> 
 (OK, people, especially Unix people would debate that one)

I had a fully operating system for less then 30 minutes - after i clicked the install icon :) and that is including - selecting - use longest free space - select country, language,import settings and whatnot :)

---

### Post by NotTheMessiah on 2007-11-06
> **scriptsales said:**
> Why not, millions of windows users can't be wrong :)



Why not???? Just because the number is huge doesn't mean they are 'correct' or whatever.... the logic is flawed - the rest of the people that are using other OS are wrong because they belong to the minority?!?!??? :confused:

---

### Post by StefanBaker on 2007-11-08
Hmmm.  I'm confused.  I don't want to offer a silly rubber chicken answer here nor do I mean to imply that YOU are silly but...

What do you mean by 'knocked the desk"?  Are you saying you bumped into the piece of furniture upon which the computer is sitting?  This, of course, would move the mouse.  Is your Windoze screen saver by any chance a blank screen?

I'm just saying...

---

### Post by hyper_ch on 2007-11-08
> **scriptsales said:**
> As for a text only installer, great for linux experts but all i want (and I suspect most Windows users looking to switch) is the ability to pop in a CD, have it fire up, ask me a couple of questions (Which, I must say the installer did just fine once I had it running) like where am I, what my keyboard layout was and then ask where to install it and how to partition my disk (Again, the installer did this very well once I had it running)
Well, the LiveCD install goes like this: [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)
The text install isn't different... it just doesn't have the fancy graphics and is just text on a background...it also asks for language, country and some other stuff...

There is no science to it. The only thing that you should be VERY careful about is the partitioner. Have a read at the options and reflect what they mean - or ask here in the forums or on irc if you are not sure.

---

### Post by scriptsales on 2007-11-09
> **StefanBaker said:**
> Hmmm.  I'm confused.  I don't want to offer a silly rubber chicken answer here nor do I mean to imply that YOU are silly but...

What do you mean by 'knocked the desk"?  Are you saying you bumped into the piece of furniture upon which the computer is sitting?  This, of course, would move the mouse.  Is your Windoze screen saver by any chance a blank screen?

I'm just saying...

When I say I knocked the desk I mean I bumped into the desk. I wasnt running windows at the time but the live CD. I.e I booted up off the Live CD, Double clicked the install icon and went from there. What must have happened is that for whatever reason (Dodgy driver or something) Ubuntu must have entered a blank screen screensaver or something. Anyway, long story short, it's installed and everything works so i am just getting used to where everything is.

Cheers
Andy

---

### Post by scriptsales on 2007-11-09
> **NotTheMessiah said:**
> Why not???? Just because the number is huge doesn't mean they are 'correct' or whatever.... the logic is flawed - the rest of the people that are using other OS are wrong because they belong to the minority?!?!??? :confused:

Look at the :), I was trying to be funny, maybe they should have a big Joke Alert Icon or something (Or maybe my sardonic comments should just be, well, funny :) )

---

### Post by ByteJuggler on 2007-11-09
> **scriptsales said:**
> 
Believe me, the Vista install is a snap (OK so spending vast amounts of time and money making it anywhere near secure is a pain in the butt) but I put the disk in, told it what country I was in and 30 minutes later I had a fully working system (OK, people, especially Unix people would debate that one)

I think the simple mistake (if you want to call it that) that you made was not waiting slightly longer for the initial startup of the installer/livecd to kick off the installation, before the screen went into standby.  If you boot Windows XP or Windows Vista's CD's and just leave them, you will also end up with a screen likely on standby and non-installed system, as Windows also requires some initial actions and questions answered to start the installation.  So, to me having to double click on an icon to start the process of answering the installation questions is neither here nor htere, and therefore in the abstract no different to having to pressing Enter to start the installation of Windows XP for example.  

To give a bit of a different perspective on this, I'd like to also submit that in some ways the Windows installers are arguably in fact more of a pain to use routinely because they don't collect all the information neccessary for installation up front (it gets collected as the installation progresses), and also requires several reboots, all of which requires you to be present and watching the darn thing install.  With Ubuntu's installer, it actually collects *all* the information up front, so you can deal with everything requiring user interaction before the real install starts: Boot the cd, wait for the desktop, click the icon, answer all the questions, all of which will take at most a few minutes, and then you can **leave the computer **  to install all by itself to a fully working system with no further interaction required (allowing you to go and watch family guy and come back to a bootable/installed system.)  If you try that with Windows you'd come back to a window requiring regional settings information or something halfway through.  

Finally I'd like to point out that with Windows your installation is typically nowhere near over after the first initial install.  You then have to install updates, often repeatedly as not all updates are cummulative, so you install some, reboot, then install some more, then reboot, then install some more etc...  Then you typically have to also install other system software, motheboard software, etc etc etc to get all your devices working.  And finally, you need to install application software (Office or whatever) which takes more time still.  With Ubuntu, installing updates is done in a single hit (a single download + install) which oftentimes won't even require a reboot, and you end up with a system with far more actual applications installed as well (OpenOffice for example.)  In addition, the entire system is updated in a single hit, not just the core operating system.  (To be fair, Microsoft is moving in this direction too with Microsoft Update, but then that still only works for MS software...)

So considered from that point of view, I think there's much to be said for the Ubuntu installer's way of doing things, and complaining about having to double click on the install icon on the ubuntu livecd desktop is like complaining about having to click on the "I agree" EULA button on the windows installer. In either case if you want to installation to proceed you just do it.

---

### Post by Daveski on 2007-11-10
> **Daveski said:**
> I think a 'Windows Installer' is being worked on where the initial installation takes place inside Windows and the installer is a Windows executable. 

I also found this tip, although I have not tried it:

> If you have a 7.10 Live CD and it will not run, preventing you from installing, when you get the boot splash screen, press F6 and type "only-ubiquity" (without the quotes) 
This will run the installer without booting a Live session. - thanks gn2.

---

### Post by StefanBaker on 2007-11-11
scriptsales wrote: "Anyway, long story short, it's installed and everything works so i am just getting used to where everything is."

Great!  I'm glad you're past the install 'problem' <grin> and moving forward.  I'm certain that you are going to really enjoy your Ubuntu experience.  It isn't just the price that's compelling - it's the software ITSELF!  Superior is just one way to say it.

Synaptic Package Manager is the invention of the century!  Be sure to enable all the 'supported' repositories but leave the backports and other repositories unchecked until you are comfortable with the OS and so forth.
System > Administration > Synaptic Package Manager
It will ask for your root password.

Also, for the Windoze Desktop needy, you can right click on any item in the menus and select either 'Add to Desktop' or 'Add to Panel (Startbar) to quickly create a 'shortcut'  (You don't need to be in SPM to do this.)

Enjoy!

---

### Post by louieb on 2007-11-11
> **scriptsales said:**
> :confused:...Now, to get to the point, why does the selecting of Install Ubuntu not simply launch an installation program?.... Lazy people ...looking to have an install program do just that....

I love Mexican food, the Dallas Cowboys and the Oklahoma Sooners too. Linux distros are kinda like a buffet a little of this some of that. Even Ubuntu has four flavors, two installers, and a bunch of spin offs. Every day somebody comes up with something new. In windows you get to choose between a couple of start menus and large or small icons. Now thats an OS for the lazy. :KS

LInux and Ubuntu is what it is and  [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

