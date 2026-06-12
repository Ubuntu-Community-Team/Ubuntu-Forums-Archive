---
title: "OS X versus Ubuntu"
date: 2007-04-14
forum: Apple PPC Users
---

### Post by blippy on 2007-04-14
NOT TROLLING, I PROMISE.

My PC was acting all wobbly, and is on its dying days. So I coughed up for a spanking new 20" iMac yesterday. OS X is pretty neat, but looking at Fink and Darwinports, I'm getting the feeling that there's actually more software out there for Ubuntu.

Does anyone have any non-fanboy comments of the relative merits of OS X versus Ubuntu, particularly as regards stability, speed, ease-of-use, and HARDWARE COMPATABILITY?

I had tried Edgy and Feisty beta on my dying PC, and it seemed fairly unstable. XP was acting kinda wonky, too, so it may just be that my hardware is on its way out.

---

### Post by seatea on 2007-04-14
I tried to use ubuntu as an alternative to Mac OS  X for  several months. I finally have gotten better at maintaining ubuntu, I am using Dapper as I wanted the official updating, but after I became frustrated with the lack of flash support,  the inability to use my Microtek scanner with ubuntu, and the often needed troubleshooting that  always seemed to be cropping  up; I installed Mac OS X on my Powermac G4 400MHz. I have been pleased with Mac OS  X's performance. It has  been much easier to use. It was helpful to learn to use a Linux based  system and I still use the Ubuntu sytem periodically. There  seems to be more and more software becoming  available for Mac OS  X. I haven't had  any significant  stability problems with ubuntu, but from my experience, Mac OS X is much simpler to use on a day to day basis.

---

### Post by Auria on 2007-04-14
Mac OS X is easier to setup, since everything works out of the box.

