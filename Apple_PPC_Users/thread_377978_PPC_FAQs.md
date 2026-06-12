---
title: "PPC FAQs"
date: 2007-03-06
forum: Apple PPC Users
---

### Post by grazie on 2007-03-06
I don't know about anyone else, but I think it's time for a Ubuntu PPC FAQ sticky on this forum. It would contain a set of FAQs that would point to other postings or wiki pages or elsewhere for further detials. It would contain things like booting problems, known sound problem, known bugs, etc. If something like this already exists (I'm surprised it doesn't already), that could be maintained and made sticky.

As an Apple Intel forum has not long ago been set up, I'd imagine it would be a similar process to get it sorted?

---

### Post by deltaboy38655 on 2007-03-07
Excellent idea!  I'm running Herd 5 on a Power Mac G4 & love it except for no Flash & lack of support for proprietary graphics card drivers.  No Envy, etc...  It will be interesting to see what develops from this forum now that bo PPC support after 7.04.  Anybody know anything about this "Irish PPC DIstro"?

deltaboy38655

---

### Post by ssam on 2007-03-07
a wiki page is easier for people to add to and edit.

i started one at [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) please add some more bits

---

### Post by stmiller on 2007-05-04
Hi, I'm working to add lots to the wiki page right now. Thanks for setting this up!

Okay added Multimedia tips, Powerbook things, 3D driver info, along with other stuff.

---

### Post by Radiolad on 2007-05-12
Hi, I have just logged in after 3 weeks of  'non-ubuntu' PC-ing. This is mainly because of the mind-boggling variety of terms used on Linux/Ubuntu. I have managed to setup my iMac G3 with Ubuntu but as yet backed away from any attempt at loading it onto my PPC G4 machine.  Having just watched the BBC 'Click' this morning I decided to dip into the Ubuntu forums again.
I am VERY pleased to see this Apple PPC User section you are compiling :)   and hope it will re- install confidence in my decidedly lacking ability with Ubuntu. I find 'command lines' and 'terminals' very daunting as I always feel I'm going to b-----r something up and thus end up with a dead PC  :( 

All good wishes to you. I hope to make the most of these pages in the near future.    RADIOLAD

---

### Post by indica on 2007-05-13
thanks ssam! we needed a faq like that in here!

---

### Post by ssam on 2007-05-13
> **indica said:**
> thanks ssam! we needed a faq like that in here!

thanks to stmiller too, hes put a lot of work in. a few other people have helped out too. (if you click on the get info button at the top of the wiki page it shows you all the edits)

---

### Post by stmiller on 2007-05-13
> **ssam said:**
> thanks to stmiller too, hes put a lot of work in. a few other people have helped out too. (if you click on the get info button at the top of the wiki page it shows you all the edits)

Hey no prob! I have some other tips and info I'll post on the wiki when I get some time. I've picked up a lot from the gentoo ppc irc folks. They are very helpful and know the hardware.

---

### Post by ssam on 2007-06-10
the FAQ has progressed a huge amount over the past months. thanks to everyones hard work.

i am wondering if it would be good to do a bit of a clean up on it. one thing i am worried about is duplication of work. For example the section on adding java has the same information as the Java page on the wiki. if the method for adding java were to change, then two places on the wiki would need to be fixed. I think it would be better for the powerpc faq page to mostly be links to other articles in the wiki.

also perhaps we should do some renaming. Maybe we could have the following pages

PowerPC             - an introduction and index of relevant pages 
PowerPC/FAQ    - the FAQ
PowerPC/Downloads  - links to downloads, mirrors, dev versions
PowerPC/Supported Hardware - a good index of apple hardware, with information about what works

then we can easily add things like

PowerPC/Tweaking ATI drivers

I can ask someone from the docteam about the naming scheme.

---

### Post by also-rr on 2007-06-10
> **deltaboy38655 said:**
> Excellent idea!  I'm running Herd 5 on a Power Mac G4 & love it except for no Flash

You can have Flash if you want it :) Even works with Youtube.

[Swfdec Ubuntu install instructions.]("http://revis.co.uk/site/?q=node/157")

---

### Post by ssam on 2007-06-17
ok

stmiller seems to be in agreement (via private message).

