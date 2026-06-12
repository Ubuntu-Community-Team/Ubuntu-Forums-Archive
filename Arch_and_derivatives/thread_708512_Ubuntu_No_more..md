---
title: "Ubuntu? No more."
date: 2008-02-26
forum: Arch and derivatives
---

### Post by Lord Illidan on 2008-02-26
I am now running 100% Arch Linux.

This distribution is superb...everything I need..and everything works. I think it's the perfect distro for an experienced Linux user.

I think I might pop in to see the release version of Hardy..but I am not as excited as I would be, tbh.

---

### Post by LaRoza on 2008-02-26
Double post?

Arch is great, and I may end up using it someday. (But I am not going to change a working system)

---

### Post by Arthur Archnix on 2008-02-26
I've just repartitioned my hds so that I could give arch a try. Here's hoping I like it as much as you..seeing as how my only experience is about two years of ubuntu

---

### Post by justin whitaker on 2008-02-26
> **Lord Illidan said:**
> I am now running 100% Arch Linux.

This distribution is superb...everything I need..and everything works. I think it's the perfect distro for an experienced Linux user.

I think I might pop in to see the release version of Hardy..but I am not as excited as I would be, tbh.

Begone foul tempter! 

:)

I've been wanting to try Arch for a while, but I just reinstalled Hardy...and I like it. 

Don't tempt me!

:lolflag:

---

### Post by Rumor on 2008-02-26
> **justin whitaker said:**
> Begone foul tempter! 

:)

I've been wanting to try Arch for a while, but I just reinstalled Hardy...and I like it. 

Don't tempt me!

:lolflag:

<stage whisper>
Hey mister! Wanna try an ISO? Sleek! fast! up-to-date! 
</stage whisper>

Welcome Illidan! I made the jump from dual booting Arch / Ubuntu to Arch-only in July and have not looked back.

---

### Post by jken146 on 2008-02-26
I have to admit, it is very tempting to switch completely to Arch.  I don't think I will, though, at least for a while.  That's mainly because I find apt a little bit better than pacman.

---

### Post by bwtranch on 2008-02-26
> **jken146 said:**
> I have to admit, it is very tempting to switch completely to Arch.  I don't think I will, though, at least for a while.  That's mainly because I find apt a little bit better than pacman.

Apt is the worst, here's how it goes:

1. emerge, the pac manager with Gentoo, great and easy-to-use
2. pacman good package management requires some skills
3. aptitude dumb, gets the job done usually, buggy, limited

So, the bottom line on package managers is a mixed bag. I am currently using a Sabayon distro that I like very well. The reason I went for it is because I wanted to check out LVM. And since I'm not allowed to make political statements anymore on this forum...let you conscience be your guide.

---

### Post by Lord Illidan on 2008-02-27
What I like most about Ubuntu as regards repository management is Synaptic. Arch doesn't really have an alternative to it. There are gui frontends, but rather shabby and out of date.
However, from the console, pacman works fine, and it's quite fast too.

---

### Post by Afoot on 2008-02-27
> **bwtranch said:**
> Apt is the worst, here's how it goes:

1. emerge, the pac manager with Gentoo, great and easy-to-use
2. pacman good package management requires some skills
3. aptitude dumb, gets the job done usually, buggy, limited

So, the bottom line on package managers is a mixed bag. I am currently using a Sabayon distro that I like very well. The reason I went for it is because I wanted to check out LVM. And since I'm not allowed to make political statements anymore on this forum...let you conscience be your guide.
I agree, apt is the worst... it has some serious issues with for instance removing dependencies of meta packages. With portage and pacman that works just as you expect. Debian should really try to clean it up...

---

### Post by K.Mandla on 2008-02-27
I'd have to agree. I thought aptitude was cool until I started using pacman. There's no contest.

---

### Post by yabbadabbadont on 2008-02-27
If only they could stay current with security fixes...

I noticed that they finally updated mplayer yesterday.  The old version had multiple critical security issues.  (and it only took them 21 days to update it  :roll:)

