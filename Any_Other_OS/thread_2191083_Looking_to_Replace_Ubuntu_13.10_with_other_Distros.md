---
title: "Looking to Replace Ubuntu 13.10 with other Distros"
date: 2013-11-30
forum: Any Other OS
---

### Post by swhit3 on 2013-11-30
I've been using Ubuntu for a few years and I am frustrated with 13.10. I've found it to be very buggy, day to day use is annoying, apps freeze and crash regularly, even after a fresh install. I really enjoyed 12.04 and even 13.04 Raring was equally impressive, but 13.10 has shaken my passion for Ubuntu. So I am asking the community for any other alternatives for a Linux distro that is stable, well established, regularly updated (possibly rolling release), that has a community similar to Ubuntu's in terms of forum help and how to tutorials on the web. I'm currently looking at Fedora and Manjaro, not very interested in Linux Mint, but what are some viable possibilities? Any help is appreciated!

---

### Post by Iowan on 2013-11-30
Personally, I still use 12.04. You could revert to either 12.04 or 13.04 (which you liked) and await 14.04. The tutorials/forum should be familiar. ;)

---

### Post by bachtobach on 2013-11-30
I'm looking at Manjaro as well, looks to be stable and a solid distro with great support. I've asked a few things on the forum and IRC and everyone seems very friendly and willing to help. Only tried it on a live usb stick and I liked it. New command lines to learn but that shouldn't be too much of an issue. I'm hoping to install it this weekend to test it (as well as to test my graphics card with later kernels) but I think it could be the one I stick with. At least until I have the knowledge and courage for Arch or Gentoo!

Also, I've heard great things about OpenSUSE so that might be worth looking in to.

---

### Post by mörgæs on 2013-11-30
Before leaving the Buntu family completely I suggest that you try a clean install of Lubuntu 13.10. It's about as stable as it gets.

---

### Post by kurt18947 on 2013-11-30
I find 13.10 pretty good, minimal problems since its release.  I've messed with OpenSUSEs Gnome flavor a little.  It seems fairly familiar as my default Ubuntu desktop is gnome as well.

---

### Post by vasa1 on 2013-11-30
In the last day or so there seem to have have been quite a few threads started with nearly the same content :)

---

### Post by monkeybrain20122 on 2013-11-30
Well if you were happy with 12.04 then why even ask? Just reinstall it and you have support til 2017.

But if you must find something outside the *buntu family I second Manjaro, I have a partition running it and I am quite impressed. If you install the non free image then everything (codecs, flash, video drivers) works out of the box and it is fast. It is based on Arch but is as easy to use as Ubuntu or Mint. It comes with xfce and kde flavours, but you can easily install other DEs (except Unity, which is a Ubuntu thing, but there is a semi working port in AUR)

 If you use Manjaro definitely you must learn how to install stuffs from AUR (ArhUserReositoriy) with yaourt. The standard repository for Manajaro is kind of thin and many third party software (Chrome, skype, etc) only provides .deb and .rpm for Linux so they are not directly installable, but you can find them in AUR along with many strange and cool stuffs that you won't find in standard Ubuntu or Fedora repos. Oh, and it is rolling so there will be no need to upgrade. So far it has been very stable.

---

### Post by kevdog on 2013-11-30
Ohhh, watch the AURs.  Id try to install the least amount out of them if possible -- I know its inevitable.  You'll need some packages that are not included in the standard libraries, however when there is a major kernel or DE upgrade, it always seems when something crashes upon reboot, its do to something previously installed from the AUR that wasn't properly upgraded for the change.

---

### Post by jeehyun on 2013-11-30
Ubuntu gnome or mint will be good. Debian distros are easy to manage os.

---

### Post by buzzingrobot on 2013-12-01
> **swhit3 said:**
> I've been using Ubuntu for a few years and I am frustrated with 13.10. I've found it to be very buggy... alternatives for a Linux distro that is stable, well established, regularly updated (possibly rolling release), that has a community similar to Ubuntu's in terms of forum help and how to tutorials on the web. I'm currently looking at Fedora and Manjaro, not very interested in Linux Mint, but what are some viable possibilities? 

My 13.10 experience doesn't mirror your experience., but c'est la vie.Could be any number of reasons for that.

If you can determine the attributes you are looking for in a distribution, that will help you find something you like without getting stuck in a loop of distrohopping. 

