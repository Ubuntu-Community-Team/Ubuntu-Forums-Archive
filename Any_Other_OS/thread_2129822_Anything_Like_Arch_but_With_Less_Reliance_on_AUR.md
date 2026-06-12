---
title: "Anything Like Arch but With Less Reliance on AUR?"
date: 2013-03-27
forum: Any Other OS
---

### Post by mamamia88 on 2013-03-27
I love arch but I find myself having to use the AUR too often.  Is there something like arch but with stuff like dropbox and chrome in the default reposs?

---

### Post by mips on 2013-03-27
AUR is one of the things that makes Arch great. Instead of tracking a gazillion PPA's you have one source. What's wrong with using AUR? Installing any packages be it in the repos or AUR is as simple as a [B]yaourt -S <package_name>
[/B]
I use Manjaro which is based on Arch, they have a few extra packages in their repos but not much more.

---

### Post by lykwydchykyn on 2013-03-27
Since both Dropbox and Chrome are proprietary, I doubt you'll find a free distro that have both in its default repositories.

---

### Post by mamamia88 on 2013-03-27
Having to hit yes a million times when updating and typos or missing stuff from pkgbuilds occasionaly.  It's just a minor annoyance. With ppas you usually don't have to worry about that because it's already compiled and ready to go and includes everything you may need that isn't in default repos.

---

### Post by mips on 2013-03-27
Then use a ubuntu based distro if you prefer the PPA way.

---

### Post by ManamiVixen on 2013-03-27
Try Fedora! It's like Arch, but without the AUR.

---

### Post by mamamia88 on 2013-03-27
> **ManamiVixen said:**
> Try Fedora! It's like Arch, but without the AUR.
What makes fedora like arch besides modernity of packages.  Is the documentation as detailed as the arch wiki? How hard is upgrading between releases.  Is going between releases reliable.  Is there a system like ppas/aur for stuff not in the repos?

---

### Post by ManamiVixen on 2013-03-27
Documentation? Yes it exists. There is a large Fedora community, a Forum, and lots of tutorials on getting things installed, but it's scattered and requires googlling. As for upgrading, No, Fedora can't do that. Every time a new version of Fedora is released, you will have to reinstall. But they only release once a year so that isn't a huge issue for many. Also not Fedora is sorta Semi-Rolling each release updating some programs and core components when they come out, but the mojority stays the same version.

---

### Post by mamamia88 on 2013-03-27
> **ManamiVixen said:**
> Documentation? Yes it exists. There is a large Fedora community, a Forum, and lots of tutorials on getting things installed, but it's scattered and requires googlling. As for upgrading, No, Fedora can't do that. Every time a new version of Fedora is released, you will have to reinstall. But they only release once a year so that isn't a huge issue for many. Also not Fedora is sorta Semi-Rolling each release updating some programs and core components when they come out, but the mojority stays the same version.

I'm sure there is documentation come to think of it i'm sure alot of the arch documentation would apply to any distro so it's not really that big of a deal.   The upgrading think is kind of a big deal for me.   Also checked out one of my programs gpodder and it's stuck on 2.2 it seems in fedora where it's 3.5 elsewhere.  Probably just stick with arch for awhile.  I want to try freebsd and opensuse eventually.   Is free bsd worth installing or is it too big of a pain to use as a desktop?

---

### Post by pissedoffdude on 2013-03-28
Eh, you only mentioned a few packages.  If yourentire build depends strictly on AUR packages, I think chances are you're running proprietary apps, in which case Ubuntu's your go-to distro since it has the best support for them.  Is there a specific problem you're having with AUR packages, or yaourt?  There are other AUR helpers out there if youart isn't suiting your needs.  By the way, you can update your system, including AUR pacakges and official repository packages with a simple "yaourt -Syua"

---

### Post by wojox on 2013-03-28
> **ManamiVixen said:**
> Try Fedora! It's like Arch, but without the AUR.

 The recommended repository for Fedora is: [RPMFusion]("http://rpmfusion.org/")

