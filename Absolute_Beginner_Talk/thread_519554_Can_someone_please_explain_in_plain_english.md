---
title: "Can someone please explain in plain english?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-08-07
Hi all.
I know Linux is a better OS than M$ Window$ and all. I know it's more stable. I use Ubuntu Feisty but I also have a windows box for the use of programs that unfortunately I cannot install under my Linux box.

This winXP PC I'm using keeps freezing slowing down etc etc. All the common problems win systems have that we all are used to.

I was just wondering if someone here could just tell me in a few plain words why is this happening. Is it because M$ software is so badly coded? Is it more than just the way the code is written? Is it because it was initially a badly written OS and it just evolved to this pathetic winVista?

What is the major difference in the way the system works between windows and Linux? What is it that makes Linux so much more stable?

In plain English if someone could explain the way these systems work.

Sorry if this is a stupid question....

---

### Post by tdrusk on 2007-08-07
It is probably due to one thing rather than a bunch of them. It probably has very little to do with the OS.

clean it up
clean the registry
defrag 20+ times
start>run>"msconfig" and delete processes you don't need.
reboot

linux manages processes better. Windows just builds up and builds up, as linux recycles I s'pose. This results in NEVER having to shut down the system. It also does not have (m)any viruses so it is safe. Also everybody can look at what makes the system, so that leads to people finding problems and fixing them, making it super stable.


Hope that helped.
:guitar:

P.S. The only stupid people are the people who DON'T ask questions.

---

### Post by xpod on 2007-08-07
I`ve seen many people recommend that XP actually *needs* re-installed every now and again due to the short "shelf life" it supposedly has.....then again i`ve seen others say they`ve run the same XP install for years without problems(that they know about):)

If your XP is not running within reason though then it quite possibly just needs a wee bit tender loving care...if not that complete re-installation of course:)  

I`ll leave the rest to someone who knows what their talking about.

Good luck either way

