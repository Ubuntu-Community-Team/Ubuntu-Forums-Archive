---
title: "Trisquel"
date: 2013-02-12
forum: Any Other OS
---

### Post by MyTinFoilHat on 2013-02-12
I'm wondering if anyone in the forums uses Trisquel. I have questions.

I've been checking out the livecd of Brigantia (5.5) and I mostly like what I see - especially because it seems to fit my particular needs. I happen to be one of those people that doesn't like or trust the idea of proprietary software; nor am I a fan of auto-opt-in services (like the ones Ubuntu has been pushing of late) - even if they claim they use 'anonymous data' or can be turned off. I want a distro that obeys me, not betrays me.  ...Which is what eventually led me to Trisquel – well, that and the familiar apt package management I've become accustomed to.

I'm mentioning all this because I feel mostly confident that Trisquel meets these needs and my experience will be based upon how well it fulfills those needs. My requirements are simple: honesty, integrity, safety, and respect in design and practice, in implementation and execution; absolute respect and adherence to user control, security. 

For the time being, I plan to dual boot my machine: Ubuntu and Trisquel. I'm newbie-enough that I have a need for a crutch, I'm not just being hypocritical.  ;)

Which brings me to my questions:

Does Trisquel support dual-boot? When I click "Install" will it give me that option? I'm guessing 'yes', but would like confirmation.

My current Ubuntu install is encrypted, will this be an issue?

Drivers. I think one of the few things holding me back at this point are drivers. Frankly, I'm a little nervous about having to seek out open source drivers for my machine. Does Trisquel install seek these out the open equivalents for me, or is this something I need to source and bring to the party myself?

If I dual boot my machine (as mentioned above), could there be a potential for losing the drivers that function on the Ubuntu side when I switch over to use Ubuntu - or vice-versa, or am I just clueless about how that works? (Hey, I told you earlier I'm a newbie. You were warned.)

I realize that 6.0 Toutatis is right around the corner. I've only experienced 1 distro version upgrade - and that was on Ubuntu - to Quantal. Would Trisquel function in the same way? Should I just hold off, try a livecd of 6.0 instead? What's your opinion?

What are the available software resources like? How reliable is the software?

I have to admit, I've tried Debian and I love how everything seems to have properties that can be changed. (Click the title bar/notification area/launcher (dash)/whatever). I'm probably not using the right terminology. Whatever. Debian seemed very flexible. I noticed (again, via livecd) that Trisquel seems to be a little thin on these sorts of "make it pretty my way" features - or is that only a livecd limitation?

If you use or have used Trisquel, what has your experience been like? What were the pros and cons?

Lastly (See? I told you I had questions!), are there good, reliable community forums that I can check out before I take another step forward (i.e., like where we are right now, but for Trisquel)?

Thanks for your time, patience, and answers. I appreciate it!

---

### Post by JiuJitsu500 on 2013-02-12
Dual boot is not going to be a problem. I don't use Trisquel, but I do have like 30 distros for BSD and Linux in virtual machines, so you just gave me a new one to try out.

Now, GRUB supports booting any number of machines, I have quint-booted before Mac, Ubuntu, Windows XP, Windows 7, and PC-BSD.

Trisquel apparently uses GRUB as it's bootloader, so after you partition and install it, GRUB will see ubuntu as well as trisquel so you'll be able to freely boot into either one you want.

I'm looking at Bodhi for the same reasons you're looking at trisquel by the way. I'm NOT digging canonical's direction with the whole auto-opt-in CRAP, and I like debian-based distros... check Bodhi out man, I like it. I'll give Trisquel a try for sure too.

EDIT*** Your second question... no, you won't lose any drivers. since it's a debian-based distro, trisquel would require similar, of not outright the same drivers. debian packages work on nearly all debain-based distros (or even converted .rpm or pacman, etc... the only universal linux package is a tarball), so you should be more than okay. I'd imagine trisquel has it's own method for finding the drivers you need to. As long as you have Nvidia, you'll be MUCH better off than having ATI, linux support for thos cards freakin suck compared to NVidia. Integrated graphics, wifi, ethernet, etc should all work fine - linux has come a LONG way and works almost always fresh out of the box with most distros now.

As for the forum, I'm not so sure man. Fedora, Ubuntu, Debain, Arch, Slackware, etc. have excellent support because of how big the distros are. BUT... being debian-based, you'll probably be fine in any of the major forums off-distro talks. Just mention what you're on. I've never heard of trisquel, but distros are pretty similar. Now, if you'll allow, I'm off to download trisquel. :)

---

### Post by zombifier25 on 2013-02-12
Most of your questions have been answered by jiujitsu, so I won't add anything here. But there will be some drawbacks in using it.

