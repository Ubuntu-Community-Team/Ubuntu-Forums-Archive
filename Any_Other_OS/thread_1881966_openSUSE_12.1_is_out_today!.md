---
title: "openSUSE 12.1 is out today!"
date: 2011-11-16
forum: Any Other OS
---

### Post by BigSilly on 2011-11-16
[Get it here]("http://en.opensuse.org/12.1"). I've decided I'm going to take an image of my current Ubuntu 11.10 set up, and give the Gnome 3 version a real good going over. I absolutely loved 11.4 with Gnome 3, and I'm hoping this is similarly superb.

Any fans here?

---

### Post by BrokenKingpin on 2011-11-16
openSuse is a good distro, but have always just felt more at home on Ubuntu or Debian.

I think the one thing holding me back is there is a currently maintained Xfce version (last one was 11.3). I could build one with the SUSE Studio, but I am just to lazy for that lol.

---

### Post by wolfen69 on 2011-11-16
> **BrokenKingpin said:**
> openSuse is a good distro, but have always just felt more at home on Ubuntu or Debian.


Same here. I use gnome shell, and would probably set up opensuse the same way I have ubuntu, so there's not much point in switching distros if ubuntu works perfectly for me. But I'll probably give it a go in vbox.

---

### Post by jjex22 on 2011-11-16
Been trying it in VMplayer this afternoon, obviously being held up a bit graphically by the visualisation, but I'm very impressed at the moment!

For KDE fans, 4.7 is looking awesome, I'm not sure if the plasma name is being carried forward or not, but this is a huge visual step up from SUSE 11.4 - obviously KDE's not changed a lot, but this feels like they're making good use of it.

only just got into gnome three, which I've got to say at a first glance is looking up on unity, but that's of course complete opinion. 

I'll be playing for the next couple of hours, but I'm definitely considering a full install of KDE  - and that's huge for me, I've not installed any KDE for... well over a year and that was Kubuntu, so huge respect to the dev's for the hard work and SUSE for tempting me.

Not got a bug yet, but as I say virtual hardware and basic testing, as with any new release expect the errors to start appearing in the morning!

---

### Post by jjex22 on 2011-11-16
> **BrokenKingpin said:**
> I could build one with the SUSE Studio, but I am just to lazy for that lol.

Gotta love the SUSE studio - one of my favorite innovations!

---

### Post by BigSilly on 2011-11-16
I've only played with the Live CD so far (Gnome 3), and am already enjoying it a great deal. What's surprised me, after using 11.10 for a while, is the low resource use of openSUSE. I had about 8 different workspaces at one point with different applications on each one, and yet the memory and CPU use was about the same as Ubuntu 11.10 with just Firefox running! Plus, I've already logged here my love of Gnome 3, which I do feel is a very lovely thing indeed. It just seems to fit with me and how I use a PC really well. I find it very intuitive, and I don't use that word lightly. I feel with Gnome 3 that I didn't have to spend any time adjusting how I use my computer or learning how to use the DE. It seemed to come very naturally, whereas with Unity I had to put the effort in. Though don't let me give you the impression I don't like Unity as I do.

So yes, I'm definitely going to be installing this one soon. :)

---

### Post by jjex22 on 2011-11-16
I can't testify to memory usage as my 11.10 is 64bit on a real pc and the SUSE is a 32bit fake pc.. on a real pc. that said it is running better (both kde and gnome) than 11.10 under vmware, though that can of course be a symptom of vmware.

Having tried fedora with gnome 3 earlier in the month, and now I'm poking around SUSE's attempt, I've gotta say that I think unity is lagging behind BUT I'm not writing it off by any means, and am looking forward to seeing where unity goes in 12.04.

Back to SUSE - Totally agree with Bigsilly - there is a very nice feel to this gnome 3, but and I almost can't believe these words are coming out of my fingers... I think I'm going to try a full install of the KDE - once the 64bit downloads (I notice the direct download is going a lot slower now everyone's noticed it's out!)

---

