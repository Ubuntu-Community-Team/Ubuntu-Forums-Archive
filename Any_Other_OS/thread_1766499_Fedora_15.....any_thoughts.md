---
title: "Fedora 15.....any thoughts?"
date: 2011-05-24
forum: Any Other OS
---

### Post by dreamer3kx on 2011-05-24
Anyone runnung it, gnome 3 looks pretty neat but looks a bit much UI wise, will you be using it, Ubuntu is all I know so Im curious.

---

### Post by wolfen69 on 2011-05-24
I'm running it right now, and absolutely love it. I'm going to switch to it at least until ubuntu gets their act together. Don't get me wrong, I love ubuntu, but I have to go with what works for me. And right now for me, gnome3/shell is where it's at. 

But I'll keep an install of Xubuntu around just in case fedora breaks. But so far it's been a joy to use. Smooth and stable. (knock on wood)

But if you're thinking of trying it, it's not as noob friendly as ubuntu is, so keep that in mind.

---

### Post by Bart_D on 2011-05-24
> **wolfen69 said:**
> ....But if you're thinking of trying it, it's not as noob friendly as ubuntu is, so keep that in mind.

I am. Explain, with examples.

---

### Post by wolfen69 on 2011-05-24
> **Bart_D said:**
> I am. Explain, with examples.

Yes sir!

They don't hold your hand by offering you codecs and drivers, first off. Secondly, partitioning is a bit more advanced, or at least different enough that you might have trouble. So it pays to have good google skills. But if you have an extra hard drive laying around, unplug your main drive and give it a try.

I feel very at home with F15.  :popcorn:

---

### Post by satanselbow on 2011-05-24
Just grabbing it now as the latest round of updates to natty has broke my Gnome3 on Ubuntu :(

---

### Post by Bart_D on 2011-05-24
> **wolfen69 said:**
> ...They don't hold your hand by offering you codecs and drivers, first off. Secondly, partitioning is a bit more advanced, or at least different enough that you might have trouble. So it pays to have good google skills.....

Gosh, what a pain!

I don't mind the partitioning or the codecs(Flash is easy enough to install, and all I need). The drivers are the major problem. Ubuntu installs EVERYTHING automatically, as any "operating system"/distro should.

With all that in mind, I'll limit my try-out of Fedora15 to the LiveCD. I'll wait for Ubuntu to sugar-coat Gnome3 before trying it.....if that never happens, well, I've got better things to do than figure out how to install an Intel network driver.

---

### Post by shuttleworthwannabe on 2011-05-24
Yes, you will struggle to get nvidia and broadcom drivers setup from repo's--needs some tweaking and coding. 
If you want all in one solution with F14 base--try fuduntu--fast and a clean distro.

---

### Post by ilovelinux33467 on 2011-05-24
I am running the KDE version and I love it :popcorn:

---

### Post by boydrice on 2011-05-24
> **Bart_D said:**
> Gosh, what a pain!

I don't mind the partitioning or the codecs(Flash is easy enough to install, and all I need). The drivers are the major problem. Ubuntu installs EVERYTHING automatically, as any "operating system"/distro should.

With all that in mind, I'll limit my try-out of Fedora15 to the LiveCD. I'll wait for Ubuntu to sugar-coat Gnome3 before trying it.....if that never happens, well, I've got better things to do than figure out how to install an Intel network driver.

You won't have any troubles with intel drivers as those are included in the kernel.  I have a Intel 5100 wireless card and a Broadcom ethernet card and both work out of the box.  You might have some issues getting a proprietary NVIDIA or ATI driver working as Fedora won't ship with those.  Checkout RPMFusion for any non-free codecs/drivers and such.  It is very easy to enable.  Fedora isn't really that much more difficult than Ubuntu at least in my experiences.  I upgraded the RC 3 image last night and it has been very smooth.

---

### Post by TeoBigusGeekus on 2011-05-24
[Very useful article.]("http://cristalinux.blogspot.com/2011/05/how-to-painlessly-switch-from-ubuntu-to.html")

---

### Post by galacticaboy on 2011-05-24
The website says you need 512mb of ram to run it, I have just that and it will not install, it says that I need over 600mb of ram to install. And my graphics card does not support Gnome 3 so it reverts to fallback mode.

---

### Post by Simian Man on 2011-05-24
> **shuttleworthwannabe said:**
> Yes, you will struggle to get nvidia and broadcom drivers setup from repo's--needs some tweaking and coding. 
If you want all in one solution with F14 base--try fuduntu--fast and a clean distro.
If you install the Nvidia drivers, use [Leigh's guide]("http://www.fedoraforum.org/forum/showthread.php?t=261937").  He explains things well and answers questions if you have any.  Though the Nouveau drivers now support KDE desktop effects and all the games I run, so I am forgoing Nvidia drivers for the first time ever - for now at least :).  As for broadcom, just installing akmod-wl from RPM Fusion was enough for me.  Not as easy as Ubuntu's "Restricted Driver" program, or distros that come with them installed, but not insurmountable either.

> **ilovelinux33467 said:**
> I am running the KDE version and I love it :popcorn:
Me too!

I did have one little gotcha though.  I installed using a USB drive, then when I rebooted, my computer hung on booting.  I was worried that the new systemd didn't like my hardware or something...but it booted the live USB fine.  So I decided to boot off the USB again and re-install.  Only when I did it didn't boot the live version, but the installed version!  What happened was that I installed the bootloader onto the USB drive instead of the hard drive :P.

Other than that, everything is great.  KDE 4.6 is great as ever, the boot is fast, and as I said, the Nouveau drivers have had some great improvements since F14.

---

### Post by IWantFroyo on 2011-05-24
I'm going to download it right now! :)
I have high hopes for F15, after loving F14 so much...
I did have a kernel problem with the Beta...

PS- I made a thread on the same topic without seeing this one... Oops...

---

### Post by ilovelinux33467 on 2011-05-24
> **Simian Man said:**
> 
Other than that, everything is great.  KDE 4.6 is great as ever, the boot is fast, and as I said, the Nouveau drivers have had some great improvements since F14.

I agree everything is *so* good in Fedora 15

---

### Post by el_koraco on 2011-05-24
Might give the KDE spin a spin. Gnome Shell needs a few years before it becomes usable. 

Btw, Fedoristas, anybody using ATI cards with the OSS drivers? I'm curious as to how they behave in Fedora (temperature control is my main point of curiosity).

---

### Post by satanselbow on 2011-05-24
Ooh I feel even more naughty visiting here on F15 than I do on W7 :D

Compaq CQ-51 360SA has everything (HW ** edit tap to click is not on - but prob jus needs the synaptic stuff  ** ) up and running out of the box btw... but Ubuntu does that as well... it's the Gnome3 goodness that i'm more interested in... without the random ppa hacking too ;)

There has defo been some work on performance since theF15  betas me thinks - which is what turned me off initially... not delved into the depths of yum yet though... now I am scared...

---

### Post by ilovelinux33467 on 2011-05-24
> **el_koraco said:**
> Might give the KDE spin a spin. Gnome Shell needs a few years before it becomes usable. 

Btw, Fedoristas, anybody using ATI cards with the OSS drivers? I'm curious as to how they behave in Fedora (temperature control is my main point of curiosity).

I am currently using Fedora 15 with the open source ATi Driver (ATi Radeon HD4570 on my laptop). Laptop does get a little hot. However apart from that everything is fine and you do have the option of installing the fglrx driver.

---

### Post by shuttleworthwannabe on 2011-05-24
> **Simian Man said:**
> If you install the Nvidia drivers, use [Leigh's guide]("http://www.fedoraforum.org/forum/showthread.php?t=261937").  He explains things well and answers questions if you have any.  Though the Nouveau drivers now support KDE desktop effects and all the games I run, so I am forgoing Nvidia drivers for the first time ever - for now at least :).  As for broadcom, just installing akmod-wl from RPM Fusion was enough for me.  Not as easy as Ubuntu's "Restricted Driver" program, or distros that come with them installed, but not insurmountable either.

The whole point is to get going from the get go--I do not mind plugin in codes and down some terminal, but ye, Ubuntu jocky-gtk make life so much easier-

---

### Post by IWantFroyo on 2011-05-24
> **satanselbow said:**
> Ooh I feel even more naughty visiting here on F15 than I do on W7 :D


I haven't even used Ubuntu to go onto UbuntuForums for quite a while. :lolflag:

Don't need myself no Unity.

---

### Post by el_koraco on 2011-05-24
> **ilovelinux33467 said:**
> I am currently using Fedora 15 with the open source ATi Driver (ATi Radeon HD4570 on my laptop). Laptop does get a little hot. However apart from that everything is fine and you do have the option of installing the fglrx driver.

Yeah, i'd be using the OSS driver in ubuntu as well if it weren't for the searing heat. Guess i'll have to wait a year for radeon to get up to speed, or buy a laptop with an Intel card. I finally managed to find a correct combo of the Xserver and fglrx, which is horrible with the latest X, so no joy for me!

---

### Post by wolfen69 on 2011-05-24
> **el_koraco said:**
> Gnome Shell needs a few ***years*** before it becomes usable. 



That's obviously a matter of opinion. ***I*** find it *very* usable as is. Plus, there are many extensions available to make it like you want. Years? I don't think so. :rolleyes:

---

### Post by Spice Weasel on 2011-05-24
I have already got it installed on a laptop, but will have to wait for my backup to finish before I install it on my desktop. It's great, best Fedora release yet. There doesn't really seem to be much difference with the BETA (Isn't that a good thing? Shows all the bugs were fixed early on, unlike Ubuntu where they aren't fixed until after the release.) except for an annoying networking error that popped up on start up, but that was fixed a while ago.

I'm an Xfce spin user (but use FVWM as a desktop), so haven't really got an opinion regarding GNOME3. I tried it out for a few minutes in VirtualBox and it went to the fallback mode which seemed to be just a faster GNOME2 with different colour scheme and instead of right clicking to change the panels you do something else (ctrl+middle? I forget.)

---

### Post by wolfen69 on 2011-05-24
> **Spice Weasel said:**
> haven't really got an opinion regarding GNOME3.
Got an extra hard drive? It's the perfect way to try out new things. I feel naked if I don't have at least 3 HD's with 3 different installs at all times. To me, part of the fun of linux is trying out new things. Just install a 3D driver and give gnome shell a spin. You will want *gnome-tweak-tool* installed to change windows settings, fonts, etc. And with extensions, you can pretty much set it up similar to gnome 2 if that's your thing. 

I really don't know why people are up in arms over G3. You can tweak it like you want, so it shouldn't be a big deal. I think G3 is far ahead of where KDE4 was when *it* was first released. (G3 seems very stable at this early stage, which is a good sign) G3 has a ways to go before it is "finished", and will no doubt win people over in time. Considerably less time than kde took, that's for sure. It has already won *me* over. But hey, if you don't like it, don't use it. Gnome 2 will not be going anywhere soon if that's what you want, as there will be people that will keep it alive for a while. That's the beauty of linux. Choice. But that doesn't mean G3 is no good, just because it's not right for *you*.

Fedora has become my go-to OS for the time being, and will continue to be for the foreseeable future, provided it doesn't fubar constantly. It's running perfect *so far*, and makes me feel like a kid in a toy store playing with my shiny new toy. Don't you love it when you find something that suits you perfectly? Make no mistake though, I will always have an ubuntu install also, just to stay in the loop and monitor progress.

This is a time of growing pains of sorts for linux, but it is also very exciting. We can look forward to many years of good distro hopping. Gnome 3, Unity, and others will continue to bake in the oven a bit more and come out so juicy and tender it will make us very happy to be a linux user. Be patient, report bugs/develop, and just be happy we have so many choices now. No need for bashing. (not saying anyone did)

:guitar: :guitar: :guitar:

---

### Post by screaminj3sus on 2011-05-24
> **el_koraco said:**
> Might give the KDE spin a spin. Gnome Shell needs a few years before it becomes usable. 

Btw, Fedoristas, anybody using ATI cards with the OSS drivers? I'm curious as to how they behave in Fedora (temperature control is my main point of curiosity).

Its already more usable than unity IMO. Seems a lot faster and more polished.

---

### Post by wolfen69 on 2011-05-25
Oh, and it sucks that fedoraforums is only allowing help related posts at this time.  They say it a bandwidth issue. Really? I thought redhat was making money. Kind of weird they would temporarily disallow "testimonials" type posts.

---

### Post by boydrice on 2011-05-25
> **wolfen69 said:**
> Oh, and it sucks that fedoraforums is only allowing help related posts at this time.  They say it a bandwidth issue. Really? I thought redhat was making money. Kind of weird they would temporarily disallow "testimonials" type posts.

Well to be fair the forum isn't officially run by the project or Red Hat.  From the disclaimer at the bottom of the forum:
"FedoraForum.org is privately owned and is not directly sponsored by the Fedora Project or Red Hat, Inc. "

I actually think it is a great idea to focus on those that need help rather than clutter their forum with "Fedora Rocks" or "Fedora sucks" type posts while people are trying to install and troubleshoot.

---

### Post by wolfen69 on 2011-05-25
> **boydrice said:**
> 
I actually think it is a great idea to focus on those that need help rather than clutter their forum with "Fedora Rocks" or "Fedora sucks" type posts while people are trying to install and troubleshoot.

Well, I've been on fedoraforums for 4 years now, and it's not a "testimonials" kind of forum to begin with. The total # of posts they get in a day pale in comparison to ubuntu.  Most people that use fedora are experienced users, have been posting there for a while, and don't go just for post count. (you know who you are) I know it wouldn't be that much of a hit on their servers if they allowed a few testimonials.

But anyway, my feelings are irrelevant as they have made a decision to wait a while before the rant/rave sessions begin. No biggie, I just mentioned it.

---

### Post by wolfen69 on 2011-05-25
> **boydrice said:**
> Well to be fair the forum isn't officially run by the project or Red Hat.

Well, to be fair, ;) Ubuntuforums.org isn't officially run by Canonical either. Yet it can handle 1000's of people a day. Perhaps redhat and canonical *should* get more involved in the forums when possible. But what the heck do ***I*** know?

---

### Post by cbowman57 on 2011-05-25
> **satanselbow said:**
> Just grabbing it now as the latest round of updates to natty has broke my Gnome3 on Ubuntu :(

I just got it to successfully update. :)

Still my preference here.

---

### Post by cbowman57 on 2011-05-25
> **galacticaboy said:**
> The website says you need 512mb of ram to run it, I have just that and it will not install, it says that I need over 600mb of ram to install. And my graphics card does not support Gnome 3 so it reverts to fallback mode.

What graphics card are you using?

---

### Post by beew on 2011-05-25
One word. Crap. AT least at this point.

Natty is rock solid comparing to F15. It is the second time it dies on me and needs a reinstall. Before wireless didn't work, Fifefox froze every few minutes and needed a hard reboot and then the UI would just suddenly disappeared with a screenful of error messages. The broadcom wireless card still doesn't work with Fedora 14, yes, I mean 14! Meanwhile the same card on the same hp netbook works with 10.10 and 11.04 since alpha, all I did was to install via jockey.

Even though I have my share of complaint against Natty, I suddenly realize how spoiled I am. :)

