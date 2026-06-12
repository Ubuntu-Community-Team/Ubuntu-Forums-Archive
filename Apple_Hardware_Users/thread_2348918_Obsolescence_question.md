---
title: "Obsolescence question"
date: 2017-01-09
forum: Apple Hardware Users
---

### Post by joannacw on 2017-01-09
I’ve heard that running Linux instead of Mac OS greatly reduces the rate of obsolescence. I have a MacBook Pro with a 2.16 GHz Intel Core 2 Duo processor and 2GB 667 MHz DDR2 SDRAM.  The hardware still seems to be working fine and I still have 132 GB of available memory, having used 22 GB. Chrome and Safari updates are no longer supported on my computer. Last time I changed computers, not because of hardware failure, but because of software obsolescence/connectivity issues.   I’m not looking to do gaming or create/edit videos, but I would like to be able to update my website, upload files to the remote printing site, stream videos etc without having to buy a new computer every 3-5 years.
 
3 questions:
 
Does running Ubuntu instead of OS X increase the useful life of older computers?

Does it make sense to install Ubuntu on the MacBook Pro described above or is it getting too old to be useful? Is there a Ubuntu-compatible browser which still supports updates that would run on this machine?
 
What version of Ubuntu should I download for this machine?
 
Thanks for your patience with these raw-beginner questions.
 
Joanna

---

### Post by ernsteiswuerfel on 2017-01-09
> **joannacw said:**
> Does running Ubuntu instead of OS X increase the useful life of older computers?
Short answer: yes.
Ubuntu LTS (long term support) versions will receive component updates (hardware support, browser, et.c) for 5 years for a specific LTS version. AMD/Intel-Computers are supported very well.

> Does it make sense to install Ubuntu on the MacBook Pro described above or is it getting too old to be useful? Is there a Ubuntu-compatible browser which still supports updates that would run on this machine?
Your MacBook Pro will be fast enough for browsing, office, internet, watching videos for years to come. Only the upcoming h265/hvec video-codec will make it struggle. Anything below it should handle with ease.
 