I decided to go back to gentoo until arch can acquire enough developers to keep up with security updates.  From reading the dev mailing list it looks to me like the current devs are a bit overwhelmed at the moment.

---

### Post by marscay on 2008-02-28
i'm just about to completely switch my distro from ubuntu to arch after testing it out for a week or so.

in my opinion it blows ubuntu out of the water if you have moderate linux skills.

there might not be a nice package GUI but pacman in my eyes is far superior to apt, between that and the AUR everything just works beautifully .....and MUCH faster than Ubuntu.

haven't had compiz crash out on me once which i can't say for either feisty/gutsy.

i also prefer the more simplistic approach to startup scripts/init etc 

i still think ubuntu is a great distro expecially for ppl new to linux but arch is definitely superior if you can handle it.

---

### Post by kellemes on 2008-02-28
Don't understand why people think Pacman is better as aptitude or apt-get, it simply does it's job and it's a little less typing.
As far as I know it's not even offering wild cards.. or it must be a recently added feature.
Also it doesn't have moo.

---

### Post by fwojciec on 2008-02-28
> **kellemes said:**
> Don't understand why people think Pacman is better as aptitude or apt-get, it simply does it's job and it's a little less typing.
As far as I know it's not even offering wild cards.. or it must be a recently added feature.
Also it doesn't have moo.

The reason I prefer pacman has more to do with makepkg/PKGBUILD than with pacman directly.  I agree with you that as far as installing packages is concerned pacman and apt-get are pretty much on par.  It is incomparably easier, however, to make/customize packages using pacman tools -- and that's of crucial importance to me.

Debian, it seems to me, is designed to create a separate caste of package creators and maintainers -- this is a means to an end, I suppose, the end being rock-solid stability of the final product.  The side effect of such an arrangement is that the process by which packages are created is shrouded in mystery and, for practical purposes, inaccessible to regular users who are expected to be satisfied with the ability to install a wide range of available binary packages or, if worst comes to worst, to compile sources manually.

In this sense any debate regarding whether apt-get or pacman are "better" is kind of pointless, IMO -- what is meaningful is not so much their relative capacities as far managing packages is concerned but the difference between the design philosophies they represent.  I happen to prefer the philosophy behind Arch and pacman which I see as a programmatic attempt at empowering the regular user.

---

### Post by mips on 2008-02-28
> **kellemes said:**
> ... and it's a little less typing.



How is it less typing?

apt-get install x
vs
pacman -S x

apt-get update
vs
pacman -Sy

apt-get upgrade or apt-get dist-upgrade
vs
pacman -Syu

When it comes to dependancies pacman performs better than aptitude.

---

### Post by marscay on 2008-02-28
> **kellemes said:**
> Don't understand why people think Pacman is better as aptitude or apt-get, it simply does it's job and it's a little less typing.
As far as I know it's not even offering wild cards.. or it must be a recently added feature.
Also it doesn't have moo.

i agree with fwojciec, it's not strictly pacman but the package system as a whole ...it's more flexible than apt.

for me pacman handles dependancies better too.

---

### Post by MONODA on 2008-02-28
yeah i tried out arch for a bit but i cant download large files at any time since i have a download limit during the day so since arch requires you to download a lot besides the iso (i donwload the iso at night) i had to give it up...

---

### Post by machoo02 on 2008-03-05
Uh-oh....I think I might have caught the Arch bug.  Decided to try it out on my laptop today, and I think that the experience can be summed up in 3 words.  **Sweet!  Merciful!  Crap!**  Bootup and shutdown is wicked fast, compiz runs amazingly, etc.  When I get a little bit of free time, and after I work out a few minor things like suspend/hibernations, I might just switch over completely.

---

### Post by deepclutch on 2008-03-05
me too! :p 2 days on archlinux now!kdemod is superb !
@[yabbadabbadont]("http://ubuntuforums.org/member.php?u=30249"):
what?security issues on arch is fixed slow? :-|
I have core,extra,community,unstable and kdemod repositories enabled.
Is there *any* reason for a desktop user to be worried :?