---

### Post by shuttleworthwannabe on 2011-05-25
Ok guys here is what I did to get my broadcom wireless (Dell Vostro 3700, F15 64-bit) working in F15 (vanilla):
(1)in terminal do
```
su
yum update kernel*
reboot
```

(2) Boot into this new kernel (F15 Gold comes with a RC1 kernel)

(3) Add rpmfusion repo's (Link to rpm [non-free]("http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-rawhide.noarch.rpm"), and [free]("http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-rawhide.noarch.rpm"))--note these are for rawhide; change to f15 final in add/remove software>System>Software Source
Once you install this by double clicking the rpm files--it will do its thing of updating sources and adding the keys to the software centre

(4) In terminal do (note: this is for 64-bit)
```
su
yum install akmod-wl   
reboot
```
Watch the terminal for Y/N responses--I chose all Y.
(5) Broadcom wireless will work on reboot.

Hope this helps.

---

### Post by shuttleworthwannabe on 2011-05-25
and if you want to enable Flash Player in 64-bit follow [these]("http://fedoraproject.org/wiki/Flash#Checking_the_plugin") instructions (use at own risk btw).

And Gnome 3 Cheat Sheet [here]("https://live.gnome.org/GnomeShell/CheatSheet").

---

### Post by Spice Weasel on 2011-05-25
> **beew said:**
> One word. Crap. AT least at this point.

Natty is rock solid comparing to F15. It is the second time it dies on me and needs a reinstall. Before wireless didn't work, Fifefox froze every few minutes and needed a hard reboot and then the UI would just suddenly disappeared with a screenful of error messages. The broadcom wireless card still doesn't work with Fedora 14, yes, I mean 14! Meanwhile the same card on the same hp netbook works with 10.10 and 11.04 since alpha, all I did was to install via jockey.

Even though I have my share of complaint against Natty, I suddenly realize how spoiled I am. :)

In my opinion, Natty is terrible compared to F15. But that's me. \\:D/

Use what works for you.

---

### Post by ilovelinux33467 on 2011-05-25
> **spice weasel said:**
> in my opinion, natty is terrible compared to f15. But that's me. \\:d/

