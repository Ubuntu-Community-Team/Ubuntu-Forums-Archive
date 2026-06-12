---
title: "Switching?"
date: 2011-04-27
forum: Any Other OS
---

### Post by eldonkr on 2011-04-27
I've been using Ubuntu for almost two years now and I think it's really awesome, but I don't know anything about any of the other Linux operating systems. I've been looking into Fedora recently and I think it's really neat. Plus you can't knock the name, I've always been an aficionado of fancy hats. I'm considering making a switch to Fedora or dual booting just to try it out. Can anyone offer some advice or insight on the matter? Perhaps somebody could highlight the differences between Fedora and Ubuntu, the pros and cons and whatnot?

Thanks in advance.

---

### Post by ventrical on 2011-04-27
Fedora is a smooth, rock solid ride - just like Ubuntu.. but, in my own opinion from observations , Ubuntu has a touch more vesatality when it comes to assistive technologies and also Ubuntu is the master of the USB disk !!IMO.

Also Linux Mint is tops which is an Ubuntu based distro with a flare for elegance and excellence.

Fedora presents a theme of peacfulness and security with smoother graphics edges. I also think it depends on what type of PC is being used. Fedora may very well outperform Ubuntu on faster PCs.

And then there is Knoppix!!! You ought to look into that distro also. You can do things with compiz that seem difficult on other PCs.

Have fun.

---

### Post by eldonkr on 2011-04-28
That's helpful. But what I'm looking for more or less is something like

Ubuntu is different from Fedora in blah blah blah, and Fedora is good for xyz but it can't do yadda yadda yadda like Ubuntu does, but that's ok because Fedora blah blah blah.

What are features I'd find in Fedora that I wouldn't find in Ubuntu? What can Ubuntu do that Fedora doesn't? What issues will I come across using Fedora? etc ect.

---

### Post by Spice Weasel on 2011-04-28
> **eldonkr said:**
> What are features I'd find in Fedora that I wouldn't find in Ubuntu? What can Ubuntu do that Fedora doesn't? What issues will I come across using Fedora? etc ect.

Fedora includes the security tool SELinux instead of Apparmour which is included in Ubuntu. It's harder to configure (but most users don't bother with configuring Apparmor anyway) but far more advanced.

Fedora does its best to stay true to the upstream (and not fiddle around with the source code of applications that it includes) which means it includes a much purer GNOME, KDE, Xfce or KDE desktop. It's also worth mentioning that Fedora has the latest Enlightenment E17 desktop in its repositories, last time I checked Ubuntu only included the much older E16.

Fedora includes nonfree firmware, but does not include any other nonfree software. If you want codecs and/or nonfree graphics drivers then you will need to enable [RPMFusion]("http://rpmfusion.org/"), which is a bit like Ubuntu's restricted extras.

Fedora uses RPM rather than Dpkg for installing stuff. This won't affect most users even if they prefer Dpkg, since you can still install APT and Synaptic and barely tell the difference. I prefer RPM because updating is much faster thanks to DeltaRPMs, which only downloads and installs the differences between two versions rather than completely uninstalling then installing the updated version. It's a pretty heated debate, so I will leave it there.

Fedora includes all of Red Hat's administration and configuration tools (I don't know if Ubuntu does or not?) which are very easy to use and useful. You get the Service Configuration tool, which sets what runs on start up, the Firewall configuration tool, the printing configuration tool, the Users Configuration tool (one of the best I've seen, lots and lots of options).

Fedora includes GNOME Shell instead of Unity (obvious)

Fedora has quick access to hard drive encryption options.

Fedora detects and applies your resolution to the framebuffer so you don't get stretched text on the tty (I have not seen any other distro do this,  but some might.)

Some more obscure and old applications are not included in the repositories. This might be an issue to some, but I've had no problems downloading the .deb package and converting it using alien.

My comparison might not be that good, since I have not used Ubuntu since 9.10.

---

### Post by ventrical on 2011-04-28
Well said. That about summs it up :)

---

### Post by eldonkr on 2011-04-28
Wow, thanks. I'm in the middle of the quarter at the moment so i think i'll wait until after finals before I go fiddling around with things under the hood of my netbook. I'll do more reading on this and if anyone has anything to add, go for it.

One of my textbooks for this quarter came packaged with Fedora Core 6, Is that nifty? Is it the same as the .iso I have recently downloaded for Fedora 14?

---

