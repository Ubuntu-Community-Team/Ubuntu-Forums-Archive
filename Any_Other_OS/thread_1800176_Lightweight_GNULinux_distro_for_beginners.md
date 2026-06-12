---
title: "Lightweight GNU/Linux distro for beginners?"
date: 2011-07-08
forum: Any Other OS
---

### Post by shobon on 2011-07-08
My dad recently got a old laptop for work (which he only really needs for email and web browsing and such), and Windows runs poorly on his currently laptop (with better specs) and I'd like to put GNU/Linux on it for him.

His only problem is that he "would have no idea how it works," so I need a lightweight distro (that would run relatively smooth with 256mb of RAM) that is user-friendly and would require little to no terminal usage (graphical update/package manager installed, easy to use DE/WM).

The laptop is a Toshiba Satellite A65-S126, 256mb RAM, 2.8GHz, 60mb HDD.

Thank you!

---

### Post by johnnybgoode83 on 2011-07-08
I would say xubuntu is your best bet.  It is part of the Ubuntu family and it ships with the lightweight xfce DE which has been described as Gnome Lite.

---

### Post by ojdon on 2011-07-08
If you spend a bit of time optimizing/speeding up/removing unneeded files then you could try giving Linux Mint LXDE a go. It's a nice mix of Linux Mint's user friendliness as well as using LXDE! The layout is somewhat similar to Windows, which I'm guessing that's what he is using at the minute. If it doesn't work great on 256MB of RAM then I suggest giving Puppy Linux a go, never tried it myself but I know it's extremely lightweight. Your best bet is to upgrade the RAM to 512MB at least. Then anything should run relatively well on that machine.

---

### Post by nmaster on 2011-07-08
with 256MB RAM, xubuntu might not be best.  i'd suggest lubuntu if you really want to stay with ?ubuntu.

if he really only needs some web applications, think about web-centric options like Joli. according to this link, you might not have enough ram, but you could give it a shot.
[http://help.jolicloud.com/entries/229205-will-joli-os-work-on-my-machine](http://help.jolicloud.com/entries/229205-will-joli-os-work-on-my-machine)

---

### Post by shobon on 2011-07-08
I'd prefer to stay with a distro that uses apt/dpkg, since that's what I know best. I'd install Arch but that'd be less user-friendly if Arch happens to break and I'm not around to fix it for him, not to mention I want to stay away from bleeding-edge and rolling releases.

Would a minimal Debian installation with LXDE or XFCE run smoothly on 256mb of RAM?

---

### Post by ojdon on 2011-07-08
Debian w/ LXDE would be your best option over XFCE.

---

### Post by wolfen69 on 2011-07-08
> **johnnybgoode83 said:**
> I would say xubuntu is your best bet.

Xubuntu will be slow on 256. I think mint makes an lxde version which might be better. Antix mepis is also a good choice, as it is made for older computers and is ready to go with codecs and such. If you try mepis, get the i386 version.

---

### Post by nmaster on 2011-07-08
> **ojdon said:**
> Debian w/ LXDE would be your best option over XFCE.

i had debian + lxde flying on a P2 machine with 128MB ram.  it was great ;)

however, you originally mentioned the need for GUI applications.  you'll need to install these yourself.  keep in mind that some ubuntu apps (like software center) won't be in the debian repos.

---

### Post by nmaster on 2011-07-08
> **shobon said:**
> I'd prefer to stay with a distro that uses apt/dpkg, since that's what I know best. 

joli is based on ubuntu so that shouldn't be the reason to not use joli.  there are probably other reasons though, lol

---

### Post by life in color on 2011-07-08
I suggest Debian!! After all it's what Ubuntu is based off of.

---

### Post by shobon on 2011-07-08
> **nmaster said:**
> i had debian + lxde flying on a P2 machine with 128MB ram.  it was great ;)

however, you originally mentioned the need for GUI applications.  you'll need to install these yourself.  keep in mind that some ubuntu apps (like software center) won't be in the debian repos.

Haha that's good to hear! And I know, I've done "from the ground up" Debian installs before, so it's all good :)

As for Joli, I'm not really the biggest fan of cloud computing and doing everything from the net. I ran Jolicloud on my netbook for a while, but in places where I wasn't online rendered my netbook somewhat useless...

---

### Post by Bart_D on 2011-07-08
> **shobon said:**
> ......
The laptop is a Toshiba Satellite A65-S126, 256mb RAM, 2.8GHz, 60mb HDD.

...

Have you thought about Ubuntu Minimal + LXDE or Openbox?

---

### Post by krapp on 2011-07-08
> **nmaster said:**
> i had debian + lxde flying on a P2 machine with 128MB ram.  it was great ;)

however, you originally mentioned the need for GUI applications.  you'll need to install these yourself.  keep in mind that some ubuntu apps (like software center) won't be in the debian repos.

Actually Software Center is believe it or not!

---

### Post by handy on 2011-07-09
Where are you fewt?
________

I think Fuduntu would very likely be ideal. It is designed to go light on resources, even so it is a very full featured distro.

