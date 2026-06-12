---
title: "Linux Mint Debian Edition"
date: 2011-05-01
forum: Any Other OS
---

### Post by screaminj3sus on 2011-05-01
I've just installed and been playing around with linux mint debian edition, and wow am I impressed. It certainly lacks a lot of the polish of ubuntu or vanilla mint but it makes up for it in its performance. I don't know why it performs so much better than pretty much every other distro I've tried, especially ubuntu.

For example in ubuntu 10.10 and 11.04 the scrolling in firefox with smooth scrolling enabled is horrific and laggy (using catalyst 11.3/11.4 and oss driver.) in LMDE its just as smooth as in windows using both the oss driver and catalyst. 

Compiz is generally FAR smoother too. Minimize animtions, general usage, doesn't have some odd artifacts like in ubuntu (in natty all the fade animations have this annoying white flicker)

Boot time is faster, applications launch faster.

Does anyone know what could make stuff like scrolling and compiz so much faster on my machine in this distro? I am quite curious as I have had these issues in other distro's too. Laptop's specs are in my signature.

---

### Post by Timmer1240 on 2011-05-01
Yes it does seem a little snappier on my computer too I like it alot now been running it for over 2 months compiz works great although it wasnt enabled and set up after install but no big deal.I had to find and install my nvidia driver not a biggy and took a little research to set my printer up but it runs great now!Its pretty much like debian takes a little work after install to get everything going but smooth sailing now.

---

### Post by michaelzap on 2011-05-01
> **screaminj3sus said:**
> Does anyone know what could make stuff like scrolling and compiz so much faster on my machine in this distro? I am quite curious as I have had these issues in other distro's too. Laptop's specs are in my signature.

Debian is a much leaner distro than Ubuntu. There's a whole lot of extra bloat on top of the Debian base in Ubuntu that slows everything down quite a bit. Some of that bloat is useful stuff, but I switched to Debian a while back because I no longer felt like the minor improvements were worth the major lags and buggy hardware support.

---

### Post by Timmer1240 on 2011-05-01
I would like to see Ubuntu  release a Debian edition I think a lot of people here would show great interest in it.A rolling release just like mint Debian its nice to get out of the 6 month cycle!

---

### Post by screaminj3sus on 2011-05-01
> **michaelzap said:**
> Debian is a much leaner distro than Ubuntu. There's a whole lot of extra bloat on top of the Debian base in Ubuntu that slows everything down quite a bit. Some of that bloat is useful stuff, but I switched to Debian a while back because I no longer felt like the minor improvements were worth the major lags and buggy hardware support.

Yeah its kind of crazy how much it slows things down though. My laptop isn't amazing by any stretch but it has decent specs (2ghz dual core, 4 gigs of ram, 512mb hd2600)

---

### Post by Rubi1200 on 2011-05-01
Just out of curiosity, how have you guys/gals dealt with some of the documented issues with LMDE?

Just for starters:

1. you have to add swap manually to fstab

2. updates with MintUpdate are a no-no, need to use Synaptic or cli

3. the log file viewer shows the wrong dates for entries

4. one of the updates pulls in a kexec package which loops the restart command, bypassing BIOS and GRUB

Any thoughts, suggestions, comments?

Thanks in advance.

---

### Post by michaelzap on 2011-05-01
> **Rubi1200 said:**
> Just out of curiosity, how have you guys/gals dealt with some of the documented issues with LMDE?

Just for starters:

1. you have to add swap manually to fstab

2. updates with MintUpdate are a no-no, need to use Synaptic or cli

3. the log file viewer shows the wrong dates for entries

4. one of the updates pulls in a kexec package which loops the restart command, bypassing BIOS and GRUB

Any thoughts, suggestions, comments?

Thanks in advance.

Er... I haven't had any of those issues...?

Maybe you should search for specific resolutions to your problems on the Linux Mint forums, but I used LMDE for quite a while and had none of those issues (I use Crunchbang and regular Debian at the moment - not LMDE).

---

### Post by Rubi1200 on 2011-05-01
Here's the thing michaelzap; when I tried the first release I had none of these issues either. Then I did a fresh install of the latest version and these are some of the things that came up. 

If you look at the Mint Forums, you will see that some of these seem to be specific to the latest release.

---

