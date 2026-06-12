---
title: "Lightwight and easy to use distro for relative"
date: 2012-11-27
forum: Any Other OS
---

### Post by MadmanRB on 2012-11-27
Okay heres the scoop, my father is working off an old laptop and is currently dual booting XP and Xubuntu 12.04, unfortunately xubuntu is not really working out for him.
I would try the latest Linux Mint on his machine but even I am having issues with it in virtualbox (12.10 really does suck no bones about it)
So I am in distribution hunt for him, I need something simple and easy to use, something fairly stable but also lightweight.
But I am taking out Ubuntu based distros out of the equation due to some major issues with Ubuntu right now with both 12.04 and 12.10 so I need something not based on the buntu family.

---

### Post by drawkcab on 2012-11-27
I would try Linux Mint Debian Edition with the xfce desktop.  It's signficantly lighter than Xubuntu in terms of the resources it requires and it is relatively easy to use for new users.  The bonus is that it's a rolling release.

The only trouble it would give someone in terms of ease of use is in terms of setting up connections with peripherals such as printers.  If you can help your father connect to his peripherals I think he would be pleased with LMDE.

---

### Post by snowpine on 2012-11-27
Hmmm, you say the computer is "old" (but don't give hardware specs) and has "major issues" with Ubuntu (but you don't say what those issues are). If you could clarify those two points, we could give you a much better recommendation.

Personally I am a Debian user, so in the absence of any details, that is my recommendation. :)

---

### Post by MadmanRB on 2012-11-27
Well I dont have the laptop on hand, all I can say is that its a 7 year old Toshiba Satellite with an old intel celeron CPU and 1 GB of RAM.
I cannot get the specs off my father as he doesnt know them, I am just looking for base recommendations.
And most of the issues he is having with Ubuntu is more from how the last two releases have been, both 12.04 and 12.10 have been very unstable for both me and my family with constant crashes even on good hardware like my top line self built computer.
With constant crashes and various bugs the 12 series of Ubuntu is not nearly as good as what it should be, this is mainly from the shift to unity as the other desktops have suffered under Ubuntu.
I am not going to ask how to problems solve these issues, I just want suggestions, thats all.
And no standard Debian will go over my fathers head, but Mint debian might be a good viable alternative for him

---

### Post by snowpine on 2012-11-27
> **MadmanRB said:**
> Well I dont have the laptop on hand, all I can say is that its a 7 year old Toshiba Satellite with an old intel celeron CPU and 1 GB of RAM.

Debian should fly on that, and has a lot fewer stability problems of Ubuntu in my experience. If you think your dad needs flash, codecs & stuff that "vanilla" Debian doesn't provide, then check out AntiX or CrunchBang, which are two of the nicer "lightweight debian derivatives" in my experience.

---

### Post by PhilGil on 2012-11-27
> **MadmanRB said:**
> And no standard Debian will go over my fathers head, but Mint debian might be a good viable alternative for him
Are you doing the install? If you are, Debian is no more challenging for an end user than any other variety of Linux. The Stable release is as close to faultless as any Linux distro gets, and still uses the familiar Gnome 2 desktop (although you can change to XFCE, if desired).

I would strongly recommend *against* a rolling release (like LMDE) unless you're going to be there to fix things when they go awry.

---

### Post by Bart_D on 2012-11-27
Well, if Ubuntu(-based) is out, then:

Debian
MacPup
Manjaro Linux XFCE version (is it based on Ubuntu???)
Zenwalk (XFCE)
Linux Mint Debian Edition (this might be a bit too heavy)

> **MadmanRB said:**
> ...Xubuntu 12.04...is not really working out for him.....

Why not?

---

### Post by MadmanRB on 2012-11-27
There are just loads of stability issues.
As for installing Debian, I honetly want something that is a bit faster to set up, its not like I cant install detain its just a slow tedious process and it would take me a while to set things up for him, I would want something that I can easily install and not take all day as debian can take hours to configure, plus it would help if something went wrong.

---

### Post by mamamia88 on 2012-11-27
> **MadmanRB said:**
> There are just loads of stability issues.
As for installing Debian, I honetly want something that is a bit faster to set up, its not like I cant install detain its just a slow tedious process and it would take me a while to set things up for him, I would want something that I can easily install and not take all day as debian can take hours to configure, plus it would help if something went wrong.

only thing that might take awhile to get working on debian would probably be the wireless card.   check if it's supported first.  otherwise it's basically an old version of ubuntu.  that's what i'd use for a relative.  I'd slap debian on it set up a cron job for automatcic updates and let them have it. maybe mint debian will be a quicker setup?

