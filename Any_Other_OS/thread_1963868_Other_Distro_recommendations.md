---
title: "Other Distro recommendations?"
date: 2012-04-23
forum: Any Other OS
---

### Post by reset042 on 2012-04-23
I've been using Ubuntu for years now, and have tried really hard to get along with Unity but I now realise that Ubuntu is fundamentally no longer the distro for me. I can see and appreciate the clever stuff being done, but it just does not suit the way I have been working for many years, and so, sadly, I've decided to move on from Ubuntu.

I looked at Lubuntu, but the first two apps I wanted to install from Synaptic were also going to install Zeitgeist, and I guess that that would happen a lot with software from the Ubuntu repos? (I don't like the way that Zeitgeist is so tied into everything. I think I can see why it's so tightly integrated, but I do not use it and would like to get rid of it and free up the unnecessary processor cycles - which on a couple of occasions started eating up huge amounts of my CPU, and is what alerted me to Zeitgeist in the first place.) So, much as it pains me, I'm wondering if I should move away from Ubuntu based distros altogether?

I like the look of LXDE (haven't tried XFCE) and would appreciate your suggestions for distros. I'm not too technically proficient (the terminal still scares me) but I can follow instructions.

There are a few important things I'd like installed: Compiz and its Cube, a dock or similar launcher such as Cairo, a decent file manager, and a taskbar.

---

### Post by alenis on 2012-04-23
I would use debian testing. You can install XFCE od LXDE without being forced to install things that you don't like, you always have the most up-to-date verisons of your software and it is usually very stable.

---

### Post by km3952 on 2012-04-23
I agree, go to Debian & have almost complete control, however you will find that you need to install 'non free' software quite a lot these days (firmware drivers that come with *buntu).

---

### Post by TeamRocket1233c on 2012-04-23
How 'bout Fedora, Crunchbang, Oracle, CentOS, or Mandriva?

---

### Post by ratcheer on 2012-04-23
My top recommendations would be **ArchBang** (or even Arch Linux) and **Sabayon**, especially the CoreCDX spin, which allows you to build up your system exactly the way you want it - I just stuck with its original FluxBox desktop.

Tim

---

### Post by snowpine on 2012-04-23
> **reset042 said:**
> I looked at Lubuntu, but the first two apps I wanted to install from Synaptic were also going to install Zeitgeist, and I guess that that would happen a lot with software from the Ubuntu repos? (I don't like the way that Zeitgeist is so tied into everything. I think I can see why it's so tightly integrated, but I do not use it and would like to get rid of it and free up the unnecessary processor cycles - which on a couple of occasions started eating up huge amounts of my CPU, and is what alerted me to Zeitgeist in the first place.) So, much as it pains me, I'm wondering if I should move away from Ubuntu based distros altogether?

What are the "first two apps" that require zeigeist? Maybe they require zeitgeist for a good reason. Maybe they will also require zeitgeist if you switch to another distro and switching distros isn't the answer at all. If you tell us the names of these secret apps maybe we can suggest alternatives. :)

---

### Post by reset042 on 2012-04-23
Thanks everyone for the suggestions. I've been wondering about whether to try Debian for a while. I'd be interested to read more opinions and advice.

@snowpine  :-)   They're not secret apps! The first app I tried to install was cairo-dock.  I'm afraid I can't remember what the second was (my poor old feeble brain...) but it wanted to pull in a lot of Gnome stuff and with it Zeitgeist. This is why I want to get away from Gnome and am looking at LXDE and XFCE.

---

### Post by snowpine on 2012-04-23
I just checked the Debian site for you, and I don't see Zeitgeist listed as a dependency for cairo-dock, so you should be OK:

[http://packages.debian.org/squeeze/cairo-dock](http://packages.debian.org/squeeze/cairo-dock)

Remember that cairo-dock is completely optional; you can run Lubuntu without it if you choose. :)

(edit) did a little sleuthing for you, for the current stable version of cairo-dock (debian has an older version) "Zeitgeist is needed for the Recent-Events applet." source: [http://www.glx-dock.org/ww_page.php?p=By%20compiling&lang=en](http://www.glx-dock.org/ww_page.php?p=By%20compiling&lang=en)

---

### Post by reset042 on 2012-04-24
Thanks for the detective work, snowpine. :)  I understand cairo-dock is optional, but I just love the simplicity, speed and ease of launching favourite apps and files. For me it works better than other options and I would not want to be without a dock. That said, I suppose I could look at other docks. 

@ Tim - thanks, I had a look at Arch and although it looked impressive they were honest about it requiring a level of technical competence that I sadly don't possess! So perhaps not for me. 