### Post by screaminj3sus on 2011-05-01
> **Rubi1200 said:**
> Just out of curiosity, how have you guys/gals dealt with some of the documented issues with LMDE?

Just for starters:

1. you have to add swap manually to fstab

2. updates with MintUpdate are a no-no, need to use Synaptic or cli

3. the log file viewer shows the wrong dates for entries

4. one of the updates pulls in a kexec package which loops the restart command, bypassing BIOS and GRUB

Any thoughts, suggestions, comments?

Thanks in advance.
1. My swap worked fine OOTB.
2. Mint update failed the first time but after running apt-get upgrade once its been fine.
3. N/A
4. Not sure what this means? I haven't had any problem booting, my grub menu comes up fine... I'm fully updated.

---

### Post by michaelzap on 2011-05-01
> **Rubi1200 said:**
> Here's the thing michaelzap; when I tried the first release I had none of these issues either. Then I did a fresh install of the latest version and these are some of the things that came up. 

If you look at the Mint Forums, you will see that some of these seem to be specific to the latest release.

Well, I'd suggest that LMDE users read the "breakages" thread before running updates in general:
[http://forums.linuxmint.com/viewtopic.php?f=141&t=67502](http://forums.linuxmint.com/viewtopic.php?f=141&t=67502)

LMDE is based on Debian testing (wheezy), which gets new software faster but does sometimes break. People who are most concerned about stability should probably use the Debian stable (squeeze) repos, which are the default in Crunchbang. Hopefully the Debian CUT (Constantly Usable Testing) project will take off and we can have the best of both worlds.

Ubuntu, of course, is based mostly on the Debian unstable (sid) repositories (except for LTS releases), so it has the very latest software but is much more likely to break than testing or stable.

---

### Post by screaminj3sus on 2011-05-01
Yep and if you choose to use the squeeze repos you can always enable backports so you still get updates for applications.

I personally prefer to be on the edge though :)

---

### Post by michaelzap on 2011-05-01
> **screaminj3sus said:**
> 
4. Not sure what this means? I haven't had any problem booting, my grub menu comes up fine... I'm fully updated.

RE #4: There was in fact a bad kexec package update in Debian testing back in March, but it was fixed long ago.

---

### Post by michaelzap on 2011-05-01
> **screaminj3sus said:**
> Yep and if you choose to use the squeeze repos you can always enable backports so you still get updates for applications.

I personally prefer to be on the edge though :)

I currently have two nearly-identical Crunchbang Xfce installs on my main laptop. One is using the standard stable repos plus backports, while the other has been dist-upgraded with the sid repos so that I can try out Xfce 4.8. Once I'm sure that there are no problems, I'll probably do that to my main installation also.

Then I'm going to play around on the extra installation and see if I can create an "Xfce Shell" (based on the design principles behind Gnome Shell, but much more stable and flexible than that is currently).

---

### Post by Timmer1240 on 2011-05-01
The only broken packages Ive had so far was VLC but it was corrected in about 3 or 4 days other than that its been fine.

---

### Post by Rubi1200 on 2011-05-02
Thanks everyone for responding. I am going to try and figure out why I am experiencing these problems that none of you seem to have had :confused:

---

### Post by linuxyogi on 2011-05-02
Hi, I am using LMDE xfce with the Debian unstable repo enabled. 

But I must say that there is nothing unstable about it.

The only problem is with winff. It can't even convert to avi.

---

### Post by Rubi1200 on 2011-05-03
Quick update for those interested.

After playing around and reinstalling a couple of times, the problems I mentioned previously have been resolved.

I am now using a stable and functional LMDE.

---

### Post by ubun2warrior on 2011-05-03
does the lmde has wubi ??

---

### Post by linuxyogi on 2011-05-03
My LMDE installation went completely haywire after installing some updates. 

It happened because some of their repos were down for some reason I don't know about which resulted in partial updating of packages & ultimately dependency hell.

IM[COLOR=Red]**H**[/COLOR]O all distros should issues an advisory in their distribution forum about such issues.

The openSUSE forum did it recently regarding their Gnome 3 repo & it was really helpful.

Bye Bye LMDE. ):P

Conclusion : I should test a distro thoroughly before making any comments about it. Be it negative or positive.

---

### Post by michaelzap on 2011-05-03
> **linuxyogi said:**
> My LMDE installation went completely haywire after installing some updates. 

