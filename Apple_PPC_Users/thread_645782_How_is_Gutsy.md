---
title: "How is Gutsy?"
date: 2007-12-20
forum: Apple PPC Users
---

### Post by indica on 2007-12-20
Hey all,

I was running edgy on an ibook g4 800.  I briefly foraged into feisty, then gave up and installed osx.  I needed to run flash for work and I needed it to be fast, uncomplicated, and to work immediately.  I'm finding that osx and microsoft based programs are getting more and more incompatible (like having problems accessing hotmail from osx's browser).  So I'm thinking of switching back, but I wanted your personal opinions first.  How are you finding it?  How's the lack of "support" going?  What are the real issues?

Thanks

---

### Post by ubuntubrian on 2007-12-20
For PPC things are not so good, especially with Gutsy. I still use Dapper because of numerous problems in later distros. Gutsy is the worst by far to date and if you're looking for ease and things like simple flash setups then look elsewhere. Still Gnash for flash (swf) and so it only works for some videos. MPlayer plays flv OK. We PPC folks are being left in the dust.
This is not in anyway meant to disparage the PPC developers. We are a minute niche now and I think I know what it looks like to see extinction heading our way for Ubuntu. Debian still fully supports PPC but you'll find the lack of restricted software means an even less pleasant experience in the media world.
I keep plugging away though and hope springs eternal! (same with the political scene so maybe I'm beating a dead horse here)

---

### Post by stmiller on 2007-12-20
Gutsy is very similar to Feisty. Main differences are that the airport extreme support is now built in, a newer kernel with some under the hood improvements, gnash with youtube playback is standard, and updated versions of gstreamer and such are there.

I think Edgy had major issues, but Feisty was much better. And Gutsy feels to me like a solid update to Feisty.

The 'lack of support' issue is somewhat overblown. Ubuntu is continuing to make PowerPC releases with package and security updates as normal, like any other distro (Suse, Fedora, Debian, Gentoo, etc.). They dropped paid technical support (only). So if you are a business who needs commercial PPC Linux support, you'll have to check out Suse or Redhat.

Check out the [Ubuntu PowerPCFAQs]("https://wiki.ubuntu.com/PowerPCFAQ")! Lots of good stuff there.

---

### Post by Auria on 2007-12-20
@stmiller: I find you are rather optimistic considering there is a major bug preventing booting in it (granted, easy to work around for many/most [?] people) but what is distressing is that last time I checked it was not yet fixed. Canonical dropping paid support is not that bad but if no one fixes PPC bugs we know where we're heading :(

---

### Post by stmiller on 2007-12-20
Ha! Well you are right. I should specify, Gutsy is nice ***IF*** you can get it to install. 

Lots of these Gutsy bugs have finally been assigned to the powerpc team and marked critical, so hopefully we will have fixes soon.

---

### Post by indica on 2007-12-20
Hmmm, some good food for thought here.   With my luck I'll be one of the ones with boot problems.  I'm frustrated with the lack of a good system.  I love the size of my ibook, I'm small and large laptops are a pain for me.  But it's disappointing that I can't find an OS that works well.

---

### Post by gtcoffee on 2007-12-21
The only thing i wanna complain the gutsy is the battery life is about 1 hour shorter than in OSX. i dont use it to watch video/flash,etc. i use it to learn programming, and it does the job. And if you can configure some settings, gutsy works good tho.

---

### Post by ssam on 2007-12-21
i am sticking on feisty for now.

i have a partitiion with gutsy on it, but there are a few things putting me off.
installing it took all the various tricks from the [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) page
sound still is not fixed (on tibook g4 1ghz)
network manager taking all cpu, and doing nothing (using [https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu) to get the hardy version seems to fix it)
about 4 small black squares along the top of the screen (in the gnome panel). not sure what is causing them. i can move the mouse on top of them.
no splash screen. (maybe because i used nosplash to get the installer to boot and this has been kept as a boot option. maybe i could turn it back on in yaboot).
no sleep (have not investigated yet)

if the hardy live cds get fixed i'll do some testing of that. but otherwise i am thinking of sticking with feisty until debian testing catches up with all the software versions I use.

i am sure that ubuntu works al lot better on some other macs, so you may have more luck. my powerbook was pretty much perfectly supported edgy and before (i think the modem did not work, and i never tried TV out).

---

### Post by pbarthelemy on 2007-12-21
Running 7.10 on a iMac PPC rev B ( ALS ) . I am quite happy.
built-in airport support is pretty cool, and my dual boot set-up is stillOK after the upgrade.

Ubuntu is the only distro that booted my iMac correctly and Gusty is the nicest....



--P

---

### Post by ubuntubrian on 2007-12-28
Do you have sound?

---

### Post by pbarthelemy on 2007-12-28
Yes I do have sound.

---

### Post by stmiller on 2007-12-30
Hey ssam:

Your comments are very interesting as I have an 867Mhz Tibook! I upgraded from Feisty and during the upgrade process told it to keep all of my configuration files when asked. The upgrade went fine and I didn't have any issues.

BUT! For the heck of it since this machine is not critical for me I just tried a clean install of Gutsy and I then had the identical problems you mentioned: no suspend, black marks on top of screen, etc. ! :confused:

I'm going to try to get some bug reports going so at least things might be fixed for Hardy.

---

### Post by indica on 2007-12-30
hmmmm, thanks guys! this really helps.  i hate being forced into using osx, but i may wait until work is less busy before switching to something else.  
a friend of mine also just got an eeepc so i'm hoping to check that little sucker out and maybe ebay my ibook, it'll be a sad day, but ya do what ya gotta do.

---

### Post by reuben on 2007-12-30
Feisty worked well (sound, networkmanager, suspend, etc.) Gutsy requires a hack to get started (ide-core), networkmanager works poorly, suspect messes up KDE. I think they've stopped doing QA on powerpc. What other distros are out there that are worth checking out on my g3?

---

### Post by ssam on 2007-12-30
> **reuben said:**
> What other distros are out there that are worth checking out on my g3?

yellowdog, debian, gentoo, fedora

but ubuntu feisty mostly has more up to date packages than the stable versions of the other distros.

---

### Post by ubuntubrian on 2007-12-31
> **pbarthelemy said:**
> Yes I do have sound.

so what was your upgrade method? I may try it after I completely back up my dual boot setup on my TiBook.

---

### Post by pbarthelemy on 2008-01-01
Hello,

I've upgraded from the web, using Synaptics. Pretty simple.
With all the fuzz about Gutsy being on pain on PPC, I guess I am super Lucky, but I find it perfect for me...

--P

---

### Post by ubuntubrian on 2008-01-01
I am completely backed up and I want to try this so I just want to completey copy what you did exactly so please bear with me. Did you change your apt.sources list? Could you post your list please? Did you then use Synaptic and reload and then mark all upgrades?
Please be very specific if you would as I want to give this the best possibloe chance of working. 
When I have upgraded I followed what i wrote above but I sure would like this to work so thanks for being patient. Maybe it won't make a difference but what the heck?

---

### Post by BladeMelbourne on 2008-01-01
Try opening /etc/apt/sources.list and replacing 'feisty' with 'gutsy'.
Then 'sudo apt-get update'

---

### Post by guidop on 2008-01-02
If you would like to start with a clean /etc/apt/sources.list file, a very useful sources.list generating tool, is at:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)


