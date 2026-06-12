---
title: "Something like Arch Linux with no net?"
date: 2013-08-17
forum: Any Other OS
---

### Post by RadicaX on 2013-08-17
So I have been looking at things like Arch Linux, or Gentoo as of late. I like the idea of building from a very minimal install and putting what you would like on there, while learning about Linux itself. Trouble with them, is that you need internet basically to install packages on them. Something I can not afford to do with my limited amount of data a month. 
So would any know of a distro like them, that I could install on a machine, and just pop in a cd to get the packages needed off? (I am betting it can be done with them though.) Have any of you done anything like this before? Thanks for any input on this matter.

---

### Post by mamamia88 on 2013-08-17
Wouldn't downloading a 700mb cd per month eat more bandwith than just updating arch occassionaly?

---

### Post by Petro Dawg on 2013-08-17
If you are good at following instructions to the "T" and want total control of your OS build you can try [LFS]("http://www.linuxfromscratch.org/") (be prepared to learn a lot).

You would still need to download the source codes from online sources, but the size of the files are typically small.


Or you could use [Puppy Linux]("http://puppylinux.org/main/Download%20Latest%20Release.htm"), as the software in the repositories are typically selected for their small size as a top priority.  

Instead of going minimal, you could purchase a CD/DVD of a distro that has all the bells and whistles pre-installed by default so that no further downloads would be required.  [SolydK]("http://solydxk.com/products/solydk/") looks promising.

---

### Post by cortman on 2013-08-17
> **mamamia88 said:**
> Wouldn't downloading a 700mb cd per month eat more bandwith than just updating arch occassionaly?

He's referring to the initial installation- for those of us whose internet is not through some reliable and always-linux-recognizable manner (tethering, for instance) something like Arch and Gentoo can be a major pain.
@OP, AFAIK there isn't a way around that- it's just part of the system.

---

### Post by buzzingrobot on 2013-08-17
Look for a distro that offers a network installation option.  You'll install a very minimal amount of code initially, just enough to get the network connection working and point you at the right server. Then you can download and install only what you want. 

I believe there's a way to do a Slackware net install. You could get a barebones setup going, then, for a real educaton, start adding to it by downloading and building from source.  You'll learn a lot, including why dependcy resolvers were invented.

---

### Post by codingman on 2013-08-17
^

I think the OP wanted something that DIDN'T need much internet :)


Anyways, try Slackware, you can have all of your stuff on one DVD or multiple CD's and no need for internet connection.

---

### Post by RadicaX on 2013-08-17
@Mamaia,

Indeed. Not quite what I meant though. My internet at best is iffy. I use a 3G Modem with 5 GB a month to use at the moment. My other option is to go dial up. (Was surprised 56k modems and dial up were still sold in my area.) I can get packages like you noted time from time, But then again, it is possible for me to get the packages in one go at a friend's house off their super speed internet and linux machine. To which I can burn to cds and just install packages from there instead. (Seeing as how I am working on a desktop, it would not be good for me to bring it along to their house and just start building a Arch build.)

So the idea is not going and download 700 MB distros to try over and over. I want a small install, and then to build it up to help learn about Linux in general.

@PetroDawg.

Thank you. the LFS looks like my kind of thing right off the bat. I have used Puppy before, and it is pretty cool, and a good idea, because it is so minimal, I could add things as I seen fit to them time from time. And it is a good idea to buy a distro with all the bells and whistles, but it helps to defeat the purpose of what I am wanting to do. My main objective is to just increase my understanding of Linux in general.

@Cortman.

Thank you. And yeah, it is quite a pain. Guess that is how the cookie crumbles sometimes.

__

Basically, it would be pretty cool I would imagine to build it and set it up ready for the stuff with no net whatsoever.

Thanks everyone. You hit it on the head codingman.

---

### Post by buzzingrobot on 2013-08-17
> **codingman said:**
> ^

I think the OP wanted something that DIDN'T need much internet :)


Anyways, try Slackware, you can have all of your stuff on one DVD or multiple CD's and no need for internet connection.

The Slackware DVD is over 4 gigs these days.

