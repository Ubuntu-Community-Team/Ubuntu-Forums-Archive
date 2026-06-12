---
title: "Where to download Ubuntu for PowerPC and other frequently asked questions"
date: 2007-04-29
forum: Apple Hardware Users
---

### Post by ssam on 2007-04-29
Ubuntu for PowerPC is now a community supported platform (the [announcement]("https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html")). This means that ISO downloads have mean moved to the ports section of the Ubuntu sever, and no longer on most mirrors. You can download them from

[ubuntu-12.04-desktop-powerpc.iso]("http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-desktop-powerpc.iso")
[ubuntu-12.04-alternate-powerpc.iso]("http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-alternate-powerpc.iso")

There is a more complete and up to date list of download locations at: [Ubuntu PowerPC Downloads]("https://wiki.ubuntu.com/PowerPCDownloads")

Answers to other PowerPC questions can be found in the [Ubuntu PowerPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ"). And there is useful information at [Ubuntu PowerPC Known Issues]("https://wiki.ubuntu.com/PowerPCKnownIssues")

---

### Post by Najand on 2007-04-30
Do you have any idea where repositories are? Or is there any available at all?

---

### Post by ssam on 2007-05-01
```

## the main repos
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## security
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe

#backports
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```

---

### Post by jcompton on 2007-05-04
Can somebody expand the explanation of how to do a proper 7.04 full Xubuntu install? Right now it simply says  "It would be possible to install with this and then upgrade to the final release." which is a little vague for newcomers.

Does anybody know *why* there's no Xubuntu PPC final? Arguably it's the most useful of all the Ubuntus for PPC users, since it tends to cater to machines of a spec lower than that you'd want to comfortably run OSX on.

---

### Post by stmiller on 2007-05-04
> **jcompton said:**
> Can somebody expand the explanation of how to do a proper 7.04 full Xubuntu install? Right now it simply says  "It would be possible to install with this and then upgrade to the final release." which is a little vague for newcomers.

Does anybody know *why* there's no Xubuntu PPC final? Arguably it's the most useful of all the Ubuntus for PPC users, since it tends to cater to machines of a spec lower than that you'd want to comfortably run OSX on.

sudo apt-get install xubuntu-desktop

---

### Post by Grexe on 2007-05-08
wish I had found this thread earlier - had to go through Ubuntu->Kubuntu migration because I could not find the PPC ISO with Google ;)

A note on repositories: I also had problems in finding repositories, also for Austria, the mirrors that are configured by the installer do not offer any PPC-binaries, so this is actually a bug.

You can use this handy [repository-generator]("http://www.ubuntu-nl.org/source-o-matic/") but be sure the mirror you select offers PPC-packages (just open one of the repository-URLs in your browser and look in dists/<your distro>/ if it contains a PPC-directory.
In my case, I had to switch to "Germany", you may want to pick the closest match that offers PPC-packages.

---

### Post by Grexe on 2007-05-08
reported as bug #113283 at
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/113283](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/113283)

---

### Post by Najand on 2007-05-10
Seems repositories are all available through all official mirrors.

---

### Post by JaceMan on 2007-05-19
> **ssam said:**
> ```

## the main repos
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## security
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe

#backports
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```

Quick question... can I do a dist-upgrade from a previous install with these sources or would I be best served to download an ISO an do a FRESH install?

---

### Post by DaDave on 2007-05-20
> **JaceMan said:**
> Quick question... can I do a dist-upgrade from a previous install with these sources or would I be best served to download an ISO an do a FRESH install?

I did a dist-upgrade (xubuntu 6.10 to 7.04) with no problems...

---

### Post by pamag on 2007-05-25
> **ssam said:**
> ```

## the main repos
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ [COLOR="Red"]dapper[/COLOR]-updates main restricted

## security
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu [COLOR="Red"]dapper[/COLOR]-security main restricted universe

#backports
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```

Beware of the **typo:** some of the sources repositories are pointing to **dapper instead feisty**

---

### Post by DaDave on 2007-06-05
Where can I find the "mini.iso" for edgy or fiesty? The link on psychocats mini page is broken.

---

### Post by stmiller on 2007-06-06
> **DaDave said:**
> Where can I find the "mini.iso" for edgy or fiesty? The link on psychocats mini page is broken.

There should be one for Edgy located in this directory, on your favorite mirror:

/ubuntu/dists/edgy/main/installer-powerpc/current/images/powerpc/netboot/