[http://www.fuduntu.org/](http://www.fuduntu.org/)

---

### Post by shobon on 2011-07-09
> **handy said:**
> Where are you fewt?
________

I think Fuduntu would very likely be ideal. It is designed to go light on resources, even so it is a very full featured distro.

[http://www.fuduntu.org/](http://www.fuduntu.org/)

No offense to fewt or anyone who works on or uses Fuduntu, but I'd prefer something that's been out for a while and has a larger following for easier support, for the sake of my dad.

---

### Post by mips on 2011-07-09
> **shobon said:**
> 
The laptop is a Toshiba Satellite A65-S126, 256mb RAM, 2.8GHz, 60mb HDD.


The best thing you can do is install a 1GB DDR1 SODIMM (PC2700) module in that laptop to bring it upt to 1.25GB. That runs even WinXP fine.

A new module can be had for US$30 and second hand via ebay etc probably much cheaper.

After this Xubuntu or Lubuntu will run fine.

---

### Post by fuduntu on 2011-07-09
> **shobon said:**
> No offense to fewt or anyone who works on or uses Fuduntu, but I'd prefer something that's been out for a while and has a larger following for easier support, for the sake of my dad.

We've kept things moving forward for almost 9 months now, and have a pretty good support response in the forum.  No worries though, use whatever works best.

---

### Post by Megaptera on 2011-07-09
> **shobon said:**
> My dad recently got a old laptop for work (which he only really needs for email and web browsing and such), and Windows runs poorly on his currently laptop (with better specs) and I'd like to put GNU/Linux on it for him.

His only problem is that he "would have no idea how it works," so I need a lightweight distro (that would run relatively smooth with 256mb of RAM) that is user-friendly and would require little to no terminal usage (graphical update/package manager installed, easy to use DE/WM).

The laptop is a Toshiba Satellite A65-S126, 256mb RAM, 2.8GHz, 60mb HDD.

Thank you!

Have you considered Peppermint? [http://peppermintos.com/](http://peppermintos.com/) "The absolute minimum required specs are as follows:

    * 192 MB of RAM
    * Processor based on Intel x86 architecture
    * At least 2 GB of available disk space"

You say 60mb HDD? A Typo?!

---

### Post by nmaster on 2011-07-11
> **krapp said:**
> Actually Software Center is believe it or not!
good to know! i guess its been a while since i've used debian ;)

shobon, since you're comfortable with using the debian net-inst and then adding lxde, that sounds like the best option. if you can add the software center for your father, it should be great for him and (as you know) it'll fly :)

---

### Post by XubuRoxMySox on 2011-07-12
I'll add my "vote" for AntiX on such a very modest machine! It's ultralight, easy for beginners, and is much less "cloud dependent" than the newest lightweight distros. It's part of the Mepis family, and support for it in both MepisLovers forums and their own AntiX forums is very good.

That said, though, I really would add some RAM to that old dinosaur, because: 

[LIST]
[*]Even the lightest-weight Linux will run better and faster with more RAM, and:

[*]Adding some RAM also adds to your distro choices!
[/LIST] 

I find Xfce to be super-easy to use and kid-friendly, which *also* makes it parent and grandparent friendly. I used LXDE on a minimal Ubuntu installation and it brought new life (and mind-bending speed) to an ancient old 256 K machine at the dance studio. LXDE "looks like Windows 98" according to alot of folks who used it on that machine. Verrrrry lightweight and fast on minimal Ubuntu! 

But it's not as much a matter of the desktop environment as it is the *applications* you use! Since applications "work best" in their "native environments," and since there aren't any native LXDE applications (other than PCManFM which is awesome, and LXMusic which was buggy when I was experimenting with it), I tend to favor Xfce-based stuff.

Hope that helps a little,
Robin

---

### Post by BrokenKingpin on 2011-07-12
Xubuntu, but if you need it to be even lighter, Lubuntu (although it is not as easy to use as Xubuntu).

---

### Post by wacky_sung on 2011-07-12
How about [Damn small Linux]("http://www.damnsmalllinux.org/")?

---

### Post by snowpine on 2011-07-12
> **wacky_sung said:**
> How about [Damn small Linux]("http://www.damnsmalllinux.org/")?

Outdated and unsupported. I do not recommend.

---

### Post by BrokenKingpin on 2011-07-14
> **snowpine said:**
> Outdated and unsupported. I do not recommend.
I agree, DSL hasn't been under active development for quite some time.

---

### Post by Megaptera on 2011-07-16
I'm impressed with Mac Pup, sleek but most important (to me) it found my wireless and connected out of the box.

[http://macpup.org/](http://macpup.org/)

---

### Post by xxxlam on 2011-07-16
Puppy Linux. Only 128 MB. Well, according to my experience, it supports more devices than Ubuntu. AND you can use it by just installing to your Flash Drive. =)

---

### Post by mips on 2011-07-16
People, I think the OP did a hit & run...

---

### Post by XubuRoxMySox on 2011-07-16
Heard alot of good stuff about Vector Linux - ultralight, yet up-to-date apps, including Firefox! Idles at under 80 mgs of RAM!

-Robin

---

