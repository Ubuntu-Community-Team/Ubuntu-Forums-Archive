---
title: "Enjoying Fedora 18"
date: 2013-01-21
forum: Any Other OS
---

### Post by BBQdave on 2013-01-21
Hello All,

If there is interest in trying out F18, I offer a couple of tips :)

The Live image does not allow you to set host name at install, so you will need to use this command after install:
hostnamectl set-hostname *newhost.newdomain* --static

The Full DVD image or Network Install image allows you to set host name.

The new anaconda is set up as a *hub and spoke* approach for install, more info here: [I][http://fedoraproject.org/wiki/Anaconda/NewInstaller](http://fedoraproject.org/wiki/Anaconda/NewInstaller)

[/I]After install, F18 is smooth and stable :D

---

### Post by BBQdave on 2013-01-27
A follow up recommendation:

The Live media needs a DVD size burn, so if you do not need the Live experience and wish to do a direct install, I would go with the DVD install media.

The Fedora 18 Net and DVD install media give you more choices, and is the full - complete New Anaconda :)

---

### Post by ACubed10 on 2013-01-27
Hmmm I've been visiting the fedora site but cannot bring myself to hit download. Still using it? Like it better than Ubuntu?

---

### Post by r-senior on 2013-01-28
I have occasional forays into Fedora and I like it. In fact, after upgrading my laptop from 12.04 to 12.10 last night and having intermittent boot problems, it might be time for a few months of Fedora on the laptop again.

Good things about Fedora are that things are nicely up to date and it feels quite clean and lightweight in comparison to Ubuntu. I get on OK with Gnome shell. Fedora is easy to install and set-up, perhaps a little more awkward than Ubuntu for certain things but not an order of magnitude more difficult. It's not the "expert" distribution that some people would have you believe.

Because it has a stronger FOSS policy, you need to tap into a third party repository for non-free stuff. I also find the font rendering poor (but it can be changed to match Ubuntu). Package management is not really that much different, although the lack of an equivalent of "apt-get autoremove" feels like an omission. It doesn't seem to bother long-term Fedora users.

Fedora forums are OK, not as busy as the Ubuntu forums. They don't have an equivalent of the Ubuntu code of conduct so there's a bit of Canonical and Microsoft bashing that goes on. The moderators can also be a bit heavy handed IMO -- but maybe I was just unlucky to see a whole bunch of people get banned in the few days after I joined.

I tend to come back to Ubuntu eventually. You should give it a try, maybe in a VM first or as a dual boot or on a second machine.

---

### Post by offgridguy on 2013-01-28
I have been considering fedora 18, not sure now after reading the previous post, also on
the consideration list, Manjaro,Cinnarch and Linux Mint 14.

---

### Post by ACubed10 on 2013-01-28
> **r-senior said:**
> I have occasional forays into Fedora and I like it. In fact, after upgrading my laptop from 12.04 to 12.10 last night and having intermittent boot problems, it might be time for a few months of Fedora on the laptop again.

Good things about Fedora are that things are nicely up to date and it feels quite clean and lightweight in comparison to Ubuntu. I get on OK with Gnome shell. Fedora is easy to install and set-up, perhaps a little more awkward than Ubuntu for certain things but not an order of magnitude more difficult. It's not the "expert" distribution that some people would have you believe.

Because it has a stronger FOSS policy, you need to tap into a third party repository for non-free stuff. I also find the font rendering poor (but it can be changed to match Ubuntu). Package management is not really that much different, although the lack of an equivalent of "apt-get autoremove" feels like an omission. It doesn't seem to bother long-term Fedora users.

Fedora forums are OK, not as busy as the Ubuntu forums. They don't have an equivalent of the Ubuntu code of conduct so there's a bit of Canonical and Microsoft bashing that goes on. The moderators can also be a bit heavy handed IMO -- but maybe I was just unlucky to see a whole bunch of people get banned in the few days after I joined.

I tend to come back to Ubuntu eventually. You should give it a try, maybe in a VM first or as a dual boot or on a second machine.

yeah I remember trying Fedora 9? I think.  The Fedora forums were very dry.  The forums here seem to be a lot better.  People who generally just love the operating system and not wanting to flame you for questions.  I tend to visit daily.  Had my old account closed this last week so that is why I have a join date of 2013 and only 15 posts lol.  I've been a member here since 2006

---

### Post by offgridguy on 2013-01-28
I do have a question about fedora, being it is a rolling release, will it work straightaway
or is it like sabayon where you have to download all the updates first?