[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

---

### Post by DaDave on 2007-06-07
> **stmiller said:**
> There should be one for Edgy located in this directory, on your favorite mirror:

/ubuntu/dists/edgy/main/installer-powerpc/current/images/powerpc/netboot/

[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

Thank you! I found both. Much appreciated...

Dave

---

### Post by avtolle on 2007-06-13
I've successfully installed Java from the Medibuntu repo. Based upon prior experience, I selected the sdk version. In order for it to run in Firefox, you will need to build the symbolic link as set out in the Wiki page. For those interested, here's what I did, with success:

In a terminal:
```

mkdir -p ~/.mozilla/plugins
cd ~/.mozilla/plugins
ln -s /usr/lib/j2sdk1.5-ibm/jre/bin/libjavaplugin_oij.so

```

---

### Post by racoq on 2007-06-22
> **ssam said:**
> Ubuntu for PowerPC is now a community supported platform (the [ announcement ]("https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html")). This means that ISO downloads have mean moved to the ports section of the Ubuntu sever, and no longer on most mirrors. You can download them from

[Ubuntu Feisty]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")
[Kubuntu Feisty]("http://cdimage.ubuntu.com/kubuntu/ports/releases/7.04/release/")
[Edubuntu Feisty]("http://cdimage.ubuntu.com/edubuntu/ports/releases/feisty/release/")

Answers to other PowerPC questions can be found in the [Ubuntu PowerPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ")

ssam, update your Thread topic and include the link for Xubuntu isos for PowerPC.
I already changed the powerpc wiki, to reflect the link to final image to the Xubuntu Feisty

---

### Post by ricnmar on 2007-07-20
Thank you very much for this information!!  I too was looking to Google for the PPC versions.  I knew there had to be SOMETHING out there as I had the old Old OLD 5.10 version for PPC, but I wanted to see the newest stuff on my MAC!!

ricnmar

---

### Post by geraschenko on 2007-07-21
> **ssam said:**
> Ubuntu for PowerPC is now a community supported platform (the [ announcement ]("https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html")). This means that ISO downloads have mean moved to the ports section of the Ubuntu sever, and no longer on most mirrors. You can download them from

[Ubuntu Feisty]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")
[Kubuntu Feisty]("http://cdimage.ubuntu.com/kubuntu/ports/releases/7.04/release/")
[Edubuntu Feisty]("http://cdimage.ubuntu.com/edubuntu/ports/releases/feisty/release/")

Answers to other PowerPC questions can be found in the [Ubuntu PowerPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ")
I couldn't find the md5sums for these ISOs. Does anybody know where to find them? I get
2081e7968e35480a8e3550abac3a086a  ubuntu-7.04-desktop-powerpc.iso

---

### Post by chiron80 on 2007-07-23
> **geraschenko said:**
> I couldn't find the md5sums for these ISOs. Does anybody know where to find them? I get
2081e7968e35480a8e3550abac3a086a  ubuntu-7.04-desktop-powerpc.iso

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

If you look at the top of the file list on this page, there is a file called "MD5SUMS".

[http://cdimage.ubuntu.com/ports/releases/feisty/release/MD5SUMS](http://cdimage.ubuntu.com/ports/releases/feisty/release/MD5SUMS)

It looks like what you got is correct (2081e7968e35480a8e3550abac3a086a).

- Ben

---

### Post by trash on 2007-07-26
> **pamag said:**
> Beware of the **typo:** some of the sources repositories are pointing to **dapper instead feisty**

Can somebody please fix this error.

I also keep getting this error, can anybody help?

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) Sub-process gzip returned an error code (1)

---

### Post by infectedproject on 2007-08-06
> **jcompton said:**
> Can somebody expand the explanation of how to do a proper 7.04 full Xubuntu install? Right now it simply says  "It would be possible to install with this and then upgrade to the final release." which is a little vague for newcomers.

Does anybody know *why* there's no Xubuntu PPC final? Arguably it's the most useful of all the Ubuntus for PPC users, since it tends to cater to machines of a spec lower than that you'd want to comfortably run OSX on.

Xubuntu 7.04 for PowerPC
[http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/)

---

### Post by makinasvp on 2007-08-14
grrrrrrrrrrr!!! Why didn't I see this thread before!
I downloaded and burnt both i386 and 64bit version and wondered WHY my iBook G4 would not boot CD. I am SUCH a noob!!!
Thanks so much for this thread! :):)

---

### Post by Appalbarrychestnut on 2007-10-06
> **ssam said:**
> Ubuntu for PowerPC is now a community supported platform (the [ announcement ]("https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html")). This means that ISO downloads have mean moved to the ports section of the Ubuntu sever, and no longer on most mirrors. 

Lord, is nothing EVER easy in Linux land?  Is it too much to ask that the Ubuntu download page include some link or notice of this so that people don't waste a half hour trying to figure out where PPC distros are hidden.  Or as I almost did, just go away assuming that UBUNTU is Intel only.

For a distro that sells itself on user friendliness there is a lot of detective work required for older Mac users to find out that it even exists for our machines.

---

### Post by walter_f on 2007-10-11
> **Appalbarrychestnut said:**
> Lord, is nothing EVER easy in Linux land?  Is it too much to ask that the Ubuntu download page include some link or notice of this so that people don't waste a half hour trying to figure out where PPC distros are hidden.  Or as I almost did, just go away assuming that UBUNTU is Intel only.

For a distro that sells itself on user friendliness there is a lot of detective work required for older Mac users to find out that it even exists for our machines.

I couldn't agree more.

In addition to that the official Ubuntu pages should have the mentioned links to the various community distros, there should be some information as well as to when the daily builds of the community versions have been brought on par (technically speaking) with the release candidates of the i386 and amd64 kind ("tribes" or whatever these major steps are being called by Canonical).

Regards,

Walter.

---

### Post by walter_f on 2007-10-11
> **walter_f said:**
> there should be some information as well as to when the daily builds of the community versions have been brought on par (technically speaking) with the release candidates of the i386 and amd64 kind ("tribes" or whatever these major steps are being called by Canonical).


At least I've found this statement

"Tribe releases are not available for PowerPC, the the daily produced on the day of the Tribe release is effectively the same."

here

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Please note, in addition to Ubuntu proper featuring Gnome, there are current Kubuntu, Xubuntu, etc. versions available in the /ports section of most Ubuntu mirrors as well, and not just for PowerPC but for the Playstation PS3 hardware architecture, too, and each of them in a daily live (Live CD) and a daily (Alternate install CD) flavour.

Some of the mentioned varieties, if not all, are available for the Sun SPARC architecture as well.

Walter.

---

### Post by MikeTheC on 2007-10-14
I have very successfully done 6.10 -> 7.04 upgrades under PPC. The only thing for me is that Linux for PPC doesn't get the love that Linux for x86 does, and this really limits it's usefulness for me. I hate to say it, but particularly for workstation use, Mac OS X is actually the superior choice, even though I would in truth prefer to run FSF/OSS softwre exclusively.

Such is life...

---

### Post by Deacon Nikolai on 2007-10-18
Gutsy is now available for Power PC Macs (and the Sony PS3?) at [http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)

Credit: [http://www.digg.com/linux_unix/Looking_for_Ubuntu_7_10_Gutsy_Gibbon_for_PPC_Macs_IBMs_and_the_Sony_PS3/](http://www.digg.com/linux_unix/Looking_for_Ubuntu_7_10_Gutsy_Gibbon_for_PPC_Macs_IBMs_and_the_Sony_PS3/)

---

### Post by vijaym on 2007-10-19
my problem is that the xubuntu powerpc download done via the torrent - all 600mb -  does not have a site where i can check the md5sum. when burnt to disk the damn thing does not boot or anything like that. 

seems that i have wasted my time and bandwidth!!

any ideas

---

### Post by docinsano on 2007-10-19
Just wondering if Gutsy has fixed the Nautilus bug. I have ubuntu feisty installed on my imac g3 and everything works but Nautilus. Is it a good time to upgrade? Or are people still screaming at nautilus?

---

### Post by Hoby on 2007-10-22
> **stmiller said:**
> sudo apt-get install xubuntu-desktop

I try this command and I get a message saying I already have the latest version. But I'm running Xubuntu 6. It also told me that several packages were not needed anymore so I did the autoremove to get rid of them.. and then strangely, the next time I opened the Update Manager - it presented me with a button to upgrade to 7.10!

I don't know if this will work for other people but just thought I'd share in case it does.

---

### Post by TCE on 2007-10-24
Does anybody know of the error cannot allocate resource region 0 of device 0001.10.19.0 that you get just before usplash and how to fix it.  I learned that this error message has something to do with openfirmware and usb-ohci.  I tried compiling a new kernel with the how to on faq and enabling the usb-ohci in menuconfig, and even though the new kernel boots i still receive this error.  I know there has to be a way around this, and looked all over google for a fix but could not find one.  Please help running out of ideas.

---

### Post by TCE on 2007-10-24
I also would like to know if anybody knows a good how to to walk me through the steps in compiling a new kernel as well as what to enable in menu config for an ibook g3 366MHZ Firewire clamshell.  Thanks

---

### Post by Tommy on 2007-10-25
> **TCE said:**
> I also would like to know if anybody knows a good how to to walk me through the steps in compiling a new kernel as well as what to enable in menu config for an ibook g3 366MHZ Firewire clamshell.  Thanks

If you have ANOTHER machine* that has successfully booted Ubuntu you can compile a special kernel for the ibook. If you only have the ibook, you'll have to find a kernel that will boot it...

*Easiest if the other machine is a PowerPC, though I believe theoretically you can cross-compile kernels on different architectures with some effort.

Here are some basic instructions on compiling an Ubuntu kernel: [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

HOWEVER if you need further assistance (such as with your booting issue) you probably need to find or start another thread -- THIS thread is "pinned" as a FAQ!

EDIT: This is a better FAQ: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)  -- It includes specific directions for compiling a PowerPC kernel.

---

### Post by Lo'oris on 2007-10-29
> **ssam said:**
> Ubuntu for PowerPC is now a community supported platform (the [ announcement ]("https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html")). This means that ISO downloads have mean moved to the ports section of the Ubuntu sever, and no longer on most mirrors. You can download them from

[Ubuntu Feisty]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")
[Kubuntu Feisty]("http://cdimage.ubuntu.com/kubuntu/ports/releases/7.04/release/")
[Edubuntu Feisty]("http://cdimage.ubuntu.com/edubuntu/ports/releases/feisty/release/")

Answers to other PowerPC questions can be found in the [Ubuntu PowerPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ")

first post should be updated for gutsy, shouldn't it?

---

### Post by Tommy on 2007-10-29
> **Lo'oris said:**
> first post should be updated for gutsy, shouldn't it?

I agree, except I think to be kind to newbies we should note that Gutsy has been difficult for many on PowerPC users and Feisty might be the easier place to start until/unless Gutsy gets cleaned up.

---

### Post by vinmal on 2007-11-06
After many hours of burning, booting and googling, I finally figured it out:
Ubuntu Gutsy 7.10 simply **doens't work on Mac/Powerpc**!! ](*,)
Feisty 7.04 does!

It's a step back (for ppc at least).
On i386 I'm very happy about Gutsy!

Long live open source

---

### Post by docinsano on 2007-11-07
So, are there any distros out there that run well on PPC that are beginner friendly? I would love to use ubuntu but, yeah, it doesn't seem to work for PPC. As for feisty, it worked, except for Nautilus, for me anyways. Well, that's all i got. Later

---

### Post by ubuntubrian on 2007-11-17
Debian Etch and Testing, Lenny I think, run on ppc fine.

---

### Post by chris4a on 2007-11-20
I'm running Fedora 8 on a Mac Mini.
Here's a link to download a CD:
[ftp://ftp.crc.dk/pub/mirrors/fedora/linux/releases/8/Live/ppc](ftp://ftp.crc.dk/pub/mirrors/fedora/linux/releases/8/Live/ppc)

You can find other mirrors.
Go to DistroWatch and look them up
from the Fedora data sheet.
Click on fedora in the page hit ratings.

---

### Post by docinsano on 2007-11-28
So what's the word on PPC Gutsy?

---

### Post by carlmccall on 2007-12-11
[SIZE=3] [COLOR=green] [FONT=Comic Sans MS]chris4a: thank you for the Fedora 8 link.  your return karma is [http://softwaresanta.com](http://softwaresanta.com)

Try this:   [http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)
 [/FONT]  [/COLOR] [/SIZE]

---

### Post by crapple on 2008-02-25
I tried to install Ubuntu on my E mac G4 and it wouldn't work. Just kept freezing after installation with alternative CD. Desktop CD didn't run, brought me to a screen which said insert help for help of something like that and wouldn't boot. What am i doing wrong?

---

### Post by Koji-Murasame on 2008-02-27
After working on it for about a day a scrounging around a bit I finally got Xubuntu 7.10 working on a secondhand PowerMac G4 I received. The key was using the alternate install CD and on the after install boot it took me to a screen with an initramfs CLI. Using [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) I found that you need to type in 
```
modprobe ide-core
exit
```
in order to finish booting and add
```
ide-core
```
to /etc/initramfs-tools/modules
then run the command
```
sudo update-initramfs -u
```
after that it was all gravy.

This thread helped out a bunch since I found most of the links in here.

---

### Post by cvmiller on 2008-04-11
I apologize in advance if this question is elsewhere.

What is the update on 8.04 PPC? Will there be a beta, will it be released at the same time as the 'other' versions (24 April)?

Curious minds want to know, and we want to try it out too!

TIA

Craig...

---

### Post by Guayo on 2008-04-27
Hello ssam and everybody!

Can someone please tell me where can I download the xubuntu hardy release?

Thanks in advance!

(Sorry if posted this in a wrong place or way, I'm kinda newbie in this forums stuffs - yes! shame on me -. Thanks anyways for your patience)

---

### Post by Jammy4041 on 2008-04-28
> **Guayo said:**
> Hello ssam and everybody!

Can someone please tell me where can I download the xubuntu hardy release?

Thanks in advance!

For PowerPC, I assume:

If it's Ubuntu your after, you can download it here:

[http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04-alternate-powerpc.iso)

But you might be better off with Xubuntu, as you say. It's not the release, but the daily current version. This might even be better than the release, who knows.


[http://cdimage.ubuntu.com/xubuntu/ports/daily/20080421/hardy-alternate-powerpc.iso](http://cdimage.ubuntu.com/xubuntu/ports/daily/20080421/hardy-alternate-powerpc.iso)


EDIT- This was released just before Xubuntu Hardy came out, but t essentially has the same features as the release.

PS- if you want x64 or x86, you are indeed posting in the wrong place.
 
You can get that here: 

[http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/)

(Try to be specific about what you want, e.g Xubuntu Hardy Heron for PPC.)

Hope this helps!

---

### Post by Guayo on 2008-04-29
Thanks Jammy4041 yes it was PPC i was asking for.

I´ll follow your recommendations next time.

Once again thank you!

---

### Post by crapple on 2008-04-30
Ubuntu 7.4,7.10,8.4


none of them work on my emac g4 all I get is a black screen.

Is there a problem or something with all the community maintained versions?

---

### Post by rupali_4 on 2008-05-02
You can do everything you want to do in a day on [www.baajaa.com](www.baajaa.com). You can look at job openings, find a date, rent an apartment, sell your bike and buy used items. And if you are interested in showbiz you can post your profile along with pics and your video as well. Also Balaji Telefilms is conducting auditions on [www.baajaa.com](www.baajaa.com) . All this and lots more on [www.baajaa.com](www.baajaa.com) !

One of the new features added on [www.baajaa.com](www.baajaa.com) is Yellow Pages. You can create a simple listing of your business for free. But what is really interesting is that you can Create Your Own Website (with your Logo, 5 pics, Company Profile, List of Products & Services, Video) and you get a Free Premium Yellow Page listing. For just Rs.3999/- !
 
Thanks,

---

### Post by egruber on 2008-05-04
I'm an Apple newbie and I tried to search for the answers, but I'm stuck.  I have a Powerbook G3 Model M5343 333 mhz running OS9. I searched the model numbers and I 'think' it's the bronze model which makes it New World and should work.  Am I correct so far?  If so, I cannot get the Mac to boot from the CD (it contains Hardy).  I tried booting while holding the 'c' key (letter c, right?).  I tried again holding the apple, option, shift and delete together, and that did not work.

Is this G3 compatible with Ubuntu?  I know some are not. If so, how do I get it to boot and install?  Also, should I use Hardy or an earlier version?

BTW, I installed Hardy on a windows PC and it worked great!

---

### Post by ChaOConnor on 2008-05-09
I guess I am a tad confused, I thought Hardy wasn't going to be supported on the PPC?  So the torrent on the first thread, is that for a beta or something?  I don't know if I should stick w/ 7.10.  Does anyone know if Hardy Heron has support for the iBook G4's airport card out of the box?

Thanks!

---

### Post by stream303 on 2008-05-10
> **egruber said:**
> If so, I cannot get the Mac to boot from the CD (it contains Hardy).  I tried booting while holding the 'c' key (letter c, right?).  I tried again holding the apple, option, shift and delete together, and that did not work.

Try holding down the "C" key very quickly after powering on and leave it held until you hear or see it booting from the drive.  Seems that some systems are sensitive to the C-key being held down prior to switching on power.

Be sure to burn the image as an iso, not just copy it over, use a CD-R and not a CD-RW, and burn at a speed slow enough for your cdrom to handle.

---

### Post by egruber on 2008-05-12
> **stream303 said:**
> Try holding down the "C" key very quickly after powering on and leave it held until you hear or see it booting from the drive.  Seems that some systems are sensitive to the C-key being held down prior to switching on power.

Be sure to burn the image as an iso, not just copy it over, use a CD-R and not a CD-RW, and burn at a speed slow enough for your cdrom to handle.

Yes, that worked.  I had actually opened another post on this question because this went unanswered for some time.  Thanks for the tip.

---

### Post by Aurora on 2008-05-25
Hi,

I'm trying to upgrade Xubuntu from Dapper to Feisty on an iMac G3.  I can navigate to /etc/apt/sources.lst in the file browser to see what's there; but if I try to edit with

sudo gedit /etc/apt/sources.lst or

sudo nano /etc/apt/sources.lst

I get a blank page in the editor. How do I edit my repos so I can upgrade?

Paul in Seattle

---

### Post by cyberdork33 on 2008-05-25
> **Aurora said:**
> Hi,

I'm trying to upgrade Xubuntu from Dapper to Feisty on an iMac G3.  I can navigate to /etc/apt/sources.lst in the file browser to see what's there; but if I try to edit with

sudo gedit /etc/apt/sources.lst or

sudo nano /etc/apt/sources.lst

I get a blank page in the editor. How do I edit my repos so I can upgrade?

Paul in Seattle
Probably because that is not the name of the file ;)
try sources.l_i_st

---

### Post by stream303 on 2008-05-26
In addition to the usual download sources:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

There is another convenient way to install by using a *mini-iso* to install over the net:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Unlike downloading a whole distro that is likely to want to be ugraded over the net soon after install, these small iso's will pull down the latest updates *right during installation* and can save you a lot of time or costly bandwidth.

I guess they are similar to Debian's "netinst" method.

---

### Post by mamyte18 on 2008-05-29
Premium Membership

Upgrade your account and earn more with Bux.to. The Premium Membership comes with the following features: 
» Surf Ads guaranteed loaded with minimum 20 ads every Day!
» Earn $0.0125 each click and $0.0125 each click from your referrals.
» Priority Payments.
Exclusively for premium members: Get your Prepaid Bux.to MasterCard®
Earnings Example
» You click 20 ads per day = $0.25
» 25 premium referrals click 20 ads per day = $6.25
» Your monthly earnings = $195.00
» Your total annual earnings = $2,340.00
Processing time: 2 working days.
I'm so proud of everybody, who clicks for bux.to and everybody who works at bux.to, they made a fantastic system. You are clicking for a wanderful system. I joined bux.to in the middle of January, but I have to admit that I wasn't brave enough to invest 500$-s with no previous knowledge about the system. So I only bought 115 refs and a premium to test bux.to and I saw that the money is comming back really fast, so in March I bought another 335 refs. So totally I invested 500$-s.

Now I reached 1000$, I duplicated my investments in 1 month. Thank you bux.to! Thanks for the clickers and the advertisers, who made bux.to a smooth running machine! Thanks for everybody, who writes success stories to make people trust the system! And finally, thanks for my referrals, especially for the guy, who bought premium membership 1 week after joining!

We have to continue our journey through the ads. Good luck for everybody!
  
Steps how to register to bux!

1 step:  [http://bux.to/?r=mamyte18](http://bux.to/?r=mamyte18)   go to this site. And register here.
2 step:  [http://www.alertpay.com](http://www.alertpay.com)
Then "SIGN UP", choose your country, then "Personal Starter" and "Get Started"; and write your name and other information. Where need.
Then you will receive a message to your email address.

When the alertpay are created go to link [http://bux.to/?r=mamyte18](http://bux.to/?r=mamyte18), then"I Accept the Terms of Service” and  click butoon register.   And that’s all. You are the member.

To look videos click "Surf Ads". And you will earn your money.
Good luck. Odeta.
If there are ome problems write to me I could help you I promise. [email]odetux18@yahoo.com[/email]

---

### Post by techbangla.net on 2008-06-30
hi, where can i find the ubuntu DVD for PPC? 
i have dual processor G5 and i'm having trouble booting linux. i tried fedora, opensuse, debian. none of them boots. only the mac osx disc boots. now i want to try ubuntu. 

please tell me where i can download the powerpc version of ubuntu dvd. thanks.

---

### Post by stream303 on 2008-06-30
Ubuntu doesn't provide DVD's for any architecture, afaik, although you can get it from third-parties such as magazines and books - but only for the main architectures such as X86.  Your best bet is either Debian, Fedora, or OpenSuse if you want a DVD for PPC. (Debian provides cd, dvd, and netinst for ppc)

In many cases older PPC's can't boot DVD's, and it would be a waste of bandwidth to download a DVD only to find that you have troubles booting it.  That is one reason I don't favor any PPC distro that forces the use of DVD.

I'd recommend reviewing this faq on iso burning:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

In most cases this means burning it as an iso image to CD-R, and at a low(ish) speed such as 4x, and holding down the "C" key while powering up, or holding down the "C" key very quickly after powering on.  In your case you could try burning the cd-image to DVD, but I'd do so at a low speed.

---

### Post by techbangla.net on 2008-06-30
hi stream, that was very helpful. i will try to get Debian net-installer working. if i can't, guess i'll just give up and buy a cheap ibm machine to run linux. thanks for your help.
:guitar:

---

### Post by stream303 on 2008-07-06
Don't get me wrong - just because there is no DVD for Ubuntu doesn't mean that you can't try the CD's (live, alternate, server), or the minimal-iso netinst version - not to mention bittorrents.

---

### Post by Aurora on 2008-07-06
Moved to main Apple User's forum. Unable to delete from here.

---

### Post by grundygreen on 2008-07-10
I have and old lime iMac with what I think is a tricky slot loading CD-rom.
I have best results with an old dapper netboot for installing.
However the mirroras have moved and I can't even load a dapper desktop. 
Someone pointed me to the hardy mini iso.
Is a little tricky but got it to install. 
Problem seem to be having issues with the respository in Britain.
Should I add other mirrors via apt.

---

### Post by Fvistrup on 2008-07-24
You just HAVE to see this
[Look at this!!!](http://s2.gladiatus.dk/game/c.php?uid=63821)

---

### Post by goodluckguys on 2008-08-15
MOVING? ivansmoving.narod.ru LOW PRICES!!!

---

### Post by Adoring on 2008-08-23
Thank you

[COLOR="White"]http://www.al-mohd.com/[/COLOR]
[COLOR="White"]http://www.al-mohd.com/forum/[/COLOR]

---

### Post by ceciliabobbi on 2008-08-23
I took a look at your site and recommend it to my visitors. I agree with you on the importance of becoming valuable in many different areas. I believe that it sustains any entrepreneur during challenges that inevitably occur.
-----------------
cecilia
[Intenet Marketing](http://www.drivenwide.com)

---

### Post by sygrup on 2008-09-04
Do you have any idea where repositories are? Or is there any available at all?
thanks

---

### Post by stream303 on 2008-09-05
Note that ppc packages are no longer on any of the mirrors to save space and bandwidth - they only exist on a ports server now.

From our friends at Xubuntu (and also in the Ubuntu 8.04 LTS errata), make sure your /etc/apt/sources.list file is correct.

This might help out:
[http://xubuntu.com/news/hardy/ports](http://xubuntu.com/news/hardy/ports)

If you aren't running Xubuntu, substitute gedit for mousepad as the editor to use to edit the sources.list file. (or kdesu kate for kde fans, sudo nano for cli, etc)

---

### Post by ! SaY MaN ! on 2008-10-04
ubuntu is great ! :guitar:


[forums]("http://www.3rbloadiz.com/vb") - [games]("http://www.3rbloadiz.com/games") - [video]("http://www.3rbloadiz.com/video") - [upload]("http://www.3rbloadiz.com/up") - [songs]("http://www.3rbloadiz.com/") - [directory]("http://www.3rbloadiz.com/dlil") - [islam]("http://www.3rbloadiz.com/islam") - [movies]("http://www.3rbloadiz.com/movies") - [chat]("http://www.3rbloadiz.com/vb")

---

### Post by ZixPro7 on 2008-10-08
Hi i am new at this point and i have 1 question : can i install ubuntu 8.04 linux (file name : ubuntu-8.04.1-alternate-powerpc)?? or i can only use 7.10 ubuntu linux?? Thanks... I have yellow dog linux 6.0 but i don't like it i can't watch youtube.com videos , skype isnt working, and much slower :D
EDIT: Oh sorry i am asking about PS3 system :)

---

### Post by skulledbird on 2008-10-09
can youguys plz join my forums?
my first forum ever!

---

### Post by PaiPimenta on 2008-10-14
> **docinsano said:**
> Just wondering if Gutsy has fixed the Nautilus bug. I have ubuntu feisty installed on my imac g3 and everything works but Nautilus. Is it a good time to upgrade? Or are people still screaming at nautilus?
I previously had Fedora PPC installed which never opened Nautilus for me, but all versions of Ubuntu I've loaded on my iBook G4 work fine with Nautilus.

---

### Post by pidayman on 2008-10-26
Thank you for this post. I thought beforehand that 6.06 was the last Ubuntu version. I went to Gentoo, then came back and found this. I felt stupid (for not finding this earlier) and happy (because I get to use Ubuntu) at the same time. I can't wait for Intrepid, personally. Hopefully, it isn't too long after its release for the PPC version.

---

### Post by Elephex on 2008-10-30
Afternoon ladies and gents,

 Anyone have a link to Intrepid Ibex for a PPC machine? I cannot find much info and do not even know if it has been released. Can one of you gurus help a "first-cupper" out?

Cheers!

---

### Post by cyberdork33 on 2008-10-30
> **Elephex said:**
> Afternoon ladies and gents,

 Anyone have a link to Intrepid Ibex for a PPC machine? I cannot find much info and do not even know if it has been released. Can one of you gurus help a "first-cupper" out?

Cheers!
if it is, it will be on the ports server, just like Hardy was:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

You might have to trim the hardy part off the address though to see Intrepid.

---

### Post by Elephex on 2008-10-30
> **cyberdork33 said:**
> if it is, it will be on the ports server, just like Hardy was:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

You might have to trim the hardy part off the address though to see Intrepid.

Cheers!! It keeps timing out, so im not sure if it is really there. But i will keep checking back.

Thanks again.

---

### Post by cyberdork33 on 2008-10-30
> **Elephex said:**
> Cheers!! It keeps timing out, so im not sure if it is really there. But i will keep checking back.

Thanks again.
Yes, it is likely overloaded. Someone may have a torrent sooner or later.

---

### Post by roym4 on 2008-10-30
try this URL for an iso image

[http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)

---

### Post by cyberdork33 on 2008-10-30
> **cyberdork33 said:**
> Yes, it is likely overloaded. Someone may have a torrent sooner or later.

Here ya go:
[http://ubuntuforums.org/showpost.php?p=6066509&postcount=1](http://ubuntuforums.org/showpost.php?p=6066509&postcount=1)

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
viva ubuntu!

---

### Post by PaladinZ06 on 2008-11-02
> **cyberdork33 said:**
> Here ya go:
[http://ubuntuforums.org/showpost.php?p=6066509&postcount=1](http://ubuntuforums.org/showpost.php?p=6066509&postcount=1)

Thanks! You :guitar:.

I've been looking for hours for something that will (hopefully) breathe new life into our Mac Mini 1.4Ghz PPC.

---

### Post by n00b0.5 on 2008-11-06
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

---

### Post by Zopiac on 2008-11-16
Ubuntu Hardy PPC, iMac G3 Blueberry

I downloaded the image, burned it, popped it in the iMac, and booted with the 'live video=ifonly' as the normal boot wasnt giving any video output (havent tried with external monitor yet). Boots up, but theres no GUI. startx fails (just making sure) and im not sure what to do now. how would i get this working?

---

### Post by Leslie Viljoen on 2008-11-17
Post this in a new message instead of this thread and you're likely to get more help.

---

### Post by poi555 on 2008-11-23
[Buy Cialis Online](http://www.youtube.com/user/v1addd1cialis)

[Buy Xenical Online](http://community.fotopic.net/user/yyoja2.html)

[Buy Soma Online](http://www.videocodezone.com/users/jaisonmega/)

[Buy Tramadol Online](http://www.livevideo.com/buy-tramadol-online-cv)

[Buy Levitra Online](http://www.articulate.com/forums/members/buy-levitra-online-bo.html)

---

### Post by Steve M on 2008-12-12
> **Zopiac said:**
> Ubuntu Hardy PPC, iMac G3 Blueberry

I downloaded the image, burned it, popped it in the iMac, and booted with the 'live video=ifonly' as the normal boot wasnt giving any video output (havent tried with external monitor yet). Boots up, but theres no GUI. startx fails (just making sure) and im not sure what to do now. how would i get this working?

Hi Zopiac,

Did you get Ubuntu running in the end?

Regarding the above downloads, after having tried both Hardy and Gutsy, desktop and alternative I have to say I am rather disappointed to find they do not work with my Powemac G4.

None of them leave me with a working Mac, with 8.04 I get a frozen screen for my troubles, with 7.10 I get a black screen with an error message.

Anyone have links to actual working Ubuntu downloads which can be loaded to a Mac or is it definitely a PC only OS? Personally I see no point having "may work" download stickies which only waste time, 4 burned discs and a day and a half of time wasted.

---

### Post by Leslie Viljoen on 2008-12-12
It annoyed me too, and South Africa has some of the most expensive Internet access in the world. That's why we created [www.ppclinux.info](www.ppclinux.info). I think it's a must-read before trying *any* linux on a PowerPC machine. Here's what we know of: [http://www.ppclinux.info/wiki/maclin/Known_Issue_Matrix](http://www.ppclinux.info/wiki/maclin/Known_Issue_Matrix)

Now... how to make sure people look at that page *before* downloading an ISO? Not sure.

---

### Post by Leslie Viljoen on 2008-12-12
.

---

### Post by Steve M on 2008-12-12
> **Leslie Viljoen said:**
> It annoyed me too, and South Africa has some of the most expensive Internet access in the world. That's why we created [www.ppclinux.info](www.ppclinux.info). I think it's a must-read before trying *any* linux on a PowerPC machine. Here's what we know of: [http://www.ppclinux.info/wiki/maclin/Known_Issue_Matrix](http://www.ppclinux.info/wiki/maclin/Known_Issue_Matrix)

Now... how to make sure people look at that page *before* downloading an ISO? Not sure.

So after looking at the above links I am none the wiser, I take it the second link is implying that one cannot run Linux Ubuntu on a Powermac G4?

I myself seem to get as far as loading it, use name, password, but as soon as the desk top appears and the network connection appears the screen freezes.

Does the Powermac "have" to have it's AGP card installed over a PCI alternative? I have PCI and AGP cards for this, and I am running a non spec card to utilise an old Apple display.

---

### Post by Leslie Viljoen on 2008-12-12
I'm really not sure about AGP, but I have had Ubuntu/Debian running on my MacMini G4 without the problem you describe. The MacMini has a Radeon card. 

I think solving your problem could help a lot of people, and then we could improve the wiki too. When the screen freezes, can you get to a command prompt using ctrl-alt-f1? Have you tried "video=ofonly" at the boot: prompt before startup? If you can get to a command line before everything freezes you might also be able to try the "fbdev" driver for XWindows that often works when other XWindows drivers fail.

This post might interest you: [http://www.ppclinux.info/boards/1/topics/show/38](http://www.ppclinux.info/boards/1/topics/show/38)

If none of those ideas get you anywhere, can you please repost your request in the main forum? It is much more likely to get attention from someone who has the same machine as you if it has a useful subject line.

---

### Post by volvo520 on 2008-12-16
:guitar: Hello,Best wishes to everybody !
Tradeshoes.,Ltd. is a professional trading company. It mainly deal with shoes. And there are many brands here. (E.g.Nike Dunk, Jordan, Air Force1,LV handbag ,Gucci shoes,Prada shoes,Watches,moblie telephone,Silver Jewelry,and so on) 
Many of goods are on sales. For example, the R4, Jodan 7, Jodan4 are just $30 per each at the moment. The company can guarantee the qualities and delivery time, since we would like to do business in a long termship. Welcome to http:// [http://www.wholesale77.com/](http://www.wholesale77.com/)
                         for more details. And pls click the icon of online service if you need. Then our workers will serve for you.

---

### Post by hdmyg85 on 2008-12-26
This clock projects the time, date, or temp on the wall or ceiling [http://www.liangdianup.com/clocks_1.htm](http://www.liangdianup.com/clocks_1.htm)  some people call
it a ceiling clock but I call it a digital projection clock. I got the black one because at the time that was the only color
they had. But now they have them in black and also in white.

---

### Post by vijaym on 2009-02-12
i never managed to get ubuntu hardy working on my g3 ibook. so moved to debian etch and it worked excellently.

---

### Post by Jammy4041 on 2009-03-13
Some good operating systems for the PowerPC arcitecture are:
 
Debian - has supported PowerPC since 1997, with LXDE, and XFCE. Use Squeeze "Testing".
 
Yellow Dog - good support for G4s and over, sells PS3 with YDL preinstalled but has outdated packages
 
Ferdora- Bang up to date with packages, I think that it's also hidden, though.
 
FreeBSD- Not a linux distro, but essentially uses the same tools. e.g. Firefox etc, and I would think that it is lighter as well, especially if it has XFCE.
 
Personally, I'll go with a Debian/ GNU Linux combination, if you have a G3, which I do.
If you have a G4 and higher, and want the extra support, go with ydl.
If you are interesting in trying something new, try FreeBSD

---

### Post by Jammy4041 on 2009-03-13
Here's where you download those operating systems. (assuming you want CD-sized disks)
 
Debian: [http://cdimage.debian.org/debian-cd/5.0.0/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/5.0.0/powerpc/iso-cd/)
 
YDL: [http://us.fixstars.com/support/downloads/](http://us.fixstars.com/support/downloads/)
 
Fedora is only go if you have a DVD-ROM drive in your computer, and is supplied on DVD only.
 
SuSE, is another great PPC Distro. How could I not have mentioned it in the last post???
It comes on a nice net-install CD, so you will need a worki8ng internet connection when you install.
[http://download.opensuse.org/distribution/11.1/iso/openSUSE-11.1-NET-ppc.iso](http://download.opensuse.org/distribution/11.1/iso/openSUSE-11.1-NET-ppc.iso)
 
FreeBSD: [ftp://ftp.freebsd.org/pub/FreeBSD/releases/powerpc/ISO-IMAGES/7.1/7.1-RELEASE-powerpc-disc1.iso](ftp://ftp.freebsd.org/pub/FreeBSD/releases/powerpc/ISO-IMAGES/7.1/7.1-RELEASE-powerpc-disc1.iso)
 
I do reccommend that you have a look at each distro, before settling on one choice. There are more, but these, I think, are the ones that stand out.

---

### Post by pxwpxw on 2009-03-25
[COLOR="Red"] PowerPC - Installing Intrepid (8.10) - No common CD-ROM drive was detected
 tiresia

The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.

[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)
[/COLOR]

---

### Post by Geshman on 2009-04-12
I have read this entire thread and I am still quite confused. Is it possible to get a graphical linux operating system for a G3 Power PC iMac? If so where do I find it?

---

### Post by pxwpxw on 2009-04-12
> **Geshman said:**
> I have read this entire thread and I am still quite confused. Is it possible to get a graphical linux operating system for a G3 Power PC iMac? If so where do I find it?


Live cd - may be too much for imac g3
Xubuntu & Kubuntu Jaunty (9.04) Beta LiveCD for PowerPC
[http://ubuntuforums.org/showthread.php?t=1117130](http://ubuntuforums.org/showthread.php?t=1117130)

Alternate cd install - text base installer does full desktop install
As listed on post #1, the cdimage.ubuntu.com/ports/releases/ for all ppc versions
Ubuntu 8.10 (Intrepid Ibex)
[http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)

Dont know where you get live cd versions for intrepid or earlier.
you could also ask ppclinux.info.

---

### Post by Tommy on 2009-05-15
> **pxwpxw said:**
> Live cd - may be too much for imac g3
Xubuntu & Kubuntu Jaunty (9.04) Beta LiveCD for PowerPC
[http://ubuntuforums.org/showthread.php?t=1117130](http://ubuntuforums.org/showthread.php?t=1117130)

Alternate cd install - text base installer does full desktop install
As listed on post #1, the cdimage.ubuntu.com/ports/releases/ for all ppc versions
Ubuntu 8.10 (Intrepid Ibex)
[http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)

Dont know where you get live cd versions for intrepid or earlier.
you could also ask ppclinux.info.

you don't have to go far... just go up the file tree at the URL you gave: [http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/) 

You can get the current Jaunty 9.04 and all the other currently-supported releases back to Dapper. 

I'm still seeing the security updates on my Dapper 6.06.1 PPC installation, so I really appreciate the effort to keep it working so long. (Since it's an  Apple Wallstreet II circa 1998 -- an "oldworld" machine -- it's been harder and harder to install new releases.)

---

### Post by Jammy4041 on 2009-05-16
Having Tried out Xubuntu 9.04 on my laptop, I think I may now have to ditch Debian and get Xubuntu. Ubuntu's implementation of XFCE  is far, far better (at default) then Debian's, The only thing lacking is the support, which is why I went to Debian in the first place. So is the community support good enough?

---

### Post by Tommy on 2009-05-17
> **Jammy4041 said:**
> Having Tried out Xubuntu 9.04 on my laptop, I think I may now have to ditch Debian and get Xubuntu. Ubuntu's implementation of XFCE  is far, far better (at default) then Debian's, The only thing lacking is the support, which is why I went to Debian in the first place. So is the community support good enough?

Obviously the best way to gauge that is to try each for awhile. You will have to gauge for yourself whether the Ubuntu support (or lack thereof) suits you better than the Debian support (or lack thereof). 

I see from your .sig that you have a 350Mhz iMac G3. My sense is that there are always a few packages that don't properly support the G3 processor slipping through the cracks, and it takes awhile to get them fixed. Apparently it is difficult to write fast code that runs well on Altivec and non-Altivec processors (roughly speaking, Apple's G4 & G5 processors included Altivec, the earlier ones did not). 

I think bug fixes might come faster wherever most of the PowerPC developers are. Unfortunately I believe there are fewer all the time.

---

### Post by Shazz.ng on 2009-05-19
Can you add this important link to the sticky thread first post ?
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by tiresia on 2009-05-24
Link to download **ISO images** for 
[Ubuntu Jaunty]("http://cdimage.ubuntu.com/ports/releases/jaunty/release/")
[Xubuntu Jaunty]("http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/")
[Kunbuntu Jaunty ]("http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/")

List of all **Ubuntu torrents** 
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

Link to download **minimal CD**
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Link to download **intrd and kernel for PowerPC** (to boot also from USB Stick, netboot,...)
[http://ports.ubuntu.com/dists/jaunty/main/installer-powerpc/](http://ports.ubuntu.com/dists/jaunty/main/installer-powerpc/)

---

### Post by dynamicsys1 on 2009-05-28
I am having no luck attempting to **replace Mac OSX on a Mini-Mac 1.42Ghz PowerPC G4** system. 

The only version I see that works with a PPC is Fedora and due to copyright issues, Fedora will not support DVD encrypted movies nor MP3 without special plug-ins. I have installed the "Mini" version (small 15 meg base of essential files) of the LiveCD for the PPC but it always boot to the OSX main window. Anyway to force OSX to boot from the CD first?

Anyway to get a link for Unbuntu 9.04 version for the PPC Mini-Mac? I have Unbuntu installed on all the the other systems with excellent hardward compatability results.

---

### Post by cyberdork33 on 2009-05-28
> **dynamicsys1 said:**
>  Anyway to get a link for Unbuntu 9.04 version for the PPC Mini-Mac? I have Unbuntu installed on all the the other systems with excellent hardward compatability results.
the post just before yours has links to all the PPC Jaunty downloads.

---

### Post by dynamicsys1 on 2009-05-28
> **cyberdork33 said:**
> the post just before yours has links to all the PPC Jaunty downloads.

I did download and burn the ISO file for the LiveMini CD (14.5 megs) version listed above and the MAC OSX still boots up to the MAC OSX screen. 

Is there a special command I have to issue to force a hard install from the ISO file on the LiveCD on the MiniMac?

---

### Post by tiresia on 2009-05-28
> **dynamicsys1 said:**
>  Is there a special command I have to issue to force a hard install from the ISO file on the LiveCD on the MiniMac?

Press the C-Key at bootup - and read the FAQ about PowerPC ;)

---

### Post by techfanboy81 on 2009-06-07
I'm so thankful that I found and read this thread  I'm having difficulty in downloading the Ubuntu PowerPC.  Posting this thread is very helpful especially to us newbies.

---

### Post by orangepenguin97 on 2009-06-09
the ubuntu website, just click ppc as your archetecture

---

### Post by Doctor J. on 2009-06-24
> **Jammy4041 said:**
> Yellow Dog - good support for G4s and over, sells PS3 with YDL preinstalled but has outdated packages
 
Ferdora- Bang up to date with packages, I think that it's also hidden, though.

Here's my 2 cents worth on the distros i've tried: 

[Yellow Dog Linux] not only has outdated packages, but not very many of those.  For instance, only the core SDL library was available, so exactly two games worked on YDL.  The YDL mail list recommended adding a Red Hat repo, but that didn't work for me and they offered no more assistance beyond that.  That was a while ago, though.  The newer releases are DVD only, no live test, and are aimed at PS3 users.  Thus it may run but not provide all drivers for Apple hardware.

[Fedora] churns out new releases whether they are ready or not.  Fedora 10 was never able to make any sound on my G4 PowerBook no matter how many of their fixes i tried.  Never mind, they ignored that and blithely went on to Fedora 11.  DVD is the default install, and you have to hunt around to find the alternate 7 CDs.  Yes, that's right the system insists on installing all 5 gigabytes of packages whether you need them or not.  That includes drivers for hardware you don't have and languages/fonts you probably won't use.  Then every time this cruft gets updated, the system wants you to download the latest version of uselessness.  Even if you are geeky enough to trick the system into deleting this stuff, it will still come back to you every time they update.  The PPC release does not offer a live test like they do for other platforms, nor is there a KDE disc for PPC.  The security model used in Fedora is somewhat different than Ubuntu and so the 'sudo' command does not work like we expect it to.  F10 does not include drivers for Applish things like pbbuttonsd, so i had to use the 'alien' utility to convert an existing debian package into an installable RPM package.  If you want check it out, look here: [http://fedoraproject.org/en/get-fedora-ppc]("http://fedoraproject.org/en/get-fedora-ppc").

P.S. The link for Debian is already out of date.  Start here: [http://cdimage.debian.org/debian-cd/]("http://cdimage.debian.org/debian-cd/").  Not to nitpick, but i don't see any *.iso for squeeze/testing, and no indication on the debian pages as to how to get it.

---

### Post by cruising on 2009-06-26
Hello there!
I'm so desperate to get ubuntu working on my iBook G4. I have both the desktop and alternate cd images downloaded. Could you give me a detailed step by step instruction to take me all the way through. 

From my experience, I have problems getting past the hard disk formatting stage now. It freezes at 33% and fails. 

Please respond asap. I need it urgently.

Thanks,

Cruising

---

### Post by cruising on 2009-06-26
Sorry for posting this if it is too 'newbie' or already answered elsewhere. I would truly appreciate the help.

---

### Post by leviofan on 2009-06-26
Do you have any idea where repositories are? Or is there any available at all?

---

### Post by Cam42 on 2009-06-28
Jaunty for PPC?

---

### Post by t4thfavor on 2009-06-29
> **Cam42 said:**
> Jaunty for PPC?

Also interested, I am inheriting a dual G5 with 16Gigs of ram and scsi :) This machine needs Ubuntu!

---

### Post by Doctor J. on 2009-06-29
> **cruising said:**
> From my experience, I have problems getting past the hard disk formatting stage now. It freezes at 33% and fails. 

Please respond asap. I need it urgently.

You will probably get better responses if you open a new thread instead of riding the back of a thread called "Where to download Ubuntu for PowerPC and other frequently asked questions".  Besides that, you really don't offer enough information to help troubleshoot what might be a hardware problem.  Are you doing a manual format, or automatic?  Without knowing more, i might suspect the hard drive is going bad.  If you still have it, i'd run the hardware test disc that came with the machine.

---

### Post by pxwpxw on 2009-06-29
[http://cdimages.ubuntu.com/ports/releases/9.04/release/](http://cdimages.ubuntu.com/ports/releases/9.04/release/)

---

### Post by techfanboy81 on 2009-07-11
> **leviofan said:**
> Do you have any idea where repositories are? Or is there any available at all?

I am also searching about repositories.  Here is the link.

[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

I hope this is the answer to your question.

---

### Post by cruising on 2009-07-12
> **Doctor J. said:**
> You will probably get better responses if you open a new thread instead of riding the back of a thread called "Where to download Ubuntu for PowerPC and other frequently asked questions".  Besides that, you really don't offer enough information to help troubleshoot what might be a hardware problem.  Are you doing a manual format, or automatic?  Without knowing more, i might suspect the hard drive is going bad.  If you still have it, i'd run the hardware test disc that came with the machine.

Thanks for the suggestion. I'll do just that. In fact, I've discovered that it is solvable by the command "live-nosplash-powerpc" when installing from the live CD. I used the alternate CD and it did not go through. 

If anyone happens to see this page somehow, here's a link to the PowerPC wiki: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Hope this helps somebody!:)

---

### Post by UbFreak on 2009-10-04
Wow! I never thought this was possible! Thanks!

---

### Post by linuxopjemac on 2009-10-27
I have seen a lot of people who like to install Linux on PPC based Macs but they don't know where to start. Let me tell you one thing, Ubuntu is not officially supporting powerpc since a long time. I tried many things on PPC based Macs and I am most satisfied with Debian now. I run Debian Lenny on a Pismo G3/400, which works well, but don't expect big graphical things there with such hardware. I also know that Debian runs well on ever older beige Macs using BootX (I did it). I have a website dedicated to Linux on Apple Macs. So maybe you will find some nice info for your computer too.

Good luck all of you
Jeroen

[http://mac.linux.be](http://mac.linux.be)

---

### Post by Jammy4041 on 2009-10-28
> **linuxopjemac said:**
> I have seen a lot of people who like to install Linux on PPC based Macs but they don't know where to start. Let me tell you one thing, Ubuntu is not officially supporting powerpc since a long time. I tried many things on PPC based Macs and I am most satisfied with Debian now. I run Debian Lenny on a Pismo G3/400, which works well, but don't expect big graphical things there with such hardware. I also know that Debian runs well on ever older beige Macs using BootX (I did it). I have a website dedicated to Linux on Apple Macs. So maybe you will find some nice info for your computer too.
 
Good luck all of you
Jeroen
 
[http://mac.linux.be](http://mac.linux.be)
 
Many distros have communtiy supported projects such as respins and there are every bit as polished as the offically support . In terms of PPC support, Ubuntu is no different. (BTW, I use Debian Squeeze on my iMac,  and sometimes you want newer application support.)
 
In my opinion, people should know of other distros such as OPENSuSE, Fedora and Debian and their benefits and how it stacks up to Ubuntu in order to make the best decisions for themselves.

---

### Post by Vlammetje on 2009-11-01
What a shame the n9.10 CD .iso file does not actually fit on a CD (705 MB) and is therefore refused by my burning software :(

If only I could get my iBook loaded with pretty much any OS right now... that would help.

---

### Post by Doctor J. on 2009-11-02
> **Jammy4041 said:**
> Many distros have communtiy supported projects such as respins and there are every bit as polished as the offically support . In terms of PPC support, Ubuntu is no different.

Meh.  The last few releases i've tried on my PowerBook have all suffered from various degrees of broken-ness.  This includes regression in things that used to work in early versions, such as Bluetooth; Gutsy wouldn't accept a network connection from either WiFi or ethernet; etc.  My two cents worth is that community supported releases such as this should ignore the release date and do more testing.  The last comment about how the Karmic Desktop iso for PPC doesn't fit on a standard 700 MeBi CD shows a continuing problem in this stuff being released regardless of whether it works or not.  In my mind habitually putting out non-functional releases will only undermine community interest in the distro.

@Vlammetje: Try the Alternate iso, it's 14 MeBi smaller.

---

### Post by mapgie on 2009-11-08
> **Vlammetje said:**
> What a shame the n9.10 CD .iso file does not actually fit on a CD (705 MB) and is therefore refused by my burning software :(

If only I could get my iBook loaded with pretty much any OS right now... that would help.

Exactly the situation I'm in!

---

### Post by HeadHunter00 on 2009-11-25
I don't think that there's a powerpc version for ubuntu

---

### Post by thatguruguy on 2009-11-27
> **HeadHunter00 said:**
> I don't think that there's a powerpc version for ubuntu

There isn't?  I'll have to let me wife know that.  She'll be disappointed, since she's been using Karmic Koala on her old G4 eMac since it came out at the end of October.

---

### Post by PowerPup on 2009-12-08
> **thatguruguy said:**
> There isn't?  I'll have to let me wife know that.  She'll be disappointed, since she's been using Karmic Koala on her old G4 eMac since it came out at the end of October.

Actually, Ubuntu is for PPC as well. :D (But you can only get support through the community forums here.)


[http://cdimage.ubuntu.com/ports/releases/9.10/release/](http://cdimage.ubuntu.com/ports/releases/9.10/release/)
[http://cdimage.ubuntu.com/kubuntu/ports/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/ports/daily-live/current/)
[http://cdimage.ubuntu.com/xubuntu/ports/releases/karmic/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/karmic/release/)

These links are for the latest versions of ubuntu, kubuntu, and xubuntu. 

Enjoy! :D

---

### Post by ghostborg on 2009-12-13
was able to burn it with k3b and overburn selected, nero and brasero would not.

---

### Post by zts-it on 2009-12-13
> **Vlammetje said:**
> What a shame the n9.10 CD .iso file does not actually fit on a CD (705 MB) and is therefore refused by my burning software :(

If only I could get my iBook loaded with pretty much any OS right now... that would help.Encountered the same problem with trying to burn to a CD-R. However, it works fine if you burn the ISO to a DVD. Use the " - " DVD media.

---

### Post by zeroti on 2010-01-23
> **Vlammetje said:**
> What a shame the n9.10 CD .iso file does not actually fit on a CD (705 MB) and is therefore refused by my burning software :(

If only I could get my iBook loaded with pretty much any OS right now... that would help.

you can also overburn using hdiutil in the terminal on os x. (there are ways to do it on other systems too.) just cd into the directory with the iso and use the following command:

```
hdiutil burn name-of-image.iso
```...but replace "name-of-image.iso" with the file name of the iso you are trying to burn. you can burn up to an additional 70 MB.

---

### Post by subslug on 2010-01-27
So next question, how do you get bluetooth working on this piece?

---

### Post by basumarmi1510 on 2010-03-15
Is it too much to ask that the Ubuntu download page include some link or notice of this so that people don't waste a half hour trying to figure out where PPC distros are hidden................... ?

Or as I almost did, just go away assuming that UBUNTU is Intel ..........

wishing happy turn.........

---

### Post by penguirl on 2010-03-26
> **zeroti said:**
> you can also overburn using hdiutil in the terminal on os x. (there are ways to do it on other systems too.) just cd into the directory with the iso and use the following command:

```
hdiutil burn name-of-image.iso
```...but replace "name-of-image.iso" with the file name of the iso you are trying to burn. you can burn up to an additional 70 MB.

How do you set the burn speed in terminal?

---

### Post by zeroti on 2010-04-06
> **penguirl said:**
> How do you set the burn speed in terminal?

to find this out, type "man hdiutil" in the terminal and hit enter. this shows the manual page for hdiutil. then type "/speed" and hit enter. this searches the man page for "speed". this shows that you need to use the "-speed" option. looking back up at the top, it looks like the format would be:

hdiutil burn -speed 2 name-of-image.iso

according to the man page you can use other numbers besides 2, including "max", which is the default option. to stop viewing the man page, type "q".

---

### Post by Doctor J. on 2010-04-12
> **subslug said:**
> So next question, how do you get bluetooth working on this piece?

To begin with, this should really go in another thread and not be tacked on to "where to download Ubuntu for PowerPC".

Sadly, it *did* work in older releases [Dapper Drake comes to mind].  However, Ubuntu's insistence on always having the latest bells and whistles means that stuff that used to work is now broken - even if you stick to LTS releases [which theoretically shouldn't have bleeding edge packages].  After beating my head against the wall numerous time trying to get Bluetooth working under Hardy on my PowerBook i finally gave up.

---

### Post by History500 on 2010-04-14
If I where to install a version of PPC ubuntu on my iBook G4, could I hold option during startup, and boot either OSX or ubuntu from there? A better question would be: Can I keep OSX and still install Ubuntu as a dual boot?

---

### Post by Doctor J. on 2010-04-19
> **History500 said:**
> If I where to install a version of PPC ubuntu on my iBook G4, could I hold option during startup, and boot either OSX or ubuntu from there? A better question would be: Can I keep OSX and still install Ubuntu as a dual boot?

Answer to question 1: not exactly

Answer to question 2: yes

Details: Linux can't trust the boot loader from any other OS, so of course it installs it's own.   On the PPC machines, it is called 'yaboot'.  Instead of holding OPT, it pops up a text menu.  By default it is set to dual-boot OSX and Ubuntu, with options to boot from CD, etc.  It is easily expandable/configurable, so you can triple- or quadruple-boot if you've got the room on your hard drive.

---

### Post by sastusbulbas on 2010-04-19
> **basumarmi1510 said:**
> Is it too much to ask that the Ubuntu download page include some link or notice of this so that people don't waste a half hour trying to figure out where PPC distros are hidden................... ?

Or as I almost did, just go away assuming that UBUNTU is Intel ..........

wishing happy turn.........

Sadly Ubuntu IS for Intel, well it seems that way for me as I have yet to find a Linux Distro that works out the box with my G4 PPC.

Whereas any old PC for £20 or less seems quite capable of working results with Ubuntu straight.

Edit, why do we have no statement on the apple users thread stating Ubuntu (or any other Linux) will NOT give a fully functioning computer? If it's not flash or video content on internet its graphic resolution, or colour, or not recognising CD or DVD or hardware issues such as inoperatable dvd drives etc etc. Evety year I come back to Linux to see if anything has changed and every year the same problems, if I was to put cost to the time I have wasted with Ubuntu on the PPC I could have bought a retail OS that works for less with less hassle and working out the box. 

The guys making these OS's up need to decide if they are going to allow people to waste time money and resources on a not fully functional OS, or a sticky to highlight pitfalls arise when using with certain hardware so at least people can get a better idea of what to expect instead of wasting hours on something that cannot display Youtube vids or operate a CD/DVD drawer, or only has a resolution of 800+600.

---

### Post by Doctor J. on 2010-04-26
I agree with your main conclusion, but question this statement:

> **sastusbulbas said:**
> Evety year I come back to Linux to see if anything has changed and every year the same problems, if I was to put cost to the time I have wasted with Ubuntu on the PPC I could have bought a retail OS that works for less with less hassle and working out the box.

Just what commercial OS were you planning on getting?  Retail stores have been X86 only for years.  Sadly, business developers gave up on us long ago.  Your choices now seem to be to restore whatever OS the machine shipped with, or see what the hobbyists have to offer.

In a way, it's not a bad situation to be in.  I experienced things the other way when Commodore/Amiga went out of business.  In my case, i was quite happy with the OS but the hardware wasn't working anymore.

---

### Post by sastusbulbas on 2010-04-27
> **Doctor J. said:**
> I agree with your main conclusion, but question this statement:



Just what commercial OS were you planning on getting?  Retail stores have been X86 only for years.  Sadly, business developers gave up on us long ago.  Your choices now seem to be to restore whatever OS the machine shipped with, or see what the hobbyists have to offer.

In a way, it's not a bad situation to be in.  I experienced things the other way when Commodore/Amiga went out of business.  In my case, i was quite happy with the OS but the hardware wasn't working anymore.

Can get new or used Windows 7 (32bit or 64bit) or XP Pro (32bit or 64bit) or Apple Tiger or Leopard and such from eBay every so often for around £30 to £80, I bought OSX 10.4 Tiger family pack (5 users) for £60. 

Some time back I bought XP Pro for £30 odd retail new and unused (from an eBay store with plenty of new copies) and Windows 7 Ultimate I bought for £80 new unused unopened, I have seen Windows 7 from £60 retail and Snow Leopard from £32 retail all new unused from eBay stores. For old G3's and such Panther is usually availale somewhere for around £30, Tiger for around £60

My upstairs PC is W7 64bit (I may change the upstairs PC to Ubuntu or Mint seeing as PPC is not Mac compatible) my downstairs PC is W7 64bit, my Mac will now be Tiger 10.4

Edit; Received my Tiger OSX 10.4 yesterday, installed it and updated to 10.4.11 with all updates up to date, and also installed a Genuine copy of Windows XP as a virtual PC within my Mac OS. The Mac is working well with XP a little slow as it's running as virtual. None of the issues I experienced with Ubuntu raised their heads.

Take your hourly rate of pay, multiply your hours spent finding out Ubuntu does not work and that gives you a rough idea of Ubuntu's cost. Time is not free.

---

### Post by roym4 on 2010-04-30
Since you're convinced that Ubuntu is not an acceptable option for you, and you've found better options, why are you still complaining about it here on Ubuntu forums?

---

### Post by zipperback on 2010-04-30
> **sastusbulbas said:**
> Sadly Ubuntu IS for Intel, well it seems that way for me as I have yet to find a Linux Distro that works out the box with my G4 PPC.

[http://www.yellowdoglinux.com/](http://www.yellowdoglinux.com/) may be more suited to what you are wanting to do.


> **sastusbulbas said:**
> 
Edit, why do we have no statement on the apple users thread stating Ubuntu (or any other Linux) will NOT give a fully functioning computer? 

HUH? I have two very old imacs that I use for various tasks, and having them running on my network as dedicated servers. They've both got PPC Versions of Ubuntu running on them and they work just fine, and are fully functional for what I use them for. And they're very stable too.



> **sastusbulbas said:**
> 
If it's not flash or video content on internet its graphic resolution, or colour, or not recognising CD or DVD or hardware issues such as inoperatable dvd drives etc etc.

Those are things which could be a problem on ANY operating system on ANY computer.

As for things more specific such as Flash. That's not really an Ubuntu issue. That's a VENDOR issue. If Adobe doesn't release a PPC version of the flash plugin, then you need to talk to Adobe. You can't blame Ubuntu or Linux in general for that. There are however people working to develop open source solutions for things like flash, which are making really good progressions in their development. 

> **sastusbulbas said:**
> 
 Evety year I come back to Linux to see if anything has changed and every year the same problems, if I was to put cost to the time I have wasted with Ubuntu on the PPC I could have bought a retail OS that works for less with less hassle and working out the box. 

Problems? What problems? Things like flash aren't an Ubuntu issue, thats an Adobe issue. As for anything else, you've not really posted any specific problems.

> **sastusbulbas said:**
> 
The guys making these OS's up need to decide if they are going to allow people to waste time money and resources on a not fully functional OS, or a sticky to highlight pitfalls arise when using with certain hardware so at least people can get a better idea of what to expect instead of wasting hours on something that cannot display Youtube vids or operate a CD/DVD drawer, or only has a resolution of 800+600.

Ok. Now you're just ranting and not providing any useful information.

The fact is that Ubuntu, out of the box, with a clean installation is very stable and works for most peoples needs. Things like Flash and other third party applications and browser plugins are beyond the scope and responsibility of Ubuntu and it's developers. Yes it is available in the repositories, but that doesn't mean that the Ubuntu developers are the ones responsible for its development.

No one is forcing you to use Linux. Linux is about freedom of choice, and if it isn't a good choice for you, you are free to run something else.

- zipperback
:popcorn:

---

### Post by sastusbulbas on 2010-05-01
> **roym4 said:**
> Since you're convinced that Ubuntu is not an acceptable option for you, and you've found better options, why are you still complaining about it here on Ubuntu forums?

Because I am replying to guys like you :)

---

### Post by sastusbulbas on 2010-05-01
> **zipperback said:**
> [http://www.yellowdoglinux.com/](http://www.yellowdoglinux.com/) may be more suited to what you are wanting to do.




HUH? I have two very old imacs that I use for various tasks, and having them running on my network as dedicated servers. They've both got PPC Versions of Ubuntu running on them and they work just fine, and are fully functional for what I use them for. And they're very stable too.





Those are things which could be a problem on ANY operating system on ANY computer.

As for things more specific such as Flash. That's not really an Ubuntu issue. That's a VENDOR issue. If Adobe doesn't release a PPC version of the flash plugin, then you need to talk to Adobe. You can't blame Ubuntu or Linux in general for that. There are however people working to develop open source solutions for things like flash, which are making really good progressions in their development. 



Problems? What problems? Things like flash aren't an Ubuntu issue, thats an Adobe issue. As for anything else, you've not really posted any specific problems.



Ok. Now you're just ranting and not providing any useful information.

The fact is that Ubuntu, out of the box, with a clean installation is very stable and works for most peoples needs. Things like Flash and other third party applications and browser plugins are beyond the scope and responsibility of Ubuntu and it's developers. Yes it is available in the repositories, but that doesn't mean that the Ubuntu developers are the ones responsible for its development.

No one is forcing you to use Linux. Linux is about freedom of choice, and if it isn't a good choice for you, you are free to run something else.

- zipperback
:popcorn:

What a load of tosh Zipperback! :)

Like I stated out the box on my PC it's fine, but with regards to my G4 no solutions for DVD/CD replay came forth when I asked, no quick easy reply to graphics issues, no answer to my non operating DVD drawer.

Loads of community fixes for general problems but it is far from straight out the box in my opinion.

Quite simply my G4 graphics and dvd drive were fine with Apple and Windows software, the flash issue I can live with, as it's clear Ubuntu can't work around it. But clearly as a newbie looking for a OS that functions in a similar manner to Windows or OSX the majority of newbies would benefit from some statement with regards to known issues.

If I was aware Ubuntu did not offer full internet functionality I may not have wasted time installing it. 
It did not support Apple G4 AGP graphics back when 8.04 was released, I did expect that simple point to be a non issue after it being out so long, but for me fresh out the box to get round the resolution and colour issue I ended up installing a non stock ATI Radeon 9200 Mac PCI card that was supported.

As for asking a newbie to post specific problems and providing useful information? Personally I think that says a lot about the attitude and support newbies may get.

Fact, 
As a newbie I see the lack of any stickies showing work around for known PPC issues a problem and my mentioning it is providing useful information for anyone interested in helping those newbies that don't quite fit into the "gang". Instead of getting asked if they have used the "search" function. 

The lack of any disclaimer on the PPC download info page is also an issue, as I believe many non techie newbies (yes we are not all Linux literate!) should be made aware that Ubuntu does not offer a work around or support video content on the web, and that any other issues could be mentioned.

I loaded PPC Ubuntu 9.10,
I got colour issues.
I got fixed 800+600 resolution.
I got a DVD drawer that would not open and close properly.
I got no CD playback or recognition.
I got no DVD playback or recognition.
I got no function/luck with formatting a second hard drive.
I found out Ubuntu had no Internet video viewing.

Hardly an out of the box functional OS for someone looking for a cheap media playing internet machine.

I am only asking for more info and support to be better organized. I would like to run Linux on my Mac, if there was a sticky giving clear concise instruction aimed at newbies experiencing known issues it may save people searching through posts with no answers.

The forum is telling people where to download for PPC, support that with a disclaimer and people such as I may not waste time or "rant" as you claim.

So do you have any solutions to my problem or are you wasting time by ranting dribble such as this Quote; *No one is forcing you to use Linux. Linux is about freedom of choice, and if it isn't a good choice for you, you are free to run something else. *

I again will state, I chose freely to download Ubuntu 9.10 as it stated suitable for PPC with community support, with no mention of known issues or non function.
It DID NOT work as I expected, and the community support I saw to be lacking. In as such it turned out I was free to waste my time.
So I chose to buy an OS and that OS worked out the box with far more usability and function and none of the issues than Ubuntu gave me. 

I now have Tiger 10.4.11 and Windows XP running on my old G4 PPC.

I would like to have the likes of Ubuntu or Mint running on my PPC, but do wonder if there will ever be a well documented site addressing issues with newbies in mind.

---

### Post by JoeMac42 on 2010-05-07
I'm perhaps somewhere between noob and novice.  Installing Ubuntu on my powerpc machine wasn't my first linux install, or even the trickiest, and no, it didn't just work right out of the box.  I started with Jaunty on my Dual-G4 FW800 PowerMac.  I was able to get most things working by searching the forums.  The toughest bit was getting the nonstandard GeForce 6600 AGP card recognized and working in X, which required generating and editing xorg.conf .  I never got the SMP-specific kernel working correctly in jaunty - it would cause a hang on shutdown.  I tried Karmic but I failed to get the video working and reverted to jaunty.   Not a flawless experience, but I learned quite a bit about some of the inner workings of Linux and X, so I don't see it as time wasted.

I just did a clean install of Lucid and I can't get over the difference compared with earlier versions that I tried,  This is the first time that I was able to get the live-cd/standard install to work.  It identified all of my hardware and the install went without a hitch.  All I needed to do was tweek yaboot.conf to have OS X as the default boot (that really should be an option during install) and add the SMP kernel variant with synaptic (and this time it also works without a hitch).

With the difficulties I was having, I was considering switching to Debian stable, but Lucid solved most or maybe all of the issues (though I'm still testing things).  With the new Nouveau driver, even glxgears works.  Obviously this may not go as well for other hardware combinations.  Also,I tried this out first via version upgrades without much success (I couldn't get the keyboard working in X).  But trying every out via the liveCD, checking to see that everything worked and proceeding to a clean Lucid install really worked this time for me right out of the box.  

Are we 2nd class citizens with Ubuntu on PowerPC? Certainly, but I think that's to be expected since our installed base is so small and some of us are working on 8-year old hardware.  Even Apple is abandoning us.  I'm just happy I can load up a modern OS and do productive work.  As long as Debian continues its support of the PowerPC architecture, I think we will continue getting new Ubuntu versions even though we are "only community supported". Now if someone could just code a decent flash player...






> **sastusbulbas said:**
> What a load of tosh Zipperback! :)

Like I stated out the box on my PC it's fine, but with regards to my G4 no solutions for DVD/CD replay came forth when I asked, no quick easy reply to graphics issues, no answer to my non operating DVD drawer.

Loads of community fixes for general problems but it is far from straight out the box in my opinion.

Quite simply my G4 graphics and dvd drive were fine with Apple and Windows software, the flash issue I can live with, as it's clear Ubuntu can't work around it. But clearly as a newbie looking for a OS that functions in a similar manner to Windows or OSX the majority of newbies would benefit from some statement with regards to known issues.

If I was aware Ubuntu did not offer full internet functionality I may not have wasted time installing it. 
It did not support Apple G4 AGP graphics back when 8.04 was released, I did expect that simple point to be a non issue after it being out so long, but for me fresh out the box to get round the resolution and colour issue I ended up installing a non stock ATI Radeon 9200 Mac PCI card that was supported.

As for asking a newbie to post specific problems and providing useful information? Personally I think that says a lot about the attitude and support newbies may get.

Fact, 
As a newbie I see the lack of any stickies showing work around for known PPC issues a problem and my mentioning it is providing useful information for anyone interested in helping those newbies that don't quite fit into the "gang". Instead of getting asked if they have used the "search" function. 

The lack of any disclaimer on the PPC download info page is also an issue, as I believe many non techie newbies (yes we are not all Linux literate!) should be made aware that Ubuntu does not offer a work around or support video content on the web, and that any other issues could be mentioned.

I loaded PPC Ubuntu 9.10,
I got colour issues.
I got fixed 800+600 resolution.
I got a DVD drawer that would not open and close properly.
I got no CD playback or recognition.
I got no DVD playback or recognition.
I got no function/luck with formatting a second hard drive.
I found out Ubuntu had no Internet video viewing.

Hardly an out of the box functional OS for someone looking for a cheap media playing internet machine.

I am only asking for more info and support to be better organized. I would like to run Linux on my Mac, if there was a sticky giving clear concise instruction aimed at newbies experiencing known issues it may save people searching through posts with no answers.

The forum is telling people where to download for PPC, support that with a disclaimer and people such as I may not waste time or "rant" as you claim.

So do you have any solutions to my problem or are you wasting time by ranting dribble such as this Quote; *No one is forcing you to use Linux. Linux is about freedom of choice, and if it isn't a good choice for you, you are free to run something else. *

I again will state, I chose freely to download Ubuntu 9.10 as it stated suitable for PPC with community support, with no mention of known issues or non function.
It DID NOT work as I expected, and the community support I saw to be lacking. In as such it turned out I was free to waste my time.
So I chose to buy an OS and that OS worked out the box with far more usability and function and none of the issues than Ubuntu gave me. 

I now have Tiger 10.4.11 and Windows XP running on my old G4 PPC.

I would like to have the likes of Ubuntu or Mint running on my PPC, but do wonder if there will ever be a well documented site addressing issues with newbies in mind.

---

### Post by Yeti can't ski on 2010-05-12
> **sastusbulbas said:**
> What a load of tosh Zipperback! :)

I am only asking for more info and support to be better organized. I would like to run Linux on my Mac, if there was a sticky giving clear concise instruction aimed at newbies experiencing known issues it may save people searching through posts with no answers.

The forum is telling people where to download for PPC, support that with a disclaimer and people such as I may not waste time or "rant" as you claim.


Dear sastusbulbas, 

Sorry for jumping into an ongoing discussion and for being perhaps too philosophical and off-topic. I completely understand your frustration (believe me, I have been there), but I believe that:  

1 – You are focusing too much on “free” as in “free beer” and not as in “free speech”. 

This is not (only) about thinking on a “money+time vs. value” basis. There would be no FOSS (Free and Open Source Software) movement if everyone thought like that. This is about having control over the programs that your computer is running and sharing the benefits with others. I don’t care what is the cost of Window$ XP or Mac/OS. There are dozens of things that I cannot do with such systems, starting with (i) not becoming a locked-in client and (ii) knowing (or being able to know) what instructions the system is giving to my computer.  

2 – In FOSS, you are not a client, you may simply elect to be a community member. 

Here, you are in a completely different position. For good and for bad you are not a customer (unless you buy professional support from Canonical, which in any case would probably not be given for legacy PPC systems). You cannot, therefore, “demand” a disclaimer or a step-by-step guide. Volunteers are investing  their free time assisting others. Here, no one has a “claim” to proper, fast and complete assistance. In any event, in my personal experience, community support is incredibly superior to any bloody call-center of any proprietary software vendor. 

Just my two cents. Cheers. 

P.S. – This thread, including your comments, was very useful for my decision to try Xubuntu 10.4 on my girlfriend’s old G4. Now I know what problems to expect. This is a concrete example of building knowledge on a community basis. You won’t find a complete and well organized handbook, but the information is there and finding it is a part of the learning process.

---

### Post by klhrevolutionist on 2010-05-15
Thanks to powerpc developer's for taking the time to do this! If I can help out in some way let me know.

Thanks ubuntu-ppc team!

---

### Post by gare on 2010-05-17
and just to repost:

[B][PowerPC wiki]("https://wiki.ubuntu.com/PowerPCKnownIssues")
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)


[Releases including PowerPc ; torrents at bottom of page ]("http://cdimage.ubuntu.com/ports/releases/10.04/release/")
[http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)
[/B]
Ubuntu 10.04 LTS (Lucid Lynx)

This directory contains only less-used images which are not mirrored widely. For the most frequently downloaded CD images, see releases.ubuntu.com. Please use a mirror if possible.

---

### Post by Trooper1420 on 2010-05-19
Hello, I am completely new to Ubuntu and Linux, but have several years working with Mac OS and Windows.
 
I recently acquired a couple G4 "Mirror Door" Macs, and I'd like to use them to start learning about Ubuntu since they won't run the most current Mac OS. (it runs 10.5.8 quite nicely, though)
 
I've downloaded Lucid Lynx and Karmic, made sure they were PPC versions, and they don't do anything on the Mac. I can't get the disk images to burn to CD with Disk Utility, neither will they show up in bootable volumes in the startup disk menu.
 
So, I downloaded 10.4 Lucid Lynx for Power PC on my Windows machine and burned a disk. The Mac will not boot from the CD no matter what I try. 
 
Naturally, I hit up google for some answers, but the results mostly consist of "download version x and boot from cd, click install", indecipherable gibberish that is way above my level (and doesn't seem applicable in any case), or threads that start with posts such as this one that quickly devolve into trollery. 
 
I am encouraged to see a lot of positive and helpful information in these forums, and hope to find some help; Is there anyone here who can tell me what I'm not doing or doing wrong in this process? What do I need to do to make a bootable CD? Is there something to adjust on my Mac? Does it matter what application I use to burn a CD, or what settings it has? 
 
Any help or information will be appreciated. Thanks!

---

### Post by linuxopjemac on 2010-05-20
Try booting with the "c" key pressed after the boing sound.

---

### Post by Trooper1420 on 2010-05-20
Thanks, but I have tried booting with 'C' and also with 'Option' to select a boot drive. So far, none of the three Ubuntu boot CDs I've tried are recognized by the Mac.

---

### Post by linuxopjemac on 2010-05-20
try booting from open firmware:
boot cd:,\\:tbxi

To get into open firmware, boot with the following key combination:
option+command+o+f

---

### Post by Trooper1420 on 2010-05-20
Thanks, I had tried some other open firmware boot commands, but not that one.
 
However, I'm sorry to say it didn't work... it came back with the message: 
"LOAD-SIZE is too small"
 
From comments and advice elsewhere, it sounds like Mac Disk Utility and the Windows applictions I've used are doing something to the Ubuntu installation CD that prevent it from being recognized as a bootable volume. 
 
For my next attempt, I will try burning the Ubuntu installer from Toast and see if that CD will boot.
 
Thanks again for the advice! I'll post with the toast results soon.

---

### Post by linuxopjemac on 2010-05-21
never mount the iso, just burn "as image" from Dik utility should work

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Rabendoktor on 2010-05-29
Hi, there,

I've got the same probs as well on my G4 MDD as on my iMac G4 (iLamp). 

On the MDD, no matter what version of installation-CD I put in, it somehow starts from them, but only to show me a bluescreen with nice vertical stripes on it. 

On the iLamp, I get past the initial boot-screen, but afterwards (no matter what boot-option I choose) only a magentascreen will remain forever.

I downloades the ISOs from cdimage, tried the alternate-version as well, know how to burn an ISO with diskutility, but nevertheless - no chance with those Macs (on my Lombard, it works very slowly, but it works)...

Any ideas how 2 fix this issue?

Thanks - and have a nice weekend....

---

### Post by zoomy942 on 2010-05-29
> **sastusbulbas said:**
> Can get new or used Windows 7 (32bit or 64bit) or XP Pro (32bit or 64bit) or Apple Tiger or Leopard and such from eBay every so often for around £30 to £80, I bought OSX 10.4 Tiger family pack (5 users) for £60. 

Some time back I bought XP Pro for £30 odd retail new and unused (from an eBay store with plenty of new copies) and Windows 7 Ultimate I bought for £80 new unused unopened, I have seen Windows 7 from £60 retail and Snow Leopard from £32 retail all new unused from eBay stores. For old G3's and such Panther is usually availale somewhere for around £30, Tiger for around £60

My upstairs PC is W7 64bit (I may change the upstairs PC to Ubuntu or Mint seeing as PPC is not Mac compatible) my downstairs PC is W7 64bit, my Mac will now be Tiger 10.4

Edit; Received my Tiger OSX 10.4 yesterday, installed it and updated to 10.4.11 with all updates up to date, and also installed a Genuine copy of Windows XP as a virtual PC within my Mac OS. The Mac is working well with XP a little slow as it's running as virtual. None of the issues I experienced with Ubuntu raised their heads.

Take your hourly rate of pay, multiply your hours spent finding out Ubuntu does not work and that gives you a rough idea of Ubuntu's cost. Time is not free.

how did you vitualize windows?  an intel mac?

---

### Post by Rabendoktor on 2010-05-30
Hi, there,

at least for my G4 MDD (PowerMac3,6, with Radeon 9000 Pro) a  firmware-update fixed my probs - although I had 4.4.8f2 installed,  running the update  ([http://docs.info.apple.com/article.html?artnum=120171](http://docs.info.apple.com/article.html?artnum=120171)) enabled me to  install Ubuntu 10.0.4 from the alternate-cd without any probs.

Have a wonderful sunday...

---

### Post by Trooper1420 on 2010-06-08
Here is an update on my efforts to burn a bootable Lucid Lynx CD for my Mac PowerPC g4 

Here's what I *was* trying:

(1)Burn  .iso from PC- did not work.

(2)Open the downloaded .iso file and  then burn the contents to a CD using Toast- also did not work. 

(3)Drag  the downloaded .iso file to the left column of Disk Utility. Hit the  burn button & insert a blank disc.

The first time I tried  method 3, the disc would not boot. I could open the CD and see the .iso  file, but it wouldn't do anything but show me a bunch of folders that  weren't much good to me. This is the point at which I nearly gave up.

I can't recall ever before trying to burn a  bootable Mac CD before, so my inexperience led me to believe that I was  doing something wrong (and my first few tries, I was). But I had  explicit directions (including the set Tacit linked to), and am "purdy  good at readin werds", so I was perplexed and frustrated about my  inability to burn a bootable disc.

Later in the week, I noticed  that another disc I burned with the Mac had some corrupt data, so I got  to thinking it was the superdrive after all. I replaced the superdrive  and burned another Ubuntu .iso CD using method #3. This CD was bootable,  and I used it to install the Ubuntu.

So: apparently a  superdrive can work well enough to read everything on a CD, and write  well enough to get *most* of the  data across, but not write well enough to make a CD bootable.

More about the installed Ubuntu in the next post.

---

### Post by Trooper1420 on 2010-06-08
Power PC Mac g4 Mirror Door Ubuntu Lucid Lynx 10.04

---

### Post by John Sawyer on 2010-06-14
> **Rabendoktor said:**
> at least for my G4 MDD (PowerMac3,6, with Radeon 9000 Pro) a  firmware-update fixed my probs - although I had 4.4.8f2 installed,  running the update  ([http://docs.info.apple.com/article.html?artnum=120171](http://docs.info.apple.com/article.html?artnum=120171)) enabled me to  install Ubuntu 10.0.4 from the alternate-cd without any probs.

I'm interested in your comment about G4 MDD firmware update 4.4.8f2, as I also have a G4 MDD.  You say your MDD already had firmware 4.4.8f2, but then you ran a firmware updater you downloaded from the Apple web page you cite, and this allowed you to install Ubuntu.  But the firmware updater available on that page is also 4.4.8f2.  I downloaded it, and ran it, and it wouldn't install on my MDD--instead, it reported that my MDD already had 4.4.8f2 installed (which I already knew, but I doublechecked by using System Profiler before running the updater you cite).  Apple's firmware updaters won't install the same version of firmware as is currently installed, so are you sure your MDD already had 4.4.8f2 installed?  Did you doublecheck before running the firmware updater you cite?

Another wrinkle: I used to fix Macs (from 1985 to about 2007), and so I've updated the firmware on all updatable models made until then, and I've kept the updaters. I looked at my collection of firmware updaters for the MDD, and found that the only one I had, was one whose readme file is dated Nov 25 2002; this version comes in the form of a standalone updater app.  The version on the Apple web page you cite, has a readme dated Dec 9 2002, and comes in Apple's later format--a generic updater app, plus a script to load into it.  Since I had only the standalone app version in my collection, this implies to me that this is the version I ran in 2002 to update my MDD's firmware to 4.4.8f2.  Since the version on the web page you cite, wouldn't reinstall on top of that version, and reported my Mac already had 4.4.8f2 installed, this indicates that both updaters install version 4.4.8f2, and implies that the only difference between the two is the different formats of the updaters.

But if your MDD already had 4.4.8f2 installed, and the Dec 9 2002 version of the 4.4.8f2 updater was still able to install on your MDD, allowing you to install Ubuntu, more power to you.  Maybe something was corrupted in your MDD's 4.4.8f2 firmware (which might have also been the cause for your earlier trouble with installing Ubuntu), and the Dec 9 2002 updater was able to detect that, and that may be why it was still able to install even though the firmware version was the same.

---

### Post by Rabendoktor on 2010-06-15
... it remains a miracle for me, too and was an act of pure despair.

Systemprofiler showed me clearly the firmware-version and nevertheless the update worked and fixed the prob - don't ask me why.....

Now Lynx works, but remains with a lot of restrictions as there is no flash-player available to work with Youtube etc., what is, as the machine is for my eldest son, a major prob...

All the best 4 Your MDD!

---

### Post by plainsdigital on 2010-06-15
This was very helpful. Thanks!

---

### Post by sol-invictus on 2010-06-21
Actually all supported ubuntu-versions are available through archive.ubuntu.org - and the community supported versions are available on ports.ubuntu.org - but for example where do i get updates for a Ubuntu PPC 8.10 ? this version got deleted from ports.ubuntu.org but is also not available on archive.ubuntu.org - is there any archive for the ports?

---

### Post by zeroti on 2010-06-22
> **Rabendoktor said:**
> ... it remains a miracle for me, too and was an act of pure despair.

Systemprofiler showed me clearly the firmware-version and nevertheless the update worked and fixed the prob - don't ask me why.....

Now Lynx works, but remains with a lot of restrictions as there is no flash-player available to work with Youtube etc., what is, as the machine is for my eldest son, a major prob...

All the best 4 Your MDD!

you can try installing youtube-dl . cut off any extra stuff from a youtube url and then download the video from the terminal like this:

youtube-dl [http://www.youtube.com/watch?v=q9Xaz7ECI4M](http://www.youtube.com/watch?v=q9Xaz7ECI4M)

---

### Post by PSimpso on 2010-06-22
Not sure if the this is the correct thread for this.

I have an iMac G3 (slot-loading, 400Mhz); I've successfully installed Ubuntu and Xubuntu 10.04. However, it's stuck in low-graphics mode.

And, ever since I did the **cmd + option + p + r** command the display shrunk a bit leaving some black space around the display.

Any ideas?

---

### Post by linuxopjemac on 2010-06-22
make a new thread and I will help you.

---

### Post by PSimpso on 2010-06-22
done:
[http://ubuntuforums.org/showthread.php?t=1515662](http://ubuntuforums.org/showthread.php?t=1515662)

---

### Post by NickHansonNet on 2010-08-13
Thanks, I needed Ubuntu on my Old eMac G4 Power PC. The Mac OSX Tiger 10.4.11 is just so slow for this mac. I will try it.

---

### Post by carlmccall on 2010-08-20
[QUOTE=carlmccall;3935482]chris4a: thank you for the Fedora 8 link.  your return karma is [http://softwaresanta.com](http://softwaresanta.com)

Try this:   [http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)

You all still want Older Versions of Ubuntu for those Beloved G3 laptops? I know where they hide them ....

OK: here is the main directory with the last few PPC Ubuntu releases: 
[http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/) (Paydirt!)
"These directories contains only less-used images which are not mirrored widely."
Mac G3, G4, or G5 processors  including iBooks and PowerBooks as well as IBM OpenPower machines. 256 MB of RAM recommended

Also available for 
[Mac (PowerPC) and IBM-PPC (POWER5) server install CD]("http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-server-powerpc.iso")
For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines.

[HP PA-RISC server install CD]("http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-server-hppa.iso")
For HP PA-RISC computers.

[IA-64 server install CD]("http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-server-ia64.iso")
For Intel Itanium and Itanium 2 computers.

[SPARC server install CD]("http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-server-sparc.iso")

in Desktop / Server / and Alternate    Install CD .iso images (An .iso image smorgasbord awaits you down at the bottom of each page.)

the latest release even comes in a PlayStation3 Version! (Get it at "Lucid Lynx"'s page)  Snag it!
_________________________________________________


For Instance:

If you wanted Ubuntu 8.04.1 LTS (Hardy Heron) click here:
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/) 
Mac G3, G4, or G5 processors 384 MB of RAM recommended

_________________________________________________

For Ubuntu 9.04 (Jaunty Jackalope) 
[http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)
"This directory contains only less-used images which are not mirrored widely."
Mac G3, G4, or G5 processors including iBooks and PowerBooks as well as IBM OpenPower machines. 256 MB of RAM recommended
  
_________________________________________________

For Ubuntu 9.10 (Karmic Koala)
[http://cdimage.ubuntu.com/ports/releases/karmic/release/](http://cdimage.ubuntu.com/ports/releases/karmic/release/) 
"This directory contains only less-used images which are not mirrored widely."
Mac G3, G4, or G5 processors  including iBooks and PowerBooks as well as IBM OpenPower machines. 256 MB of RAM recommended.

_________________________________________________

For Ubuntu 10.04 LTS (Lucid Lynx)
This directory contains only less-used images which are not mirrored widely.
[http://cdimage.ubuntu.com/ports/releases/lucid/release/](http://cdimage.ubuntu.com/ports/releases/lucid/release/)

Desktop CD

The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use. You will need at least 256MB of RAM to install from this CD.

There are three images available, each for a different type of computer:

Mac (PowerPC) and IBM-PPC (POWER5) desktop CD
    For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines.

IA-64 desktop CD
    For Intel Itanium and Itanium 2 computers.

PlayStation 3 desktop CD
    For Sony PlayStation 3 systems. (This defaults to installing Ubuntu permanently, since there is usually not enough memory to try out the full desktop system and run the installer at the same time. An alternative boot option to try Ubuntu without changing your computer is available.)

[http://cdimage.ubuntu.com/ports/releases/lucid/release/](http://cdimage.ubuntu.com/ports/releases/lucid/release/)

I hope that helps! :D  ;)  ):P  :KS

---

### Post by carlmccall on 2010-08-20
> **John Sawyer said:**
> I'm interested in your comment about G4 MDD firmware update 4.4.8f2, as I also have a G4 MDD.  You say your MDD already had firmware 4.4.8f2, but then you ran a firmware updater you downloaded from the Apple web page you cite, and this allowed you to install Ubuntu.  But the firmware updater available on that page is also 4.4.8f2.  I downloaded it, and ran it, and it wouldn't install on my MDD--instead, it reported that my MDD already had 4.4.8f2 installed (which I already knew, but I doublechecked by using System Profiler before running the updater you cite).  Apple's firmware updaters won't install the same version of firmware as is currently installed, so are you sure your MDD already had 4.4.8f2 installed?  Did you doublecheck before running the firmware updater you cite?

Another wrinkle: I used to fix Macs (from 1985 to about 2007), and so I've updated the firmware on all updatable models made until then, and I've kept the updaters. I looked at my collection of firmware updaters for the MDD, and found that the only one I had, was one whose readme file is dated Nov 25 2002; this version comes in the form of a standalone updater app.  The version on the Apple web page you cite, has a readme dated Dec 9 2002, and comes in Apple's later format--a generic updater app, plus a script to load into it.  Since I had only the standalone app version in my collection, this implies to me that this is the version I ran in 2002 to update my MDD's firmware to 4.4.8f2.  Since the version on the web page you cite, wouldn't reinstall on top of that version, and reported my Mac already had 4.4.8f2 installed, this indicates that both updaters install version 4.4.8f2, and implies that the only difference between the two is the different formats of the updaters.

But if your MDD already had 4.4.8f2 installed, and the Dec 9 2002 version of the 4.4.8f2 updater was still able to install on your MDD, allowing you to install Ubuntu, more power to you.  Maybe something was corrupted in your MDD's 4.4.8f2 firmware (which might have also been the cause for your earlier trouble with installing Ubuntu), and the Dec 9 2002 updater was able to detect that, and that may be why it was still able to install even though the firmware version was the same. :KS  If I remember correctly, the free application "MacTracker"  [http://mactracker.dreamhosters.com/](http://mactracker.dreamhosters.com/)   has the latest version of Firmware Updater listed on each machine's page -
along with a link to the latest firmware on Apple's web site.
):P  :KS

---

### Post by trj021782 on 2010-09-28
Hi, I am somewhat new to Ubuntu but I have it installed on my PS3 (I am running 9.10) I am having a hard time finding software for PPC64 Ubuntu 9.10 does anyone know any good sources? 

I am specifically looking for emulators

Also it would be good if the files .deb because i have yet to successfully install anything from tarballs with the exception of Opera which came with an install script.

***EDIT***

also is there a way to get rid of the stupid coffee beans and tag below my name on this forum. . . . or at least change it to something else?

---

### Post by hlpguru on 2010-10-13
> **jcompton said:**
> Can somebody expand the explanation of how to do a proper 7.04 full Xubuntu install? Right now it simply says  "It would be possible to install with this and then upgrade to the final release." which is a little vague for newcomers.

Does anybody know *why* there's no Xubuntu PPC final? Arguably it's the most useful of all the Ubuntus for PPC users, since it tends to cater to machines of a spec lower than that you'd want to comfortably run OSX on.




Hello there! 

I've found a website [http://www.thinkwiki.org/wiki/Installing_Xubuntu_7.04_on_a_ThinkPad_X60s](http://www.thinkwiki.org/wiki/Installing_Xubuntu_7.04_on_a_ThinkPad_X60s) maybe it will help.

---

### Post by bagstars on 2010-11-12
Do you slove this problem now ? I also need it...But i canot understand the words well

---

### Post by albasnians on 2010-12-15
There are so many ways If you have Internet connection then Its easy to go through the offical site of Ubuntu and download the latest version of powerpc....Its easy and helpful for you..

---

### Post by moore.bryan on 2011-01-09
I can't seem to find a way to burn the Natty daily iso to a usb and have my G4 Mac recognize it as bootable. Every time I get to the boot menu and select the Linux disk (my usb), it just goes back to the boot menu and lets me select it again. That round-robin seems indefinite. Any help would be greatly appreciated.

---

### Post by JANGUS on 2011-01-17
OK, i'm the noob'est noob here, and this is my first post.

I am running OSX Tiger (10.4.11) here on my trusty old G4 MDD with a "giga" 1.4gig  CPU accelerator and doing quite well with it actually.

I have discovered Gimp and Inkscape and love the open source concept.

I registered only a few days ago, and have been lurking around to see if I can get a look at Ubuntu in action.

Would it be possible to install some version of Ubuntu on a partition of one of my internal hard drives and be able to boot it, using the option key at power-up time?
I guess this would be called a "dual-boot" situation.
If so, can someone provide a link as to what to download.

At first, it seemed as though this would not be possible, and that only a burned CD/DVD with Ubuntu on it will work, but after reading many other posts it seems that this may, in fact, be possible.

Yes, I am a bit confused about this and if someone could give me some clarification along with a little -why- info, it would be greatly appreciated.
Thanks

---

### Post by bilallucky on 2011-01-25
I knew there had to be something out there as I had the old version 5.10 for PPC, but I wanted to see the newest stuff on the MAC.

---

### Post by EnGorDiaz on 2011-03-02
> **moore.bryan said:**
> I can't seem to find a way to burn the Natty daily iso to a usb and have my G4 Mac recognize it as bootable. Every time I get to the boot menu and select the Linux disk (my usb), it just goes back to the boot menu and lets me select it again. That round-robin seems indefinite. Any help would be greatly appreciated.

that because openfirmware doesnt support usb boot you need a firewire drive

---

### Post by linuxopjemac on 2011-03-02
you CAN boot from usb stick, see installation instructions MintPPC.

---

### Post by xXkanfirXx on 2011-04-01
Hey everyone, 

So I just received a iMac G4 from someone for free. It's currently running Mac OS X panther, with the 700mhz PPC processor and 512MB of RAM. It's extremely sluggish and outdated. I'm trying to get it going for my mother and she's pretty computer illiterate so she just needs something simple for web browsing and checking emails. I don't really feel like messing with it and I don't have any discs, so I thought about just putting Ubuntu or Xubuntu on it. I heard Xubuntu is better for computers with lower specs? Which would you recommend, and how do I got about installing it on the Mac? I'm Mac illiterate. 

Thanks!

---

### Post by mondo2k on 2011-04-22
> **xXkanfirXx said:**
> Hey everyone, 

So I just received a iMac G4 from someone for free. It's currently  running Mac OS X panther, with the 700mhz PPC processor and 512MB of  RAM. It's extremely sluggish and outdated. I'm trying to get it going  for my mother and she's pretty computer illiterate so she just needs  something simple for web browsing and checking emails. I don't really  feel like messing with it and I don't have any discs, so I thought about  just putting Ubuntu or Xubuntu on it. I heard Xubuntu is better for  computers with lower specs? Which would you recommend, and how do I got  about installing it on the Mac? I'm Mac illiterate. 

Thanks!

I recently inherited a G3 iMac 350 (Indigo) and I'm chasing my tail  trying to get the right OS with a current browser on it... even OS 9.2.2  was running sluggish on it. Hopefully my trial-and-error research will  help you.

- with a G4 you should at least have a DVD drive in it,  which is good because I only have a CD drive in the iMac and many of  the current distros are sized larger than 700MB.

- I've been  successful at installing Ubuntu 10.10 (which ran horribly on the iMac  even after using the Xcfe desktop - too much bloat for the processor)  and Xubuntu 6.10 (which is running like a champ, but I can't easily  upgrade or get a current-gen browser for it), so now I'm downloading  Ubuntu 8.0.4 server and will install the Xcfe desktop directly from the  main install to avoid Gnome and KDE. Then I'll update Xubuntu online as  much as possible.

- I'm using a program called TransMac v9.1 to  easily burn the ISO images into bootable CDs on my Windows XP machine. I  guess having a Mac that could burn stuff would be better, but this  works.

- all the releases are at [http://cdimage.ubuntu.com]("http://cdimage.ubuntu.com/ports/releases/9.10/release/")  , with all the older Xubuntu versions found under the 'ports' category  and not under 'xubuntu', but if you're burning DVDs, you won't need the  older releases. Make sure the ISO you choose to download has -powerpc-  in it's label.

- i had (and may have again installing v8.0.4)  issues with the monitor settings on my iMac during and after the  install, hopefully, with you working on a G4, this won't happen.

-  i upped the iMac's RAM from 64MB to 512MB. With that and Xubuntu, it's  almost like running a current-gen PC. I say almost because of the pokey  USB 1.1 speed and lack of multimedia options and the fact that I need to  use an ethernet cable means I can't -really- turn it into a 40-lb portable  computer. :p

- buy your mom a real two button mouse with a scrollwheel. She'll need it.

-  OpenOffice (now called LibreOffice by the non-powerpc folk) and AbiWord  + Gnumeric are great MS Office substitutes, but the slightly less  friendly OpenOffice is more MS Office compatable.

- the simplest  partitioning system you can have on a ppc-Mac with Ubuntu/Xubuntu is [1]  a very small Apple partition so the Mac can boot, [2] a small NewWorld  /boot partition, [3] the main data partition, which mine is of the /ext3  file type, and [4], the /swap file partition. I can't use LVS on my  iMac (it won't boot when I do) and encryption is pretty much pointless  since I need every bit of speed I can get. You may be able to get away  with one or both though.  

- every install has taken me an hour. A 350MHz processor + 100MHz bottleneck = zzzzzzzzzzzzz...


Good luck!

---

### Post by mondo2k on 2011-04-23
To make things clearer, I'm going to list the partitions I made on my 7.5gb (8.0gb) iMac Indigo hard drive as I'm reinstalling xubuntu for ubuntu 8.04.1. 

Using a install CD made from ubuntu-8.04.1-server-powerpc.iso file, when I got to the partitioning options, I selected the Guided option which automatically set everything up but I still tweaked the settings. I didn't select LVM or encryption. EDIT: slightly upped the swap partition after I couldn't get a GUI running in Hardy; updated the numbers below. 

Partition -      Size   - Flags and Use -       Name       - Mount Point - *Comments
------------------------------------------------------------------------------
#1         -   32.3kb   -        none       -        Apple        -      none      - *don't play with this partition!

#2         -    1.0mb   -    B K boot     -     NewWorld    -      none       - *confirm this is the NewWorld type

#3         - 6.1gb    -      f ext3        - 6.1GBmain   -         /          - no comments

#4         - 1.0gb -      f swap       -        swap        -       swap      - no comments


The swap file is considerably less than the recommended 2xRAM size, but my hard drive is so small, if I need more RAM I'll upgrade it from 512mb to 1.0gb. EDIT: Planning on doing this later tonight.

Ubuntu server installed without problems. Now I'm downloading the xubuntu front end. Hopefully I won't have any video issues and I can start on-line upgrading to later versions of the OS.

10 HOURS LATER: 
Both Xubuntu and Xcfe run terribly slow on the **Ubuntu 10.04.2 Lucid server** that I finally decided upon, so I'm experimenting with window managers like Fluxbox and Openbox and I've seen a significant improvement. I'm going to test other browsers like Opera and I'll probably shove another 512mb of RAM in the Indigo after I'm done goofing around. Although I have little things to tweak here and there, I'm happy that Ubuntu can make a garbage computer functional again. :)

NEXT MORNING:
- Still deciding on whether to use IceWM or Blackbox as my x-windows manager; all three web browsers I tried - Firefox 3.6, Opera, and Epiphany - run fairly well on these frugal desktops although there's no flash. The manager that's easiest to configure is probably the one I'll choose.

- Having issues with sound - there isn't any after the initial "choom" of booting up.

- I have about 3.7gb of storage left. It's time to start cutting away some unneeded bloat. BleachBit is a lifesaver.

- Here's the entire xorg.conf script I typed in to get the gui operating. This script works on the iMac 350mhz Indigo as well as it's earlier version the 350mhz Blueberry:

##imac-ppc-slot-loader-350-xorg.conf#################

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 58-62
VertRefresh 75-117
#ModeLine "1024x768" 78.75 1024 1044 1140 1328 768 781 784 820 +hsync +vsync
#ModeLine "800x600" 62.40 800 821 901 1040 600 609 612 644 +hsync +vsync
#Modeline "640x480" 49.90 640 657 721 832 480 481 484 514 +hsync +vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
#Virtual 1024 768
EndSubSection
EndSection

Section "Module"
Disable "dri"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "intl"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "CCEusecTimeout" "100000"
#Option "UseFBDev" "true"
EndSection

---

### Post by mondo2k on 2011-04-24
I still have the sound glitch to troubleshoot but I've found a comfortable set-up for this little iMac.

Ubuntu PPC Server 10.04 + Xubuntu desktop (not used directly)
LXDE windows manager
Opera web browser
Abiword/Gnumeric for office stuff
other software: BleachBit, alien, Rhythmbox, deborphan, comix, KeePassX 

And then I went into the Synaptic Package Manager and removed all the things I couldn't use or didn't want (CUPS and printing packages, extra languages, PulseAudio, media burning software, bluetooth and wireless. Changing my windows manager from IceWM to LXDE doesn't slow anything down but that extra 512mb of RAM I installed is now getting used. LXDE is much more easily configurable than IceWM and I'm willing to accept the slightly higher specs to run it. I have 3.6 gigs of free space left on this tiny hard drive, and that's with a 1.0gb swap partition.

What am I going to use this iPC for? A low-power means for using the Internet, light word processing, and storage/use of some mp3's and cbr's.

I can't play legally-owned audio CDs, although I can stream radio and (download and) play mp3s. Kind of stupid.

---

### Post by MolsterS013 on 2011-05-10
Hey everybody!

I have recently installed Ubuntu 10.04 on my iBook G4 PowerPC. I used the desktop download link given on the PowerPC downloads page (linked in the first post). I am primarily using this computer as a server (I would have used the server download, but the wireless drivers were hard to work with, so I am running the GUI as a server). While the computer will be used mainly as a server, it will, at times, also be used for non-server reasons. The problem is that I can't seem to find a way to download Chromium, and I really don't like Firefox. When i try to download it through the Software Center, there is no "Install" button, and the only information given is this:

"To show information about this item, the software catalog needs updating."

I've tried doing

sudo apt-get update

but I still can't download it.

If anyone could give any help, it would be much appreciated Thanks!

---

### Post by airk on 2011-05-11
> **MolsterS013 said:**
> The problem is that I can't seem to find a way to download Chromium, and I really don't like Firefox.

The answer is quite simple. Some of the core components of Chromium havent been built for the PowerPC arch (namely the V8 Javascript engine). So it's not (easily) possible to build Chromium for PowerPC.

[Chrome on PowerPC]("http://groups.google.com/a/chromium.org/group/chromium-discuss/msg/44b00b52d014b7e4")

---

### Post by pauljwells on 2011-05-11
> **MolsterS013 said:**
> I really don't like Firefox.

Firefox 4 is a big improvement on earlier versions. I've moved back to FF from Chromium.

You need 11.04 on PPC to get FF4 though

---

### Post by nerdy_kid on 2011-05-26
anyone know where/if I can download natty powerpc?  I found an iso for oceiric, but none for natty, which I thought was strange.

---

### Post by pauljwells on 2011-05-28
You're right. I can't find one anywhere :-(
I installed pre-release from the daily build (which is where you're finding the Oneiric)
If you want a working system 10.10 is a lot less buggy than 11.04. I've not tried the pre-alpha oneiric yet but plan to as soon as I can. It could well be a better bet than natty already for a hacking system
Looks like the only way to get natty is to install minimum 10.10 and immediately dist-upgrade
Post this as a question on ubuntu answers [https://answers.launchpad.net/ubuntu]("https://answers.launchpad.net/ubuntu") and maybe you'll get an answer or start a bug...

---

### Post by nerdy_kid on 2011-05-30
> **pauljwells said:**
> You're right. I can't find one anywhere :-(
I installed pre-release from the daily build (which is where you're finding the Oneiric)
If you want a working system 10.10 is a lot less buggy than 11.04. I've not tried the pre-alpha oneiric yet but plan to as soon as I can. It could well be a better bet than natty already for a hacking system
Looks like the only way to get natty is to install minimum 10.10 and immediately dist-upgrade
Post this as a question on ubuntu answers [https://answers.launchpad.net/ubuntu]("https://answers.launchpad.net/ubuntu") and maybe you'll get an answer or start a bug...

yeah thanks, I think I'm going to install 10.10 then dist upgrade to natty.  As soon as my nice Ubuntu keyboard comes in :D  (at least, I hope its nice lol)

---

### Post by jhicks124 on 2011-05-30
Now I downloaded that, but it doesn't fit on a CD (744 mb)...is there a way too boot it from a flash drive? ...my old G4 doesn't have a DVD drive...

---

### Post by nerdy_kid on 2011-05-30
> **jhicks124 said:**
> Now I downloaded that, but it doesn't fit on a CD (744 mb)...is there a way too boot it from a flash drive? ...my old G4 doesn't have a DVD drive...

744MBs?  The one I downloaded was 710, which I'm assuming fits via overburn.  Try downloading the minimal CD

---

### Post by pauljwells on 2011-05-30
If you want to try unity-2d, install unity-2d-default-settings from synaptic, then install my debs from this post to fix the colours and the mouse edge detection.

[http://ubuntuforums.org/showpost.php?p=10822941&postcount=13]("http://ubuntuforums.org/showpost.php?p=10822941&postcount=13")

---

### Post by MacHackers on 2011-06-16
Where do we put these? In sources.list? By the way, I am using the PPC Version of 10.04.

---

### Post by MacHackers on 2011-06-16
> **jhicks124 said:**
> Now I downloaded that, but it doesn't fit on a CD (744 mb)...is there a way too boot it from a flash drive? ...my old G4 doesn't have a DVD drive...
Google your prefered flavor of Ubuntu PPC. I am using 10.04 LTS for PPC Platforms now, so I know they have PPC Editions of 10.04 and earlier. All you have to do is download it, and if you are using Mac OS X (on a PPC Mac), go to Disk Utility and drag the file to the white space in Disk Utility, (make sure it is NOT MOUNTED, and by it, I mean the .iso file.) Click it and click "Burn". Stick a CD in the drive, and wait until it gets done burning. Stick the CD IN THE DRIVE BEFORE SHUTDOWN. Shutdown the PPC Mac. (If I haven't mentioned yet, there is a Ubuntu site where there is problems that were found while using the PPC Edition such as distorted volume.) Hold down the "C" key. If everything went okay and worked out, it will boot a LIVE copy of Ubuntu without Installing in about 5 minutes or less. If you wish to boot Mac OS X again, just shutdown the computer, reboot it without holding the "C" key. (I am running Ubuntu 10.04 PPC Edition now, so it does fit on a DVD and CD.)

Hope this Helps!
Patrick.

---

### Post by MacHackers on 2011-06-16
Hey Guys! Thanks for all of the comments made. I have installed Ubuntu 10.04 on my eMac (1.0 GHz) and it runs and boots, successfully. I have steps on how to install Ubuntu on your G3,G4, or G5 mac. This works with the following systems: iBook (G4), iBook Clamshell, eMac G4 (all of them..), PowerBook G4 and G5, iMac (G3, G4, G5), and other G3,G4, and G5 machines. This also works with some IBM machienes. This easy guide that I made will show you how to boot a live CD of Ubuntu without Installing anything (unless you want to install Ubuntu.) You can install Ubuntu to your HDD if you want. It boots by itself, however, since PPC doesn't support "GRUB", it runs "yaboot". The guide below explains all this... By the way.... You must be running Mac OS X on your mac to do this. Do this guide on a G3,G4, or G5 mac. Thanks.....

1) Navigate your browser over to [http://wiki.ubuntu.com/PowerPCDownloads](http://wiki.ubuntu.com/PowerPCDownloads).

2.) Locate your preferred Ubuntu "Flavor". I am running 10.04 PPC Edition, so I'm sure you'll find something. If possible, do not use the ftp:// links.

3.) Click the link (in http:// format) and again click the link that says "Mac (PowerPC) and IBM-PowerPC (Power5) Desktop CD". Please note that these releases are for G3, G4, and G5 Macs and IBM-PowerPC computers.

4.) Download the image (while using Mac OS X. Use the computer that you are wishing to install or 'test' Ubuntu on.. If you can't do this... It's fine). It should take around 2 to 2.5 hours on a generic DSL connection. If you are on dial-up, you may want to let it download during the day or at night.

If you are using Safari 3.0 or higher, when it gets finished (before it mounts), it may ask you the following messages in the downloads window:
"Mounting/ or Downloading this may harm your computer"
"(Name of File) contains an application. Do you want to continue?".
Click "Continue" to both of these.

If you are using Firefox, you should be fine.....

5.) If you were using Safari, it most-likley mounted the image on the desktop. Drag the "Flash Drive looking" icon to the dock where the trash is at. This should eject it. If you were using Firefox, it gave you a prompt at the beginning. If it mounted, eject it the same way, but DON'T DELETE THE .iso FILE!

6.) Open Mac OS X's "Disk Utility" application. Search it in Spotlight or locate it in your Finder window (Applications (Folder) > Utilities > Disk Utility.

7.) Once you have it open, drag the .iso file to the blank (white) part under the "Device Sources".

8.) Once you have that done, click on the .iso file and (in the upper left hand corner of the window..) click "Burn". It worked for me, but it may not work for you: it may or may not fit on a "CD".

9.) Follow the on screen prompts and click "Burn".

10.) Once it has burned, depending on what you clicked, it will eject it or mount it. If it ejected it, stick it back in the drive. It should "mount" on the desktop.

11.) Close all applications and SHUTDOWN the mac. Do not unplug the cord (DC Cord).

12.) Turn on your mac. The SECOND YOU HIT THE POWER BUTTON, Let it go and hold down the "C" key. Hold the "C" key while the screen is still black, but the computer is ON. This is where the timing matters.

13.) If you downloaded the right copy (PPC, NOT INTEL), and everything went right, in about 5 minutes or less, you should have a live copy of Ubuntu booted. I would suggest backing up your OS X partition before you install.

Also, I am NOT NOT NOT responsible if you try to do this and possibly mess up your mac. It worked for me and I have it installed. By the way, don't screw around with "GParted" because if you delete a very small partition, you can delete your Mac OS X partition and it may delete if you mess with it, even if you don't think it will. _**So, it's safe to stay AWAY from GParted unless you know what you are doing. **_It worked for me, and I have it installed, so it should work for you. This is a post to answer all of your questions. If you need help, you can message me and I will help.

Thanks!                                                       :grin:

---

### Post by MacHackers on 2011-06-16
They haven't uploaded Unity for PPC Systems yet.

---

### Post by MacHackers on 2011-06-17
> **Grexe said:**
> wish I had found this thread earlier - had to go through Ubuntu->Kubuntu migration because I could not find the PPC ISO with Google ;)

A note on repositories: I also had problems in finding repositories, also for Austria, the mirrors that are configured by the installer do not offer any PPC-binaries, so this is actually a bug.

You can use this handy [repository-generator]("http://www.ubuntu-nl.org/source-o-matic/") but be sure the mirror you select offers PPC-packages (just open one of the repository-URLs in your browser and look in dists/<your distro>/ if it contains a PPC-directory.
In my case, I had to switch to "Germany", you may want to pick the closest match that offers PPC-packages.
Hey guys... I posted how to install the Ubuntu PPC edition the other day.. Maybe you should check it out.

---

### Post by jamielooiswong on 2011-06-26
Can somebody expand the explanation of how to do a proper 7.04 full  Xubuntu install? Right now it simply says  "It would be possible to  install with this and then upgrade to the final release." which is a  little vague for newcomers.

Does anybody know *why* there's no Xubuntu PPC final? Arguably it's  the most useful of all the Ubuntus for PPC users, since it tends to  cater to machines of a spec lower than that you'd want to comfortably  run OSX on.

---

### Post by nerdy_kid on 2011-06-29
> **jamielooiswong said:**
> Can somebody expand the explanation of how to do a proper 7.04 full  Xubuntu install? Right now it simply says  "It would be possible to  install with this and then upgrade to the final release." which is a  little vague for newcomers.

Does anybody know *why* there's no Xubuntu PPC final? Arguably it's  the most useful of all the Ubuntus for PPC users, since it tends to  cater to machines of a spec lower than that you'd want to comfortably  run OSX on.

7.04 is unsupported, install a later version and then just install the xubuntu-desktop package.

---

### Post by pauljwells on 2011-07-04
> **MacHackers said:**
> They haven't uploaded Unity for PPC Systems yet.

Erm, what do you mean? Both unity and unity-2d are in the daily builds, and if you enable the unity-2d ppa, although there are no binaries the source builds easily. I have 3.8.8 on my G5 and very nice it is too. For the reluctant to compile, I put ppc debs here (for 11.04):

[http://dl.dropbox.com/u/18375146/unity-2d-3.8.12-0ubuntu1%7Ebzr631.zip]("http://dl.dropbox.com/u/18375146/unity-2d-3.8.12-0ubuntu1%7Ebzr631.zip")

enjoy...

EDIT: I don't have the latest version on dropbox. These work but the latest builds are much improved.

Add the daily unity-2d ppa to your sources and then follow this procedure to build the latest released source. It's easy and the latest builds are really slick!

[http://ubuntuforums.org/showpost.php?p=11110818&postcount=2]("http://ubuntuforums.org/showpost.php?p=11110818&postcount=2")

---

### Post by rsavage on 2011-07-09
I've started putting together a set of instructions for installing Lubuntu Natty (with Firefox 6) on PowerPC here [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) . "*The objective of the lubuntu project is to create a faster, more lightweight and energy saving variant of Ubuntu by using LXDE, The Lightweight X11 Desktop Environment, as its default GUI.*" See [http://lubuntu.net/about](http://lubuntu.net/about) .
 
Even if you choose not to install Lubuntu, you maybe interested in some of the instructions/information in the thread. For example, there are instructions to create a bootable usb flash stick from both Linux or Mac OS X. Running a Live CD from a USB stick is so much more rewarding than from an actual CD. A CD is very very very slow and will never give a true reflection of what the installed system will be like. USB is faster than a CD, but please be aware it is still slower than a hard drive and the computer also has to de-compress the data that's been squeezed onto the 'CD'.
 
The Lubuntu instructions/thread also describes how to set up a command line only base ubuntu system. Once you have that installed you can add any variant of Ubuntu you wish. Just type the command "sudo tasksel" and you'll be given a list to choose from. Included in the list are Ubuntu, Xubuntu, Kubuntu, Ubuntu Netbook and Edubuntu.  I've done this successfully for Natty desktop versions of both Xubuntu and Kubuntu.
 
Lubuntu is considerably lighter than normal Ubuntu and is very quick to boot (by far the quickest I've tried). There really is no need to install old (and unsupported) versions of Ubuntu if you think your hardware is too old. Lubuntu Natty is much better looking than previous versions and has a more 'with it' feel. It also has Firefox 6 so you'll have the very latest browser too!
 
The script I've put together for installing PowerPC Lubuntu Natty is easily customizable to your own preferences. It does not rely on one big umbrella meta package to install everything, but instead installs packages individually. Hopefully, this will mean it is more stable when Natty is updated to 11.10 'Oneiric Ocelot' and beyond.
 
I think the lubuntu instructions are already pretty comprehensive, but I keep thinking of things to add to them. There are already instructions for setting up wifi, configuring an xorg.conf file, as well as, how to add codecs on PowerPC. I'll keep editing them so watch out for updates!

---

### Post by trungvkvk on 2011-07-14
I've successfully installed Java from the Medibuntu repo. Based upon prior experience, I selected the sdk version.
thank you very much

---

### Post by phillw on 2011-08-27
Hi,

following on from a chat about us having 11.10 include an alternate (text based) installer iso image, the request was made to those who look after such things at Canonical and they not only delivered the i386 that was requested, but a full set that includes images suitable for G3 Macs both as alternate and LiveCD. Please note that these are still daily builds and 11.10 is still at alpha stage, so are not suitable for 'production' machines, but may be of interest to anyone who likes to have a tinker.

Head over to [Testing](https://wiki.ubuntu.com/Lubuntu/Testing) for a bit more background on them. As Lubuntu is a really small team, we'd appreciate anyone who could test them out and report any issues. I have access to an elderly iMac, so I'll do what testing I can, but I don't know of any others on the Lubuntu team who have Macs.

Regards,

Phill.

/edit.... there is problem with the initial builds of the alternate isos... please do not try to use them.

---

### Post by B_Free on 2011-09-08
the live cd
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

---

### Post by awesomemac on 2011-09-13
Hi, I am a Mac user and my computer recently crashed. It was running OS X 10.4.11. I realize it was a GUI problem now, but i deleted my Hard drive and installed OS 9, which I am beginning to hate because you can't really do crap with it. Then, I remember Linux. if someone could please help me find out which version I need to use that would be appreciated. I've got me a 500MHz PPC G4 with about 1.5GB ram I think (need to check lol) and about 80GB HD space. Also, if I could install it onto a USB flash drive, that would be appreciated. It's a 8GB USB stick. Don't need it to fit on there, but just thought it'd be nice so that I could have a backup disk in case my system crashed or something. Also, I am currently using a 2GHz Intel macbook with 2GB RAM, and if I could find something for that, that'd be cool too. It's running OS X 10.6.8 atm. Any help is greatly appreciated! 

Thanks!!!!

---

### Post by svtguy88 on 2011-09-15
^^^You cannot boot off of the USB ports on your G4, as they are USB 1.1, which is not sufficient for a boot device.

As for what kind of Linux to run, you can try the link just above your post.  It links to a development release, but you can try the Live CD and see how it works on your particular system.  (note - the PowerPC image is oversized right now, and will not fit on a CD.  give it a few days, and it should be fixed, I think).

Otherwise, for a machine that isn't running a alpha/beta/testing install, I would recommend grabbing a Debian Squeeze PowerPC install CD, and use that.

Regardless, just about any modern Linux install you do will run circles around the functionality of MacOS 9.

---

### Post by rsavage on 2011-09-25
> **pkmgarf said:**
> Regardless, just about any modern Linux install you do will run circles around the functionality of MacOS 9.

I don't think that is true.  I think people need to select a distribution based on the capabilities of their hardware otherwise they are going to be v disappointed/frustrated.  For example, standard Ubuntu is trying to compete with modern versions of Windows/Mac OS X which run on modern hardware.  Whilst probably being a lot more forgiving, standard Ubuntu also requires a modern spec.  

If you have a G3 or G4 then I wouldn't go any higher than the long term release Ubuntu 10.04 (*EDIT: Although some people seem happy with Unity on 11.10*). If you want a newer version such as natty (11.04) or oneiric (11.10) then think about Xubuntu or Lubuntu which are both excellent and run really fast on my G4 (way faster than standard Ubuntu).  

I wouldn't recommend a development release to somebody new to linux unless there is a special reason why they need it.  My own personal opinion (and I know that there are many that will disagree with me on this) is that I wouldn't recommend debian to somebody new to linux.  I just find debian so much harder than Ubuntu.

Everybody has their personal preferences and I think if you have time then it is a good idea to try a few distributions to see what you are happy with.  I like round window corners, shadows and transparency so prefer Xubuntu over Lubuntu, but if I was limited to only 128MB of ram, or had a very slow processor/graphics card then Lubuntu would be my choice.  Some people prefer the long term releases for their stability, but the feedback from the forum seems to be that if you have a nVidia card or want to connect to a new usb device then you may have better performance/success with a  newer release.

This post [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) explains how to install any version of ubuntu/xubuntu/lubuntu etc, as well as, the common fixes you may need.  You don't need a CD to install!!

I'd like to see a lot of the information in the above post migrated over to the PowerPC FAQ wiki so that people can find it more easily.  If you have some spare time then be my guest to do a bit of cut and pasting!  It would be time really well spent to get the PowerPC documentation back up to date.

---

### Post by Ms. Daisy on 2011-10-05
> **mondo2k said:**
> - the simplest  partitioning system you can have on a ppc-Mac with Ubuntu/Xubuntu is [1]  a very small Apple partition so the Mac can boot, [2] a small NewWorld  /boot partition, [3] the main data partition, which mine is of the /ext3  file type, and [4], the /swap file partition. I can't use LVS on my  iMac (it won't boot when I do) and encryption is pretty much pointless  since I need every bit of speed I can get. You may be able to get away  with one or both though.  


So are you saying that I can't just wipe out the Mac OS and install Ubuntu on a G4 Emac?  I need to create a partition for some of the crucial mac system to live on?  Will the Ubuntu installation CD (powerPC version) know this already & take care of it for me?

---

### Post by rsavage on 2011-10-05
> **Ms. Daisy said:**
> So are you saying that I can't just wipe out the Mac OS and install Ubuntu on a G4 Emac?  I need to create a partition for some of the crucial mac system to live on?  Will the Ubuntu installation CD (powerPC version) know this already & take care of it for me?

You can wipe your mac system alright.  When you come to install just select the 'use entire disk' option and the installer will recommend/suggest the necessary partitioning which you can just go with.  It sounds more complicated than it is.

---

### Post by Ms. Daisy on 2011-10-05
.

---

### Post by svtguy88 on 2011-10-06
> **Ms. Daisy said:**
> So are you saying that I can't just wipe out the Mac OS and install Ubuntu on a G4 Emac?  I need to create a partition for some of the crucial mac system to live on?  Will the Ubuntu installation CD (powerPC version) know this already & take care of it for me?

As rsavage said, just click "use whole disk."  That will take care of it for you.

To explain what we are talking about though:

partition 1 is a small partition that all New World macs need to boot (It's not any part of MacOS at all, but simply a boot partition)

partition 2 is the partition that yaboot (the bootloader that is used for your machine) lives on - in a single OS environment this partition points the system to the next partition to actually boot Linux (if dual/triple booting, it points to each of the respective partitions).

partition 3 is the Linux file system

partition 4 is swap space

Just thought I'd break it down a little.  With Linux, it seems, the more in depth you understand something, the more luck you have bringing it back if/when something goes wrong.

---

### Post by blckjck on 2011-10-11
> **pkmgarf said:**
> ^^^You cannot boot off of the USB ports on your G4, as they are USB 1.1, which is not sufficient for a boot device.

As for what kind of Linux to run, you can try the link just above your post.  It links to a development release, but you can try the Live CD and see how it works on your particular system.  (note - the PowerPC image is oversized right now, and will not fit on a CD.  give it a few days, and it should be fixed, I think).

Otherwise, for a machine that isn't running a alpha/beta/testing install, I would recommend grabbing a Debian Squeeze PowerPC install CD, and use that.

Regardless, just about any modern Linux install you do will run circles around the functionality of MacOS 9.

I just booted and installed Ubuntu 10.04 from a live cd via a usb cd-rom on a blue G3/350 with an 8 gig drive and 512mb of ram.  I would think that the G4 can do it also.

---

### Post by svtguy88 on 2011-10-11
I was referring to booting from a USB flash drive.

---

### Post by blckjck on 2011-10-12
> **pkmgarf said:**
> I was referring to booting from a USB flash drive.

 So you got me curious. If I can boot a usb-cdrom drive, I should be able to boot a stick.

So, I created a thumbdrive with a xubuntu-powerpc live cd, and viola, it boots!

---

### Post by svtguy88 on 2011-10-12
^^^^Really??

That is really surprising to me.  I could have sworn nothing without USB 2.0 was capable of booting a flash drive.

How large was the image yo downloaded for Xubuntu?  I've not used a flash drive to install from brefore, but I imagine that if it's a full size (~700 MB) image, it probably takes a LONG time to load.

---

### Post by Ms. Daisy on 2011-10-12
> **pkmgarf said:**
> As rsavage said, just click "use whole disk."  That will take care of it for you.

To explain what we are talking about though:

partition 1 is a small partition that all New World macs need to boot (It's not any part of MacOS at all, but simply a boot partition)

partition 2 is the partition that yaboot (the bootloader that is used for your machine) lives on - in a single OS environment this partition points the system to the next partition to actually boot Linux (if dual/triple booting, it points to each of the respective partitions).

partition 3 is the Linux file system

partition 4 is swap space

Just thought I'd break it down a little.  With Linux, it seems, the more in depth you understand something, the more luck you have bringing it back if/when something goes wrong.

Thanks for the explanation, pkmgarf.  That helped a lot!

---

### Post by blckjck on 2011-10-13
> **pkmgarf said:**
> ^^^^Really??

That is really surprising to me.  I could have sworn nothing without USB 2.0 was capable of booting a flash drive.

How large was the image yo downloaded for Xubuntu?  I've not used a flash drive to install from brefore, but I imagine that if it's a full size (~700 MB) image, it probably takes a LONG time to load.

  The image is a standard ISO image, that happens to be to big for a CD (grrr)  I am trying several different methods to find the easiest way to do a full install.  I hope to write a guide for it. It takes 5 min. to boot up the live "CD", then about an hour to copy and install.  I had a problem with dpkg hanging when cleaning up.  That is one of the reasons I am trying different ways to make this easyier.  It worked fully, complete install, just trying to get rid of glitches.

---

### Post by flatlined on 2011-10-25
> **blckjck said:**
> The image is a standard ISO image, that happens to be to big for a CD (grrr)  I am trying several different methods to find the easiest way to do a full install.  I hope to write a guide for it. It takes 5 min. to boot up the live "CD", then about an hour to copy and install.  I had a problem with dpkg hanging when cleaning up.  That is one of the reasons I am trying different ways to make this easyier.  It worked fully, complete install, just trying to get rid of glitches.


Did you ever get around to writing a guide or is there one around to boot the iso image off a flash drive on a PowerPC Mac? I have an eMac G4 and have yet to get this to work.

---

### Post by jnorthr on 2011-10-25
FYI - 
have found a new provider of mozilla firefox for apples with PPC architectures. Google for tenfourfox or click to [http://tenfourfox.blogspot.com/](http://tenfourfox.blogspot.com/) where you can find a PPC version of the latest firefox for PPC. Dunno about ubuntu for PPC's - sorry.

---

### Post by Pocho la Pantera on 2012-03-25
Hello I am writing because I have problems installing Ubuntu on my PPC G4 eMac. I want to install version 10.0.4 and I have no video.

 Ubuntu is installed because you hear the sound when you start the operating system but I have no video.

 I could say that Ubuntu would run on my eMac:

Información del hardware:

  Nombre del equipo:    eMac
  Modelo de ordenador:    PowerMac4,4
  Tipo de CPU:    PowerPC G4  (2.1)
  Unidades de CPU:    1
  Velocidad de la CPU:    800 MHz
  Caché de nivel 2 (por CPU):    256 KB
  Memoria:    1 GB
  Velocidad del bus:    100 MHz
  Versión de la ROM de arranque:    4.4.9f1
  Número de serie:    G8316285NUF

Thanks!

---

### Post by NStephenH on 2012-05-07
How do I start the GUI, or do I have to download it. It also said that there wers some problems with y graphics card. I am using an iBook g3.

---

### Post by hyderb on 2012-05-29
thanks

---

### Post by boneskid1 on 2012-06-14
alright i am new to this but i was serching for an alternateive to osx on my powerbook g4 17 in.

i see that 12.04 can be installed via live disc but can i install it on my hdd if i so wanted to?

also is there any instructions on how to properly install some of the builds?

and last but not least, what is the best build for the powerbook g4?

Thank you for your help ahead of time
boneskid1

---

### Post by 2blue on 2012-07-08
I am new to this too, at least to buntu on ppc. I burned the lightest version of the buntus, lubuntu 12.04 for my G4 ibook, the regular live CD ("Desktop CD" as oposite to "alternate install CD") is the simplest, it is all wizard run and easy. Full HD install option is availabe as soon as you are booted in the live CD. Make sure you get the [powerpc]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/") build for for the G4. 

I got some very good help with a bug in the boot up stage, that might pop up. It turns out you need to run the command "live b43.blacklist=yes" in the black screen, then after install "Linux b43.blacklist=yes". 

All applications seem to run fine, though I still have not sorted out wireless, and there are probably more that needs atention along the way. Having wired connection to network available will make it easier.

There are few mac users that take the bother with alternatives to OSX, but if you have hardware abandoned by apple or want to do something out side the confindments of OSX, it is very nice to have alternatives. 

It might be helpful with a new sticky thread for the latest 12.04 version, as this thread is getting loooong

---

### Post by miguelbaines on 2012-08-19
Loading 12.04 onto a 2001 Quicksilver G4. Used the Ubuntu alternate iso, burned at slow rate, everything went smooth up until I got the 'yaboot failed to install' message. Searched for nearly a week on the interwebs, was able to edit the yaboot.conf file, saved it, and when it came time to run ybin, that's where the fun begins. For a while I was getting 'permission denied,' but found i was entering the wrong command (apparently), now I'm at a point where it says,

 'could not create temp file, error in building the first stage of loader.'

I can't for the life of me (or maybe I'm not looking in the right direction) find a way to correct this error.

Does anyone have any ideas??

Thanks.

Never mind. I figured it out. Now I just get a grey screen at boot on the ubuntu side, otherwise mac os x boot like a charm.

---

### Post by dubbadan on 2012-08-21
hi. 
(violins please) :-({|=
i'm another frustrated mac ppc user trying to get more life from an old machine rather than throwing it out and getting a new one as apple would love us to do. i have a G5 powermac and for a while now have been feeling like i've been left behind, with applications being made only for the intel macs. i had a friend recently make me aware of ubuntu as an alternative to mac osx. after a brief look on the web i tried a ubuntu 6.06 live cd which seemed to work fine. i backed up and installed it only to find a string of problems arise. it seems as though every time i try to do something, there is something that prevents me from doing it. i was hoping (and was lead to believe) that ubuntu is "easy to use" but it seems to me that its only people that use computers A LOT anyway that are saying that. i'm almost at the point of giving up and jumping back into the giant consumerism vortex, but i saw this thread and thought i'd see if there's anyone still reading it that may have the experience to help. here are a few of the issues i can think of right now:

- i have 2 hard drives in my computer, of which only one seems to be available to me now.

- i can't get newer versions of ubuntu to run on my computer (i have tried 10.04 and 12.04 as live cds)

- using ubuntu 6.06, i can't get the latest firefox version and have had trouble browsing the web as a result.

---

### Post by rsavage on 2012-08-21
Posts in this thread just get ignored.  Despite repeated pleas to the mods to lock the thread, they won't.  
 
Please do not post in this thread with questions, but start your own thread.  People will then be able to find your post easily when searching for the same problem.  Having said that, pretty much every question is already answered in the PowerPC FAQ and Known Issues wiki pages.  See post 1 of this thread (this is the only post of the thread that you need to read).  There is A LOT of bad advice on the internet and these wiki pages are an attempt to give you good reliable advice.  Please help to keep them updated.
 
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by boneskid1 on 2012-08-24
oops saw the first part of the thread

---

### Post by faintingeagle on 2012-09-02
Hello!
I recently bought a PowerBook G4, 1.33Ghz, 1.25Gb of RAM, 80GB HDD, and I realized it just sucked. There's no software support. I got the download listed above and installed it onto a disk.
When it boots to the disk I get an invisible toolbar on the left, that when I scroll my mouse over it the tags show up, but no buttons. The desktop area is white, and when I open the "Install Ubuntu 12.04 LTS" button, nothing happens. I've tried booting in live, live-powerpc, live-nosplash-powerpc, live-nosplash, and any other option in that menu LOL. 
Screenshot: [Here]("http://i.imgur.com/s1qq5.jpg")

Before anyone says anything about the disk, I've installed Ubuntu before and I know what I'm doing, as per the disk's burning.

Thanks all!

---

### Post by Tommy on 2012-09-02
I'm not active in PPC anymore (though for some reason I still subscribe to this topic). I want to offer a suggestion for this sticky PPC entry --

I think if someone writes a NEW entry that reiterates the links to the PPC FAQ info PLUS tells folks to DO NOT REPLY to the sticky entry UNLESS they are correcting some incorrect info in the sticky topic ITSELF. Folks with PPC questions need to create a NEW forum topic with the [PPC] subject tag. 

Once the new post is written, the author can ask the moderators to please make the new post sticky AND to un-sticky the ancient one. I hope they would agree to that, because it won't leave the forum bereft of stickied PPC wisdom.

After that point, when folks ignore what the sticky topic says and add entries onto the new sticky FAQ post, folks can help by flagging the off-topic postings and the moderators can move the postings to a new topic or delete them or whatever.

I suspect the moderators will agree to sticky a new post. The PPC FAQ on the Wiki looks really excellent (especially compared to the old days) and there's a lot of good current info in other topics, we just need to help folks know to use the [PPC] tag so folks like faintingeagle can find what they need. 

(BTW, faintingeagle, I saw someone else posted the exact same problem on this board just a few weeks back. I am not going to say any more about it here. I posted a link to it on your own visitor messages page.)

---

### Post by rafaelfrequiao on 2012-09-04
Hi, i'm testing a daily build of 12.10 (downloaded yesterday) and i can't use any desktop environment. I removed Unity and installed GDM and Gnome-Shell but nothing helped.

Using a PowerBook G4 (5,4).

EDIT: It seems like Kubuntu 12.04 LTS is running without errors from the Live CD. But due to some weird error i can't install it on my HDD.

Please, i am messing around with video options in kernel before boot and nothing worked (even caught a kernel panic) - radeonfb, offb and ofonly... NOTHING WORKED.

---

### Post by rafaelfrequiao on 2012-09-06
UPDATE: using Kubuntu 12.04.1 LTS.

Community supported until April 2015. So far so good.

Messing with my PowerBook, in 2 days, i managed how to get sound and Airport Extreme to work. Later i got the PMU (power management) working.

I self-compiled and tested Linux 3.6.0-rc4 kernel (not-ubuntu) and the PMU stopped working. After that i run apt-get upgrade and got an update to the 3.2 kernel, which was somewhat better and stable.

I'm thinking to write a guide...

---

### Post by mörgæs on 2013-06-22
Bumping to prevent auto-close of the thread. 
Much relevant information is collected here.

---

### Post by phillw on 2013-08-17
[FONT=arial]Hi folks,
[/FONT][FONT=arial]
Lubuntu is still committed to ppc, as are the people who make things like the kernel happen:

[/FONT]
[FONT=arial]As of when the next rebuild happens [1] the kernel for ppc should now boot okay. This has been tested with servers (G3 & G5) only and how it behaves with the multitude of graphics cards apple shipped with their machines is an unknown. Below is the chat I had:[/FONT]
[FONT=arial]
[/FONT]
[INDENT][COLOR=#204a87](22:55:56) [/COLOR][COLOR=#204A87]**phillw: xxxxx**[/COLOR]: do you know if linux-ppc [powerpc] (saucy-proposed) [3.11.0-0.1] is the kernel that will get ppc desktops back working?
[COLOR=#af7f00](22:56:11) xxxxx[/COLOR][COLOR=#AF7F00]**: **[/COLOR]phillw: Should do, yes.
[COLOR=#af7f00](22:56:27) xxxxx[/COLOR][COLOR=#AF7F00]**: **[/COLOR]phillw: I just smoketested it on my G3 and G5, and both work.
[COLOR=#204a87](22:56:57) [/COLOR][COLOR=#204A87]**phillw: **[/COLOR]great, so the cron build tomorrow should put the ppc-lubuntu testers back in the chase?
[COLOR=#af7f00](22:57:45) xxxxx[/COLOR][COLOR=#AF7F00]**: **[/COLOR]phillw: Depending on how quickly I get it migrated, but probably yes.
[COLOR=#204a87](22:58:38) [/COLOR][COLOR=#204A87]**phillw: xxxxx**[/COLOR]: scheduled to start at 16:29 (UTC)  is that enough time for you?
[COLOR=#204a87](22:59:22) [/COLOR][COLOR=#204A87]**phillw: **[/COLOR]or would you prefer an extra 24 hours?
[COLOR=#0c1b84](23:00:43) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]Oh, indeed, it's almost a day until the next build. Yeah, that one should be fine.
[COLOR=#204a87](23:01:31) [/COLOR][COLOR=#204A87]**phillw: xxxxx**[/COLOR]: okies, if you are sure, I will email the testers, obviously they are chomping on the bit to get back to work!
[COLOR=#0c1b84](23:02:43) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]I make no guarantees that various DRM/KMS drivers are working (I don't run consoles on any of my PPC machines, they're all servers), but these kernels at least boot on all my kit, which is a step up from the previous version. :P
[COLOR=#204a87](23:03:05) [/COLOR][COLOR=#204A87]**phillw: **[/COLOR]there's one sure fire way to check :P
[COLOR=#0c1b84](23:03:27) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]3.11 includes a pretty massive changeset to the radeon driver, so that could cut both ways. Maybe it's drastically improved, or maybe it has a ton of new bugs that break it on !x86... We'll see.
[COLOR=#204a87](23:04:55) [/COLOR][COLOR=#204A87]**phillw: **[/COLOR]as always, we rely on the testers to let us know :) That the promise to have a kernel that at least stood a chance of working has been kept, they will be happy and do not 'rant' over bugs.
[COLOR=#0c1b84](23:05:42) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]Well, I can nearly guarantee that it should boot on pretty much any hardware we've supported before. Between yyy and I, we have a pretty wide array of stuff to boot and stress test on.
[COLOR=#0c1b84](23:05:49) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]It's just that he and I both only run headless servers.
[COLOR=#0c1b84](23:05:51) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]So, we'll see. :)
[COLOR=#204a87](23:07:07) [/COLOR][COLOR=#204A87]**phillw: **[/COLOR]the graphics cards that apple used were and are always an issue... they have gotten used to workarounds, only by letting it into the wild can these issues with the graphics cards be started to be investigated :)
[COLOR=#204a87](23:07:38) [/COLOR][COLOR=#204A87]**phillw: xxxxx**[/COLOR]: many thanks to you and yyy for this work, I do know ppc for desktops is a low priority :)
[COLOR=#0c1b84](23:07:42) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]It's not the cards, per se, it's that the radeon driver has become very x86-centric, and very few people care about fixing the PPC bugs with it.
[COLOR=#0c1b84](23:08:09) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]nouveau seems to suffer fewer of those issues (for whatever reason), so the nvidia cards that Apple shipped with later G5s seem to be in better shape.
[COLOR=#204a87](23:09:35) [/COLOR][COLOR=#204A87]**phillw: **[/COLOR]we're still working with G3's and g4's... as long as the darn thing will boot, the graphics cards could be seen as nearly a seperate branch of their own.
[COLOR=#0c1b84](23:10:19) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]Yeah, I haven't tried running X on the ATi Rage128 in my G3 for, like, a decade.
[COLOR=#0c1b84](23:10:38) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]I assume it probably sort of works. But I have no idea, and don't care, as it's a headless router/firewall in my house. :P
[COLOR=#0c1b84](23:11:14) xxxxx[/COLOR][COLOR=#0C1B84]: [/COLOR]Though, the offb driver would work for boring old 2D X. You'd just get zero acceleration.[/INDENT][FONT=arial]

So, allow the daily to build and start testing!!! [2]


Regards,


Phill.
1. [https://wiki.ubuntu.com/Lubuntu/Testing#When_do_they_build.3F](https://wiki.ubuntu.com/Lubuntu/Testing#When_do_they_build.3F)
[/FONT]
2. [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing)

---

### Post by Steve M on 2013-08-30
Nice to see there may be hope for an old Mac I have, it's a G4 but with an aftermarket graphics card. May have to revisit that if I get this current project stable.

---

### Post by wrgt on 2013-10-19
I was successful in installing Lubuntu 13.10 ppc to my Powerbook G4 12" 667mhz, 256mb ram, nvidia geforce fx go 5200. I encountered no problems loading the desktop live cd and running the installation. 
However, there are several problems encountered after the installation. 
The wifi does not work and I had to install b43 firmware and restart. 
I am unable to watch youtube videos in firefox so I had to download and use minitube instead. 
No sounds are coming out of the laptop. Still looking for solutions.
Function keys are not working so I cannot adjust brightness, volume, etc. Still looking for solutions, especially to the brightness issue.
Battery applet would not load to the panel, although I can see my battery charge status in system profiler and benchmark. Just a minor issue.

---

### Post by andi2 on 2013-12-14
Hello,

I've experienced the same sound issue as you've mentioned on my 12" Powerbook G4 and have tried every single stop from the FAQ (mainly deleting the snd-aoa entries from the blacklist), but nothing works out for me. Have tried Debian 7 in parallel and here sound works great. Do you have any positive news on your list of open points?

---

### Post by andi2 on 2013-12-23
There seems to be a crash in the snd_powermac module during start-up:

[   31.655474] ------------[ cut here ]------------
[   31.655485] WARNING: at f2f22e30 [verbose debug info unavailable]
[   31.655489] Modules linked in: cfg80211(F) uio_pdrv_genirq(F) snd_powermac(F) uio(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) apm_emu(F) apm_emulation(F) hid_generic(F) usbhid(F) hid(F) nouveau(F) firewire_ohci(F) sungem(F) sungem_phy(F) firewire_core(F) crc_itu_t(F) ttm(F) drm_kms_helper(F) drm(F) ssb(F) uninorth_agp(F)
[   31.655558] CPU: 0 PID: 23 Comm: kworker/0:1 Tainted: GF            3.11.0-4-powerpc-smp #6-Ubuntu
[   31.655588] Workqueue: events device_change_handler [snd_powermac]
[   31.655593] task: ef935ee0 ti: ef994000 task.ti: ef994000
[   31.655597] NIP: f2f22e30 LR: c005c2c4 CTR: f2f22df0
[   31.655602] REGS: ef995dc0 TRAP: 0700   Tainted: GF             (3.11.0-4-powerpc-smp)
[   31.655605] MSR: 00029032 <EE,ME,IR,DR,RI>  CR: 42402028  XER: 00000000
[   31.655620] 
[   31.655620] GPR00: c005c2c4 ef995e70 ef935ee0 f2f28780 00000000 ef994000 0000430d 00c69000 
[   31.655620] GPR08: f2f28784 00000001 00000001 00001032 42402022 00000000 c0064094 ef8c5df8 
[   31.655620] GPR16: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 c15ff380 
[   31.655620] GPR24: c09f0000 00000001 00000000 c1602500 c15ff180 00000000 c5b0b400 00000000 
[   31.655675] NIP [f2f22e30] device_change_handler+0x40/0x290 [snd_powermac]
[   31.655691] LR [c005c2c4] process_one_work+0x158/0x3cc
[   31.655695] Call Trace:
[   31.655704] [ef995e70] [00000001] 0x1 (unreliable)
[   31.655712] [ef995e90] [c005c2c4] process_one_work+0x158/0x3cc
[   31.655719] [ef995ec0] [c005cc44] worker_thread+0x134/0x3fc
[   31.655729] [ef995ef0] [c0064148] kthread+0xb4/0xb8
[   31.655736] [ef995f40] [c0017120] ret_from_kernel_thread+0x5c/0x64
[   31.655740] Instruction dump:
[   31.655746] 7c0802a6 7d800026 90010024 bf810010 9181000c 3d20f2f3 83c98790 2f9e0000 
[   31.655760] 419e0244 83fe0178 7fe90034 5529d97e <0f090000> 2f890000 409e022c 813f003c 
[   31.655775] ---[ end trace 34d3ae03e2af2a2e ]---

---

### Post by cool3 on 2013-12-30
Great info here.

---

### Post by Deacon Nikolai on 2018-08-07
Are PPC versions still supported?

---

### Post by mörgæs on 2018-08-11
At least they are supported in 16.04. 

You can download the [Lubuntu]("http://cdimage.ubuntu.com/lubuntu/releases/xenial/release/") ISO here (supported through april 2019) and [Ubuntu]("http://cdimage.ubuntu.com/ubuntu/releases/xenial/release/") (april 2021).

Another option is [Debian]("https://www.debian.org/ports/powerpc/").

---

### Post by clifftlong on 2021-05-17
yes its working !!!!! thanks

---