use what works for you.

+1

---

### Post by el_koraco on 2011-05-25
> **screaminj3sus said:**
> Its already more usable than unity IMO. Seems a lot faster and more polished.

i didn't say unity's not a train wreck.

---

### Post by tmette on 2011-05-25
I've gotten used to Natty and haven't had any crashes with 11.04.  With all this talk about Gnome3, which I really liked the looks of when watching some YouTube videos, I immediately want to go home and try out Fedora 15.

---

### Post by krapp on 2011-05-25
I think it's important to keep in mind that stability is less claimed by Fedora as a priority than by Ubuntu as comparisons between Unity and GNOME 3 continue to arise . . .

---

### Post by cbowman57 on 2011-05-25
> **tmette said:**
> I've gotten used to Natty and haven't had any crashes with 11.04.  With all this talk about Gnome3, which I really liked the looks of when watching some YouTube videos, I immediately want to go home and try out Fedora 15.

Why not just run Gnome 3.0 on Natty?

---

### Post by Simian Man on 2011-05-25
> **krapp said:**
> I think it's important to keep in mind that stability is less claimed by Fedora as a priority than by Ubuntu as comparisons between Unity and GNOME 3 continue to arise . . .

I didn't really care for either Gnome-Shell or Unity, but think Gnome-Shell is more stable.  Though Unity probably has more features at the moment (mostly thanks to Compiz).

---

### Post by Allavona on 2011-05-25
Running Gnome3 on Xubuntu and absolutely love it. 

But F15 has Gnome3 by default, and because it's integrated in the OS, I had to try it. I found it to be functional and speedy. Didn't have any issues with hardware working and it took a little bit of time to get all my codecs, plugins, Java, etc...but once said and done, all is well.
Gnome-tweak-tool is a must, as are some of the shell-extentions. For those used to Ubuntu Software Center, the add/remove software will take some getting used to.
And after "sudo" and "apt-get" for many moons, it's now "su" and "yum!!"

I would recommend F15 to moderately experienced users because, as stated in earlier posts, it is a bit more advanced, with different commands and such. But totally worth exploring.

RPM hell...Here I come!!

---

### Post by Simian Man on 2011-05-25
> **Allavona said:**
> And after "sudo" and "apt-get" for many moons, it's now "su" and "yum!!"

You can easily setup sudo in Fedora, in fact the installer now offers to do it for you.

---

### Post by wolfen69 on 2011-05-25
> **Allavona said:**
> Running Gnome3 on Xubuntu and absolutely love it. 


Mark my words that if you update it, IT WILL BREAK! Don't say you weren't warned. Go ahead and update it, I dare you. ;)

---

### Post by cbowman57 on 2011-05-25
> **wolfen69 said:**
> Mark my words that if you update it, IT WILL BREAK! Don't say you weren't warned. Go ahead and update it, I dare you. ;)

It is possible to maintain a working G3 on Natty without breaking anything, but it requires running some extra ppa's.  :)

I've been up & running with multiple updates for about 3 weeks now.

---

### Post by wolfen69 on 2011-05-25
> **cbowman57 said:**
> It is possible to maintain a working G3 on Natty without breaking anything, but it requires running some extra ppa's.  :)

I've been up & running with multiple updates for about 3 weeks now.

I gave up with that mess. I just waited for F15 to come out. I'd rather use native G3.

---

### Post by krapp on 2011-05-25
> **Simian Man said:**
> I didn't really care for either Gnome-Shell or Unity, but think Gnome-Shell is more stable.  Though Unity probably has more features at the moment (mostly thanks to Compiz).

I just mean to say that whoever accuses Fedora of being less stable than Ubuntu isn't scoring that many points. For the sake of Ubuntu let's hope Fedora is less stable than Ubuntu, because this is how it should be.

---

### Post by Bart_D on 2011-05-25
THREE Questions:

1.Is there a way to change the screensaver,icons and wallpaper in Fedora's implementation of Gnome 3?

2. Has anyone tried Oracle Virtual Box? Does it work as well as it does in Ubuntu 11.04?

3. Is there a way to automatically log-in? When shutting down/restarting the PC, do you HAVE to log-out first or can you somehow shutdown/restart directly WITHOUT having to logout first?

---

### Post by wolfen69 on 2011-05-25
> **Bart_D said:**
> THREE Questions:

1.Is there a way to change the screensaver,icons and wallpaper in Fedora's implementation of Gnome 3?
Yes, with *System Settings* and *Gnome Tweak Tool*.

> **Bart_D said:**
> 2. Has anyone tried Oracle Virtual Box? Does it work as well as it does in Ubuntu 11.04?
I'm about to try it, but there shouldn't be any problems.

> **Bart_D said:**
> 3. Is there a way to automatically log-in? 
*System Settings*>*User accounts*
> **Bart_D said:**
> When shutting down/restarting the PC, do you HAVE to log-out first or can you somehow shutdown/restart directly WITHOUT having to logout first?
Yes. Just hit the *Alt* key and *Suspend* changes to *Power Off*.

---

### Post by Bart_D on 2011-05-25
Do update us on Virtual Box. That is CRUCIAL for me.

> **wolfen69 said:**
> Yes, with *System Settings* and *Gnome Tweak Tool*.....

System Settings? Where? I don't see an option/options. Could you give some more details?

Also, how do you actually install Gnome Tweak? I searched in the "Add/Remove Software" option and it just listed about 500 items with "Gnome" in it. No option to install Gnome Tweak, or an indication as to whether it was already installed.

---

### Post by wolfen69 on 2011-05-25
> **Bart_D said:**
> Do update us on Virtual Box. That is CRUCIAL for me.



System Settings? Where? I don't see an option/options. Could you give some more details?

Also, how do you actually install Gnome Tweak? I searched in the "Add/Remove Software" option and it just listed about 500 items with "Gnome" in it. No option to install Gnome Tweak, or an indication as to whether it was already installed.

Are you using gnome shell, or the fallback mode?

---

### Post by Bart_D on 2011-05-25
> **wolfen69 said:**
> Are you using gnome shell, or the fallback mode?

I just installed Fedora and am new to it. I'm just using the default session...it looks like Gnome 3. Sorry I can't give more details...I'm just really not sure.

---

### Post by wolfen69 on 2011-05-25
> **Bart_D said:**
> I just installed Fedora and am new to it. I'm just using the default session...it looks like Gnome 3. Sorry I can't give more details...I'm just really not sure.

You need to install 3D video drivers to get the gnome shell. I'm not familiar with fallback mode. (which is what you're in)

---

### Post by Bart_D on 2011-05-25
Ok.

One last thing, how do you install/activate RPMFusion?

---

### Post by wolfen69 on 2011-05-25
> **Bart_D said:**
> Ok.

One last thing, how do you install/activate RPMFusion?