---

### Post by r-senior on 2013-01-28
Fedora 18 isn't a rolling release, it's the successor to Fedora 17. It will have outstanding updates if you install from a live image but it works without these.

---

### Post by offgridguy on 2013-01-28
> **r-senior said:**
> Fedora 18 isn't a rolling release, it's the successor to Fedora 17. It will have outstanding updates if you install from a live image but it works without these.
Thank you, just returned from the public library, couldn't find 
where to download fedora, is it a free download?  Appreciate a link. Couldn't download cinnarch or mint, so downloaded Lubuntu
and Manjaro. Using Lubuntu at the moment.

---

### Post by r-senior on 2013-01-28
Information and downloads from the Fedora Project pages:

[http://fedoraproject.org/en/get-fedora-options](http://fedoraproject.org/en/get-fedora-options)

Or, if you want to be nice to their servers:

[http://torrent.fedoraproject.org/](http://torrent.fedoraproject.org/)

---

### Post by offgridguy on 2013-01-28
> **r-senior said:**
> Information and downloads from the Fedora Project pages:

[http://fedoraproject.org/en/get-fedora-options](http://fedoraproject.org/en/get-fedora-options)

Or, if you want to be nice to their servers:

[http://torrent.fedoraproject.org/](http://torrent.fedoraproject.org/)
Thank you for the link's.:D

---

### Post by monkeybrain2012 on 2013-01-28
I dual boot Fedora with Ubuntu. My F17 install has been quite solid, not sure I want to update to F18 at this point given what I have been reading about it so far, but thanks for the tips. Probably will update in a few months after a few waves of bug fixes.

---

### Post by AdamWill on 2013-01-28
> **monkeybrain2012 said:**
> I dual boot Fedora with Ubuntu. My F17 install has been quite solid, not sure I want to update to F18 at this point given what I have been reading about it so far, but thanks for the tips. Probably will update in a few months after a few waves of bug fixes.

Most of the problems people have had with F18 are in the installer, which isn't really surprising as it's effectively a ground-up rewrite. F18 itself is a pretty decent release, I'm not aware of any major screwups in there.

The new upgrade tool is new code as well and does have some known issues, but frankly, so did the old ones, so you've probably got about as much chance of a successful upgrade as you ever did :P If you have multiple encrypted partitions it's known to be buggy, I think, but most people get something that works.

---

### Post by AdamWill on 2013-01-28
> **BBQdave said:**
> A follow up recommendation:

The Live media needs a DVD size burn, so if you do not need the Live experience and wish to do a direct install, I would go with the DVD install media.

The Fedora 18 Net and DVD install media give you more choices, and is the full - complete New Anaconda :)

It's not DVD sized, it's just gone up from 700MB target to 1GB (I think Ubuntu did something similar recently in fact). So you can write it to a 1GB, 2GB or 4GB USB stick, for instance.

---

### Post by ACubed10 on 2013-01-28
> **AdamWill said:**
> It's not DVD sized, it's just gone up from 700MB target to 1GB (I think Ubuntu did something similar recently in fact). So you can write it to a 1GB, 2GB or 4GB USB stick, for instance.
yeah that's the first thing I noticed when I went to download F18.  Decided against it.  I'll keep reading updates on fixes to make sure everything is good to go before trying it in a virtual

---

### Post by UltimateCat on 2013-01-28
> **offgridguy said:**
> I have been considering fedora 18, not sure now after reading the previous post, also on
the consideration list, Manjaro,Cinnarch and Linux Mint 14.

Think you'll like Linux Mint. I know a few folks that run Mint and they are happy.

I'm still running Fedora 17 and it is still running stable.....just waiting a little bit longer for the fresh install of FC18.

---

### Post by BBQdave on 2013-01-29
> **AdamWill said:**
> It's not DVD sized, it's just gone up from 700MB target to 1GB (I think Ubuntu did something similar recently in fact). So you can write it to a 1GB, 2GB or 4GB USB stick, for instance.

Hey AdamW :)

Ya, I just meant that if you are going to burn a dvd - and do not need the live experience - go for the **full** dvd. Though the Live iso may be the way to go, so one can check out the DE before install.

And I am still happily cruising along with F18 Gnome 3 - no bugs that I am aware of - smooth and stable :D

---

### Post by offgridguy on 2013-01-29
> **UltimateCat said:**
> Think you'll like Linux Mint. I know a few folks that run Mint and they are happy.

I'm still running Fedora 17 and it is still running stable.....just waiting a little bit longer for the fresh install of FC18. Thanks for the vote of confidence,i checked distrowatch, couldn't find a site where i can get a download?

---

### Post by r-senior on 2013-01-29
All versions available through the Fedora Project site ...

[http://archive.fedoraproject.org/pub/fedora/linux/releases/](http://archive.fedoraproject.org/pub/fedora/linux/releases/)

Really old stuff under the archive directory ...

[http://archive.fedoraproject.org/pub/archive/fedora/linux/releases/](http://archive.fedoraproject.org/pub/archive/fedora/linux/releases/)

---

### Post by AdamWill on 2013-01-30
The F17 torrents are also still listed on the torrent page: [http://torrent.fedoraproject.org/](http://torrent.fedoraproject.org/)

acubed10: most of the wackiness in f18 is in anaconda, and that's not going to change, because we can't issue updates for the installer, really. Well, we _can_ provide updates.img files for specific bugs that really cause people pain, but it's not a method that scales very far, and we don't do image respins. More or less, the installer you get at release time is the one that release is stuck with forever.

Outside of the installer, the rest of f18 is pretty solid already, I think the general consensus runs. So I don't think waiting is gonna accomplish much when it comes to 18 - either decide you're going to read all the docs and figure out the installer and go for it (or upgrade with fedup or yum), or hold off for f19, are the basic options, I'd say.

---

### Post by buzzingrobot on 2013-01-30
My recommendation for someone wanting to install Fedora 18, or any distribution that uses an installer they have no experience with, is to devote the first one or two installs to practice.  If they work, great.  But, if not, it's probably operator error, so figure out what went wrong and try again.

Granted, if you are trying to preserve existing data/partitions, you can't do that.  But, you can take it as far as committing the partitions before you back off.

If you just need to devote all of your one and only drive to Fedora, the new installer should be very easy.

Also, with the network install and, I think, the DVD install, you can choose between Gnome 3, KDE, Cinnamon, and XFCE (maybe a couple others). MATE's available in the repositories, but you need to do the install first.

---

### Post by BBQdave on 2013-01-31
> **BBQdave said:**
> ...no bugs that I am aware of...

Check that, a minor bug with search and gedit crashing. When selecting a file, through search - gedit crashes. Overall nothing too crazy, but I have down shifted to F17 Gnome 3.4.2 for my production machine. I will hang with F17 until EOL, and then load F19 :)

---

### Post by AdamWill on 2013-02-01
> **buzzingrobot said:**
> My recommendation for someone wanting to install Fedora 18, or any distribution that uses an installer they have no experience with, is to devote the first one or two installs to practice.  If they work, great.  But, if not, it's probably operator error, so figure out what went wrong and try again.

Granted, if you are trying to preserve existing data/partitions, you can't do that.  But, you can take it as far as committing the partitions before you back off.

If you just need to devote all of your one and only drive to Fedora, the new installer should be very easy.

Also, with the network install and, I think, the DVD install, you can choose between Gnome 3, KDE, Cinnamon, and XFCE (maybe a couple others). MATE's available in the repositories, but you need to do the install first.

That's not bad advice. MATE is available from the installer if you use the netinst image, just not if you use the DVD.

---

### Post by cg40k on 2013-02-01
Recently tried out F18, and honestly I can just switch Ubuntu to Gnome3 desktop environment and get the same feeling.

Still, not a bad distro by any means, its nice that rpmfusion is in there now.

---

### Post by offgridguy on 2013-02-01
I saw this in their advertisement page.

> Desktop: Have you ever tried to use a new printer and been frustrated by error messages and having to hunt for the correct driver to install? With the new easy printing feature in Fedora 14, plug your printer in and Fedora automatically finds and installs the correct driver. This feature allows you to print in many different locations and churn out copies within minutes. It's one of several innovations in Fedora 14 that let you take better advantage of your system's hardware. 

I would be real interested to know if this actually works, as 
installing drivers for my Brother Printer is a struggle. BTW this ad was in reference to fedora 17. on ebay.

Anyway my interest is enough that i have ordered the fedora 17 install CD from
ebay, along with linux mint 14.

---

### Post by BBQdave on 2013-02-05
OK, it is a week away from F16 going *end of life* and F18 is one month old...

So I installed F18 Gnome 3 - 64bit, and I am amazed at the smoothness and no bugs :)

Everything in F18 is working great; and I tested for some of the minor bugs that I encountered with F18 when it was first released - everything fixed.

So again, if you are interested in trying Fedora, I would wait roughly a month after release - to install. If you are looking for long term support, 13 months is what you get with Fedora. No worries installing the latest release when your current Fedora goes EOL - as one month smooths out the new release :)

The other pleasant surprise with F18: I plugged in my printer, and F18 auto configured it. That's a *FIRST* for me and Linux - plugged in printer and then hit print on my document... and I have a printed document :)

---

### Post by nkbielst on 2013-02-05
I traded off Ubuntu 12.04 and Fedora 17 for quite a while...I considered the two about equal in stability, with F17 being a bit faster/more responsive.

Ubuntu 12.10 was not stable on my machine (not sure why). So I waited patiently for F18. The new features are really nice. This is the first distro that could connect to my exchange server during a live session. Quite impressed.

---

### Post by Sam Mills on 2013-02-06
Anyone thinking of trying Fedora must keep in mind that it was never meant to be a rock solid stable distro to begin with. It exists for Red Hat. It is a testing ground for new ideas that *might* be included into Red Hat in the future.

But if you love tinkering and trying cutting edge software, Fedora is a decent choice.

---

### Post by iamkuriouspurpleoranj on 2013-02-07
Did the F18 netinstall today to have a pure MATE untouched by Gnomish hands.

Took forever to complete but then I usually go out and build a house during the initial Fedora system update. So that was no shock.

F18 is really nice with MATE. It has a proper Gnome 2 layout, not a stylised version as you see with some distros running MATE. That's not a complaint. I just wanted Fedora w/ MATE to look like CentOS/RHEL. And it does. In fact, I'm currently also running Scientific Linux and now I've pimped them both up in the same way, it's hard to tell the difference.

Anyone concerned that some software e.g. XMind doesn't have an rpm version should check out "alien". Unfortunately, alien is not available in Fedora (officially) so what you can do is build the rpms in Ubuntu and copy them across. Or maybe I could take the deb package for alien and transform that to an rpm. Will investigate.

Fedora is a great distro but it takes some work to make it 100% fun-friendly if (like me) you don't want to use the third party Easy-Life service. 

Anaconda the installer still confuses me. I'm not scared of many things in Linux but I am scared of Anaconda. Note that it works best i.e. less confusingly if you have already made space on your hard drive. If it will be the only OS and you are happy to take the defaults, then it will also be easy.

Gnome 2 is the past but then so are vinyl records.

---

### Post by BBQdave on 2013-02-07
> **Sam Mills said:**
> Anyone thinking of trying Fedora must keep in mind that it was never meant to be a rock solid stable distro to begin with.

I've tested many Linux distros... the two most rock solid distros are **Debian** and **Fedora**.

Not sure why people tag Fedora as bleeding edge? Fedora has *Rawhide - bleeding edge*; and Debian has *Sid - bleeding edge*. Debian with backports is nice, but equally as nice is Fedora. There is definitely more up to date software in Fedora, which some may equate to fast change.

There is a reason **Fedora** and **Debian** are the cores to so many Linux distros... rock solid stability :)

---

### Post by BBQdave on 2013-02-07
> **iamkuriouspurpleoranj said:**
> Did the F18 netinstall today...

I have a fast internet connection... Really like the F18 Net Install CD :)