---

### Post by MadmanRB on 2012-11-28
Yeah he needs drivers for the wireless card, thus why debian is not that ideal.

---

### Post by ugm6hr on 2012-11-29
> **MadmanRB said:**
> But I am taking out Ubuntu based distros out of the equation due to some major issues with Ubuntu right now with both 12.04 and 12.10 so I need something not based on the buntu family.

What do you use? 

If you've moved away from Ubuntu-based, why not use whatever you use?

---

### Post by sudodus on 2012-11-29
> **MadmanRB said:**
> Well I dont have the laptop on hand, all I can say is that its a 7 year old Toshiba Satellite with an old intel celeron CPU and 1 GB of RAM.
I cannot get the specs off my father as he doesnt know them, I am just looking for base recommendations.
And most of the issues he is having with Ubuntu is more from how the last two releases have been, both 12.04 and 12.10 have been very unstable for both me and my family with constant crashes even on good hardware like my top line self built computer.
With constant crashes and various bugs the 12 series of Ubuntu is not nearly as good as what it should be, this is mainly from the shift to unity as the other desktops have suffered under Ubuntu.
I am not going to ask how to problems solve these issues, I just want suggestions, thats all.
And no standard Debian will go over my fathers head, but Mint debian might be a good viable alternative for him

I would suggest ***Linux Mint Mate 32-bit*** 