[http://rpmfusion.org/Configuration](http://rpmfusion.org/Configuration)

I'm about to try Vbox, and I'll post back in a bit.

---

### Post by Bart_D on 2011-05-25
^^^^Thanks man. Thanks a lot.

---

### Post by wolfen69 on 2011-05-25
As I thought it would, vbox works perfect. Installed 11.04 unity to play around with.

---

### Post by Bart_D on 2011-05-25
That does sound promising.

Regarding installation of 3D drivers(Intel), is there a way to install them after activating RPMFusion? Is RPMFusion even required or can it be done with installing it?

---

### Post by wolfen69 on 2011-05-25
> **Bart_D said:**
> That does sound promising.

Regarding installation of 3D drivers(Intel), is there a way to install them after activating RPMFusion? Is RPMFusion even required or can it be done with installing it?

I've never used Intel video, but I thought they were installed automatically. Perhaps you should join [http://forums.fedoraforum.org/?](http://forums.fedoraforum.org/?) and ask there.

---

### Post by Bart_D on 2011-05-26
Well, I had a look at Gnome Tweak:
[http://www.youtube.com/watch?v=MQIvEBilnRc&feature=related](http://www.youtube.com/watch?v=MQIvEBilnRc&feature=related)

Frankly, it seems pretty useless unless you want to COMPLETELY change your Gnome 3 Shell experience. I thought it would help me to change icons...it doesn't. I NEVER used Ubuntu Tweak and, based on what I've seen, I won't be using Gnome Tweak either.

Anyways, as far as Fedora goes, I will reserve judgment until I have installed Virtual Box tomorrow.

So far, it(Fedora) won't allow me to enter the IP address of a network printer....this was done in a few simple steps in Ubuntu. Fedora(probably a Gnome3 problem) just sits there and does nothing, unable to detect ANY network printers and unable to allow the user to specify anything.

Other than that, I would say that it is a good think that they left out ALL office producitvity applications. For those of use who rely on Virtual Box for this, it saves a lot of space and memory. No wonder the Fedora Live CD is only ~550 MB.

It appears to be a very lean distribution.....even Xubuntu isn't that small!

Anyways, will test Virtual Box tomorrow and THAT will make or brake my Fedora experience.

---

### Post by cbowman57 on 2011-05-26
> **wolfen69 said:**
> I gave up with that mess. I just waited for F15 to come out. I'd rather use native G3.

No problem, that's your choice.

---

### Post by boydrice on 2011-05-26
> **Bart_D said:**
> That does sound promising.

Regarding installation of 3D drivers(Intel), is there a way to install them after activating RPMFusion? Is RPMFusion even required or can it be done with installing it?

Not sure which Intel chipset you have but all I thought all Intel drivers were already in the mainline kernel.

---

### Post by Bart_D on 2011-05-26
Yeah, I should clarified that.

Anyways, it turns out I am running Gnome3 Shell. I saw what it is supposed to look like(YT video) and what the fallback mode should look like(again, YT video) and, well, I'm not running the fallback mode. Drivers were automatically installed.

This is not a problem.

---

### Post by Spice Weasel on 2011-05-26
Finally upgraded my desktop... Holy crap all of the minor annoyances from F14 are gone, and lovely new features too!

Now... Time to upgrade to Rawhide. Let the breakage begin. :lolflag:

---

### Post by wolfen69 on 2011-05-26
> **Bart_D said:**
> Yeah, I should clarified that.

Anyways, it turns out I am running Gnome3 Shell. I saw what it is supposed to look like(YT video) and what the fallback mode should look like(again, YT video) and, well, I'm not running the fallback mode. Drivers were automatically installed.

This is not a problem.

How do you like it?

---

### Post by wolfen69 on 2011-05-26
> **Spice Weasel said:**
> Let the breakage begin. :lolflag:

It's been rock solid for me. Let's hope it stays that way. :popcorn:

I may switch back to ubuntu when gnome 3 is supported, but I can always have ubuntu in Vbox to keep up on what's going on. I like to help people when I can.

---

### Post by Bart_D on 2011-05-27
> **wolfen69 said:**
> How do you like it?

Well, I've had a chance to try it out on 2 machines - both supported the Gnome 3 Shell mode.

Observations:

1. When you open up the file manager to, say, Documents, and you then want to open up Downloads, it opens in the same window.i.e. you don't get 2 windows coming up-one for Downloads and the other for Documents. Not sure if this was the case with Unity.

2. RAM usage is shockingly low, yet it just doesn't feel as snappay as you would think. I've tried this on both an older and a newer machine.....when I open up System Monitor, for example, after I click X to close it, the window actually does not close for a good 1.5 seconds. With Ubuntu(Unity), this is instantaneous. I've noticed this with a few other applications as well, in Fedora.

I think that 1 and 2 are possibly because Gnome 3 is not as user-friendly as Unity, rather than Fedora-specific issues.

3. ALL window managers seem wasteful....the name, let us say "Ubuntu Forums - Reply to Topic - Mozilla Firefox" will appear on one line and then a WHOLE separate line is required, just below this, for the menus. In Virtual box, valuable resolution is lost because of this. Can't remember if this was the case in Ubuntu(Unity)....although I highly doubt it.

Jury is still out on Virtualbox......I had a nightmare installing it and had to do some real goofing around in terminal. Still can't get USB support for the guest OS. More time needed here.....which I find a bit disappoinging.

4. This is a Gnome 3 problem, I think. I uninstalled Orca, which was the only entry in the Universal Access category of Applications. Restarted the PC. Guess what.....Universal Access remained as an application category with no entries. I would have wanted it to disappear.

OVERALL USABILITY:
Visual Effects: Gnome 3 > Unity
Usability: Unity > Gnome 3

Points 1,2 and 4 above are minor. I'm still working on point 3(should not have taken this long to get VBox up and running) and it WILL influence my opinion greatly.

---

### Post by wolfen69 on 2011-05-28
> **Bart_D said:**
> Well, I've had a chance to try it out on 2 machines - both supported the Gnome 3 Shell mode.

Observations:

1. When you open up the file manager to, say, Documents, and you then want to open up Downloads, it opens in the same window.i.e. you don't get 2 windows coming up-one for Downloads and the other for Documents. Not sure if this was the case with Unity.

2. RAM usage is shockingly low, yet it just doesn't feel as snappay as you would think. I've tried this on both an older and a newer machine.....when I open up System Monitor, for example, after I click X to close it, the window actually does not close for a good 1.5 seconds. With Ubuntu(Unity), this is instantaneous. I've noticed this with a few other applications as well, in Fedora.

I think that 1 and 2 are possibly because Gnome 3 is not as user-friendly as Unity, rather than Fedora-specific issues.

3. ALL window managers seem wasteful....the name, let us say "Ubuntu Forums - Reply to Topic - Mozilla Firefox" will appear on one line and then a WHOLE separate line is required, just below this, for the menus. In Virtual box, valuable resolution is lost because of this. Can't remember if this was the case in Ubuntu(Unity)....although I highly doubt it.

Jury is still out on Virtualbox......I had a nightmare installing it and had to do some real goofing around in terminal. Still can't get USB support for the guest OS. More time needed here.....which I find a bit disappoinging.

4. This is a Gnome 3 problem, I think. I uninstalled Orca, which was the only entry in the Universal Access category of Applications. Restarted the PC. Guess what.....Universal Access remained as an application category with no entries. I would have wanted it to disappear.

OVERALL USABILITY:
Visual Effects: Gnome 3 > Unity
Usability: Unity > Gnome 3

Points 1,2 and 4 above are minor. I'm still working on point 3(should not have taken this long to get VBox up and running) and it WILL influence my opinion greatly.

Sorry to hear that. I havn't had any of those problems, but then again I'm not a noob and can do this stuff in my sleep. 

F15+G3=win (for me)

But hey, if it doesn't suit you, that's OK. There's a lot of choices out there in linuxland. Good luck.

---

### Post by DJWK on 2011-05-28
Running Fedora 15 right now, and its terrible. I don't like GNOME 3 at all. It feels too much 'touchscreen' and doesn't really work that great with dual head. Looks great though.

Now downloading Ubuntu, i'm coming home :)

---

### Post by satanselbow on 2011-05-28
Up until a few days ago I was quite happy hacking G3 onto Natty... then a particularly vicious round of updates inflicted enough breakage for me not to be bothered fixing it and clean reinstalll... then realised I actually need to get some work done and can't be bothered to deal with all the messing about currently required to get a (cough) "stable"  G3 running on Nutty or OO...

OpenSuse makes my skin crawl... can't actually remember why but it brings me out in hives :( so F15 it is. 

Apart from a minor(ish) battle with LAMP virtualhosts (largely typos on my part and interference from SELinux) I can't fault it :D

I don't want or need massive amounts of tweaks - jus the theme changer + gnome-tweak-tool + Dconf covers it for me... the fed forums are a bit "Suit n Tie" for me so will probably still hang out here and play with OO / G3 when I get the time ;)

Nutty (both general stability and the ironically named "Unity" - which seems to have divided the Ubu community like nothing before) has left a bit of a bad taste in the mouth for me. Official Gnome3 support has got to be considered essential now surely... without it I'm thinking Ubu will lose ground and credibility as an alternative OS increasingly rapidly :( ... IMHO...

---

### Post by Starlight on 2011-05-28
I've replaced Kubuntu with Fedora 15 recently so that I could use Gnome 3. :) So far, I think it's a really nice system, but the most annoying thing is rather poor software availability for it :( The latest available version of Kadu (a client for the most popular IM network in Poland) is horribly old, Clipgrab (a nice youtube downloader that I used on Kubuntu) seems to have no Fedora package at all... :( All this is very weird, since Distrowatch says that Fedora is one of the most popular distros.

---

### Post by BigSilly on 2011-05-28
> **satanselbow said:**
> 
OpenSuse makes my skin crawl... can't actually remember why but it brings me out in hives

That's a real shame. I'm really enjoying it at the mo. It's aces with Gnome 3. :)

It's kinda sad reading opinions on Gnome 3 around the net. Lots of people have really got the willies with the change, and I don't think it's justified personally. It's thought of as primarily designed for touchscreens, but I think the design is just as elegant on larger desktop screens with traditional controls. I certainly don't feel any screen real estate is wasted. I seem to have much more room, if anything, and it's so easy to get around.

I've mentioned elsewhere that I love Unity. It's really brilliant. But I think Gnome 3 is just a nicer place to be, and is a fantastic design for *any* device, where Unity really does feel a little out of place and slightly awkward on a desktop screen. Just imho.

---

### Post by satanselbow on 2011-05-28
> **Starlight said:**
> but the most annoying thing is rather poor software availability for it :( The latest available version of Kadu (a client for the most popular IM network in Poland) is horribly old

Have you enabled to rpmFusion repos? There is a lot of more current software versions and numerous apps not in the official repos to be found ;)

Their may be rpm's available on the apps own website, you could build from source and try "alien" ... results may vary ;)

---

### Post by Starlight on 2011-05-28
> **satanselbow said:**
> Have you enabled to rpmFusion repos? There is a lot of more current software versions and numerous apps not in the official repos to be found ;)

Their may be rpm's available on the apps own website, you could build from source and try "alien" ... results may vary ;)

Hi! I've tried searching for it anywhere, and there are no rpms available for Fedora 15. What's weird, in Fedora 14's official repos there's a newer version of Kadu than for F15. There's nothing on the app's website as well. If you look here: [http://www.kadu.net/w/English:Download](http://www.kadu.net/w/English:Download) there are versions available for many different OSes, even very obscure ones, but nothing for Fedora.

I thought about compiling, but there's no Checkinstall for Fedora too, and I don't want to make a huge mess out of my system by installing stuff outside the package manager...

---

### Post by ratcheer on 2011-05-28
> **TeoBigusGeekus said:**
> [Very useful article.]("http://cristalinux.blogspot.com/2011/05/how-to-painlessly-switch-from-ubuntu-to.html")

Yes, thanks very much. I have bookmarked it.

Tim

---

### Post by satanselbow on 2011-05-28
> **Starlight said:**
> 
but there's no Checkinstall for Fedora too, and I don't want to make a huge mess out of my system by installing stuff outside the package manager...

There are openSuse rpm's here:

[http://download.opensuse.org/repositories/openSUSE:/11.4:/Contrib/standard/i586/](http://download.opensuse.org/repositories/openSUSE:/11.4:/Contrib/standard/i586/)

Might be worth a whirl - depends how bad you need it ;)

---

### Post by Starlight on 2011-05-28
> **satanselbow said:**
> There are openSuse rpm's here:

[http://download.opensuse.org/repositories/openSUSE:/11.4:/Contrib/standard/i586/](http://download.opensuse.org/repositories/openSUSE:/11.4:/Contrib/standard/i586/)

Might be worth a whirl - depends how bad you need it ;)

Thanks! I actually found someone suggesting on one forum that Fedora 14 rpms can be installed on Fedora 15 so I did that, and it works :) It's still a little older version (0.9.0, and in openSUSE it's 0.9.2) but it seems kind of unsafe to install packages made for another distro :O

And I've noticed that openSUSE has a lot more other stuff for Kadu... I wonder where the difference in software availability comes from. Distrowatch says that Fedora is more popular o_O

---

### Post by spkr322 on 2011-05-28
i have installed it and it is good to look how about the software collection

---

### Post by Minox on 2011-05-28
I really like Fedora 15.
I've never used Fedora before, but I thought I'd give it a shot. I think it might become my primary OS.

---

### Post by SoFl W on 2011-05-28
> **TeoBigusGeekus said:**
> [Very useful article.]("http://cristalinux.blogspot.com/2011/05/how-to-painlessly-switch-from-ubuntu-to.html")


Thanks, I was actually Tri-booting (Win/Ubuntu/Fedora 13) a while back.  I liked Fedora but Ubuntu and this community was much nicer.  I tried Fedora-XFCE in a virtual machine, I think I will also give Fedora Gnome another try.

Because of the people here, I am not sure I want to make a more serious switch than a virtual machine.

---

### Post by nm_geo on 2011-05-28
I installed it yesterday and have been hackin' and tweakin'.  The lack of a shutdown button was weird to me.. You can hit alt and the suspend button turns to power down.  Well I found a way to get the power button installed and it stayed until an update today broke it again.. seesch

I really did not like the not having the min, max buttons so loaded up Gnome Tweak Tool solved that one too.

Resized the borders on open windows where i could grab them easier and changed their default sizes. oh yeah I added color to the title bars those plain neutral bars disturb me.

The Icons (under applications) were too large so I down-sized them as well.  

Let's see I changed the theme.. That was an experience but it all appears to work now.  Oh yeah I changed the default background that blue bird was not cool. 

Fedora claims to be more cutting edge than other distros and I would say yeah they are more than Ubuntu. If you want a production machine stay with Ubuntu 10.04 LTS.  If you want to play with Gnome 3 try Fedora 15 out.  By the way it sounds like Oneiric will have Gnome 3 installed along with Unity hmmmm.. more to hack :P

Let see a good site for tweaking Fedora 15
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

Will add a screenshot when I reconnect with Fedora 15.

That's about it for now OVER & OUT

---

### Post by RedLeg217 on 2011-05-28
I fooled around with Fedora 15 and decided I liked GNOME 3 far less than Unity.

---

### Post by nm_geo on 2011-05-28
> **Starlight said:**
> Thanks! I actually found someone suggesting on one forum that Fedora 14 rpms can be installed on Fedora 15 so I did that, and it works :) It's still a little older version (0.9.0, and in openSUSE it's 0.9.2) but it seems kind of unsafe to install packages made for another distro :O

