---
title: "Should I wait?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by naughtywizard on 2007-03-03
I want to make the jump, I really do.  More for political/philosophical reasons than technical. But I'm wondering if I should wait for a future release.  I'm computer literate, but not savvy, and frankly I'm scared.

My box is a Gateway 7426GX notebook, amd64 bit chip, and broadcom 4320 wireless.  It is my only computer, and I can't afford to have it down for long.  I've been reading threads the past few days, and with the headaches folk are having with similar configs should I just be patient? will some of these problems be addressed in a future release, or should I wait until I can get a more amenable rig (which kinda defeats the whole purpose, no?).

---

### Post by floke on 2007-03-03
Try a LiveCD. That way you'll have an idea of whether or not it works well.
Before running the cd - be sure to select the 'check disc' option to make sure it has no errors on it.

---

### Post by naughtywizard on 2007-03-03
The live CD works fine (v 6.06), other than not seeing the broadcom wireless card. 

I found a related thread [here]("http://http://www.ubuntuforums.org/showthread.php?t=251011&highlight=live+cd%2C+broadcom"), but nothing else.  Any suggestions?

---

### Post by hellraiser_rob on 2007-03-03
sometimes you just have to fly by the seat of your pants and hope you don't get a wedgy

---

### Post by Ek0nomik on 2007-03-03
Installing your wireless card with be a bit of work, but once you figure out how to do it, it will be cake.  I see many people suggest 6.06 with older computer configurations, so I would just give it a go.  If you have nothing to lose, just try it out.  I personally wouldn't wait for the newer release.

Cheers!

---

### Post by naughtywizard on 2007-03-03
Unfortunately, I do have much to lose.  Not financially (always kept backups), but I'm involved in community and anti-war organizing, and this is my ony way to stay in touch with a lot of folk.  Being offline for more than a day or two would be major ungoodness. And trying to network from the hour a day alloted at the library just isn't practical.

Sadly, it's looking like I must continue the microsuck a bit longer; especially since my reasons for wanting to switch are philosophical rather than pragmatic.(at least I've already gone over to firefox and openoffice)

And being patient for what I want is a discipline I can always use practice on. ;)

---

### Post by pegazuz on 2007-03-03
> **naughtywizard said:**
> Unfortunately, I do have much to lose.  Not financially (always kept backups), but I'm involved in community and anti-war organizing, and this is my ony way to stay in touch with a lot of folk.  Being offline for more than a day or two would be major ungoodness. And trying to network from the hour a day alloted at the library just isn't practical.

Sadly, it's looking like I must continue the microsuck a bit longer; especially since my reasons for wanting to switch are philosophical rather than pragmatic.(at least I've already gone over to firefox and openoffice)

And being patient for what I want is a discipline I can always use practice on. ;)

There are many versions of live linux live cds and if you try one a day I would guess in a week you will have a couple that will work right off with no fiddling required.  I just started trying Linux seriously  a few months ago but find I use it almost all the time to surf the internet or do email.  I still need windows to upload my photos and sync my Dell Axim but I figure in a few months i may be able to do those too with out windows. In my experience as someone with limited computer skills, linux is harder to learn and configure, but easier to use once you figure it out and more reliable.  Under Microsoft, Firefox often crashes, but never under Linux.  Linux also seems easier to maintain and update.

A very safe way to try Linux with virtually no risk to your machine is to install a distro to an external  hard drive and run it from there. I did this so nothing was done to touch my MBR or ability to boot up windows. There is always a small risk that trying a dual boot will screw up your hard drive and ability to boot windows although any such problems can be fixed usually within a few hours by reinstalling windows.

I have two external hard drives set up now to boot two different versions of linux and you can buy a small one that will work great for linux for $50-70.  Another one I like is using Puppy linux cause it runs so fast and it will run off a small flash drive as well as live CD.  A small flash drive can be bought now for $20 that will run Puppy fine.  So I wouldn't wait, get started and try some more.

---