---

### Post by Ripfox on 2008-03-05
Pardon the ignorance...what is Arch built on?

---

### Post by LaRoza on 2008-03-05
> **ripfox said:**
> Pardon the ignorance...what is Arch built on?

[http://en.wikipedia.org/wiki/Arch_Linux](http://en.wikipedia.org/wiki/Arch_Linux)

---

### Post by Ripfox on 2008-03-05
So do I want the "core" or "ftp" iso?

---

### Post by Ripfox on 2008-03-05
anyone?

---

### Post by fwojciec on 2008-03-05
> **ripfox said:**
> So do I want the "core" or "ftp" iso?

Either will be fine -- if you choose the FTP iso keep in mind that some people have reported an issue with it...  during the FTP install, apparently, the /tmp folder is created with incorrect permissions so you might have to correct it manually before installing X and a desktop environment (the correct permissions are "1777").

If you connect to the internet using wifi then it's probably better to go with the core iso.

---

### Post by Ripfox on 2008-03-05
Does the core iso include a graphical desktop environment (X)?

Is it KDE, Gnome, XFCE? 

Just curious...

---

### Post by deepclutch on 2008-03-05
I have installed X,Kdemod etc from scratch via ftp,no bloats hence :D!

I have my installation via ftp method.it is easy although 3 outstanding bugs exists:
my post here:
> Hey!Nobody dare to try [Archlinux]("http://archlinux.org/")?2 days on archlinux now!apart from 3 minor bugs which I fixed on my install,archlinux with kdemod(modular kde) is the fastest kde IMHO :D !enjoying kde in arch!way better than suse experience!
guess what?I am booting more into my arch install rather than the good ol` Debian Sid these days! :D
BTW,[kdemod]("http://kdemod.ath.cx/"),the modular kde is the answer for the default kde install which installs everything hence called as bloat!
Works perfect for me!Oh!and arch linux may need some experienced linux user to try,not n00b's!esp pacman(I liked it :D ),repo management etc.

for those who are aspiring for archlinux installation/for old archlinux users:
the three bugs I had on default ftp install were:
1.the /etc/pacman.d/mirrorlist the setup server line is pucked up after installation.
the last line was like this:
```
# Setup-Entry
Server = ftp://ftp.ibiblio.org/pub/linux/distributions/archlinux/[COLOR=Red]**mirrorlist**[/COLOR]/os/i686 
```which I edited correctly to:
```
# Setup-Entry
Server = ftp://ftp.ibiblio.org/pub/linux/distributions/archlinux/**[COLOR=Black]$repo[/COLOR]**/os/i686 
```2.the hal mounting trouble which needs adding of a new file :/etc/hal/fdi/policy/preferences.fdi
with contents:
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->


<!-- 
  The following shows how to put sync and noatime on for devices smaller then
  1Gb and off for device larger then that. Note that the sync option can wear
  out device faster then you'd like too. See
  http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html for
  more info.
--> 
<!--
  <device> 
    <match key="block.is_volume" bool="true">
      <match key="volume.size" compare_lt="1000000000">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
      </match>
      <match key="volume.size" compare_ge="1000000000">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">false</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">false</merge>
        </match>
      </match>
    </match>
  </device>
--> 
</deviceinfo>

```default Gnome and hal is way  better and it works!
after adding these lines,everything works again in kde(automounting/umounting of DVD/cd drives,usb drives etc etc)
3.the default permission for /tmp directory is 755 which u should change to :
```
chmod 1777 /tmp 
```a minor glitch too:
the dvd/cd drive line was missing in /etc/fstab.I added it manually and that problem also fixed :)
```
/dev/dvd  /media/cdrom0  udf,iso9660 ro,user,noauto,unhide   0     0 

```Note that /dev/dvd is a symlink.

