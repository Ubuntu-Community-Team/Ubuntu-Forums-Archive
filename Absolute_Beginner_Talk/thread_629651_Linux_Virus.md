---
title: "Linux Virus?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Apotheosis on 2007-12-02
I know there is supposed to be no such thing as an virus on a Linux machine, but lately my computer has been running like crap and that seems to be the only explanation.  Before this, I have ran Ubuntu for over a year and never had any of these problems.  Here is a short list of what is going on:

- Media, both on the internet and on my HD, will often pause and skip forward a few seconds while the sound goes nuts.
- Just five minutes ago I was browsing the internet and my computer randomly logged me out.
- Firefox will randomly freeze moderately often.
- Sometimes my touchpad refuses to work right and the cursor will jump all over the screen.
- Often my computer will run very sluggishly when I am not doing anything very taxing at all.

I think that is about it.  I will update it if I think of more things.

---

### Post by Dr Small on 2007-12-02
Your CPU going bad perhaps ?

---

### Post by quinnten83 on 2007-12-02
corrupted X perhaps?

---

### Post by Apotheosis on 2007-12-02
Sorry, but I am quite the novice when it comes to computer hardware and some software.

How could my CPU go bad and how can I tell if it is?  Also, what is an "X" and how can I tell if it is corrupted or not?

---

### Post by frank002 on 2007-12-02
Can't help with cpu but X is Ubuntu's graphical subsystem. I believe you can reconfigure it by opening a terminal window and typing dpkg- reconfigure xserver-xorg.

---

### Post by Apotheosis on 2007-12-02
When I typed that in I got this:

bash: dpkg-: command not found

---

### Post by eolson on 2007-12-02
Try
sudo dpkg- reconfigure xserver-xorg.

---

### Post by megamania on 2007-12-02
> **Apotheosis said:**
> 
- Media, both on the internet and on my HD, will often pause and skip forward a few seconds while the sound goes nuts.
- Just five minutes ago I was browsing the internet and my computer randomly logged me out.
- Firefox will randomly freeze moderately often.
- Sometimes my touchpad refuses to work right and the cursor will jump all over the screen.
- Often my computer will run very sluggishly when I am not doing anything very taxing at all.

As the other posters said, it sounds like hardware fault. 

I had a few of your problems (especially the first and last ones you mention) when my hard drive started breaking down.

---

### Post by irish_flu on 2007-12-02
I'm gonna come off as a jerk when I say this, but what made you decide those symptoms were indicative of a virus?  Nothing there seems like viral activity to me.

OK, jerk mode is now off.  :)

I see a few possible things here.  Maybe your Operating System is just "screwed up".  can you think of any changes you might have made (installed some new software, did a major upgrade, added or removed hardware, etc)  directly before this stuff started happening?

If you can think of anything like that, then there's where you should start.


Other than that, it could also be a few hardware-related issues, for instance:
- is your hard drive full, or does it make strange sounds?

- it could be getting pretty hot inside your machine, causing it to behave oddly.  Are any of your fans suddenly extra loud, or perhaps not working at all?

Is that a laptop?  If so, do you notice it seeming extra hot when you've used it for a bit?

These are just guesses, of course; sorry I'm not more helpful, friend.  Tell us as much as you can about the machine.  Anything physically odd you've noticed?  What are the system specs?

---

### Post by jordanmthomas on 2007-12-02
> **eolson said:**
> Try
sudo dpkg- reconfigure xserver-xorg.

you have an extraneous space
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by eolson on 2007-12-02
Could also be a memory problem.   Run memtest, thiink it's option 5 or 6 on the grub menu.

---

### Post by rainwalker on 2007-12-02
> **eolson said:**
> Try
sudo dpkg- reconfigure xserver-xorg.

If you do that, make sure you post ANY questions you have, because you'd be messing with your core graphics settings.

---

### Post by Wiebelhaus on 2007-12-02
Lol , Linux virus.....This is not windows , If your system is running slow it is with 100% certainty not a virus.

---

### Post by curty4christ on 2007-12-02
I hate to break it to yall but there is not a operating system that is fully immune to viruses. :)  Its just not possible.  So that very well could be a virus.

---