Lots of install configuration choices; and again with the new *hub and spoke* approach to Anaconda - *reclaim* partitions and choose *standard* or *lvm* for drive set up.

---

### Post by monkeybrain2012 on 2013-05-12
Well a little bit late to the party, finally removed Fedora 17 and did a clean install of Fedora 18 with KDE this time. It is really nice and installation is a lot faster than Ubuntu. Only thing is that the installer overwrote grub in Ubuntu (it is a dual boot) even though I have chosen not to install bootloader (I re-did the installation just to be sure),  but it was easily fixed. The default software manager apper kind of sucks so installed yumex and everything is cool. :)

---

### Post by buzzingrobot on 2013-05-13
FWIW, I've spent 24 hours or so with a Fedora 19 alpha install, using MATE and Gnome-Shell. Other than one new Gnome extension that brought it to its knees, I've seen no crashes. (They must be in there, hiding, though.)  Other than the software updates, it looks much like F18.  But, MATE 1.6 is smoother and faster than the 1.5 release available on F18.  Gnome also seems smoother and faster.  That's not bad for a beta test candidate. Anaconda is much less obtuse, too. 

After installing the Infinality package, font rendering is excellent. 

F18 is a very good release, and F19 looks to be at least as good.  Wonder if these two releases will be the basis for Red Hat Enterprise Linux 7, expected later this year?  An RHEL 7 defaulting to Gnome 3.8, with Cinnamon, MATE, etc., available, would be intriguing desktop possibility.