I spoke to matthew east (from the doc-team) on irc
> 
<ssam> i'd like to clean up the powerpc information on the wiki. what is the best way to organise it? should i have a PowerPC page that links to things like PowerPC/FAQ PowerPC/Downloads PowerPC/Installation etc?
<mdke_> ssam: sometimes we use subpages, but not for whole architectures
<mdke_> for topics like installation, we do it - [https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC)
<ssam> so should there just be lots pages with names like PowerPCFAQ
<mdke_> no, I think that would be a bad idea
<mdke_> you should try and integrate material with the existing material on topics; for example if there is a topic which has specific powerpc related issues, you could make a subpage (as with Installation) or include a note in the main page
<mdke_> have a look at the homepage to see how things are organised
<ssam> but there are quite a lot of powerpc specific issues, especially now that its a community port
<mdke_> sure. It's the same with amd64
<ssam> it would be nice to have somewhere to point people to show that ubuntu on powerpc still exists
<mdke_> you could create a page simply called "PowerPC" and include some basic information about the architecture and links with pointers to other helpful material
<ssam> the main ubuntu web site does not give any clue where to find downloads of powerpc for example
<mdke_> that's a bug
<ssam> its been reported
<mdke_> yes, that's what I mean
<ssam> ok, i'll do a PowerPC page
<mdke_> as for downloading, it's mentioned on this page - maybe you can point to that. [https://help.ubuntu.com/community/ProcessorArch](https://help.ubuntu.com/community/ProcessorArch)
<mdke_> (that page is linked from the front page)
<ssam> also the PowerPCFAQ is a bit of a mess. i think it should have less information on it, and be more a collection of links to useful information, does that sound sensible
<mdke_> yes, absolutely sensible. I'm not a fan of FAQs at all, in fact
<ssam> thank you for your advise
<mdke_> thanks for contributing :)


So we need to integrate as closely as possible into the rest of the wiki, rather than have a PowerPC section.

I shall start PowerPC page today

bits of information from the PowerPCFAQ need to be but into the generic wiki pages where possible, and be linked to.

