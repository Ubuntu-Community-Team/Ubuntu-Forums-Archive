---
title: "Ubuntu to Debian question"
date: 2011-06-10
forum: Any Other OS
---

### Post by Zlatan on 2011-06-10
Hello team, a copy-paste from my post in Things that you hate in Ubuntu:
[I]I hate branding and some default stuff in Ubuntu thatI do not use- it is Ubuntu One, Chat/Mail/Broadcast menu in indicators and some more.
Would love to use something like Debian, but there's what I love in Ubuntu better than in Debian- new apps versions, more frequent updates, easy restricted packages management and additional/proprietary drivers management. Other than that I would choose Debian.[/I]
Do you have any idea how it would be easier to de-brand Ubuntu to have purier Debian-ish distro or how to have more up-to-date Debian with easy managable proprietary drivers (particularly Broadcom Wifi) and restricted-etras (like Java, Flash, mp3, etc.)?
Thank you so much for your valuable ideas;)

---

### Post by Thewhistlingwind on 2011-06-10
Go use mint.

---

### Post by cariboo on 2011-06-10
Do a cli install using the [mini iso]("https://help.ubuntu.com/community/Installation/MinimalCD") then install the [gnome]("http://packages.ubuntu.com/natty/gnome") meta package for a gnome desktop environment

---

### Post by Paqman on 2011-06-10
> **cariboo907 said:**
> Do a cli install using the [mini iso]("https://help.ubuntu.com/community/Installation/MinimalCD") then install the [gnome]("http://packages.ubuntu.com/natty/gnome") meta package for a gnome desktop environment

This. Installing the package jockey-gtk will give you the Additional Drivers tool from Ubuntu.

---

### Post by Zlatan on 2011-06-10
> **Paqman said:**
> This. Installing the package jockey-gtk will give you the Additional Drivers tool from Ubuntu.

And what about restricted-extras? Will I get them here? Thanks

---

### Post by Paqman on 2011-06-10
> **Zlatan said:**
> And what about restricted-extras? Will I get them here? Thanks

Sure. Since you'd still be using the Ubuntu repos you could install any package you wanted.

---

### Post by NightwishFan on 2011-06-10
Debian is not hard to use.

---

### Post by Zlatan on 2011-06-10
> **NightwishFan said:**
> Debian is not hard to use.

Yes, instead that stable is not up-to-date and does not have restricted-extras installation goodness? Or these are fairly easy to achieve?
BTW, does Debian testing get all (incl security) updates? I've read that security updates are not included there but can not be sure about how serious that source was...
Thank you

---

### Post by IWantFroyo on 2011-06-10
> **Thewhistlingwind said:**
> Go use mint.

Mint doesn't have as much branding, but what they do have is even more annoying. 

They have that horrible Mint Search thing, which caused me to leave.

I've used Debian. It isn't as up to date in its software as Ubuntu, but it is pretty good.

---

### Post by Zlatan on 2011-06-10
> **IWantFroyo said:**
> Mint doesn't have as much branding, but what they do have is even more annoying. 

They have that horrible Mint Search thing, which caused me to leave.

I've used Debian. It isn't as up to date in its software as Ubuntu, but it is pretty good.

love your sig mate:) no windows here for years...

---

### Post by JustinR on 2011-06-10
Hi,

Everything mentioned above is completely removable without consequence on Ubuntu - almost all of it has it's own package.

```

sudo apt-get purge ubuntuone-client indicator-messages

```

Ubuntu One has a few dependencies you would need to remove after that.
Branding is pretty much a fixable cosmetic issue.

---

### Post by Zlatan on 2011-06-10
> **JustinR said:**
> Hi,

Everything mentioned above is completely removable without consequence on Ubuntu - almost all of it has it's own package.

```

sudo apt-get purge ubuntuone-client indicator-messages

```

Ubuntu One has a few dependencies you would need to remove after that.
Branding is pretty much a fixable cosmetic issue.

Hi Justin, thanks for your reply but as far as I'm not into computer design loooks like my choice looks closer to Debian rather than doing cosmetic changes to Ubuntu defaults;)

---