---

### Post by BBQdave on 2013-05-14
> **buzzingrobot said:**
> After installing the Infinality package, font rendering is excellent.

Hold off updating Infinality - see [**Warning**]("http://www.infinality.net/blog/")

Still cruising along with F18 and Gnome 3.6.3 :)

---

### Post by AdamWill on 2013-05-28
buzzingrobot: we don't talk about what Fedora release a given RHEL is 'based on' (in fact the relationship is somewhat more complex than that in any case) but you will certainly see a lot of the stuff you saw first in Fedoras 15 through 19 in RHEL 7 as well, yes.

RHEL has a much more limited package set than Fedora, though, and this is not expected to change. I don't believe RHEL 7 will include any official alternative desktops, and it'd be extremely unlikely to officially include Cinnamon or MATE or anything like that. Alternative desktops are often made available through the popular 'extra' repositories for RHEL, though.

---

### Post by TNFrank on 2013-06-14
I'm giving F18 a test drive right now as I type this. Looks pretty decent but I'm not giving up my Ubuntu 12.04 anytime soon.  I'll just run F18 from a USB disk as a second Op System OR if I can ever get a hard drive enclosure for my old Mac hard drive I'll install it there and let it be kind of a second machine. 
 One nice thing, F18 found my WiFi quickly which is nice.  Looks like I've got 4 Linux based Op Systems that I like now, Ubuntu, Peppermint One, Tiny CorePlus and now Fedora. 