*@ *TeamRocket1233c - *"CrunchBang Linux is not recommended for anyone needing a stable system" *reading that on the #! site was nice and honest of them, but it means it's not for me! Another reason I'm moving away from Ubuntu is that I'm fed up with the huge number of X segfaults I'm getting on a regular basis.

Thanks to all again. I'm downloading Debian Squeeze at the moment to give that a try, but I'd still welcome any suggestions.

---

### Post by Lemuriano on 2012-04-24
Hi,

 If free as in freedom is a priority for you and use or are willing to use only free software, then Trisquel 5.5 is worth a  try. You can choose between Gnome 3.2 fall back mode, LXDE or from the terminal or SPM XFCE which was my choice. 

I have to said that it´s very stable and run smoothly without any issues. Take a look a the XFCE desktop:

Regards.

---

### Post by snowpine on 2012-04-24
> **reset042 said:**
> *@ *TeamRocket1233c - *"CrunchBang Linux is not recommended for anyone needing a stable system" *reading that on the #! site was nice and honest of them, but it means it's not for me! Another reason I'm moving away from Ubuntu is that I'm fed up with the huge number of X segfaults I'm getting on a regular basis.

CrunchBang is Debian Squeeze with Openbox; it's about as stable as you can get (certainly more stable than Ubuntu). The disclaimer does scare a few users off, as we've discussed a couple of times on the forums:

[http://crunchbanglinux.org/forums/topic/2/the-crunchbang-linux-disclaimer/](http://crunchbanglinux.org/forums/topic/2/the-crunchbang-linux-disclaimer/)
[http://crunchbanglinux.org/forums/topic/13850/excellent-distro-but-people-are-in-the-dark-about-it/](http://crunchbanglinux.org/forums/topic/13850/excellent-distro-but-people-are-in-the-dark-about-it/)

(Disclaimer of my own: I'm a moderator on #! forums, so I may be a little biased.)

---

### Post by jefsview on 2012-04-24
Crunchbang is very stable. I used it as a base install for a few months. What I loved about it was that it detected my wireless out of the box and had an exceptional start-up script that walked newbies through getting your system up and running quickly. More Linux and Debian distros could use those.

Crunchbang is based on Debian Stable, so some of the software is not the latest; yet they have a backports edition available. I used it as a base and went to Sid. In the end, I just didn't like how Debian treated multiarch support, so I've gone back to Xubuntu 12.04, which is fantastically better than 11.10.

That being said, I'm still eager to try out the French Voyager 12.04 (Based on Xubuntu LTS) at the end of the month, just cause I like how it looks and love the Conky config application they use.

-- Jeff

---

### Post by cortman on 2012-04-24
I was about to recommend Crunchbang myself. It's rock solid, and it comes with a really nicely tweaked openbox + tint2 environment. Really lightweight and really slick.

---

### Post by ph4nt0m117 on 2012-04-24
XFCE
Nubuntu
Solaris

win 7

:|

I prefer XFCE myself :3 U never worked for me and kept resetting itself.  It's like a Macbook with the battery unplugged and plugged back in.

bleh

XFCE is my fav.

YLMF is pretty good too.  Applications that could be needed are already in there and some that aren't as well.  radioget is pretty neat.  Anything being broadcast in china over TV or asia in total can be seen over a video stream.

---

### Post by Herpythebrony on 2012-04-24
Xubuntu, Linux Mint xfce or mint debian xfce or aptosid xfce if you want Debian Base

---

### Post by codingman on 2012-04-25
I personally like Fedora, especially since F17 is coming out. I have one computer that is solely for Fedora. It's also a bit more stable than Ubuntu in some ways.

---

### Post by codingman on 2012-04-25
> **ph4nt0m117 said:**
> 
Nubuntu


I thought that had lost support. No?

---

### Post by codingman on 2012-04-25
I have not tried Debian but I have heard it is rock solid, and BTW, what will you be using on it?

---

### Post by aykoola on 2012-04-25
Debian is rock solid. But you have to put in a bit more work. So far i love it, but i'll try precise to see which one i prefer until wheezy comes out. Then i'll probably use Wheezy.

---

### Post by Lemuriano on 2012-04-25
LMDE-XFCE (Linux Mint Debian Edition), is a very nice ditro plus is a semi-rolling release.

Regards.

---

### Post by reset042 on 2012-04-26
Thanks everyone - this is a great help. 

I installed Debian Squeeze in a VirtualBox VM, and was impressed at how snappy it seemed despite running in a VM. I have tried it with both XFCE and LXDE and, although I haven't yet been able to devote much time to fully exploring them, I like them both. My initial impression was that LXDE seemed a bit faster and lighter, but XFCE seemed perhaps more polished. I don't know if that assessment is fair.

One slight disappointment of both is that the font antialiasing doesn't seem to be as good and polished as that in Ubuntu. As I'm staring at a monitor for anywhere between 8 and 12 hours a day (yes, I know I should get a life!) this is very important to me. I wonder if there's any way to use the Ubuntu antialiasing?

Also I was unable to get the Compiz cube working in either LXDE or XFCE although I strongly suspect this is a limitation of running in a VirtualBox VM.

@snowpine and jefsview - thanks for the clarification re #! - I'll try and give it a look
@ph4nt0m117 - thanks for the suggestion re Win 7. This computer came with it pre-installed, so I did try that. Once. For about 15 minutes. Never again.

---

### Post by mips on 2012-04-26
> **reset042 said:**
> 
One slight disappointment of both is that the font antialiasing doesn't seem to be as good and polished as that in Ubuntu. As I'm staring at a monitor for anywhere between 8 and 12 hours a day (yes, I know I should get a life!) this is very important to me. I wonder if there's any way to use the Ubuntu antialiasing?

Yes you can implement the exact same font antialiasing ubuntu uses, I've done it before.
[http://crunchbanglinux.org/forums/topic/7415/howto-font-rendering-like-ubuntu/](http://crunchbanglinux.org/forums/topic/7415/howto-font-rendering-like-ubuntu/)
[http://lovingthepenguin.blogspot.com/2010/07/ubuntu-font-rendering-in-debian-squeeze.html](http://lovingthepenguin.blogspot.com/2010/07/ubuntu-font-rendering-in-debian-squeeze.html)
[http://noz3001.wordpress.com/2011/07/01/ubuntu-font-rendering-on-debian-wheezy/](http://noz3001.wordpress.com/2011/07/01/ubuntu-font-rendering-on-debian-wheezy/)



On a unrelated note another thing to consider if you are not happy with the older packages in Debian 6 you could try their testing version (Wheezy) for more up to date stuff. Even though it's testing it's not really unstable.

---

### Post by reset042 on 2012-04-26
> **mips said:**
> Yes you can implement the exact same font antialiasing ubuntu uses, I've done it before.

Brilliant! Thanks for that.

> **mips said:**
>  ...Debian 6 you could try their testing version (Wheezy) for more up to date stuff. Even though it's testing it's not really unstable.

Thanks again. Yes, I think I'll install Wheezy on this computer directly, and not through a Virtualbox VM. Am I right in thinking it'll keep Ubuntu and will install alongside that and update grub?

---

### Post by reset042 on 2012-04-26
@mips - Am I missing something, or does the antialiasing tip you supplied only work in Gnome? XFCE is still giving me a headache with its jagged fonts!

---

### Post by mips on 2012-04-26
> **reset042 said:**
> @mips - Am I missing something, or does the antialiasing tip you supplied only work in Gnome? XFCE is still giving me a headache with its jagged fonts!

No it should be universal as i did it with XFCE which is my DE of choice.

If you really want I could try and install Crunchbang xfce in a vm and get the fonts going but I suspect you might have it sorted before I even get that far.

---

### Post by codingman on 2012-04-27
> **reset042 said:**
> Thanks everyone - this is a great help. 

 My initial impression was that LXDE seemed a bit faster and lighter, but XFCE seemed perhaps more polished. I don't know if that assessment is fair.


By far that is fair, LXDE stands for Lightweight X11 Desktop Environment, that is why it uses less resources.

---

### Post by Antman on 2012-04-27
> **Lemuriano said:**
> LMDE-XFCE (Linux Mint Debian Edition), is a very nice ditro plus is a semi-rolling release.

Regards.

+1 if you are looking for a Debian distro.

---

### Post by Antman on 2012-04-27
If you are looking for something that keeps the Arch K.I.S.S. philosophy, but without the potential dangers of breakage from super new updates, give the [Chakra Project's Archimedes]("http://www.chakra-linux.org/") distro a try. It uses a semi-rolling release model with tested software.:guitar:

---

### Post by OpenSourceRules on 2012-04-28
If you like dock by default, Xubuntu and Dreamlinux comes to mind.  
Unfortunately, the menu for Dreamlinux is a little difficult to fix.

---

### Post by mips on 2012-04-28
> **reset042 said:**
> @mips - Am I missing something, or does the antialiasing tip you supplied only work in Gnome? XFCE is still giving me a headache with its jagged fonts!

Somehting you could try is to simply copy over the /etc/fonts/ from a existing Ubuntu install (not sure about a LiveCD but worth a try) to your debian install. **Edit:** Here is a easier way, [http://ospa.arvat.org/ubuntu-fonts-in-debian-squeeze/](http://ospa.arvat.org/ubuntu-fonts-in-debian-squeeze/)

(You could also copy [http://font.ubuntu.com/download/ubuntu-font-family-0.80.zip](http://font.ubuntu.com/download/ubuntu-font-family-0.80.zip) these fonts over to your debian install if you dont already have them.)

Another link for you [http://forums.debian.net/viewtopic.php?f=10&t=38534&p=353765#p353765](http://forums.debian.net/viewtopic.php?f=10&t=38534&p=353765#p353765)

Edit: If you use Wheezy i think the libcairo package is already patched but you would still have to do the first step I mentioned.

---

### Post by Sableyes on 2012-04-28
> **reset042 said:**
> T My initial impression was that LXDE seemed a bit faster and lighter, but XFCE seemed perhaps more polished. I don't know if that assessment is fair.

It is fair, but take into considertation XFCE shines as a modular desktop, not a lightweight desktop. As in you can take individual bits of XFCE (panel, WM, etc) and install and use them with other desktops. Such as folk who use XFCE  Panel in OpenBox.

XFCE is not lightweight, nor should it be. It is however far more flexible in its uses (/modular) than most people ever seem to notice.

---

### Post by OpenSourceRules on 2012-04-29
> **Sableyes said:**
> It is fair, but take into considertation XFCE shines as a modular desktop, not a lightweight desktop. As in you can take individual bits of XFCE (panel, WM, etc) and install and use them with other desktops. Such as folk who use XFCE  Panel in OpenBox.

XFCE is not lightweight, nor should it be. It is however far more flexible in its uses (/modular) than most people ever seem to notice.

XFCE is not as light as LXDE, but it is considerably lighter than Gnome (especially after the Gnome shell).

---

### Post by mips on 2012-04-30
> **OpenSourceRules said:**
> XFCE is not as light as LXDE, but it is considerably lighter than Gnome (especially after the Gnome shell).

Just to add people must also not confuse Xubuntu with a standard install of XFCE either. Xubuntu pulls in a lot of gnome & other unneeded stuff/services which makes it 'heavier'. A base install of Ubuntu + bog standard XFCE will use less resources and feel snappier which is the way I prefer running it.

---

### Post by OpenSourceRules on 2012-05-01
> **mips said:**
> Just to add people must also not confuse Xubuntu with a standard install of XFCE either. Xubuntu pulls in a lot of gnome & other unneeded stuff/services which makes it 'heavier'. A base install of Ubuntu + bog standard XFCE will use less resources and feel snappier which is the way I prefer running it.

This is how the Fedora XFCE runs; it cannot run without the Gnome base at all.  
But my discovery is that: XFCE under Linux Mint still runs a lot slower than Xubuntu anyway.

---

### Post by ratcheer on 2012-05-01
> **OpenSourceRules said:**
> This is how the Fedora XFCE runs; it cannot run without the Gnome base at all.  
But my discovery is that: XFCE under Linux Mint still runs a lot slower than Xubuntu anyway.

After my fresh install of 12.04, this past weekend, my old 12.04 that I had nursed along since Beta 1 was available to experiment on, so I installed xfce 4 on it. Even though it uses about 150 MB less memory, it gives me noticeable lags. Even worse than gnome-shell, which I run on 11.10.

Maybe the problem is something else in that installation, but Unity performs very briskly.

Tim

---

### Post by The Rnegade on 2012-05-02
I've tried a great deal of linux distro's my favourite of all time is Fedora

---

### Post by jrdavis on 2012-05-02
I would recommend Sabayon or Pardus.  I use Pardus, personally, and I feel it's the best one.  It was developed by the Turkish national gov't as an alternative to windows, and it's free.  They've done a phenomenal job.  Also, it's a lot faster than sabayon when it comes to software installation.

---

### Post by Sableyes on 2012-05-03
> **jrdavis said:**
> I would recommend Sabayon or Pardus.

I want to like Sabayon but WOOOOOOOW long install times! :sad:

Pardus is good :guitar:

---

### Post by ratcheer on 2012-05-03
> **Sableyes said:**
> I want to like Sabayon but WOOOOOOOW long install times! :sad:
  

Package maintenance is slow, too. It is a nice distro, but somewhat obtuse in its methods and procedures.

I have just done a fresh install of Arch Linux. What a trip! Everything has to be configured from the ground up, even a task panel at the bottom of the screen.

Tim

---

### Post by TeamRocket1233c on 2012-05-03
Arch or Gentoo? FreeBSD or OpenBSD maybe?

---

### Post by zhogan85 on 2012-05-03
> **ratcheer said:**
> I have just done a fresh install of Arch Linux. What a trip! Everything has to be configured from the ground up, even a task panel at the bottom of the screen.


Yeah, it is a trip, and can be frustrating. I've done a couple of Arch installs, and it definitely gets easier. What DE/WM are you using?

---

### Post by zhogan85 on 2012-05-03
> **TeamRocket1233c said:**
> Arch or Gentoo? FreeBSD or OpenBSD maybe?

+1 for Arch. I've also been interested in taking FreeBSD for a spin lately. Alas, not enough time in the day these days...

---

### Post by ratcheer on 2012-05-03
> **zhogan85 said:**
> Yeah, it is a trip, and can be frustrating. I've done a couple of Arch installs, and it definitely gets easier. What DE/WM are you using?

OpenBox, because I used it before on ArchBang. But, with Arch, I "get to" add each little component separately. Such as a task panel. First, I tried pypanel, which seemed pretty nice but things kept getting a little screwy. So, I removed it and installed tint2, which is doing much better for me.

I am using it right now the simple way, booting to a text console, logging in, and running startx. It is kind of cool, in a way.

I also need to figure out how to configure udev to mount my USB external drive so that all users can have full access. And I would like to install fglrx, but I am seeing that it has major problems with Xorg 1.12, which is what Arch has installed.

---

### Post by kelvin spratt on 2012-05-03
> **zhogan85 said:**
> Yeah, it is a trip, and can be frustrating. I've done a couple of Arch installs, and it definitely gets easier. What DE/WM are you using?
Read the Wiki its all simple there is nothing hard to configure in Arch its all done for you in the Wiki. There again some people would rather struggle then complain?.

---

### Post by VanR on 2012-05-05
Try out SolusOS. It's Debian Squeeze with a custom 3.0 kernel, Gnome 2.3 and up-to-date applications(Firefox 12 and Thunderbird 12 came in today). Only available in 32-bit right now, but 64-bit is coming in a week or 2. I love it.
[www.solusos.com](www.solusos.com)

---

### Post by linuxmatt7 on 2012-05-06
I would recommend that you try Xubuntu 12.04 LTS you will fall in love. This is what happened to me. If you want to go a little bit more advanced than Ubuntu family than I recommend you try Fedora 16 you might like it. 

I used to use Linux Mint when I started with Linux. Now I step up a level in Linux computing so now I use Xubuntu.

---

### Post by OpenSourceRules on 2012-05-07
Dreamlinux is pretty cool, but it requires a little extra work.
Although my computer cannot boot from USB, the ability to update a system and run on USB sounds cool.  (Especially when you can get an USB pendrive with the capacity of an old hard drive.)

---

### Post by TeamRocket1233c on 2012-05-07
I kinda wanna give OpenIndiana a shot on my new desktop PC should I ever get up the dough for the parts to build it.

Solaris is decent too from what I've read, and also, I think Oracle offers it for free for personal use.

Actually, scratch OpenIndiana and Solaris, as Solaris/OpenSolaris/OpenIndiana is a dying platform, if I'm to use any kind of UNIX, I'm going OpenBSD. For Linux distros, it's going to be either Crunchbang, a custom Ubuntu install, or Fedora, maybe CentOS or Oracle Linux, or possibly Arch.

---

### Post by reset042 on 2012-05-08
> **linuxmatt7 said:**
> I would recommend that you try Xubuntu 12.04 LTS
I have tried Xubuntu in a Virtualbox VM and was impressed. I'm seriously considering installing it. The only problem for me is that it's part of the 'buntu family. I'm wary of the way 'buntu is going with things becoming proprietary and tied into the OS. For example: Firefox just kept crashing over and over again. So I uninstalled the Ubuntu version, and am running the Mozilla version and the crashes have stopped. It's that sort of thing that's driving me away from 'buntu although ideally I'd rather not.

Thanks everyone - some very interesting suggestions and I'm still looking at the options.

---

### Post by SlugSlug on 2012-05-08
I also move to Xubuntu due to unity,

Found it great much better than it was last LTS,  though I did have to install nautilus and gedit

The default file browser (Thunar) just didn't cut it for me but nautilus works fine & the default text editor (leafpad) was just to basic.

---