---

### Post by wojox on 2013-03-28
> **pissedoffdude said:**
> There are other AUR helpers out there if youart isn't suiting your needs.  By the way, you can update your system, including AUR pacakges and official repository packages with a simple "yaourt -Syua"

+1, I prefer [packer]("https://github.com/keenerd/packer/wiki") myself.

---

### Post by mamamia88 on 2013-03-28
Nope only problem I have with the AUR and Yaourt is the fear that the person maintaing the packages will get bored or that there will be a typo or something when updating that will waste some of my time to fix.  Like yesterday I updated an app.  The maintainer had left off a dependency and typed a directory wrong.    I reported it and it was fixed in around 15 minutes but still was time that I could have been doing something else.   And the only propietary app I'm using atm is dropbox.   Everything else is open source.  As of right now these are all the AUR packages I have installed
```
local/aften 0.0.8-1
local/android-sdk r21.1-1
local/android-sdk-platform-tools r16.0.2-1
local/android-udev 1.7-1
local/autsmuxer-git 20130327-1
local/dropbox 2.0.2-1
local/go-mtpfs-git 20130326-1
local/gpodder3 3.5.0-1
local/menulibre 13.03.16-2
local/package-query 1.1-2
local/python2-mygpoclient 1.7-3
local/spdifconvert 0.4-1
local/tsmuxer 1.10.6-13
local/ttf-mac-fonts 1-5
local/ttf-vista-fonts 1-6
local/xfce-theme-albatross 1.3.1-1 (xfce-themes-shimmer-collection)
local/xfce4-places-plugin 1.5.0-1
local/xfce4-volumed 0.1.13-7
local/yaourt 1.2.2-1

```

---

### Post by kevdog on 2013-03-28
I'm still not seeing why AUR is a problem?  It's either that or a PPA or compile from source.  There is no way everything is going to make to any distribution's official repository, so there are always going to be compromises when adding in user supplied packages.  AURs definitely break from time to time, but so do PPAs

---

### Post by mamamia88 on 2013-03-28
> **kevdog said:**
> I'm still not seeing why AUR is a problem?  It's either that or a PPA or compile from source.  There is no way everything is going to make to any distribution's official repository, so there are always going to be compromises when adding in user supplied packages.  AURs definitely break from time to time, but so do PPAs

True.   I'm even editing my yaourtrc right now to try and miniimize the amount of button pressing.  Anyone know of a way to skip the editing check and only prompt me to edit files if something goes wrong the first time?

---

### Post by kevdog on 2013-03-29
You mean like the --noedit option?

---

### Post by catlover2 on 2013-03-29
I always like to review PKGBUILDs before using them, but the --noconfirm option works well enough to automate it.

@kevdog: what is --noedit? I don't see in the the yaourt manpage.

---

### Post by kevdog on 2013-03-29
Sorry I didn't post some incorrect information.  I use a combination of yaourt and packer (which is a yaourt helper application).  When you asked the question, I did a man search on both yaourt and packer but must have got the two windows confused when I typed the last post.  If you were to do a man packer however, you would find the following:

Snippet
```

OPTIONS
       --ignore <'package'>
           Ignore packages. Separate package names with a comma.

       --noconfirm
           Perform commands without confirmation from the user.

       --noedit
           Perform commands without asking if the user wants to edit any
           installation files.


```

I seem to use packer a lot for day to day operations like updating packages from the AUR and core repositories.  yaourt is definitely more full featured and I use this when having to manually reinstall the AUR developmental files (having to repull the bzr, or git packages) or removing AUR packages (since interestingly packer can only install files but not remove them).

---

### Post by NikiNfOuR on 2013-03-29
If recommending fedora, why not try fuduntu which is forked from fedora with the classic GNOME 2 ?? It is good. I liked it and is planning on using it in my desktop.... In fuduntu you have the Dropbox, Google chromium, Libre Office, Cairo Dock, Jockey everything pre-installed!!