Linux Rocks.:guitar:

---

### Post by BBQdave on 2013-06-14
> **TNFrank said:**
> I'm giving F18 a test drive right now as I type this. Looks pretty decent but I'm not giving up my Ubuntu 12.04 anytime soon.

Was cruising along happily with F18 and Gnome 3... until Spring updates, new Kernel Linux, and a crippled Toshiba Satellite notebook. The **Kernel Linux 3.9.2-200.fc18.x86_64** and up is causing different problems on varying hardware. Well over a month and still no fix.

I am currently using and enjoying :) Ubuntu Unity 12.04LTS for my daily driver. I like the flow of Unity with the *side bar*, *Dash*, and *global menus* - and it is nice to have a desktop populated with folders and files :D

Back to **LTS** - as my old hardware had Ubuntu 10.04 and Debian 6. Over a year ago I updated to new hardware, and tested different Linux distros. For me, LTS makes for a solid daily driver and I too will be hanging with Ubuntu 12.04 :D

---

### Post by TNFrank on 2013-06-14
One "problem" with Fedora 18 that I ran into(as have others) is that it'll not let you log in to Terminal as "sudo" to do stuff.
Ubuntu has spoiled me, it's such an easy op system to use.  Don't see myself going to any other op sys anytime soon.

---

### Post by monkeybrain2012 on 2013-06-14
> **TNFrank said:**
> One "problem" with Fedora 18 that I ran into(as have others) is that it'll not let you log in to Terminal as "sudo" to do stuff.
Ubuntu has spoiled me, it's such an easy op system to use.  Don't see myself going to any other op sys anytime soon.

[http://www.mjmwired.net/resources/mjm-fedora-fc6.html#sudo](http://www.mjmwired.net/resources/mjm-fedora-fc6.html#sudo)

I never needed to set it up like that though, during installation (or first boot?)  I added myself as an administrator and sudo just works. Though I noticed that with Fedora there are things that even sudoer cannot do like cd-ing the root folder, for that you have to actually become root (su) But root cannot use graphic text editors like kwrite or gedit, so have to use something cryptic like nano or vi.

Also I disabled Selinux or set it to permissive mode, it is like an overly active imune system that doesn't allow you to do anything. Google talk cannot start and freezes the browser whenever I logged into gmail because Selinux prevents it and there are numerous other things that it prevents.  I know it is probably more desirable to explictly permit something but I haven't got the time to read the rather complicated documentations right now. I am not James Bond and don't need that level of security.[IMG]http://ubuntuforums.org/images/smilies/icon_razz.gif[/IMG]

Oh yeah, synaptic (muon) is another thing I miss from Debian based systems. I use Fedora in kde, packagekit is atrocious and I removed it and use Yumex instead. It is a lot better but still no match for synaptic or muon. Searching is painful and updating takes long.

Speaking of ease of use, in Ubuntu you don't need to think twice to install the Nvidia driver, well in Fedora you need to disable nouveau and separately install the driver and akmod. The first time I installed the driver I forgot to disable nouveau and couldn't boot (In Ubuntu when the Nividia driver loads it disable nouveau automatically) Then there was a mismatch in akmod and driver version in an update and it hanged while booting. Took a few hours to fix it.

---

### Post by monkeybrain2012 on 2013-06-14
> **BBQdave said:**
> Was cruising along happily with F18 and Gnome 3... until Spring updates, new Kernel Linux, and a crippled Toshiba Satellite notebook. The **Kernel Linux 3.9.2-200.fc18.x86_64** and up is causing different problems on varying hardware. Well over a month and still no fix.



Couldn't you just log into a previous kernel? I think Fedora automatically keeps the two previous kernels and you have to remove them manually from the terminal (don't show up in  gui package managers like Yumex)