And I've noticed that openSUSE has a lot more other stuff for Kadu... I wonder where the difference in software availability comes from. Distrowatch says that Fedora is more popular o_O

The RPM fusions are out as of today.  See Screenshot.

---

### Post by Bart_D on 2011-05-29
> **wolfen69 said:**
> Sorry to hear that. I havn't had any of those problems, but then again I'm not a noob and can do this stuff in my sleep. 

F15+G3=win (for me)

But hey, if it doesn't suit you, that's OK. There's a lot of choices out there in linuxland. Good luck.

I'm actually 99% certain I will be moving to Fedora for now....will be sorting out the VBox thing though.

I hate the fact that I will be ditching Ubuntu, but I may go back if Unity becomes comparable to Gnome 3.

So, what did it for me? You guessed it....Gnome3.

---

### Post by Darren Sparrow on 2011-05-29
I thought I'd give Fedora 15 a go, but I couldn't even boot the disk on my pc, it kept running around in circles! So I tried it on a couple of friends pc's. One has a fairly new machine, and fedora liked that one and loaded up ok. Can't say i'm impressed with Gnome 3 really, it's not very intuitive, and once we let a Windows user at it, we new that if Gnome3 was going to be flagship for new linux users then it would fail. They found Mint, Ubuntu, Debian etc to be much easier to use, and the opinion was that Gnome3 would not convert anyone to Linux. 

We also tried Fedora on another friends pc that is several years old, and again it didn't wish to load correctly. I remember problems with previous fedora's such as 13 which made my mouse pointer stay in the top left hand corner. 

So, it would seem that Ubuntu, Mint, Debian, and other distros that don't use Gnome3 as their main will see more uptake by new users, whereas if you're prepared to persevere then I guess Gnome3 is for you. I'll probably just fork the Gnome2 myself and use that or unity.

---

### Post by BigSilly on 2011-05-29
> **nm_geo said:**
> I installed it yesterday and have been hackin' and tweakin'.  The lack of a shutdown button was weird to me.. You can hit alt and the suspend button turns to power down.  Well I found a way to get the power button installed and it stayed until an update today broke it again.. seesch

I dunno about Fedora, but there is actually a small Gnome shell extension for that, which I got from the Opensuse repo. My menu permanently shows power off now as it should. I'll be amazed if Fedora doesn't have it too.

> **nm_geo said:**
> I really did not like the not having the min, max buttons so loaded up Gnome Tweak Tool solved that one too.

So does Fedora come with added buttons on the window then or am I reading you wrong? I agree that you don't need or want them. Once you have used Gnome 3 a while, you understand what the design team behind it was getting at when they said they just confuse matters. Both minimise and maximise are completely redundant on Gnome 3 and I haven't missed them personally. At all.

> **nm_geo said:**
> The Icons (under applications) were too large so I down-sized them as well.

That's a great idea, as the default is rather large. I didn't imagine you could change that at this early stage in Gnome 3's life, but if you can do it I'll look into it. Hopefully as time goes on desktop distros will begin to customise Gnome 3 like this so they can differentiate a bit.

> **nm_geo said:**
> By the way it sounds like Oneiric will have Gnome 3 installed along with Unity hmmmm.. more to hack :P

Yes I've heard that Gnome 3 will come with 11.10 one way or another. I think this is a really Good Thing and I'll definitely be back to try it when it appears. :)

---

### Post by Starlight on 2011-05-29
> **nm_geo said:**
> The RPM fusions are out as of today.  See Screenshot.

Thanks! But there's no Kadu in RPM Fusion o_O At least I can't find it there...

---

### Post by ojdon on 2011-05-29
The only thing that is stopping me from using Fedora 15 is that florence doesn't seem to work for me anymore. It never worked in any of the Fedora 15 builds including the final version. Something to do with at_spi_registry refuses to start. 