For instance, if you like Unity, then a look at 12.04 LTS is probably in order.  If you want a more traditional panel-based interface, don't trust anything built on Ubuntu 13.10 (like Mint 16) then you're looking at XFCE/MATE/Cinnamon/LXDE on another platform. 

If you want the latest and greatest no matter what, there's Arch and Debian Sid.  Or, you could plant yourself firmly in Fedora's things-will-certainly-break development cycle, aka Rawhide. 

Desktop environments and window managers can be installed on any distribution, so those should not lead your decision.

A tension exists between reliability and regularly updated.  I.e., the more things change, the more likely something will introduce unexpected bugs, which in turn drives more change. So, at one end of the spectrum, we have distributions like Red Hat/CentOS/Scientific that are famously stable and supported for years.  Excellent documentation, especially from Red Hat. The down side:  An old software base that balks at running many contemporary desktop applications and an OS and community primarily focused on server installations. 

Just a bump along the way is Debian Stable.  Strong community and can run the usual contemporary apps, although tomorrow's bleeding edge might be a bit dicey.  Good documentation.

As rolling releases, Arch and its canned derivatives like Manjaro will see the most frequent changes.  That's good for security and bug fixes.  Getting on the rolling release bandwagon means learning the procedures specific to that distribution and making an effort to stay up to speed with the state of the release at any given time. (I did it for a bit.  Tried to run the updates a day or two after availabililty to see if others identified problems.  In the end, the lure of the beeding edge faded.)

I've used Fedora a great deal and it is a fascinating product. Strong community (altho the forum is an independent project) with experienced knowledgable people. Fedora 20 is due to be released in a couple of weeks. I've found its alpha and beta test releases to be very stable.

---

### Post by monkeybrain20122 on 2013-12-01
> **buzzingrobot said:**
> 

Desktop environments and window managers can be installed on any distribution, so those should not lead your decision. 

Except for Unity. :)


> As rolling releases, Arch and its canned derivatives like Manjaro will see the most frequent changes.  That's good for security and bug fixes.  Getting on the rolling release bandwagon means learning the procedures specific to that distribution and making an effort to stay up to speed with the state of the release at any given time. (I did it for a bit.  Tried to run the updates a day or two after availabililty to see if others identified problems.  In the end, the lure of the beeding edge faded.)


Actually Manjaro is not as bleeding edge as Arch, things sit in Arch repos for a while before they become available in Manjaro (I hope with the exception of security patches, this is a criticism against Mint, I will look into that). I find most software in my Manjaro install to be older than their counterparts in Fedora (just normal updates, not rawhide)


> I've used Fedora a great deal and it is a fascinating product. Strong community (altho the forum is an independent project) with experienced knowledgable people. Fedora 20 is due to be released in a couple of weeks. I've found its alpha and beta test releases to be very stable.
 Agree. Fedora is quite fascinating in that it somehow manages to deliver the bleeding edge while still very stable. It is a lot more stable and polished than Debian Sid in my experience and newer packages too.  Sorry, IMO Sid is only 'bleeding' in the sense that it is a bloody mess,--got broken dependencies almost every update,--not in the sense of cutting edge.

---

### Post by swhit3 on 2013-12-01
Hmm I'm thinking perhaps I might try dual booting Fedora and Manjaro and wait it out for those two until the release of 14.04 which I hope will be rock solid.

---

