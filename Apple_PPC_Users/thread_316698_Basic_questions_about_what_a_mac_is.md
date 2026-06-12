---
title: "Basic questions about what a mac is"
date: 2006-12-11
forum: Apple PPC Users
---

### Post by zugvogel on 2006-12-11
Hello. I was wondering if you apple-mac people out there could help me. I have never used a mac before - I grew up on windows, and have used linux exclusivly for 2 years. I need to get a new laptop, and for various reasons, I am considering getting a mac. I don't intend to install ubuntu, but since I am coming from a completely-ubuntu background, I thought I should my questions here.

1. I have seen that macs have a terminal - is it the same thing as linux with similar commands (eg, mkdir, passwd, etc).
2. Can I do ssh directly from the command line? Do you need to install X-windows on macs - will ssh -X work?
3. Can you lock the screen like in Ubuntu?
4. Do you need anti-virus?
5. Can you play microsoft file formats like wmv from the internet? What about ogg?
6. Is the DVD-playback like windows, in that it's locked to one specific region?
7. Can you compile linux-software to work on a mac? How do you solve the dependency problems? (I've never had to compile software on ubuntu - just used synaptic)
8. Is there any part of it that locks you into a proprietry format? Like windows media player ripping cds to it's own format, etc.
9. Is there a free equivalent of Kolourpaint and gimp ?

I hope that's not too many questions - thanks in advance for your help!!

---

### Post by 3rdalbum on 2006-12-11
1. Many commands that work in Linux work in almost exactly the same way in OS X.
2. SSH works, and X sessions can be forwarded to and from OS X.

4. I would recommend using as much security on OS X as you would on Windows. Most Mac users currently get along fine without anti-virus, but Apple has a lax attitude to security. Despite what the ads say.
5. There's a Windows Media Player for OS X, but you'll probably experience periods where Microsoft will update the codecs for Windows, but there will be a delay in porting them to Mac. There are audio players for Mac that will play Ogg.
6. DVD playback is determined by the drive, not by the operating system as far as I know.
7. There's a project called Fink - it's like apt-get for Linux programs on OS X.
8. Apple has its own DRM - iTunes by default will rip to AAC, when you make videos it will want to make them as Quicktime movies, all that sort of stuff.
9. I believe The Gimp is available for OS X. If not native, then through Fink.

Most important things to remember: Mac OS X is not open-source, not even its kernel. Mac OS X is not Linux; hell, it's not even Unix.

---

### Post by handylinux on 2006-12-11
Well, I thought you might as well have some answers from an actual Mac user (18 years Mac only, recently began to learn about Linux).

It sounds like you're planning to get a Mac and use Mac OS (not Linux) on it? If you do want to use Linux, either alone or via virtualization (running side-by-side using a utility like Parallels) or dual-booting, the new Intel-based Macs are ideal, as I believe x86 Linux versions will run perfectly on them (haven't tried it myself yet though). Pre-2006 Macs are PowerPC-based, will run Ubuntu and other Linuxes well, but with a few limitations (such as lack of Flash) that unfortunately make Linux not a complete alternative to Mac OS on PPC machines.

1. I have seen that macs have a terminal - is it the same thing as linux with similar commands (eg, mkdir, passwd, etc).
Mac OS X, which like Linux is Unix-based (or similar to Unix -- I'm not up on all the details of the situation), includes a Terminal program, which works like the one in Linux, so far as I'm aware. And I believe most of what it does, including commands like "sudo", would be familiar to any Linux user.

2. Can I do ssh directly from the command line? Do you need to install X-windows on macs - will ssh -X work?
I don't know what "ssh" is (Mac users simply don't have to do any command-line stuff, though in OS X they can learn about it easily if they wish), but previous response seems to cover this. Mac OS X also bundles a utility called "X11" which allows fairly easy use of many *nix-type apps in a special environment, however without access to many OS X features, such as installed fonts, etc.