### Post by FerroPower on 2011-11-16
Hope they sort out the libraries needed to run a DSL connection in LiveCD last time I couldn't get any help how I am going to download the certain lib files which was needed to setup my dsl in 11.4 since then I hated opensuse. its fails in LiveCD. while everything works out of the box for other distros like LinuxMint Debian, Ubuntu, Fedora.

---

### Post by wolfen69 on 2011-11-16
> **BigSilly said:**
> I had about 8 different workspaces at one point with different applications on each one, and yet the memory and CPU use was about the same as Ubuntu 11.10 with just Firefox running!

Can you post some numbers on ram usage? Using more memory is not necessarily a bad thing, if it is caching important stuff. 

There are some people out there that have 8gb ram, but try and keep ram usage to an absolute minimum. Why? I believe if you have it, use it. You can't save it for a rainy day, and using more doesn't slow anything down. (as long as you have enough)

Now off to try out opensuse.

---

### Post by BigSilly on 2011-11-16
> **wolfen69 said:**
> Can you post some numbers on ram usage? Using more memory is not necessarily a bad thing, if it is caching important stuff. 

There are some people out there that have 8gb ram, but try and keep ram usage to an absolute minimum. Why? I believe if you have it, use it. You can't save it for a rainy day, and using more doesn't slow anything down. (as long as you have enough)

Now off to try out opensuse.

I tend to agree with you, and I too don't see the point of having the hardware if it isn't getting used. Generally I don't notice such things as RAM usage until they make themselves known, and one of the things I noticed with 11.10 was the use of swappiness. I had to set my swap usage to 5 from the 60 it was set to as default. This was because I started to get some system slowdown and poor performance. I found a number of posts detailing the issues with Ubuntu and swap, and the change seemed to fix things. I couldn't understand why Ubuntu was using a lot of swap aggressively when I have plenty of RAM.

Anyway all I can say is, going on Gnome System Monitor, the RAM usage with openSUSE and Gnome 3 is around 567Mb with Firefox running, and idles at around 400Mb and less. Like I say, even when I had more applications running, the system monitor hardly reported any change in the resource usage. My spec is below, but please not I am not a very technical user! If you'd like more detailed output let me know. :D  With Ubuntu it can be around the 700Mb mark with just Firefox running at times, but I've noticed this can vary a lot.

---

### Post by wolfen69 on 2011-11-16
I'm using 12.1 right now as I type (I decided on a proper install to an extra HD I had laying around), and have to say I'm disappointed once again. There are no additional repos available at the moment, such as nvidia, vlc, etc.... I need those 2 things for what I do on my computer. (I'm not into compiling any more) Pretty sad they couldn't get the repos ready before release time.

Had to activate my wireless card in yast. (Really?) Every other distro auto-detects it. <scratches head>

And I guess gnome-shell is not possible without the nvidia drivers. I'm stuck using gnome-fallback with the nouveau drivers.  :-s

The boot up screens are glitchy with artifacts, and sometimes you see only text scrolling. Not a deal breaker, but in this day and age there should be a static screen with a progress bar until you login. 

It's little things like this that keep me on ubuntu. I'm sure it's OK for some people, but not *for me*. 

Goodbye opensuse, I'll try again *next* release. Now it's time to try out Fedora 16.

---

### Post by jjex22 on 2011-11-16
+1 here - now it's on a real machine I also get an odd boot sequence - bits of loading text appear on and off down the left hand side THROUGH the splash? weird. My hardware was fully supported inc. Wireless, but that's usual for this pc. KDE 64 - using ~560MB after loading and opening Firefox (to come here) only annoyance for me at the moment is when I lock the screen and log back in the wireless is disabled - change setting... lock screen, sign in and it's reset, bit annoying!

I'll keep this up and running to see what fixes come through over the next week, but I think I'm also going to give Kubuntu a go - not tried it upon reflection since 10.04, but if 11.10 is running even 20% heavier than this set up, I may be interested. Right so that's Kubuntu and Lubuntu to give a proper work out this week - talk about opposite approaches!

Edit: changed my wireless driver and odd issue's gone - to be honest I'm impressed for my need I'm still only having the splash screen issue which can be display driver related, but as I'm not having any other display issue and I've now tested nearly all the heavy graphics things I do - media playback etc, and I rarely actually shut off my main comp - naughty I know - I'm okay to put up with this - for a new release, this is nothing to some of the nonsense I've put up with (remember when you DL'd an update that broke my unity 3d, ubuntu? ...:| )