### Post by curty4christ on 2007-12-02
I hate to break it to yall but there is not a operating system that is fully immune to viruses:)  its just not possible.  So that very well could be a virus.

---

### Post by jordanmthomas on 2007-12-02
> **curty4christ said:**
> I hate to break it to yall but there is not a operating system that is fully immune to viruses:)  its just not possible.  So that very well could be a virus.

Thing is, viruses / trojans  / rootkits written for Linux do a very good job of hiding themselves.  Slowing down the computer is just asking to get caught.  So generally, if your computer is running slow you shouldn't be worried that it's a virus working.

---

### Post by fatality_uk on 2007-12-02
> **sx66gns said:**
> Lol , Linux virus.....This is not windows , If your system is running slow it is with 100% certainty not a virus.

There are, what are laughingly termed, "Proof Of Concept" viruses that HAVE been made for LINUX. While the nature of Linux lends itself to non-replication, there is nothing to say that a "real world" virus wont crop up one day.

---

### Post by maharbA on 2007-12-02
from what I've heard, Firefox can be unreliable in Linux. Supposedly Firefox 3 (granparadiso) will improve the situation, but it's only a beta right now.

You can be reasonably sure that Firefox's behavior is not caused by a virus. If it's bugging you, try using another browser (I've heard good things about Epiphany, and you could always try granparadiso)

---

### Post by Apotheosis on 2007-12-02
Megamania, what would cause a hard drive failure?  My laptop is only about two years old, and I take pretty good care of it, save forcing it to shut down by holding the power button a small handful of times.

Irish_flu, I equated those with a virus out of habit.  After using Winblows for years on end, I just came to accept that generally if one has those problems it is probably malware/ a virus.  Well I did upgrade to Gusty from Edgy recently, but I am pretty sure I was having these problems before then as well.  Other than that, I really haven't touched anything in quite some time.

Currently, I only have 10 out of 60 gigs left.  I was under the impression that that wasn't *too* full.  It does sound like my computer is eating my hardware when it acts sluggish when it shouldn't, which I mentioned earlier.  I think my fans are fine and I don't believe it gets too hot.

Oh and that reconfigure command I was told to run was a bad idea.  It kept asking me a lot of questions I didn't know the answers to and at one point it disabled the monitor when I selected the wrong command.

Edit to add*  Gah, I am a really slow typer.  These replies are to posts on the first page.  I will read some more and write another reply.  Thanks for all the help, guys!

---

### Post by spiderbatdad on 2007-12-02
```
sudo dpkg --reconfigure xserver-xorg
```

---

### Post by Dr Small on 2007-12-02
> **spiderbatdad said:**
> ```
sudo dpkg --reconfigure xserver-xorg
```
Correction:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by thelatinist on 2007-12-02
> **Apotheosis said:**
> Irish_flu, I equated those with a virus out of habit.  After using Winblows for years on end, I just came to accept that generally if one has those problems it is probably malware/ a virus.

It's hard to break out of those habits of thinking like a Windows user.  There are many things that could be causing your problems, but it is almost certain that a virus is not the cause.  10 GB free space should be plenty.  The most likely cause would seem to me to be problems with X, as others have said, especially if you upgraded.  You could try backing up your data and doing a fresh install of 7.10.

---

### Post by GSF1200S on 2007-12-02
I would reconfigure X as Dr. Small suggested.. seems like some weird X issues...

---

### Post by spiderbatdad on 2007-12-02
> **Dr Small said:**
> Correction:
```
sudo dpkg-reconfigure xserver-xorg
```


mmm...pardon me, please.:(

---

### Post by Dr Small on 2007-12-02
> **spiderbatdad said:**
> mmm...pardon me, please.:(
No harm done :) You are fine ;)

---

### Post by Apotheosis on 2007-12-02
So for the past two hours, I have been running memtest.  After two hours it hadn't found any errors, so I just stopped it. Perhaps I will give it another try when I go to bed.

As far a reconfiguring X, as I previously stated, it asked me a ton of questions I didn't know the answer to, so I would really rather not do that.  Any other suggestions?

---

### Post by Dapman01 on 2007-12-02
> **Apotheosis said:**
> Megamania, what would cause a hard drive failure?  My laptop is only about two years old, and I take pretty good care of it, save forcing it to shut down by holding the power button a small handful of times.

Irish_flu, I equated those with a virus out of habit.  After using Winblows for years on end, I just came to accept that generally if one has those problems it is probably malware/ a virus.  Well I did upgrade to Gusty from Edgy recently, but I am pretty sure I was having these problems before then as well.  Other than that, I really haven't touched anything in quite some time.

Currently, I only have 10 out of 60 gigs left.  I was under the impression that that wasn't *too* full.  It does sound like my computer is eating my hardware when it acts sluggish when it shouldn't, which I mentioned earlier.  I think my fans are fine and I don't believe it gets too hot.

Oh and that reconfigure command I was told to run was a bad idea.  It kept asking me a lot of questions I didn't know the answers to and at one point it disabled the monitor when I selected the wrong command.

Edit to add*  Gah, I am a really slow typer.  These replies are to posts on the first page.  I will read some more and write another reply.  Thanks for all the help, guys!

Did you upgrade it from Fiesty to Gutsy....that may be your problem.  From what I heard Ubuntu doesn't have the whole upgrade thing down just yet and it is recommended that you just start from scratch

---

### Post by monte48lowes on 2007-12-02
The easiest way to reconfigure X is written in xorg.conf:

```
cat /etc/X11/xorg.conf | grep dpkg
```

results in

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will ask fewer questions. 

Mike

---

### Post by st33med on 2007-12-02
Also, may I ask how much memory you have? And what is your swap? To find out, type:
```
free
```
In the terminal and post it here.

---

### Post by GSF1200S on 2007-12-02
> **monte48lowes said:**
> The easiest way to reconfigure X is written in xorg.conf:

```
cat /etc/X11/xorg.conf | grep dpkg
```

results in

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will ask fewer questions. 

Mike

Yeah, I can vouch for:

sudo dpkg-reconfigure -phigh xserver-xorg

It will ask you for what drivers you want (just go vesa for now), and what resolution your monitor is.

I used to use this whenever a kernel update or xorg update came out while I was beta testing Feisty, as x would crash until I reinstalled the nvidia drivers from the command line...

---

### Post by baxterdog on 2007-12-02
To add my two cents:

It is very possible that it is a hardware failure. My W**** box that had RAID0 was acting up a few weeks ago, not recognizing the DVD drive as DVD, just CD. Couldn't read/write correctly.

Did everything; reinstalled drivers, rebooted w/o the device installed, moved it to another IDE line, ...everything.

The next day I found a segment failure in one of the HD's. Lost everything because it was RAID0. Replaced with a new HD, reinstalled W**** OS and all peripherals were back.

Hardware can fail even after one day! The gaussian curve for MTBF (Mean Time Between Failure) is just a statistical curve. This is why hardware that has to work for long periods of time is run in a lab to for many moons to expose 'infant mortality'.

Check the hardware for this one!

---

### Post by Apotheosis on 2007-12-02
Here is my swap information:
superuser@Taneshia:~$ free
             total       used       free     shared    buffers     cached
Mem:        384448     379916       4532          0       4052      65364
-/+ buffers/cache:     310500      73948
Swap:      1028152     555728     472424

When I did the alternate config method, my screen went blank for about 10 seconds and when it came back on, this was in the terminal:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071202221959

Dapman, I went from Edgy to Gusty, but I downloaded the CD and did it that way, rather than just upgrading.

Oh, and how would I tell if my hardware was messing up?  Would I just have to take it somewhere?

---

### Post by blehman419 on 2007-12-02
backup and install.  my computer started to lag, and when i reinstalled, everything was back to normal.  i think sometimes you just need a fresh clean slate.

---

### Post by Apotheosis on 2007-12-02
To do this I would have to go buy an external.  Right now, a month before Christmas, that is not optimal.  I will keep trying different suggestions, but I guess if it comes down to it, I will just suck it up and do as you suggested.

---

### Post by baxterdog on 2007-12-02
Apotheosis, come on!? Reformatting is easy! We're used to it as ex windoze users, right? I found that it was way easier to reformatt than deal with the constant updating.

---

### Post by aqchat300 on 2007-12-02
> **frank002 said:**
> Can't help with cpu but X is Ubuntu's graphical subsystem. I believe you can reconfigure it by opening a terminal window and typing dpkg- reconfigure xserver-xorg.

to be novice:gnome is the X Server x server is basically kde and gnome they both provide the graphics and the xconfig file people talk about has to do with basically noobish eye candy and graphics gone wrong.. ok back on topic..

on-topic:my guess is a reinstall should fix it sounds like a corrupted file in ubuntu or low ram?:(


edit:i really need to read before i post... i see someone suggested the format... and reinstall....

---

### Post by Apotheosis on 2007-12-03
> **baxterdog said:**
> Apotheosis, come on!? Reformatting is easy! We're used to it as ex windoze users, right? I found that it was way easier to reformatt than deal with the constant updating.

Yes, it is easy and I have done it more times than I want to remember, but right now I don't have anything to back up my data and I don't really feel like losing everything.  I think I will just wait and ask for an external for Christmas and do it then.

Well, thanks for all the suggestions and help, guys.

---

### Post by megamania on 2007-12-03
> **Apotheosis said:**
> Megamania, what would cause a hard drive failure?  My laptop is only about two years old, and I take pretty good care of it, save forcing it to shut down by holding the power button a small handful of times.


First of all, your question made me realize that when I had the problems you are having now, it wasn't literally a hard drive failure.
I went crazy for months, and then simply tried changing the sata cable and everything started working correctly again!

Anyway, besides faulty cables, a hard disk can simply break down because it's defective - all things break in the long term, and some break in the short term... I'm not saying it is your hard disk, but it is possible. There are so many possibilities, we can just try to guess.

From what you say, however, I think it's not a software problem, and it's not a virus/trojan.

---

### Post by red_Marvin on 2007-12-03
You could always check the output of *dmesg* when the computer starts acting up again.

---

### Post by rune0077 on 2007-12-03
Also, whenever things slows down on your system, first thing to do is check your System Monitor (System > Administration > System Monitor). If your problems is caused by a bad script or some software taking up more space than it ought to, it should be visible from here. Open the monitor as soon as things starts acting up, then check the list for anything that uses an unlikely high amount of CPU (like, consistently hogging 50+% of the CPU). If there's such a service/program, try killing it and see if that doesn't change anything.

---

### Post by quandary on 2007-12-03
> **megamania said:**
> As the other posters said, it sounds like hardware fault. 

I had a few of your problems (especially the first and last ones you mention) when my hard drive started breaking down.

I can confirm that.
If your warranty period has ended, and if you are clever, this might be a good moment to look for a extension of the warranty period, if that's still possible retrospectively...
No matter what it is, I strongly advise you to do a backup of all your data ASAP! Don't forget E-Mail.

However, as warranty extension costs money, you should first systematically rule out any kind of other error, before going for the hard drive.

Firefox can be due to bugs in an updated version, or an added plugin. I'm also experiencing problems with Firefox.
You can use IceApe instead (formerly known as netscape). I like Epiphany, because it's very bug free, but unfortunately, it is sooooo slow.

As said before, your problems are not usual for viruses.
But to be sure, you can install a Linux anti-virus program. That's anyway a good idea.
Some suggestions:
--------------------------------------------
[http://www.vanja.com/tools/sophie](http://www.vanja.com/tools/sophie)
[http://www.clamav.net](http://www.clamav.net)
[http://www.openantivirus.org](http://www.openantivirus.org)
[http://www.vanja.com/tools/trophie](http://www.vanja.com/tools/trophie)
[http://www.grisoft.com](http://www.grisoft.com)
[http://www.f-prot.com](http://www.f-prot.com)
[http://www.kaspersky.com](http://www.kaspersky.com)
[http://www.centralcommand.com](http://www.centralcommand.com)
[http://www.hbedv.com](http://www.hbedv.com)
[http://www.commandsoftware.com](http://www.commandsoftware.com)
[http://www.symantec.com](http://www.symantec.com)
[http://www.f-secure.com/products/anti-virus](http://www.f-secure.com/products/anti-virus)
[http://www.avast.com](http://www.avast.com)
[http://www.nod32.com](http://www.nod32.com)
[http://www.pandasoftware.com](http://www.pandasoftware.com)
[http://www.nai.com](http://www.nai.com)
[http://www.virusbuster.hu/en/](http://www.virusbuster.hu/en/)
[http://www.cyber.com/](http://www.cyber.com/)
[http://www.ikarus-software.com/](http://www.ikarus-software.com/)
[http://www.bitdefender.com/](http://www.bitdefender.com/)
[http://www.trendmicro.com](http://www.trendmicro.com)
[http://www.sald.com](http://www.sald.com)

some may be a bit old....
--------------------------------------------
Additionally Checking for rootkits may also be a good idea.
There are some debian packages:
- Rootkit Hunter: apt-get install rkhunter
- Check Rootkit: apt-get install chkrootkit. 


Running memtest was a good idea.
Additionally, I don't think this is a problem with the CPU, because if so, it's not likely that your computer would boot up at all...

I know from windows that there are some advanced hardware diagnostics programs, so you  probably should get yourself a hardware diagnostics program for Linux.

As also said previously, your filesystem, or a part of it, could be corrupted.
In this case, run fsck (WARNING: read the web manual first, and backup your data BEFORE).

If all fails, format and do a clean install.
If you don't have an external usb drive, i think there are some free web services that offer you storage...
You of course would have to use several of them, to get so many gigs uploaded. You can also try uploading your files to rapidshare or verzend. In a encrypted and compressed archive, of course.

Besides, I've recently buyed a 500 GB USB drive, costed only $150, which includes 2 years warranty, so that shouldn't be that much of a problem...

---

### Post by Irony on 2007-12-03
> I went from Edgy to Gusty,

Maybe this is the problem, as it isn't possible?

You need to go Edgy > Feisty > Gutsy or just do a fresh install of Gutsy.

---

### Post by meierfra on 2007-12-03
> mem: 384448 379916 4532 0 4052 65364
-/+ buffers/cache: 310500 73948
Swap: 1028152 555728 472424

I suggest more ram.  Or use xubuntu

---

### Post by Niniel on 2007-12-03
> **baxterdog said:**
> Apotheosis, come on!? Reformatting is easy! We're used to it as ex windoze users, right? I found that it was way easier to reformatt than deal with the constant updating.

Lol, and here you are doing the same. And there are many more updates for Ubuntu than for Windoze (I don't consider that a bad thing, in fact, it makes me wish MS was as good in pushing out fixes and updates).
Kind of funny, isn't it?

It would be neat if somebody ever analyzed the forums and figured out what advice was given the most. My impression so far is "reinstall". :)

---

### Post by lespaul_rentals on 2007-12-03
He says he has been "running Ubuntu for over a year" with no problems, yet his profile says his operating system is 7.10 Gutsy.  It seems quite obvious that he did an upgrade or new install to 7.10, and such negative symptoms match the description of standard Gutsy problems.

So, yeah...if you upgraded to 7.10, that's probably your problem right there.

---

### Post by 99bluefoxx on 2007-12-03
i experienced similar problems before, when my WD80 GB lost the last 39% of the file system to corruption, and linux woyuld no longer boot
also, if you are overclocking your CPU, it can destabilize the whole system, believe me, i tried a 100%[2.93>3.93] OC on mine, and it crashed every five minutes, so i went with a 40-60% overclock
if your arnt overclocking anything, it may be your RAM, did you have it upgraded recently?if so, are they both compatable with each other?PC3200 sometimes will not work with PC2100, so check your BIOS for a "RAM flexibility" option, probally found under the "chipset" tab or menu.and if you have upgrade your version recently, it could be that as well, a clean install is oftentimes better than a upgrade, as i found when trying to move up from 6.10 to 7.04, and my default kernel crashed, forcing me to boot from a earlier version, and causing my system to lag, while i downloaded the ISO for a 7.04 disk. these are just a few suggestions i can give you, out of my own experience. hope i could help

---

### Post by megamania on 2007-12-03
> **Irony said:**
> You need to go Edgy > Feisty > Gutsy or just do a fresh install of Gutsy.
Right. 

If you really upgraded directly from Edgy to Gutsy (I didn't think that was possible), my advice is to clean install and check if you experience the same problems. It's the easiest and cheapest thing to do.

---