3. Can you lock the screen like in Ubuntu?
I don't know what "lock the screen" means. Is it a security feature, requiring a password to access the computer? I don't think there's anything exactly like this in Mac OS X, but there are numerous security features available, including FileVault (which encrypts the Home folder -- but use with caution), and a password can be required to awaken the computer from sleep. There may be some third-party utility that will do what you want (there is a huge amount of Mac free/shareware).

4. Do you need anti-virus?
No, not really. As of now, there are no viruses or other malware that attack Mac OS X. There may be in the future, as the computer press continually trumpets -- I can only speculate why it is that so many computer journalists are so anxious to see Apple damaged in some way -- but there are none now, and have been none in the four-year history of OS X. That's none as in Zero, Nada, Zilch. The only reason to have antivirus software in OS X is if you exchange a lot of documents with Windows Office users; the many viruses that afflict their documents have no effect in the Mac environment, but a Mac user can unknowingly pass on an infected document received from a Windows user to another Windows user. Personally, I don't feel that my responsibility extends to protecting Windows users from themselves; they could, after all, get a Mac, or run Linux. 

I don't know what the previous respondent means about Apple having "a lax attitude to security"; Apple does release fairly frequent security updates when problems are found, and again, so far no regular Mac user has had to deal with any actual, real-world virus or security problem. As I said, I've used Mac OS exclusively for 18 years, made my living doing Mac support for 12+, and frankly, I know little about this whole subject, because, as a Mac user, I've never had to know anything about it. (I did see an actual virus on a Mac once -- about 1990. On a computer that was so poorly maintained I actually had to vacuum the dirt out of it to get at its components. There were freeware virus solutions for the classic Mac OS that took care of it.)

There are commercial anti-virus utilities available for the Mac (and most of the occasional panic announcements about potential Mac OS X vulnerabilities come from them, for some mysterious reason), but I regard them as a pointless expense -- and in fact, there've been numerous cases where they've done actual harm to Mac users' computers, "when used as directed," etc. There's a Mac version of the freeware ClamAV antivirus utility, which is all I recommend to my clients who might be concerned about the issue.

5. Can you play microsoft file formats like wmv from the internet? What about ogg?
Yes. Micro$oft ceased development of Windows Media Player for Mac some time ago, but the final version still works in OS X. Even better, though, is the free Flip4Mac utility, which allows WMV etc. content to be routed to and played through Mac OS X's built-in QuickTime technology. Ogg and, so far as I know, any other format playable in Linux can also be played in OS X; there is a Mac version of VLC Media Player. There are occasional problems with Windoze-specific media on Web sites, but as a Linux user you'd be used to that problem anyway.

6. Is the DVD-playback like windows, in that it's locked to one specific region?
Yes, DVD players in Macs, as in other computers, are region-specific in firmware. You're allowed something like five region switches before it locks up. However, there are third-party solutions which, I understand, allow further region switching on at least some hardware. It's a hardware not an OS issue.

7. Can you compile linux-software to work on a mac? How do you solve the dependency problems? (I've never had to compile software on ubuntu - just used synaptic)
Probably in many cases. Mac users have never had to "compile" anything, so I'm not familiar with what this is about. I've heard of Fink but never used it. I think much or most Linux software can be run under X11 in OS X anyway. See 9 below.

8. Is there any part of it that locks you into a proprietry format? Like windows media player ripping cds to it's own format, etc.
Yes, "Apple has its own DRM" as in content you buy from the iTunes store is in proprietary format(s). However, if you rip your own CDs in iTunes (or any of numerous other utilities, some free) you can do it any way you want. And you can even get around the DRM in iTunes-purchased music by recording it to a CD, then ripping it back. In general, I don't think the situation in Mac OS regarding such issues is any worse than anywhere else, and probably a lot better than in Micro$oft's totally-controlled environment. Apple has implemented whatever DRM it's had to do to make the iTunes system work, but its primary interest has always been in pleasing its own customers, not the media giants.

9. Is there a free equivalent of Kolourpaint and gimp ?
I don't know about Kolourpaint, but there is a Mac version of The GIMP, as well as other major FOSS applications like OpenOffice, Inkscape, Scribus, etc. Most at this point run in X11, though fully OS X-native versions (a.k.a. "Aqua", though that's actually no longer the official name of the Mac OS X desktop) are in the works. In the meantime, there are also OS X-native adaptations like NeoOffice (OpenOffice) and Seashore (The GIMP). There are also a lot of neat OS X-only free and shareware apps for alternatives to the Big Bloatwares.