### Post by floke on 2007-03-03
Well I reckon the best bet is to set up a dual-boot system, so if you break Linux, or can't sort out the wireless card straight away, you can always boot into Microshaft.

---

### Post by luckylucky on 2007-03-03
I understand your concerns in this area.  I too have made the jump to Ubuntu, and in some ways was similar to you in that my computer is my life-blood (financially, for work) and couldn't afford down time.  I am supremely pleased to have made the transition, and am very satisfied with Ubuntu (other than a couple of challenges I've had figuring out how to hack something).  It is definitely worth the effort.

[COLOR="Red"]**My recommendation to you would be this...**[/COLOR]

1) First back up your computer
2) Reinstall a fresh windows
3) Use GParted to resize the NTFS partition to 30% of your hard disk
4) Use GParted to make a fat32 partition of 40% of your hard disk
5) Install Ubuntu on the remaining 30%

Now you'll have a dual boot system, both Win & Ubuntu co-existing on your computer.  If you are stuck in Ubuntu and need something done you can still reboot & revert to windows.  The fat32 partition is just to have a harddrive space accessible by both OSes so that you can access your files from win or linux.

Over time you'll find that you'll grow more & more comfortable with Ubuntu and will use it almost exclusively, but atleast for now you'll have the risk-free ability to cross back to Win without any worries.  I think this is the best transition strategy for most people in your situation.  Thus you can have both, and later, if you deem it worthwhile you may obliterate the NTFS partition altogether... but only when you are comfortable and sure you want to do that.

Good luck!
LuckyLucky

P.S. I just wrote this on my laptop that has this configuration (10gig Win, 10gig Ubuntu, 60gig fat32) so my recommendation is what I do myself.  I use Ubuntu about 97% of the time, just going to the win from time to time to use a legacy application that doesn't work that well in Wine).

PP.S.  Yes, make the jump... don't wait!

---

### Post by nerdman978 on 2007-03-03
I agree with alot the people who replied. Try a Live CD, if you like linux, then move on to partition your drive for both Windows and Linux (back up important Windows files first!). Another option would be to run Linux in a virtual machine (Windows offers a free one). Good luck.

---

### Post by Amenemhet on 2007-03-03
JUMP JUMP!!! Go ahead! You know you want to! There are lots of us here who will help you up if you stumble...which I am sure you will, as most of us did at one time or another. I bet you won't regret it, and will wonder in 6 months why you didn't do it earlier!

---

### Post by houstonbofh on 2007-03-03
You will never get to the point you are looking for.  There will always be some "risk" for you in trying a new thing.  Duel boot minimizes this.  Make sure you are only using about 1/3 of the HD, and defrag.  Now boot the live CD, and shrink your windows partition to half it's size.  Install Ubuntu in the rest. Install the Windows ext2fs file system driver, and the ntfs3g linux file system driver, and you can see the hard drives from either system.  Eventually, you will find the Windows partition lagging... :)

---

### Post by floke on 2007-03-03
Absolutely! JUMP!

Also, a word on expectations - expect things to go wrong, expect frustrations, expect to break stuff (:( ), expect to be able to learn how to fix it (:) ), expect people in the forums to help you (we will), expect to learn more about Linux and yourself every day, expect to have uncontrollable moments of joy when you work something out, expect to have freedom (no viruses, WGA etc.), expect to spend more time than any normal person would deem reasonable on finding stuff out about Linux (it's very addictive!), and expect (as the previous post said) to look back and think why the hell you didn't do any of this earlier.

Good luck.

---

### Post by naughtywizard on 2007-03-03
> **luckylucky said:**
> I understand your concerns in this area.  I too have made the jump to Ubuntu, and in some ways was similar to you in that my computer is my life-blood (financially, for work) and couldn't afford down time.  I am supremely pleased to have made the transition, and am very satisfied with Ubuntu (other than a couple of challenges I've had figuring out how to hack something).  It is definitely worth the effort.

[COLOR="Red"]**My recommendation to you would be this...**[/COLOR]