---

### Post by boydrice on 2011-11-16
> **BrokenKingpin said:**
> openSuse is a good distro, but have always just felt more at home on Ubuntu or Debian.

I think the one thing holding me back is there is a currently maintained Xfce version (last one was 11.3). I could build one with the SUSE Studio, but I am just to lazy for that lol.

There are no official Xfce or LXDE live media but either can be selected during the DVD or netinstall.

---

### Post by Brushstroke on 2011-11-16
Any ATI users out there? I tried OpenSUSE 11.4's implementation of Gnome 3 but I didn't install it because it kept defaulting to fallback mode in the live environment. I guess it didn't have the drivers for my card. Have any ATI users had bad experiences with the live version of Gnome 3 in this new SUSE release?

If I hear good reports, I might consider giving their version with Gnome 3 a go.

---

### Post by wolfen69 on 2011-11-17
> **Brushstroke said:**
> Any ATI users out there? I tried OpenSUSE 11.4's implementation of Gnome 3 but I didn't install it because it kept defaulting to fallback mode in the live environment. I guess it didn't have the drivers for my card. Have any ATI users had bad experiences with the live version of Gnome 3 in this new SUSE release?

If I hear good reports, I might consider giving their version with Gnome 3 a go.

I guess right now the ati and nvidia repos (among others) aren't available yet. It makes no sense for a major distro to release without these things. Do they really expect people to build from source and blacklist entries? Not that I can't do it, but I'd rather not.

---

### Post by BigSilly on 2011-11-17
> **wolfen69 said:**
> I guess right now the ati and nvidia repos (among others) aren't available yet. It makes no sense for a major distro to release without these things. Do they really expect people to build from source and blacklist entries? Not that I can't do it, but I'd rather not.

I agree. That is pretty disappointing for a modern Linux release. Like you I could do the whole thing manually, but I'd rather it came ready to go with the software and drivers I like to use in the package manager.

I'm sure they'll get it going soon enough, and I'll install it then. But I take your point that this type of thing is what makes Ubuntu so good.

---

### Post by coffeecat on 2011-11-17
> **Brushstroke said:**
> Any ATI users out there? I tried OpenSUSE 11.4's implementation of Gnome 3 but I didn't install it because it kept defaulting to fallback mode in the live environment. I guess it didn't have the drivers for my card. Have any ATI users had bad experiences with the live version of Gnome 3 in this new SUSE release?

To your first question: yes. With my HD5450 card the live Opensuse 12.1 CD booted to the gnome shell desktop without difficulty. Indeed, I was pleasantly surprised how quickly it booted. If yours defaulted back to the fallback session then I guess you have a very old ATI card or very new card. The open source ATI driver - which will be the default with Opensuse - is quite capable of running Gnome Shell (and Unity for that matter) with most ATI cards. Which card do you have?

**EDIT**: oops, sorry, just noticed you were referring to 11.4. Have a go with 12.1 and tell us how you get on with your card.

---

### Post by sffvba[e0rt on 2011-11-18
My burn of 12.1 was a dud (which in hind sight may be a blessing in disguise as it prevented me from hopping again :D)


404

---

### Post by wolfen69 on 2011-11-18
> **not found said:**
> My burn of 12.1 was a dud (which in hind sight may be a blessing in disguise as it prevented me from hopping again :D)


404

You might not be missing much. Over on their forums it seems to be getting less than stellar reviews, and there's not much excitement over it.

---

### Post by BigSilly on 2011-11-18
> **wolfen69 said:**
> You might not be missing much. Over on their forums it seems to be getting less than stellar reviews, and there's not much excitement over it.

Yes, some very mixed opinions. Overall it seems people feel there are a lot of rough edges and a general impression that it wasn't really ready for release. I think I'll stay with Ubuntu 11.10, which thankfully has been running brilliantly.