---

### Post by buzzingrobot on 2013-06-14
> **monkeybrain2012 said:**
> 
Speaking of ease of use, in Ubuntu you don't need to think twice to install the Nvidia driver, well in Fedora you need to disable nouveau and separately install the driver and akmod. The first time I installed the driver I forgot to disable nouveau and couldn't boot (In Ubuntu when the Nividia driver loads it disable nouveau automatically) Then there was a mismatch in akmod and driver version in an update and it hanged while booting. Took a few hours to fix it.

I've never needed to manually blacklist Nouveau in Fedora. I enable the RPMFusion repos, do a "sudo yum install akmod-nvidia", and that's it.  The instructions at RPMFusion's howto section are thorough and accurate.

---

### Post by monkeybrain2012 on 2013-06-14
> **buzzingrobot said:**
> I've never needed to manually blacklist Nouveau in Fedora. I enable the RPMFusion repos, do a "sudo yum install akmod-nvidia", and that's it.  The instructions at RPMFusion's howto section are thorough and accurate.

Well I installed from rpm-fusion-rawhide which has a more up to date driver (Nvidia 319.23) , with just rpm-fusion I think you only get 303. The performance is a lot better, maybe it is only in rawhide that you need to disable nouveau.

---

### Post by BBQdave on 2013-06-15
> **monkeybrain2012 said:**
> Couldn't you just log into a previous kernel? I think Fedora automatically keeps the two previous kernels and you have to remove them manually from the terminal (don't show up in  gui package managers like Yumex)

Yes, you can log into a previous Kernel Linux for awhile - but over time with current updates and the older kernel, things start to get buggy. So you end up in the same situation of buggy function - running off of an older kernel with an updated Fedora system :(

Oddly, Spring does not seem to be good with Fedora and stability. Had the same issues last Spring with F16 crippling my hardware and the soon to be released F17 was buggy. Here I am again with F18 crippling my hardware and when I tested F19 beta - same buggy crippling behavior.

I need stability in a Linux distro, and thought I could get that in Fedora - waiting a couple months after release to install... sadly, whatever they are testing in the beta, seems to be tested in the current release as well. So in my experience, Fedora really is a test bed for RHEL.

No worries, I have stability in a smooth Ubuntu Unity 12.04LTS system :D

---

### Post by monkeybrain2012 on 2013-06-15
> **BBQdave said:**
> 
I need stability in a Linux distro, and thought I could get that in Fedora - waiting a couple months after release to install... sadly, whatever they are testing in the beta, seems to be tested in the current release as well. So in my experience, Fedora really is a test bed for RHEL.

No worries, I have stability in a smooth Ubuntu Unity 12.04LTS system :D

But then since Ubuntu is going sort of rolling, I would rather they test like Fedora than Debian unstable.  As far as beta testing goes, Fedora is still quite stable and usable for the most part. On the other hand I almost get dependency conflicts on a daily basis with Debian unstable.

---

### Post by AdamWill on 2013-06-27
> **TNFrank said:**
> One "problem" with Fedora 18 that I ran into(as have others) is that it'll not let you log in to Terminal as "sudo" to do stuff.
Ubuntu has spoiled me, it's such an easy op system to use.  Don't see myself going to any other op sys anytime soon.

As monkeybrain said, if you create a user as an 'administrator' in Fedora (all the user creation tools should have this option, except gnome-initial-setup, which *always* creates the user as an administrator) then sudo will be enabled for that user. If you don't, it won't.

---