### Post by odiseo77 on 2011-06-10
Debian Testing has a security repository, and IMO it's not so outdated, (maybe not bleeding edge, but not outdated, either). And there's always Debian Sid, if you want a bleeding edge experience (honestly, I don't find a huge difference between them when it comes to package versions). If you use Sid, just remember to check what you upgrade, and what is being removed when you upgrade some packages.

---

### Post by Zlatan on 2011-06-10
> **odiseo77 said:**
> Debian Testing has a security repository, and IMO it's not so outdated, (maybe not bleeding edge, but not outdated, either). And there's always Debian Sid, if you want a bleeding edge experience (honestly, I don't find a huge difference between them when it comes to package versions). If you use Sid, just remember to check what you upgrade, and what is being removed when you upgrade some packages.

What's the best in balance in up-to-date and stability/security in your opinion? Stable/Testing or Unstable? Thanks

---

### Post by ivanovnegro on 2011-06-10
> **Zlatan said:**
> Hello team, a copy-paste from my post in Things that you hate in Ubuntu:
[I]I hate branding and some default stuff in Ubuntu thatI do not use- it is Ubuntu One, Chat/Mail/Broadcast menu in indicators and some more.
Would love to use something like Debian, but there's what I love in Ubuntu better than in Debian- new apps versions, more frequent updates, easy restricted packages management and additional/proprietary drivers management. Other than that I would choose Debian.[/I]
Do you have any idea how it would be easier to de-brand Ubuntu to have purier Debian-ish distro or how to have more up-to-date Debian with easy managable proprietary drivers (particularly Broadcom Wifi) and restricted-etras (like Java, Flash, mp3, etc.)?
Thank you so much for your valuable ideas;)

Of course you could try some other Debian derivatives with codecs and firmware enabled by default, just google a bit, there is an amount.
As mentioned Mint here, you could of course try Linux Mint Debian Edition with more recent apps, as it is a rolling distro based on Debian Testing.

> **Zlatan said:**
> Yes, instead that stable is not up-to-date and does not have restricted-extras installation goodness? Or these are fairly easy to achieve?
BTW, does Debian testing get all (incl security) updates? I've read that security updates are not included there but can not be sure about how serious that source was...
Thank you

Here some read on [Debian Testing]("http://www.debian.org/releases/testing/"). I would also suggest to read their Wiki and documentation. Debian is a powerful distro.

> **IWantFroyo said:**
> Mint doesn't have as much branding, but what they do have is even more annoying. 

They have that horrible Mint Search thing, which caused me to leave.

I've used Debian. It isn't as up to date in its software as Ubuntu, but it is pretty good.

Debian is indeed so stable and a really good distro even if the newer apps are not included. Debian will give you a full overall consistency and a high quality stability, dont know how better to describe it.

I have to admit that I begun to use Debian as my primary work station, I would never expect that to happen, I simply tried it and was shocked how good it is.
PS: To use newer stuff there is also the art of Apt Pinning.
When you go the standard Debian way to use only the stable repo, it is as user friendly as Ubuntu, if you want newer stuff you can of course compile, use other Debian repos, use Testing/Sid, Apt Pinning... there are so many possibilities and there you can see that Debian is a versatile distro also for experienced Linux users.

You can also install #! (CrunchBang Linux), it comes with firmware and proprietary stuff enabled, but it uses Openbox or Xfce.

---

### Post by ivanovnegro on 2011-06-10
> **odiseo77 said:**
> debian testing has a security repository, and imo it's not so outdated, (maybe not bleeding edge, but not outdated, either). And there's always debian sid, if you want a bleeding edge experience (honestly, i don't find a huge difference between them when it comes to package versions). If you use sid, just remember to check what you upgrade, and what is being removed when you upgrade some packages.

+1

---

### Post by Zlatan on 2011-06-10
A note for discussion- it is on Debian and Ubuntu, no Mints, Gentoos, etc on interest for the moment, sorry. Gnome is a preference for the moment as well, thanks;)

---

### Post by Zlatan on 2011-06-10
> **odiseo77 said:**
> Debian Testing has a security repository, and IMO it's not so outdated, (maybe not bleeding edge, but not outdated, either). And there's always Debian Sid, if you want a bleeding edge experience (honestly, I don't find a huge difference between them when it comes to package versions). If you use Sid, just remember to check what you upgrade, and what is being removed when you upgrade some packages.

looks like there's a bit of difference in hassle-free ubuntu-ish branded codec and driver install and debian-ish doit your-self... kinda mindset change requirement?;)

---

### Post by krapp on 2011-06-10
> **Zlatan said:**
> Yes, instead that stable is not up-to-date and does not have restricted-extras installation goodness? Or these are fairly easy to achieve?


On Mint you don't even have to install something like "restricted-extras." On Debian you install "flashplugin-nonfree" and add debian-multimedia.org to your /etc/apt/sources.list and then update APT. Either way it's just as uncomplicated as Ubuntu.

I find the "Debian is old" argument to be overstated. What sort of applications would you need? It's easy enough to get the latest Firefox, for instance.

---

### Post by ivanovnegro on 2011-06-10
> **Zlatan said:**
> What's the best in balance in up-to-date and stability/security in your opinion? Stable/Testing or Unstable? Thanks

Stable has always security updates but will be very out of date with the apps, imagine you are using the Ubuntu LTS version. Now here comes the good thing, PPAs for Ubuntu; Backports for Debian Stable.

Testing has newer stuff but is less stable in the sense of the Debian philosophy, nobody is saying it is unusable, in fact it is very usable without problems, but things *could* break, you have to control your update behavior not just put the button. Security updates are slower.

Unstable/Sid, is also usable, but it is unstable, constantly changing and with more breakages, its bleeding edge. Even though people can use it without problems.

I would you suggest to first try Stable, at the moment it is not as outdated. If you feel comfortable you could change your sources list to Testing, Sid is really more if you have the experience with Debian and the ability to fix things sometimes.

---

### Post by odiseo77 on 2011-06-10
> **Zlatan said:**
> What's the best in balance in up-to-date and stability/security in your opinion? Stable/Testing or Unstable? Thanks

I would say, in case you will use this system as a desktop, then the best balance between up-to-date and stability/security, is offered by Debian Testing; it has up-to-date packages, but most of them have passed through some minimal testing. In the 4 years I've been using Debian Testing, I've only had one serious breakage once when the system didn't boot (like 3 years ago), but that is rare. The only inconvenience of running *Testing* is that sometimes some packages may last a bit long to get upgrades, and in case of some program with some bug, or a program with a new feature you're expecting, it can get annoying, but the plus side is that *Testing* is flexible enough so that you can install stuff from *Unstable*, or even from the *Experimental* repository, in case this happens (of course, taking a special care of posible removals of programs installed on your system).

---

### Post by ivanovnegro on 2011-06-10
> **odiseo77 said:**
> I would say, in case you will use this system as a desktop, then the best balance between up-to-date and stability/security, is offered by Debian Testing; it has up-to-date packages, but most of them have passed through some minimal testing. In the 4 years I've been using Debian Testing, I've only had one serious breakage once when the system didn't boot (like 3 years ago), but that is rare. The only inconvenience of running *Testing* is that sometimes some packages may last a bit long to get upgrades, and in case of some program with some bug, or a program with a new feature you're expecting, it can get annoying, but the plus side is that *Testing* is flexible enough so that you can install stuff from *Unstable*, or even from the *Experimental* repository, in case this happens (of course, taking a special care of posible removals of programs installed on your system).

That is the good description for it, I would also suggest Testing if you want updated apps and security updates as the balance of stable and new stuff.

---

### Post by NightwishFan on 2011-06-10
Use stable and stay tuned to the backports service for some newer stuff. A working system beats a new one any day. What is the advantage of simply being new?

---

### Post by odiseo77 on 2011-06-10
> **NightwishFan said:**
> Use stable and stay tuned to the backports service for some newer stuff. A working system beats a new one any day. What is the advantage of simply being new?

I haven't used Stable+Backports myself, but I've read good things about it, so for more stability it may be advisable, I guess.

---

### Post by Zlatan on 2011-06-11
one more question here (did not have time to google this seriously yet)- is there any chance to use gnome-shell on debian? probably this should not work on stable? thank you

---

### Post by PhilGil on 2011-06-11
> **Zlatan said:**
> one more question here (did not have time to google this seriously yet)- is there any chance to use gnome-shell on debian? probably this should not work on stable? thank you
It's very unlikely that Gnome 3 will ever be available for the current stable Debian release (either through backports or a 3rd party repository). It's far too big a change to a core system component.

Gnome 3 will likely hit Debian sometime in the current development cycle and be the default DE in the next stable release. However, it is not yet available in any of the Debian distributions: [http://packages.debian.org/search?keywords=gnome&searchon=names&suite=all&section=all](http://packages.debian.org/search?keywords=gnome&searchon=names&suite=all&section=all) .

---

### Post by Zlatan on 2011-06-11
> **PhilGil said:**
> It's very unlikely that Gnome 3 will ever be available for the current stable Debian release (either through backports or a 3rd party repository). It's far too big a change to a core system component.

Gnome 3 will likely hit Debian sometime in the current development cycle and be the default DE in the next stable release. However, it is not yet available in any of the Debian distributions: [http://packages.debian.org/search?keywords=gnome&searchon=names&suite=all&section=all](http://packages.debian.org/search?keywords=gnome&searchon=names&suite=all&section=all) .

found t[http://wiki.debian.org/GnomeShell]("http://wiki.debian.org/GnomeShell")his recently, they say gnome-shell is available. anyone has tried this method?

---

### Post by el_koraco on 2011-06-11
> **Zlatan said:**
> found t[http://wiki.debian.org/GnomeShell]("http://wiki.debian.org/GnomeShell")his recently, they say gnome-shell is available. anyone has tried this method?

That's the old iteration of Gnome Shell, from October last year or something. What you can do is manually compile Gnome Shell on Gnome 2 with Debian.

---