RE: My earlier post - I do think it's a simple matter of Compiz on Ubuntu that just uses more memory than Gnome 3/Shell. I don't have a problem with that really, since it's working very well indeed, and still uses much less resources than my W7 with Aero on the same PC.

---

### Post by Brushstroke on 2011-11-18
My burn of OpenSUSE 12.1 GNOME didn't go over well. Wouldn't boot to the live environment or the installation setup. Meh. People have said it's not a great release. Oh well. Staying on Ubuntu it seems. :p

---

### Post by BigSilly on 2011-11-18
> **Brushstroke said:**
> My burn of OpenSUSE 12.1 GNOME didn't go over well. Wouldn't boot to the live environment or the installation setup. Meh. People have said it's not a great release. Oh well. Staying on Ubuntu it seems. :p

Yeah, and it seems none of us need much persuading! :lolflag:

---

### Post by wolfen69 on 2011-11-18
> **BigSilly said:**
> Yes, some very mixed opinions. Overall it seems people feel there are a lot of rough edges and a general impression that it wasn't really ready for release. I think I'll stay with Ubuntu 11.10, which thankfully has been running brilliantly.


I wasn't really planning on switching to opensuse or anything anyway, but I always try out the latest versions of all the major distros on a spare hard drive. I was honestly hoping I would like it, but as you mentioned, it does feel it a bit rushed and incomplete.

I'm sure some people will enjoy it depending on their needs, but right now I couldn't give it a hardy recommendation. Oh well, it's good that we all have many choices.

My ubuntu installs aren't going anywhere anytime soon, that's for sure. Although *for me*, Fedora is a close second fav.

---

### Post by BigSilly on 2011-11-19
[Looks like the Nvidia repo is up now]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/467824-nvidia-repo-opensuse-12-1-missing-2.html#post2406098"). I'll give it a go after I've backed up my Ubuntu install. I can't say whether the ATI drivers are present yet though. I'm sure I read somewhere that ATI users were upset that their drivers were missing too.

---

### Post by ShodanjoDM on 2011-11-19
Quad boot (Ubuntu 11.04, 11.10, Arch and now OpenSUSE 12.1), this is the first time I've done a full OpenSUSE install on the HDD. 

Decided to use Gnome 3 version, and Nouveau driver works fine with it although I eventually installed Nvidia binary driver for a better performance with my card (GTS 250).

As mentioned before, the lack of official Nvidia/ATI driver repository is somewhat annoying, but now that it's available, I might try to install the driver again from the repo.

In my experience, OpenSUSE use slightly less RAM than Ubuntu when booting into the Gnome 3 desktop but that probably because there are more autostarted applications in Ubuntu than OpenSUSE. Then the inclusion of the IceWM as default is a pleasant surprise for me. Then there's YaST.

Still need to familiarize myself more with this distro though.

---

### Post by BigSilly on 2011-11-19
Well it's disaster for me sadly. Backed up my Ubuntu with Clonezilla, and installed openSUSE 12.1 Gnome. Noticed a glitchy boot up after installing, but once in I got the Nvidia repo and installed the driver, thinking this might solve it. Installed, rebooted, and it booted to a text prompt. OK, so logged in and startx, nothing but a rolling screen of text.

Reboot, retry a couple of times. Search around for solutions. Unsuccessful. Give up, back on Ubuntu.

I dunno what happened to this release. OpenSUSE 11.4 was really solid for ages for me, and that was with only a "preview" of Gnome 3. This one really does seem to have been rushed without a thought for anyone actually using it. Really sad about it actually.

---

### Post by BigSilly on 2011-11-20
At a loose end today, so decided to give this release another go. Somehow, inexplicably, it went really well and actually installed everything fine this time. Really pleased. :)  I don't know what I did on my first attempt that messed it up, but it's perfect now. I suspect I installed the wrong Nvidia driver first time out.

But now I'm really enjoying it. Is it a replacement for Ubuntu? I'm not sure, but I'll be sticking with it until it does something silly. If it does. Everything seems solid and stable enough to me thus far.

---

### Post by BrokenKingpin on 2011-11-21
I am interested in the tumbleweed repos (to make openSUSE rolling), but apparently you have to rebuild any proprietary NVidia or ATI drivers manually for every kernel update.