[[COLOR="SeaGreen"]http://www.linuxmint.com/edition.php?id=103[/COLOR]]("http://www.linuxmint.com/edition.php?id=103")

or ***Knoppix*** (originally for live sessions, but today you can install it as a debian release). The hardware detection is excellent.

(I might install Lubuntu 12.04 if it were my father, but I understand that you are not happy with this version of Ubuntu.)

---

### Post by MadmanRB on 2012-11-29
> **ugm6hr said:**
> What do you use? 

If you've moved away from Ubuntu-based, why not use whatever you use?

Due to his hardware mainly, I am currently using openSUSE 12.2 KDE and I am unsure if KDE will suit his machine.
Again there is gnome shell, but he tried it, he hates it.
Thus XFCE based distros are more or less preferred.

---

### Post by snowpine on 2012-11-29
> **MadmanRB said:**
> Yeah he needs drivers for the wireless card, thus why debian is not that ideal.

It's "penny wise and pound foolish" in my opinion to choose which distro to use on a daily basis for the next x years because you are avoiding a 5 minute procedure to install a wireless driver.

Assuming for the sake of argument that Debian will be rock-solid stable while Ubuntu has a bug that requires 1 hour of troubleshooting, you are getting a 12-fold return-on-investment for that 5 minutes you spent following the directions on Debian Wiki.

That's all I'll say about that so I don't come off as a Debian fanboy. :)

---

### Post by MadmanRB on 2012-11-29
well the fact that debian can take a long time even for a basic setup is what gets to me, I really do not have the time nor patience to install something like debian

---

### Post by snowpine on 2012-11-29
> **MadmanRB said:**
> well the fact that debian can take a long time even for a basic setup is what gets to me, I really do not have the time nor patience to install something like debian

I recommend Xubuntu LTS as an easier to install, less stable derivative of Debian Xfce.

---

### Post by MadmanRB on 2012-11-29
> **snowpine said:**
> I recommend Xubuntu LTS as an easier to install, less stable derivative of Debian Xfce.

That is what he is using, did you even read my first post?

---

### Post by snowpine on 2012-11-29
> **MadmanRB said:**
> That is what he is using, did you even read my first post?

And thus the conversation comes full circle.

---

### Post by ugm6hr on 2012-11-29
> **MadmanRB said:**
> Due to his hardware mainly, I am currently using openSUSE 12.2 KDE and I am unsure if KDE will suit his machine.
Again there is gnome shell, but he tried it, he hates it.
Thus XFCE based distros are more or less preferred.

How about just installing XFCE on OpenSUSE?
I have no experience with SUSE, but I presume that should be easy to achieve, and satisf your requirements.

It also means you will be able to easily advise on packages / applications available etc.

---

### Post by MadmanRB on 2012-11-29
Well it does have a DVD installer with XFCE, but I want more options before I decide.

---

### Post by PhilGil on 2012-11-29
> **MadmanRB said:**
> but I want more options before I decide.

[PCLinuxOS]("http://www.pclinuxos.com/") is a interesting distribution that isn't talked about much around here. It's been around for many years and has an active community. It was originally forked from Mandrake/Mandriva, but is not closely tied to that troubled project any more. Interestingly, it uses apt as it's package manager (a huge plus IMHO).

That being said, I agree with Snowpine that discarding Debian because of the setup is a mistake. It is possible to install Debian Squeeze from a live DVD or USB which makes it almost as fast and easy as an Ubuntu install. ISO's are available here: [http://live.debian.net/](http://live.debian.net/)

---

### Post by mythic97 on 2012-11-29
VM make everything look unstable because you don't have full power on mint if you got a spare USB with nothing on it uses it as a live USB and you will get a good representation of how well it works or try Lubuntu

---

### Post by MadmanRB on 2012-11-29
> **PhilGil said:**
> [PCLinuxOS]("http://www.pclinuxos.com/") is a interesting distribution that isn't talked about much around here. It's been around for many years and has an active community. It was originally forked from Mandrake/Mandriva, but is not closely tied to that troubled project any more. Interestingly, it uses apt as it's package manager (a huge plus IMHO).

No PClinux is out as you cant install non native packages in it without command line and they always dodge you asking about it on the forums over on the PClinux forums as he would want some apps that are not in the default repositories.
Trust me I used it, and hate the way they act over there

---

### Post by mamamia88 on 2012-11-29
All distros are easy to use from the end users perspective. Since you are setting it up for him give him the one that won't have him calling you all the time telling you something is broken.  For this reason I suggest Debian Stable.   Seriously it isn't hard to install and it's rock solid.   Only minor issue may be getting your wifi working and i most cases it's easy.  If you don't believe me try installing it in a vm for yourself. The installer may not be as pretty as Ubuntu but it's effective. Set up ssh so that you can update his machine for him on occasion and you'll never hear from him with problems hopefully.

---

### Post by sudodus on 2012-11-29
Please make it easier to suggest some distro/flavour: let us know what special programs your father needs on top of the standard selection(s)!

---

### Post by PhilGil on 2012-11-29
> **MadmanRB said:**
> No PClinux is out as you cant install non native packages in it without command line and they always dodge you asking about it on the forums over on the PClinux forums as he would want some apps that are not in the default repositories.
Trust me I used it, and hate the way they act over there
That's good to know for future reference. I've never used the distro but I do like reading their magazine.

---

### Post by mamamia88 on 2012-11-29
> **MadmanRB said:**
> No PClinux is out as you cant install non native packages in it without command line and they always dodge you asking about it on the forums over on the PClinux forums as he would want some apps that are not in the default repositories.
Trust me I used it, and hate the way they act over there

how about manjaro then?   based on arch so the aur is usable for packages outside official repos.  they should have a front end for yaourt but i haven't bothered looking.  that being said for a command line tool it's easy to use.

---

### Post by benerivo on 2012-11-29
SolusOS is an easy to use debian based distro. It uses a gnome desktop but is likely to be quite lightweight for an older computer. 
[http://solusos.com/about/](http://solusos.com/about/)

Sabayon is a gentoo based distro which comes in several desktop versions, and the xfce one might be best to try. The DVD comes with stacks of software with it.
[http://www.sabayon.org/release/press-release-sabayon-10](http://www.sabayon.org/release/press-release-sabayon-10)

Both are designed for home desktop use, and ready to use 'out of the box'.

---

### Post by andrew.46 on 2012-11-29
I have heard some excellent reports about [Salix]("http://www.salixos.org/wiki/index.php/Home") which has just had new versions released based on Slackware 14.0. Might be worth a look....

---

### Post by overcast on 2012-11-29
Lubuntu is much lightweight than xfce or mint. Also it can customized to look like XP and learning curve isn't steep. My suggestion, install lxde over XFCE and then see if he likes it.

---

### Post by MadmanRB on 2012-11-29
> **overcast said:**
> Lubuntu is much lightweight than xfce or mint. Also it can customized to look like XP and learning curve isn't steep. My suggestion, install lxde over XFCE and then see if he likes it.

Again I am trying to get away from buntu based distros.

---

### Post by BertN45 on 2012-11-29
> **MadmanRB said:**
> Okay heres the scoop, my father is working off an old laptop and is currently dual booting XP and Xubuntu 12.04, unfortunately xubuntu is not really working out for him.
I would try the latest Linux Mint on his machine but even I am having issues with it in virtualbox (12.10 really does suck no bones about it)
So I am in distribution hunt for him, I need something simple and easy to use, something fairly stable but also lightweight.
But I am taking out Ubuntu based distros out of the equation due to some major issues with Ubuntu right now with both 12.04 and 12.10 so I need something not based on the buntu family.

If you tell us why your father does not like Xubuntu, the advises would be more useful. If he dislikes it, because it is NOT Windows XP, give up all hope. I do not understand why you discard all Ubuntu distros, normally they run very good on 7 year old hardware. Besides they have 4 completely different desktops and the kernel is Linux and that is shared with all other distributions. Likewise XFCE and LXDE are shared by many distros.

The best wild guess would be Opensuse LXDE or XFCE versions, if you refuse to use the Ubuntu versions.

edit: If you give a Linux distro to a senior, you better look for a robust product, supported by a sound company, so the first two are Ubuntu (Canonical) or OpenSuse (Novell).

---

### Post by gnusci on 2012-11-29
This web site is one the best to read about distros

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by MadmanRB on 2012-11-29
> **BertN45 said:**
> If you tell us why your father does not like Xubuntu, the advises would be more useful. If he dislikes it, because it is NOT Windows XP, give up all hope. I do not understand why you discard all Ubuntu distros, normally they run very good on 7 year old hardware. Besides they have 4 completely different desktops and the kernel is Linux and that is shared with all other distributions. Likewise XFCE and LXDE are shared by many distros.

The best wild guess would be Opensuse LXDE or XFCE versions, if you refuse to use the Ubuntu versions.

edit: If you give a Linux distro to a senior, you better look for a robust product, supported by a sound company, so the first two are Ubuntu (Canonical) or OpenSuse (Novell).

Yes I know linux is not XP, he gets that too.
Look as I said Ubuntu seems to be very buggy even the alleged stable version 12.04.
I have had countless stability issues with it, its not a matter how well it runs fore you its how it runs for me and my family and my experience BOTH 12.04 AND 12.10 have casued me and my family nothing but grief.
So when I suggest not giving me Ubuntu based distros I mean it.

> **gnusci said:**
> This web site is one the best to read about distros

[http://distrowatch.com/](http://distrowatch.com/)

I know about distro watch
The problem with that is that there are literally thousands of linux distros/ flavors and all that the choose from.
The purpose of this topic was to filter that down.

---

### Post by BertN45 on 2012-11-30
> **MadmanRB said:**
> Yes I know linux is not XP, he gets that too.
Look as I said Ubuntu seems to be very buggy even the alleged stable version 12.04.
I have had countless stability issues with it, its not a matter how well it runs fore you its how it runs for me and my family and my experience BOTH 12.04 AND 12.10 have casued me and my family nothing but grief.
So when I suggest not giving me Ubuntu based distros I mean it.

As you probably know Ubuntu is based on Debian. Linux Mint is also based on Ubuntu and there is one Mint distro based on Debian directly.

What is left is OpenSuse 12, also a very nice and stable system not based on Ubuntu and not based on Debian. It has four flavours on one DVD; GNOME3; KDE; XFCE and LXDE. You could try GNOME3, but XFCE and LXDE will surely run on an older system.

---

### Post by viper250 on 2012-12-03
i know you are trying to avoid ubuntu versions but have you checked out pinguyos
there are 3 versions of it 10.04 11.04 and 12.04 (which i use)
these are very easy distros to install and configure and works very well
only issue you might have is wireless 
some systems used restricted drivers easily downloaded via ethernet.
dvd playback usually worked out of the box on any machine ive installed it in.

---

### Post by mamamia88 on 2012-12-03
> **viper250 said:**
> i know you are trying to avoid ubuntu versions but have you checked out pinguyos
there are 3 versions of it 10.04 11.04 and 12.04 (which i use)
these are very easy distros to install and configure and works very well
only issue you might have is wireless 
some systems used restricted drivers easily downloaded via ethernet.
dvd playback usually worked out of the box on any machine ive installed it in.
if he has problems with one ubuntu version distros based on ubuntu will probably have same problems for him.

---

### Post by viper250 on 2012-12-05
all i was saying is that pinguy is a quite a bit different than most flavors of ubuntu 
it reminds you more of mac os10 or osx
it uses ubuntu software repositories but it is more  Debian based
i have installed this os a lot for people and they were very pleased

then they might want to try dream linux
but they might have a problem with dvd playback

---

### Post by pissedoffdude on 2012-12-06
Give Fuduntu a try.  It's excellent with hardware detection and stability, and it comes with basically all the apps most people need (plus the infinality fonts pre-installed is awesome!).  It uses the last version of Gnome 2.X, so at least it's stable, and it should hopefully be pretty intuitive and user friendly, as it has a dock as well.

But it might be the case that he needs an XP-like gui to feel comfortable, so I'd say give LXDE on OpenSuse a try, or just tweak Fuduntu's Gnome to look like XP.

---

### Post by kazuya on 2012-12-06
There are numerous to choose from.
If no Ubuntu-based, below are some to choose for lightweight, and ease of use.
(1) Salix and Vectorlinux (slackware-based) but easy to use and quite fast, With 1GiG RAM, you need a light Desktop environment like LXDE, XFCE4, MATE. Openbox and enlightenment are even lighter but interface may not be as comfortable.

(2) Manjaro linux (xfce4 or lxde version) - Easiest implementation of Archlinux.
This is very very fast performing - Has a gui package manager.

(3) Sabayon (Use xfce4, mate, and/or lxde) - Very newbie friendly but fast performing as well compared to Ubuntu or Debian.

(4) Crunchbang (Debian-based) - Fast, but comes with openbox, you have to install xfce4 and/or lxde after install.

(5) For super minimalistic with potential to be fully functional for all your needs, bodhi linux, mepis antiX.

I hope this helped.

Suse is more bloated and less stable than even Ubuntu or its derivatives.

In your relative's Ubuntu or xubuntu install try installing preload and/or prelink; also in startup and sessions, disable blutooth services and others you do not use. This can greatly improve performance of machine.

---

### Post by JasonR on 2012-12-07
I don't know what he's using the distro for, but...I have my 70 year-old mother set up with the minimal desktop install of Scientific Linux 6.3.  It's a Red Hat clone that uses Gnome 2.  Not the latest software, but it's light on resources and very stable once I got it set up.  My goal was a distro with as little tech support from me as possible!  So far, so good.

---

### Post by fuduntu on 2012-12-07
> **JasonR said:**
> I don't know what he's using the distro for, but...I have my 70 year-old mother set up with the minimal desktop install of Scientific Linux 6.3.  It's a Red Hat clone that uses Gnome 2.  Not the latest software, but it's light on resources and very stable once I got it set up.  My goal was a distro with as little tech support from me as possible!  So far, so good.

Fuduntu: kernel 3.6, very recent software, and GNOME 2.  Also light on resources, and power friendly.

:popcorn:

---

### Post by addegsson on 2012-12-07
Linux Mint Debain Xfce, Manjaro Linux Xfce, Fuduntu (Gnome 2), Vector Linux and (my fav) Xubuntu 12.10. :D

---

### Post by JasonR on 2012-12-07
> **fuduntu said:**
> Fuduntu: kernel 3.6, very recent software, and GNOME 2.  Also light on resources, and power friendly.

:popcorn:
 Very interesting.  Haven't heard anything bad about this distro.

---

### Post by snowpine on 2012-12-07
> **JasonR said:**
> Very interesting.  Haven't heard anything bad about this distro.

My only minor criticisms are the "rolling release" updates and the lack of Gnome 3, but those fall into the category of "feature, not a bug" are not deal-breakers for me, therefore I happily use Fuduntu on my EEE netbook and recommend it to others. :)

---

### Post by JasonR on 2012-12-07
> **snowpine said:**
> My only minor criticisms are the **"rolling release" updates **and the lack of Gnome 3, but those fall into the category of "feature, not a bug" are not deal-breakers for me, therefore I happily use Fuduntu on my EEE netbook and recommend it to others. :)

Is a rolling release better for less sophisticated users, like my mother? I've got her SL set to auto update.  She won't go to the next major release, but I'm happy with the current edition, which is set for support thru (I think) 2017.

---

### Post by snowpine on 2012-12-07
> **JasonR said:**
> Is a rolling release better for less sophisticated users, like my mother? I've got her SL set to auto update.  She won't go to the next major release, but I'm happy with the current edition, which is set for support thru (I think) 2017.

I personally do not recommend rolling release for most users in most cases (although as I mentioned I do nevertheless use Fuduntu on 1 of my computers, because it is such a nice netbook distro). I like a nice stable system that is the same today as it was yesterday. An older user is less likely to view perfectly functional 2-3 year old software as "antiquated" in my opinion.

---

### Post by fuduntu on 2012-12-07
> **JasonR said:**
> Is a rolling release better for less sophisticated users, like my mother? I've got her SL set to auto update.  She won't go to the next major release, but I'm happy with the current edition, which is set for support thru (I think) 2017.

We have a pretty thorough QA process and try to only introduce stable updates.  We are in the business of providing a stable desktop, so we try to strive to achieve that using a waterfall development model.

---