---

### Post by mamamia88 on 2013-03-29
> **kevdog said:**
> You mean like the --noedit option?
I thought no edit would just skip editing altogether and if a build failed it would just loop

---

### Post by Rukiri on 2013-03-30
My answer would be gentoo, you compile from source and ebuilds are easy to work with.
Still a waiting game to install though but very easy, completely ignore genkernel it's worthless and with a lot of problems.. kernel 3.9.0-rc4 is very stable for an rc release. <-- it's what I use. 

It's also very stable once you get it up and running, but if you want something like arch I'd probably go with either Debian Sid(or siduction) or Gentoo(funtoo is also available, but it doesn't have the latest packages in it's portage tree like gnome 3.8 for example...)

I'll be nice, here's my make.conf, edit for your needs.

> 
# --[Compiler Flags]-- #
ACCEPT_KEYWORDS="~amd64"
ACCEPT_LICENSE="*"
CHOST="x86_64-pc-linux-gnu"
CFLAGS="-march=corei7 -O2 -pipe"
CXXFLAGS="${CFLAGS}"
MAKEOPTS="-j9 -l8"


# --[Portage Settings] -- #
PORTAGE_NICENESS="10"
PORTAGE_ELOG_SYSTEM="save"
PORTAGE_ELOG_CLASSES="warn error info log qa"
PORTDIR=/usr/portage


# --[Layman Settings] -- #
#source /var/lib/layman/make.conf
#PORTDIR_OVERLAY=/usr/local/portage


# --[System Settings]-- #
LINGUAS="en_US"
ALSA_CARDS="hda-intel"
INPUT_DEVICES="evdev keyboard mouse joystick synaptics"
VIDEO_CARDS="nvidia vesa"




# --[Use Flags]-- #
USE="bindist mmx sse sse2 sse3 bash-completion branding cleartype corefonts
truetype unicode dbus fontconfig gnome gtk gtk+ opengl qt4 qt3support X
cdpau webkit cups python ruby ffmpeg alsa ogg flack mp3 mp4 nvidia cuda
quicktime jpeg jpeg2000 midi png wav raw scanner libnotify ncurses
mudflap musepack musicbrainz networkmanager wicd nptl pam pango rss sasl sdl
sqlite startup-notification svg tiff usb vorbis wavpack wifi x264 xorg
xscreensaver xv xvid zlib zip unzip unrar theora declaritive sql script"