### Post by rousseau09 on 2013-12-01
Maybe try Kali Linux (based on Debian). It's a pentest distro but I've found it really stable for my usage. 
[http://www.kali.org/](http://www.kali.org/)
I also maintain a small website to help and support Kali. Might try it as well [http://www.blackmoreops.com/](http://www.blackmoreops.com/)
Hope that helps in your search of finding an alternate.

Note: You might want to try Kali in a VBox first. Kali doesn't like USB method too much, requires some skills. But then again, if you've used Ubuntu for few years, that won't be a problem.

---

### Post by BBQdave on 2013-12-02
As offered by others... Ubuntu Unity 12.04LTS (smooth and stable, and you have through 2017).

I would also offer that Fedora 20 beta with Gnome 3 is incredibly stable, and Gnome 3 has finally arrived with nice polish and function.

Be careful though, I gave F20-beta Gnome 3 a test spin, and now it is my daily driver :D

---

### Post by swhit3 on 2013-12-04
Hmmm Fedora 20 with Gnome 3.10 does look pretty interesting, but not sure how stable it will be when it's released or how much of a learning curve it is from Ubuntu

---

### Post by mips on 2013-12-04
My vote goes to Manjaro ;)

---

### Post by r-senior on 2013-12-04
I switched to Fedora (Gnome) for a while and enjoyed it.

Things I had to spend time adjusting to:

a. Fonts: I found the rendering poor but there are guides to set it up with the Ubuntu font and rendering settings.
b. Yum: A different beast from apt, which takes some getting used to. I found the GUI (PackageKit?) less than good.
c. Package breakages: Not many but more than with apt.
d. Ran into some problems with SELinux and ended up disabling it IIRC

Fedora implements the free software ethos more strictly than Ubuntu and I resorted to RPMFusion for some things that I can't remember but probably media stuff.

The forums are pretty good, quieter than here but plenty of help if you need it. I still lurk over there and post from time to time. I think I joined the forum at a bad time because there were a few flame wars and bans in the first week I subscribed. It doesn't have the same sort of CoC as this forum and things can get out of hand. Expect some Ubuntu bashing too. ;)

It was certainly stable enough despite the bleeding edge reputation and not really more difficult, just different.

I've got a couple of other things running in VMs that I would consider for my desktop. OpenSUSE is looking nice these days but I suspect it would be another learning curve with Yast. Elementary OS is a nice minimal option and I'm interested to see what they come up with for their release next year.

---

### Post by swhit3 on 2013-12-08
Installed 12.04, got tired of it within an hour, so installed the latest Manjaro build. Other than my function keys not working, every thing has worked right out of the box. It's basic, slick, and fast. Don't know if I'll stick with it for too long, Fedora 20 comes out in a week or so and I'm very tempted to give it a try!

---

### Post by monkeybrain20122 on 2013-12-08
> **r-senior said:**
> 
I've got a couple of other things running in VMs that I would consider for my desktop. OpenSUSE is looking nice these days but I suspect it would be another learning curve with Yast. Elementary OS is a nice minimal option and I'm interested to see what they come up with for their release next year.

I don't think OpenSuse likes dualboot except with Windows. I had tried to set it up as a triple boot with Ubuntu and Fedora but it never worked because the installer insisted that I already have a / partition and refused to make another one (Hello? Of course I already have a /, it is a dual boot) and then the screen for installing grub is so confusing that I don't even know if there is an option to choose where to install it.

Fedora since 18/19 seems to have removed the option to not to install grub, so now I have to always reinstall grub into Ubuntu's partition after installing Fedora. It is also peculiar of Fedora 19 that if I clone it and restore it on another hard drive it won't even boot, have to boot into rescue mode to run drcut something. I have no such issue with debian based distros and Manjaro (or Fedora 18) Fedora by and large is stable and good but from time to time there are gottchas, I agree that selinux can be a pain.

---

### Post by kevdog on 2013-12-08
Ubuntu is great -- it really is.  But on the other hand its a very nice life experience to really try out other distros and learn things that are non-Debian based as well.  It really broadens your horizons -- if you have time for all the shananagins of course.

---

### Post by sammiev on 2013-12-08
I triple boot and sometimes more. At this time I'm running Ubuntu14.4 - W7 - Opensuse13.1
Opensuse13.1 is my main OS at this time but still spend an hour or two a day on Ubuntu14.4 which has been rock solid to date.

---

### Post by oldos2er on 2013-12-09
> **swhit3 said:**
> I've been using Ubuntu for a few years and I am frustrated with 13.10. I've found it to be very buggy

Have you tried any of the other *buntu "flavors"? Kubuntu, Lubuntu, Xubuntu? I'm running Ubuntu Server with X and a window manager installed, and it's very stable.

Other than that, here's another vote for OpenSuse 13.1, the KDE version is quite nice.

---

### Post by orb9220 on 2013-12-09
[Found SolydXK]("http://solydxk.com/") has a Xfce and KDE Debian semi-rolling based on testing a solid performer.
Comes out with a monthly update pack where testing goes thru another round of testing for stability & bug issues.
Last 4 updates where problem free for me.

So no more required recommended clean installs everytime a new version comes out.
And pretty fresh apps also Running KDE 4.11.4 and 3.11-2 Kernel and pretty fresh apps.
Been smooth,snappy and trouble free experience for me.
.

---

### Post by buzzingrobot on 2013-12-09
It's worth noting the Ubuntu ships with the Apport bug reporting tool enabled, while many distributions do not ship with it or an equivalent enabled by default.  The absence of popup messages in those distributions alerting the user to a problem does not mean problems do not happen.

I have found 13.10 to be exceptionally smooth and stable. While, early on, I did see the occassional Apport crash report, I can't recall any that actually impacted the behavior of the system.  I.e., without the Apport alert, I would not have noticed a thing. (And almost all of the Apport alerts are I did receive were triggered by unsupported packages I had installed from outside the Canonical universe.)

---

### Post by sammiev on 2013-12-09
> **orb9220 said:**
> [Found SolydXK]("http://solydxk.com/") has a Xfce and KDE Debian semi-rolling based on testing a solid performer.
Comes out with a monthly update pack where testing goes thru another round of testing for stability & bug issues.
Last 4 updates where problem free for me.

So no more required recommended clean installs everytime a new version comes out.
And pretty fresh apps also Running KDE 4.11.4 and 3.11-2 Kernel and pretty fresh apps.
Been smooth,snappy and trouble free experience for me.
.

Time to play again!
Thanks

---

### Post by monkeybrain20122 on 2013-12-09
> **sammiev said:**
> I triple boot and sometimes more. At this time I'm running Ubuntu14.4 - W7 - Opensuse13.1
Opensuse13.1 is my main OS at this time but still spend an hour or two a day on Ubuntu14.4 which has been rock solid to date.

Do you know how to multiboot with OpenSuse if it is NOT the main OS? Seems that you can only do a multiboot if you install OpenSuse first,--unless the other os is Windows,-- and let it control grub (grub legacy?) I tried to add it to a dual boot (Ubuntu 13.10 and Fedora 19) but the installer refused to make another / partition because it already exists (one for Ubuntu, one for Fedora) It is a show stopper for me if there is no way around it since I don't intend to use it as my main OS. So instead I installed Manjaro in the spared space and it is quite nice.

---

### Post by sammiev on 2013-12-09
I had a extended partition about 250 gib. I shrunk the partition to about 170 gib and left the rest as unallocated and then boot opensuse13.1 live and installed. On install opensuse found the unallocated space and installed itself. I included a pic of gparted after the instillation.

edit: opensuse is sda7 and sda8 are opensuse3.1 Sda5 is ubuntu14.1 Sda6 is my linux-swap. GL and remember to backup your data 1st.

---

### Post by monkeybrain20122 on 2013-12-10
So when you installed OpenSuse the only OS was Windows on the ntfs partition, that means you installed OpenSuse before you installed other Linux distrosm, right?  In your set up I guess OpenSuse also is the OS in charge of booting, correct?

But I couldn't install it when I already had Ubuntu and Fedora installed because I couldn't create new / and /home partitions in the unused space (installer complained that those flags were already used). Before 13.1 its installer didn't even pick up other Linux OSes (at the time I had Ubuntu, Fedora and Debian and it only saw Ubuntu) Finally the screen on installing the bootloader was so confusing that I seriously worried that it would mess up my other distros so I had to abort.  I tried google and I could find no guide for installing OpenSuse along other distros except some old threads (likely outdated) on UF saying that it was hard because of incompatible grub or something, all the tutorials and instructions I could find were dualbooting with Windows which are useless to me.

---

### Post by sammiev on 2013-12-10
> **monkeybrain20122 said:**
> So when you installed OpenSuse the only OS was Windows on the ntfs partition, that means you installed OpenSuse before you installed other Linux distrosm, right?  In your set up I guess OpenSuse also is the OS in charge of booting, correct?

But I couldn't install it when I already had Ubuntu and Fedora installed because I couldn't create new / and /home partitions in the unused space (installer complained that those flags were already used). Before 13.1 its installer didn't even pick up other Linux OSes (at the time I had Ubuntu, Fedora and Debian and it only saw Ubuntu) Finally the screen on installing the bootloader was so confusing that I seriously worried that it would mess up my other distros so I had to abort.  I tried google and I could find no guide for installing OpenSuse along other distros except some old threads (likely outdated) on UF saying that it was hard because of incompatible grub or something, all the tutorials and instructions I could find were dualbooting with Windows which are useless to me.

Nope I installed opensuse after that, that is why it was on /dev/sda7 and /dev/sda8.
I installed another OS in it's place today. ( wish I knew you had this problem before I did another install ) I could have added this one onto /dev/sda9 and /dev/sda10. If I get time tonight I will try it again. I have all backup to another drive so it only takes me 30 min to undo a ooppppss.

---

### Post by sammiev on 2013-12-10
Ok I shrunk /dev/sda8 and saved. Left the free space as unallocated. Booted on USB/DVD installation media of opensuse13.1 and it asked me if I wanted to have /dev/sda9 and /dev/sda10. I select next and carried on. Pics attached. So now I have 4 OS on one HD -> W7 - Ubuntu14.1 - Solydxk - opensuse13.1 and all working. :)

