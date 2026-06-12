---
title: "optimizing system with limited resources"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by rufi_dukes on 2007-05-09
i'm running an old pentium 2 with a modest 20 gig harddrive and 128mg of ram;
i want to know if anyone has suggestions as to:
-what linux distro is best suited to running under such limited resources
-what applications and system config generally would facilitate same, given that i have these fairly modest usage needs/aims:

-use email;
-read newsgroups
-use some math programs like maxima, kio, gmplot and the like;
-learn unix and slowly get to master the linux environment

in other words, can someone advise me (in the most dumbed down terms possible, please!) as to what distro and apps would best allow me to do above, working within the limits i've set out?

thx kindly,

---

### Post by rufi_dukes on 2007-05-09
forgot to mention the important fact that i'm running ubuntu 6.06 LTS which i installed from a CD, but that each time i get a few apps running, like pan, opera, (and especially in combination with synaptic) and say maxima.... the machine starts chugging and soon becomes impossibly slow or totally unresponsive...
sorry, this sh. have gone in original message!

rufus

---

### Post by stmiller on 2007-05-09
You can try a lightweight window manager:

sudo apt-get install blackbox blackbox-themes

Blackbox looks like this: [http://bb.lnix.net/screenshots/](http://bb.lnix.net/screenshots/)

or Xfce is quite nice, so try this:

sudo apt-get install xubuntu-desktop 

to get Xfce (I use it on an older laptop).

---

### Post by Nythain on 2007-05-09
you could try Xubuntu... xfce desktop is much lighter weight... or you could consider a completely different distro, i hear damn small linux is pretty light and fast... [www.distrowatch.com](www.distrowatch.com) lists just about every distro known to man, and some that arent :)

---