> What version of Ubuntu should I download for this machine?
 On 64bit AMD/Intel-hardware any flavor will run. I like Ubuntu MATE most: [https://ubuntu-mate.org/](https://ubuntu-mate.org/)
Depends on your choise which desktop or look you like most. You can install aditional desktop environments afterwards.

---

### Post by 1clue on 2017-01-09
I would recommend a "lightweight" distro, for Ubuntu derivatives that  would be Xubuntu or Lubuntu. Mainstream Ubuntu might work for awhile but  all software tends to get heavier after awhile, and if you're worried  about Mac OS being slow and outdated then you should aim  for something  lighter.

By "lightweight" I mean choosing desktop/window  management software which does not require a lot of CPU work.  Heavy=graphics intensive, light=simple graphics.

Years ago there was a saying, it's still around. Linux is the fastest operating system you can put on your PC. It's true in some cases, but certainly not in others. 

At the time that statement was originally made, Linux was still primarily a command-line operating system. The GUI was being developed but in no way stable yet and I viewed it as more of a time consuming toy than anything I would want to use full-time.

Many people still use that statement, even while using the most bloated blinged-up software they can find. The truth is, Linux can be faster than your commercial OS or it can be much much slower. Certain groups of Linux users like to have flashy things on their computer desktop, and that's fine as long as your hardware is up to it and your preferences run that way. Mine don't. I prefer something lightweight even on a fully capable modern machine.

So what I would recommend is to download and burn the appropriate image of Xubuntu and Lubuntu and Ubuntu, so you can boot from them on your mac. Keep in mind that booting from the CD is going to be considerably more sluggish than from the hard drive when reading  from the drive. So give it plenty of time and pay attention to the indicator light when it's blinking.

---

### Post by joannacw on 2017-01-09
Thank you both! This is helpful.

1clue, a few follow-up questions:

Do I understand rightly that you recommend using Ubuntu/Xubuntu/Lubuntu from a disc instead of partitioning the hard drive and installing them that way? (And can I run them off CDs? I'd seen an article online that made me think I'd need to go out and buy DVDs instead because CDs didn't have enough memory...)

Also, does 'simple graphics' mean lower picture quality--would I notice a difference as I edit photos or build webpages with photos?

Thank you again.

---

### Post by 1clue on 2017-01-09
Boot from CD: I'm only recommending that so you get an idea of what you will install.  In general running off a CD is a terrible way to run Linux. You'll add several minutes to your boot time and nothing will behave in a way that you want.  Your changes generally won't be saved anywhere unless you jump through a lot of hoops to save it.

CD vs DVD: I said CD but truth is I don't know how big the installer image is. I generally put it on a USB stick if I need to use a physical installer media, or a DVD if the machine is too old. I don't think I have any more CD blanks. ***Edit:** I'm 50. It still looks like a CD, so I call it that. I was around way before CDs came out.  :)*

Simple graphics is no-frills. You still get the same resolution, but for example an animated widget for minimizing a window would be a frill. Having a desktop cube is crazy animation, very heavy. So is jello windows.

[https://www.youtube.com/watch?v=4QokOwvPxrE](https://www.youtube.com/watch?v=4QokOwvPxrE) shows a "heavy" desktop environment.

---

### Post by lisati on 2017-01-09
For some of the flavours, you'll need a DVD rather than a CD. The situation has changed since I first started using Ubuntu - "standard" Ubuntu won't comfortably fit on CD these days. 

@1Clue: I'm 56, and have come to realise that for some folks, referring to a disk as a CD works for them, even though it might actually be a DVD. I'm thankful that we are not limited to using older technologies, such as floppy disks, paper tape, or punch cards. :D

---

### Post by joannacw on 2017-01-09
Thank you! Sounds as though 'lightweight' is what I want--I've never had animated widgets or desktop cubes and can't think why I'd want them. 

The other thing I don't understand about the different Linux distros is to what degree the same programs can be run on different ones. So, for instance, would most photo editing and website building programs that would run on Ubuntu Mate also run on Xubuntu? (And is it significantly harder for an ignorant person to figure out how to install such programs on Xubuntu?) 

Thanks again for all your help and patience.

---

### Post by Irihapeti on 2017-01-09
The different packages that come with the various flavours are, if you like, the packagers' suggestions or preferences. You're not restricted to them. I run Xubuntu and I have installed packages from the Kubuntu, Ubuntu and probably other flavours (if I looked hard enough). To install them, you use the Software Centre or its equivalent, just as you would for any other program.

If a program comes from a different flavour, such as Kubuntu, then it will pull in a lot of extra supporting packages. I'm not aware that this causes a problem, unless of course you are short of disk space.

---

### Post by 1clue on 2017-01-09
> **joannacw said:**
> Thank you! Sounds as though 'lightweight' is what I want--I've never had animated widgets or desktop cubes and can't think why I'd want them. 


YAY! While I had a longer-than-brief, more-than-shameful fixation on jello windows the rest of it was neat to look at but I never wanted that either.  Your preference shows you're sane and actually use your computer for some sort of work.

> 
The other thing I don't understand about the different Linux distros is to what degree the same programs can be run on different ones. So, for instance, would most photo editing and website building programs that would run on Ubuntu Mate also run on Xubuntu? (And is it significantly harder for an ignorant person to figure out how to install such programs on Xubuntu?) 


Generally speaking you can run anything on any UI. That's the idea anyway.

Some of the environments have a lot of widgets and apps which depend on libraries and other tools in a specific desktop environment.  For example, if an app or widget is named k<some word not wanting a k in front> it's probably part of the KDE environment, which is a more ... business? ... related desktop system. Using that tool will probably load a whole lot of other stuff related to KDE.  Gnome has a lot of stuff specific to it too.

Gnome is somewhat infectious in some dependencies.  Gnome directly requires systemd, which is an init system. An init system is, approximately, what runs programs on your computer. Why gnome requires a specific init system has been a long-running debate with much contention, but in the case of Ubuntu and its variants systemd/gnome has won out.

Getting back to the point, loading some app or tool built for some window manager or desktop will load a bunch of stuff from that WM/desktop, but won't load the entire desktop.  So if you use something from kde it doesn't mean you have all of kde loaded, only those components necessary for the tool or app you chose.

If you are running Xubuntu (which uses XFCE window manager) and you want something from LXDE (the WM for Lubuntu) then it won't be a huge crossover, because both are lightweight WMs which rely mostly on lightweight libraries common to lots of different things. But if you're running Xubuntu or Lubuntu and you want something from gnome or kde then it's going to be a big deal.


If you're lost, then stop reading now. What I'm about to say won't likely make it better for you.

The Open Source community is comprised of thousands of apps maintained by many thousands of developers. These developers are from diverse backgrounds. Some work for the US government, some for schools, some for corporations (which may or may not contribute software they paid developers to write) and some are self employed or have a job but work on the side for FOSS (free/open source software).

Most of the better-written apps have configurations built into them at compile-time which either use or don't use something specific to a certain window manager or other package or feature. For example you can compile some apps with or without kde support, gnome support, qt support, ipv6 support, etc. It's possible to either trim these apps down so they require very little or to bloat them so they require both KDE and Gnome and a few others.

The difference between kubuntu and ubuntu and xubuntu and lubuntu are the options chosen when building these packages.

If this stuff really matters to you you can try out something like Gentoo, which is a source-based distro which lets you configure your preferences for the entire box and then build every piece of your system with those preferences in mind.  In effect you are building your own distro with your own priorities in place.

Gentoo is my other favorite distro. I have a whole bunch of *buntu boxes (mostly ubuntu server) and a few Gentoo boxes, where I want something very specific and it matters enough to go through the extra effort to get it.  I also maintain several boxes of other distros. I choose the distro based on the purpose of the box.

> 
Thanks again for all your help and patience.

You're asking good questions. Those of us who have been around for awhile live for this.

---

### Post by Irihapeti on 2017-01-09
As I see it, the "heavyweight" has to do with the graphics rendering of the OS in general, and some programs that need a lot of memory to run well. In my experience, if you can slim down the graphics side of the OS, you can run quite substantial programs. I have an old Asus EeePC900 netbook with only 1GB of RAM. I can run LibreOffice and Firefox with no problem, though they're not as fast as on a more powerful system.

---

### Post by joannacw on 2017-01-09
Thanks again!

Yes, the computer's mainly for working: correspondence, newsletters, photo editing and storage, and keeping up the website and Facebook page of the nonprofit I work for, plus occasional youtubing (watching not posting). If I can do those things I'm set. I probably don't need anything as fancy as Gentoo. 

Do you have a recommendation for a WYSIWYG web design program in Linux? I don't need to run videos/sound files/animation/PayPal buttons on the website... just pictures, regular text and hypertext, preferably not constrained to some prefabricated templates but fully editable. 

Thanks again!

ps I hope WYSIWYG is the right term but I may be misusing it--I'd like something that lets me drag text boxes and photos around, cut and paste, and see what it;s all going to look like in the end, and that gives me menus where I can select page width etc. rather than my having to know the right coding commands to enter to set those parameters.

---

### Post by Irihapeti on 2017-01-09
There is very little available for WYSIWIG web page editing in Linux. As far as I know, there's nothing in the Ubuntu repositories. Unless you count LibreOffice writer, which will produce html output – but the code looks like a rat's nest! (Code of that kind makes it more difficult for the next person who has to maintain the page.)

Programs that I've heard mentioned are KompoZer (which hasn't been updated for years but, apparently, still works), BlueGriffon (commercial) and the Composer package that comes with Seamonkey browser. That one at least gets updated regularly. I've used it occasionally and found that it does a fairly OK job.

But I've found that the best way long-term is to bite the bullet and use a code editor like Bluefish and check the output in a browser regularly. It gives me more flexibility and more control over the end result, and with luck, the resulting code will be acceptable to the person who has to take over from me. There are plenty of online tutorials for beginners. I figure that if this granny can do it, most people can. It's a matter of taking it slowly and being willing to have a few oopsies along the way.

---

### Post by QIII on 2017-01-09
+1 for Bluefish, do your edits and refresh your browser a lot.

---

### Post by 1clue on 2017-01-10
I've never seen a professional web page/app designer use a gui tool, other than to evaluate it.  They all either put out crap html as was previously mentioned, or they do things in a way which is incompatible with some sort of company standard, or they don't support some feature.

+1 for using a good programming editor and a browser. Actually several browsers on several machines IMO. I work from a live webapp server.

I use sublime text 3. [http://www.sublimetext.com/3](http://www.sublimetext.com/3) It's not WYSIWYG, and it's not free. It's the best GUI programmer's text editor I've seen since I started programming professionally back in the 90s. The only competition it has IMO is vim.  The license is one per human, you can have it on as many computers as you want, anywhere you want.  Linux/Mac/Windows. No I don't work for them, just a happy customer with full disclosure.  ST3 app is tiny, added functionality comes from plugins, which are many.

---