This is a shame, as tumbleweed may have been the tipping point for me switching to openSUSE, but having to rebuild my NVidia driver for every kernel update just seems like too much of a pain.

---

### Post by collisionystm on 2011-11-21
> **BrokenKingpin said:**
> I am interested in the tumbleweed repos (to make openSUSE rolling), but apparently you have to rebuild any proprietary NVidia or ATI drivers manually for every kernel update.

This is a shame, as tumbleweed may have been the tipping point for me switching to openSUSE, but having to rebuild my NVidia driver for every kernel update just seems like too much of a pain.

Its really not that bad. You have to do it on Ubuntu too unless you install the driver using Jockey.

---

### Post by wolfen69 on 2011-11-21
> **collisionystm said:**
> Its really not that bad. You have to do it on Ubuntu too unless you install the driver using Jockey.

Isn't there a DKMS module available in opensuse?

---

### Post by collisionystm on 2011-11-21
> **wolfen69 said:**
> Isn't there a DKMS module available in opensuse?


Maybe. But that is only if it has a driver from the Repo's right?

---

### Post by BigSilly on 2011-11-21
Back on Ubuntu anyway. Loved openSUSE, very nice. I just think overall Ubuntu is too good a desktop to be doing without! :D

Hats off to the openSUSE devs though. Great release. :)

---

### Post by sffvba[e0rt on 2011-11-21
[http://www.jupiterbroadcasting.com/14057/opensuse-12-1-review/](http://www.jupiterbroadcasting.com/14057/opensuse-12-1-review/)

Chris is loving the release :)


404

---

### Post by BigSilly on 2011-11-21
> **not found said:**
> [http://www.jupiterbroadcasting.com/14057/opensuse-12-1-review/](http://www.jupiterbroadcasting.com/14057/opensuse-12-1-review/)

Chris is loving the release :)


404

Yes I've seen that. Great review.

Wish they'd bring back Bryan though. The guy in the background just ain't the same. Occasionally muttering "uh-huh" every so often does not make an inspiring listen sat on the bus going to work!

---

### Post by wolfen69 on 2011-11-21
> **not found said:**
> [http://www.jupiterbroadcasting.com/14057/opensuse-12-1-review/](http://www.jupiterbroadcasting.com/14057/opensuse-12-1-review/)

Chris is loving the release :)


404

I heard it, and he made it out to be the greatest distro/OS release of all time. (I don't share his opinions)

And yeah, what's up with the new guy? What happened to Bryan?

Edit: [why Bryan left LAS]("http://lunduke.com/?p=1929")

---

### Post by BigSilly on 2011-11-21
> **wolfen69 said:**
> I heard it, and he made it out to be the greatest distro/OS release of all time. (I don't share his opinions)

And yeah, what's up with the new guy? What happened to Bryan?

Edit: [why Bryan left LAS]("http://lunduke.com/?p=1929")

It is a very good release and he's entitled to his opinion. ;)

Still doesn't really reveal why Bryan left though. Either way it's sad. The whole tone of the show has changed. I loved it because it was funny and almost a comedy show, but now it just rambles on and I haven't listened to it for ages. I'm sure the new chap is a nice bloke and all, but he doesn't make a natural radio presenter.

---

### Post by collisionystm on 2011-11-21
> **not found said:**
> [http://www.jupiterbroadcasting.com/14057/opensuse-12-1-review/](http://www.jupiterbroadcasting.com/14057/opensuse-12-1-review/)

Chris is loving the release :)


404


He calls it Open SOOSA

lol. 

I hope that's not the really pronunciation

---

### Post by wolfen69 on 2011-11-21
> **collisionystm said:**
> He calls it Open SOOSA

lol. 

I hope that's not the really pronunciation
Hey! I say it that way too. I've heard suzy, sooza, soossy, etc. I guess it really doesn't matter much. But you know how us americans like to butcher things. ;)

How does everyone else say "OpenSuse"?

---

### Post by sffvba[e0rt on 2011-11-21
I just came back to write that the new Linux Action Show is lopsided now without Bryan as it is now a one man show basically but I see I was beaten to it by several :D

As for the pronunciation, that will vary just like Ubuntu depending on the country you are in. I couldn't even find any consensus on the openSUSE side of the forums :)

I used to pronounce is like Zues-ah, but that's just me (at least I can pronounce Ubuntu perfectly as I am from South Africa :p)


404

---

### Post by collisionystm on 2011-11-22
> **wolfen69 said:**
> Hey! I say it that way too. I've heard suzy, sooza, soossy, etc. I guess it really doesn't matter much. But you know how us americans like to butcher things. ;)