### Post by Spinelli on 2007-05-09
It sounds like you need Slackware.
[http://www.slackware.com]("http://www.slackware.com")

I think Slackware will meet most of your requirements. I would recommend the Fluxbox window manager. [http://www.fluxbox.org/]("http://www.fluxbox.org/"). It is very light weight.

Things I like about Slackware:

1. No added bullshit and no beta software
2. Runs very well on old hardware
3. Forces you to learn how the UNIX command line works
4. Simple, stable, and secure is the Slackware mantra.

I will warn you Slackware is not for the faint of heart. I don't think it comes with any of your math programs. You could hunt down a Slackware package for them using google or compile from source. If you learn Slackware you will understand GNU/Linux better than most people. Slackware is not for everyone. Try it I promise it won't kill you!

---

### Post by serfcx on 2007-05-09
My old Toshiba portege 7020 CT could not get on with Xubuntu and would only run at 640x480 no matter how I tried to change xorg.conf

Have a look at Zenwalk. I havent tried the new beta 4.6 but earlier versions work well and at 1024x768. Its Slackware based.

---

### Post by rufi_dukes on 2007-05-09
this is great!
thx for ALL replies and please, keep them coming as i want to get as many angles as possible on this...

another issue would be ease of installation, as i think it important to have a low threshhold of basic autonomy and utility... IOW, i can learn once i've got a stable, lean system running

thx again to all who have responded so thoughtfully 
rufus

---

### Post by ahaslam on 2007-05-09
You'll want to take a look at the 'run like Arch' link in my signature.

So If you're not looking to customise Ubuntu, you may wish to consider Arch for ultimate performance or perhaps Zenwalk for an easier life ;)

---

### Post by Spinelli on 2007-05-09
You might want to try Damn Small Linux or SLAX they are only live CDs. They are not designed to be installed to a hard drive, but they are very fun to play around with. They are both extremely light weight.

[http://www.slax.org/]("http://www.slax.org/") 
[http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")

If you want a distro you can install to your hard drive that is light weight I would recommend Slackware or Gentoo. I have never used Gentoo, and as you can tell from my previous post I am a Slackware freak. In my opinion Slackware is easier to install than Ubuntu. Of course you need to read the manual first! I started out using Ubuntu as my day to day desktop OS, but once I tried Slackware there was no going back. Warning using Slackware may lead to physical dependency and/or addiction!

The Slacker's Bible.
[http://www.slackbook.org/html/index.html]("http://www.slackbook.org/html/index.html")

---

### Post by rufi_dukes on 2007-05-09
having read all these responses i thought i might like to try slackware;
only to realize that this computer doesn't have the capacity to burn a CD;
it seems that all the minimalist versions of linux require that you be able to make a CD, or have i misunderstood sthg here?

i would have that this requirement is a bit at odds with the minimalist pitch to those having limited computing resources;

is there a minimalist version that i can just dload to my hard drive and "away she goes"...?

thx for yr continued patience and indulgence with a delicate newborn... (this goes for all respondants: many thx!)

ps by the way, i tried the Xubuntu option and quite like it, but ultimately, given the constraints of my machine (which i can't do anything about for several months till some sheckles come my way) i had better go for a slimmer version of linux

---

### Post by Terl on 2007-05-09
I used to use a very nice lightweight slackware based linux called [Zenwalk]("http://www.zenwalk.org/").  It is very easy to use and equally easy to install.  I used to run it on an old 233mhz gateway with 128 megs of ram.  Zenwalk is just under a 500mb download.  There is a link to purchase a disk (reasonable price) also.

If you cannot burn the cd's there are some quite reliable vendors out there that you can buy one from.  I used to get mine from a vendor when I still had dial-up.  It was just easier.  :)

---

### Post by Lord Illidan on 2007-05-09
I second Zenwalk Linux, fast and good.

It's forums are here : [Zenwalk Support - Index]("http://support.zenwalk.org/index.php")

---

### Post by rufi_dukes on 2007-05-09
i notice that it is recommended having a pentium 3 or greater for zenwalk;
mine is P2, malheureusement....
which is a bit offputting, since the whole idea is to try to optimize my old puter...
but thx anyway,
i might take a walk to our local shop tomorrow and see what they have got (i live in a remote corner of australia where we are not really well-served for such things)
cheers,
rufus

---

### Post by Terl on 2007-05-09
I would give it a try though.  I have run some distros on some very low specs...I had slackware 7 running on an IBM 760XD 166Mhz with 64MB of ram (I also had freebsd on it at one point and even Suse 7).  You just have to run very lightweight desktops (I used FVWM) and lightweight programs.  When I ran zenwalk on the old 233 I used sylpheed as a mail client and dillo for a browser for example.  

The key to much of this is the desktop.  I could make KDE run on the 233 but it was slow; gnome was better, xfce was even better, but blackbox, fluxbox, FVWM were all much better.

Hey, the worst that will happen is a reinstall :)  If you don't mind running in text mode you can still send email (Mutt or Pine) and even surf the net with Lynx.  I say go for it, have fun.

---

### Post by RedSquirrel on 2007-05-09
If you want to stick with an ubuntu system, you might try the barebones install. It uses the _net installer_, so you don't have to burn a CD.

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)


Using that, you can install a lightweight window manager such as Fluxbox or IceWM. 

In my case, I *can* burn a CD, so I downloaded the server CD, installed that, and then added Fluxbox on top. Now I just apt-get anything else I need...

Have fun. :)

---

### Post by ahaslam on 2007-05-09
> **rufi_dukes said:**
> having read all these responses i thought i might like to try slackware;
only to realize that this computer doesn't have the capacity to burn a CD;
it seems that all the minimalist versions of linux require that you be able to make a CD, or have i misunderstood sthg here?

i would have that this requirement is a bit at odds with the minimalist pitch to those having limited computing resources;

is there a minimalist version that i can just dload to my hard drive and "away she goes"...?

thx for yr continued patience and indulgence with a delicate newborn... (this goes for all respondants: many thx!)

ps by the way, i tried the Xubuntu option and quite like it, but ultimately, given the constraints of my machine (which i can't do anything about for several months till some sheckles come my way) i had better go for a slimmer version of linux

From Gentoos's site; "You can install Gentoo in many different ways. You can download and install from one of our Installation CDs, **from an existing distribution**, from a bootable CD (such as Knoppix), from a netbooted environment, from a rescue floppy, etc."

PS. it seems that Ubuntu also offers many alternate approaches: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
A tweaked server install as mentioned in '[run like Arch]("http://ubuntuforums.org/showthread.php?t=206022")' is just as quick as Zenwalk (quicker if you use openbox), get to it ;)

Good luck with whatever you decide.

---

### Post by Spinelli on 2007-05-09
> **rufi_dukes said:**
> having read all these responses i thought i might like to try slackware;
only to realize that this computer doesn't have the capacity to burn a CD;
it seems that all the minimalist versions of linux require that you be able to make a CD, or have i misunderstood sthg here?


If you are still interested in Slackware you should read the following link.
[http://www.slackbook.org/html/installation-requirements.html#INSTALLATION-METHODS]("http://www.slackbook.org/html/installation-requirements.html#INSTALLATION-METHODS")

It looks like you might be able to install an old version of Slackware without a CD, but all the newer versions require a CD. You could also order the Slackware CD sets at the Slackware Store.

[http://store.slackware.com/cgi-bin/store]("http://store.slackware.com/cgi-bin/store")

---

### Post by rufi_dukes on 2007-05-09
so, is it possible for me to go to my public library and on one of their windows machines, burn, say, 2 or 3 different ISOs for 2 or 3 different versions of linux, come home and wack the CD in my ubuntu machine and fire up and install either or all of these versions, just to try?

(i'm just not sure if i can format the CD with ISO properly if i'm doing it on a windows machine)
thx,
rufio

---

### Post by Lord Illidan on 2007-05-10
> **rufi_dukes said:**
> so, is it possible for me to go to my public library and on one of their windows machines, burn, say, 2 or 3 different ISOs for 2 or 3 different versions of linux, come home and wack the CD in my ubuntu machine and fire up and install either or all of these versions, just to try?

(i'm just not sure if i can format the CD with ISO properly if i'm doing it on a windows machine)
thx,
rufio

Yes, if they have a cd burner, and a cd program capable of burning in iso format. Nero Burning Rom, or CD burner XP Pro - freeware : [http://www.cdburnerxp.se/](http://www.cdburnerxp.se/) can do it pretty easily.

---

### Post by Cyklopz on 2007-05-12
Some additional info on DSL, it can be installed to your hdd or even to a usb key.  I'm running on an old presario 1700t with 192megs or ram right now.  It is fast and light weight but not a bad little distro.  I'm going to try the alternative install of 7.04 on this machine but may have to return to DSL if performance takes to great a hit.

Cy

---

### Post by rufi_dukes on 2007-05-12
> **Cyklopz said:**
> Some additional info on DSL, it can be installed to your hdd or even to a usb key.  I'm running on an old presario 1700t with 192megs or ram right now.  It is fast and light weight but not a bad little distro.  I'm going to try the alternative install of 7.04 on this machine but may have to return to DSL if performance takes to great a hit.

Cy

thx mate,
i'm currently stuck with what i've got: no CD burner, the library doesn't have a burner that will recognise the ISO format, and i live in a remote area....
stuck!
but i'm using this as an opportunity to study all the options,
and i've filed yr helpful comments...

thx again,
rufio

---

### Post by Spinelli on 2007-05-13
> **rufi_dukes said:**
> thx mate,
i'm currently stuck with what i've got: no CD burner, the library doesn't have a burner that will recognise the ISO format, and i live in a remote area....
stuck!


OpenBSD allows you to boot the installer from a floppy and then install via FTP. I would imagine this would take a very long time. Also OpenBSD is not very "user friendly". It is a very traditional Unix like operating system that aims to be the most secure operating system in the world. I use OpenBSD as a server not as a desktop operating system. 

[http://www.openbsd.org]("http://www.openbsd.org")
[http://www.openbsd.org/faq/index.html]("http://www.openbsd.org/faq/index.html")

You can always buy the CDs for Slackware, DSL, OpenBSD, or whatever and have them shipped to you.

---

### Post by Spinelli on 2007-05-13
It looks like Free DOS has some "unofficial" floppy images. I don't know if that would interest you.

[http://www.freedos.org/freedos/files/]("http://www.freedos.org/freedos/files/")

---

### Post by Harii on 2008-04-22
Too bad you don't have any friends or family with a cd burner.
But for a disro--
 i think antix-mepis would work great.
It works with older hardware and boots up in good speed.

---