### Post by Spice Weasel on 2011-04-28
> **eldonkr said:**
> One of my textbooks for this quarter came packaged with Fedora Core 6, Is that nifty? Is it the same as the .iso I have recently downloaded for Fedora 14?

Fedora Core 6 is seriously outdated and unsupported. It's 4 years old.

Fedora 14 is the up to date version.

---

### Post by eldonkr on 2011-04-28
> **Spice Weasel said:**
> Fedora Core 6 is seriously outdated and unsupported. It's 4 years old.

Fedora 14 is the up to date version.

Why didn't I think of that? I never get useful software with my textbooks.

---

### Post by eldonkr on 2011-04-28
I put Fedora 14 on a usb stick and played around with the live emulation for a while. A couple things I noticed is that unlike Ubuntu Fedora doesn't have a software center, or an envelope in the notification panel that lets me launch Empathy or Evolution. Not having a software center isn't a big deal, but the latter is something I've gotten used to having. Is there some kind of equivalent to this in Fedora or will I have to get used to having a seperate icon for chat and mail if I switch to Fedora?

---

### Post by kaldor on 2011-04-29
> **eldonkr said:**
> I put Fedora 14 on a usb stick and played around with the live emulation for a while. A couple things I noticed is that unlike Ubuntu Fedora doesn't have a software center, or an envelope in the notification panel that lets me launch Empathy or Evolution. Not having a software center isn't a big deal, but the latter is something I've gotten used to having. Is there some kind of equivalent to this in Fedora or will I have to get used to having a seperate icon for chat and mail if I switch to Fedora?

Fedora sticks to GNOME basics. Ubuntu adds Canonical's technologies such as the indicator applets you are used to.

---

### Post by manzdagratiano on 2011-04-30
You know what they say - the grass is always greener on the other side.

---

### Post by eldonkr on 2011-04-30
It isn't too big of a deal. I'll try Fedora out sometime down the road after this quarter is over. I don't want to do any kind of operating switch in the middle of a school term. I may like it and decide to stick with it, or I may stick with Ubuntu, I've liked Ubuntu so far I'm just wanting to try something different. You can't say that you're a cake lover if all you've ever had is cake and you've never tried pie or brownies.

---

### Post by eolson on 2011-04-30
Nothing wrong with Fedora if you want to be on the bleeding edge.  It was/is never intended to be a totally stable OS.  It's where Red Hat gets the bugs out (they hope).

---

### Post by manzdagratiano on 2011-04-30
> **eldonkr said:**
> It isn't too big of a deal. I'll try Fedora out sometime down the road after this quarter is over. I don't want to do any kind of operating switch in the middle of a school term. I may like it and decide to stick with it, or I may stick with Ubuntu, I've liked Ubuntu so far I'm just wanting to try something different. You can't say that you're a cake lover if all you've ever had is cake and you've never tried pie or brownies.

Yup! Totally agree... You should certainly experience Fedora for yourselves. I just never got around to liking it - I use it on my work machine every day since that's what the sysadmin has on all the systems there, so I guess it is not my kind of pie. For me, if ease and pizzaz were the factors, Ubuntu has them all. Then there are other distros which embody simplicity and excellence as well - Arch, Debian, Slackware, Gentoo... :P

---

### Post by eldonkr on 2011-04-30
> **eolson said:**
> It was/is never intended to be a totally stable OS.

I'm not comfortable with stable or buggy. In fact I usually stay a release behind whatever the newest release for Ubuntu is just to in an attempt to avoid a lot of bugs.

And what's this with bleeding edge? I'm not too hip to the jive with all of these newfangled technojaron slang terms.

---

### Post by wojox on 2011-05-01
> **eldonkr said:**
> I'm not comfortable with stable or buggy. In fact I usually stay a release behind whatever the newest release for Ubuntu is just to in an attempt to avoid a lot of bugs.

And what's this with bleeding edge? I'm not too hip to the jive with all of these newfangled technojaron slang terms.

[Fedora myths]("http://fedoraproject.org/wiki/FedoraMyths")

I've been using Fedora on one partition for a year. It's really just an unpolished Ubuntu with a different package manager. The forums are just as great as these.

---

### Post by eldonkr on 2011-05-01
I'm liking Fedora the more I read about it. When I was checking out the Fedora site and downloading the ISO I also checked out the spins and downloaded the Security spin. What I'm wondering, since I haven't booted the live emulation of the spin yet, is how different the security spin is from regular Fedora?

---

