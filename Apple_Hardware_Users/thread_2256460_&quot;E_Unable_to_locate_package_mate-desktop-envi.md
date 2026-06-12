---
title: "&quot;E: Unable to locate package mate-desktop-environment-extras&quot;"
date: 2014-12-12
forum: Apple Hardware Users
---

### Post by este.el.paz on 2014-12-12
Folks:

Trying to follow in the footsteps of the masters, I have spent half the day trying to add the MATE desktop environment to my install of Lu 14.04 on my iBook G4 . . . I added the MATE ppa(s) . . . managed to get the key added as well . . . each time running the command to install "vanilla MATE" brings an error window . . . ```
E: Unable to locate package mate-desktop-environment-extras
```

When I tried to install the "Ubuntu MATE remix" command option . . . I get:

```
: Unable to locate package ubuntu-mate-core
E: Unable to locate package ubuntu-mate-desktop

```

Any thoughts on how to add the MATE DE to my Lubuntu install?  Doesn't seem to be happening using my skillset . . . .

e.e.p.

---

### Post by ibjsb4 on 2014-12-12
Sounds like you haven't done an update.

---

### Post by este.el.paz on 2014-12-12
> **ibjsb4 said:**
> Sounds like you haven't done an update.

Anything more specific?  I ran update/upgrade several times in this process, and then update/dist-upgrade . . . rebooted and **then**again tried to apt-get install mate . . . .

e.e.p.

---