It happened because some of their repos were down for some reason I don't know about which resulted in partial updating of packages & ultimately dependency hell.

IM[COLOR=Red]**H**[/COLOR]O all distros should issues an advisory in their distribution forum about such issues.

The openSUSE forum did it recently regarding their Gnome 3 repo & it was really helpful.

Bye Bye LMDE. ):P

Conclusion : I should test a distro thoroughly before making any comments about it. Be it negative or positive.

When that happens (a particular repo is not available for some reason), you should get a warning and a prompt as to whether you want to install only partial packages or cancel (just as you do in Ubuntu). The default answer is no (cancel), and for good reason. Did you answer yes to a prompt like this? If so, that's something that could happen to you in any distro. You might be more likely to get the prompt if you're using the sid repos (they are called "unstable", after all), but as long as you answer no it wouldn't break anything.

---

### Post by michaelzap on 2011-05-03
> **ubun2warrior said:**
> does the lmde has wubi ??

Nope. Wubi is an Ubuntu thing (the Ubuntu-based Linux Mint editions have mint4win, which is based on Wubi). If you just want to try out LMDE, make a bootable USB or Live CD instead.

---

### Post by linuxyogi on 2011-05-03
> **michaelzap said:**
> When that happens (a particular repo is not available for some reason), you should get a warning and a prompt as to whether you want to install only partial packages or cancel (just as you do in Ubuntu). The default answer is no (cancel), and for good reason. Did you answer yes to a prompt like this? .

It did say that it failed to get updates from some repos but it didn't say anything about any partial packages or something like that. AFAIK in Ubuntu too, if a certain repo is unavailable it just tell you that getting update information from xyz repo "failed". 

On the other hand, if you cancel a update process which is already in progress it does ask you if you want install partial updates.

---

### Post by krapp on 2011-05-03
> **linuxyogi said:**
> My LMDE installation went completely haywire after installing some updates. 

It happened because some of their repos were down for some reason I don't know about which resulted in partial updating of packages & ultimately dependency hell.

IM[COLOR=Red]**H**[/COLOR]O all distros should issues an advisory in their distribution forum about such issues.

The openSUSE forum did it recently regarding their Gnome 3 repo & it was really helpful.

Bye Bye LMDE. ):P

Conclusion : I should test a distro thoroughly before making any comments about it. Be it negative or positive.

You switched the sources from "Testing" to "Unstable"; what'd you expect? :P

---

### Post by michaelzap on 2011-05-03
> **linuxyogi said:**
> It did say that it failed to get updates from some repos but it didn't say anything about any partial packages or something like that. AFAIK in Ubuntu too, if a certain repo is unavailable it just tell you that getting update information from xyz repo "failed". 

On the other hand, if you cancel a update process which is already in progress it does ask you if you want install partial updates.

I actually just got this error earlier tonight on a Xubuntu system, so I have the memory of the Ubuntu error message fresh in my mind. Some repos couldn't be contacted when I tried to update (due to a fritzy connection on our end), so the Update Manager GUI popped up a big error message telling me what hadn't updated and asking me whether I wanted to apply the changes I'd requested anyway. I had to close that window and press the button again for it to download and install the packages that were available.

OTOH, I also had something similar happen after updating my Crunchbang Xfce test installation to the sid repos, but in that case there was no updated tint2 package available. That error message didn't stop the whole process, and it did in fact break tint2 on that system (which is no biggie). That's the kind of thing that should only happen in the sid (unstable) repos, however - it's just part of living on the edge.

---

### Post by screaminj3sus on 2011-05-03
> **linuxyogi said:**
> 

The openSUSE forum did it recently regarding their Gnome 3 repo & it was really helpful.


lol they didn't do it soon enough. I had installed opensuse when I heard they had a gnome 3 "stable" repo, and when I updated with it, it totally b0rked everything. After that happened to a bunch of people they put up the warning though.


Regarding mint, You did say you were using the unstable repos, things like that can happen. I haven't had an problems with testing so far.

---

### Post by cbowman57 on 2011-08-03
> **michaelzap said:**
> ...
Then I'm going to play around on the extra installation and see if I can create an "Xfce Shell" (based on the design principles behind Gnome Shell, but much more stable and flexible than that is currently).

This is interesting.  Have you explored this idea further?

---