EDIT: > 
EDIT[QUOTEP.S. The only stupid people are the people who DON'T ask questions.][/QUOTE]

And of course,  the there is no such thing as a stupid question here at UF.

---

### Post by edonia on 2007-08-07
> **ROUBOS said:**
> 
I was just wondering if someone here could just tell me in a few plain words why is this happening. Is it because M$ software is so badly coded? Is it more than just the way the code is written? Is it because it was initially a badly written OS and it just evolved to this pathetic winVista?


One of the main reasons are the "dll" (Dynamic Link Library) system. The windows box is closed for some reasons and they need to hide it. So you need for your applications some interfaces to use the System and here are many issues for the bad behavior.

---

### Post by dca on 2007-08-07
I've gotten pretty use to re-imaging HDD(s) in a corporate environment every six mos to a year.  Not only is that the probability of malware installation but every single bit of software (apps) you install on your Windows system has the potential to slow it down.  Not only because of it embedding in your start-up directory or the start-up/run-once key of the registry but also because of it filling up the registry w/ add'l keys/locations of nec data files for the app.  Not clearing the temp directories in your profile and not frequently defragging the file system also can slow the system.  Not getting too ridiculous in your pagefile size (virt mem, swap equiv) also plays a part...

---

### Post by tdrusk on 2007-08-07
Also Linux is safer because all of your core stuff that a virus would try to take out is password protected, meaning you would have to tell the virus your password before it could do any harm at all.

---

### Post by xpod on 2007-08-07
> Not getting too ridiculous in your pagefile size (virt mem, swap equiv) also plays a part...

How about just using the Classic theme?.......thats an old favorite too it seems:lolflag:

---

### Post by vincentvee on 2007-08-07
i don't know what it is that causes it, windows runs good as a fresh install but it degenerates from there, and i always had a feeling it had something to do with how files are stored on the system and the fact that the filesystem needs defragmenting all the time, which as far as i know, linux has no need for(someone correct me if i am wrong there), but once my old windows pc started to run slow, i found that defrag would give it a bit of a boost, i used to re-install windows XP about once a month, which would keep it running smoother than most, the best way to do it is with an imaging program and take a disk image of the complete system after install and config, then install from this disk image when it needs doing.......i'm told disk imaging has come a long way since then, i wouldn't know since i don't use windows at all anymore.

> **ROUBOS said:**
> Hi all.
I know Linux is a better OS than M$ Window$ and all. I know it's more stable. I use Ubuntu Feisty but I also have a windows box for the use of programs that unfortunately I cannot install under my Linux box.

This winXP PC I'm using keeps freezing slowing down etc etc. All the common problems win systems have that we all are used to.

I was just wondering if someone here could just tell me in a few plain words why is this happening. Is it because M$ software is so badly coded? Is it more than just the way the code is written? Is it because it was initially a badly written OS and it just evolved to this pathetic winVista?

What is the major difference in the way the system works between windows and Linux? What is it that makes Linux so much more stable?

In plain English if someone could explain the way these systems work.

Sorry if this is a stupid question....

---

### Post by stinger30au on 2007-08-07
microsoft has a "closed source". this means only the programmers at microsoft can look at and edit the code that goes together to make the either o/s run.

Linux has "open source" so anybody can look at the source and add/change at their will.

As linux is open source, there is a few million eyes looking at the source.
M/S has only a few thousand looking at the source.

Linux can get patches out in a few days of anyone finding a error in it that will be a potinetial security risk.
M/S can take weeks/months for a patch to come out.


When Linux writes data to a disk it does it in a logical and orderly fashion, hence there is no hard drive defragment program required as the o/s looks after itself.

M/S on the other hand when it saves anything to disk, it just shoves the data all over the hard drive in pretty much no order or sequence and basically does not give a hoot where the data gets saved.hence the need for disc defragmenters in M/S O/S

Linux was built from the ground up with security in mind...
Microsoft O/S does not care about security, in their eyes, it is somebody elses problem...  YOURS!

---

### Post by armandh on 2007-08-07
cloged with app crap running in the background.
layers of AV and firewall sucking capacity
you would be supprised how fast xp-1 boots and runs on an old 500 P-III
[until it is infected]

---

### Post by ROUBOS on 2007-08-07
OK,
so M$ use the Registry. Which is a database that holds settings and options for the OS (for Hardware and software) and all the software installed. 

and the DLL is a shared library for all the software installed. 

Now this Registry database grows as we install software and can slow the machine down. The DLL shared library also gets updated and with installing and uninstalling programs it makes a mess of things causing the OS to slow down or even stuff up. 

Also necessary is the defraq so that the data is accessed faster and better off the HDD.

OK so window$ is not good enough to handle the Registry and DLL files properly causing all these issues. 

Is this the main structure of the M$ OS? How does that differ from the LINUX more stable OS.

I noticed with Linux by installing NeverWinterNights on my Ubuntu box, that what was just needed was to copy files onto a single folder and running the game. Deleting the folder uninstalled the game. 
So in Linux programs work autonomous? Is this why there is no need for all those "restarts" ??

So in window$ programs need access to the core of the OS (Registry and DLL) to work and that also causes problems with viruses. Whereas LINUX works differently?

---

### Post by ROUBOS on 2007-08-07
> **stinger30au said:**
> microsoft has a "closed source". this means only the programmers at microsoft can look at and edit the code that goes together to make the either o/s run.

Linux has "open source" so anybody can look at the source and add/change at their will.

As linux is open source, there is a few million eyes looking at the source.
M/S has only a few thousand looking at the source.

Linux can get patches out in a few days of anyone finding a error in it that will be a potinetial security risk.
M/S can take weeks/months for a patch to come out.


When Linux writes data to a disk it does it in a logical and orderly fashion, hence there is no hard drive defragment program required as the o/s looks after itself.

M/S on the other hand when it saves anything to disk, it just shoves the data all over the hard drive in pretty much no order or sequence and basically does not give a hoot where the data gets saved.hence the need for disc defragmenters in M/S O/S

Linux was built from the ground up with security in mind...
Microsoft O/S does not care about security, in their eyes, it is somebody elses problem...  YOURS!

Cool answer. That's what I'm talking about.

---

### Post by Jeek Elemental on 2007-08-07
well the long term cause Id say is the api-of-the-week mentality of m$, if their current toy doesnt catch on they drop it, while still needing to keep it around for the programs that use it.

that said, I dont think windows as a whole is bad, some parts of it drag the rest down and your experience is coloured by which parts you spend your time in :)

