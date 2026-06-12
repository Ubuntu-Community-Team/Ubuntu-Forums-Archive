---
title: "Linux on an old compaq: time to get my hands dirty"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by MikeMLP on 2006-08-19
Greetings:
after being very impressed with ubuntu on my laptop, and using for about 3 months, I've decided to install linux on an old compaq to use as a backup in case my laptop has a problem (which did occur last year, but that is OT and another story...)  My question is, given the specs (which are posted below), and what I want it to do for me (also posted below) can you give me some suggestions for the proper linux distribution to use that will...

1. be fastest on this old machine
2. be easiest to setup and maintain, and most like ubuntu (preferably debian-based, and having good community support, especially for initial set-up)
3. hopefully having some sort of live disc so I can test hardware interoporability

Now on to the specs:

Compaq Presario 5140 (circa 1997)

P II 266
768 MB of PC133 SDRAM
6GB HD ATA 66
4MB ATI Rage 128 Pro integrated AGP 2x graphics
2X DVD-Rom
Standard 10/100 Ethernet card / 56K Modem
FX 500 15-in monitor 1024x768 max res, monitor-integrated speakers, and monitor-integrated usb hub

And what I want to do with it:
**Run openoffice** - this is required, as all my school documents will be .odt from now on, and I will need to be able to (semi) read .doc documents as well
**Run firefox** -another must-have for me...
Run an **IM client** like GAIM
have access to quick and easy access to security and program updates through the use of an easy package manager, **like Synaptic**

I have about a week to complete this project, and since this is *really* a test box, I have considered getting my hands dirty and trying something ultra-customizable like **Gentoo** or **building my own distribution** based on my requirements (I would prefer, of course for there to be a nicely maintained distribution out there that I could just grab)

Since, aside from the CPU speed, this machine is pretty beefy for its time, I am also considering trying Xubuntu on for size (I know a lot of you will probably argue that even Xfce is too resource-intensive, but I'd be willing to give it a shot, I've seen this machine perform above expectations in the past)  

Please let me know if you have any suggestions, especially of certian distros that I may not have heard of before, or of links to guides, and so forth... As I said, this machine is pretty much mine to screw around with, so throw out any and all ideas and links to related materials.  I'm ready, willing, and wanting to get my hands dirty on this project.

---

### Post by aysiu on 2006-08-19
You have plenty of RAM, but for a 6 GB hard drive, I would recommend Xubuntu.

---