I'm currently using Ubuntu + Gnome-Shell + Custom Kernel (13 seconds to GDM) :D 

The only problem I have left is that GDM refuses to automatically login even though I have it enabled. :S So I tried following [this guide]("http://florence.sourceforge.net/english/tips.html#gdm") to get Florence the Virtual Keyboard working but it can't find any of the files that need editing. :( 

Once [Maliit]("http://www.jonnor.com/2011/04/introducing-maliit-on-screen-keyboard-in-gnome-3/") gets released on Fedora I'd probably make the jump! :)

---

### Post by krapp on 2011-05-29
Sad to see so many ditching the .deb universe altogether! Why not give Debian a shot?

---

### Post by nm_geo on 2011-05-29
> So does Fedora come with added buttons on the window then or am I  reading you wrong? I agree that you don't need or want them. Once you  have used Gnome 3 a while, you understand what the design team behind it  was getting at when they said they just confuse matters. Both minimise  and maximise are completely redundant on Gnome 3 and I haven't missed  them personally. At all.Sorry if i confused you.  Fedora 15 does not come with min, max buttons on windows just the Close button.  I understand you really don't need them in Gnome 3, but there are just things that make me feel better and I want them. :P

---

### Post by BigSilly on 2011-05-29
> **nm_geo said:**
> Sorry if i confused you.  Fedora 15 does not come with min, max buttons on windows just the Close button.  I understand you really don't need them in Gnome 3, but there are just things that make me feel better and I want them. :P

:D

That's fine. Just remember it won't be long before you realise that you aren't even using them. :p  ;)

---

### Post by wolfen69 on 2011-05-29
> **Starlight said:**
> I've replaced Kubuntu with Fedora 15 recently so that I could use Gnome 3. :) So far, I think it's a really nice system, but the most annoying thing is rather poor software availability for it :( The latest available version of Kadu (a client for the most popular IM network in Poland) is horribly old, Clipgrab (a nice youtube downloader that I used on Kubuntu) seems to have no Fedora package at all... :( All this is very weird, since Distrowatch says that Fedora is one of the most popular distros.

I doubt most people will stay away from Fedora just because Kadu is old, and Clipgrab is not available. ;)   I've never even heard of them. Actually, most of fedora's packages are the very latest.

---

### Post by 23dornot23d on 2011-05-29
Interesting with Fedora 15 .....

I downloaded it and tried to install it and it needs a minimum of 640 Meg memory

Now this is the first time I have seen a restriction like this .....

Maybe its telling me its time to upgrade my desktop computer ...

Running it from the live CD though .... it does work - but does not include the themes on the second screen.

( I will load it on my laptop at some point  .... as that has more memory ..... to test it out )

**Interesting that its gone for Gnome-Shell ...... and if they ever get the video problems sorted with gtk-record my desktop ....... then it may become more of a useful tool to me. **

---

### Post by NormanFLinux on 2011-05-29
If your computer does not have an accelerated graphics card, you can install Fedora in a "fall-back" environment minus the GNOME Shell, which unfortunately, was compiled only to run in a 3D environment.

---

### Post by sffvba[e0rt on 2011-05-30
Review of Fedora 15... note Brian doesn't like Fedora... but many of the points raised are valid...

[http://www.jupiterbroadcasting.com/8881/fedora-15-review-las-s17e01/](http://www.jupiterbroadcasting.com/8881/fedora-15-review-las-s17e01/)



404

---

### Post by jramshu on 2011-05-30
OK. I have a 64 bit amd and plenty of room so I decided to give Fedora 15 x86_64 a shot. 

First off it took over grub and failed to list Ubuntu, easy fix.
Then went to install nvidia 8200 drivers, crash. 
Couldn't get it to blacklist the nouveau drivers, probably just me.

I like the look of Gnome 3 but....if they are trying to get more users to *nix,IMHO, Fedora is not the best distro to get new users. It's not that it's too complicated, just not newbie friendly. Switching over and adjusting myself to yum and all, not a big issue, though I still found myself trying to use Ubuntu specific commands. LOL!!

I will still be recommending to everyone I know who is interested in switching from windows that Ubuntu is the way to go, or Linux Mint. I will probably suggest 10.04 LTS for now.

---

### Post by FormatSeize on 2011-05-31
I don't like Fedora 15. I've tried it, but it's pretty terrible. (I think I have Alpha). Fedora 14 is fantasic, though.

---

### Post by Bart_D on 2011-06-02
Okay. I've had a week or so with Fedora 15.

To a new user of Linux, it feels incomplete and very confusing.

BAD: Software Update is an application menu item....Software Updates is another item. Huh? Are you kidding me? Coming from Ubuntu, I was laughing at that! I had to guess. And I guessed wrong.

VERY BAD: Network printing does NOT work in Gnome 3. Fedora can't print to a network printer unless you try CUPS.....this was NOT required in Ubuntu.

AWFUL: Try this. Log in, use several apps, then switch user. You will find that, sooner rather than later, after you log back in the desktop will freeze rendering itself **useless**.

GOOD: Wireless was automatically picked up. Graphics drivers(Intel) were automatically picked up....which is more than what I can say about Arch Linux, or as I call it,Farse Linux.

To someone who is not afraid of the terminal, not necessarily a terminal expert, this Fedora 15 will be good and meet their needs.

The Fedora website is horrible and has screenshots from a MUCH older version of Fedora! Ubuntu.com would NEVER do that! Red Hat seems uninterested in the desktop.

I am shocked that Fedora is ranked so high on Distrowatch.com. Mint is significantly better. If it wasn't for Gnome 3 being better, currently, than Unity, I would be on Ubuntu.....no questions asked. As soon as Unity catches up(the next release or 2, max.<----that's as long as I would be willing to continue using Fedora), I'm leaving Fedora and going back home to Ubuntu.

Terribly disappointed.

---

### Post by Minox on 2011-06-02
After playing around with it for a bit, I noticed something odd.
It seems like Empathy on Fedora 15 messes up. A few things I noticed were:
[LIST]
[*]It doesn't receive IMs from WLM, unless the contact window is open.
[*]My Google Talk contacts were complaining that they kept getting messages saying that I've "left the room", when I hadn't.
[*]Google talk doesn't notify me of new IMs.
[*]I get messages saying that my IMs have failed (WLM) but they still arrive. Most of the time.
[*]Sometimes messages on WLM won't send, but only to certain contacts.
[/LIST]

Le sigh. It's a shame because Empathy integrates quite well with GNOME 3.

I don't have any problems on Ubuntu. Hm.

---

### Post by kk0sse54 on 2011-06-02
> **Bart_D said:**
> Graphics drivers(Intel) were automatically picked up....which is more than what I can say about Arch Linux, or as I call it,Farse Linux.
You obviously didn't get the point of Arch at all.


> The Fedora website is horrible and has screenshots from a MUCH older version of Fedora! Ubuntu.com would NEVER do that! Red Hat seems uninterested in the desktop.
What website are you visiting? The front page of the Fedora project clearly shows an updated screenshot featuring Gnome 3.

> I am shocked that Fedora is ranked so high on Distrowatch.com. Mint is significantly better. If it wasn't for Gnome 3 being better, currently, than Unity, I would be on Ubuntu.....no questions asked. As soon as Unity catches up(the next release or 2, max.<----that's as long as I would be willing to continue using Fedora), I'm leaving Fedora and going back home to Ubuntu.

Terribly disappointed.

There are other distros other than Ubuntu or Fedora, if you're so disappointed why not look into the plethora of others?

---