I ran win2k pro for about 5 (heavy use) years without reinstalling, to keep it humming does take alot of work and vigilance from the user tho.

disable all services you dont need, there are lots of guides available on how to trim the system.
get a good antivirus program (I recommend Avast, free for personal use). Realize tho that even the best antivirus is always a step behind.

know which processes normally run on your system, and work to keep this a short list. If something seems amiss, your first action is to check for any new processes, and identify it (google usually enough).

also keep an eye on key registry ..keys :) like auto-startup, it seems every program wants to put some crud there. I remember one of the last audio drivers I installed put 3 (!) programs there, totalling some 40MB memory use, and totally useless.

In the end it comes down to whether youre willing to do all this and keep adding to what is basically worthless knowledge, or switch to something else.

---

### Post by mike102282 on 2007-08-07
> **Jeek Elemental said:**
> well the long term cause Id say is the api-of-the-week mentality of m$, if their current toy doesnt catch on they drop it, while still needing to keep it around for the programs that use it.

that said, I dont think windows as a whole is bad, some parts of it drag the rest down and your experience is coloured by which parts you spend your time in :)

I ran win2k pro for about 5 (heavy use) years without reinstalling, to keep it humming does take alot of work and vigilance from the user tho.

disable all services you dont need, there are lots of guides available on how to trim the system.
get a good antivirus program (I recommend Avast, free for personal use). Realize tho that even the best antivirus is always a step behind.

know which processes normally run on your system, and work to keep this a short list. If something seems amiss, your first action is to check for any new processes, and identify it (google usually enough).

also keep an eye on key registry ..keys :) like auto-startup, it seems every program wants to put some crud there. I remember one of the last audio drivers I installed put 3 (!) programs there, totalling some 40MB memory use, and totally useless.

In the end it comes down to whether youre willing to do all this and keep adding to what is basically worthless knowledge, or switch to something else.

Thats it there aren't alot of people who want to go through all that effort and personally I don't think they should have to. That is one of the many reasons i left MS for linux.

---