So,why not arch guys? ;)[http://ubuntuforums.org/showthread.php?t=713597](http://ubuntuforums.org/showthread.php?t=713597)

---

### Post by Ripfox on 2008-03-05
That makes absolutely no sense to me frankly. :lolflag:

What is the DEFAULT desktop environment?

---

### Post by fwojciec on 2008-03-05
> **ripfox said:**
> Does the core iso include a graphical desktop environment (X)?

Is it KDE, Gnome, XFCE? 

Just curious...

After installation the system boots into console login prompt -- from then on you can set up basic things like networking, users, startup daemons, etc. and then just use the package manager to install X and whatever DE/WM you want.

If you chose to go for it I strongly recommend that you take advantage of the great [installation guide](http://wiki.archlinux.org/index.php/Beginners_Guide) which outlines the procedure from installation to getting a basic graphical environment up and running.

---

### Post by Ripfox on 2008-03-05
Meh...sounds like a sticky mess of a pain in the *** really. If I wanted to do that I would just install an Ubuntu server and add on x + blackbox or something. That's fast too. :)

---

### Post by PurposeOfReason on 2008-03-05
> **ripfox said:**
> Meh...sounds like a sticky mess of a pain in the *** really. If I wanted to do that I would just install an Ubuntu server and add on x + blackbox or something. That's fast too. :)
First try took me four hours on a max connection of 160kbs. My last try (4th) took two hours. I'm still learning too. I had to slap HAL around all day today so it would auto mount a cd if I put it into the drive and still let me unmount it without a reboot.

---

### Post by fwojciec on 2008-03-05
> **ripfox said:**
> Meh...sounds like a sticky mess of a pain in the *** really. If I wanted to do that I would just install an Ubuntu server and add on x + blackbox or something. That's fast too. :)

If you're looking for something that's easy "just works"-style and gui-oriented then Arch is definitely not a good choice.  As far as performance and customizability are concerned, however, Ubuntu server installation is merely a half measure compared to what Arch brings to the table.  Also, once it is set up, Arch requires next to no maintenance and since it is a rolling release distro it has no upgrades every 6 months -- so in a way it is distros like *buntu that can seem like "a pain in the ***" for those who have become accustomed to the Arch way of doing things :P

It all depends on what you prefer, in the end...

K.Mandla has written an nice [post](http://kmandla.wordpress.com/2008/03/04/should-ubuntu-be-more-like-arch/) discussing the relative virtues of Arch and Ubuntu on his blog -- have a look if you're interested.

---

### Post by Ripfox on 2008-03-05
Like I said, thanks for the info but, yeah Hardy is for me.

---

### Post by Rumor on 2008-03-06
> **ripfox said:**
> Pardon the ignorance...what is Arch built on?

It isn't. Arch is an independently developed Linux distro.

---

### Post by jseiser on 2008-03-06
ubuntu server + blackbox would be as slow as arch with kdemod.

---

### Post by Rumor on 2008-03-06
> **ripfox said:**
> Meh...sounds like a sticky mess of a pain in the *** really.

Not really. It sounds like [the Arch Way]("http://wiki.archlinux.org/index.php/The_Arch_Way") of doing things :)

> **ripfox said:**
> If I wanted to do that I would just install an Ubuntu server and add on x + blackbox or something. That's fast too. :)

That wouldn't really be the same. An Ubuntu Server install will have given you some packages that a base install of Arch will not have given you. Since it is a server install, it assumes you want the server packages. Arch does not make any assumptions of what you want to do with your system. It lets you choose what you want to install, what you want to run at start-up and so on.

Arch is what you make it.

---

### Post by steveneddy on 2008-03-06
Besides package management, what are the main advantages of arch over a distro like Ubuntu?

I would like to run OPENSuse or Fedora, but the community lacks something that I have here.

I finally have things running well on Ubuntu and have stopped upgrading so nothing breaks.

Relaibility, stability and everything working, every time, is my bottom line.

I don't have time for constant tweaks and repairing something that "broke" in an "upgrade".

Would arch make any of these issues better, or is it a "tweakers" OS?

---

### Post by fwojciec on 2008-03-06
> **steveneddy said:**
> I finally have things running well on Ubuntu and have stopped upgrading so nothing breaks.

I think it's unlikely that you would enjoy Arch -- Arch could not be used the way you choose to use Ubuntu, it pretty much requires that you update it on regular (as in daily) basis.

---

### Post by deepclutch on 2008-03-06
Anyone using pulseaudio server on Archlinux?especially on kdemod?
Howz it?any outstanding bugs-with flashplugin etc?
//offtopic-sry!

---

### Post by mips on 2008-03-06
> **steveneddy said:**
> 
Would arch make any of these issues better, or is it a "tweakers" OS?

Weird thing is when I had ubuntu I was always tweaking it, with arch I have not done ANY tweaking since initial setup. It is actually the distro with the least tweaking I have come across so far.

Being a 'build your own distro' I though it would be the other way round and one would be constantly tweaking stuff.

---

### Post by Rumor on 2008-03-06
> **steveneddy said:**
> Besides package management, what are the main advantages of arch over a distro like Ubuntu?

I would like to run OPENSuse or Fedora, but the community lacks something that I have here.

I finally have things running well on Ubuntu **_and have stopped upgrading so nothing breaks_**.

Relaibility, stability and everything working, every time, is my bottom line.

I don't have time for constant tweaks and repairing something that "broke" in an "upgrade".

Would arch make any of these issues better, or is it a "tweakers" OS?

While Arch is a tweaker's OS, I can echo Mips' comment that I have not tweaked it beyond the initial install. Once it is set up the way I want, there is no need.

The reason I emphasized a part of your post is that this was one of the reasons I left Ubuntu. Every time there was an update to the restricted headers, my nVidia drivers would not work and X broke for me. It was frustrating to the point that I decided to try something else.

I know there have been X issues with Arch for some users, but for me, pacman has not let a conflict between my nvidia package and the Arch kernel break my system. Each time there has been a conflict where pacman has said nothing was upgraded because it would have caused a problem, I've been able to upgrade just the kernel and my nvidia drivers from the command line and then go on without any issues.

For me, Arch updates have been seamless. For me, nothing has broken. I've found it more stable than Ubuntu, though it may very well be that I now know more about how Linux and its related bits and pieces work than I did when I was running Ubuntu.

---

### Post by mips on 2008-03-06
> **Rumor said:**
> 
For me, Arch updates have been seamless. For me, nothing has broken. I've found it more stable than Ubuntu, though it may very well be that I now know more about how Linux and its related bits and pieces work than I did when I was running Ubuntu.


Lol, I still cringe a bit everytime I do a pacman -Syu and reboot, why I don't know as it has never let me down. Just today my downloaded updates were about 170MB and as per usual things just work afterwards.

---

### Post by Ripfox on 2008-03-06
Arch is for tweakers, man :lolflag:

J/K

---

### Post by cprofitt on 2008-03-07
> **Lord Illidan said:**
> I am now running 100% Arch Linux.

This distribution is superb...everything I need..and everything works. I think it's the perfect distro for an experienced Linux user.

I think I might pop in to see the release version of Hardy..but I am not as excited as I would be, tbh.

I too have found Arch and like it -- though I am not a big fan of KDE.

I am in a debate over Debian v. Arch. I like Arch because it is much more up-to-date that Debian stable and I really like Pacman.

---

### Post by LaRoza on 2008-03-07
> **ripfox said:**
> That makes absolutely no sense to me frankly. :lolflag:

What is the DEFAULT desktop environment?

There is no default.

Arch is very light and barebones. You install what you want, which is easy with its package manager.

---

### Post by deepclutch on 2008-03-07
look at bsd style initscripts -it is sooo cool :cool: and simple! :p

BTW,archlinux users prefers kde if I am not wrong ;)

---

### Post by Rumor on 2008-03-07
> **PrivateVoid said:**
> I too have found Arch and like it -- though I am not a big fan of KDE.


Well, since KDE is just one of many choices, use what you prefer. I use Gnome on my desktop and Fluxbox on my laptop.

> **deepclutch said:**
> BTW,archlinux users prefers kde if I am not wrong ;)