How does everyone else say "OpenSuse"?

I say open suse like I would say doctor Seuss lol

---

### Post by ShodanjoDM on 2011-11-22
> **wolfen69 said:**
> Hey! I say it that way too. I've heard suzy, sooza, soossy, etc. I guess it really doesn't matter much. But you know how us americans like to butcher things. ;)

How does everyone else say "OpenSuse"?

Open Soo-Sae? That's how I pronounced it in my native language anyway :D

---

### Post by BrokenKingpin on 2011-11-22
> **collisionystm said:**
> Its really not that bad. You have to do it on Ubuntu too unless you install the driver using Jockey.
I do? I have been using Ubuntu for years and I have never had to compile my own NVidia driver.... same with Debian. I assume the new Nvidia driver is delivered through the repos with the new kernel.

---

### Post by collisionystm on 2011-11-22
> **BrokenKingpin said:**
> I do? I have been using Ubuntu for years and I have never had to compile my own NVidia driver.... same with Debian. I assume the new Nvidia driver is delivered through the repos with the new kernel.


Everytime I have installed a driver from the manufacture website, I.E. Ati Catalyst, I have had to re-run setup after every kernel update because it has to update the kernel

---

### Post by BrokenKingpin on 2011-11-22
> **collisionystm said:**
> Everytime I have installed a driver from the manufacture website, I.E. Ati Catalyst, I have had to re-run setup after every kernel update because it has to update the kernel
I just use the nvidia drivers out of the repos. I thought the catalyst drivers were also in the repos, unless you require the absolute latest version of them.

---

### Post by collisionystm on 2011-11-22
> **BrokenKingpin said:**
> I just use the nvidia drivers out of the repos. I thought the catalyst drivers were also in the repos, unless you require the absolute latest version of them.

I did.

Radeon HD 6380G would not work with 11.10 until the 11.11 catalyst came out

---

### Post by wolfen69 on 2011-11-29
After an initial disappointing try with 12.1, I decided to give it another go. Things went fairly well, and everything seemed to be OK, but sound in vlc kept crapping out for some reason. Overall, it seems to be better than in the past, but it's not going to replace Ubuntu for me any time soon.

Next I'm gonna try out Mint 12. Cheers.

---