### Post by ROUBOS on 2007-08-07
Well at the moment I only have firefox running and there are 53 Processes listed in the Windows Task Manager :(

Obviously not so many are needed but I do need to know what's not required. Then again CPU usage is 2%. System Idle Process is showing CPU 99

PF Usage is 445MB 

Anyway M$ OS does not take care of itself and that's causing alot of problems to normal (simple) users who just install software and expect the system run smoothly.

Is MacOS on the same boat?

---

### Post by Circus-Killer on 2007-08-07
aside from reasons already mentioned, i think another problem is that there is not one person up in microsoft that knows what windows "looks" like. what do i mean by this? well, every project i have ever worked on, no matter how small a part i was contributing in, i new the whole layout of the system in my head. however, at microsoft, what a programmer works on is all he sees, with no real idea of what the rest of the system is about.

this lack of structure obviously has repercussions, such as trying to make a hundred different parts seemingly work together. but even open source programmers suffer this challenge, the difference is that open source programmers can always look at the code of whatever they need to interact with, whereas windows programmers have to use restricted APIs that dont give enough insite to the programmer to program efficiently or even properly.

this is just my opinion, but this is one of the biggest problems with closed source programming, especially when source is closed to your own devs. why do MS do this? well, simply so that no one person will have complete "control" or whatever. but yah, thats my thoughts on why windows sucks. :P

---

### Post by nowhere.elysium on 2007-08-07
Windows isn't an intrinsically bad OS, per se: it's just become the lowest common denominator: basically, because everyone uses it, it has to be usable by everyone, see?
The fact that it's a black-box style OS doesn't curry any favour with the Linux Corps, certainly, and this I fully appreciate, but its main weakness is its security model (or relative lack thereof).
Because there's no solid authentication method for installing software, new processes can set themselves up as administrator-level processes: much like letting everything run as root. This gives it complete control over all areas of the computer, and causes myriad problems.

The previous coment about Windows boxes slowing down really soon after building: well, that's fixable. Once a machine has been built (including drivers, that is), the first things I do are:
Set the page file size to max out at 1.5 times the RAM
Install EasyCleaner (marvellous piece of software)
Install Kerio PF 2.1.5 - the last free version of the firewall
Install AVG Free
Then I lecture the user-to-be on the dangers of Emule, LimeWire etc, etc - tell them that BitTorrent is the only relatively safe method of file sharing, and that those free CDs that you get really aren't as cool as all that.
This method does mean that you get several questions for a while afterwards, but it also heightens user awareness, which is always good, and more oftenthan not, they ask what it is that's running on my laptop(s)/desktop(s), and how they can make theirs look like that. Cue one more victory for Linux...

---

### Post by nowhere.elysium on 2007-08-07
> **ROUBOS said:**
> 
Is MacOS on the same boat?

Not quite. It's more hassle to install stuff in MacOS, and you've got to ahve administrator privileges. It's easier to break the access priviliges than it is in Linux, but not by much. Unfortunately, I encounter a lot of problems with MacOS's user's attitude, than I do with Windows. At least with Windows, they're aware of viruses, which although they're not strictly an applicable problem with MacOS, there's no awareness of security or safe behaviour. The current line of MacOS adverts do nothing to sway this saddening trend. The one where they mock Vista's UAC system is just shameful: yes, Vista's method is crap, but at least there's some form of enforced awareness in place. 

For the record, I fix Macs for a living, and fix PCs for extra drinking money.

---

### Post by ROUBOS on 2007-08-07
Thanks people. This has turned out into a nice discussion and the responses I got are very informative and useful.
I got a lot out of this thread. Thanks again :)

---

### Post by Paulmd on 2007-08-07
> **ROUBOS said:**
> Hi all.
I know Linux is a better OS than M$ Window$ and all. I know it's more stable. I use Ubuntu Feisty but I also have a windows box for the use of programs that unfortunately I cannot install under my Linux box.

This winXP PC I'm using keeps freezing slowing down etc etc. All the common problems win systems have that we all are used to.

I was just wondering if someone here could just tell me in a few plain words why is this happening. Is it because M$ software is so badly coded? Is it more than just the way the code is written? Is it because it was initially a badly written OS and it just evolved to this pathetic winVista?

What is the major difference in the way the system works between windows and Linux? What is it that makes Linux so much more stable?

In plain English if someone could explain the way these systems work.

Sorry if this is a stupid question....

There are also hardware reasons for this behavior. The top one is Capacitor Plague.  Open it up, look at the capacitors (they look like little soda cans) if any are bulging or leaking (even a little) they're bad. Also, check that the fans are working, and blow out the dust. A system that overheats will not be stable.    The other major random-freeze causer is a bad video card.

---

### Post by sailor2001 on 2007-08-07
you could: run/msconfig/start and untick all the extra garbage that is clogging up your drive...
black viper had a tutorial on that.  google!

---

### Post by lisati on 2007-08-07
> **nowhere.elysium said:**
> 
Then I lecture the user-to-be on the dangers of Emule, LimeWire etc, etc - tell them that BitTorrent is the only relatively safe method of file sharing, and that those free CDs that you get really aren't as cool as all that.


... with the possible exception of some CDs and DVDs I recently saw bundled with some mags in one of  my local bookshops which had Ubuntu 7.04 on them.....

Having said that, there is no substitute for keeping a clear head and being wise, which doesn't always come easy. Keep on smiling.

---