Hardware compatibility is very good, but they achieve it only by cheating (OS X can only be installed on Apple's hardware, so no wonder the hardware support is good)

In terms of stability, OS X was rock solid to me, much more than Ubuntu (but i heard feisty has a new kernel that's much better on PPCs so that may fix the somewhat frequent crashes i got in ubuntu)

What annoys me in Ubuntu is the lack of flash, lack of Java, no reliable 3D drivers... most of these are PPC-specific though, since x86 ubuntu has these.

My opininon is that Mac OS X is better on PPCs. On intel computers Ubutnu would be much closer to OS X

And of course Ubuntu is open-source, what OS X will never have

---

### Post by rccharles on 2007-04-14
> **Auria said:**
> 
And of course Ubuntu is open-source, what OS X will never have

Actually, the Unix layer, Darwin, is open source.
[http://developer.apple.com/opensource/index.html](http://developer.apple.com/opensource/index.html)

Robert

---

### Post by rccharles on 2007-04-14
> **blippy said:**
> NOT TROLLING, I PROMISE.

My PC was acting all wobbly, and is on its dying days. So I coughed up for a spanking new 20" iMac yesterday.

Have you thought of getting a copy of Parallels? 
[http://www.parallels.com/products/desktop/](http://www.parallels.com/products/desktop/)

Folks are running there old Windows software in a Parallels virtual machine.  

You could run Ubuntu in another virtual machine.  Sure adds up to a lot of software.

[QUOTE=blippy;2452334
 OS X is pretty neat, but looking at Fink and Darwinports, I'm getting the feeling that there's actually more software out there for Ubuntu.[/QUOTE]

Seems like Mac OS has Mac software plus Open Source software.  How is this less? & you can run windows in a virtual machine.  

Robert

---

### Post by Auria on 2007-04-14
AFAIK Parallels only works on Intel, so thats not an option (we're in the PPC section of the forum, remember)

Also i know Darwin is Open-Source, but that's just a part of the OS. And Mac OS X does not have as many Open-Source apps as Linux. Perhaps what i dislike most is not the closed-source nature but Apple's restrictive licenses, like that you can only install OS X on Apple's hardware. I heard often from application developers "we would support OS X if we could install it on our computers, but since Apple makes it illegal, we're not going to buy an entire computer just to support one OS we dont even use"

---

### Post by 3rdalbum on 2007-04-15
> **rccharles said:**
> Actually, the Unix layer, Darwin, is open source.
[http://developer.apple.com/opensource/index.html](http://developer.apple.com/opensource/index.html)

Only parts of Darwin are open-source. You cannot build it without binary blobs.

Also, the Darwin which you can get the "source code" for is not the same as the one that comes with OS X. You cannot download the source code for the actual OS X version of Darwin.

VERY few people outside Apple do any hacking on Darwin anymore, and those who do never see their efforts in the main tree. Apple doesn't let non-employees see the Darwin bug tracker either. For all I care, OS X could be based on Windows Vista with a restrictive EULA.

---

### Post by dpny on 2007-04-15
I run OS X on my G5 and Ubuntu on my Pismo, which is what I'm using to post right now. 

I find OS X is easier to maintain. A lot of this comes from the fact that Apple is writing software for their hardware, so they know exactly what they need to spec for and what problems they might find. So, for instance, to use Samba on OS X all I have to do is click one checkbox in the Sharing control panel. For Ubuntu, I had to 1) use apt-get to install Samba 2) read documentation on how to configure Samba and 3) spend time in the shell configuring files to set user name, password, etc. I find this to be the case in general with Ubuntu: you have to be more willing to spend time under the hood to get it to work. Apple makes OS X a turnkey install: no need to muss about in the BSD guts of the system unless you want to.

Ubuntu also suffers from some of the general problems of Linux, which is writing open software and drivers for some closed hardware. One of the big issues in Linux is getting good video drivers. ATi and nVidia don't exactly have writing OSS drivers at the top of their to-do list. Because of this, it took me some mucking around with xorg.conf to get direct rendering (and, thus, usable screen redraw times) on my Pismo, and the drivers still aren't as good as the ones Apple writes for the same machine. I still get tearing when I drag windows, and the open source drivers don't make use of the machine's built-in DVD decoding hardware, which means I can't watch DVDs on this machine, something I can do in OS X. These problems can crop up in other areas as well: sound can be weird, etc.

As other people have mentioned, there are also problems specific to PPC Linux, like lack of decent Flash libraries/players, lack of the same for RealPlayer, and no WMV codecs at all. Some stuff is also just a pain in the ***. The machine will absolutely not see the network at work in Ubuntu, but will when booted into OS X.

Basically, Apple doesn't really sell computers or operating systems. They sell vertically integrated computing solutions, which means that all of the parts of their increasingly wide variety of software and hardware works with all of the other parts. One of the advantages of this is that (most of the time) using OS X and friends is seamless and pretty simple, which is what Joe and Jane Average Computer user need.

All that sounds pretty bad, yet this machine is booted into Ubuntu 90% of the time. I couldn't make Ubuntu my primary OS for a variety of reasons, the least of which is that the programs I need to earn my living--Quark, Photoshop and friends--aren't available under any Linux. However, I have learned a lot about OS internals from running Linux, and I learn more every day. For all of the normal day-to-day stuff I do--web, email, music, etc.--Ubuntu is just fine. Like I said, I'm typing this on my laptop, in Ubuntu, right now.

---

### Post by dpny on 2007-04-15
> **3rdalbum said:**
> Only parts of Darwin are open-source. You cannot build it without binary blobs.

ALL of Darwin is open-sourced. What isn't open source is stuff like Aqua, but that isn't Darwin. You can run Darwin with X if you want to.

> Also, the Darwin which you can get the "source code" for is not the same as the one that comes with OS X. You cannot download the source code for the actual OS X version of Darwin.

I'm not sure where you got this info, but it from what know it is 100% wrong. You can grab all of the source code for the latest Darwin you like. What you can't get, as I said above, is Aqua and friends. But, like I said, these are not a part of Darwin, but are Apple' version of the X server and other stuff. Not open source. Never has been. Never will be.

---

### Post by ssam on 2007-04-15
it depends what you need. if you are hooked on commercial software like photoshop then you will need to stick to mac os x. if you are hooked on oss software like the gimp and openoffice, then you will find them better to use on linux.

if you have a new (intel based) iMac, then you dont need to worry about the powerpc specific issues, poor support for flash, java etc.

its not hard to set up a dual boot and have a play with both.

---

### Post by 3rdalbum on 2007-04-15
> **dpny said:**
> ALL of Darwin is open-sourced. What isn't open source is stuff like Aqua, but that isn't Darwin. You can run Darwin with X if you want to.

I'm not sure where you got this info, but it from what know it is 100% wrong. You can grab all of the source code for the latest Darwin you like. What you can't get, as I said above, is Aqua and friends. But, like I said, these are not a part of Darwin, but are Apple' version of the X server and other stuff. Not open source. Never has been. Never will be.

The last thing I want to do is start a flamewar :-)

I know the distinction between Darwin and OS X's higher components. The source code package for Darwin that you download from Apple's website contains some precompiled binaries. The source for these is not provided, and you can't build the system without them.

This was why OpenDarwin was such a sham, and partly why it failed. Apple is perfectly within the law to distribute the Darwin system in this manner, but I cannot consider it to be open-source.

---

### Post by grazie on 2007-04-15
blippy,

Unless you got an old model, the 20" iMac you bought will have an intel cpu. Therefore alot of what has been said on this thread isn't relevent. You would have been better posting on the Apple Intel forum (if you have bought an intel mac). 

Having said that the big plus points of OS X are the ease of use and stability of both OS + Applications. The minus points are the cost (hardware and apps, I think the OS cost is pretty reasonable) and it's comparitively slow and resource hungry (not as bad as another piece of c**p that shall remain nameless).

Linux is mostly free in terms of cost and the freedom in having access to the source code. I've found Edgy to be much more stable on PPC than x86. Applications are not surprisingly always as feature rich, polished and stable as OS X, althoughly open source software can often be better than commercial alternatives. It is usually a lot faster than OS X and less resource hungry on the same hardware.

Linux on Intel Macs  do have their own set of specific problems, which are mostly concerned with booting and device drivers. (You'll get a lot more info on the other forum)

However, as you've already got the hardware why not make your own mind up.

---

### Post by dpny on 2007-04-15
> **3rdalbum said:**
> I know the distinction between Darwin and OS X's higher components. The source code package for Darwin that you download from Apple's website contains some precompiled binaries. The source for these is not provided, and you can't build the system without them.

This was why OpenDarwin was such a sham, and partly why it failed. Apple is perfectly within the law to distribute the Darwin system in this manner, but I cannot consider it to be open-source.

Interesting: this is the first I've heard about this. Which parts are the pre-compiled binaries?

---

### Post by blippy on 2007-06-11
> **blippy said:**
> Does anyone have any non-fanboy comments of the relative merits of OS X versus Ubuntu, particularly as regards stability, speed, ease-of-use, and HARDWARE COMPATABILITY?

I've been playing around for a bit. I tried out Sabayon earlier today. Can't say I'm impressed. It didn't install to my partition correctly, for starters. I decided to wipe my computer and let it use the whole HD. The screen resolution wasn't quite as I expected, and everything seemed "too large". I tried to emerge a package, but it ran into problems. I rapidly concluded that Sabayon was not for me. The disadvantages seem to severely outweigh the advantages. I've tried MEPIS, PCLinuxOS and Mint earlier this year, and they all had what I considered to be deal-breakers.

The state of play now is that I'm running Feisty as my sole OS on my iMac, although I would consider going back to OS X. My assessment of Ubuntu versus OS X so far is:
OS X has more polish, it looks gorgeous, and the things  that work work well.  Plus, my built-in webcam works - which is a huge bonus. OTOH, Ubuntu looks "OK" when I install the proprietary drivers, but Ubuntu wins big on the repos.

IMO, Ubuntu is the best Linux distro out there, and either OS X or Ubuntu wins depending on which day you ask me.:p

---

### Post by czechman86 on 2007-06-12
I myself run OSX, but like Ubuntu better. I only have a PPC computer, and so I must choose wisely what I will run. I would run Ubuntu if Skype worked on it, however, Skype does not work on Ubuntu for PPC, and open Wengo will never let log in, so I figured that if I switched back to OSX, communication would be much easier, and that it has. I prefer Ubuntu because it is easier to customize and I also enjoy OSs that are not graphically intense. As for flash, I can live in a world with out it. Let's face it, most everything that is flash is garbage and eats memory. I hope that this added something.

---

### Post by macluvjay on 2007-06-12
blippy,

You may be interested in checking out Mac-on-Linux.  It's pretty great at  virtualizing Mac OS on PPC machines from within Linux.  My suggestion would be to join us on irc at #mol on freenode and grab subversion.  The debian/ubuntu packages are a bit dated and there is heavy ongoing development from JoseJx of the Gentoo team.

---

### Post by TonySmash on 2007-06-12
my little take on the debate:

I've been using OSX for several years and while I love it, a month or so ago I decided I wanted a change. So I tried Ubuntu, and concluded that Ubuntu is CONSIDERABLY BETTER, if:

- I didn't screw up every single ubuntu install within a few days
- I didn't have to reformat, repartition, and reinstall Ubuntu and Tiger about 12 times in the past month
- I didn't have to spend 14 hours (literally) trying to get Airport Extreme to work
- Ubuntu would support flash. And java.
- And iTunes.
- Specifically iTunes w/ video. 

but, in general, I vastly prefer ubuntu. it has some BIG problems, but i find it a lot more fun to use than osx. using the terminal is new to me, but i already love it. having different workspaces is great. GAIM works better than iChat or Adium ever did. in general, it's been a lot of fun.

but unless youre willing to sit through a lot of pain and frustration (which, in my case, made the end result much more rewarding and now i'm addicted to ubuntu), stick with OSX. its....safer. much less risk of you throwing a coffee mug through your iMac's shiny 20" screen. 

:D

---

### Post by blippy on 2007-06-13
> **macluvjay said:**
> blippy,

You may be interested in checking out Mac-on-Linux.  It's pretty great at  virtualizing Mac OS on PPC machines from within Linux.  My suggestion would be to join us on irc at #mol on freenode and grab subversion.  The debian/ubuntu packages are a bit dated and there is heavy ongoing development from JoseJx of the Gentoo team.

Thanks, but my iMac runs on Intel.

---

### Post by blippy on 2007-06-13
> **TonySmash said:**
> my little take on the debate:

I've been using OSX for several years and while I love it, a month or so ago I decided I wanted a change. So I tried Ubuntu, and concluded that Ubuntu is CONSIDERABLY BETTER, if:

- I didn't screw up every single ubuntu install within a few days
- I didn't have to reformat, repartition, and reinstall Ubuntu and Tiger about 12 times in the past month
- I didn't have to spend 14 hours (literally) trying to get Airport Extreme to work
- Ubuntu would support flash. And java.
- And iTunes.
- Specifically iTunes w/ video. 

but, in general, I vastly prefer ubuntu. it has some BIG problems, but i find it a lot more fun to use than osx. using the terminal is new to me, but i already love it. having different workspaces is great. GAIM works better than iChat or Adium ever did. in general, it's been a lot of fun.

but unless youre willing to sit through a lot of pain and frustration (which, in my case, made the end result much more rewarding and now i'm addicted to ubuntu), stick with OSX. its....safer. much less risk of you throwing a coffee mug through your iMac's shiny 20" screen. 

:D

I guess it's horses for courses. For example, I'm not into iTunes, so it doesn't really worry me. What I would like going is my webcam. I had a scout through the forums, and it appears that the iMac webcam used to work, but there's a regression problem in Feisty. My worry with Ubuntu is that it's often the case of two steps forwards, two steps back.

Can't say I'm overly impressed with Beryl (although it doesn't actually work on my machine). It makes for good YouTube vids, but little else. I'm all for gorgeous, but let's not forget usability and simplicity. Actually, I notice that the Feisty background is a lighter shade of brown - and looks better than previous incarnations of the desktop. It's the details that make the difference rather than the bling. Installing the proprietory drivers makes the destop instantly look better - the fonts and icons are smaller. 

Whilst we're on the subject, has anyone had a look at Metisse:
[http://youtube.com/watch?v=dxsUKX6xXyE](http://youtube.com/watch?v=dxsUKX6xXyE)
I'm not sufficiently motivated to try it out myself, but it looks like the creators could bring GUIs to a whole new level.

In the meantime, I continue with Ubuntu, with its excellent collection of software, but its bogus webcam support. Come October, I guess it's time to make my mind up if I want to give Gutsy a whirl, or plonk down some cash for Leopard. :D

---

### Post by arkstfan on 2007-06-15
I'm still just piddling around with Ubuntu and I hate saying this but the issue for me is thinking. I actually have to think about what it takes to get things to work. After two years of OSX I've become terribly used to the old Apple slogan applying (it just works).

I've as yet not successfully installed any program not listed in the package for download and installation.

Personally I doubt I'll ever boot into Ubuntu a majority of the time because of the flash, wmv, realplayer issues. I really started playing around with Ubuntu because I was toying with the idea of starting my own business and wanted to see how feasible it would be to buy some less than cutting edge used computers and load them up with linux and OpenOffice. My testing shows it to be very feasible and a great way to keep down start-up capital.

If not for the multi-media issues my biggest problem would be the fan on my iMac G5. It rarely runs where I can hear it in OSX, and its a constant drone in Ubuntu. If you've never had an iMac you don't understand the fan issue. When I was first looking at switch from Windows I'd see people griping about the fan running, but I had a light tan box under the desk. Put it on the desk in a narrow enclosure and discover the maddening sound a fan can create.

---

### Post by stmiller on 2007-06-15
> **arkstfan said:**
> 
If not for the multi-media issues my biggest problem would be the fan on my iMac G5. It rarely runs where I can hear it in OSX, and its a constant drone in Ubuntu. If you've never had an iMac you don't understand the fan issue. When I was first looking at switch from Windows I'd see people griping about the fan running, but I had a light tan box under the desk. Put it on the desk in a narrow enclosure and discover the maddening sound a fan can create.

All multimedia codecs work fine in PowerPC Linux, including youtube playback with the latest gnash. Other flash sites are hit and miss. But I there is codec support for everything from windows media 9 to quicktime h.264, to realplayer. I listen to NPR news with Realplayer, and watch apple.com trailers in HD using the totem plugin. All in PowerPC Linux. Check out the PPCFAQs for help to install everything if you need help.

Which iMac G5 do you have? The iSight model? We need more feedback from iSight iMac G5 owners. The thermal problems are reportedly fixed with a Feisty kernel. Have you tried the Feisty version of Ubuntu? There are several iMac G5 Ubuntu users on this forum, also.

Most people don't understand that Linux is a community sort of thing. We need your help! So make a bug report, give some detailed feedback on forums, anything helps. :)

---

### Post by arkstfan on 2007-06-16
> **stmiller said:**
> All multimedia codecs work fine in PowerPC Linux, including youtube playback with the latest gnash. Other flash sites are hit and miss. But I there is codec support for everything from windows media 9 to quicktime h.264, to realplayer. I listen to NPR news with Realplayer, and watch apple.com trailers in HD using the totem plugin. All in PowerPC Linux. Check out the PPCFAQs for help to install everything if you need help.

Which iMac G5 do you have? The iSight model? We need more feedback from iSight iMac G5 owners. The thermal problems are reportedly fixed with a Feisty kernel. Have you tried the Feisty version of Ubuntu? There are several iMac G5 Ubuntu users on this forum, also.

Most people don't understand that Linux is a community sort of thing. We need your help! So make a bug report, give some detailed feedback on forums, anything helps. :)

No last model before iSight.

Thanks for the tips I'll start hunting the other stuff down.

---

### Post by powerpc64 on 2007-06-17
[http://ubuntuforums.org/showthread.php?p=2698277#post2698277](http://ubuntuforums.org/showthread.php?p=2698277#post2698277)

---

### Post by tgalati4 on 2007-06-17
Don't forget that you can run OS X and Desktop Manager to get 8 or more desktops.  You can run XDarwin as a slim Xserver in one or more of those desktops.  You can run gnome-panel either locally or through ssh to a remote Ubuntu machine.  This gives you a full remote desktop to another Linux machine with all of Ubuntu's goodness available.

You can install Fink commander.  (Fink doesn't really stand for anything) You can install several open source packages as binaries or compile from source (could take an hour or more).

This allows you to keep iTunes for all of your iCrack devices and still use open source applications and Gnome apps and remote Ubuntu machines.  OS X is quite versatile.

I agree with everything said in this thread.  Apple locks you in, and they have some restrictive policies and DRM, but OS X has the polish and stability that make it a first rate OS for PPC.  I've gotten 53 days of uptime on a G4 powerbook that I use for everything.  I had to reboot when trying to print to two printers simultaneously using HP's Image Zone software (quite bloated) and listening to iTunes.  Hard crash--Grey Screen of Death, Power-off is your only option.

Most of my previous reboots were forced due to OS updates.  If you don't have Tiger on G4/Firewire hardware, it's worth the $129 that they charge.

---