1) First back up your computer
2) Reinstall a fresh windows
3) Use GParted to resize the NTFS partition to 30% of your hard disk
4) Use GParted to make a fat32 partition of 40% of your hard disk
5) Install Ubuntu on the remaining 30%

Now you'll have a dual boot system, both Win & Ubuntu co-existing on your computer.  If you are stuck in Ubuntu and need something done you can still reboot & revert to windows.  The fat32 partition is just to have a harddrive space accessible by both OSes so that you can access your files from win or linux.

Over time you'll find that you'll grow more & more comfortable with Ubuntu and will use it almost exclusively, but atleast for now you'll have the risk-free ability to cross back to Win without any worries.  I think this is the best transition strategy for most people in your situation.  Thus you can have both, and later, if you deem it worthwhile you may obliterate the NTFS partition altogether... but only when you are comfortable and sure you want to do that.

Good luck!
LuckyLucky



Sir, (or madam...doesn't matter) I could kiss you!  This looks like a safe jump, even with my limited technical skills.  And a quick google brought a live cd version of [GParted]("http://gparted.sourceforge.net/livecd.php") for anyone else who might want to try jumping in with waterwings.

Thank you all for advise and suggestions, I'll try and get back in a few days to report on progress or nightmares or both.

Now if you all will excuse me, there's a war to stop.

Peace and penguins, Rich

---

### Post by radtek on 2007-03-07
[FONT="Comic Sans MS"]I never was really happy with a dual boot system. When things got a little frustrating on the beginning edge of the learning curve it was too tempting to reboot into windows.

I realized on my own that the plunge would force me to develop my facility for linux much in the same way as it was for windows 10 years ago. I have never looked back. Does *everything work?* No. But that is just some growing pains and dependency loss from M$! With Ubuntu I am able to do **everything I need to with confidence and a good conscience as well.**

Ubuntu makes it easy. Seriously.

Do it. Do it.[/FONT]

---

### Post by luckylucky on 2007-03-08
> **naughtywizard said:**
> Sir, (or madam...doesn't matter) I could kiss you!  This looks like a safe jump, even with my limited technical skills.  And a quick google brought a live cd version of [GParted]("http://gparted.sourceforge.net/livecd.php") for anyone else who might want to try jumping in with waterwings.

Thank you all for advise and suggestions, I'll try and get back in a few days to report on progress or nightmares or both.

Now if you all will excuse me, there's a war to stop.

Peace and penguins, Rich


Awe, shucks, thanks :cool: 
Since you're sooooo nice, I'll give ya a little extra treat...
[COLOR="Red"]Attached to this post you'll find a blank VMware appliance. [/COLOR] All you have to do is download the VMware player from [www.vmware.com](www.vmware.com) , burn a CD of Ubuntu, pop the CD in and boot the VMware app.  This way you can use Ubuntu in a risk free environment to start using it.  


By the way, during the install you'll notice there are two virtual hard drives.  Format the first one (16 gigs)  so that 512megs is /swap as linux-swap and the rest as /  as ext3  The second drive format it as fat32 and then register it as /media/storage .   After you are done with the install save the subfolder called "VirtualFat32-20gigs" to keep a swapable extra virtual harddrive (kind of like a portable external harddrive).  Keep your important files mainly there.

Sorry, I didn't include the VMware tools because it's too large to include as an attachment here, but you can get it for free from VMware anyways (download the free VMware server, open the zipped file, find the linux.iso file (search for "*.iso") then put it on a USB key, put it into your VMware app of Ubuntu, open the iso file, extract the one called vmwareto.tgz (you might need to rename it to end as .tgz ) then extract its' contents onto your desktop, then in terminal type:
cd ~/Desktop/vmware-tools-distrib

then type:
sudo ./vmware-install.pl

then pretty much follow the instructions that it asks of you during the install.


To add some more cool stuff go to [www.getautomatix.com](www.getautomatix.com) to have an easy time installing some other useful stuff into your Ubuntu.  Search this forum to understand more about automatix.


I wish you tremendous success in your Linux journeys!

LuckyLucky

---