I believe the complete commands for doing a distribution upgrade using apt are:
```

$ sudo apt-get update        # Verify no errors, problems usually are in sources.list file.
$ sudo apt-get dist-upgrade  # Also removes unneeded packages. Answer any config questions.
$ sudo apt-get -f install    # Check upgrade, in case there are additional packages.
$ sudo dpkg --configure -a   # In case additional packages need default configuration.

```
I've successfully upgraded a G3 iMac directly from Dapper to Feisty this way.  Haven't been brave enough to try to upgrade my machines to Gutsy yet...

---

### Post by ubuntubrian on 2008-01-02
I would be upgrading from Dapper to Gutsy (if I have the guts!). Mistake?

---

### Post by AlphaMack on 2008-01-02
You're better off with Feisty.

---

### Post by ssam on 2008-01-03
> **guidop said:**
> If you would like to start with a clean /etc/apt/sources.list file, a very useful sources.list generating tool, is at:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)


I believe the complete commands for doing a distribution upgrade using apt are:
```

$ sudo apt-get update        # Verify no errors, problems usually are in sources.list file.
$ sudo apt-get dist-upgrade  # Also removes unneeded packages. Answer any config questions.
$ sudo apt-get -f install    # Check upgrade, in case there are additional packages.
$ sudo dpkg --configure -a   # In case additional packages need default configuration.

```
I've successfully upgraded a G3 iMac directly from Dapper to Feisty this way.  Haven't been brave enough to try to upgrade my machines to Gutsy yet...

the official upgrade method is
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

this does some extra checks that the dist-upgrade leaves out. it also make sure that you have the ubuntu-desktop metapackage installed (so that you get new packages), and cleans up some old packages that are no longer needed.

---

### Post by guidop on 2008-01-03
Unfortunately, when I tried the Ubuntu recommended upgrade method on Xubuntu (6.06-->+) and Kubuntu (6.10-->7.04) in May to July 2007, the updater would crash at some point and/or leave me with either an unbootable system, or one in which I could not get a (wired) network connection. I wound up either doing a clean install, or dist-upgrade using the more familiar (to me) apt method, and it seemed to work.

Perhaps the (newer version?) upgrade tools in Feisty will work?


I would really appreciate answers to these questions:

1) Have you successfully upgraded from Feisty to Gutsy on **PowerPC**, and what exact steps were used?  Were there any issues after the upgrade, and how were they fixed?

2) Will the official Server command line upgrade method work also for Ubuntu/Kubuntu/Xubuntu etc. desktops?   ```

$ sudo apt-get install update-manager-core
$ sudo do-release-upgrade
```

3) Is there a site where apt vs. aptitude vs. update manager differences are clearly explained?

4) If I did perform a dist-upgrade using apt, rather than the official method, how do I verify whether I am missing the above mentioned packages/metapackages, and how would I go about installing them and cleaning up my install, if necessary?

---

### Post by ubuntubrian on 2008-01-04
I checked the official method and that won't work for Dapper to Feisty. I guess I'd use the method that Guidop posted, which is what I've done before , more or less. Still worried about losing sound in Feisty although the Live CD has sound so maybe it would be fine. Decisions, decisions.....

---