The Debian network install image is something like 30 megs.  Ditto Ubuntu's, which is based on it.  The advantage is only downloading what you want, rather than downloading a 700-meg LiveCD or a larger LiveDVD and then only installing what you want off that.

---

### Post by mamamia88 on 2013-08-17
Maybe you can try arch and update it using a public wifi spot like a coffee shop or restaurant?

---

### Post by SweetAurora on 2013-08-17
You are going to to find it very hard to use Linux without Internet. Linux is **HEAVILY **internet dependent. It **MUST **have a connection to function correctly. If you want to try Linux without internet, try Linux Mint 13 or Precise Puppy Linux. Both practically have everything you would ever need to use, preinstalled. Like codecs, flash, java, office, ect...

Edit: The **DVD COPY **of Linux Mint 13 has everything installed. The CD version is just the main install. The DVD copy is ~4.7GB. Puppy on the otherhand is ~256MB or less.

---

### Post by RadicaX on 2013-08-17
Whoo, that is giant, 4 gigs on the dvd? That is cool though haha. Mama mia, that is a good idea, but alas not possible. It will be a desktop I am going to work with, not a laptop. If it was a laptop, I could use it somewhere rather than the middle of nowhere. Hence part of the need to be able to get the stuff on cds and just wham bam have it ready.

The minimal installs might work, if I could do a couple of the things at a time. First install 30 MB. and maybe being able to use 200-300 MB a month on downloads. I could see building it up after sometime.  (My network, with what limited data I have, is shared too, making things harder because I have to regulate usage among the four.) Or I could go to friends house, get the packages on a blank cd. (Because They would let me.) and try to install the packages that way. (Seen some kind of trick for installing on Ubuntu without going online, imagine it would work with the minimal install.) But how much would I learn that way? Ubuntu even in the command-line makes things pretty easy.

@Sweet.

Indeed. What is not internet dependent now a days?

---

### Post by codingman on 2013-08-17
You can buy the DVD online. I did a quick search on uncle Google and found a couple for 8 bucks. Yeah, kind of expensive for an open source distribution, but I guess it's better than having to pay lots of money for monthly charges.

I just thought of SliTaz, a nice lightweight distro with minimal internet requirements.

EDIT: Sorry, I mean a Slackware DVD can be found online for 8 bucks.

---

### Post by trent.josephsen on 2013-08-17
4 gigs is nothing. Debian is something like a 10-DVD set. Of course, nobody actually downloads them all -- that's why netinstall exists.