# --[Gentoo Mirrors]-- #
SYNC="rsync://rsync.us.gentoo.org/gentoo-portage"
GENTOO_MIRRORS="http://mirror.mcs.anl.gov/pub/gentoo/ rsync://mirror.mcs.anl.gov/gentoo/ [ftp://mirror.mcs.anl.gov/pub/gentoo/](ftp://mirror.mcs.anl.gov/pub/gentoo/) [http://mirror.datapipe.net/gentoo](http://mirror.datapipe.net/gentoo) [ftp://mirror.datapipe.net/gentoo](ftp://mirror.datapipe.net/gentoo) [http://gentoo.mirrors.easynews.com/linux/gentoo/](http://gentoo.mirrors.easynews.com/linux/gentoo/) [http://chi-10g-1-mirror.fastsoft.net/pub/linux/gentoo/gentoo-distfiles/](http://chi-10g-1-mirror.fastsoft.net/pub/linux/gentoo/gentoo-distfiles/) [ftp://chi-10g-1-mirror.fastsoft.net/pub/linux/gentoo/gentoo-distfiles/](ftp://chi-10g-1-mirror.fastsoft.net/pub/linux/gentoo/gentoo-distfiles/) [http://www.gtlib.gatech.edu/pub/gentoo](http://www.gtlib.gatech.edu/pub/gentoo) rsync://rsync.gtlib.gatech.edu/gentoo [ftp://ftp.gtlib.gatech.edu/pub/gentoo](ftp://ftp.gtlib.gatech.edu/pub/gentoo) [http://gentoo.mirrors.hoobly.com/](http://gentoo.mirrors.hoobly.com/) [ftp://ftp.ussg.iu.edu/pub/linux/gentoo](ftp://ftp.ussg.iu.edu/pub/linux/gentoo) [http://lug.mtu.edu/gentoo/](http://lug.mtu.edu/gentoo/) [ftp://lug.mtu.edu/gentoo/](ftp://lug.mtu.edu/gentoo/) [ftp://gentoo.netnitco.net/pub/mirrors/gentoo/source/](ftp://gentoo.netnitco.net/pub/mirrors/gentoo/source/) [http://gentoo.netnitco.net](http://gentoo.netnitco.net) [http://gentoo.osuosl.org/](http://gentoo.osuosl.org/) [http://gentoo.mirrors.pair.com/](http://gentoo.mirrors.pair.com/) [ftp://gentoo.mirrors.pair.com/](ftp://gentoo.mirrors.pair.com/) rsync://mirrors.rit.edu/gentoo/ [ftp://mirrors.rit.edu/gentoo/](ftp://mirrors.rit.edu/gentoo/) [http://gentoo.mirrors.pair.com/](http://gentoo.mirrors.pair.com/) [ftp://gentoo.mirrors.pair.com/](ftp://gentoo.mirrors.pair.com/) rsync://mirrors.rit.edu/gentoo/ [ftp://mirrors.rit.edu/gentoo/](ftp://mirrors.rit.edu/gentoo/) [http://gentoo.mirrors.pair.com/](http://gentoo.mirrors.pair.com/) [ftp://gentoo.mirrors.pair.com/](ftp://gentoo.mirrors.pair.com/) rsync://mirrors.rit.edu/gentoo/ [ftp://mirrors.rit.edu/gentoo/](ftp://mirrors.rit.edu/gentoo/) [http://gentoo.mirrors.pair.com/](http://gentoo.mirrors.pair.com/) [ftp://gentoo.mirrors.pair.com/](ftp://gentoo.mirrors.pair.com/) rsync://mirrors.rit.edu/gentoo/ [ftp://mirrors.rit.edu/gentoo/](ftp://mirrors.rit.edu/gentoo/) [http://gentoo.mirrors.pair.com/](http://gentoo.mirrors.pair.com/) [ftp://gentoo.mirrors.pair.com/](ftp://gentoo.mirrors.pair.com/) rsync://mirrors.rit.edu/gentoo/ [ftp://mirrors.rit.edu/gentoo/](ftp://mirrors.rit.edu/gentoo/)
[http://mirrors.rit.edu/gentoo/](http://mirrors.rit.edu/gentoo/) [ftp://mirror.iawnet.sandia.gov/pub/gentoo/](ftp://mirror.iawnet.sandia.gov/pub/gentoo/) [http://mirror.iawnet.sandia.gov/gentoo/](http://mirror.iawnet.sandia.gov/gentoo/)
[ftp://gentoo.llarian.net/pub/gentoo](ftp://gentoo.llarian.net/pub/gentoo) [http://gentoo.llarian.net/](http://gentoo.llarian.net/) [ftp://gentoo.mirrors.tds.net/gentoo](ftp://gentoo.mirrors.tds.net/gentoo)
[http://gentoo.mirrors.tds.net/gentoo](http://gentoo.mirrors.tds.net/gentoo) [http://ftp.ucsb.edu/pub/mirrors/linux/gentoo/](http://ftp.ucsb.edu/pub/mirrors/linux/gentoo/) [ftp://ftp.ucsb.edu/pub/mirrors/linux/gentoo/](ftp://ftp.ucsb.edu/pub/mirrors/linux/gentoo/)
[ftp://ftp.lug.udel.edu/pub/gentoo/](ftp://ftp.lug.udel.edu/pub/gentoo/) [http://mirror.lug.udel.edu/pub/gentoo/](http://mirror.lug.udel.edu/pub/gentoo/) [http://gentoo.cites.uiuc.edu/pub/gentoo/](http://gentoo.cites.uiuc.edu/pub/gentoo/)
[ftp://gentoo.cites.uiuc.edu/pub/gentoo/](ftp://gentoo.cites.uiuc.edu/pub/gentoo/) rsync://gentoo.cs.uni.edu/gentoo-distfiles [http://gentoo.cs.uni.edu/](http://gentoo.cs.uni.edu/)
[http://mirror.usu.edu/mirrors/gentoo/](http://mirror.usu.edu/mirrors/gentoo/) ftp://ftp.wallawalla.edu/pub/mirrors/ftp.gentoo.org"


---

### Post by iamkuriouspurpleoranj on 2013-03-30
It's going to be difficult to find a distribution that keeps on the bleeding edge but keeps everything *in distro.* Certainly compiling would seem the best way for you to go whether it's with Arch, Gentoo, Slackware or FreeBSD. Personally I'm starting to warm to "bleeding old" distributions like CentOS.

---

### Post by trent.josephsen on 2013-03-30
For myself I just try to keep my AUR usage to a minimum, and it's not usually a problem when I do have to upgrade things. I don't really use anything proprietary except Flash, though.

If I found that managing my AUR packages was eating too much time... I'm tempted to say Gentoo, but Gentoo does have that annoying tendency to consume all your free time. Fedora is probably a good option if you're ok with giving up rolling release. If you like the rolling release model, though, I'm sorry but Arch is by far the least maintenance-intensive option I've used, nearly on par with Debian. Fuduntu looks cool, though, really. If I were in your situation that's probably the one I would try first.

Be aware that **anyone** can upload a package to AUR, and the packages are not signed. If you do not verify the PKGBUILD is trustworthy, you could find yourself downloading and installing malware. This is why yaourt doesn't allow you to suppress the editing prompt. (I guess packer does, though, so if you think that's an acceptable risk, nobody's stopping you from using that.)

---

### Post by Rukiri on 2013-03-31
I generally find the aur packages buggy and half the time they never install, that's why I prefer ebuilds mainly because they are apart of the official repos but they just seem to work and the packages themselves even run better as well (don't know the reason) but they do, cinnamon for example the control panel will not open but does in gentoo.  It's all about packaging, I wouldn't consider arch on my main system but as a test system sure if it's from the official repos if not, no thanks.  

Debian sid or siduction and obviously gentoo are the best choices at least in my opinion, would be nice to see another ubuntu distro but was rolling release, I like apt-get, but installing every 6 months is a pain<.<

apt-get, yum, and portage are the best package managers for linux, pacman is nice but it's no apt-get or portage.

Again if you like the debian experience I'd stay with debian and go sid with it's rolling release, it's the only distro outside gentoo I'd go with these days.  
The cool factor of arch just wore off after while, it's great it let's you build your system but if I want to build my system from scratch I'm going source and I believe ubuntu/debians repos have a much large application count than arch.  Gentoo pretty much has everything.
If you want gentoo I can pretty much sum up your install with a quick text but reading the handbook is nice, everytime I install I go through it albet being lazy and just copying the commands mainly as I already know what they do and what they're for.

There's also another distro Funtoo, the main difference is that it's portage is git based ny rsync, personally.. I'd rather have a more up to date portage tree as funtoo just started adding gnome 3.8 today, while gentoo started adding on day 2 of release (no distro has the latest on day 1, maybe large distros like ubuntu or fedora(especially fedora, if you want a good gnome experience fedora is a nice system but remember to reinstall every release... that's the bad part about fedora it's a nice system/os but it plagues you to update constantly, I work with a lot of game code and updating is not an option which is why I went with a rolling release, )

Fedora
Gentoo
Debian Sid (or the distro siduction which is based on debian sid)
Funtoo (slightly better core system than gentoo and git based portage but the tree isn't as up to date as gentoo and doesn't have every package that gentoo does)
Fuduntu (A Rolling released - sort of)
OpenSuse (The build system is nice and overall it's a nice distro that uses kde)

---

### Post by andrew.46 on 2013-03-31
My base system is Slackware and I believe this shares a common feel with Arch. The dependency tracking issue with Slackware is only an issue for people who have never actually used Slackware :).

---

### Post by mamamia88 on 2013-03-31
So i settled on xubuntu 13.04.  While it was installing I wrote a bash script that added all the ppas i wanted, downloaded all the apps i wanted, and completely removed most of everything I didn't want.   My nexus 7 mounts right out of the box and it feels super smooth. It also came with the theme I use on every xfce distro anyway albatross.   Gotta say I might have a keeper.  Not a rolling release but I'll keep up hope.

---

### Post by os2 on 2013-04-20
Might as well have gone with Fuduntu. But the jungle is so crowded there you'd have difficultly seeing the wood from the trees. That's what it's always like coming from Arch. I don't like the AUR either as it was too much work and many free packages were missing.
Better yet, openSUSE, this is like God's Distro.

---

### Post by iamkuriouspurpleoranj on 2013-04-20
^openSUSE is _ok_ but you flatter it to call it *God's distro*.

---

### Post by os2 on 2013-04-20
Maybe you care to make a suggestion then?

I've gone crazy over the past month or so hopping from Ubuntu, Mint (Debby Derivatives), Fuduntu, Fedora, Arch. Here's the list I had to go on: distrowatch.com

I was able to find all my apps under one roof only under openSUSE.

---

### Post by iamkuriouspurpleoranj on 2013-04-20
openSUSE has the same over-reliance on community repos/builds, so would it meet the needs of the OP?

Glad you found a distro you like but my experience has not been so rosy. As one example, I can install XMind on anything (Fedora, CentOS, Manjaro, Mageia etc.) and it only exists as a .deb package. Yet I've never had any luck with installing it on openSUSE. That's surely my fault but nonetheless I find "God's distro" an exageration.

To avoid reliance on third party packagers but stay on the bleeding edge, you'll need to compile.

---

### Post by os2 on 2013-04-20
I was going to ask you how does any of this help the OP.

What's the alternative you've not said? All the main distros quoted rely on community support to some extent or another. The "claim" of finding all packages "under-one-roof" took account of this.

Lest we forget, Linux is Linux. And if you strip a package to its nuts and bolts you can get it to run on any distro. That's the essence of Linux. Question is, how far deep are you inclined to go to strip an app to its bare bones in order to get it to work?

PM me if you still need help getting your app to work on openSUSE.

---

### Post by mips on 2013-04-20
Fuduntu is dead sorry to say.

I still don't get peoples issues with AUR.

---

### Post by fuduntu on 2013-04-20
Fuduntu won't be "dead" until September.  Until then it is still supported, just like any non-rolling release distro. :)

---

### Post by mips on 2013-04-20
Sorry, that's just the impression I got. For all practical purposes it's dead by your own announcements.

Do you guys have any future projects in mind?

---

### Post by fuduntu on 2013-04-20
> **mips said:**
> Sorry, that's just the impression I got. For all practical purposes it's dead by your own announcements.

Do you guys have any future projects in mind?

We were pretty specific when we said September 30th.  Ubuntu's releases (non LTS) go into maintenance mode on release day and are supported for 9 months, does that make them dead when they are released?  Nope. :)  Same concept, except when we end support for 2013.2 we are going to end the project at the same time.

No new development, but maintenance.  I wouldn't recommend new users come to us, with only 5 months of support left but existing users should know that they don't have to jump ship today. :)

I have no future projects on my plate, except living life.  The team members that decided to move forward with a new project are meeting tomorrow in #fuduntu to discuss their future distribution.

---

### Post by iamkuriouspurpleoranj on 2013-04-21
^the problem with AUR is unsigned packages

^^The help was to point out that there's always a trade-off. The best strategy for bleeding edge is to know what you're doing and be your own package maintainer. I can't blindly trust a company that sits behind a distro (Novell for openSUSE or Canonical for Ubuntu) but at least I know what it is, where it is and can sue it or lob a brick through a window at its offices if something bad happens. With jiM_@Nonymuss_hACkeR, I never feel quite safe enough, despite his excellent reputation in the community.

@OP, try openSUSE. I am running it right now. I don't share OS2's opinion that it's "God's Distro" but it is fairly up-to-date and if you feel comfortable relying on third parties, then it might be your thing. However, I was under the impression that you wanted to avoid that.

---

### Post by Rukiri on 2013-04-21
> **mips said:**
> Fuduntu is dead sorry to say.

I still don't get peoples issues with AUR.
For the most part the packages are buggy and they have to edit to fix, now official packages are another thing (if your using pacman you're alright) but if you're rebuilding from source prepare for a world of errors and bugs

My recommendation is still gentoo, it's VERY easy to install just time consuming... takes me about 30 minutes to go from install to actually booting my system, than... 5 or so hours compiling needed packages.  

Arch linux is awesome and does have a ports system and you are optimizing for your hardware (well maybe architecture) but it's a farcry from portage which I think is much easier to work with and takes less time to compile.
The way the PKGBUILDs or made is kinda sad, it does track dependents but that's it, it's not tracking version # and with ebuilds it does and generally as long as you have version X or newer it will compile no problem but that's not how it's going to work with arch, and 900 ebuilds is way to many to edit and is actually 100% more time consuming than gentoo is.   a52dec is a great example, mismatch version of libtool, easy to fix but when the upgrade comes it'll happen again and again as you're always going to have a newer base-devel than what it was compiled for. 

Arch linux bar non is the best binary linux distro, but source is not it's cup of tea..

You're asking for a rolling release, the best 2 are Arch and Gentoo.

Also if you do choose gentoo, don't pick Funtoo, for some reason it's disk management wil bork your system fast (you'll run out of space in maybe a day or 2 without installing anything... it is a known bug but it's not existent in upstream gentoo)  I do like funtoos addwifi command, but wicd works just the same well.. almost.  It loses signal often, addwifi keeps the single.   But I usually uninstall and purge wicd once I have KDE installed and NetworkManager. 

If you want pretty much a hands on approach to linux and want to absolutely do it yourself, then your going to have to go with Linux from scratch.  I've done it a few times, it's not hard it's just very time consuming (just think of doing the gentoo 20X over and over without a break).  It takes me about 3-4 hrs just to get my stage3 completed but once that's done I actually CAN turn it into gentoo and run it like normal or install pacman and call it a day as your system by that time is completely optimized for your system.

Read this
[http://www.gentoo.org/doc/en/faq.xml#stage12](http://www.gentoo.org/doc/en/faq.xml#stage12)

Basically it's telling you to bootstrap your system (which is rebuilding your toolchain)  and then emerge - system which rebuilds your core packages.  This basically insures that your system is 100% optimized for your CPU/architecture.
There's also source mage, it is linux from scratch, now source mage does nothing to the packages, no fixes, no nothing it just packages it for it's package manager but... I prefer portage, sourcer is written is bash so it's a faster package manager but compiling times are the same and Useflags are awesome.  All my LFS boxes use portage, except one which uses pacman which I just use as a dev machine.

---

### Post by trent.josephsen on 2013-04-21
@Rukiri, you seem to be pushing the source-based angle pretty hard, but I don't think that's particularly relevant. I agree, if you like to recompile stuff from source a lot, Arch is probably not the way to go. But if you want a simple Linux that works without a long and painful install process, and doesn't require surgical levels of maintenance post-install, Gentoo is probably not the best choice either. Let's not go all fanboy here and realize that our favorite distros have their own drawbacks that we have simply learned to deal with.

---

### Post by joco1500 on 2013-04-21
Fuduntu has those as the default

but i dont think that its what your looking for

---

### Post by Elfy on 2013-04-21
Closed. This was finished 3 weeks ago.

---

