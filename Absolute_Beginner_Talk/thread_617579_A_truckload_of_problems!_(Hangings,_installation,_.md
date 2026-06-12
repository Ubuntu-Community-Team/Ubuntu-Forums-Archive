---
title: "A truckload of problems! (Hangings, installation, Internet speed)"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Apoorv on 2007-11-19
First of all, my hardware -

Intel Pentium 4 3.00 Ghz with HT
Intel D101Ggc Motherboard
256 Mb DDR RAM 400 Mhz
ATI Radeon Xpress 200 On board graphics (Which takes about 32 MB of RAM from the 256 MB)


Because of the lack of RAM, I was unable to install from the live CD. Therefore, I installed my system from the alternate text install CD.

Now it seems that the default system works just fine, without any problems. But as I start configuring (installing new apps, codecs, utilities) I have always been left with a system that hangs randomly, without any reason. Sometimes it runs fine over a period of several hours, at other times it may hang just after startup. It isn't event triggered, my system has hanged without any visible apps running. And it has run fine with about 20 apps running simultaneously. This problem has been there since the time of Breezy Badger, and still exists on Gutsy. It has stopped me from using Ubuntu as my mainstream OS.

Because this problem is not event triggered, I have a feeling that it is due to a startup service. Somebody had a similar problem and asked me to disable a service called powernowd. I did that, but still the problem prevails.

Now for the new problems.

1) I installed Opera Kestrel (9.5 Beta), uninstalled it, and reinstalled the stable version 9.4. Now it doesn't work.

2) I have tried disabling many services using :
a) System >> Preferences >> Sessions.
b) System >> Administration >> Services
I have no idea which ones got disabled actually, maybe some got disabled, some didn't, but some services which were surely not disabled (as I can see them running in the system tray) are - Network Monitor and Update Notifier.

3) I can't log out/shut down. When I click on the quit button on the top right corner, the system just freezes. Ctrl + Alt + Bckspace works, but Ctrl + Alt + Del doesn't (weird).

4) I am getting very slow speeds in general, from all high speed downloads, like Ubuntu http/ftp downloads, packages from even the best repos, and general surfing speeds. I'm sure that my net connection is fine because when I download the same things from the same places on Windows, I get blazing fast speeds. The only place where I'm getting decent speeds is on torrents in KTorrent.

5) Even after installing the proprietary ATI drivers, I cannot enable Compiz. I get an error (It was something containing the word 'Composite ').


I also want to disable every possible service I can, I mean all services which are not necessary.

Any kind of help would be highly appreciated.

---

### Post by Mikecore on 2007-11-19
With that little amount of ram thats probably most of your problem. I'm can believe it even ran with Comp enabled. Dude Ram is cheap install some more and then if it doesn't work talk about not using linux as your main OS.

---

### Post by doctorbighands on 2007-11-19
It sounds bad, I'm sure, but I think the previous poster is right. A three-gig processor anchored to 256MB RAM is bound to be an issue for you in this case.

Perhaps it isn't the source of your problems, but an increase in RAM is absolutely going to help you in the grand scheme.

---

### Post by old_geekster on 2007-11-19
The RAM could definitely be a problem, as previously stated.  However, some of your problems could be caused by your ATI card.  Sometimes their drivers are not as compatible with Ubuntu as nVidia's.  No criticism intended, simply stating a fact.

---

### Post by Apoorv on 2007-11-20
But my system speed is just fine! I've run about  20 apps simultaneously without any apparent slowing down of my system. 

Can't you just guys suggest measures to solve the following problems? If you suggest that I buy new hardware for a new OS, then you are being like Microsoft! And Ubuntu promised to liberate us all from the reign of Microsoft.

---

### Post by hyper_ch on 2007-11-20
> **Apoorv said:**
> Can't you just guys suggest measures to solve the following problems? If you suggest that I buy new hardware for a new OS, then you are being like Microsoft! And Ubuntu promised to liberate us all from the reign of Microsoft.

Then we are being like Microsoft...



P.S.: A 3 ghz processor with only 256 and 32mb ram shared for the videocard? WTF....

---

### Post by Apoorv on 2007-11-20
Look, the problem is not in buying the hardware. I'll just run out and fetch a new gig RAM chip. But I want to solve this problem just for the sake of it. I want Ubuntu to work on older hardware too. And none of my problems is in anyway linked to lack of RAM.

---

### Post by Apoorv on 2007-11-20
The minimum requirements for Gutsy is 256 MB of RAM. And if it is 256 MB, it ought to work properly on 256 MB.

---

### Post by hyper_ch on 2007-11-20
as you say, you don't have 256mb ram

---

### Post by philinux on 2007-11-20
Check out my specs in my sig. Gutsy is running fine. 49 sec boot up, only slows down a bit when its  flat out, only to be expected, and <10 sec shutdown.

If I were you I'd move home to its own partition. Extract all you installed apps per attached screenshot then do a clean install.

And get a bit more ram.

---

### Post by Apoorv on 2007-11-21
Bump.

---

### Post by Inxsible on 2007-11-21
The minimum requirement for Ubuntu is 256, and like you said it works. Only when you install new software, it goes bonkers. The other thing is you dont really have 256 MB since 32 mb is shared by the video card.

You can install Xubuntu or Fluxbuntu and see if those work out for you.

---

### Post by OffAxis on 2007-11-21
> 5) Even after installing the proprietary ATI drivers, I cannot enable Compiz. I get an error (It was something containing the word 'Composite ').


Installing Compiz on a borderline system is madness I say.

Like Inxsible suggested, give Xubuntu or Fluxbuntu a shot.

---

### Post by Apoorv on 2007-11-22
Why are you guys forcing me to upgrade!?! My problems are [size=7]NOT[/size] related to lack of RAM!! Except for the compiz one. I do not need compiz. It's just a toy, not for everyday use.

---

### Post by Joeb454 on 2007-11-22
Nobody's forcing you, we're just saying that it's better to have more than the minimum recommended RAM to run your system.

Especially if you only have the minimum RAM and then 32Mb of that is for video...that puts you straight down to 224Mb RAM, which is under the minimum...see what we're getting at now?

And if you start shouting less people will want to help

---

### Post by kleo skywalker on 2007-11-22
People, if Apoorv has said that he wants solutions other than udgrading RAM, it really isn't much point suggesting that, is there?

Apoorv, if you are open to trying out variations of Ubuntu, then the suggestions about Xubuntu and Fluxbuntu make sense. 
And even if you are frustrated with people recommending RAM upgrades again and again, you could keep in mind that they're spending time and effort to help you, so you could express your frustration nicely.

---