### Post by ibjsb4 on 2014-12-12
I think that we have used the same install method.
[https://launchpad.net/~ubuntu-mate-dev/+archive/ubuntu/trusty-mate](https://launchpad.net/~ubuntu-mate-dev/+archive/ubuntu/trusty-mate)

Your using Lu and I use gnome.  I show a environment-core package, could be a difference in desktops.

Like I said, installing per the ppa has worked for me (3times).  And not for you ..

Could you install it from synaptic?  The 'ubuntu' part is dropped from the package name.
[ATTACH=CONFIG]258529[/ATTACH]
I also think a install without recommended packages is a good idea.  I have tried it both ways and --with-recommends pulls in about 200M of unneeded packages.

Edit
There is a ubuntu-mate-desktop in synaptic

---

### Post by este.el.paz on 2014-12-13
@ibjsb4:

Thanks for the further data, I did look in synaptic, and did see mate, but I was trying to use the CLI . . . for speed . . . but that got stymied at each step.  A bit busy today, but I will run it through synaptic using "mate-desktop" . . . and I'll post back with the results . . . .  It's always a "mystery" . . . when things work and when they don't . . . .

e.e.p.

[Edit: PS:  One of my targets is to have a working "suspend" or "hibernate" feature, which MATE may or may not provide, but, in terms of "recommended packages" . . . if 200 M's would give me suspend, that would be worth the space of it . . . .  Any thoughts on that from your experience in MATE DE?]

---

### Post by ibjsb4 on 2014-12-13
> if 200 M's would give me suspend, that would be worth the space of it
I do not see that the extra 200M brings anything to the table.  It is stated somewhere on a mate site that there is no advantage to pulling in the recommends,  I just don't believe everything I read and tried it anyhow.
Suspend is something you will just have to try and see what happens next.  I do not use it, but should be doable.
> Any thoughts on that from your experience in MATE DE?
You can count my Mate experience in weeks,  were both newbies :)

I still wonder why the standard install is not working for you.  Maybe you can find a tip here.
[http://askubuntu.com/questions/87040/how-do-i-install-mate-the-desktop-environment](http://askubuntu.com/questions/87040/how-do-i-install-mate-the-desktop-environment)

And this environment-extra package.  I find Debian references to it.  Have you somehow installed debian-mate instead of ubuntu-mate?

---

### Post by este.el.paz on 2014-12-13
@ibjsb4:

Thanks for the added thoughts . . . found a couple minutes to boot back into 14.04 and run a synaptic search for "mate-desktop" . . . and a bunch of stuff shows up, but it is version 1.6xx and the DVD of Ubuntu-MATE I booted yesterday had MATE 1.8 . . . .  I believe I want 1.8, because another one of the main reasons I like MATE is the floating GNOME feet screensaver . . . I just find it funny to watch those feet floating on the screen in my idle moments . . . .  I think they took them out in 1.6 . . . ???  

This isn't my first rodeo with MATE, I've had a number of MATE DE in Linux Mint on my MBPro . . . I've got LM17 MATE going . . . I'll have to check which version it is using, it's also based on 14.04 LTS . . . and it has the GNOME feet, but I recall in the last year posting in a few forums asking how to get the feet back . . . I wants the feets . . . .  : - )))  The floating MATE target symbol is just not that funny . . . what can I say, I have a refined sense of humor . . . .  : - 0

Anyway, I'll have to get back to checking through your links and see if they provide anything . . . already have a bunch of hours piled into this . . . probably easier/faster to just do the fresh install . . . but, if it would just add in it would keep my bookmarks and so forth . . . .  I'll post back.

e.e.p.

---

### Post by ibjsb4 on 2014-12-13
PPA-purge may come in handy.

[http://askubuntu.com/questions/309966/difference-between-ppa-purge-and-add-apt-repository-r](http://askubuntu.com/questions/309966/difference-between-ppa-purge-and-add-apt-repository-r)

Its in the repositories.

---

### Post by este.el.paz on 2014-12-15
> **ibjsb4 said:**
> PPA-purge may come in handy.

[http://askubuntu.com/questions/309966/difference-between-ppa-purge-and-add-apt-repository-r](http://askubuntu.com/questions/309966/difference-between-ppa-purge-and-add-apt-repository-r)

Its in the repositories.

Yes, it might.  A gentleman on the mate forum said that "PPC is not in the repositories" . . . so if I want to add MATE it looks like I would have to "nuke and pave" . . . rather than "purge" . . . .

e.e.p.

---

### Post by este.el.paz on 2014-12-17
Tried to run the liveDVD a couple times on my iBook . . . the system looks very nice . . . I added the "agp.mode" boot params . . . but first time I had set up the clock, logged into gmail . . . spent a few minutes in the system . . . and then the optical drive started to "chatter" rapidly . . . and the GUI froze--had to shut down.  I rebooted, and the desktop loaded into 2/3 black and 1/3 GUI screen . . . shut down again.  Third time, on the next day . . . the GUI loaded fine, got the clock set up OK . . . tried out some stuff, opened up a few tabs in the browser . . . then the fan started blowing very hard and clicking on tabs and buttons was no longer working . . . mouse was moving around, but nothing was responding . . . finally shut it down to get out of it . . . .

I think when I first tried 14.10 this desktop frozen thing was happening, or possibly it was with 14.04 . . . possibly fixed with an xorg.conf file, but question would be whether this MATE system is requiring more than the iBook has to deliver??

e.e.p.

---

### Post by abtabt on 2014-12-18
i use mate dvd [https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA](https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA) for a test ,works good i use nvidiafb driver
on a imac 700/800 with Persistent Live FW (its fast with FW disk )

---

### Post by vasa1 on 2014-12-18
[http://news.softpedia.com/news/Ubuntu-MATE-14-04-1-LTS-to-Get-Official-PowerPC-Support-Dust-Your-Old-Mac-467813.shtml](http://news.softpedia.com/news/Ubuntu-MATE-14-04-1-LTS-to-Get-Official-PowerPC-Support-Dust-Your-Old-Mac-467813.shtml)

---

### Post by este.el.paz on 2014-12-18
> **abtabt said:**
> i use mate dvd [https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA](https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA) for a test ,works good i use nvidiafb driver
on a imac 700/800 with Persistent Live FW (its fast with FW disk )

@abtabt:  Nice to hear from you again, my iMac is once again "not well" . . . RAM problems again, but I did test out this spin from rsavage from G+ . . . put it on a USB drive but the computer didn't find it using option key, probably would have to use openfirmware . . . but, what is this "Persistent Live FW" that you are talking about?

> **vasa1 said:**
> [http://news.softpedia.com/news/Ubuntu-MATE-14-04-1-LTS-to-Get-Official-PowerPC-Support-Dust-Your-Old-Mac-467813.shtml](http://news.softpedia.com/news/Ubuntu-MATE-14-04-1-LTS-to-Get-Official-PowerPC-Support-Dust-Your-Old-Mac-467813.shtml)

@vasa1:  Thanks for the link to the story . . . I have that iso . . . and I do like MATE quite a bit, it just seems like a few problems showed up while booted in the LiveDVD . . . and, hoping to be able to add MATE thru the repository doesn't seem do-able for PPC . . . have to wait until I have more time to fiddle with it . . . already have a lot of time spent getting 14.04 "fixed" to run on the iBook . . . .

e.e.p.

---

### Post by abtabt on 2014-12-18
e.e.p. 

Persistent Live FW (its fast with FW disk ) i use a extern  FireWire disk its faster then USB 1.1 and i think 2.0 is slower ,about 1 min to boot its like hd speed and its still 
there to use next time no need to re typ yaboot stuff nomodeset etc, only power up and  start ther you end last day to explore more install more etc

---

### Post by este.el.paz on 2014-12-18
> **abtabt said:**
> e.e.p. 

Persistent Live FW (its fast with FW disk ) i use a extern  FireWire disk its faster then USB 1.1 and i think 2.0 is slower ,about 1 min to boot its like hd speed and its still 
there to use next time no need to re typ yaboot stuff nomodeset etc, only power up and  start ther you end last day to explore more install more etc

@abtabt:  Alrighty . . . external HD connected to FW . . . I'll have to look into this further.  But, did you "install" the system?  Or, you just have the .iso moved to an external HD partition and use GRUB to boot?  Does the iso have to be the only item in the partition?  Or can it be loaded in with other items?  Any keys to use on boot?  Like the option key?

These kind of questions,

e.e.p.

---

### Post by abtabt on 2014-12-18
no install 
if you look in [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

about Persistent Live USB then you can see how to (in my case i use Firewire disk)

you can start with c key or alt key  or open firmware its like DVD but you save all you 
do and can edit yaboot config etc 

about if you can mix with other stuff, yes you can but ........

read How_do_I_boot_from_a_USB and you see diff way to do 

but Persistent Live USB/FIREWIRE/HD install works very well

---

### Post by este.el.paz on 2014-12-18
> **abtabt said:**
> no install 
if you look in [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

about Persistent Live USB then you can see how to (in my case i use Firewire disk)
you can start with c key or alt key  or open firmware its like DVD but you save all you 
do and can edit yaboot config etc 
about if you can mix with other stuff, yes you can but ........
read How_do_I_boot_from_a_USB and you see diff way to do 

but Persistent Live USB/FIREWIRE/HD install works very well

@abtabt:

Thanks for the followup . . . I will read it, but, w/o reading it yet, I'm getting the idea that it would be similar to making a bootable USB drive . . . but, on an ext HD???

I'll check it out . . . appreciate it . . . .

e.e.p.

---

### Post by rsavage on 2014-12-22
> **este.el.paz said:**
> 

I think when I first tried 14.10 this desktop frozen thing was happening, or possibly it was with 14.04 . . . possibly fixed with an xorg.conf file, but question would be whether this MATE system is requiring more than the iBook has to deliver??

e.e.p.

Well it was compiled and built on a machine with 512MB, so unless you have less than that, then no.

---

### Post by este.el.paz on 2014-12-22
> **rsavage said:**
> Well it was compiled and built on a machine with 512MB, so unless you have less than that, then no.

@rsavage:

Thanks for the reply, OK, I think I have 540MB on my iBook, but my question was from the "frozen" desktop issues in spite of using the "agp.mode" boot params and usually the Live versions have been pretty good . . . only after install has it been when the problems "show up."  

I think after I work on "sound" I'm going to try to figure out abtabt's suggestion to use persistent live install on a FW ext HD and play around with MATE that way . . . before trying an install.  Traditionally my PPC's have "liked" XFCE and/or Xubuntu . . . and not so much straight Ubuntu . . . .  But, I do like MATE . . . .
e.e.p.

---