### Post by jonathan22 on 2011-06-02
> **Simian Man said:**
> If you install the Nvidia drivers, use [Leigh's guide]("http://www.fedoraforum.org/forum/showthread.php?t=261937").  He explains things well and answers questions if you have any.

In addition to Leigh's NVIDIA guide, I recommend mjmwired's Personal Fedora Guide for post-installation help with non-free codecs, plug-ins, etc.  It makes installing Fedora easier.

[http://www.mjmwired.net/resources/mjm-fedora-f15.html](http://www.mjmwired.net/resources/mjm-fedora-f15.html)

---

### Post by Bart_D on 2011-06-03
Arch NEEDS to have a better installer for its graphics installation section. The rest of it, is half-decent.

I'm sorry, but if you-THE USER-has to tell it EVERYTHING, then what is it actually doing? Anything?

> **C!oud said:**
> What website are you visiting? The front page of the Fedora project clearly shows an updated screenshot featuring Gnome 3.

There are other distros other than Ubuntu or Fedora, if you're so disappointed why not look into the plethora of others?

1. [http://fedoraproject.org/en/features/#entertainment](http://fedoraproject.org/en/features/#entertainment)

2. Tried the majority. Did not like. Kept coming back to Ubuntu. Tried Fedora because I wanted Gnome3 Shell.....

---

### Post by Thewhistlingwind on 2011-06-03
> **Bart_D said:**
> Arch NEEDS to have a better installer for its graphics installation section. The rest of it, is half-decent.

I'm sorry, but if you-THE USER-has to tell it EVERYTHING, then what is it actually doing? Anything?


1. The installer is a pretty standard Linux installer. Ever tried Debian?

2. Running your programs? Shell scripts exist for a reason dude.

3. Ubuntu and arch represent two different philosophies of design. "The user should have everything done for them." and "The user should do everything himself."

Theres benefits to both approaches, I'm not so sure I like either extreme though.

---

### Post by BrokenKingpin on 2011-06-03
There is always good tech coming from the Fedora camp, but as for a desktop OS for the end user it is crap.

---

### Post by wolfen69 on 2011-06-03
> **BrokenKingpin said:**
> There is always good tech coming from the Fedora camp, but as for a desktop OS for the end user it is crap.

Why is that? I've had no problems with it.

---

### Post by DeMus on 2011-06-05
Is this the best the guys at Gnome can come up with? I certainly hope there will still be OS'es which will not include this. It's more than terrible. It's not productive at all.
When you want to start a program you have to click on Activities at the top left corner. Then a list of favorites drops down, a list with mighty icons I might add. If the program is not in that list you have to click on Applications and all installed programs appear, again with these mighty icons.
I mean a six year old might like this but for me it is madness. I just saw a page about the new Windows 8 which imitates Apple (as usual), this Gnome 3 is a bit the same as that dreadful Unity Canonical came up with. Who was first, I don't know.
Guys, if it ain't broken, don't fix it. Don't invent something new just because you think you have to invent something.

Another thing about Fedora 15 is this: I used a live CD on my laptop. The hardware was recognized without a hitch, but many programs crashed so I was filling out bug reports most of the time. I use the 64-bit version but somehow this is not stable (yet).

---

### Post by wolfen69 on 2011-06-05
> **DeMus said:**
> Is this the best the guys at Gnome can come up with? I certainly hope there will still be OS'es which will not include this. It's more than terrible. It's not productive at all.
When you want to start a program you have to click on Activities at the top left corner. Then a list of favorites drops down, a list with mighty icons I might add. If the program is not in that list you have to click on Applications and all installed programs appear, again with these mighty icons.
I mean a six year old might like this but for me it is madness. I just saw a page about the new Windows 8 which imitates Apple (as usual), this Gnome 3 is a bit the same as that dreadful Unity Canonical came up with. Who was first, I don't know.
Guys, if it ain't broken, don't fix it. Don't invent something new just because you think you have to invent something.

Another thing about Fedora 15 is this: I used a live CD on my laptop. The hardware was recognized without a hitch, but many programs crashed so I was filling out bug reports most of the time. I use the 64-bit version but somehow this is not stable (yet).

Ahhhhhh, my fiend, my friend. Another person that used it for a whole 5 min and declares it unfit. Just a heads up: you can put as many things on the "dock" on the left as you want. And if something is not on the dock, I merely type in the first couple letters of the app, and by magic it appears on the screen. Hit enter. I can open an app in literally 2 seconds. How is that not better than sifting through menus and sub-menus?

Also, if you prefer the way gnome 2 works, that's fine, but did you also know that by adding extensions you can pretty much make it act like gnome 2? I've seen screenshots of G3 that look almost exactly like G2 with menus coming off the panel. Before you declare something unfit, maybe you should do a little research about it and spend more time on it. Have a nice day.

---

### Post by DeMus on 2011-06-05
> **wolfen69 said:**
> Ahhhhhh, my fiend, my friend. Another person that used it for a whole 5 min and declares it unfit. Just a heads up: you can put as many things on the "dock" on the left as you want. And if something is not on the dock, I merely type in the first couple letters of the app, and by magic it appears on the screen. Hit enter. I can open an app in literally 2 seconds. How is that not better than sifting through menus and sub-menus?

Also, if you prefer the way gnome 2 works, that's fine, but did you also know that by adding extensions you can pretty much make it act like gnome 2? I've seen screenshots of G3 that look almost exactly like G2 with menus coming off the panel. Before you declare something unfit, maybe you should do a little research about it and spend more time on it. Have a nice day.

Well, I have used it more than 5 minutes, I can tell you that, but I get your point. It's just that I don't like changes. You write you saw Gnome 3 looking like Gnome 2. Well, it's the same thing over and over again: people change things and I have to see to it it looks like it has always looked. Remember the stupid idea Canonical had putting the min-max-close buttons to the left (wrong) side of the screen and I had to put them back to the right (right) side? Now this, now I have to make G3 look like G2 again. WHY? Can you explain that to me? Why do I need to do that when It has always been like this and it has always been good. Like I said before: If it ain't broken, don't fix it.

---

### Post by wolfen69 on 2011-06-06
> **DeMus said:**
> Well, I have used it more than 5 minutes, I can tell you that, but I get your point. It's just that I don't like changes. You write you saw Gnome 3 looking like Gnome 2. Well, it's the same thing over and over again: people change things and I have to see to it it looks like it has always looked. Remember the stupid idea Canonical had putting the min-max-close buttons to the left (wrong) side of the screen and I had to put them back to the right (right) side? Now this, now I have to make G3 look like G2 again. WHY? Can you explain that to me? Why do I need to do that when It has always been like this and it has always been good. Like I said before: If it ain't broken, don't fix it.

Huh? First you complain that gnome 3 is too different, and then complain that it can be changed to gnome 2-
Sorry, I'm lost. All I know is i have no problems with gnome 3. Then again, I can adjust to *any* desktop environment. Isn't that what we signed up for as geeks? No complaints here. I'm just a happy linux user.

---

### Post by screaminj3sus on 2011-06-06
> **Bart_D said:**
> Arch NEEDS to have a better installer for its graphics installation section. The rest of it, is half-decent.

I'm sorry, but if you-THE USER-has to tell it EVERYTHING, then what is it actually doing? Anything?



1. [http://fedoraproject.org/en/features/#entertainment](http://fedoraproject.org/en/features/#entertainment)

2. Tried the majority. Did not like. Kept coming back to Ubuntu. Tried Fedora because I wanted Gnome3 Shell.....
Whats wrong with the arch graphics installation? On my machines it was:

pacman -S xf86-video-intel (or pacman -S xf86-video-ati)
???
Profit!

---

### Post by Shinka.S on 2011-06-07
I'm a huge fan of Ubuntu/Mint but I switched to Fedora because I really love Gnome3. It felt weird for about 15 minutes and then I was just in love with the interface.

Still, I tend to prefer Debiab-based distributions so I'll probably switch to Mint/Mint Debian or even Ubuntu when Gnome3 (without unity) will be well integrated.

---

### Post by nzjethro on 2011-06-07
I'm still pretty new to this linux thing, but I figured when I gain a bit of confidence with Ubuntu I might have a hoon on Fedora. Good to read the positive (and I suppose negative too) reviews.

---

### Post by boydrice on 2011-06-07
Well I ran Fedora 15 since release date until yesterday.  I grew tired of GNOME 3 the longer I used it and went down the path of tweaking to behave more like a normal desktop which made me realize that GNOME 3 isn't for me.  My wife who is a Mac user however loved GNOME 3.  I experienced a few bugs along the way, one where it seemed to kernel panic on shutdown, and another where a full screen of solitaire lost all of its window borders and buttons that did not return.  Other than that I found Fedora to be fine, but I have retreated back to Slackware like I always do.

---

### Post by Dlambert on 2011-06-07
I love it!

---

### Post by wolfen69 on 2011-06-07
> **Dlambert said:**
> I love it!

I know the feeling. It's been rock solid for me. But it helps when you build your own computers and make sure everything is 100% compatible. ;) Almost every distro runs perfect *for me*.

---

### Post by gabhla on 2011-06-08
Guess I'm biased because I've always liked Fedora.  And I like Gnome 3.  I didn't think I would.  At first I bumfuzzled about for about twenty minutes until I begin to adjust. By now I feel comfortable with Gnome 3.  But, that's me, no doubt others will have a different experience.  Only changes I made was to add the weather extension and, of course, changed the wall paper.

---

### Post by user333 on 2011-06-08
I have tried Fedora and I like it a lot. Right now I'm not going switch because I finally got a Ubuntu network working, and I don't want to start all over again yet.

The main differences I see between the two are these:
[INDENT]Ubuntu focuses on visual appeal but Fedora focuses on getting stuff done, even if it doesn't look great.
[/INDENT][INDENT]Ubuntu has a big time lag before they update packages (besides the usual security fixes), but Fedora tends to keep things updated.
[/INDENT][INDENT]Also, I find Fedora to be less frustrating to a veteran Linux user, while Ubuntu tries to fit the needs of people who could care less what happens under the hood.
[/INDENT]Personally, I can't decide between them, so I may just install both :)

---

### Post by jramshu on 2011-06-08
> **jramshu said:**
> 


Then went to install nvidia 8200 drivers, crash. 
Couldn't get it to blacklist the nouveau drivers, probably just me.



Thought I would come back and say that the problem was the nouveau drivers for me. Not that they didn't work with my card, they worked fine. I enabled the nvidia drivers and didn't blacklist the nouveau drivers the way I was suppsosed to. 

It works fine. No problem after that.

---

### Post by athenroy on 2011-06-09
I can't wait to see your comments about Gnome 3 in 6 months to a year!  The longer you use it, the less you like it and if you try using it for anything practical, like office work, not everyone that uses Linux surfs the web 24/7, the work flow and lost motions and ergonomics makes it impractical compared to even Windows.   I wonder if Red Hat has implemented Gnome 3 yet?

---

### Post by wolfen69 on 2011-06-09
> **athenroy said:**
> I can't wait to see your comments about Gnome 3 in 6 months to a year!  The longer you use it, the less you like it and if you try using it for anything practical, like office work, not everyone that uses Linux surfs the web 24/7, the work flow and lost motions and ergonomics makes it impractical compared to even Windows.   I wonder if Red Hat has implemented Gnome 3 yet?

Do you really expect everyone to agree with that? I multi-task like the dickens, and have no problems with "workflow". It's just a matter of getting used to it. Btw, the more I use it, the more I can't live without it.

If it doesn't work for you, that's OK. But don't assume everyone is just like you.

---

### Post by collisionystm on 2011-06-09
how do you minimize windows in Fedora 15? Do you really have to 'right cick' minimize every time?

---

### Post by el_koraco on 2011-06-09
> **collisionystm said:**
> how do you minimize windows in Fedora 15? Do you really have to 'right cick' minimize every time?

You can change that with the Gnome Tweak Tool.

---

### Post by Bart_D on 2011-06-09
> **Thewhistlingwind said:**
> ...Ubuntu and arch represent two different philosophies of design. "The user should have everything done for them." and "The user should do everything himself."....

I HATE the latter! I absolutely HATE it!

The operating system is MERELY a tool that the user requires in order to be productive on his/her system. To have to tweak it every 2.5 days, while hoping that it doesn't TOTALLY destroy everything, is simply unacceptable.

Seriously, when you are in the middle of using, GIMP for example, and updates that you THOUGHT were running silently in the background(after running pacman -Syu) turn out to break your system, it is EXTREMELY **INFURIATING**!

What's the point of bleeding edge if you are always so scared of updates that you never update the system!!! I just don't get it....and I NEVER will!

---

### Post by FormatSeize on 2011-06-10
> **dreamer3kx said:**
> [...] but [it] looks a bit much UI wise,
It is.
> **dreamer3kx said:**
> will you be using it, Ubuntu is all I know so Im curious.
No. 
I don't see myself leaving Fedora 14 any time soon. It's the only OS I have that sits on it's own disk drive because when I use it, everything I could possibly want is there. It's wonderful. 
 
I'm not sure that it's sufficiently clear to me exactly what Fedora 15 is.
> **wolfen69 said:**
> I'm running it right now, and absolutely love it. I'm going to switch to it at least until ubuntu gets their act together.
Even if Ubuntu gets their act together, why bother? Fedora, at least to me, is what Ubuntu wants to be when it grows up.

---

### Post by malspa on 2011-06-10
I installed the KDE spin the other day, and it looks great!

The installation was quick and easy, but I had to spend quite a bit of time setting things up. Most of that time, though, was spent downloading updates and a few apps (the CD didn't come with LibreOffice, for example). The time spent was worth it, in the end. I didn't have to bother with nVidia drivers -- things worked out of the box here.

In both F14 and F15, I thought they did a very nice job with KDE4.

---

### Post by FormatSeize on 2011-06-10
> **Bart_D said:**
> The operating system is MERELY a tool that the user requires in order to be productive on his/her system. To have to tweak it every 2.5 days, while hoping that it doesn't TOTALLY destroy everything, is simply unacceptable.
 
Seriously, when you are in the middle of using, GIMP for example, and updates that you THOUGHT were running silently in the background(after running pacman -Syu) turn out to break your system, it is EXTREMELY **INFURIATING!**
I see where you are coming from. I can see how basically living in fear that everything you were working on getting blown away can be troublesome, along with wondering how much time should one spend working on things in relation to working on the system that allows him to work on things. 
 
But I suppose it's a personal preference. There are times when I want to tell the system everything and have it do very little for me, and there are times when I want the system to know that there is something else that I have to be doing, so it has to do a lot more than normal. But I guess that's why so many of us have or try so many different distros. 
 
> **malspa said:**
> In both F14 and F15, I thought they did a very nice job with KDE4.
I give KDE crap whenever I get the opportunity, but I will agree that the F14 implementation was somewhat bearable.

---

### Post by wolfen69 on 2011-06-10
> **FormatSeize said:**
> 

Even if Ubuntu gets their act together, why bother? Fedora, at least to me, is what Ubuntu wants to be when it grows up.

I'm not sure what that means, and seems a bit childish, imho.

---

### Post by FormatSeize on 2011-06-10
> **wolfen69 said:**
> I'm not sure what that means.
Not much. Just an expression of disappointment in the whole Unity thing. I think that one day it'll be something that I use, but by the time that day comes it'll likely be GNOME3 would likely still be my first choice.

---

### Post by wolfen69 on 2011-06-10
> **FormatSeize said:**
> Not much. Just an expression of disappointment in the whole Unity thing. I think that one day it'll be something that I use, but by the time that day comes it'll likely be GNOME3 would likely still be my first choice.

I pretty much agree. I'm just using fedora because they have a usable gnome-shell at the moment. But when ubuntu supports G3, I will likely move back. Ubuntu has always worked well for me, and I expect it to once G3 is properly supported. Plus, I'm very familiar with apt-get and the debian way of doing things.

---

### Post by Bart_D on 2011-06-11
Gnome 3 Shell randomly displays no wallpaper - just a black wallpaper - upon logging in/starting up Fedora 15. Happens occasionally, not often but that simply won't do.

Not using a fancy theme. Just changed icons (to elementary) using Gnome-Tweak, installed Flash and Virtual Box. So, overall, minor changes.....yet it is still acting up.

This is no good.

I WILL be ditching Fedora as soon as Ubuntu 11.10 comes out.

---

### Post by Z3548s on 2011-06-30
I thought that F15 Xfce was ok but some bugs shouldn't have even occurred. Posting it on their forum didn't help because I requested a detailed response (since I'm new at linux). I fixed it my self getting the info from an Ubuntu video. But either way, I'm going back to Ubuntu Xfce for now. 

In all fairness to Fedora, F14 Xfce didn't have the problems that I encountered in F15. Hopefully, F16 will be better than.

---

### Post by FormatSeize on 2011-06-30
I recant my earlier statement about not liking Fedora 15. It took some getting used to, but it's actually a very likable, productive environment once you take the time to get used to it.

---

### Post by wolfen69 on 2011-06-30
> **FormatSeize said:**
> I recant my earlier statement about not liking Fedora 15. **It took some getting used to**, but it's actually a very likable, productive environment once you take the time to get used to it.

I took to it like a fish takes to water. I love it.

---

### Post by rushikesh988 on 2011-07-01
> **dreamer3kx said:**
> Anyone runnung it, gnome 3 looks pretty neat but looks a bit much UI wise, will you be using it, Ubuntu is all I know so Im curious.
fedora is preety nice ...bt I don't like that thought that redhat gives it free just to get users feedback and get open communities supoort so that they can impliment it in thier redhat :(

---

### Post by wolfen69 on 2011-07-01
> **rushikesh988 said:**
> fedora is preety nice ...bt I don't like that thought that redhat gives it free just to get users feedback and get open communities supoort so that they can impliment it in thier redhat :(

There's nothing wrong with that. It actually benefits everyone. Afterall, it's still open source. And when redhat gets better, the average linux user can run it through a distro called CentOS. It is redhat without the name and free to use by all.

---

### Post by Psyco430404 on 2011-07-01
i used it for a good month before i found my self in "dependency hell", the bleeding edge kernel implementations had broke my compiling abilities for cinelerra. It also broke a few other packages but i fixed those other breaks.

All in all i enjoyed the experiment and it taught me a lot more about Linux, but i think ill stick with Ubuntu and just install the DE/WM that i want and not have a tiff over unity.

---