I disagree that drivers will not be a problem in Trisquel. Drivers support will be a huge problem in Trisquel. You will have no problem with some, because the 
Linux kernel has come a long way and now supports a very wide range of devices. But because Trisquel follows a very strict policy of free software only, and thus all binary blobs from the kernel is cleaned and proprietary drivers are not allowed, so support for certain devices, especially wireless and video cards, will be impaired, or there will be no support at all.

(Also, say goodbye to Flash, since it's proprietary. And Gnash, the replacement, is nowhere as good)

Personally, I feel that Trisquel is a niche distro aimed at a niche market (e.g. FSF purists, ..) but there's no harm trying it out. But if I want a functional distro, I would use Ubuntu.

---

### Post by JiuJitsu500 on 2013-02-13
Wow, so check it..... I came back from a quick commercial break and downloaded trisquel while reading their FAQ and checking out some documentation....

I don't think I'll like this one very much, zombie just pointed out some things I didn't know, like having strict adherence to the FSF ordeal and being pretty much stuck to the GNU/Linux name instead just Linux (FSF and Stallman's staple argument)... which automatically makes me think that nothing proprietary (broadcom drivers, NVidia drivers, etc) would be available.

Though ubuntu-based, this alone limits the things you can get/do dramatically. Open-Source or Free alternatives are, like zombie said, NOWHERE close often times to free proprietary software (his example of flash is 100% dead-on).

Good luck with trisquel man, I'm not diggin the idea. Still going to virtualbox it though just to not waste my download.

**EDIT** Oh, you don't have to give up Ubuntu in general, btw.... the other versions of it (gnome-shell remix, kubuntu, xubuntu, lubuntu, cinnamon remix, MATE mix), or other ubuntu based distros don't have the damn options a standard install does.... I like the gnome-remix, or xfce... just saying :)

---

### Post by iamkuriouspurpleoranj on 2013-02-13
Just tried Trisquel 6.0 pre-release (based on Precise - not sure if alpha or beta. RC quality). I liked it very much. Unfortunately, I need the proprietary graphics driver to make my PC operate with a bearable noise level and you cannot install it on Trisquel. I suppose you could hack it but then why would you bother?

A few things it has:

An attractive and proper albeit conservative Gnome-Panel theme (i.e. Gnome 3 fallback)
NetBeans, Eclipse, and VirtualBox in the repos.
LibreOffice 3.5
Gimp... 2.6 (like Precise)
Tasksel with GLAMP (GNU/Linux Apache MySQL PHP)

However, you're pretty much stuck with that DE. A version of the distro for old hardware called Trisquel Light (LXDE) is available but I couldn't find the LXDE package in the software-center,  so maybe the two are separate. No Xfce, no KDE and no Gnome Shell. No Openbox for some reason. I guess it's not 100% free.

Seems perfectly usable and I would run it for a couple of weeks if it was quieter on my PC.

---

### Post by iamkuriouspurpleoranj on 2013-02-13
> **MyTinFoilHat said:**
> I realize that 6.0 Toutatis is right around the corner. I've only experienced 1 distro version upgrade - and that was on Ubuntu - to Quantal. Would Trisquel function in the same way? Should I just hold off, try a livecd of 6.0 instead? What's your opinion?
 
...

Debian seemed very flexible. I noticed (again, via livecd) that Trisquel seems to be a little thin on these sorts of "make it pretty my way" features - or is that only a livecd limitation?


Go straight for 6.0. It seems stable enough to me (as of today). As it should, since Trisquel developers essentially only weed out the non-free stuff from Ubuntu. That's not to belittle their work - it's just their primary development activity.

Re flexibility: Indeed, it seems like Unity in the sense that it's great if you like the theme but if you don't there's not a lot you can do to change things. It has the gnome tweak tool and will apparently support other themes but Gnome-Panel (Gnome 3 fallback) is really quite inflexible.

I could really see someone with the right hardware and a commitment to the FSF's principles getting a lot of enjoyment out of this.

---

### Post by Lemuriano on 2013-02-14
If you need to use another DE like xfce or any other that is in the Ubuntu repositories just go to the CLI and type:

```
sudo apt-get install xfce4
```Or go to synaptic package manager. Trisquel is indeed 100% free  

When you buy hardware that is freedom friendly, everything would work including wifi and 3D acceleration. 

Some PC manufactures like Toshiba for example use a DRM feature to prevent the owner of a laptop from changing the mini-pci wifi card with a different model or brand. 

