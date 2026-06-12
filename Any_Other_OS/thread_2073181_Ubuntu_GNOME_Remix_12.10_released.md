---
title: "Ubuntu GNOME Remix 12.10 released"
date: 2012-10-19
forum: Any Other OS
---

### Post by kansasnoob on 2012-10-19
I began to follow this project during Quantal development and you may find some useful notes here:

[http://ubuntuforums.org/showthread.php?t=2064293](http://ubuntuforums.org/showthread.php?t=2064293)

This project should not be confused with [UGR]("http://ugr.teampr0xy.net/"), [Ubuntu GNOME Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/"), or any other project.

The differences are stark, as the release notes say, "***The Ubuntu GNOME Remix is a mostly pure GNOME desktop experience built from the Ubuntu repositories***." That's right, Jeremy Bicha and the rest of the development team have worked with the Ubuntu devs to the extent that all *needed* packages are available in the repos :)

Basic project info is available here:

[https://launchpad.net/~ubuntu-gnome](https://launchpad.net/~ubuntu-gnome)

I highly recommend joining the team and subscribing to the [mailing list]("https://lists.launchpad.net/ubuntu-gnome/") if you are truly interested in the project. There is also an IRC channel for discussions and questions regarding the development of Ubuntu GNOME Remix:

> #ubuntu-gnome

So, on to the Release Notes which you really should read:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

Therein you'll find the download links, including torrents and md5sums, along with a list of known issues, etc. The package manifests are available here:

[http://bicha.net/ubuntu-gnome-remix/](http://bicha.net/ubuntu-gnome-remix/)

***********************

Now, my personal opinion and interpretation of the project based on my limited understanding and abilities;

# The project is needed so the Ubuntu devs and Gnome devs can work together efficiently on shared interests w/o breaking each others work. While you can actually just install the proper 'ubuntu-gnome' meta-packages from the repos many of the default Ubuntu/Unity settings are incompatible with a pure Gnome DE.

# When Jeremy says "pure Gnome" he means it! Where ever possible the project uses the default Gnome packages such as 'gdm' rather than 'lightdm', 'abiword' rather than 'libreoffice-writer', 'epiphany-browser' rather than 'firefox', etc, etc. Of course you can install whatever packages you wish from the repos.

# While many users focus solely on desktop environment (Unity vs. Gnome Shell vs. Gnome Classic) an even more important consideration is what window manager is in use. Beginning with 12.10 Ubuntu dropped Unity-2D which used Metacity in favor of using Unity with Compiz + llvmpipe. While this may be fine for some users there are a number of graphics chips that simply don't play well with Compiz, even with the new magic :(

OTOH Gnome, and specifically this remix, uses Mutter which is the clutter-based evolution of Metacity. In fact Compiz is not even installed by default in this remix so only the default Gnome Shell and Gnome classic (no effects) sessions work out-of-box after installation. Compiz (and presumably CCSM) must be installed from the repos to use standard Gnome classic.

# I have a personal desire to keep Metacity and 'gnome-panel' alive because it's simple, lightweight, and *just works*. It's not an absolute need because Lubuntu is a very reasonable replacement, but if you want something why not try to keep it alive ;)

I really can't think of anything else to add ATM but I'll subscribe to this thread and try to help when and where possible. Just remember that my primary focus is on Gnome classic (no effects) so I can't answer much regarding the default Gnome Shell DE, sorry :redface:

WebUpd8 has some pretty great screenshots and a video posted here:

[http://www.webupd8.org/2012/10/prefer-gnome-shell-download-ubuntu.html](http://www.webupd8.org/2012/10/prefer-gnome-shell-download-ubuntu.html)

---

### Post by x-shaney-x on 2012-10-19
Cannot even get it to boot up.
Tried downloading the torrent then the iso proper and both times I get an error on boot (which I have now forgotten) so doesn't even start up.

Burned with Startup Disk Creator.

---

### Post by jerrrys on 2012-10-19
"***The Ubuntu GNOME Remix is a mostly pure GNOME desktop experience built from the Ubuntu repositories***."

Its in the repositories yet its in the other OS/Distro Talk forum  :confused:

---

### Post by kansasnoob on 2012-10-19
> **x-shaney-x said:**
> Cannot even get it to boot up.
Tried downloading the torrent then the iso proper and both times I get an error on boot (which I have now forgotten) so doesn't even start up.

Burned with Startup Disk Creator.

I've only tested the i386 version and only with a burn-once DVD which worked really well for me so I suspect it's something to do with Startup Disk Creator :confused:

---

### Post by kansasnoob on 2012-10-19
> **jerrrys said:**
> "***The Ubuntu GNOME Remix is a mostly pure GNOME desktop experience built from the Ubuntu repositories***."

Its in the repositories yet its in the other OS/Distro Talk forum  :confused:

In deed, I struggled with that decision. Where do you think would be more appropriate?

I could ask one of the mods to move it :)

---

### Post by kansasnoob on 2012-10-19
> **kansasnoob said:**
> I've only tested the i386 version and only with a burn-once DVD which worked really well for me so I suspect it's something to do with Startup Disk Creator :confused:

Follow up on that :redface:

I checked my Beta thread and that was also the first question there (look at post #2 and onward):

[http://ubuntuforums.org/showthread.php?t=2064293](http://ubuntuforums.org/showthread.php?t=2064293)

Some day I need to invest in a few more flash drives :)

---

### Post by jerrrys on 2012-10-19
> **kansasnoob said:**
> In deed, I struggled with that decision. Where do you think would be more appropriate?

I could ask one of the mods to move it :)

Now that its official we need a Gnome forum  :)

---

### Post by kansasnoob on 2012-10-19
> **jerrrys said:**
> Now that its official we need a Gnome forum  :)

Well, I think it would be best to think of it as "semi-official". The goal is to become a full fledged Ubuntu flavor but there are still some hoops to jump through.

We can't permanently use the name "Ubuntu GNOME Remix", that's just a transitional name that represents the meta-packages available in the repos.

One of the greatest obstacles is developing a QA team. I helped a little with that when Lubuntu was new but I just don't have the stamina anymore due to age and illness :(

---

### Post by x-shaney-x on 2012-10-19
> **kansasnoob said:**
> I've only tested the i386 version and only with a burn-once DVD which worked really well for me so I suspect it's something to do with Startup Disk Creator :confused:

Tried unetbootin and worked fine and now installed to hard drive so definitely a Startup Disk Creator problem.

---

### Post by jerrrys on 2012-10-19
> **kansasnoob said:**
> One of the greatest obstacles is developing a QA team. I helped a little with that when Lubuntu was new but I just don't have the stamina anymore due to age and illness :(

I hear you.  I have the age thing going on too.  Makes me wonder if part-time help is of any use in gnome related projects.

---

### Post by kansasnoob on 2012-10-19
> **x-shaney-x said:**
> Tried unetbootin and worked fine and now installed to hard drive so definitely a Startup Disk Creator problem.

Thanks for letting us know :)

---

### Post by kansasnoob on 2012-10-19
> **jerrrys said:**
> I hear you.  I have the age thing going on too.  Makes me wonder if part-time help is of any use in gnome related projects.

My thought is that it's always worthwhile to do what you want to do, but only as much as you're comfortable doing.

I'm finding it easier all the time to just say, "I can't, won't, and have no inclination to do that!"

But I still believe that even the smallest contribution is always appreciated by someone :)

---

### Post by Ichtyandr on 2012-10-20
Ubuntu's startup disk creator worked fine on precise in my case.
The new spin is pure awesomeness, especially with [gnome3 team ppa]("https://launchpad.net/~gnome3-team/+archive/gnome3")  
I am affected by this [bug that does not show keyboard layouts]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914/") though

---

### Post by x-shaney-x on 2012-10-20
Been playing around with this past couple of days and things going really well.
Especially now the "Dash to Dock" gnome extension has been updated to work 3.6 (provides an intellihide dock. Yes, dodge!!).

However, I am finding I am missing one thing from Unity (and only one thing) - Global Menu!

