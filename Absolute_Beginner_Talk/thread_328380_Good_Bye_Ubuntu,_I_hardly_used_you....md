---
title: "Good Bye Ubuntu, I hardly used you..."
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by S.D.K. on 2006-12-30
Well, it happened again.
Ubuntu no longer will boot for me.

THis is the fourth time. Guess this means that Linux is not meant for me.
Well thank you for all the help that I got here. While this community was nice enougt to answer most of my questions, sadly I will never know why Ubuntu dies on me.

I've been getting the same error since installation #2 of Drapper Drake:


17179586.460000 EXT3-fs error (device hdb1) ext_check_descriptions Invalid bitmap
for group 384 not in gray (block 2147483647)!

Mount /dev/hdb1 on root failed: Invalid argument

mount /root/dev No Such file
/sys No Such File
/proc No Such file

Target filesystem doesn't have /sbin/init

/bin/sh: can't access tty; job control turned off

Any way to salvage my experience with Ubuntu or will I be force to use Windows XP for a long long time?

---

### Post by melancholeric on 2006-12-30
Sounds like the hard drive is failing. If it is it won't take long for winxp refusing to run on it too.

---

### Post by 23meg on 2006-12-30
Can you boot in recovery mode?

---

### Post by raul_ on 2006-12-30
There are a lot of posts about that error:

[http://www.ubuntuforums.com/search.php?searchid=11988170]("http://www.ubuntuforums.com/search.php?searchid=11988170")

Did you give them a try?

---

### Post by MkfIbK7a on 2006-12-30
yeah it sounds like you harddrive is going to die any day now sorry bout that :(

---

### Post by Sef on 2006-12-30
> Well, it happened again.
Ubuntu no longer will boot for me.

THis is the fourth time. Guess this means that Linux is not meant for me.

Could be too that a debian based system is not good for you machine.  I had one computer that I could only install a slackware based Linux to get it running well.

---

### Post by S.D.K. on 2006-12-30
> **melancholeric said:**
> Sounds like the hard drive is failing. If it is it won't take long for winxp refusing to run on it too.

That is one possibility, but that Hard Drive is only three years old and up until this point, rarely used.


> **23meg said:**
> Can you boot in recovery mode?

No, it can't as it spits out a bunch of text and then some errors.


XP won't die on me as this computer is only 8 months old and XP is on its own physical drive.

Installation #4 Ubuntu lasted the longest.  I turned the computer off over night as I slept and when I woke up turned the computer on, it booted just fine.

Still when can you tell that a hard drive is going to die/is dying on you?

---

### Post by ComplexNumber on 2006-12-30
**S.D.K.**
try another linuix distro.

---

### Post by raul_ on 2006-12-30
I think Suse is the next best thing

---

### Post by Stephen47 on 2006-12-30
you might try this to tell if the hard drive is dying:
 [http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)
It is for hitachi drives but I think it works for other brands as well.

---

### Post by smoker on 2006-12-30
>  	you might try this to tell if the hard drive is dying:
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)
It is for hitachi drives but I think it works for other brands as well.

this is a great app, also, each hard drive manufacturer has it's own diagnostic tool you can freely download and copy to a bootable floppy or cd. the age of a drive isn't really a good gauge, a hard drive can fail at any time. overheating can cause a lot of problems, is your drive running cool enough?

---

### Post by adamonline on 2006-12-30
> **S.D.K. said:**
> Still when can you tell that a hard drive is going to die/is dying on you?

You can't!  That's the power of the hard drive.  Instant, unforseen failure.

Then again, sometimes you get weird stuff happening, like your issue.  I once had a RAID array where one of the drives would fail about once a week, but I could restart the computer, enter raid setup at boot, and automatically repair it.  One day, after a couple months and the frequency between occurences becoming shorter and shorter, it just wouldn't repair.  Luckily I backed up when it started happening, so no real harm done...

Maybe if you install a fifth time, you should just install to the same drive that your Windows is on and see what happens.  You did say you were dual booting?

Don't give up on Ubuntu altogether!  it's my understanding that sometimes things happen that make it impractical to stick with it, but perhaps when you get your next system down the road you'll be able to have one of the many Ubuntu systems that just works right ;)  Don't ask me tho, I'm just a noob...

---

### Post by The Noble on 2006-12-30
That is really too bad and is really frustrating. Same thing happened to me actually: I could run Windows XP but it would fail every few days. I installed Ubuntu on the same drive and it never died (I only had the computer for the week though). If you have the time and patience, you could try to share the Windows drive with Ubuntu. If this is the last straw for you, though, good bye and happy travels!

---

### Post by gn2 on 2006-12-30
Could be that particular hard drive just doesn't like Ubuntu.

One of my notebook drives makes horrible clicking noises with Ubuntu and is silent with Windows 2000 Pro...?

---

### Post by moshuptrail on 2006-12-30
just typing the command : dmesg 
at the command line wil tell pretty quick if the HD is having errors
you'll see things like seek failures and so forth.

---

### Post by S.D.K. on 2006-12-30
Well, according to Seagates HD Diagnostic Tools, both Drives show no problems.

I can still access my Ubuntu Drive via explore2fs.

Trying another Linux Distro is out of the question as everyone I talked to said that Ubuntu is great for people whose only OS experiece is on Windows.

As for installing Ubuntu on my Master Drive...It would take me a few days to back up a lot of files to clear up a good 30 more GB of free space in my every shrinking 160 GB HDD :-k 

However, I still need to know why this error keeps popping up. Installing another linux OS on it would be useless if I get a similar error to it without knowing why.

Every time I've used Ubuntu, I've downloaded all the updates, then used easyUbuntu/Automatix to download things to be able to use Ubuntu as I want to.

The last time I used it I used Automatix and didn't install the nVIDIA drive to it as I read that it could cause some problems. I was able to shut it off and get back to it unlike the last two installations of it.

I really don't want to give up on Ubuntu, but I can't keep installing it over and over and having a error pop on to me with no idea how to fix it.

---

### Post by Bartender on 2006-12-30
I second the suggestions to get the manufacturer's diagnostic.  Find it, download it, run it, see what the diagnostic says.  EDIT: Whoops, too late!

Also try Speedfan, a free Windows download, and see if it detects both drives and reports their temps.  If the HDD isn't getting sufficient cooling that'll definitely shorten its lifespan.  Anything over 40 degrees or so should be addressed.

My HDD is running around 24 degrees C according to Speedfan, hardly higher than ambient.  But my situation is kinda unique - I built a wooden cabinet and installed the PC parts inside on a roll-out drawer.  A little fan blows right onto the HDD from underneath.

Another EDIT:  Ubuntu isn't the only distro that could work out for you.  PCLinuxOS is another good candidate.

---

### Post by 23meg on 2006-12-30
[QUOTE=S.D.K.]
Trying another Linux Distro is out of the question as everyone I talked to said that Ubuntu is great for people whose only OS experiece is on Windows.[/QUOTE]It can be great, but so can other distros. Do try some others; Ubuntu isn't your only option.

---

### Post by smoker on 2006-12-30
you could always try out some other linux live-cd's, i believe you can get live versions of sabayon, mepis, knoppix, there are probably loads more, find one you like, and runs ok, then try to install that,

---

### Post by riven0 on 2006-12-30
Yeah, I feel for you, S.D.K. Can't imagine Ubuntu failing on me every few days; I'll be sad forever. :( 

But your problem is one I've never heard of before. If it's not the hd I don't know what it could be. Is it possible that you have another hd to test Ubuntu on? 

[Here is another good article]("http://www.pcstats.com/articleview.cfm?articleid=1583&page=4") on diagnosing hd's going bad.

---

### Post by SAGEv4.5 on 2006-12-30
> **S.D.K. said:**
> 
Still when can you tell that a hard drive is going to die/is dying on you?

spin rite by steve gibson from grc. not a free program but good!

---

### Post by S.D.K. on 2006-12-30
I've tested my Windows XP Drive and the Ubuntu Drive and both tested out to be working good.

The spare drive didn't show any of the classical signs of Disk Failure before I used it as a Linux drive.

Could it be that I've installed it using the x86 installation method? My processor is an AMD 64 Athlon.

But if that is the problem, why? no error popped up when using the LiveCD and it could restate it with no problems once I installed it. Its just leaving it alone to go back to XP for a few hours and coming back causes the errors.

I can still "read" the ext3 drive by using explore2fs on XP, so the data is still there.

It couldn't be a problem with Grub could it?

But today, after using XP and then going back to Ubuntu it was okay.
It was just after I came back from work that the error message popped up.

---

### Post by riven0 on 2006-12-30
> **S.D.K. said:**
> But today, after using XP and then going back to Ubuntu it was okay.
It was just after I came back from work that the error message popped up.

Does the error always come up after you use easyUbuntu?

---

### Post by trbloomer on 2006-12-30
If you enjoy messing around with your computer I´d sugest you keep troubleshooting the current install dmesg was a good idea at least it might give you some clues as to what is happening.

However if you really don´t like working on your computer then maybe using XP is the way to go for you, at least assuming its working well. Either way you can get work done and have fun with the machine.

---

### Post by S.D.K. on 2006-12-30
> **riven0 said:**
> Does the error always come up after you use easyUbuntu?

I thought it was because ot Easy Ubuntu. My last installation I used Automatix2 and skipped installing any of the nVIDIA drives.

> **trbloomer said:**
> If you enjoy messing around with your computer I´d sugest you keep troubleshooting the current install dmesg was a good idea at least it might give you some clues as to what is happening.

However if you really don´t like working on your computer then maybe using XP is the way to go for you, at least assuming its working well. Either way you can get work done and have fun with the machine.

typing "dmesg" on the prompt I get after Ubuntu fails to boot does nothing.

---

### Post by riven0 on 2006-12-30
> **S.D.K. said:**
> I thought it was because ot Easy Ubuntu. My last installation I used Automatix2 and skipped installing any of the nVIDIA drives.

:-k Okay, so if I'm reading this right, the errors happen sometimes after using either easyUbuntu or Automatix2. So, if you willing to do some testing, why don't you try doing something like this:

Re-install Ubuntu all over again. (Yes, I know, it's a headache :rolleyes:)

*Don't* install either easyUbuntu and Automatix2. It's quite possible both these programs are giving your computer problems. Members on this forum can help you install all those codecs manually. It may sound scary, but believe me, it isn't. :mrgreen: 

Then test it for a few days and see if the errors crop up again.

---

### Post by bakegoodz on 2006-12-30
If XP is on another drive works, that just points more to the drive being the problem.
Yes try your Manufacturers hard drive utility, and do the full media scan. If it comes back with an error I would recommend a new drive or useing Spinrite to fix it. I just saved someone's drive that wouldn't boot or could be read with a livecd with Spinrite. [http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm) Don't a accuse me if spamming, I can't find another program anywhere that does the amazing data recovery that this does.

---

### Post by S.D.K. on 2006-12-30
> **riven0 said:**
> :-k Okay, so if I'm reading this right, the errors happen sometimes after using either easyUbuntu or Automatix2. So, if you willing to do some testing, why don't you try doing something like this:

Re-install Ubuntu all over again. (Yes, I know, it's a headache :rolleyes:)

*Don't* install either easyUbuntu and Automatix2. It's quite possible both these programs are giving your computer problems. Members on this forum can help you install all those codecs manually. It may sound scary, but believe me, it isn't. :mrgreen: 

Then test it for a few days and see if the errors crop up again.

Well I guess I can do it one more time:-k 

On another forum, it was suggested that I run Memtest86+.

I'll probable do that after that done.

For the record, easy Ubuntu never worked well with me. Many of the repositories gave me 404 errors or not found errors.

Automatic2 worked well.

Sigh...it going to be a pain in the *** installing several dozen things things manually.
I really don't like using the terminal as I have no real idea what I'm doing when I'm copying and pasting things.

---

### Post by MkfIbK7a on 2006-12-30
it could possibly be a problem with the harddrive jumper maybe the drive with ubuntu is jumpered for slave instead of master...

---

### Post by S.D.K. on 2006-12-30
> **wert613 said:**
> it could possibly be a problem with the harddrive jumper maybe the drive with ubuntu is jumpered for slave instead of master...

Huh?

Well the drive it is on is a slave drive.

---

### Post by riven0 on 2006-12-30
> **S.D.K. said:**
> Sigh...it going to be a pain in the *** installing several dozen things things manually.
I really don't like using the terminal as I have no real idea what I'm doing when I'm copying and pasting things.

Don't worry; we'll help you along. :D  The thing is, the majority of the third party codecs and drivers can be done through Synaptic package manager, but it's just easier copying and pasting. You'll see... :mrgreen:

---

### Post by MkfIbK7a on 2006-12-30
try to change it to master and windows slave (or change both drives to cs)

---

### Post by adamonline on 2006-12-31
And don't forget, as mentioned above, that it may be a hardware compatibility issue with the hard drive you're using... So, even though the tests you've ran on it have come out okay... ... ...  

And I used to have no idea what I was typing at the command line, but I've really spent more time learning what I was doing than copying and pasting, and the gui's almost more of a PITA now...  That's the beauty of Linux...  It's like mixing vinyl compared to mixing CD's...  Though it's unlikely you feel what I mean by that ;)

I'm not even two weeks into this, but I know I'll always have a linux machine from now on...  I don't even use my windows box but to play CS:S and use certain proprietary software...  And to test my DHCP serving :D

I'm glad to hear you'll try a (sigh) fifth time, I'd recommend using the 64 bit install (I deduce that'll match your processor?).  I imagine that's more likely to throw an error being installed on an x86 machine, than the x86 version is to throw an error on a... um... 'later' processor...  Anyway, again, I offer my noob disclaimer ;)

---

### Post by ragnar_123 on 2006-12-31
Stephen47:

Ultimate Boot CD would be better, as it includes all major hdd tools.
visit: [http://ultimatebootcd.com](http://ultimatebootcd.com) for more info.

---