---

### Post by monkeybrain20122 on 2013-12-11
> **sammiev said:**
> Ok I shrunk /dev/sda8 and saved. Left the free space as unallocated. Booted on USB/DVD installation media of opensuse13.1 and it asked me if I wanted to have /dev/sda9 and /dev/sda10. I select next and carried on. Pics attached. So now I have 4 OS on one HD -> W7 - Ubuntu14.1 - Solydxk - opensuse13.1 and all working. :)

Did you make /dev/sda8 and /dev/sda9 / and /home for OpenSuse? No complaint from the installer? Where did you install grub?

---

### Post by sammiev on 2013-12-11
> **monkeybrain20122 said:**
> Did you make /dev/sda8 and /dev/sda9 / and /home for OpenSuse? No complaint from the installer? Where did you install grub?

yes / and /home I left the grub as default. No complaints from the installer. Always backup your data first.

---

### Post by swhit3 on 2013-12-13
So I've been using Fedora 19 for about a week now and I gotta say wow was I wrong about Fedora. I've always been against using GNOME as a desktop ever since the inception of Unity, but after using Fedora I have to say I was dead wrong. I know it's not for everyone, some people are really against GNOME and it's "simplicity" or lack of features/removal of features, but after using Ubuntu, Manjaro, and Fedora, I am totally going to stick with Fedora. It works well for me, everything has worked like it should and GNOME feels snappy and fresh compared to Unity, which still seems a little half baked, I wouldn't call it totally finished yet, but then again what really is ya know? Fedora 20 comes out in a couple of days, new GNOME version and improvements all around, pretty excited about it now that I'm very impressed with what Fedora has put out. If you can put your bias aside, I would encourage anyone to try Manjaro or Fedora to see how they work for them because I for one am glad that I tried something else. Ubuntu still rocks though, love its community more than anything!