Slackware is a good choice because, unlike the rolling release distros, it doesn't depend on an *ongoing* Internet connection. You can install Arch from a CD with no net, but you wouldn't want to leave it like that because of the whole bleeding edge deal, and keeping it up to date is going to cost you in data. Gentoo is even worse. On the other hand, you can install Slackware from a CD with no net and it will be fine for months on only a handful of small updates. (At least, that's what I recall from last time I used it, which was several years back.) 

Of course, you still have to get the CD. You can install Slackware (with no X) from CD 1 alone (the 4-gig DVD isn't the only way to get it!), but honestly, if you're throttled just spend a few bucks (or euros or whatever) and [get it shipped to you]("https://www.osdisc.com/products/linux/slackware"). Or ask your friend to download it for you.

Debian is another good choice for someone with slow Internet for much the same reasons. Rolling release distros like Arch and Gentoo are death for someone with limited internet. (I installed Gentoo over dialup several times. I don't recommend it.)

---

### Post by codingman on 2013-08-17
Aah... there's that doggoned site!

---

### Post by RadicaX on 2013-08-18
I went to that site and was shocked how many dvds some of the "sets" had. 18 on one of the Linux Mint ones. The price is not to bad really, 33 bucks still beats the pants off any windows os out there. (XP is still 20$, and that does not include all the great free software out there.) I can see why you guys said slackware, with just a dvd, or set of cds, pretty cheap.  

So a question then to any who have done one of those minimal installs. Do you just redirect apt-get to the cd? (Or whatever package manager you might be using.) Pretty cool there is even sets out there for Ubuntu or Debian like that. I guess some other person out there in this big wide world had little to no net and wanted some great programs for his Linux of choice too.
So far Linux from scratch has looked the most appealing, for the ability to study it, and build up your own Distro.

---

### Post by Irihapeti on 2013-08-18
I've installed Ubuntu over the net a number of times. Back in the days when I had to watch my data use fairly carefully, I basically set up a repository on a machine on my LAN and directed apt-get to that. There are various ways of doing that - apt-cacher-ng is one of them which also works for Debian.

Whether or not you can direct apt-get to a CD/DVD depends on how it is set up. If it's just a collection of packages, it won't work. It needs to have the repository control files so that apt-get knows what to do with it. But the packages can still be imported into apt-cacher-ng

I'm not sure what's available for non-deb distros. There's almost certainly a way of setting up a repo on your LAN. You wouldn't need a fancy machine for it, either.

---

### Post by trent.josephsen on 2013-08-18
Debian has a tool called apt-cdrom that you can use to add a CD (with the proper index files as Irihapeti said) to the source list.

Slack used to have a utility... maybe it was pkgtool? It's been a while, but it would let you re-run part of the installation process to add and remove packages. It would use the CDs as sources. Pat may have changed it since then, so I couldn't walk you through the process, but it's still possible if you do a little research.

LFS is kind of cool, but I'd suggest installing it on a separate partition and not using it as your primary. Lots of things can go wrong and it'll take a long time to get it set up. Not to mention that you'll need a fallback when you eventually get sick of maintaining it ;)

For me Arch hit a happy medium of low-maintenance and high-control, and although I liked both Debian and Slackware for pretty much the same reasons, I had broadband at that point and nothing prevented me using a rolling release distro. Granted that was in like 2008 and the Linux world has changed a bit, but that's what I found. Hope it helps and good luck.

---

### Post by codingman on 2013-08-18
You can add and remove software by going through the ncurses setup again on the installation media.

---

### Post by cortman on 2013-08-18
If you're interested in building LFS, go for it! It's pretty much the ultimate as far as home-built GNU/Linux systems go. I built it myself a couple months ago but got sidetracked to other projects before I got X stabilized on it. It was challenging and quite eye-opening, and to be honest, not terribly hard so long as you **follow the book**. Good luck! :)

---

### Post by kevdog on 2013-08-18
Arch issues updates almost on a daily basis --  they are not too big however it seems newer kernel versions come down about every 2 weeks.  It's really painful as well to not keep up on your updates as things tend to break.

---

### Post by RadicaX on 2013-08-19
LFS is probably the way I will go. Debian maybe after that. I like the idea of not updating often unless it is for security. (Big plus to Debian on that.) The idea is to just learn about Linux and such more so. So that is what I want to do. I see someone on this forums quite a bit, can crack out a code and figure out what is needed to change and fix most problems. I think that is pretty cool. Something I would like to be able to do more of myself on these forums.

---

### Post by codingman on 2013-08-20
LFS is a very nice distro because it's your own! Just remember to follow each instruction very carefully, one wrong mistake and your crippled.

---

### Post by RadicaX on 2013-08-20
Will do. If it went well, maybe I could set it up for a more no internet friendly type Linux? (course it still would be friendly with net too, just friendly without it also.)

---

### Post by cortman on 2013-08-22
> **RadicaX said:**
> Will do. If it went well, maybe I could set it up for a more no internet friendly type Linux? (course it still would be friendly with net too, just friendly without it also.)

I find Mint/Ubuntu fits that bill fairly nicely, as it comes with about all the software I need OOTB.
Good luck and best wishes! >o>

---

### Post by RadicaX on 2013-08-23
Thank you very much Cortman. Indeed, both of them come with most things you need right out the box. But I would like it if my system was set up and easy to change as the things I needed changed. Maybe one day I would like to slap a new program on with no net, or a new DE, it would be nice just to get it on a cd, start up, and do as little as possible to have it working past that point. *Buntu has done this for all the programs I have wanted online, but with limited to no net, that can change the ball game a bit.

---