As noted in the previous response, no, Mac OS X is not open-source. Nobody has ever so claimed. And no, Mac OS X is not Linux; as for "not even Unix", neither is Linux, strictly speaking, as I understand it. But both Mac OS X and Linux are based on "Unix-like" kernels, and, though the Linux I've seen so far is more like Windoze superficially (as expected, since its developers come from the Windoze world), Mac OS X and Linux are very similar under the hood.

And, I would say, similar in spirit. The fact that Mac OS X is commercial, and not Linux, doesn't automatically mean that it's just like Windoze. Apple is a corporation, yes, and often acts like one -- most Mac users have a love-hate relationship with the parent company; we love the OS and the computer (why is it nobody else seems to be able to make a computer that isn't ugly?) but are often annoyed by Apple's corporate antics -- but Apple is NOT Micro$oft. Apple competes in the open market by producing quality products, not by kneecapping potential opponents (the Tonya Harding strategy), etc. Just seeing Windoze on a computer screen makes me feel creepy and violated, but I enjoy Linux in much the same way I do Mac OS.

If you are really committed to free-and-open-source as a First Value, then Linux is the way to go. For me, it just doesn't do what I need, so I don't really expect to switch from Mac OS; but I do plan to learn more about Linux, and do what I can to help it do what I hope it'll do: overtake, surpass and eventually replace Windoze as the worldwide computer standard. I wouldn't want to see Apple do that, even if it could; it might very well turn into Micro$oft if it did. "Absolute power corrupts absolutely."

In fact, the problem isn't really Micro$oft; it's the irresistable temptation posed by that amount of power. Computer technology, like the internal combustion engine, is too important to the world for its basic foundation to be owned by anyone. My ideal computer future would see Linux (or something similar) as the worldwide standard, along with OpenOffice (and perhaps some other major apps, like The GIMP, Inkscape, Scribus). In such a Linux world, Mac OS would retain a small but solid niche market, for those who want the best and are willing to pay for it -- like Mercedes Benz and Steve Jobs' famous example, BMW. And then let Micro$oft show they can build a really good, *nix-based OS, and compete in a free market -- as Apple does now.

---

### Post by pauljwells on 2006-12-12
I've been a mac user for six years and a linux user for three. I've played quite a bit with compiling. Fink, networking etc and my answers to your questions are as follows:

1. The terminal is a bash shell, just like in Linux. The other popular shells are also included with OSX

2. You can use ssh with or without -X directly from the command line. You will need to install Apple's X11 client, which is on the install DVDs but is not installed by default, and use the included xterm as your terminal, rather than the OSX Terminal. The OSX ssh recognises ssh1 and ssh2 keys and uses .ssh in your home directory just like a Linux version. You can open port 22 using the graphic firewall config in the preferences panel.

3 You can set the screensaver to start when you move the mouse to a corner of the screen and you can set it to require your password to close.

4 No - you need to follow the same security rules as you do with linux really. OSX is very similar to Ubuntu in that the root account is disabled and you get root access with sudo (or with OSX's graphical equivalent)

5 Yes. Media player will play MS files, even those that are DRM'd. Flip4Mac runs unencrypted windows files. VLC is available for mac as are many other of the well known FOSS programs.

6. Hardware related - as the other responses have explained.

7. You can download Apple's own integrated development environment (IDE) called XCode for free from their developer website. It is similar to KDevelop, for example and is truly an excellent IDE. It is aimed primarily at writing for OSX, obviously, but also allows other development. It includes gcc glibc and all the other good stuff. Fink also has a repository of ported programs available for mac (requires the X11 client). Many are already compiled but you can compile your own too if you want. Some of the Fink ports are quite old though. Porting to OSX is made dificult by the filesystem, which is case preserving, but not case sensitive. makefile and Makefile are the same, for example. You can see this will make file tricky.

8. iTunes rips by default to AAC, which contains DRM, but if you rip from CD there are no restrictions on using these files on other machines. There are some limits to the number of times you can burtn to CD though. iTunes will rip to MP3 too if you set it in the preferences. Ports of LAME and similar FOSS programs are available in Fink.

9. Gimp is available in Fink as other responses have said.

I personally have always bought mac equipment - the attention to detail is excellent and the machines are actually good value when you compare specs with other stuff. Also, they have FAR better resale value than any other computer equipment. The new intel macs will run linux, OSX and windows all at once using virtualisation programs like Parallels. I think you can't go wrong - it is the route I have taken.

---

### Post by AlphaMack on 2006-12-13
These have already been answered in detail, but I'll leave my two cents...


*1. I have seen that macs have a terminal - is it the same thing as linux with similar commands (eg, mkdir, passwd, etc).*

Yes as it's a bash shell.

*2. Can I do ssh directly from the command line? Do you need to install X-windows on macs - will ssh -X work?*

Absolutely.  You just need to allow remote access from 'Sharing' in System Preferences if you want to be able to remotely SSH into your box.  

*3. Can you lock the screen like in Ubuntu?*

You can use a screen corner (set from Dashboard and Expose in System Preferences) or use the Keychain Access menu bar item (if you include it).

*4. Do you need anti-virus?*

Subjective, but if you need it, you can download [clamXav](http://www.clamxav.com/).  OS X includes a firewall (ipfw).  I don't want to come across as a fanboy of Rixstep although I frequently contribute to his forum, he has written several informative articles on protecting yourself:

[Oomp-A:  Hardening the Arteries Against the Chocolate](http://rixstep.com/2/20060216,01.shtml)
[Input Managers: The Cure](http://rixstep.com/2/20060227,00.shtml) (although this can be defeated by at least one cracker utility)
*Quick Note:  Oompa Loompa and more recently 'iAdWare' both exploit /Library/InputManagers as well as ~/Library/InputManagers.
[/Library FAQ](http://rixstep.com/2/20060316,00.shtml)

Moral of the story:  Use a standard account for day-to-day tasks.  Most software will prompt you for both the admin username/password when you do need to use the installer or even drag-and-dropping into non-privileged areas.


*5. Can you play microsoft file formats like wmv from the internet? What about ogg?*

You can use VLC.  For viewing WMV from a web browser (such as streaming video), use Flip4Mac (free download).  There is also a QuickTime plugin for Ogg [here](http://xiph.org/quicktime/download.html) although with iTunes you won't be able to stream over an AirPort Express.

*6. Is the DVD-playback like windows, in that it's locked to one specific region?*

Yes.

*7. Can you compile linux-software to work on a mac? How do you solve the dependency problems? (I've never had to compile software on ubuntu - just used synaptic)*

You can download Xcode from the ADC site (requires membership - free) or install the version from the OS X installation disc - you really need to install it for gcc.  As stated already, Fink has precompiled binaries but are often older versions.  On the plus side it uses apt.  Darwin Ports is the other package manager, but requires compiling from source.  

*8. Is there any part of it that locks you into a proprietry format? Like windows media player ripping cds to it's own format, etc.*

Unfortunately, OS X is all about lock-in with Apple's software.  Most of the time, while Apple software will have the ability to read open formats, you will end up saving in a proprietary format only readable by that program.  A perfect example is Mail.app.  With Tiger (10.4.x), Apple Mail stores your messages in a proprietary and undocumented file format .emlx instead of the standard mbox format.  If you later migrate to - say - Thunderbird, it is possible to convert your messages back to mbox for importation, but the process can be ugly as I have experienced myself.  I personally use the FOSS equivalents whenever I can in order to keep my personal data portable.

Mark Pilgrim wrote on the subject when he transitioned from OS X to Ubuntu:

[Bye, Apple](http://diveintomark.org/archives/2006/05/30/bye-apple)
[When the bough breaks](http://diveintomark.org/archives/2006/06/02/when-the-bough-breaks)
[Juggling oranges](http://diveintomark.org/archives/2006/06/16/juggling-oranges)

*9. Is there a free equivalent of Kolourpaint and gimp ?*

Absolutely.  GIMP is [available as a universal binary](http://gimp-app.sourceforge.net/).

A few more pieces of software I recommend on OS X:

AppleJack - Single user mode script to fsck your volume, repair permissions, clean problematic cache files, validate preferences, and clear VM.  Can be run in auto-pilot.  Free.

CLIX - Store frequently run commands in a database.  Comes with a bunch of database files for just about anything.  Free.  (Or if you prefer, Tinkertool to mess with defaults).

DiskWarrior - This will save your bacon when you need it when fsck can't fix HFS+.  $99.

Adium - Based on GAIM.

Burn.app - The closest thing to K3B without blowing money on Toast.  Free.

Cyberduck - FOSS FTP client.

iStumbler - War driver tool.  Free.

Pacifist - Front end for pax.

Of course, I also have:  Abiword, Audacity, Azureus, aMule, Democracy Player, DiVX, Firefox, Goliath (WebDAV), HandBrake, Inkscape, iTunes-BPM, iTunes-LAME, Max, MPlayer, NeoOffice (Aqua port of OOo), Nvu, Thunderbird, Vienna (RSS reader), VirtueDesktops (virtual desktops), iTerm, ManOpen, and OpenUp - all of which are free and some you might recognize in your Ubuntu installation.  And of course games like Supertux, Frozen Bubble, Metal Blob Solid (Blob Wars), and StepMania (open source DDR).

GIMP and Inkscape are the only two apps in my list that actually require X11.

---

### Post by zugvogel on 2006-12-13
alphasubzero949, pauljwells, handylinux and 3rdalbum - thank you all very much for your lengthy replies! This has really given me an insight into what a mac is, in language that I as a linux user understand, and I appreciate it very much. Thanks also for the list of applications you have - it's really useful to know that I can run all of those, as well as the additional software you suggest which will be useful.

I have been looking at the macbook (not "pro"). It sounds like it's possible to install Ubuntu on a macbook too - have you had experience with doing this (or any other intel mac)? Is it the same as doing it on a windows (ie, put the cd in, partition, install, etc).

Thanks again for your help - this has been very useful.

---

### Post by handylinux on 2006-12-13
The MacBook (not Pro) is very nice. I'd recommend getting the latest Core 2 Duo (call it 1.1) version, not the original (1.0) Core Duo, which suffers somewhat from first-release-itis. (The same goes for the original Core Duo MB Pro, which is even worse in this regard.)

Another poster wrote: "iTunes rips by default to AAC, which contains DRM".
iTunes rips by default to AAC (aka MP4), yes, but that's easily changed to any of a number of other formats (and in fact you'll want to change it for different jobs). And so far as I know, if you rip off your CD to AAC there's no DRM -- the DRM is in music you buy from the iTunes Store, which comes in AAC, Apple's "official" format.

I second the recommendation of AppleJack and DiskWarrior; excellent utilities.

Some Mac resources:
[Apple Discussions]("http://discussions.apple.com") online forums
[MacInTouch]("http://www.macintouch.com") community forum
[MacFixIt]("http://www.macfixit.com") "troubleshooting solutions"
[Macworld]("http://www.macworld.com") magazine online version
[Introduction to Mac OS X]("http://www.peachpit.com/articles/printerfriendly.asp?p=412362&rl=1") (Robin Williams)
[Mac 101]("http://www.apple.com/support/mac101") (Get Started with the Mac)
[Tiger Support]("http://www.apple.com/support/tiger") (Apple site)
[Apple Quick Assist]("http://www.apple.com/support/quickassist")
[Macintosh OS X Routine Maintenance]("http://www.macattorney.com/ts.html")
[Unleash Your Multilingual Mac]("http://homepage.mac.com/thgewecke/mlingos9.html")
[Apple Glossary]("http://docs.info.apple.com/article.html?artnum=51908")
[Macintosh Security and Privacy]("http://macintouch.com/security.html") (MacInTouch)
[Protect Your Mac]("http://www.macworld.com/2006/06/features/protectmac/index.php") (Macworld)
[Mac OS X Hints]("http://www.macosxhints.com/") (the hacker's home)
[Apple Software Support]("http://www.apple.com/support/software/")
[Open Source on Mac]("http://www.nothickmanuals.info/doku.php?id=opensourcemac")
[MacUpdate]("http://www.macupdate.com/index.php?os=macosx") (shareware listings)
[VersionTracker]("http://www.versiontracker.com/macosx/") (ditto)

---

### Post by 3rdalbum on 2006-12-14
I third the DiskWarrior suggestion, but it's best to back up and reformat after using it to rescue your disk. I used to use it as a full disk repair solution - so my disk would crash and DW would rescue it, then a few months later the disk would crash again and DW would rescue it... until finally the disk crashed and DW couldn't repair all the damage it has sustained through all the crashes and rebuilds. I nearly lost everything on the disk.

I know some people were questioning what I said about Apple security. There are many security flaws, and even some privacy problems, that Apple are aware of but refuse to fix. One of them allows you to install possibly-malicious applications without you having to provide your password.

Whereas, there's only one I know about on Linux. (and it's probably there in OS X too). Many Mac users say "there has never been any malware for Mac OS X in its 4 year history", but there have been, and information about one of them has been linked in this thread by another poster.

Sorry about the AAC comment - I was getting a little confused between iTunes and Windows Media Player. Actually, if you're concerned about lock-in, the only HD MP3 player that is officially supported on the Mac is the iPod (but this is the fault of the MP3-player manufacturers). You can get unsupported drivers for other popular MP3 players for OS X.

---

### Post by cabletie on 2006-12-15
> **pauljwells said:**
> 
8. iTunes rips by default to AAC, which contains DRM

Simply not true.

When you use a Mac, there is NO DRM on anything except for songs and videos you BUY from the iTunes Store.

To be clear:

When you rip a CD, it rips to AAC by default with NO DRM.

It's not even possible to put DRM on anything with a Mac, Apple doesn't publish the spec or licence it, so again, only files from the iTunes store that you paid money for have DRM. No-one is forced to buy from the iTunes music store. 

It wouldn't make sense for your own computer to put DRM on files you're creating, now would it?

---

### Post by 3rdalbum on 2006-12-16
> **cabletie said:**
> Simply not true.

When you use a Mac, there is NO DRM on anything except for songs and videos you BUY from the iTunes Store.

To be clear:

When you rip a CD, it rips to AAC by default with NO DRM.

True. In my above post, I apologised for my mistake.

> It's not even possible to put DRM on anything with a Mac, Apple doesn't publish the spec or licence it, so again, only files from the iTunes store that you paid money for have DRM.

Clarification: This does not mean that OS X prevents the application of DRM. It's just as easy to create a program that makes DRM files on OS X, and in fact Apple would have one of those. DVD Jon is currently writing some software that applies DRM, and this may run on OS X.

> It wouldn't make sense for your own computer to put DRM on files you're creating, now would it?

It wouldn't make much sense, but that wouldn't stop Microsoft. (and it wouldn't stop the RIAA from insisting that operating systems do that)

---

### Post by macogw on 2006-12-30
> **3rdalbum said:**
> 
Most important things to remember: Mac OS X is not open-source, not even its kernel. Mac OS X is not Linux; hell, it's not even Unix.
Yes it is.  It's a BSD!  That's a *nix.

The terminal on a mac is bash, just like in Ubuntu.  I want to figure out how to invert colours on the mac terminal.  black background / white text GOOD white background/black text BAD

---

### Post by 3rdalbum on 2006-12-30
OS X is not a BSD. It has small parts of FreeBSD in it, that's all. It's like saying that the Linux kernel is derived from NetBSD simply because they have the same Bluetooth stack.

---

### Post by handylinux on 2006-12-31
> **3rdalbum said:**
> OS X is not a BSD. It has small parts of FreeBSD in it, that's all. It's like saying that the Linux kernel is derived from NetBSD simply because they have the same Bluetooth stack.
Well, if you want to picks nits, it's also true that *Linux* "is not Unix". Both Linux and OS X are "**[Unix-like]("http://en.wikipedia.org/wiki/Unix-like")**" (Wikipedia link, for any who wish to explore the subject) operating systems, and both are consequently commonly thought of as derived from Unix, although technically (and for copyright purposes) neither really is.

Your original comment, as I read it, was intended to disparage OS X by comparison with Linux; you can do that, of course, but of the reasons you give for doing so, only the first is valid (that OS X is not open-source); that OS X is not Linux is, of course, obvious; that OS X is "not Unix" is equally true of Linux, thus not a criterion to distinguish the two.

If you *really* want to pick nits, and it's true that "The various BSD systems are notable in that they are in fact descendants of UNIX, developed by the University of California at Berkeley with UNIX source code from Bell Labs" (quote from Wikipedia article above), then seems to me it *could* be argued that Mac OS X, being based (if distantly) on BSD, has a slightly better claim to being "Unix" than does Linux, whose connection is slightly more distant.

But I wouldn't so argue. What I *would* argue is that Mac OS X and Linux users have more reason to be friends and cooperate than to pick nits at each other. Yes, OS X is commercial, not open-source; but it shares a "Unix-like" foundation with Linux; and both are tiny, beleaguered communities struggling to survive in a world dominated by a corporate behemoth which does not share any of the values that motivate both Linux and Macintosh -- excellence for its own sake and making computers for people (rather than vice versa) -- but instead survives (and prevails) by (a) buying or otherwise acquiring the fruits of others' creative effort, and then (b) "competing" by employing every "dirty trick" it can get away with to crush and wall out from the market any potential competitors rather than by offering the best products. See my [previous post]("http://www.ubuntuforums.org/showthread.php?p=1872452#post1872452") (final paragraphs) for more on this.

---

### Post by cabletie on 2007-01-01
> **macogw said:**
> 
The terminal on a mac is bash, just like in Ubuntu.  I want to figure out how to invert colours on the mac terminal.  black background / white text GOOD white background/black text BAD

Open Terminal.

Terminal menu -> Window Settings -> Color

Choose your color setup, then if you want it to stick click 'Use Settings as Defaults"

That should about do it.

---

### Post by Lord Illidan on 2007-01-01
> 
 6. Is the DVD-playback like windows, in that it's locked to one specific region?
 Yes, DVD players in Macs, as in other computers, are region-specific in firmware. You're allowed something like five region switches before it locks up. However, there are third-party solutions which, I understand, allow further region switching on at least some hardware. It's a hardware not an OS 

I'm confused, doesn't VLC bypass the regions with libdvdcss? or doesn't it do it under Macs?

---

### Post by cabletie on 2007-01-01
> **Lord Illidan said:**
> I'm confused, doesn't VLC bypass the regions with libdvdcss? or doesn't it do it under Macs?

VLC bypasses any region encoding on OS X.

I like the new onscreen controls when watching a movie fullscreen as well, the VLC guys certainly don't rest on their laurels.

I tend to rip with MacTheRipper, then use Toast to compress the VIDEO_TS folder down to the size of a single-layer DVD. Toast doesn't complain about copy protection once you remove all the crap with MTR.

---