---

### Post by monkeybrain20122 on 2013-12-13
> **swhit3 said:**
>  It works well for me, everything has worked like it should and GNOME feels snappy and fresh compared to Unity, which still seems a little half baked, I wouldn't call it totally finished yet, but then again what really is ya know? 

I have exactly the opposite feeling re. gnome shell vs Unity. I like both, but to me Unity feels smoother for multi-tasking with the appropriate compiz plugins enabled. The dash in Unity is more powerful (search files as well, I disable web search) and better organized. The notifying area  in GS is badly design  IMO (if you open something that goes to  the panel like skype I bet you'd have a hard time knowing what happens  because it seems that it just disappeared) The virtual desktops and the activity corner to expose them are at opposite sides of the screen and there is no way as far as I know to expose the virtual desktop by moving the mouse to the edge (like Unity) It feels rather awkward. With gnome shell I always feel a bit claustrophobic. The default settings in gnome shell  are crazy IMO, for examples, no log out, almost all touchpad functions disabled, no filter or grouping for applications in the dash..

But not to sound overly negative, with some tweakings with dconf-editor and the tweak tool, plus a few extensions gs can be made quite usable, I prefer it over all the 'traditional desktops' but I just like Unity better. :)

```
If you can put your bias aside, I would encourage anyone to try Manjaro  or Fedora to see how they work for them because I for one am glad that I  tried something else 
```

I like them all, so I triple boot. :) Ubuntu is the main os, but I also do some work in Fedora. Manjaro is at the moment just for experiment, I wanted to use it as a gateway to Arch but find it very nice.

---