I want my system (software & hardware) to work for me and to be able to simply choose what I want do with it. Why been subjugated to the will of xyz company is better? Reverse engineering is not the solution but supporting freedom friendly hardware is, so demand is increase and therefor the offer will materialize in a more popular way.   

Regardless of the distro, I prefer not to use proprietary hardware and/or software like Nvidia or Intel wifi cards, because they don´t care about Linux (or I should said Gnu/Linux) and that´s why the support that we receive from then is 0. Remember the video of Linus Torvalds regarding Nvidia.

[http://www.youtube.com/watch?v=IVpOyKCNZYw](http://www.youtube.com/watch?v=IVpOyKCNZYw) 

In my humble opinion is not ethically correct or good business to support a legal entity that in turn it does 0 for us.   

There are companies that sell PC´s that are freedom friendly and would work with any distro and one that I know is

 [http://libre.thinkpenguin.com](http://libre.thinkpenguin.com) 

When I left Windows for Ubuntu, there where certain software and hardware that was design specifically for Windows and would not work, but Ubuntu prevail because I feel that I had more control over it. Then I learn the difference between open source and free software and as it happen with Ubuntu before, I have no choice but to embrace it. 

Trisquel besides been and excellent ambassador is essay to use.

Regards

PS. Finally I haven been using Trisquel Brigantia-Xfce for almost a year as my main OS and besides been and educational experience, I enjoy every minute of it. :D

---

### Post by iamkuriouspurpleoranj on 2013-02-15
It's true. I tested it out and you can indeed install Xfce - and presumably the others - from synaptic package manager or the command line. It's just not listed in what looks like the Gnome software installer (whatever that's called).

---

### Post by iamkuriouspurpleoranj on 2013-02-15
^^ Preinstalled Trisquel: that's great !

---

### Post by JiuJitsu500 on 2013-02-16
@ Lemuriano

Hold on... I don't think there are many setups at all that are strictly Free-Friendly, but if I'm wrong then I won't disagree. Find me a laptop you can't build yourself though with all FSF compliance. HP, ASUS, Acer, Dell, a TON of companies who make mostly dig Linux and the idea of open-source... but dude... get real to think any decent and commonly found laptop is ALL FSF or open friendly. Still won't argue if you're right. BUT, I will disagree that you have to be out of your mind in the graphics department.

Do you really think noveau or flgrx are even CLOSE to proprietary?

NVidia and ATI are all you have. Integrated graphics with both AMD and Intel are not even an argument, period. Both are well supported, yada yada.

NVidia and ATI BOTH offer their OWN drivers, available from the manufacturer and the repos of many distros (as they come in tarballs, virtually any distro can install them, use them, keep updated, etc). And I mean that. Fedora and all the .rpm guys, arch and the pacman guys, debian and all the .deb guys, keep going... gentoo, slackware, dragora, name it... they ALL have ATI and NVidia support FROM the manufacturer... and if not, they are based on a package manager who has a developer who DOES make the drivers (even if they are not of as-high quality...

So, then you ask why that's necessary... well, because I buillt this damn computer or bought it as-is. So, when I look for a distro that supports it all, most of which works out-of-box, I want to know the manufacturer supports my distro (at least the manager. You can get Fedora to function as well as Ubuntu or Slax or Arch with drivers FROM the manufacterer... so why go with the whole Free Software thing? They make the devices, so their drivers should be better than the open-source ones, right? Not in all cases, granted. They are STILL open, anyone can change it.

Besides, no one plays Battlefield 3 or Skyrim with 50 mods - let alone anything newer (Crysis 3, Dead Space 3... anything coming out, etc)... There is literally nothing else requiring perfect drivers. My NVidia 550M (i think) works like a boss with compiz and games like MW2 or 3, or Age of Empires, and I run Photshop and Autocad (any edition) like a champ. Not to mention having 6 virtual machines at once eating (as in destroying) my CPU, yet still not doing a lot of damage to my GPU. That's WITH the drivers from NVidia themselves on Ubuntu and ArchBang (not virtualized).

The only thing that tells me they are proprietary is that modifying the code is a no-no for redistribution. Regardless, that's a TON of support from both, though ATI is severely lagging behind NVidia I believe. A buddy of mine had a 5xxx series from '10 I believe under Ubuntu with their own drivers - playing the new(ish) Hitman game in widows, and can't really do a ton with ubuntu in the game (though can play modern warefare like a champ). Maybe Mr. Torvalds got to them NVidia guys though... hmmm...

Tresquel, even then, is not a distro I would touch for replacement. Nor would any of the Free-only distors (on linux, solaris, BSD, anything unix-like or on a computer at all).

I agree with the need for more support from the manufacturer, truly. But there is a LOT right now, especially from NVidia. If linux gaming were bigger, maybe it'd be true. Still, Windows will be for any foreseeable future the king here. I play anything as well with my ubuntu ans my mac - and that's WITH proprietary drivers.

I'm not telling the FSF to screw themselves, but until GNU comes out with their own distro and not just the HURD kernel - then suck it. Propreitary will ALWAYS be there, open or not. And like today's graphics in linux, proprietary drivers and such will be better.

So no trisquel for me. On a VM it works great, on an actual hard drive, not so much.

---

### Post by JiuJitsu500 on 2013-02-16
Oh, don't take me for an Apple or Microsoft fan at all... please. I love linux and Ubuntu - but Ubuntu is changing for a market that requires money from us eventually. Some say anyway, I disagree with that... but also disagree with the whole auto-opt-in crap they are pulling.

I still seriously think Precise is it for me.

I have a Mac, and never again. I have Windows, and will not go past 7 - anything past XP sucks a$$ for the most part, but 7 is at least bearable (and I play video games from time to time)...

That leaves me with the rest of *nix - and Solaris is under-developed and I can't use it for crap, BSD is lightyears behind linux in the desktop world, and linux itself requires proprietary jazz. Any computer always will - and open-source is the key.

The "open" part makes it innovative. If your company can best the free developer world, you win. If not, you lose, and someone else from the winner comes in with they pay to do it as a job now. It's not about the money, but it is. If I make a graphics card or CPU, I will make damn sure I make the best support for it in all platforms.

Apple and Microsoft go to whole other levels. I'd agree if I bought Windows and got every bit of support for FREE from then on out, and every bit of microsoft product software for free from then on out - updates, repair, replace (OEM coop), etc...

But they don't. and Mac/Apple is even worse. They have excellent AppleCare and Genius support - but that's about it. The fact the Jobs and Cook put out a memo telling every level of support to officially deny that malware, viruses, spyware, or anything like those are real and true for Macs is stupid - and the fact that that same memo put out that they are not to contact higher support or remove/replace hardware or software at any cost. That's Apple for you. Microsoft did a similar thing with Windows - when it CLEARLY stated in their EULA that you can return for a ful refund ANY unused copy of windows - but put that off on the OEM companies... WTF???!!! Go figure. The whole "you can't get a virus on a mac" is 100% TRUE and legal for them to say - Windows viruses do not affect mac. Linux viruses hardly, if at all, truly exist at any rate by comparison.

That's my view on super-proprietary. NVida and ATI are right in their own way to chase a dollar or thousands or billions, got it... and are right to support machines that make it, and not those that break it...

but in the end, who else do you have? We HAVE to rely on proprietary junk. You think Open Ofiice or LibreOffice are anywhere NEAR Microsoft Office? GIMP is as powerful, hell yeah, but NOT at all as user-friendly (also agreed, an insulting term to the user)... audacity? the update system (windows = suck, I know... but Mac is actually downright better at this than any linux I've tried when upgrading releases - even rolling)? name it... linux is better at almost everything on it's own, but you cannot say that proprietary is garbage, useless, or something that shouldn't happen.

I love Stallman for making linux happen, he is a saint to me up there with Torvalds himself. But GNU has not ever made a distro... so that's iffy. But still, the people who stick to that argument mean that you cannot have anything proprietary - which I disagree with.

I'm a capitalist, I make my OWN life. I'm not a communist, nor socialist. Screw that. If I do it better than you, I'm going to go further than you. FSF is all about carrying each other's weight - which is *<snip>* for an argument.

To the OP ---- I'd reccomend sticking with an ubuntu-derrivitave, or a debian-based distro unlike Free-Only. That's crap to me, though good principals. Eventually, you'll need something proprietary, but that doesn't mean you'll pay anything for it more than a download. Xubuntu, Lubuntu, etc should do it.

---

### Post by Lemuriano on 2013-02-16
> **MyTinFoilHat said:**
> Lastly (See? I told you I had questions!), are there good, reliable community forums that I can check out before I take another step forward (i.e., like where we are right now, but for Trisquel)?

Yes

```
[http://trisquel.info/en/forum](http://trisquel.info/en/forum)
```

---

### Post by MyTinFoilHat on 2013-02-17
Thank you to everyone who replied.

I've actually reconsidered the whole Trisquel scenario for the time being. I've actually tabled it for now.

I attempted to setup a dual boot with Ubuntu and Trisquel and found the entire process frustrating and daunting. In fact, I had issues during the installation process that were, perhaps, only related to my understanding. (I'm still very new to gnu/linux so I'm not quite to the level of understanding that most everyone else in the community is). 

So, things went poorly for me. I ended up having flashing folder with a "?" blinking at me at some point and the only way to resolve it (for me) was to insert the liveCD again and again. I think people refer to this as a boot loop or something and I'm hazarding a guess that this is related to grub not knowing what to do.

At any rate, I couldn't use Trisquel and found this whole scenario scary (as a new user). After days of frustration, the only thing that ended up working for me was to boot from CD and reintall Ubuntu.

Until I can get myself to a better place of knowledge and understanding, I'm going to have to live with compromised principles and use Ubuntu. I'm actually mostly okay with using Ubuntu overall. In fact, I like it A LOT, but it would be MUCH better for me if the installation process itself actually gave the user options for downloading those packages (i.e., Amazon, shopping-lens, etc). I'd have no issues with Ubuntu in that way. 

Personally, I just don't like having things shoved down my throat; nor do I enjoy (what I consider to be) bloatware. And I certainly don't like being automatically opted-in to anything. I believe in options and what has frustrated me about Canonical's vision is the lack of options. IMHO, all they really need to do is present a clearly-definied, non-intrusive method for ASKING during the installation process. Something like this:

(This prompt would explain ALL the lens and scope options and concisely summarize their purpose as well as their ties to third parties. It would also explain that this is another way for the user to 'financially contribute to Canonical's financial success' by way of monetizing their personal data.)

> 
Hey there! Welcome to Ubuntu! Before we get started, we'd like to offer you some peripheral services. Would you like to install these options? If you say NO, we won't install those packages, but if you change your mind, you're welcome to come back here to get this option again...

with the users necessarily having to respond one way or the other.
> 
Would you like to install AMAZON, SHOPPING-LENS, (etc)?
[ ] YES, I want those components. Please install those now after I've read and agree to the Privacy Policy related to the services for which I am knowingly opting-in/agreeing to.
[ ] No Thank you. I do not want those components installed. Please don't install those components. I understand that if I change my mind, I can come back here to get them.


And that would be the end of that.

If it were that simple, I'd have NO QUALMS with Ubuntu at all. Hell, I'd even recommend it to everyone I know! Seriously. I'm not just saying that. I honestly would recommend Ubuntu to everyone - even those people I know that enjoy these sorts of options. However, that's hard to do when the system that's currently in place doesn't provide that as a clear, concise option (as I've sketched above). Currently it's akin to "Oh, by the way, we have these features. We've taken the liberty of putting them on your system for you. In fact, they're already engaged. If you don't want these features, you're going to have to do x, y, and z and uninstall x, y, z.

To my mind, it is all about splitting hairs to call the latter "options", but that's the way the cookie crumbles I suppose. 

At any rate, I'm going to have to hold-off on other options for the time being and, at the same time, be content with keeping up on Canonicals evolving features that I'll inevitably have to OPT-OUT of...

(SIGH)

---

### Post by Lemuriano on 2013-02-17
Perhaps you should try Xubuntu. It has a nice the level of customization, it belong to the Ubuntu family, but you may have more control and wont have to deal with some of the issues you mention (Amazon). 

Regards.

---

### Post by J_we on 2013-02-17
> **JiuJitsu500 said:**
> @ Lemuriano

Hold on... I don't think there are many setups at all that are strictly Free-Friendly, but if I'm wrong then I won't disagree. Find me a laptop you can't build yourself though with all FSF compliance. HP, ASUS, Acer, Dell, a TON of companies who make mostly dig Linux and the idea of open-source... but dude... get real to think any decent and commonly found laptop is ALL FSF or open friendly. Still won't argue if you're right. BUT, I will disagree that you have to be out of your mind in the graphics department.

Do you really think noveau or flgrx are even CLOSE to proprietary?

NVidia and ATI are all you have. Integrated graphics with both AMD and Intel are not even an argument, period. Both are well supported, yada yada.

NVidia and ATI BOTH offer their OWN drivers, available from the manufacturer and the repos of many distros (as they come in tarballs, virtually any distro can install them, use them, keep updated, etc). And I mean that. Fedora and all the .rpm guys, arch and the pacman guys, debian and all the .deb guys, keep going... gentoo, slackware, dragora, name it... they ALL have ATI and NVidia support FROM the manufacturer... and if not, they are based on a package manager who has a developer who DOES make the drivers (even if they are not of as-high quality...

So, then you ask why that's necessary... well, because I buillt this damn computer or bought it as-is. So, when I look for a distro that supports it all, most of which works out-of-box, I want to know the manufacturer supports my distro (at least the manager. You can get Fedora to function as well as Ubuntu or Slax or Arch with drivers FROM the manufacterer... so why go with the whole Free Software thing? They make the devices, so their drivers should be better than the open-source ones, right? Not in all cases, granted. They are STILL open, anyone can change it.

Besides, no one plays Battlefield 3 or Skyrim with 50 mods - let alone anything newer (Crysis 3, Dead Space 3... anything coming out, etc)... There is literally nothing else requiring perfect drivers. My NVidia 550M (i think) works like a boss with compiz and games like MW2 or 3, or Age of Empires, and I run Photshop and Autocad (any edition) like a champ. Not to mention having 6 virtual machines at once eating (as in destroying) my CPU, yet still not doing a lot of damage to my GPU. That's WITH the drivers from NVidia themselves on Ubuntu and ArchBang (not virtualized).

The only thing that tells me they are proprietary is that modifying the code is a no-no for redistribution. Regardless, that's a TON of support from both, though ATI is severely lagging behind NVidia I believe. A buddy of mine had a 5xxx series from '10 I believe under Ubuntu with their own drivers - playing the new(ish) Hitman game in widows, and can't really do a ton with ubuntu in the game (though can play modern warefare like a champ). Maybe Mr. Torvalds got to them NVidia guys though... hmmm...

Tresquel, even then, is not a distro I would touch for replacement. Nor would any of the Free-only distors (on linux, solaris, BSD, anything unix-like or on a computer at all).

I agree with the need for more support from the manufacturer, truly. But there is a LOT right now, especially from NVidia. If linux gaming were bigger, maybe it'd be true. Still, Windows will be for any foreseeable future the king here. I play anything as well with my ubuntu ans my mac - and that's WITH proprietary drivers.

I'm not telling the FSF to screw themselves, but until GNU comes out with their own distro and not just the HURD kernel - then suck it. Propreitary will ALWAYS be there, open or not. And like today's graphics in linux, proprietary drivers and such will be better.

So no trisquel for me. On a VM it works great, on an actual hard drive, not so much.


There are many problems with NVIIDA and ATI drivers. AMD has done an extremely poor job and we don't have all the code needed to produce a truly free driver. 

Intel graphics aren't as powerful although they are better supported in some areas and have greatly improved. They are beginning to get competitive with the low end of NVIDIA. What is nice about Intel is all distributions have support out of the box. There aren't any proprietary drivers to install and you don't have to worry about losing support down the line when NVIDIA/AMD pull support (and it always happens with proprietary software). We aren't dependent on NVIDIA/AMD/Intel for support with the Intel graphics drivers. Overall most people would be better off with the Intel graphics on Linux right now. Most people don't play games even though it is a growing percentage.

It doesn't really matter which side your on everybody who knows anything hates what NVIDIA is doing. The company is awful when it comes to Linux even if they have done a decent job on coding the drivers themselves. They do not cooperate with the community and that is why Linus was bitching about them.

As far as hardware goes it is becoming easier to get Linux friendly hardware. Unfortunately there are major issues with the majority of systems put out by ZaReason, System76, and others. Personally I think the hardware is on the low end quality wise. The one laptop for instance that I received from ZaReason didn't support suspend to ram. Another laptop  got from System76 was pure junk. 

Overall ThinkPenguin has done a pretty good job. It's as close to Apple/Lenovo as you'll find and certainly beats Dell/HP/Acer.

HP/Toshiba/Dell/Lenovo/IBM/Compaq systems all ship systems with digital restrictions that can be a major problem too. It is the #1 issue facing new Ubuntu users right now.

The propritary drivers are definitely holding Linux back. If propritary drivers were eliminated there would be an increase in support for Ubuntu and more users. That would in turn help fund the development. This is because it would become easier to use. Trisquel has seen an uptake in popularity since ThinkPenguin started supporting the distribution. When hardware isn't compatible people will buy proper hardware. That results in better support for both Linux and the user.

NVIDIA/ATI would be forced to embrace the free software model or leave. While it might be they choose to leave it would be for the best. As it is we are turning Linux into a clone of Microsoft Windows and Apple OS X. Ubuntu even copied the right/left for minimize/maximize/the docker bar/proprietary software/etc.

Steam coming to Linux is probably not a good thing. It's likely to bite users later. We have seen it happen time and time again. Most users haven't been around long enough to remember.

Some recent debacles:

Ubuntu pulls Oracle Java from users systems because it can't push security updates due to a change in the proprietary license. Left millions of users freaking out and no clear solution on how to fix the problem.

Adobe Flash was discontinued on Linux and now firefox will not get anything but security updates. Soon users will find they can't access sites because "a newer version of flash is required, please click here to install" and obviously can't. Now it isn't quite as end of the world as in the past. Chrome does exist although it isn't in the Ubuntu repository. A lot of Chrome is actually proprietary too. Most users shouldn't be installing stuff outside of Ubuntu's main repository and maybe universe/multiverse.

Lexmark, Cannon, Samsung, Dell, ... scratch that. EVERY other company other than HP has crummy support for Linux (printers). They release propitiatory drivers which don't work between releases and are near impossible to get working after the support is discontinued. There are excepetions with many high end laser printers because they comply with postscript. However all in all the best printers are the free software friendly HP printers.

Then you have USB N adapters which are basically all crap. Atheros is releasing the complete code for one of its newer chipsets. That should solve the problem but the point is we need companies to release 100% of the code to fix this nightmare. The other chipset that works great is an older USB G chipset from Realtek. It doesn't dependent on any proprietary software. Despite the driver missing a lot of features found elsewhere it just works- with EVERY distribution out there. It's in the mainline kernel, it works on Raspberry PI, and much more.


Some older examples: Corel ported wordperfect, draw, and some others to Linux in the late 1990s. All the users who invested in that lost access to there documents when the company discontinued it.


I could go on... I won't. I doubt anybody is still reading this rant.

---

### Post by J_we on 2013-02-17
> **MyTinFoilHat said:**
> Thank you to everyone who replied.

So, things went poorly for me. I ended up having flashing folder with a "?" blinking at me at some point and the only way to resolve it (for me) was to insert the liveCD again and again. I think people refer to this as a boot loop or something and I'm hazarding a guess that this is related to grub not knowing what to do.

At any rate, I couldn't use Trisquel and found this whole scenario scary (as a new user). After days of frustration, the only thing that ended up working for me was to boot from CD and reintall Ubuntu.

(SIGH)

Trisquel removed 'bad' software. That might be why you had problems. The solution is not to use 'bad' software. The solution is to take into consideration what hardware you buy in the future. 

Everybody benefits from more free software. Now I'm not going to tell you to buy a new computer if you don't have the money. And I wouldn't suggest Trisquel if your just getting familiar with Linux in general. However it is one of the better distributions in various areas. It is the most respecting of users freedom and that can make it hard to use. Regardless of the distribution though avoiding the non-free bits is the best thing you can do to help promote Linux. And using stuff that is free is often easier/better too in various ways. Particularly for new users.

Ubuntu, Linux Mint, ZorinOS, and some others are definitely better choices for new users. I find Unity though a challenge. I think Linux Mint and Zorin OS are best for new users at this point in time.

Canonical has made some grave mistakes with the direction its headed. It isn't just Unity either. It's all over the place and doesn't know what to do. If the company doesn't figure out its niche soon I'm sure it'll go under just like the other commercial distributors have.

All of this said Trisquel is actually easier to use with the right hardware. Have you ever tried to use a dial-up modem in Ubuntu? It's MUCH MUCH MUCH easier in Trisquel.

---

### Post by dusanyu on 2013-02-17
Have you given a look at opensuse? It has a nice community good repos and the DVD has  the choice Kde gnome xfce and window manager only systems.  Other desktops like cinnamon and mare are in repo. You can even go rolling rerelease. 

Menus in all are preconfigured and it generally feels more polished than Ubuntu . 

On and one click install is awesome (auto configs repos for you)

---

### Post by MyTinFoilHat on 2013-02-18
> **J_we said:**
> Trisquel removed 'bad' software. That might be why you had problems. The solution is not to use 'bad' software. The solution is to take into consideration what hardware you buy in the future. 

Everybody benefits from more free software. Now I'm not going to tell you to buy a new computer if you don't have the money. And I wouldn't suggest Trisquel if your just getting familiar with Linux in general. However it is one of the better distributions in various areas. It is the most respecting of users freedom and that can make it hard to use. Regardless of the distribution though avoiding the non-free bits is the best thing you can do to help promote Linux. And using stuff that is free is often easier/better too in various ways. Particularly for new users.

Ubuntu, Linux Mint, ZorinOS, and some others are definitely better choices for new users. I find Unity though a challenge. I think Linux Mint and Zorin OS are best for new users at this point in time.

Canonical has made some grave mistakes with the direction its headed. It isn't just Unity either. It's all over the place and doesn't know what to do. If the company doesn't figure out its niche soon I'm sure it'll go under just like the other commercial distributors have.

All of this said Trisquel is actually easier to use with the right hardware. Have you ever tried to use a dial-up modem in Ubuntu? It's MUCH MUCH MUCH easier in Trisquel.

As I see it, the root of the problem isn't necessarily Ubuntu, but rather on the ideas that promote the status quo. "Share this", "Friend this person", "Like this", etc, etc ad nausea. It's social media that's behind the current schemata, a schemata that now has evolved to usurping an individual's constitutional or human rights by way of agreements to terms of service. So now, in effect, we have corporations that (somehow) are able to effectively 'trump' your rights. My goals and objectives (as well as assets and liabilities) are perceived very differently than those for whom social media is a way of life. Everything truly is relative.

My point in checking out other distros was a means to an end: the achievement of my own goals, a balancing of what *I* consider to be *my* assets and liabilities.

To make matters worse (again, from my perspective) we now have communities pushing the social media/integrate everything agenda. I don't use Facebook, Twitter, Google, etc. These things are not a part of my life, nor do I want them to be a part of my life. So, it is with particular disdain that gaze upon the scopes, lenses, and other emerging features in Ubuntu with some measure of disgust - even with the ability to disengage these features. Furthermore, someone else in my position might also call this "bloatware" as seen on mobile devices the world 'round.

Do not misunderstand: I honestly enjoy Ubuntu. I think it has tremendous potential. It just needs to stop presuming a user's want of participation in these things. Options are a way of life for me (and, undoubtedly, others). The more options and features, the richer the user's experience. This includes the ability of the user to simply say "No thanks" from the onset. We simply can't withhold great potential from a class of people simply because they might not want or have a need to utilize those features.

Perhaps my ideas are a tad radical for some and, as I said previously, I do not begrudge Canonical making profits; however, I do not wish it to do so in a way that usurps my rights. Call me old, but time was when someone asked permission before doing something rather than assuming and having someone.

I actually have a proposed idea as well as an expansion on that idea, a solution if you will, so that Canonical AND people like me can both have their cake and eat it too.

The idea is simple: Being PROMPTED during installation process. Something akin to this (as previously mentioned):

> 
Hey there! Welcome to Ubuntu! Before we get started, we'd like to offer you some peripheral services. Would you like to install these options? If you say NO, we won't install those packages, but if you change your mind, you're welcome to come back here to get this option again...


with the users necessarily having to respond one way or the other.
> 
Would you like to install AMAZON, SHOPPING-LENS, (etc)?
[ ] YES, I want those components. Please install those now after I've read and agree to the Privacy Policy related to the services for which I am knowingly opting-in/agreeing to.
[ ] No Thank you. I do not want those components installed. Please don't install those components. I understand that if I change my mind, I can come back here to get them. 


Now, I'm not technical so I can't know whether or not the following suggested enhancement is possible. I have to rely on the skill of others to help me understand whether or not it is possible:

The packages that Canonical is working toward integrating, in addition to what's already in place(as seen in this post on OMGUBUNTU.co.uk ): [http://www.omgubuntu.co.uk/2013/02/100-scopes-list-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/02/100-scopes-list-ubuntu-13-04) 

Would it be possible to, say, put all these features into a package separate from the "main" Ubuntu, in a separate repo, so that (during installation) when the user decides to add those features, the repo is added and the features installed? Conversely, a user response of "No thanks." would insure that the repo is NOT added and those features NOT installed?

In short:

PROMPT user before installation.
Receive user response.
Add repo and selected features ONLY if the User affirms; otherwise, ignore and proceed with "clean" installation.


With all our wonderful technology and the skills of an entire community of developers, certainly this can't be impossible.

Wondering what people's thoughts are. I'd love to propose this to Canonical.

---

### Post by Hylas de Niall on 2013-03-14
Toutatis (6) seems pretty nice IMHO. I just installed it on my Toshiba laptop (a210) and it all works fine - straight out the box.
Very happy with it so far, that's with ATI graphics too.

---

### Post by Lemuriano on 2013-03-14
> **Hylas de Niall said:**
> Toutatis (6) seems pretty nice IMHO. I just installed it on my Toshiba laptop (a210) and it all works fine - straight out the box.
Very happy with it so far, that's with ATI graphics too.

Did a netinstall of Toutatis and then install xfce on a system76 pan7 laptop and I´m very pleased with the outcome. The only downside is the laptop itself, because my System76 laptop is not freedom friendly.

---

### Post by BBQdave on 2013-03-14
> **MyTinFoilHat said:**
> I honestly enjoy Ubuntu. I think it has tremendous potential. It just needs to stop presuming a user's want of participation in these things. Options are a way of life for me (and, undoubtedly, others). The more options and features, the richer the user's experience. Wondering what people's thoughts are.

I think you should give Fedora 18 with Gnome 3 a try :D

Add Adobe Flash Player and Fluendo mp3 codec pack, both free downloads, and you have a nice system that is not to far off from your Unity experience. With One exception, Fedora does not data mine you.

---