Actually, I think Arch users prefer quite a wide range of desktops. Xmonad and Awesome seem to top this month's screenshot thread in the Arch forums.
the last time a "what is your desktop" type thread was run, I think Gnome came out on top by a small margin.

---

### Post by bonzodog on 2008-03-07
> **deepclutch said:**
> 
BTW,archlinux users prefers kde if I am not wrong ;)

Hrm...I don't know about that; Yes, kdemod is one of the big reasons that Arch is gaining users at an almost apocalyptic rate, but I find that there are a lot of *box/wmii/dwm/awesome Wm users as well.

---

### Post by PurposeOfReason on 2008-03-07
> **deepclutch said:**
> look at bsd style initscripts -it is sooo cool :cool: and simple! :p

BTW,archlinux users prefers kde if I am not wrong ;)

There forums show a lot of tilers and *boxs. I almost never see gnome.

---

### Post by raul_ on 2008-03-07
> **Rumor said:**
> It isn't. Arch is an independently developed Linux distro.

I think it's actually built of CRUX and Slackware, with a bit of BSD-like init scripts.

The best description i've seen of Arch is

**"Arch is Linux with a great package manager"**

---

### Post by Gigamo on 2008-03-07
I've also noticed many arch users use tiling wm's. Including myself. But that's because I find it extremely handy, and I used the WM on ubuntu as well. However, like said, the arch install comes with no DE, not even X. You entirely choose what you install and whatnot.