### Post by linuxyogi on 2014-01-02
I installed Fedora 20 day before yesterday mainly coz I want to use selinux. 

My home was on a separate partition so I mentioned that during the installation. 

The installation went fine.  

When I typed my password at the login screen the Desktop wont appear. So I logged in as root, created another account and logged in using that. Then when I tried to copy the files from my old home folder to the new one I got file permission problem. So I used chown as root then moved all the files.

IMO the only feature of Fedora that is superior to Ubuntu is the delta rpms. It saves a lot of time and downloading speacially on low speed connection.

After updating the system I installed all the apps of my choice.

Then there was another issue. When I tried to open some apps for example Firefox or Thunderbird the whole screen was getting filled with colors and the entire system hanged.

Then I tried installing the nvidia proprietary diver from rpmfusion. The installation was ok but after reboot I got a black screen. So I removed the driver from the command line and got the GUI back. But the graphics issue remained.

I was totally frustrated at this point so I Xubuntu 12.04 again.

I have used a lot of distros. Obviously not all of them. In my limited experience openSUSE is the only distro I like besides Ubuntu.

---

### Post by Bucky Ball on 2014-01-02
Yea, probably repeating things, but wondering why you didn't stick with 12.04 LTS if that suited. Supported until April 2017.

I've been getting into VirtualBox over the last couple of weeks and have tried about fifteen new distros. Am using the solid 12.04 LTS as host, though. ;)

---

### Post by buzzingrobot on 2014-01-02
> **Bucky Ball said:**
> Yea, probably repeating things, but wondering why you didn't stick with 12.04 LTS if that suited. Supported until April 2017.

I've been getting into VirtualBox over the last couple of weeks and have tried about fifteen new distros. Am using the solid 12.04 LTS as host, though. ;)

I make a big deal of font rendering and it seems to me it's better on 13.10 than 12.04.  Maybe that's due to changes in freetype from upstream?

---

### Post by monkeybrain20122 on 2014-01-02
> **linuxyogi said:**
> 
Then I tried installing the nvidia proprietary diver from rpmfusion. The installation was ok but after reboot I got a black screen. So I removed the driver from the command line and got the GUI back. But the graphics issue remained.



Still not working? I think you need to install kmod-nvidia in addition to akmod-nvidia at this point because somehow akmod doesn't build the kmod due to a problem in rpmfusion that affects all proprietary drivers (not just Nvidia)

I am sticking to F19 for now.

---

### Post by buzzingrobot on 2014-01-02
I've often seen Nvidia installers, regardless of distribution and including the .run package from Nvidia, fail to run nvidia-xconfig.  That creates the xorg.conf file that must be there to support the driver. Without it, the system will very likely reboot to a black screen.

So, I always run "sudo nvidia-xconfig" after installing Nvidia. If xorg.conf was, in fact, created, that file will be backed up and a new xorg.conf created with the same content.

---

### Post by monkeybrain20122 on 2014-01-02
> **buzzingrobot said:**
> 

So, I always run "sudo nvidia-xconfig" after installing Nvidia. If xorg.conf was, in fact, created, that file will be backed up and a new xorg.conf created with the same content.

I did. The problem with F20 apparently has nothing to do with this. 

Also in Fedora I always have to manually removed/disable the nouveau driver even though some people claim it is not required any more since F18, but if I don't do that it always fails to boot. I dual boot with Ubuntu on same machine and use the same version of Nvidia driver (in Ubuntu use xorg-edgers), never have any issue with installing nivida driver on the Ubuntu partition.

---

### Post by buzzingrobot on 2014-01-02
> **monkeybrain20122 said:**
> I did. The problem with F20 apparently has nothing to do with this. 

Also in Fedora I always have to manually removed/disable the nouveau driver even though some people claim it is not required any more since F18, but if I don't do that it always fails to boot. I dual boot with Ubuntu on same machine and use the same version of Nvidia driver (in Ubuntu use xorg-edgers), never have any issue with installing nivida driver on the Ubuntu partition.

'Tis strange, this Nvidia thing.  I know people report all kinds of trouble with Nvidia on Fedora; the forum over there has plenty of them.  For whatever reason, I haven't had problems, on multiple Fedora installs on different hardware.  I follow the howto at rpmfusion, run nvidia-xconfig, and all is well.

Now, when I had a machine with a Radeon card, things were very, unhappily, different.

---

