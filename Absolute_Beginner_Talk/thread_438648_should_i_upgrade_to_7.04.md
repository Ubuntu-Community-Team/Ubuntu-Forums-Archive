---
title: "should i upgrade to 7.04?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-05-09
hello all

so i recently installed 6.10 a few weeks ago to start my adventures in linux. so after much hard work and many hours of reading guides, i got it set up nice and good 2 go. very happy with it.

so here are my questions, should i upgrade to 7.04? and if i do, do i do it from another cd or through synaptic? and most importantly, will i lose my settings such as how my evolution is set up and all of that. most likely, i will lose some hardware configuration, but i can deal with that hopefully. also, do upgrades in anyway mess with my windows xp partition (because i dual boot)? as you can probably tell, i have never upgraded an OS, not even in windows -- its usually just WIPE and CLEAN INSTALL.

thanks in advance.

---

### Post by aimran on 2007-05-09
If you already have beryl set up then just be prepared to have it broken when upgrading to 7.04 :)

I like the feel of 7.04 personally. My suggestion is to upgrade.

---

### Post by BarfBag on 2007-05-09
You should definitely upgrade.  6.10 wasn't a very stable release.  Did you use Automatix or EasyUbuntu, or do the configuration the hard way?  If you did it the hard way, it's as simple as:

> sudo apt-get dist-upgrade

But back up first.

---

### Post by Miroku on 2007-05-09
thx for the quick replies

i never used automatix or easyubuntu -- either i upgraded through the terminal or synaptic

also, what should i back up exactly? --- and can someone answer those questions i asked in the first post?

---

### Post by Sef on 2007-05-10
> so here are my questions, should i upgrade to 7.04? and if i do, do i do it from another cd or through synaptic? and most importantly, will i lose my settings such as how my evolution is set up and all of that. most likely, i will lose some hardware configuration, but i can deal with that hopefully. also, do upgrades in anyway mess with my windows xp partition (because i dual boot)?

1) If things are running for you as you want them to, then there is not really a reason to upgrade unless you have a desire to.

2) A clean install will wipe out all of your settings.   An upgrade will keep your settings.  Howerver, an upgrade is more likely to fail than a clean install.

3) A clean install will wipe out all of your settings.  An upgrade, if it works right, will not.  

4) An upgrade should not affect your Windows partition.  

5) If you do upgrade, you might want to remove Beryl first and the restricted drivers.   They can cause upgrade problems, but not for sure they will.

> also, what should i back up exactly?

Back up your files...all of them...on Windows and Ubuntu.

---

### Post by Miroku on 2007-05-10
hmmm, reading your reply Sef, it seems that it is very risky to do an upgrade and you are making it seem like there is a high chance of failure. not very encouraging. i will have to wait and read some more stuff about this before i can do anything.

i am the type of guy that likes to stay on top of all of my software. i guess it is because of Windows, where i keep my adaware, antivirus, and any other program i have up to date, mainly just for security purposes. its more of a compulsion more than anything else, lol.

also, doing a clean install -- i would not need to re-partition and make ext3 and swap space again right? could i just use the ones that are set up already?

i dual boot with 2 harddrives. the master has both OSes + GRUB, while the slave is basically a storage drive and is NTFS formatted.

---

### Post by Nekiruhs on 2007-05-10
Well, Upgrades really aren't bad its only bad really if you lose power during upgrade. Or if you have software conflicts.

---

### Post by mills on 2007-05-10
i upgraded from dapper to edgy countless times as i only had a dapper cd and kept breaking edgy.
i would guess about 10 upgrades and never had a problem with the upgrade or my windows partition, but bear in mind about half of those upgrades i had no settings or anything to lose becuase i never had time to make settings or a home partition

i say go for it, if it breaks you just get to more experience:)

---

### Post by newlinux on 2007-05-10
I've upgraded two machines from dapper to edgy to fiesty (one of them is dual boot) and one of them from edgy to feisty (dual boot with OS X). Dapper to edgy was a little problematic, edgy to feisty was smooth. I think it is pretty safe (in terms of possible data loss, but it IS possible to lose data). Unless there is something specific with feisty that you want the only real reason to update is just to stay current with updates in software and drivers. I have two machines that still run edgy (they are servers, and I don't want to chance breaking them or having to take the time to reconfigure) and don't plan on upgrading them any time soon.

Just my 2 cents. And the experience varies greatly with things breaking.

---

### Post by Miroku on 2007-05-13
so i upgraded to 7.04

it was not a smooth upgrade at all. i upgraded through the update manager by clicking on 'upgrade to 7.04' -- it started downloading something i believe but that is where it stopped responding. i was forced to kill the process.

then i decided to upgrade from the alternate CD. everything was going good until it went to 'deleting obsolete software' -- after it stopped responding. at this point, i believe everything was installed so instead of killin the process, i CTRL + ALT + Backspace'd it. after i logged back in it was 7.04 but there were several updates that ihad to do.

after i restarted, it gave me the xserver error so i did some reconfiguring and had it back up and running. after another restart, the nvidia restricted drivers were used. so i think everything is all good now.

my screensaver (GLmatrix) is running kind of slow so i am contemplating on wether or not to use the nvidia drivers offered by their website. also, using the restricted drivers, i have no option of playing around with the nvidia settings like i used to have in edgy. 

should i stay with the restricted drivers or get the ones from the nvidia site OR are they actually the same thing -- lol?

thanks.

---

### Post by Miroku on 2007-05-13
so i installed the drivers from the nvidia website -- apparently the restricted drivers are the same, but they were not configured to fit with my kernel? -- whatever that means.

now screensaver runs smooth like before and i also have nvidia settings i can play around with.

cool.

---

### Post by ramjet_1953 on 2007-05-13
You only have to read these forums, to see that upgrading does have some significant risks, especially if your current version is anthing more than a standard install.

Also, there are still some issues with Feisty yet to be sorted.
Again, have a look at the forums, and see if any of the issues are potentially a problem for you.

Issues that I have noticed are:

1. Many people are complaining about random hard locks of their system. (Possibly video card issues)

2. There is a big problem with SANE and scanners

3. Inserting a VCD disk causes hard locks.

4. There seem to be a lot of problems being reported with printer installs, even with HP printers, which are normally a no-brainer.

I am currently running Edgy, which has been stable for me, with my particular hardware configuration, so I won't even consider upgrading to Feisty untill the dust has settled and the outstanding issues have been addressd. I will probably wait until the next LTS release.

Regards,
Roger :cool:

---

### Post by jbonll05 on 2007-05-13
Three days ago update manager had an across the top of the screen notice that I could update  from 6.10 to 7.04 here . The machine is a 32bit i686 AMD cpu machine. The update went smooth and everything seems to be working just fine.  I do not know why update manager included the message at the top of the update panel. I probably have not been singled out for the message. 
JB,Ubuntu user since 4oct05

---

### Post by Miroku on 2007-05-14
i noticed that i had to reinstall certain things for them to start working again, these including my HP PSC1315, the way my evolution is set up to receive hotmail, the video drivers, and possibly some other things that i am unaware of at the moment.

no computer freezing/locks yet -- so still happy

---