---

### Post by RedSquirrel on 2008-03-07
> **deepclutch said:**
> what?security issues on arch is fixed slow?

That was the case with mplayer. It took them three weeks to fix the problem after the bug report was filed.

[http://bbs.archlinux.org/viewtopic.php?pid=332405](http://bbs.archlinux.org/viewtopic.php?pid=332405)


With regard to security, you might want to browse the Arch forums, for example:

**Arch approach to security**
[http://bbs.archlinux.org/viewtopic.php?pid=332180](http://bbs.archlinux.org/viewtopic.php?pid=332180)


I've been using Debian (mainly sid) exclusively for about two weeks now ("business card" iso, only the base system + Openbox and a few other goodies). It seems just as light or lighter than Arch to me.

Configuring it is different from Arch (no rc.conf!), but I have a reasonable knowledge of its guts so it's not a problem for me. Mind you, after using Arch for a few months I find myself typing "pacman" instead of "aptitude" every once in a while. :)

---

### Post by deepclutch on 2008-03-08
well!I am just a week old to archlinux.for the past 6-7 yrs am on Debian and for the past 3 yrs on Debian Sid,which I had installed via network-install iso.

I am very much satisfied with Debian Sid apt-pinned with experimental and testing repos ;)

even my siggy can be helpful :p

---

### Post by raul_ on 2008-03-08
Has anyone spoke of the AUR?

---

### Post by ST.x on 2008-03-08
> **K.Mandla said:**
> I'd have to agree. I thought aptitude was cool until I started using pacman. There's no contest.

QFT, + yaourt <3

---

### Post by raul_ on 2008-03-08
IMHO the AUR owns checkinstall :) although checkinstall is easier to use than making a PKGBUILD

---

### Post by finferflu on 2008-03-08
Not that easier. If you manage to get to the checkinstall command you can surely write a PKGBUILD. The only difference in writing a PKGBUILD is making sure you use fakeroot'ed directories.

---

### Post by herbster on 2008-03-09
Arch rocks! Been using it a while now and pacman is the bomb. Arch is really great for one who wishes to further knowledge of their system/linux in general as it really requires you to know what the hell you're doing much moreso than with Ubuntu.

And yes, AUR is very neat, as is ABS. A very, very user-friendly, fast, simple system for building packages and finding practically anything you need to install.

I probably like this community more than Arch's, however, as the snobbery and holier-than-thou-ness many of them give off to anyone who uses/used Ubuntu is incomprehensibly lame. I mean, it's a computer at the end of the day, yeesh.