### Post by xmastree on 2006-08-19
Much as I hate to say it, I wouldn't advise ubuntu.
I have a Toshiba P233 laptop, and I tried Ubuntu but it was too slow. I eventually settled on [Puppy linux]("http://www.puppylinux.org/user/index.php") having also tried [damn small]("http://www.damnsmalllinux.org/") and [feather]("http://featherlinux.berlios.de/").
You can read a sort of review of the four I tried [here](http://www.openlaptops.org/index.php/topic,145.msg833.html#msg833)

All have live CDs to try first.

---

### Post by aysiu on 2006-08-19
That Toshiba laptop had 96 MB of RAM... as opposed to 768 MB of RAM.

Big difference.

---

### Post by DirtDawg on 2006-08-19
> **aysiu said:**
> You have plenty of RAM, but for a 6 GB hard drive, I would recommend Xubuntu.

I would also reccomend Xubuntu. I think you'll find it's exactly what you're looking for.

Xubuntu doesn't come with OpenOffice, but it does come with Abiword which may suit your needs. Of course, you can always install OpenOffice if it doesn't.

There's also plenty of room for customization with Xubuntu.

---

### Post by xmastree on 2006-08-19
> **aysiu said:**
> That Toshiba laptop had 96 MB of RAM... as opposed to 768 MB of RAM.

Big difference.
True...
I'm limited to a maximim of 160MB, :(  if I can find a 128 EDO SoDIMM anywhere. ](*,)

---

### Post by MikeMLP on 2006-08-19
I've decided to start with what I know best and go for Xubuntu, but since I burned my iso in windows last time, I need to know where to get a good md5 checksum program that can do iso files within linux, and I need to know if there is anything I need to do to get my laptop to burn the iso to a disc within linux (since last time I did that in windows as well). (I did use the automatix script, I am not sure if that enables cd-burning)  I would apreciate a few words per these to items please.

---

### Post by aysiu on 2006-08-19
[http://ubuntuguide.org/wiki/Dapper#How_to_check_MD5_checksum_of_files](http://ubuntuguide.org/wiki/Dapper#How_to_check_MD5_checksum_of_files)

---

### Post by MikeMLP on 2006-08-19
ok, I'm working my way towards installation (backing up the few remaining files that are of any value to me, and then partitioning), but I would like to ask, given the specs (especially the video specs)  what kind of monitor resolution would you guess this thing could drive?  The current monitor is getting really out of whack (as on old CRT) and a shiny new LCD may be in its future.  The question is, should I go with a really nice one that I can later attach to a new pc when I am ready to trash this one, or do I go with a really cheap, low res one, that I wouldn't want to use with any other machine...  I'd apreciate any input from people who may have faced a similar situation.

---

### Post by MikeMLP on 2006-08-19
and another question: this one regarding cmos batteries.  Have any of you ever had any success in making your own replacement battery pack?  This machine had a soldered on battery, and ports for a replacement battery.  I've tried a replacement battery, but it doesn't seem to work, probably because the replacement is as old as the original.  It seems silly to trash the machine when all it needs is a new cmos battery...  I'm wondering if there is a reliable source for new replacement batteries, or a nice howto on building your own battery pack somewhere on the net.  This is quite obscure, I know, but if anyone has run into anything like this I'd apreciate a post, thanks!

---

### Post by insane_alien on 2006-08-19
you should be able to pick up a replacement battery at an electronics store (its radio shack in the US isn't it?) if the replacement port doesn't work then you could desolder the origional battery and solder a new battery in there. that could work.

---

### Post by MikeMLP on 2006-08-19
Given what I said in the first post about my usage needs, and the fact that any documents created will likely be saved almost immediately to USB flash disk, what do you think would be a good partition size for the root and home partitons?  HD is 6.06 GB, I'm going to start by trying Xubuntu...

---

### Post by MikeMLP on 2006-08-19
Finally, another question: this machine could be qualified as *extremely proprietary* in that the monitor had no built in osd to change geometry settings, instead, it relied on a driver.  There was a button that you would press on the monitor itself that would send a signal via usb to open a control panel within Windows 95 (yes, that is what it shipped with, but now I am erasing a win2k install).  From that control panel, you could adjust monitor geomoetry settings like size and position, etc... Now as you might expect, once win2k was installed, this utility was gone and lost forever, and as a result, by default, this monitor leaves about half an inch of blank space on the left side of the screen, while pushing about half an inch of desktop off on the right.  Sux bigtime, huh?

What I am wondering is if there is some sort of linux-based package that I can download that would be able to change the geometry of the monitor, like the old utility used to do.  Again, very obscure, but hopefully you had, at least, an interesting read as to why people should NEVER go proprietary when they have the option, and how lock-in is just as much of a problem on hardware, as it is on software.  If anyone can dig up links to a utility that might do what I'm looking for, I'd be a very happy man!

---

### Post by keri_ubu on 2006-08-19
I can really recommend trying Puppy, it runs as a live CD so you can try to see it works before you install on HD
it is very easy to install, very fast (... and very different)

---

### Post by MikeMLP on 2006-08-19
ok, I got it up and running with Xubuntu, and performance is passable.  I have a really strange problem though:  When I open up firefox and do a search in the search box, as soon as I hit enter, the machine freezes.  So far, I've reproduced it three times.  The first time it happened immediately and the computer automatically rebooted.  The second time, the screen went black and it froze, requiring a manual reboot.  The third time, the screen went black and then the CPU speaker beeped several times, also resulting in a manual boot.  I have tried reinstalling firefox from the repos (rather than from the CD, as it came preinstalled,) and it made no difference.  Can anyone recommend an alternate browser to try, preferably something non mozilla-based?  I really have no idea why this is happening.  Every other program that I've used so far has worked flawlessly.  I've even installed openoffice, and used it a bit.  I'm really throwing my hands up in the air on this one.

Thanks!

---

### Post by MikeMLP on 2006-08-19
ok, this is getting weirder by the minute.  I installed lynx to be sure that this system could handle the load, and I did a search for firefox... no problem.  I was hoping to download and install the latest version, thinking that that would solve the issue.  I scrolled through the links and highlighted the pertinent one, hit enter and....

you guessed it, the machine immediately halted and the restarted itself (at least I wasn't bothered with having to touch the power button myself this time ; |.  So now, I am beginning to wonder if there is a core piece of software that was installed wrong, or has some bug that no one is aware of.  What is it that allows a linux system to  "click a link" regardless of the browser?  I md5 checked my CD, and I did the CD check (I used the alternate install disc for xubuntu) and both passed.  The md5 was right, and the CD check was fine as well.  I really have no idea what the problem could be, at this point, I feel like I've run into something I can't conquer.  I really need some compu-help....

update: it seems that it takes a certain amount of time... After any web browser is opened, it takes between 15 seconds and 90 seconds for the machine to automatically reboot.  Perhaps there is a list of networking modules I can reinstall... or something...

update: I was able to open the browser, and let the machine sit for a while, with no problem.  I then did a search, and let it sit, no problem.  Then, I clicked a link, and no problem.  and another one, no problem... things were looking good... but alas, a couple minutes later, the system rebooted itself.  It now seems that the problem is correlated to the frequency of searches / clicks in a web app.  This makes little sense, as the system is getting its time updated, and is using the weather applet that comes with Xfce.

upate: on boot, I get (and have always gotten: ACPI : Unable to locate RSDP, however since the machine boots anyway and I've had other error messages on my laptop that don't result in crahses, I never thought anything of it.  Now I must wonder if this has anything to do with my browser problem.  As long as I don't touch a browser of any kind, this machine seems to be very stable.

---

### Post by xmastree on 2006-08-20
Try running memtest from the grub boot menu.

---

### Post by MikeMLP on 2006-08-20
yes, I started that... memory was the first thing that crossed my mind, since bad memory is great at causing random reboots.  it'll probably take about 10 hours to get through all of the tests.  I decided, instead, to quit after the first one finished (with no errors) and install vanilla ubuntu, gnome and all, since I know that worked on my laptop without a problem.  If the lockups and reboots were more random, I'd think more of a memory problem, but I could have left the thing up for hours, and done anything on it except access the web.  In any case, if I still run into the same  problem after installing regular ubuntu, the first thing I'll do is complete memtest.  I also noticed that the version of memtest on the recovery disc is 1.65, but the current version is 3.1 or so... I'm wondering why this is, and if it would be a good idea for me to try getting the latest version on a floppy or something...

Thanks for the tip, and I'll let the thread know what happens.

---

### Post by MikeMLP on 2006-08-21
I ran a memtest x86+ from the livecd (to be sure the one on the HD was not corrupted in any way, and after running for over 27 hours, and going through 15 passes, it found zero errors.  I'll let it go longer, but, I doubt it will detect anything.

so... this leaves me baffled... what could it be? some kernel bug that only affects certain hardware? a bug somewhere within the networking subsystem?  I think my next step is to start trying different distros.  Because in the mean time, I installed ubuntu 6.06 on the old compaq, using the same cd that I used to install onto my laptop, with which I am writing out this message, and I experienced the exact same issue as I did with my newly-burned xubuntu disc.  

No memtest errors, and a well-behaving copy of windows 2000 running on the very same machine, just a few days ago brings me to one conclusion: software bug.  what else could it be?

---

### Post by MikeMLP on 2006-08-21
Perhaps I spoke a bit too soon:  let me sum up what has happened up until now, so new viewers of this topic won't have to go digging back a few pages:

1. thought I could resurrect an old W2k machine with linux
2. installed xubuntu just fine, was able to install openoffice through synaptic without trouble, but experieneced a nearly immediate **crash,** just seconds after opening and using a browser, sometimes accompanied by an **automatic reboot**, sometimes accompanied only by a **serries of beeps** from the pc speaker, and sometimes **completely silent**, and not autorebooting.
3. installed alternate browsers, such as seamonkey and lynx.  Problem reproduced on all alternate browsers
4. installed/used alternate distributions, including non-ubuntu-based puppy linux, problem reproduced on all distributions.
5. ran 27+hour memtest x86+, found no errors

which leads me back to thinking about the network card... with one caveat:  IF it is the network card, then **why** was I able to download and install alternative browsers / openoffice through synaptic?

To reconcile this fact, I really need to know more about the way linux handles faulty hardware.  Are there ways to test something like a faulty NIC, like a package I could download and run?  is webbrowsing handled differently than a simple synaptic download at the hw<>software level?  Is there a specific place where I can go to see the logs of events directly before the last crash?

Anyone with any sort of opinion or potentially helpful information is urged to respond.
Thanks.

---

### Post by xmastree on 2006-08-22
> **MikeMLP said:**
>  IF it is the network card, then **why** was I able to download and install alternative browsers / openoffice through synaptic?

Different protcol? I've had NICs which under windows would ping websites, connect to IM services, but couldn't browse the web.

---

### Post by MikeMLP on 2006-08-22
possibly...  But then, again, there is the question of hardware or software...  could a breakdown in hardware only mess up one protocol?  It just doesn't seem possible to me.  Driver issue?  How do I troubleshoot something like this if all indications are that everything is working properly (except, of course, for the crash itself).

All I can think of is of putting in a new card when I get a chance and seeing what happens.  Again, if anyone can think of some other software angles that might give me some indication of a problem with hardware or software, please mention it.

---

### Post by MikeMLP on 2007-05-25
Ok, dragging up a very old thread here, but I think I may have found a couple of answers.

I don't know how important it is to have the system clock functioning normally, but on this old heap, it doesn't.  I've been trying to find a replacement part (it has to be a battery pack, since the original watch-battery was soldered in, but no luck yet.  I've noticed that on the web, the machine tends to reboot on its own just after dismissing a firefox window explaining that the system time and the time for a web security certificate are very different from each other.

The crashes seem to happen in other situations too, but it seems as though in the above situation - the security certificate - the crash is certain.

I've got a feeling that this crash occurs because of something in the kernel not liking the discrepancy.  Interesting, anyway, for those of you who put some thought into this thread a while back.

---

### Post by irish_flu on 2007-05-25
> **MikeMLP said:**
> 
I've got a feeling that this crash occurs because of something in the kernel not liking the discrepancy.  Interesting, anyway, for those of you who put some thought into this thread a while back.

Oh man, I'm with you on that.  I have an old tablet PC running Windows 2000. The CMOS battery is cooked, but it's no big deal *as long as I don't competely discharge the main battery* hehe.

Anyway, so when I first got it I fired it up, ran a "service pack" install, and promptly drained the battery.  when it came back up, the system time was before the service pack had been created and that made Windows ANGRY. :D

---

### Post by MikeMLP on 2007-05-25
It is funny though, how this Compaq, which was running win2k on a "cooked" cmos battery without any similar issue (eg - random restarts) has such issues with Linux.  Then again, I didn't try to install win2k with a cooked battery - it was installed and updated (service pack wise) long before the battery decided to stop working.  Interesting that major troubles related to the cmos battery could happen on Windows too though...

---

### Post by Shazaam on 2007-05-25
xmastree...
Try this site for memory etc-- [http://www.kahlon.com/](http://www.kahlon.com/)

---

### Post by irish_flu on 2007-05-25
> **MikeMLP said:**
>  Interesting that major troubles related to the cmos battery could happen on Windows too though...

Time is pretty important to any OS.  If I said "OK I have to go to the Dentist next Tuesday" then the next time I check my schedule it was 1977 and my dentist appointment wasn't for thirty years, it might freak me out too! :p

---