there hardware support information will need to go in [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by ssam on 2007-06-17
[https://wiki.ubuntu.com/PowerPC](https://wiki.ubuntu.com/PowerPC)

---

### Post by lixy on 2007-07-22
Nouveau is misspelled "Nouveou" in the following section.

[https://wiki.ubuntu.com/PowerPCFAQ#head-d6be5f475782e6b1d7c441ad9571a2d83d8cbffa](https://wiki.ubuntu.com/PowerPCFAQ#head-d6be5f475782e6b1d7c441ad9571a2d83d8cbffa)

Please take a sec' to fix that.

---

### Post by donnux on 2007-07-23
I just posted about my problem of Ubuntu not installing.

Then, to kill time, I read the PowerPCFAQ.

There, I found the thread "How do I get Ubuntu working on an iMac G3?".

I followed the directions and now Ubuntu is alive and working on my iMac DV. :)

---

### Post by grazie on 2007-10-05
It seems that while I've been away some folks have been doing a lot of work. I hope to add to the updated wiki myself. WELL DONE!

---

### Post by Tommy on 2007-10-26
I just found the FAQ on the wiki and it looks great! [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

It doesn't yet have any of the more recent Gutsy issues, but maybe until those get nailed down the FAQ could point to the relevant threads here at ubuntuforums.

---

### Post by MirandaSoft on 2007-11-05
[CENTER]***Hello to ALL Linux PowerPC Users, worldwide!***[/CENTER]

Since Canonical Ltd. had dropped support of the PowerPC processor, I wondered about having my business (MirandaSoft.net) heighten support for where others have left off. I've tried Fedora 7 on my Apple iBook G4 but there are too many quirks, and I have always had problems with Fedora since it's first release.

Well, in April 2006, I dropped all dependencies to Microsoft-based software, and migrated to GNU Linux and Apple Mac OS X. Then, in August 2006, I chose to accept Ubuntu Linux as MirandaSoft's preferrred Linux operating system. Months later, I was shocked to hear that Canonical Ltd put the Ubuntu Linux PowerPC code to the community, similar to what Red Hat did.

New Users to Ubuntu Linux or ANY Linux Disto: The road is a very rough road, shifting from Microsoft Windows to Linux, and never going back. Once you make the switch, you will wonder why you became a victim to the monopoly.

I use an Apple iBook G4 1.33GHz, 1.5GB RAM, and 80GB Hard Drive. 60GB is configured for Apple Mac OS X 10.4.10. And 20GB is configured for Ubuntu Linux 7.10 PowerPC.

My business website has the [MirandaSoft Report]("http://www.MirandaSoft.net/wordpress"), which has support for Ubuntu PowerPC, based on the experimentations I'm doing, in hopes to migrate back to Ubuntu Linux.

The PowerPC FAQ is very good and informative. Power Users will want to bookmark this link:
[http://packages.ubuntu.com/gutsy/allpackages]("http://packages.ubuntu.com/gutsy/allpackages")

Many people have E-Mailed me their interest in me keeping support for PowerPC Linux, but those emails are not from Philippines. I hate being the only one in Philippines that is Running Ubuntu Linux on an iBook G4.

I did the migration from a clean 7.04 installation to a network upgrade to 7.10. It is documented in the MirandaSoft report.

---

### Post by ssam on 2007-11-06
> **MirandaSoft said:**
> [CENTER]***Hello to ALL Linux PowerPC Users, worldwide!***[/CENTER]

Since Canonical Ltd. had dropped support of the PowerPC processor, I wondered about having my business (MirandaSoft.net) heighten support for where others have left off. I've tried Fedora 7 on my Apple iBook G4 but there are too many quirks, and I have always had problems with Fedora since it's first release.

Well, in April 2006, I dropped all dependencies to Microsoft-based software, and migrated to GNU Linux and Apple Mac OS X. Then, in August 2006, I chose to accept Ubuntu Linux as MirandaSoft's preferrred Linux operating system. Months later, I was shocked to hear that Canonical Ltd put the Ubuntu Linux PowerPC code to the community, similar to what Red Hat did.

New Users to Ubuntu Linux or ANY Linux Disto: The road is a very rough road, shifting from Microsoft Windows to Linux, and never going back. Once you make the switch, you will wonder why you became a victim to the monopoly.

I use an Apple iBook G4 1.33GHz, 1.5GB RAM, and 80GB Hard Drive. 60GB is configured for Apple Mac OS X 10.4.10. And 20GB is configured for Ubuntu Linux 7.10 PowerPC.

My business website has the [MirandaSoft Report]("http://www.MirandaSoft.net/wordpress"), which has support for Ubuntu PowerPC, based on the experimentations I'm doing, in hopes to migrate back to Ubuntu Linux.

The PowerPC FAQ is very good and informative. Power Users will want to bookmark this link:
[http://packages.ubuntu.com/gutsy/allpackages]("http://packages.ubuntu.com/gutsy/allpackages")

Many people have E-Mailed me their interest in me keeping support for PowerPC Linux, but those emails are not from Philippines. I hate being the only one in Philippines that is Running Ubuntu Linux on an iBook G4.

I did the migration from a clean 7.04 installation to a network upgrade to 7.10. It is documented in the MirandaSoft report.

get yourself added to [http://www.ubuntu.com/support/commercial/marketplace](http://www.ubuntu.com/support/commercial/marketplace)

what ubuntu on powerpc really needs is a developer. there are a small number of anoying bugs in ubntu powerpc, but there is noone with the time and skill to fix them.

---

### Post by MirandaSoft on 2007-11-06
Thanks for the info ssam.

I have all of my favorite developer installed into my installation of Ubuntu Gutsy PPC, however, I'm spending the day in completing the Ubuntu PowerPC FAQ and tweaking my installation to my standard.

So far, there's been a few quirks I've discovered. One being Ubuntu won't let more than one Palm device to be sync'd. It might be a simple technical error as my two USB-driven Palm devices are going through two USB 2.0 HUBs. Running dmesg shows errors when trying to get a different Palm device sync'd.

Back to developing... I used to make Linux software... But I've ran out of ideas about what to make. I've already seen that Linux PPC software is in demand. However, my next plan is focused into tweaking the Linux kernel to my iBook G4. I plan to compile a kernel, but that will be later on this week.

Primarily, I'll be focusing on QEMU this week. My Palm OS development software runs in Windows (98) and I've only made a Q version that runs in Mac OS X 10.4.10, but it runs very poorly.

Secondarily, I plan to reconfigure MOL (Mac on Linux) to run Mac OS X partition. First attempts to get MOL to run had failed.

Immediate reports are being filed onto The MirandaSoft Report. Bug reports will be soon reported under Launchpad. Most of my work is privatized. However, I'm targeting in going back to Linux, permanently.

Compiz crashed, or failed to run, per the PPC FAQs. Had to do some minor tweaking to xorg.conf to make it work. Beryl does not seem to work as it did in Feisty.

Note: my Gutsy installation was a Fresh Feisty installation, dist-upgraded, and then, upgraded to Gutsy. It took four hours for the entire process.

Note about Gnash: Yahoo Messenger online in Yahoo Enhanced Mail website will not function. Yahoo reports Adobe Flash 9.0 or higher is needed.

---