---

### Post by aeto on 2008-03-10
Whatever works, ja? ;) 

Anyway, a buildscript can be anything with the correct variables. Anything other than something called PKGBUILD can be specified via makepkg.conf or at runtime with option -p.

```
pkgname=monkey
pkgver=1
pkgrel=1
arch=(i686)
source=(http://animals.china.billgates/monkey.tar.mz)

build() {
cd $srcdir/$pkgname-$pkgver

mkdir -p $pkgdir/home/pidstew/monkey
cp -r * $pkgdir/home/pidstew/monkey/
}
``` And then ```
makepkg -g >> thescript && makepkg -icp thescript
``` should take care of your checkinstall habit. Seriously, that was just less than 30 secs.

---

### Post by johnnybirdman on 2008-03-10
> **machoo02 said:**
> Uh-oh....I think I might have caught the Arch bug.  Decided to try it out on my laptop today, and I think that the experience can be summed up in 3 words.  **Sweet!  Merciful!  Crap!**  Bootup and shutdown is wicked fast, compiz runs amazingly, etc.  When I get a little bit of free time, and after I work out a few minor things like suspend/hibernations, I might just switch over completely.

I'm looking to try this out on a  laptop as well.  What, if any, guides did you use for install.
If installing ubuntu is a 1 (on a 1 to 10 scale of hardness), where would you put Arch?
Thanks for any info.
J.

---

### Post by herbster on 2008-03-10
> **johnnybirdman said:**
> I'm looking to try this out on a  laptop as well.  What, if any, guides did you use for install.
If installing ubuntu is a 1 (on a 1 to 10 scale of hardness), where would you put Arch?
Thanks for any info.
J.

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

Put it this way: With Ubuntu, you install the system and many of the main parts of an everyday user's needs are there (evolution, firefox, etc.-- hell, even compiz). You install Arch and you are booting into a terminal, basically. You'll have to install the X server, gnome, window managers, firefox, etc. yourself. This is not to comment on the difficulty, as the installation of these packages are a breeze, but to say that you get a very, very barebones system whereby you yourself then choose exactly what you want.

---

### Post by miggols99 on 2008-03-10
> **johnnybirdman said:**
> I'm looking to try this out on a  laptop as well.  What, if any, guides did you use for install.
If installing ubuntu is a 1 (on a 1 to 10 scale of hardness), where would you put Arch?
Thanks for any info.
J.
You could use my guide, which is much more "newbie" friendly :)

[http://archux.com/page/installation-guide](http://archux.com/page/installation-guide)

---

### Post by johnnybirdman on 2008-03-10
> **herbster said:**
> [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

Put it this way: With Ubuntu, you install the system and many of the main parts of an everyday user's needs are there (evolution, firefox, etc.-- hell, even compiz). You install Arch and you are booting into a terminal, basically. You'll have to install the X server, gnome, window managers, firefox, etc. yourself. This is not to comment on the difficulty, as the installation of these packages are a breeze, but to say that you get a very, very barebones system whereby you yourself then choose exactly what you want.

Thanks.  I'm running ubuntu server for a small web page so barebones/command line stuff does not bother me, in some ways I like it more.
Thanks again.
J.

---

### Post by johnnybirdman on 2008-03-10
> **miggols99 said:**
> You could use my guide, which is much more "newbie" friendly :)

[http://archux.com/page/installation-guide](http://archux.com/page/installation-guide)

Thanks miggols, I'll give it a try and let you know how it goes.

---

### Post by mips on 2008-03-10
> **johnnybirdman said:**
> I'm looking to try this out on a  laptop as well.  What, if any, guides did you use for install.
If installing ubuntu is a 1 (on a 1 to 10 scale of hardness), where would you put Arch?
Thanks for any info.
J.

It really is not as hard as it is made out to be. It is easier than Gentoo, some bsd's and some other linux distros. If you can follow the wiki then you will be fine.

Btw, it runs like snot on my 1.4ghz celron, 512mb laptop.

---

### Post by MisfitI38 on 2008-03-10
> **raul_ said:**
> I think it's actually built of CRUX and Slackware, with a bit of BSD-like init scripts.

The best description i've seen of Arch is

**"Arch is Linux with a great package manager"**

Actually, Arch is independently developed from scratch, and is not based upon any other distro nor OS. Judd Vinet said that he was initially inspired by ideas behind CRUX, but built Arch from scratch. While Arch does use 'BSD-style' init scripts, it is not based on BSD init code either. Basically, 'BSD-style' init scripts are scripts called from a single rc file, rather than from many files within a directory, in the spirit of simplicity, which is a driving force behind the Arch Way. Also, Arch and Slack share some similarities, but Arch is not based on Slack either.
;)

---

### Post by MisfitI38 on 2008-03-10
> **machoo02 said:**
>   Bootup and shutdown is wicked fast.

You can speed up boot and udev events even more [here ]("http://wiki.archlinux.org/index.php/Speedup_boot")and [here.]("http://wiki.archlinux.org/index.php/Speedup_udev") :)