Of all things, something I hated at first but after using it for so long, going over to shell has reminded me just how ugly window menus look.
The new nautilus and web etc are a step in the right direction but still a lot of apps to catch up :(

---

### Post by MikeCyber on 2012-10-21
Does FXAA within Nvidia settings work in the remix? I need it for Flightgear.

---

### Post by Ajay Chahar on 2012-10-21
Can people leave feedback on how this remix is treating them? Thanks!

---

### Post by PaulW2U on 2012-10-21
I'm actually in the process of converting my test Ubuntu/Unity installation into an Ubuntu GNOME Remix installation. I've removed most of the Unity files and added ubuntu-gnome-desktop.

I've also added Gnome 3 PPA so I'm not sure what I've got that isn't in the standard release but I love the new login screen. Everything seems a little more polished than when I last used Gnome Shell but may be that's the due to the upgrade from Gnome 3.4 to 3.6.

Very pleased with what I now have installed.

---

### Post by Ichtyandr on 2012-10-21
It is quite great actually. Probably the desktop experience that is most unique and coherent, and does not copy from anyone else. Do add the ppa for parts of the latest gnome that were not included in Ubuntu for the full picture. It behaves great with nouveau drivers. It is actually much smoother than Unity according to subjective experience on both my desktop and netbook.

I had to install firefox, thunderbird and libreoffice though, and I am not sure whether it is easier to install regular Ubuntu and then put gnome-shell, or install ubuntu gnome desktop and then add all these programs.

It is a great distro/spin and I apreciate all the work put into it!

---

### Post by neu5eeCh on 2012-10-21
I've been using this distro in my dedicated distro-hopping partition and am impressed with it. It's quite smooth and I prefer it to Unity (mainly because I detest the launcher, am unimpressed by the dash and don't like the global menu). 

My biggest problem with Gnome Shell (and it's really trivial) is that I can't shade windows using the mouse scroll button. You wouldn't think this would be a deal breaker, but it is. I also don't like indicator applets being forced to the bottom of the screen - makes applets like RadioTray much more inconvenient to use. If anyone knows of any Gnome Extensions that can remedy these items, let me know.

I remain interested in the new Pear OS and Luna.

---

### Post by x-shaney-x on 2012-10-21
Gnome tweak tool has options to toggle shade on user selected clicks (left, right or middle button), not sure if it can do it on scroll though.

There is an extension that can put tray icons back on the top panel: [https://extensions.gnome.org/extension/495/topicons/](https://extensions.gnome.org/extension/495/topicons/)

I haven't tried it myself though so can't vouch for it.

---

### Post by kansasnoob on 2012-10-21
> **MikeCyber said:**
> Does FXAA within Nvidia settings work in the remix? I need it for Flightgear.

I wish I had a clue but I don't :cry:

What little I know about graphics could be stored in a thimble :redface:

---

### Post by kansasnoob on 2012-10-21
BTW I'm working on some other projects right now like this one:

[http://ubuntuforums.org/showthread.php?t=2074321](http://ubuntuforums.org/showthread.php?t=2074321)

But if you check the mailing list I did ask if I made any major errors in this notification:

[https://lists.launchpad.net/ubuntu-gnome/](https://lists.launchpad.net/ubuntu-gnome/)

One thing I did not include was this:

> Perhaps one other thing worth mentioning is that all our fixes go back into the ubuntu archives, so they will benefit all users that choose to use gnome shell/classic, even if they dont use the remix! In fact we even fixed a bunch of bugs (with a few more fixes pending) when using lightdm and gnome-shell  together.

So we do have motivated devs :guitar:

---

### Post by neu5eeCh on 2012-10-21
> **x-shaney-x said:**
> Gnome tweak tool has options to toggle shade on user selected clicks (left, right or middle button), not sure if it can do it on scroll though.


Thanks for the other extension. I know about Gnome tweak tool but it doesn't allow the mouse scroll button to shade the windows. Little things like this just drive me nuts. Do the Gnome devs really prefer double clicking on Windows borders? :rolleyes: It must be a trivially easy hack, but no one with the knowhow seems inclined.

---

### Post by buzzingrobot on 2012-10-21
Installed it this evening.  I like it.  Very nice work. Subjectively, I think it's faster than the 12.10 install it replaced. (Unity is looking really good, but that HUD and lens thing don't appeal to me. I'm more in tune with Gnome's aesthetics.)

I installed Synaptic after giving Software I quick try.  I've used it in other distros, so I'll go back for another look.

The "Additional Drivers" in "Software Sources" did not work, repeatedly., when I went after the Nvidia driver.  A progress bar moved a fraction of an inch, then stopped.  I installed the driver with apt-get.  (Believe Additional Drivers is a QT app and comes with a long trail of KDE dependencies, so perhaps it didn't make into this Gnome version. Or, maybe the servers were down tonight. )

The extensions  site is definitely down at the moment, so that will have to wait.



Unless this thing crashes and burns on me, I intend to keep it running at least until Fedora 18 comes out in December (per the current schedule). Then, who knows? :)

---

### Post by Psyael on 2012-10-22
Just wanted to drop a note saying that I've wanted this distro for something close to two years now, so thank you for making it. You might want to edit your README in "What's Not Included" though to include the need to install update-manager if people want the traditional system update. It's how most mainstream Ubuntu users expect to find/install updates.

I'm not sure why it isn't in there, even more traditional GNOME distros like Debian tend to include it and supposedly it is a GNOME package, but I'm not one to raise a fuss.

---

### Post by kansasnoob on 2012-10-22
> **Psyael said:**
> Just wanted to drop a note saying that I've wanted this distro for something close to two years now, so thank you for making it. You might want to edit your README in "What's Not Included" though to **include the need to install update-manager** if people want the traditional system update. It's how most mainstream Ubuntu users expect to find/install updates.

I'm not sure why it isn't in there, even more traditional GNOME distros like Debian tend to include it and supposedly it is a GNOME package, but I'm not one to raise a fuss.

I'd posted a bit about that in the dev forum:

[http://ubuntuforums.org/showthread.php?t=2064749](http://ubuntuforums.org/showthread.php?t=2064749)

Sadly the forum mods made it very hard to search that out :(

---

### Post by MikeCyber on 2012-10-23
You should add the option to install other deskops at install after selecting flash etc. addons alike it's done in FreeBSD or OpenSuse. Also useful would be a rating for gaming etc. Default Unity would 
probably be last in such ratings.
Also nvidia install should be smoother.

This would separate the remix from the default. You have a name for remix already to become official?

---

### Post by Psyael on 2012-10-23
> **kansasnoob said:**
> I'd posted a bit about that in the dev forum:

[http://ubuntuforums.org/showthread.php?t=2064749](http://ubuntuforums.org/showthread.php?t=2064749)

Sadly the forum mods made it very hard to search that out :(

Does this updater automatically check for updates and prompt the user if they wish to install them? The post makes it sound almost like it's just a manual check.

---

### Post by kansasnoob on 2012-10-23
> **Psyael said:**
> Does this updater automatically check for updates and prompt the user if they wish to install them? The post makes it sound almost like it's just a manual check.

I can't answer that definitively because (a) I've tweaked so much stuff in both my Gnome shell and Gnome classic installs that I no longer know what the default Gnome behavior is, and (b) out of habit I always check for updates each day before I start working just so it's out of the way :)

But I want to say yes, in fact not very long ago there was a mid-day security update for Firefox and I got a notification. I think I recall reading at one time that security update notifications are nearly immediate, but standard distribution updates are on a slower interval (like once a week) :confused:

---

### Post by kansasnoob on 2012-10-23
> **MikeCyber said:**
> You should add the option to install other deskops at install after selecting flash etc. addons alike it's done in FreeBSD or OpenSuse. Also useful would be a rating for gaming etc. Default Unity would 
probably be last in such ratings.
Also nvidia install should be smoother.

This would separate the remix from the default. You have a name for remix already to become official?

I seriously doubt that the devs would want to "*add the option to install other deskops at install*" because the greatest purpose of this project is to be as close as possible to a pure Gnome experience, in large part so the Gnome devs and Ubuntu devs can work somewhat more seemlessly without breaking each others work :)

The netboot mini.iso does provide that sort of option via 'tasksel' and uses the familiar Debian text installer. In fact I think the devs are trying to improve the wireless support in the mini.iso since the alternate images have been dropped.

Regarding the name we know that Gnome does not want their full name used in the final product, and I suspect that the name will be decided on by Canonical. My best guess, and it's only a guess, is Gubuntu :)

---

### Post by mips on 2012-10-23
> **kansasnoob said:**
> I seriously doubt that the devs would want to "*add the option to install other deskops at install*" because the greatest purpose of this project is to be as close as possible to a pure Gnome experience, in large part so the Gnome devs and Ubuntu devs can work somewhat more seemlessly without breaking each others work :)

+1 WHy even bother otherwise. Why did you download the is in the first place, to install KDE?

---

### Post by Bart_D on 2012-10-23
> **kansasnoob said:**
> I began to follow this project during Quantal development and you may find some useful notes here:

[http://ubuntuforums.org/showthread.php?t=2064293](http://ubuntuforums.org/showthread.php?t=2064293)

Is there a link with official screenshots of this remix?

---

### Post by neu5eeCh on 2012-10-23
I'm back in Gnome Shell right now. I can't get TopIcons:

[https://extensions.gnome.org/extension/495/topicons/](https://extensions.gnome.org/extension/495/topicons/)

Or Enhanced Dock to work:

[https://extensions.gnome.org/extension/394/enhanced-dock-for-running-programs-and-with-previe/](https://extensions.gnome.org/extension/394/enhanced-dock-for-running-programs-and-with-previe/)

I'll check in again in about a week. If I could get these two extensions to work, I might actually use this DE, but that's always been my problem with Gnome - the reliability of the extensions.

**Edit:** The Deepin Enhanced Dock also doesn't work:

[https://extensions.gnome.org/extension/265/deepin-enhanced-dock/](https://extensions.gnome.org/extension/265/deepin-enhanced-dock/)

Using Gnome Shell 3.6.

---

### Post by kansasnoob on 2012-10-23
> **Bart_D said:**
> Is there a link with official screenshots of this remix?

No but WebUpd8 has some good ones along with a video:

[http://www.webupd8.org/2012/10/prefer-gnome-shell-download-ubuntu.html](http://www.webupd8.org/2012/10/prefer-gnome-shell-download-ubuntu.html)

It really is pretty much pure Gnome, but a few things were held back from version 3.6 because of package conflicts with Ubuntu. Those packages are mentioned in the release notes.

---

### Post by SpaceAviator on 2012-10-24
I really wish to install this as my main distribution but I've two questions : 

1. Does the additionals drivers tab in software sources work? Someone in this thread said it doesn't but I def need proprietary drivers for my ATi 7850.

2. Can we install steam when it is released? I am assuming we can since this is based on ubuntu and uses official repositories.

---

### Post by since on 2012-10-24
I prefer xfce4

---

### Post by kansasnoob on 2012-10-24
> **since said:**
> I prefer xfce4

Nothing at all wrong with that, or Lubuntu :)

Edit: Just thought to add; it's rather like, "why do there have to be so many flavors of ice cream"?

How much difference is there between chocolate ripple and chocolate swirl?

Why do we still need chocolate chip?

Who in the world likes Rocky Road?

Ubuntu is, and I suspect always will be, about freedom and choice :D

---

### Post by x-shaney-x on 2012-10-24
> **mips said:**
> +1 WHy even bother otherwise. Why did you download the is in the first place, to install KDE?

My suspicion is the poster may have been referring to the idea of a one-for-all ubuntu where you would choose the desktop you want on install, rather than downloading the flavour from whichever source.

I doubt that would ever happen anyway and since not all the "main" ubuntu flavours are even officially part of ubuntu, even less so.

---

### Post by kurt18947 on 2012-10-25
> **VTPoet said:**
> I'm back in Gnome Shell right now. I can't get TopIcons:

[https://extensions.gnome.org/extension/495/topicons/](https://extensions.gnome.org/extension/495/topicons/)

Or Enhanced Dock to work:

[https://extensions.gnome.org/extension/394/enhanced-dock-for-running-programs-and-with-previe/](https://extensions.gnome.org/extension/394/enhanced-dock-for-running-programs-and-with-previe/)

I'll check in again in about a week. If I could get these two extensions to work, I might actually use this DE, but that's always been my problem with Gnome - **the reliability of the extensions.**

**Edit:** The Deepin Enhanced Dock also doesn't work:

[https://extensions.gnome.org/extension/265/deepin-enhanced-dock/](https://extensions.gnome.org/extension/265/deepin-enhanced-dock/)

Using Gnome Shell 3.6.

True.  I recall reading somewhere that one of the goals of Gnome 3.8(?) was to have extensions work regardless of gnome version.  Let's hope.

---

### Post by MikeCyber on 2012-10-26
> **mips said:**
> +1 WHy even bother otherwise. Why did you download the is in the first place, to install KDE?

Why, well for ex. for gaming use Gnome classic without effects as it's fastest. Also sometimes, for a change use fvwm2 crystal etc.
It's easy sure, but to have it at install would be more newbie friendly. Well, especially putting all newbies on a slow and ugly Unity is...

---

### Post by kansasnoob on 2012-10-26
I'm trying to parse some of the dconf/gsettings changes regarding a few things but I've particularly been looking at "update-notifications". I don't have it all figured out but thought I'd share this:

[ATTACH]226156[/ATTACH]

I do seem to be able to get what I want but it seems that I need to change some settings two or three times to get what I want :(

We'll get there :guitar:

Edit: Just thought to add that that's in classic (no effects) with 'update-manager' installed.

---

### Post by SpaceAviator on 2012-10-26
Are there any themes that are compatible with this version of Gnome?

---

### Post by Cfa77 on 2012-10-26
Does anybody know if Ubuntu 12.10 has solved the driver problem in the webcam of some asus laptop models???

---

### Post by kansasnoob on 2012-10-26
> **SpaceAviator said:**
> Are there any themes that are compatible with this version of Gnome?

Need to know if you're using Gnome Shell or classic :)

---

### Post by kansasnoob on 2012-10-26
> **Cfa77 said:**
> Does anybody know if Ubuntu 12.10 has solved the driver problem in the webcam of some asus laptop models???

Do you know of a bug # :confused:

---

### Post by SpaceAviator on 2012-10-26
> **kansasnoob said:**
> Need to know if you're using Gnome Shell or classic :)

Wait, this remix comes with both?

I was just talking about the shell, btw.

---

### Post by kansasnoob on 2012-10-26
> **SpaceAviator said:**
> Wait, this remix comes with both?

I was just talking about the shell, btw.

Yes. By default you can use either Gnome Shell or Gnome classic (no effects). If you wish to use Gnome classic you must install 'compiz' and presumably 'compizconfig-settings-manager'.

Regardless I have had good luck with the themes provided here:

[https://launchpad.net/~webupd8team/+archive/themes](https://launchpad.net/~webupd8team/+archive/themes)

But there's not much for Quantal yet, mostly just minor tweaks for Gnome Shell. The Precise version does provide the Zukitwo themes which I personally love but they're buggy in the 3.6 version of gnome-shell.

---

### Post by x-shaney-x on 2012-10-26
> **SpaceAviator said:**
> Are there any themes that are compatible with this version of Gnome?

Well you can enable the dark version of the default theme in gnome tweak tool :)

Unfortunately, Google Chrome doesn't use it so looks badly out of place :(

---

### Post by SpaceAviator on 2012-10-26
I might have to leave SolusOS for this then.

Is the Xorg version different in this remix? I installed this remix a three days ago and the drivers installed fine from software sources. But when I did the same in Ubuntu it broke unity...

---

### Post by Cfa77 on 2012-10-26
yes; in my laptop skype appears up-side down... :-(

---

### Post by kansasnoob on 2012-10-26
> **Cfa77 said:**
> yes; in my laptop skype appears up-side down... :-(

I don't know what would cause that but it might help others to see this:

[http://ubuntuforums.org/showthread.php?p=12235067#post12235067](http://ubuntuforums.org/showthread.php?p=12235067#post12235067)

> I own an Asus K50IJ (laptop) and when I am using applications like skype or video calls my camera shows me upside down. Is this a driver problem, an update? Can somebody help me? What can I do?

---

### Post by kansasnoob on 2012-10-26
> **SpaceAviator said:**
> I might have to leave SolusOS for this then.

Is the Xorg version different in this remix? I installed this remix a three days ago and the drivers installed fine from software sources. But when I did the same in Ubuntu it broke unity...

AFAIK we use the same version of Xorg as Ubuntu. But Ubuntu now uses that combo of compiz + llvmpipe to eliminate a need to fallback to metacity (and Unity-2D), whereas this remix uses Mutter for gnome-shell and Metacity for classic w/o effects.

I was interested in Solus until I read that SolusOS 2 will not be debian based. Instead, using Pisi package manager from Pardus.

---

### Post by kansasnoob on 2012-10-26
> **kansasnoob said:**
> I don't know what would cause that but it might help others to see this:

[http://ubuntuforums.org/showthread.php?p=12235067#post12235067](http://ubuntuforums.org/showthread.php?p=12235067#post12235067)

I've been searching to see if I can find a Launchpad bug report, but no such luck. I did find a couple of other suggestions though.

One that sounded safe and sensible to me was installing 'v4l2ucp' (aka: Video4Linux Control Panel) and try "Flip vertically":

[ATTACH]226178[/ATTACH]

There are a number of older how-to's regarding "skype webcam upside down" but I don't want to endorse anyone else's CLI fixes when I can't test them myself:

[ATTACH]226179[/ATTACH]

---

### Post by x-shaney-x on 2012-10-27
One thing I do find odd about 'remix.  Odd and quite annoying.

I used gparted to set labels for all my partitions, which amongst other things makes the partitions immediately recognisable in file managers and such.

Yet when I boot into other distros after using 'remix, the label is always reset.
Only happens with the 'remix partition.

---

### Post by kansasnoob on 2012-10-27
> **x-shaney-x said:**
> One thing I do find odd about 'remix.  Odd and quite annoying.

I used gparted to set labels for all my partitions, which amongst other things makes the partitions immediately recognisable in file managers and such.

Yet when I boot into other distros after using 'remix, the label is always reset.
Only happens with the 'remix partition.

That's also happening in plain-Jane Ubuntu 12.04 :(

I've just been too busy to figure out if it's a gparted problem or something else. I do have an older Ubuntu Oneiric still installed that hasn't been updated in a few months so maybe I should see if it's effected?

I need to think about it :-k

I've even wondered if it could have something to do with changes to 'gnome-disk-utility' which I detest. By "detest" I simply mean it's much less intuitive than gparted :)

But I can assure you that it effects Ubuntu 12.04 also :)

---

### Post by x-shaney-x on 2012-10-27
> **kansasnoob said:**
> That's also happening in plain-Jane Ubuntu 12.04 :(

I don't know about 12.04 but I have a plain 12.10 install and the remix install along with a couple of non-ubuntu installs and it is not happening on the plain 12.10 partition, only the remix one.

I'll try changing the label another way and see what happens.

---

### Post by x-shaney-x on 2012-10-27
Regarding the label issue:

Tried using e2label and still having the same problem so did a little experiment.

Used e2label in Kororaa to change the label of my ubuntu 12.10 and Remix 12.10 partitions.
Booted into each in turn then back into Kororaa.
The plain ubuntu kept it's label, the Remix one reset again.


Then booted into plain ubuntu and used e2label to change the Remix and Kororaa labels.
Booted into each of those in turn then back to ubuntu.

Kororaa kept it's label and Remix reset once again.

Very odd...

---

### Post by kansasnoob on 2012-10-27
> **x-shaney-x said:**
> I don't know about 12.04 but I have a plain 12.10 install and the remix install along with a couple of non-ubuntu installs and it is not happening on the plain 12.10 partition, only the remix one.

I'll try changing the label another way and see what happens.

It's all cool, I should have spent more time trying to get to the root of the problem. Not exactly the same issue but I read this on Lubuntu QA recently:

[https://lists.launchpad.net/lubuntu-qa/msg01576.html](https://lists.launchpad.net/lubuntu-qa/msg01576.html)

> However, there is a rather more important issue. palimipset (aka
gnome-disk-utility) is installed but inaccessible. No menu entry and will
not start from terminal. syanptic states it is installed. I have no way to
access this utility. Which is now a blocker on my sorting out partitions on
the two disks.

I'm thinking that 'gnome-disk-utility' (aka: 'palimpsest') may have a compatibility issue with shared parted libs, or maybe 'udisks' libs :confused:

FYI in 12.10 the possibly conflicting app is called Disks, it was previously known as GNOME Disk Utility or palimpsest.

I may try purging that app and then see what happens with Gparted. It certainly is a pain in the neck when you have a partitioning arrangement like this:

[ATTACH]226184[/ATTACH]

Many of those have no OS installed ATM but that's my main test box and sometimes I need to test something between various versions and/or flavors - and labeling is important!!!

---

### Post by kansasnoob on 2012-10-27
> **x-shaney-x said:**
> Regarding the label issue:

Tried using e2label and still having the same problem so did a little experiment.

Used e2label in Kororaa to change the label of my ubuntu 12.10 and Remix 12.10 partitions.
Booted into each in turn then back into Kororaa.
The plain ubuntu kept it's label, the Remix one reset again.


Then booted into plain ubuntu and used e2label to change the Remix and Kororaa labels.
Booted into each of those in turn then back to ubuntu.

Kororaa kept it's label and Remix reset once again.

Very odd...

Yeah, my idea didn't work :(

At this point I'm so clueless about the cause I don't have any idea how to file a bug :confused:

---

### Post by x-shaney-x on 2012-10-27
And this small discussion has brought something else into my mind.
It feels really awkward discussing this distro, just not sure what to call it :o)

Any word on a snappy name yet?

Aside from anything else, everything else on my custom grub menu is one word, a 3 worded distro looks wrong :oD

---

### Post by kansasnoob on 2012-10-27
> **x-shaney-x said:**
> And this small discussion has brought something else into my mind.
It feels really awkward discussing this distro, just not sure what to call it :o)

Any word on a snappy name yet?

Aside from anything else, everything else on my custom grub menu is one word, a 3 worded distro looks wrong :oD

No name yet, that will be a Canonical decision.

---

### Post by kansasnoob on 2012-10-27
About the partition labeling not "sticking";

It seems that I made an incorrect assumption about this effecting Precise. I was looking at it somewhat from the wrong angle. I still use Ubuntu Precise as my work-horse because Ubuntu Quantal fails to run at all on one of my boxes, and it runs poorly on my other two boxes :(

Anyway I can set a device label using Gparted in Precise and it "sticks" as long as the device I'm labeling is Precise or older. If the device is Quantal it seems NOT to "stick".

So far I've found that if I'm booted into Ubuntu Precise and label Quantal "ubuntu-gnome" using Gparted the label is lost on reboot, **BUT I can successfully get the label to "stick" if I create the label using 'gnome-disk-utility' in that Precise install**.

Confusing huh :(

What could be the difference between creating a device label using Gparted and creating a device label using 'palimpsest'?

Regardless I have much more testing to do :)

I reset my old VIA iso-testing box so I'm going to try every flavor of *buntu Quantal and try to find the "common link" if it's possible.

---

### Post by x-shaney-x on 2012-10-27
Is it ok to set the label of the currently running OS while it is actually running?  Not something I have tried but interested to see how it would work in that instance here.

---

### Post by x-shaney-x on 2012-10-27
Hello, me again!

The plot thickens...
Went ahead and changed the label within 'Remix itself using "Disks".
After rebooting into all other distros and back again, the label is being read correctly by all and has not been reset.  Weird!

---

### Post by kansasnoob on 2012-10-27
> **x-shaney-x said:**
> Hello, me again!

The plot thickens...
Went ahead and changed the label within 'Remix itself using "Disks".
After rebooting into all other distros and back again, the label is being read correctly by all and has not been reset.  Weird!

Weird indeed. I need to do some cross testing with the other flavors to see which are effected.

---

### Post by kansasnoob on 2012-10-28
This partition labeling bug is a real mind-bender. ATM it seems to me that hardware even effects the outcome.

I can easily reproduce this bug using SATA II drives, but not older IDE drives :confused:

I have a couple of older SATA I drives so I'll see what happens with them when I have time :)

---

### Post by darkxst on 2012-10-29
> **kansasnoob said:**
> No name yet, that will be a Canonical decision.

Just to clarify, Ubuntu GNOME remix is a community effort, thus when the time comes to choose a new name, it will be a community decision. 

Canonical provide guidelines that we must follow to become an officially recognized flavour, however beyond that they have no direct involvement in the direction of this project.

[https://wiki.ubuntu.com/RecognizedFlavors](https://wiki.ubuntu.com/RecognizedFlavors)

---

### Post by x-shaney-x on 2012-10-29
> **darkxst said:**
> Just to clarify, Ubuntu GNOME remix is a community effort, thus when the time comes to choose a new name, it will be a community decision. 

Canonical provide guidelines that we must follow to become an officially recognized flavour, however beyond that they have no direct involvement in the direction of this project.

[https://wiki.ubuntu.com/RecognizedFlavors](https://wiki.ubuntu.com/RecognizedFlavors)

The less involvement the better though I would imagine they are going to have final approval on the name, even if they don't choose it directly?

---

### Post by kansasnoob on 2012-10-29
> **darkxst said:**
> Just to clarify, Ubuntu GNOME remix is a community effort, thus when the time comes to choose a new name, it will be a community decision. 

Canonical provide guidelines that we must follow to become an officially recognized flavour, however beyond that they have no direct involvement in the direction of this project.

[https://wiki.ubuntu.com/RecognizedFlavors](https://wiki.ubuntu.com/RecognizedFlavors)

Sorry if I misstated things :oops:

I do recall following LXDE + Ubuntu dev over several years. First there was the totally unofficial Ubuntu Lite, later U-lite, etc.

I have no idea who was eaten in the process but I was on the front-lines of testing when Lubuntu did become official :)

I just like this spin - I like it a lot!

And I find it odd that someone would take out time to create an account to scold me :(

---

### Post by darkxst on 2012-10-29
> **kansasnoob said:**
> 

And I find it odd that someone would take out time to create an account to scold me :(


No that was not my intention at all, just clarifying on a point of misinformation that I have seen thrown around the interwebs by various people, that to varying degrees seem to imply that this is a canonical project.

---

### Post by kansasnoob on 2012-10-30
> **darkxst said:**
> No that was not my intention at all, just clarifying on a point of misinformation that I have seen thrown around the interwebs by various people, that to varying degrees seem to imply that this is a canonical project.

Thanks for clarifying that. I'm just a worn out old end-user/iso-tester that happens to love this remix :)

There's some really good info in the link you provided, particularly:

> Guidelines to become and remain a recognized flavor:

    Image has track record of community interested in creating, supporting and promoting its use.
    Leading members have signed Ubuntu Code of Conduct.
    One or more developer with upload rights.
    Flavor lead identified and responsive though 6 month cycle.
    Flavor QA lead (may be different from flavor lead) identified to coordinate testing of image at milestones during release.
    Follow the milestone and release processes.
    Best effort support from flavor community for security updates and high priority bug fixes for default 18 month support period.

    If flavor ceases to do active releases for consecutive cycles, release team may request the TechnicalBoard review whether it should remain recognized flavor. 

I just wish I were mentally and physically able to provide more actual hands-on support :(

---

### Post by Stinger on 2012-10-30
> **kansasnoob said:**
> I just like this spin - I like it a lot!

And I find it odd that someone would take out time to create an account to scold me :(
+1 I like this spin a lot too :D
I think communication between users and developers, and the other way round, could be better, I'm not saying anyone is to blame but if we want this baby to grow and really make a difference we all need to feel that we are working as a team and not as individuals.
Although a lot of people has joined the [Ubuntu Gnome Team]("https://launchpad.net/~ubuntu-gnome") I didn't get the feeling of being part of the project so I signed off.

The only thing the [Ubuntu Gnome wiki page]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10") tells you is that "If you would like to help shape Ubuntu" you can [join Ubuntu]("http://www.ubuntu.com/community/get-involved") or [join Gnome]("http://www.gnome.org/get-involved/")
That's of course mighty fine, but I want to help shaping Ubuntu Gnome Remix and I just can't find a way to do exactly that :???:

---

### Post by kansasnoob on 2012-10-30
I put a link in my OP to the project page:

[https://launchpad.net/~ubuntu-gnome](https://launchpad.net/~ubuntu-gnome)

If you join the team you can then subscribe to the mailing list:

[https://lists.launchpad.net/ubuntu-gnome/](https://lists.launchpad.net/ubuntu-gnome/)

I'm Lance there.

There is also an IRC chat channel:

```
#ubuntu-gnome
```

---

### Post by Stinger on 2012-10-30
As a matter of fact I was the first to post on the mailing list ;)

---

### Post by uhgreen on 2012-10-30
I just installed the Ubuntu Gnome Remix yesterday and I LOVE it.

A few words of note:  making a USB drive... dd did NOT work.  Startup Disk Creator did NOT work.  UNetBootin DID work.  I think somebody already mentioned that in this thread but it MIGHT be worth mentioning again.

Gnome 3 is so much faster than Unity.  Stupid Compiz sucks.

---

### Post by Uncle Spellbinder on 2012-10-31
> **kansasnoob said:**
> ...I was interested in Solus until I read that SolusOS 2 will not be debian based. Instead, using Pisi package manager from Pardus.
Hmmmm. That's the main reason I'm so excited at the prospects of SolusOS 2. 

I'm currently using SolusOS 1.2 (still Debian based) on my laptop. Installing Ubuntu Gnome Remix on my desktop as I type this.

---

### Post by Uncle Spellbinder on 2012-11-01
Installed, updated with the GNOME3 Team PPA. So far, I'm really liking Ubuntu Gnome Remix a lot!

---

### Post by kansasnoob on 2012-11-01
> **Uncle Spellbinder said:**
> Installed, updated with the GNOME3 Team PPA. So far, I'm really liking Ubuntu Gnome Remix a lot!

In deed, previous to this my three greatest thrills were how stable Ubuntu Gutsy and Jaunty were, and when Lubuntu became official. I do realize though that we've all had different experiences. 

I hope we get some good news out of Raring UDS :guitar:

And I personally hope that we can keep metacity and gnome-panel alive because that combo works just as well for me as openbox w/LXDE on low-end hardware :biggrin:

---

### Post by rezzo on 2012-11-01
Sounds good!

I've been using Gnome 3 with Arch Linux (great distro), but I'll give it a try this flavor in another pc. (:

---

### Post by Stinger on 2012-11-01
> **rezzo said:**
> Sounds good!

I've been using Gnome 3 with Arch Linux (great distro), but I'll give it a try this flavor in another pc. (:
Please do, it works really great, here some screenshots of my box with the Faience icons and the default Adwaita theme set to dark.
I'm using one of my old Gnome2 backgrounds. :cool:

---

### Post by SpaceAviator on 2012-11-01
This remix has been working great so far!

I ran into some problems with installing google chrome stable via  deb package but dpkg installed it minus minor dependency problems which I fixed via apt-get -f install

anyway, does anyone know how to fix font rendering? It doesn't look this remix has the font rendering that comes with ubuntu. Maybe we can get some infinality patches going?

Here you go, possible fix : [https://launchpad.net/~no1wantdthisname/+archive/ppa](https://launchpad.net/~no1wantdthisname/+archive/ppa)

---

### Post by SpaceAviator on 2012-11-01
Also as someone new to this remix : what exactly should I do after installing?

I see people reporting they updated after adding the gnome3 ppa. What is that about?

How do I get the most out of this remix?

---

### Post by x-shaney-x on 2012-11-01
Not sure there is anything wrong with the font rendering.
Ubuntu "proper" uses the ubuntu font, whereas gnome remix uses the default Gnome font "Cantarell", which does have a slightly more wiry look about it.
Try changing the font to ubuntu via Gnome Tweak Tool and see?

What you do after install really depends on the individuals needs.
Personally, I haven't done much of anything other than install some preferred app, such as Google Chrome and Gthumb.

The gnome 3 PPA includes updates to some core apps such as totem and nautilus though nautilus is quite different from regular ubuntu (some say crippled).

With a gnome 3 distro, one thing you should certainly do is check out gnome extensions: [https://extensions.gnome.org/](https://extensions.gnome.org/)
Gnome is built light and streamlined but gives users the option of adding features via extensions, which is a much better way than throwing everything in whether people want it or now, in my opinion.
You just install them directly from the website and they are working there and then.

---

### Post by SpaceAviator on 2012-11-01
wait so if I understand this correctly, updating via the gnome3 ppa is recommended?

---

### Post by kansasnoob on 2012-11-02
> **SpaceAviator said:**
> wait so if I understand this correctly, updating via the gnome3 ppa is recommended?

First of all let's be certain that we're talking about the same PPA:

[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=quantal](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=quantal)

With the Quantal filter applied you'll see that there are actually very few package updates available there:

[ATTACH]226569[/ATTACH]

Some are addressed in the release notes:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10#What.27s_Not_Included](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10#What.27s_Not_Included)

> Some GNOME apps will not be upgraded to 3.6 for the 12.10 release. If you want these, try the GNOME3 PPA. Affected apps include Aisleriot, Nautilus, System Settings, and Totem. 

I'm personally using it almost "out-of-box" but with the newer Nautilus. It's really all just a matter of choice :)

---

### Post by SpaceAviator on 2012-11-02
Thanks for the reply! I'm loving this bad boy so far.

I just one problem - when I full screen flash videos in chrome, the top panel stays for quite a bit before it goes away on its own. What's up with that?

Also if I am playing a movie in the totem player and I fullscreen it - there is a flash of controls when I move my mouse during fullscreen mode but they vanish as soon as they appear. Is that just me?

---

### Post by x-shaney-x on 2012-11-02
> **SpaceAviator said:**
> I just one problem - when I full screen flash videos in chrome, the top panel stays for quite a bit before it goes away on its own. What's up with that?

I also get that and assume it's a bug or may be related to a gnome extension.  Do you have any extensions installed?

> **SpaceAviator said:**
> Also if I am playing a movie in the totem player and I fullscreen it - there is a flash of controls when I move my mouse during fullscreen mode but they vanish as soon as they appear. Is that just me?

On mine the controls appear on mouse moevement and stay there for a couple of seconds.
Shouldn't just instantly disappear.

---

### Post by SpaceAviator on 2012-11-02
Any possible fix for totem controls? or how can I help troubleshoot?

---

### Post by screaminj3sus on 2012-11-02
> **SpaceAviator said:**
> Thanks for the reply! I'm loving this bad boy so far.

I just one problem - when I full screen flash videos in chrome, the top panel stays for quite a bit before it goes away on its own. What's up with that?

Also if I am playing a movie in the totem player and I fullscreen it - there is a flash of controls when I move my mouse during fullscreen mode but they vanish as soon as they appear. Is that just me?
One of my laptops has had a long standing bug with totem that's similar, the controls simply refuse to appear at all in fullscreen when using the touchpad. As soon as I plug in a usb mouse the issue goes away :/

---

### Post by MikeCyber on 2012-11-03
VLC works best out of the box, without any handicraft

---

### Post by kansasnoob on 2012-11-04
I decided to remove this post and post the same info here:

[http://ubuntuforums.org/showthread.php?t=2080504](http://ubuntuforums.org/showthread.php?t=2080504)

Tweren't thinkin' straight :-k

---

### Post by x-shaney-x on 2012-11-06
Well this is a new one on me:

Settled down to watch a film using "Videos" (totem) and found the screen blanking every 15-20 minutes.

This is something I haven't experienced in years so I presume it is something centric to gnome shell and it's components?

I suspected gnome screensaver but after disabling it the screen still blanks.

The little googling I have done so far seems to suggest various ways around from altering xorg.conf to installing applications or other video players.
Since most of the answers I have found give conflicting information and/or the information is dated, just what is the reason for this?

---

### Post by kansasnoob on 2012-11-07
> **x-shaney-x said:**
> Well this is a new one on me:

Settled down to watch a film using "Videos" (totem) and found the screen blanking every 15-20 minutes.

This is something I haven't experienced in years so I presume it is something centric to gnome shell and it's components?

I suspected gnome screensaver but after disabling it the screen still blanks.

The little googling I have done so far seems to suggest various ways around from altering xorg.conf to installing applications or other video players.
Since most of the answers I have found give conflicting information and/or the information is dated, just what is the reason for this?

It works OK for me with Caffeine which I discussed in step #12 here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Although Totem does not work at all on my VIA P4M800 box, there I must use VLC :)

---

### Post by x-shaney-x on 2012-11-07
Wow!  So it's MEANT to do that?

I haven't always agreed with desktop design decisions and found many such decisions baffling (a major reason for leaving unity) but this one is incomprehensible above all others.
The Gnome people actually don't consider that people might want to watch a video uninterrupted?
Worse still not offering a simple way to disable it?

Thanks for the info on caffeine, most helpful but I don't consider installing other applications to do this acceptable, let alone adding PPA's in order to install the application for something like this.

Up until now I have found gnome shell and gnome remix refreshing and without any real negatives but this is quite a big deal (to me at least).

Maybe I have got it all wrong and maybe I am missing something obvious but I just cannot understand the reasoning at all.

---

### Post by kansasnoob on 2012-11-07
Yeah you used to be able to use 'gnome-inhibit-applet' which was in the repos but when they introduced gnome3 they left out a lot of doo-dads that really improve overall functionality.

---

### Post by x-shaney-x on 2012-11-07
Yea.  What some people consider functionality others don't and I know it is hard to get a balance to suit everyone but I don't consider this is something I would have thought was a necessity!

I have tried the caffeine gnome shell extension, which I would have considered an acceptable solution but that doesn't work at all!

---

### Post by Stinger on 2012-11-07
And of course I don't have to mention 'Brightness & Lock' from the 'System Settings' ? ;)

---

### Post by x-shaney-x on 2012-11-07
Of course :)
But I'm not on about simply turning the option off since I would prefer my screen to blank under normal circumstances, I just feel it should have the intelligence to inhibit blanking when watching a video.
I am pretty sure video players include these options (smplayer and VLC I think are two).

Yes, I could make do with disabling the option before watching a video but going into system settings to alter something before watching a vid just doesn't sit well with me, just like I wouldn't expect to alter a system setting before editing a document or altering a setting before browsing the web.

Aside from anything else, chances are I am not going to remember to do it so will have at least one interruption during a film the first time it blanks and then I have to pause it while I go to settings to change the option.
Then once finished my laptop is left with the screen draining away because I forgot to change the option again.

---

### Post by Stinger on 2012-11-07
@x-shaney-x
I see, you want Totem/videos to override these settings.
This could be a Totem bug, Totem only allows disabling the screensaver.

I think you should file a bug against Totem, it should be allowed  to  disable 'Brightness & Lock'/suspend  as well.

---

### Post by kansasnoob on 2012-11-07
> **Stinger said:**
> @x-shaney-x
I see, you want Totem/videos to override these settings.
This could be a Totem bug, Totem only allows disabling the screensaver.

I think you should file a bug against Totem, it should be allowed  to  disable 'Brightness & Lock'/suspend  as well.

Thanks for that screenshot. I didn't even know that option existed :oops:

---

### Post by x-shaney-x on 2012-11-07
> **kansasnoob said:**
> Thanks for that screenshot. I didn't even know that option existed :oops:

I still don't.  I cannot find anything anywhere to bring up that preferences window?!
Nothing in dconf-editor to change it either.

<EDIT>
GAH! Nevermind.  I keep forgetting the app title in the panel has options with some apps :)
Though still, doesn't seem to be blocking the screensaver, despite the option. And I assume it is the screensaver that is kicking in and causing the blanking.

---

### Post by Stinger on 2012-11-08
> **x-shaney-x said:**
> 
<EDIT>
GAH! Nevermind.  I keep forgetting the app title in the panel has options with some apps :)

He he, you should be used to that by now with the global menu's from Unity and Mac 
But of course, Gnome-Shell is a little different ;)

---

### Post by x-shaney-x on 2012-11-08
yes it is a bit inconsistent right now.  
With "Web" and "Files" there is no menubar so the obvious thing is to look for options elsewhere.
Because totem still has the menubar I didn't think to look further.
Still, I do prefer the approach Nautilus approach and will be happier when more apps catch up.

Doing some more searching there are bug reports regarding the totem blanking problem stretching back 5 years and beyond so I don't hold out much hope of it ever working properly.

I will probably give in and install smplayer which is what I normally use or maybe VLC.

---

### Post by kansasnoob on 2012-11-09
Since I maintain 23 old boxes with P4M800 graphics it'd be silly for me to pursue Gnome anymore after reading this:

[http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html#more](http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html#more)

Since that involves the deprecation of Metacity it just makes more sense for me to focus on Lubuntu which uses Openbox. No sour grapes though :)

Their decision is based on available resources and so is mine. They can't afford to divert resources from the development of Mutter and Gnome Shell - and I can't divert my financial resources toward upgrading that much hardware.

In the meanwhile I'll just keep using [Ubuntu 12.04 classic mode]("http://ubuntuforums.org/showthread.php?t=1966370") and I'll finally be able to devote 100% of my testing (and tweaking) time to Lubuntu dev :D

If that doesn't work out there's always SolusOS and MATE.

---

### Post by x-shaney-x on 2012-11-09
> **Stinger said:**
> And of course I don't have to mention 'Brightness & Lock' from the 'System Settings' ? ;)

Just an update on this:

I settled down once again to watch a film this evening.
Decided to use the option you highlighted in the screenshot and set the screen to turn off "Never".

Started up the film and 10-15 minutes later the screen turned off.
Logged out, back in again, check the option still said "Never" then went ahead with the film again.
10-15 minutes later the screen turned off!!
Serious problem here.

---

### Post by kansasnoob on 2012-11-09
> **x-shaney-x said:**
> Just an update on this:

I settled down once again to watch a film this evening.
Decided to use the option you highlighted in the screenshot and set the screen to turn off "Never".

Started up the film and 10-15 minutes later the screen turned off.
Logged out, back in again, check the option still said "Never" then went ahead with the film again.
10-15 minutes later the screen turned off!!
Serious problem here.

Having read this:

[https://live.gnome.org/ThreePointSeven/Features/DropOrFixFallbackMode](https://live.gnome.org/ThreePointSeven/Features/DropOrFixFallbackMode)

I wonder if you could be effected by the part that says:

> several apps now require clutter and can't work without GL. Thus they won't work in fallback mode if it was forced by lack of GL (totem, audio/video UI in empathy, cheese, etc.)

I'm really clueless and I just can't afford to spend any more time working on something that won't work for me in the future :(

---

### Post by x-shaney-x on 2012-11-09
Shouldn't think so since the computer has enough oomph to run shell without issue.
I have also now discovered I have the same problem using VLC too, not just totem.

Trying smplayer next...

---

### Post by Stinger on 2012-11-10
> **x-shaney-x said:**
> Just an update on this:

I settled down once again to watch a film this evening.
Decided to use the option you highlighted in the screenshot and set the screen to turn off "Never".

Started up the film and 10-15 minutes later the screen turned off.
Logged out, back in again, check the option still said "Never" then went ahead with the film again.
10-15 minutes later the screen turned off!!
Serious problem here.

I can smell a bug here ;) we just have to locate this little bugger.
Maybe it's possible somehow to trace it ? Does running Totem from a terminal give you a clue ?

---

### Post by x-shaney-x on 2012-11-10
> **Stinger said:**
> I can smell a bug here ;) we just have to locate this little bugger

Indeed.  As mentioned, I used VLC and the screen still blanked.
This was with the screen set to never turn off AND with the VLC option to inhibit screensaver enabled.

So I went on to smplayer.
This time I had no interruptions at all.  smplayer also has an inhibit option which was enabled by default and I left it so.

Didn't have time to do anything else but I want to try with smplayer and the screen turn off set to 10 minutes or something and see if smplayer still inhibits.

Maybe this points to a bug in the way totem and VLC try to inhibit the blanking?
I must assume smplayer does it differently.

<EDIT>
Tried smplayer with screen blanking back on and it doesn't inhibit.
So the only way to watch a whole film is to turn screen blanking off completely AND use smplayer.

---

### Post by neu5eeCh on 2012-11-10
I still cant' run my preferred extensions and themes are limited.

Then I read this:

[https://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/](https://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/)

If I'm re-posting a link everyone knows, apologies. I was and am so &*%$ irritated by the article that I'm uninstalling Gnome Shell. I'm done with it. This kind of attitude is precisely why I detest Apple (especially) and Windows. When I read that Gnome devs are, at worst, deliberately breaking third party extensions to prevent damage to their "brand", that's the last straw. :???:

---

### Post by x-shaney-x on 2012-11-10
It was this "brand identity" and "design" over all else approach that I have seen building in unity (and will no doubt get stronger) that has been the biggest factor in me giving up on unity forever and moving on to shell instead.

Indeed, it wouldn't suprise me that shell may go the same way and KDE also.

At the same time, for years desktop environments and distros have been horribly inconsistent in many ways and often 3 different gnome (or KDE) apps may be part of the same environment but look and feel even work completely different to each other.

I think having a clear goal of where they want their desktop to go is a good thing, as is a certain amount of consistency between the various apps and components.
When this reaches a point where they are actually blocking other ways of doing things altogether, that don't fit in with their "design", then we have a problem...

---

### Post by neu5eeCh on 2012-11-10
> **x-shaney-x said:**
> When this reaches a point where they are actually blocking other ways of doing things altogether, that don't fit in with their "design", then we have a problem...

Right. But even more so, if the Gnome Devs are going to show complete indifference (let alone hostility) to contributions from the broader community, then I want nothing to do with them. I was wondering why it was taking so long to get useful extensions & themes... now I know. 

> **x-shaney-x said:**
> At the same time, for years desktop environments and distros have been  horribly inconsistent in many ways and often 3 different gnome (or KDE)  apps may be part of the same environment but look and feel even work  completely different to each other.

Yes, but it seems that this is only going to get worse. Rather than inconsistent looks, we'll have apps that don't even work from one DE to the next. DEs like XFCE (which I use) and LXDE are going get shafted. Not sure how this is all going to sugar off.  Some of the code issues are above my pay grade.

---

### Post by neu5eeCh on 2012-11-10
Here. This is the choice quote from Allan Day:

> ** Facilitating the unrestricted use of extensions and themes by end  users seems contrary to the central tenets of the GNOME 3 design.**   We&#8217;ve fought long and hard to give GNOME 3 a consistent visual  appearance, to make it synonymous with a single user experience and to  ensure that that experience is of a consistently high quality. A general  purpose extensions and themes distribution system seems to threaten  much of that. 

I&#8217;m particularly surprised by the inclusion of themes. It seems  bizarre that we specifically designed the GNOME 3 control center not to  include theme installation/selection and then to reintroduce that very  same functionality via extensions.
The only reason Gnome even **has** extensions, apparently, is because Gnome can't lock up its source code. What's the next best thing? Being as unfriendly as possible to contributors.

---

### Post by Stinger on 2012-11-10
> **x-shaney-x said:**
> Indeed.  As mentioned, I used VLC and the screen still blanked.
This was with the screen set to never turn off AND with the VLC option to inhibit screensaver enabled.

So I went on to smplayer.
This time I had no interruptions at all.  smplayer also has an inhibit option which was enabled by default and I left it so.

Didn't have time to do anything else but I want to try with smplayer and the screen turn off set to 10 minutes or something and see if smplayer still inhibits.

Maybe this points to a bug in the way totem and VLC try to inhibit the blanking?
I must assume smplayer does it differently.

<EDIT>
Tried smplayer with screen blanking back on and it doesn't inhibit.
So the only way to watch a whole film is to turn screen blanking off completely AND use smplayer.
What about [GNOME MPLAYER 1.0.7]("http://www.webupd8.org/2012/11/install-gnome-mplayer-107-in-ubuntu-1210.html#more") ? Should be the same with the same backend. If you have the time you could try that one too ;)

---

### Post by x-shaney-x on 2012-11-10
> **VTPoet said:**
> Here. This is the choice quote from Allan Day:

The only reason Gnome even **has** extensions, apparently, is because Gnome can't lock up its source code. What's the next best thing? Being as unfriendly as possible to contributors.

Though as I understand it, a promise for 3.8 is that extensions will be automatically updated (ie made compatible) for users, to get around the problem of waiting for your favourite extension to be updated by it's developer. That alone would make extensions MORE desirable to users.

I'm not sure we are getting the full story here somehow.
In any case, at the moment at least, Gnome's idea of "branding" seems to be different to unity's to me.
In that Gnome's is more about a consistent and recognisable interface rather than unity's which seems to be gearing more towards a sell-able brand.
Time will tell.

Either way, I can't say I feel particularly comfortable in ANY desktop environment these days.
My choice is more on what works best for me right now. What the future holds is another matter...

---

### Post by x-shaney-x on 2012-11-10
> **Stinger said:**
> What about [GNOME MPLAYER 1.0.7]("http://www.webupd8.org/2012/11/install-gnome-mplayer-107-in-ubuntu-1210.html#more") ? Should be the same with the same backend. If you have the time you could try that one too ;)

Gave gnome-mplayer a try (from the PPA you linked to) and sad to say it behaved exactly the same as totem and VLC and blanked out after 10 minutes or so.
Like the others I tried with Brightness & Lock settings set to turn off after 10 minutes and again with it set to Never.

---

### Post by Chdslv on 2012-11-11
> **x-shaney-x said:**
> It was this "brand identity" and "design" over all else approach that I have seen building in unity (and will no doubt get stronger) that has been the biggest factor in me giving up on unity forever and moving on to shell instead.

All you have to do is, open Synaptic, reload it and install gnome-shell, and then log out and log into Gnome, and uninstall Unity.

You have your Ubuntu-Gnome remix without the Ubuntu-Gnome-desktop. You'd have Gnome 3.6.1, and if you'd like to change the Quantal repos to Raring, you can get the 3.7.1, only you won't have much extensions.

Good day!

---

### Post by Stinger on 2012-11-11
@x-shaney-x
The Caffeine shell extension should be working now according to the latest four posts on the [Caffeine page]("https://extensions.gnome.org/extension/517/caffeine/")
This is a comment from the author 'eon'
> A bug should be opened against Ubuntu. This extension or lavi741's one use the Inhibit dbus interface of the session manager that's all and it is provided by a standard GNOME component.
And as you can se from the latest user comments, it should be working in Gnome-Shell 3.6.1 and Ubuntu 12.10
You could try the extension again ;)

---

### Post by x-shaney-x on 2012-11-11
> **Stinger said:**
> @x-shaney-x
The Caffeine shell extension should be working now according to the latest four posts on the [Caffeine page]("https://extensions.gnome.org/extension/517/caffeine/")
This is a comment from the author 'eon'

And as you can se from the latest user comments, it should be working in Gnome-Shell 3.6.1 and Ubuntu 12.10
You could try the extension again ;)

I actually tried it again yesterday after reading those same comments and still not working here.
Though I got the impression from the comments that people are using shell over regular Ubuntu so may not have something installed on the remix that might be leading to the problems.

I'm starting to wonder if it could be a problem my end. Might be worth trying on a fresh install when I get a bit of time...

---

### Post by Uncle Spellbinder on 2012-11-22
Yeah, I'm really liking Ubuntu Remix. I've added the Gnome testing PPA and Gnome 3 PPA. I guess I'm trying to see if I can break it.  :grin: 
I've gotten to the point where i can now manipulate the gnome 3 panel. I was able to change the theme and remove the "accessibility" icon. I also have all three buttons on the window (minimize, maximize and close).

[SIZE="1"]click image for full 1600x900 resolution[/SIZE]
[[img]http://i.imgur.com/Rs3M5l.jpg[/img]](http://i.imgur.com/Rs3M5.jpg)

---

### Post by VideoRoy on 2012-11-25
Thanks to kansasnoob for kicking off this thread!

I may be different but I have never been that attached to any of the DEs in linux although I never really liked Gnome2 but it worked.  I got used to Unity right away due to simplicity.

I have been trying to find a good OS for my HP Mini Netbook for a couple of years and Ubuntu finally fixed all my hardware issues in 12.10 but made Unity un-useable.  This got me looking at Gnome-Fallback that I am using now and like but also Remix.

I have a number of test computers and decided to give Gnome Remix and a go on and older laptop and I really like it probably 90% out of the box.  Probably will not work on my Mini well but will try.  I will definitely use it on my desktop.

I am in the computer biz but I actually get pretty tired of tweaking things although I am able to do it.  With that said here are the few things I had to tweak to get Remix where I like it.

1. load dconf-editor for window button fixes
- Call me crazy but I like close, min and max buttons.  Screen capture attached to show how to do it.

2. load gdebi for loading .deb packages
- Had to do this because I could not load Chrome which is my default browser on Windows, Linux and Android.  Just give it me already.

3. uninstall gnome-packagekit
- Hated this software installer in Gnome always and really got used to Ubuntu Software Center.  Packagekit is barely usable and has the worst search and package descriptions.

4. Install software-center
- Yes Ubuntu Software Center seems to work just fine since.

5. Install update-manager
- Same as above just got used to how it works.

6. Install cairo-dock or docky
- Since I hid the gnome dash I use cairo-dock and get my apps menu as well as a nice configurable dock.  Probably could have used and extension dock but already familiar with these two.

7. load shell extensions hide-dock, move clock and remove accessibility.  hide-dock is the only real important here and the others are cosmetic.
Screen capture attached to show the extensions.

Also I installed msttcorefonts and libreoffice for my base config.  More to do but this gets the shell / desktop environment where it works for me.

Thanks again!!

---

### Post by x-shaney-x on 2012-11-26
Bought a new mouse last week, a Microsoft one.
I was about to take it back to the shop because I found the scroll wheel was scrolling about half a page in apps and web browsers.

I happened to boot into Kororaa for something and noticed the scroll wheel worked normally (as in it scrolled like my previous mouse).
So I tried Windows and it worked normally there also.

Well I suffered from the broken GDM problem people have had recently so did a PPA purge on the Gnome 3 repo and noticed since then the mouse is working normally here too.
What could be the problem with the Gnome 3 repo that's screwing the scroll wheel?

---

### Post by kansasnoob on 2012-11-26
> **x-shaney-x said:**
> Bought a new mouse last week, a Microsoft one.
I was about to take it back to the shop because I found the scroll wheel was scrolling about half a page in apps and web browsers.

I happened to boot into Kororaa for something and noticed the scroll wheel worked normally (as in it scrolled like my previous mouse).
So I tried Windows and it worked normally there also.

Well I suffered from the broken GDM problem people have had recently so did a PPA purge on the Gnome 3 repo and noticed since then the mouse is working normally here too.
What could be the problem with the Gnome 3 repo that's screwing the scroll wheel?

I noticed a discussion on the mailing list about the PPA but it didn't effect me so I'm clueless:

[https://lists.launchpad.net/ubuntu-gnome/](https://lists.launchpad.net/ubuntu-gnome/)

---

### Post by jbicha on 2012-11-29
> **VideoRoy said:**
> 

1. load dconf-editor for window button fixes
- Call me crazy but I like close, min and max buttons.  Screen capture attached to show how to do it.

You can also do that with Tweak Tool (arrangement of buttons on the titlebar) which is included.

> **VideoRoy said:**
> 
2. load gdebi for loading .deb packages
- Had to do this because I could not load Chrome which is my default  browser on Windows, Linux and Android.  Just give it me already.

I recommend chromium-browser, but this should also be fixed by using Software Center. (There actually is a packaging bug that Google needs to fix themselves at some point too.)

> **VideoRoy said:**
> 
3. uninstall gnome-packagekit
4. Install software-center
5. Install update-manager

That's been [done]("http://www.webupd8.org/2012/11/ubuntu-gnome-remix-1304-replaces-gnome.html") for 13.04.

---

### Post by jbicha on 2012-11-29
> **x-shaney-x said:**
> 
Started up the film and 10-15 minutes later the screen turned off.


That is [bug 1046118]("http://pad.lv/1046118") which was fixed in gnome-settings-daemon 3.6.2 which is available in the GNOME3 PPA. We'll try to get that fixed as an SRU for Quantal users not using the GNOME3 PPA.

---

### Post by Uncle Spellbinder on 2012-12-04
Can anyone tell me how to install *gnome-shell-extensions-user-theme*?

I've added the gnome 3 PPA and it still doesn't show in synaptic or via apt-get in terminal.


[SIZE="1"][COLOR="White"].[/COLOR][/SIZE]

---

### Post by screaminj3sus on 2012-12-04
> **Uncle Spellbinder said:**
> Can anyone tell me how to install *gnome-shell-extensions-user-theme*?

I've added the gnome 3 PPA and it still doesn't show in synaptic or via apt-get in terminal.


[SIZE="1"][COLOR="White"].[/COLOR][/SIZE]

[https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

---

### Post by Uncle Spellbinder on 2012-12-04
Thanks!

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Miscellaneous/thumbsup.gif[/IMG]



[SIZE="1"][COLOR="White"].[/COLOR][/SIZE]

---

### Post by screaminj3sus on 2012-12-04
I've recently installed this and am having an issue. Is there any way to get hibernate to show in the user menu in gnome-shell 3.6?

I've already done the following:
Enabled hibernate via policykit as shown here: [https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html). Hibernate is showing fine in the gnome control center power settings (its not greyed out)

Installed alternate status menu

rebooted.

I only have suspend and power off options in the user menu.

It worked fine when I used vanilla ubuntu 12.10 and unity, it showed up under the power cog.

EDIT: also I'm in a bit of a conundrum with bugs in this release.. there's this really annoying bug:  [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1046118](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1046118) which can be fixed by using the gnome 3 ppa. But when I use the gnome 3 ppa brasero is basically unusable: [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/1072151](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/1072151)

any way around these?

---

### Post by screaminj3sus on 2012-12-06
The gstreamer situation seems to be a bit of a mess in 12.10 :/

rhythmbox also seems to be a bit broken. In the preferred format settings it tells me I need additional codecs, even though I have all gstreamer 0.10 and gstreamer 1.0 codecs installed. Is there any chance we can get fixes for this stuff in the gnome 3 ppa maybe?

EDIT: Sound juicer works at least. I guess for now I'll stick with the gnome 3 ppa and use sound juicer and xfburn for ripping/burning.

---

### Post by screaminj3sus on 2012-12-07
Is there any chance we could get an update to gnome 3.6.2 in the gnome 3 ppa? I'm running into this incredibly annoying bug with the new lock screen now that should be fixed by 3.6.2: [https://bbs.archlinux.org/viewtopic.php?id=151967](https://bbs.archlinux.org/viewtopic.php?id=151967) gdm and gnome-screensaver is still at 3.6.1/3.6.0 in quantal :(. I'm not totally sure if the bug is in gdm or gnome-screensaver, a post on the arch bbs said it looks like a gdm bug.

---

### Post by SpaceAviator on 2012-12-13
Is installing ubuntu-restricted-extras okay to install on this or something else?

---

### Post by kansasnoob on 2012-12-13
> **SpaceAviator said:**
> Is installing ubuntu-restricted-extras okay to install on this or something else?

Where I'm using Firefox I'm also using 'ubuntu-restricted-extras' with no problem.

When Chromium is used I also install 'lubuntu-restricted-extras'.

---

### Post by deadflowr on 2012-12-13
> **kansasnoob said:**
> Where I'm using Firefox I'm also using 'ubuntu-restricted-extras' with no problem.

When Chromium is used I also install 'lubuntu-restricted-extras'.

Is there any particular reason to install the lubuntu package?

---

### Post by kansasnoob on 2012-12-13
> **deadflowr said:**
> Is there any particular reason to install the lubuntu package?

Well, it's pure habit on my part. I know that Chromium is native to Lubuntu. Right now I'm using 12.10 gnome-remix with Firefox so I only have 'ubuntu-restricted-extras' installed, and if I install 'lubuntu-restricted-extras' it installs all of the following:

```
chromium-browser (version 20.0.1132.47~r144678-0ubuntu0.12.04.1) will be installed
chromium-browser-l10n (version 20.0.1132.47~r144678-0ubuntu0.12.04.1) will be installed
chromium-codecs-ffmpeg-extra (version 20.0.1132.47~r144678-0ubuntu0.12.04.1) will be installed
libxss1 (version 1:1.2.1-2) will be installed
lubuntu-restricted-addons (version 12) will be installed
lubuntu-restricted-extras (version 57) will be installed

```

I suppose once we decide what default apps we're going to use with each release we should build our own "restricted" meta-packages.

OTOH I've tweaked mine so much ATM that I can no longer be sure what's normal (or out-of-box) behavior so I should probably test a fresh install again soon ..... if I ever get over this freaking flu bug :(

---

### Post by deadflowr on 2012-12-13
> **kansasnoob said:**
> Well, it's pure habit on my part. I know that Chromium is native to Lubuntu. Right now I'm using 12.10 gnome-remix with Firefox so I only have 'ubuntu-restricted-extras' installed, and if I install 'lubuntu-restricted-extras' it installs all of the following:

```
chromium-browser (version 20.0.1132.47~r144678-0ubuntu0.12.04.1) will be installed
chromium-browser-l10n (version 20.0.1132.47~r144678-0ubuntu0.12.04.1) will be installed
chromium-codecs-ffmpeg-extra (version 20.0.1132.47~r144678-0ubuntu0.12.04.1) will be installed
libxss1 (version 1:1.2.1-2) will be installed
lubuntu-restricted-addons (version 12) will be installed
lubuntu-restricted-extras (version 57) will be installed

```

I suppose once we decide what default apps we're going to use with each release we should build our own "restricted" meta-packages.

OTOH I've tweaked mine so much ATM that I can no longer be sure what's normal (or out-of-box) behavior so I should probably test a fresh install again soon ..... if I ever get over this freaking flu bug :(


Wow. I did not know that Chromium is included in the lubuntu-restricted-extras packages.
Seems bizarre for a full-fledged browser to be included, but stranger things have happened.(it probably has to do with those chromium codecs)
Thinking back to the last time I installed Lubuntu, Chromium was the installed browser.
Interesting stuff.

---

### Post by screaminj3sus on 2012-12-15
Well, figured out how to solve all my issues with gnome in 12.10, downgraded to gnome-shell remix 12.04 :)

The first time I ever tried gnome-shell remix was this 12.10 version, so I hadn't even thought to try 12.04 until now. I installed it today and it works flawlessly, haven't run into a single bug yet. Gnome 3.4 is just in way better shape then gnome 3.6 at the moment. I hope by the time raring comes out gnome 3.6 will be less buggy :/

---

### Post by Rangir on 2012-12-18
Installed Ubuntu Gnome Remix, but it has nothing much to offer. I also installed gnome shell in Ubuntu quantal. It gave an up to date gnome shell and all the applications Ubuntu has, Firefox and all. I have Unity and gnome shell like a remix by itself. I was wondering, whether we need such an ubuntu gnome remix.

---

### Post by Stinger on 2012-12-18
> **Rangir said:**
> I was wondering, whether we need such an ubuntu gnome remix.

Have you come to a conclusion or an answer to your question above, or are you still wondering ?

---

### Post by Rangir on 2012-12-18
> **Stinger said:**
> Have you come to a conclusion or an answer to your question above, or are you still wondering ?

If I could install the gnome shell from ubuntu repos and it made my ubuntu a gnome remix, then why do I need an ubuntu gnome remix? Yes, I am still wondering. I have seen the ubuntu gnome remix and found that there is nothing, which ubuntu quantal could give. It was a wasted download time. 

When I write sudo apt-get install gnome-shell in quantal, after a while I have my automatic ubuntu gnome remix. 

Do you think I should have ubuntu quantal in one partition and ubuntu gnome remix in another partition or should I have only one quantal with gnome shell installed? Why do you think ishould have 2 partition with the same thing?

---

### Post by Rangir on 2012-12-18
> **Stinger said:**
> Have you come to a conclusion or an answer to your question above, or are you still wondering ?

If I could install the gnome shell from ubuntu repos and it made my ubuntu a gnome remix, then why do I need an ubuntu gnome remix? Yes, I am still wondering. I have seen the ubuntu gnome remix and found that there is nothing, which ubuntu quantal could give. It was a wasted download time. 

When I write sudo apt-get install gnome-shell in quantal, after a while I have my automatic ubuntu gnome remix. 

Do you think I should have ubuntu quantal in one partition and ubuntu gnome remix in another partition or should I have only one quantal with gnome shell installed? Why do you think I must have 2 partition with the same thing?

---

### Post by kansasnoob on 2012-12-18
> **Rangir said:**
> Installed Ubuntu Gnome Remix, but it has nothing much to offer. 

You are, of course, entitled to your opinion :)

> I was wondering, whether we need such an ubuntu gnome remix.

Since the Ubuntu repos have a large variety of desktop environments and/or window managers available for download it could be argued that Canonical need offer no flavor other than Ubuntu itself, particularly since one can use the mini.iso to build whatever they wish from a minimal install :D

It's all a matter of choice and personal preference :guitar:

---

### Post by kansasnoob on 2012-12-18
> **Rangir said:**
> Why do you think I must have 2 partition with the same thing?

Who's giving you the impression that you ***must*** do anything?

In my case this is a great spin because in 12.10 Ubuntu dropped Unity-2D and the metacity window manager in favor of using Compiz+llvmpipe, and I maintain over 20 PC's that simply will no longer run Ubuntu itself due to that change :(

Change is ongoing in Linux, and particularly in Ubuntu and Gnome over the past 18 months or so. In this case Gnome's Mutter window manager does run lighter than Compiz so I can still install Ubuntu using this remix and then tweak things as desired to my hearts content.

Many more changes are coming with Gnome 3.8 which we probably won't see in it's entirety for at least another 6 to 8 months so I plan on following this remix just to see how those changes effect me long before I ***must*** make any decision.

But my production machines are all running either Lubuntu 12.10 or Ubuntu 12.04 (some with Unity and others with classic).

I'm retired and if I ever felt that I ***must*** do anything I'd ***not*** be doing that thing very long ;)

---

### Post by Rangir on 2012-12-18
> **kansasnoob said:**
> Who's giving you the impression that you ***must*** do anything?

That's okay! I think that chap stinger was trying to sting me.:smile:

> In my case this is a great spin because in 12.10 Ubuntu dropped  Unity-2D and the metacity window manager in favor of using  Compiz+llvmpipe, and I maintain over 20 PC's that simply will no longer  run Ubuntu itself due to that change :sad:

There was a mention about unity2d somewhere in the forums, I believe.

> Change is ongoing in Linux, and particularly in Ubuntu and Gnome  over the past 18 months or so. In this case Gnome's Mutter window  manager does run lighter than Compiz so I can still install Ubuntu using  this remix and then tweak things as desired to my hearts  content.

Once you logout and log into Gnome, it works  with mutter, so from there you can uninstall unity so you'd have only  mutter to work for you.  [http://blog.burrowsapps.com/2012/09/ubuntu-completely-remove-unity.html](http://blog.burrowsapps.com/2012/09/ubuntu-completely-remove-unity.html)  You can uninstall compiz too. Then you are free of that heaviness.

> I'm retired and if I ever felt that I ***must*** do anything I'd ***not*** be doing that thing very long :wink:

This, I agree wholeheartedly! There is nothing called* a must. *

---

### Post by Stinger on 2012-12-18
> **Rangir said:**
> That's okay! I think that chap stinger was trying to sting me.:smile:
Hi Rangir, welcome to the Ubuntu forums.
I see you have already guessed why I choose my nickname :mrgreen:

I don't like Unity much as it is, but I do love Gnome and therefore I choose the Ubuntu Gnome Remix.

Your preferences may vary therefore your choice is different, I can accept that, but please don't limit my choice by telling me that we don't need the Ubuntu Gnome Remix.

Linux is about freedom to choose :D

Cheers

---

### Post by Rangir on 2012-12-18
> **Stinger said:**
> Hi Rangir, welcome to the Ubuntu forums.
I see you have already guessed why I choose my nickname :mrgreen:

Ha, ha you are very welcome for sting a little.;)

> I don't like Unity much as it is, but I do love Gnome and therefore I choose the Ubuntu Gnome Remix.Hey, you have a pal here. I don't like it at all, as it curbs my freedom. I might be even thinking on moving to Debian, even though it is bit conservative, Debian doesn't push thing sdown our throats. Unity i sjust ugly, even though Dash is fine.

> Your preferences may vary therefore your choice is different, I can accept that, but please don't limit my choice by telling me that we don't need the Ubuntu Gnome Remix.Maybe, I wrote somewhat in a wrong way. I meant that we can have gnome shell in any way we want it. It can be installed in any Ubuntu derivative. Its a joy, really. Unity is not, oh sorry unity lovers!

> Linux is about freedom to choose :D

CheersAbsolutely! Cheers!):P

By the way, I am a scorpion too!

---

### Post by kansasnoob on 2012-12-18
> **Rangir said:**
> That's okay! I think that chap stinger was trying to sting me.:smile: 

Stinger is OK, OTOH I can be a real stinker at times :p

> There was a mention about unity2d somewhere in the forums, I believe.

Unity-2D is dead .... period. It'll still work in 12.04 until April 2017 though.

> Once you logout and log into Gnome, it works  with mutter, so from there you can uninstall unity so you'd have only  mutter to work for you. 

But with P4M800 graphics you can no longer even use the Ubuntu live DVD/USB to install. And most of the flavors have eliminated the alternate CD's, whereas this disc works without the need of using a mini.iso which is incredibly more time consuming.

> This, I agree wholeheartedly! There is nothing called* a must. *

In deed. If any of this becomes a job to me I'm gone! I could always start building second hand jigsaw puzzles to deal with the frustration of that one last missing piece :lolflag:

---

### Post by screaminj3sus on 2012-12-18
> **Rangir said:**
> If I could install the gnome shell from ubuntu repos and it made my ubuntu a gnome remix, then why do I need an ubuntu gnome remix? Yes, I am still wondering. I have seen the ubuntu gnome remix and found that there is nothing, which ubuntu quantal could give. It was a wasted download time. 

When I write sudo apt-get install gnome-shell in quantal, after a while I have my automatic ubuntu gnome remix. 

Do you think I should have ubuntu quantal in one partition and ubuntu gnome remix in another partition or should I have only one quantal with gnome shell installed? Why do you think I must have 2 partition with the same thing?

It has the advantage of having gnome-shell out of the box + not having a bunch of unity packages installed that I don't need. Downloading ubuntu, installing gnome-shell, and removing all the unity stuff would be a pain compared to just downloading the GS remix in the first place. If you want to just install gnome-shell on an existing ubuntu install there is nothing wrong with that, but the remix does have a purpose.

---

### Post by Rangir on 2012-12-18
> **screaminj3sus said:**
> It has the advantage of having gnome-shell out of the box + not having a bunch of unity packages installed that I don't need. Downloading ubuntu, installing gnome-shell, and removing all the unity stuff would be a pain compared to just downloading the GS remix in the first place. If you want to just install gnome-shell on an existing ubuntu install there is nothing wrong with that, but the remix does have a purpose.

Yes, you are right. Who needs this Unity stuff, anyway!
I didn't think of it that way. Thanks for the hint.
The only thing that's nice is the Dash, but I noticed lot of screenshots with the old slingshot launcher. I am going to search the Net to find that package. It is supposed to be as old as maverick, but seems to be working well with Raring too.

Is there a Precise ubuntu gnome remix? It would be better, if there is one as it would be LTS.

---

### Post by kansasnoob on 2012-12-18
I'd really appreciate if we not let this devolve into opinions regarding one DE or another. This thread has to do with "ubuntu-gnome-remix". It's not meant to represent the approval or disapproval of any DE or distro:D

Opinions belong at the Community Cafe:

[http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

Or possibly at Testimonials:

[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

So let's please NOT kill this well intentioned thread :D

---

### Post by kansasnoob on 2012-12-18
> **Rangir said:**
> Is there a Precise ubuntu gnome remix? It would be better, if there is one as it would be LTS.

No, this was the first effort. I made some notes regarding the use of Gnome classic in 12.04 here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Stinger could probably help you a lot with converting Precise, but ATM I'm almost getting a "troll" vibe. You first complained that there there was no need for this respin and now you're asking if there was a previous respin :confused:

---

### Post by Stinger on 2012-12-18
> **Rangir said:**
> 
Is there a Precise ubuntu gnome remix? It would be better, if there is one as it would be LTS.

Taadaah !
I give you the unofficial [Ubuntu GNOME Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/"), by [Jan Hoffmann]("https://launchpad.net/~jan-hoffmann") :D

I use it for my laptop.

---

### Post by Rangir on 2012-12-18
> **kansasnoob said:**
> No, this was the first effort. I made some notes regarding the use of Gnome classic in 12.04 here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Stinger could probably help you a lot with converting Precise, but ATM I'm almost getting a "troll" vibe. You first complained that there there was no need for this respin and now you're asking if there was a previous respin :confused:

Oh, I didn't complain, and I got some info from others, even you, so I started thinking, and aksed if there was a Precise remix. 

What is a "troll" vibe?

I am reading your thread. So, it'd take time for me to come back here. Thanks for the link.

---

### Post by Rangir on 2012-12-18
> **Stinger said:**
> Taadaah !
I give you the unofficial [Ubuntu GNOME Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/"), by [Jan Hoffmann]("https://launchpad.net/%7Ejan-hoffmann") :D

I use it for my laptop.

Thanks!
Going to download it now!
See you later!:)

---

### Post by Rangir on 2012-12-18
Kansasnoob, that's tons of info. Reading right now. Copying & pasting too.
Thank you very much!:D

See you later.

---

### Post by kansasnoob on 2012-12-18
> **Rangir said:**
> 
What is a "troll" vibe?



That was based on you saying, ["Yes, you are right. Who needs this Unity stuff, anyway!"]("http://ubuntuforums.org/showpost.php?p=12411024&postcount=149")

Trolls in general tend to take threads off-topic and by introducing inflammatory subjects they can get a thread closed :(

Nothing in my OP expresses any opinion regarding Unity or any other DE, I'm simply trying to provide info :D

---

### Post by kansasnoob on 2012-12-18
> **Stinger said:**
> Taadaah !
I give you the unofficial [Ubuntu GNOME Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/"), by [Jan Hoffmann]("https://launchpad.net/~jan-hoffmann") :D

I use it for my laptop.

That is not this :tongue:

Close only counts in ...............

---

### Post by screaminj3sus on 2012-12-18
> **Rangir said:**
> Yes, you are right. Who needs this Unity stuff, anyway!
I didn't think of it that way. Thanks for the hint.
The only thing that's nice is the Dash, but I noticed lot of screenshots with the old slingshot launcher. I am going to search the Net to find that package. It is supposed to be as old as maverick, but seems to be working well with Raring too.

Is there a Precise ubuntu gnome remix? It would be better, if there is one as it would be LTS.

Yes there is, its actually what I'm using currently on my pc because I found gnome-shell 3.6 to be extremely buggy at the moment (I've already ranted about that in some previous posts in this thread lol): [http://ubuntu-gs-remix.sourceforge.net/p/download/](http://ubuntu-gs-remix.sourceforge.net/p/download/)

I've been very satisfied with it, 12.04 + gnome-shell is rock solid :)

---

### Post by kansasnoob on 2012-12-18
> **screaminj3sus said:**
> Yes there is, its actually what I'm using currently on my pc because I found gnome-shell 3.6 to be extremely buggy at the moment (I've already ranted about that in some previous posts in this thread lol): [http://ubuntu-gs-remix.sourceforge.net/p/download/](http://ubuntu-gs-remix.sourceforge.net/p/download/)

I've been very satisfied with it, 12.04 + gnome-shell is rock solid :)

But it is not related to this specific project ](*,)](*,)](*,)

---

### Post by Stinger on 2012-12-18
> **kansasnoob said:**
> That is not this :tongue:

Close only counts in ...............

Well well my friend, have a look at the [first edition of the iso-build-script]("http://bazaar.launchpad.net/~ubuntu-gnome-dev/+junk/iso-build-script/revision/1") where it says "initial commit, based off Jan Hoffmann's work for the Ubuntu GNOME Shell Remix" :shock:

Convinced ? ;)

This is the first 5 lines from the livecd-script.sh
> 1#!/bin/bash
 2 
 3# Thanks Jan Hoffmann from the Ubuntu GNOME Shell Remix for this script
 4# Download the original at [http://sourceforge.net/projects/ubuntu-gs-remix/files/live-script/](http://sourceforge.net/projects/ubuntu-gs-remix/files/live-script/)
 5# Customized by Jeremy Bicha for the Ubuntu GNOME Remix

Never forget your roots.

---

### Post by Rangir on 2012-12-18
> **screaminj3sus said:**
> Yes there is, its actually what I'm using currently on my pc because I found gnome-shell 3.6 to be extremely buggy at the moment (I've already ranted about that in some previous posts in this thread lol): [http://ubuntu-gs-remix.sourceforge.net/p/download/](http://ubuntu-gs-remix.sourceforge.net/p/download/)

I've been very satisfied with it, 12.04 + gnome-shell is rock solid :)

Downloaded it, installed it and playing with it. Appears to be quite solid. Gnome 3.4 has lots of extensions and this remix would be LTS. How did I miss it before, I've no idea.

Shouldn't write about that here, so would you start a topic, screaminj3sus?

---

### Post by kansasnoob on 2012-12-19
> **Stinger said:**
> Well well my friend, have a look at the [first edition of the iso-build-script]("http://bazaar.launchpad.net/~ubuntu-gnome-dev/+junk/iso-build-script/revision/1") where it says "initial commit, based off Jan Hoffmann's work for the Ubuntu GNOME Shell Remix" :shock:

Convinced ? ;)

This is the first 5 lines from the livecd-script.sh


Never forget your roots.

Roots are one thing, but that project and this project are NOT one in the same :)

I notice a few people saying that the 12.04 gnome-shell remix is LTS which is factually incorrect:

> As there are some people asking about the next version based on Ubuntu 12.04: Yes, there will be a new version released shortly after Ubuntu's final release. **It won't be a LTS version, though**, as it contains software from the universe repository that is not supported as long.

Source:

[http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/1/](http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/1/)

Additionally [that PPA]("https://launchpad.net/~jan-hoffmann/+archive/gnome-shell") has recieved no updates since April 2012.

I just don't want to give anyone false info or mislead them into believing that one project morphed into another which is just not true. Here's the announcement of 12.10 on Jan's blog:

[http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/4/](http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/4/)

You'll notice that it says:

> With Ubuntu GNOME Remix coming together with Ubuntu 12.10, there won't be a new version of **my own remix** anymore.

---

### Post by Stinger on 2012-12-19
> **kansasnoob said:**
> Roots are one thing, but that project and this project are NOT one in the same :)
I had my saying and proved the relationship between the two unofficial remix'es, the original from Jan and the improved from Jeremy.
I humbly rest my case ;)

Actually UGR isn't Jeremy's invention originally either, here is the original [UGR Linux]("https://sites.google.com/a/teampr0xy.net/ugr/") and [their wiki page]("https://wiki.ubuntu.com/UGR"), maybe Jan Hoffmann got the idea to his build script from the [UGR-isobuilder page]("https://wiki.ubuntu.com/UGR/IsoBuilder") ?
But that's pure speculation. ;)

---

### Post by Rangir on 2012-12-19
Whatever it is, I'm very glad that Stinger, Screaminj3sus and others, who pointed at this this UGR 12.04. It is a fantastic one. As it is Precise based, the gnome shell would be 3.4.2 and could be updated with whatever updates issued by Precise repos. I understand the ppa is not updated as Kansasnoob say, but any update from Precise would come through. I am more interested in the gnome classic than the gnome shell, so this would sort of work as LTS for me, I believe. Right now, it works superbly. Let's see what it'd bring in. I shall be using it on the doomsday too, whether the world would end that day.:) How did I miss it before, I don't know.

Thanks guys!:D

---

### Post by kansasnoob on 2012-12-19
> **Stinger said:**
> I had my saying and proved the relationship between the two unofficial remix'es, the original from Jan and the improved from Jeremy.
I humbly rest my case ;)

Actually UGR isn't Jeremy's invention originally either, here is the original [UGR Linux]("https://sites.google.com/a/teampr0xy.net/ugr/") and [their wiki page]("https://wiki.ubuntu.com/UGR"), maybe Jan Hoffmann got the idea to his build script from the [UGR-isobuilder page]("https://wiki.ubuntu.com/UGR/IsoBuilder") ?
But that's pure speculation. ;)

But in my OP I clearly stated:

> This project should not be confused with UGR, Ubuntu GNOME Shell Remix, or any other project.

And I verified that the info I was providing was correct with the "Ubuntu-GNOME-Remix" team :)

This is a totally different project, just using someone else's iso script doesn't change that fact.

---

### Post by SpaceAviator on 2013-02-26
are we still alive?

---

### Post by kansasnoob on 2013-02-26
> **SpaceAviator said:**
> are we still alive?

Yes!

[https://lists.launchpad.net/ubuntu-gnome/](https://lists.launchpad.net/ubuntu-gnome/)

It's a small team but "ubuntu-gnome-desktop" is in the repos and will remain there.

What we need are people willing to create a QA team and others willing to create a semi-official wiki :D

Sadly I'm getting long-in-the-tooth so I can't help much but this is a project that needs the help of motivated and capable members.

---

### Post by SpaceAviator on 2013-02-26
> **kansasnoob said:**
> Yes!

[https://lists.launchpad.net/ubuntu-gnome/](https://lists.launchpad.net/ubuntu-gnome/)

It's a small team but "ubuntu-gnome-desktop" is in the repos and will remain there.

What we need are people willing to create a QA team and others willing to create a semi-official wiki :D

Sadly I'm getting long-in-the-tooth so I can't help much but this is a project that needs the help of motivated and capable members.

That's good to hear! I'll sign up right away and see what I can do.

Cheers!

---

### Post by kansasnoob on 2013-02-26
> **SpaceAviator said:**
> That's good to hear! I'll sign up right away and see what I can do.

Cheers!

Cool, you'll find that everyone on the mailing list is quite easy to get along with :)

---