### Post by IWantFroyo on 2011-11-29
openSUSE is my favorite after the Debian family (#! being my favorite out of those).

I tried 12.1, and it was superb. I've only tried the KDE version so far, however.

---

### Post by nodrog1952iii on 2011-11-29
I had been a Ubuntu/Gnome2 user since 2008. Then, thanks to Unity, I switched to OpenSUSE/KDE4 prior to the release of Ubuntu 11.10.  Thank god!!!  With KDE4 I am able to customize my desktop just like I did with Gnome2 and I now have a desktop with a look and feel that is virtually identical to my Gnome2 desktop.  Oh, BTW, with KDE4 Plasma Desktop I am also able to get all of the enhanced effects that I got with Compiz on Gnome2 including the cube, wobbly windows, etc.  I highly recommend that those of you that are fed up with Unity try KDE4 on OpenSUSE.  You won't go back!

---

### Post by kio_http on 2011-11-30
> **nodrog1952iii said:**
> I had been a Ubuntu/Gnome2 user since 2008. Then, thanks to Unity, I switched to OpenSUSE/KDE4 prior to the release of Ubuntu 11.10.  Thank god!!!  With KDE4 I am able to customize my desktop just like I did with Gnome2 and I now have a desktop with a look and feel that is virtually identical to my Gnome2 desktop.  Oh, BTW, with KDE4 Plasma Desktop I am also able to get all of the enhanced effects that I got with Compiz on Gnome2 including the cube, wobbly windows, etc.  I highly recommend that those of you that are fed up with Unity try KDE4 on OpenSUSE.  You won't go back!

I've always been a KDE user since KDE 3.2 I think. I used commercial SuSe before but I'm setted on Kubuntu since 6.06. Give Kubuntu 11.10 a go if you like OpenSuse.

---

### Post by nodrog1952iii on 2011-11-30
> **kio_http said:**
> I've always been a KDE user since KDE 3.2 I think. I used commercial SuSe before but I'm setted on Kubuntu since 6.06. Give Kubuntu 11.10 a go if you like OpenSuse.

Prior to leaving Ubuntu, I initially upgraded my 11.04 installation to Kubuntu and gave it a test drive.  Generally, I liked it very much.  However, I was unable to get my fonts configured to my complete satisfaction especially for Firefox and Thunderbird and so I subsequently installed OpenSUSE and tried it out. There are two reasons why I chose OpenSUSE.  First, KDE4 is the default desktop interface for OpenSUSE.  Therefore, I theorized that KDE would get the same focus at OpenSUSE that Gnome has gotten at Ubuntu.  Secondly, there is an OpenSUSE font repo specifically for Firefox and Thunderbird fonts named Muzlocker.   With the Muzlocker fonts on OpenSUSE, my Firefox and Thunderbird fonts are every bit as good (antialiased, etc) as with Microsoft or gnome2.  Nevertheless, it is entirely possible that I gave up on Kubuntu too soon.

---

### Post by BigSilly on 2011-11-30
I've always been really happy with the look of fonts on openSUSE. :confused:

Anyway, I made the switch back onto openSUSE 12.1 Gnome 3 today as my main OS. For a number of reasons - but mostly, I just feel overall if I'm being completely honest with myself, Gnome 3 and Shell is my preference over Unity, and Gnome 3 seems better suited on openSUSE than Ubuntu, where Unity is the main concern. Like I say, Unity is really great and I'd recommend it to anyone, especially anyone new to Linux, but I prefer the workspace handling on Gnome shell, and I feel it's a better design *generally*. I really loved it for the six months I had it on openSUSE 11.4, and had been missing it a bit.

I've been very bipolar over the last couple of weeks testing things out and seeing what I liked. I spent a lot of time with Unity and KDE4, as well as Gnome 3 which I have previous happy experience with. But I've had to settle down eventually before I go insane from distro-hopping, and I really love my final choices.

Not that anyone cares or needed to know! :D  Still using Ubuntu via the KDE variant though. Can't give up Ubuntu altogether!

---

### Post by ernestj on 2011-11-30
I downloaded opeSUSE today burned the iso, but when I boot to it, there is no option to just try it.
How do I try it?

ernie

---

### Post by collisionystm on 2011-11-30
> **ernestj said:**
> I downloaded opeSUSE today burned the iso, but when I boot to it, there is no option to just try it.
How do I try it?

ernie

download the Live-CD not the dvd.

---

### Post by collisionystm on 2011-11-30
So I went ahead and installed Suse 12.1 with Gnome. Its pretty cool.

I have a Radeon 6380G so it took a few extra minutes to get the system up, but now that it is, I am happy to report I am getting much higher FPS on GLX Gears that I was with Ubuntu 11.10

I went from 1600-1800 fps on Ubuntu to 2600-2800 fps on suse. Same catalyst 11.11. Pretty sweet

---

### Post by inobe on 2011-11-30
> **FerroPower said:**
> Hope they sort out the libraries needed to run a DSL connection in LiveCD last time I couldn't get any help how I am going to download the certain lib files which was needed to setup my dsl in 11.4 since then I hated opensuse. its fails in LiveCD. while everything works out of the box for other distros like LinuxMint Debian, Ubuntu, Fedora.

when i had dsl i needed to locate ATT nameservers to update resolv.conf in etc/resolve.conf.

that seem to have went on throughout a few distributions, still didn't stop me:P

i have cable now, it's faster, either way, it will get installed.

---