---

### Post by finferflu on 2008-03-11
Hey MisfitI38, nice to see you over here as well :D

---

### Post by MisfitI38 on 2008-03-11
> **finferflu said:**
> Hey MisfitI38, nice to see you over here as well :D

Thanks for the welcome.
Nice to see you too, finferflu. :popcorn:

---

### Post by johnnybirdman on 2008-03-11
> **miggols99 said:**
> You could use my guide, which is much more "newbie" friendly :)

[http://archux.com/page/installation-guide](http://archux.com/page/installation-guide)

Thanks again.  I'm up and running with some input from your site as well as the beginners guide.  I have it up to the point were I'm using fluxbox with startx, sound is working and I have installed firefox. now to install some other stuff, see if I can get wireless working,etc.  
The old laptop is quite snappy as well, more so than with xubuntu which was installed prior.
Thanks again.
J.

> **mips said:**
> It really is not as hard as it is made out to be. It is easier than Gentoo, some bsd's and some other linux distros. If you can follow the wiki then you will be fine.

Btw, it runs like snot on my 1.4ghz celron, 512mb laptop.

you are correct.  I won't use the word 'easy' but I wouldn't call it hard either.  Reading, understanding, failing at times, all part of the learning.  I have an old Dell CpxJ 650 with 512 ram and it is much more responsive with Arch and Fluxbox than it was with xubuntu.  I'm going to try to trim the startup which is currently not very fast, but once in X it runs well.

---

### Post by Gigamo on 2008-03-11
Getting wireless working was a breeze here. Just go to the WICD part of the arch wiki and follow the instructions.

---

### Post by PurposeOfReason on 2008-03-11
> **Gigamo said:**
> Getting wireless working was a breeze here. Just go to the WICD part of the arch wiki and follow the instructions.
That's how I did it though it doesn't like my WEP key no matter what I do.

EDIT - At least it didn't yesterday. Today we're all good. :confused:

---

### Post by Gigamo on 2008-03-11
> **PurposeOfReason said:**
> That's how I did it though it doesn't like my WEP key no matter what I do.

Ah, I'm using WPA2, have not had the chance to have issues with WEP :)

---

### Post by PurposeOfReason on 2008-03-11
> **Gigamo said:**
> Ah, I'm using WPA2, have not had the chance to have issues with WEP :)
Just tried it again and it worked. I swear it just picks days.

---

### Post by andrew.46 on 2008-03-11
Hi:
> **Rumor said:**
> Welcome Illidan! I made the jump from dual booting Arch / Ubuntu to Arch-only in July and have not looked back.

I have the same umbilical cord situation with Slackware / Ubuntu which I dual boot. I am just not quite ready to delete the ubuntu partition :-)

         Andrew

---

### Post by raul_ on 2008-03-11
> **PurposeOfReason said:**
> Just tried it again and it worked. I swear it just picks days.

wireless and furniture are on a conspiracy. I had to get rid of all of my furniture. It just kept staring at me.

---

