---
title: "wine in gutsy"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-10-20
My computer keeps freezing when I try to run a .exe file in wine, or if I even try to configure wine. Any help?

---

### Post by mvanes on 2007-10-20
Is it happening with all executables that you're trying to run or just this one specific exe?

What version of WINE are you running? Is it the latest? 

Check: [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by CapitanYochua on 2007-10-20
Well. It's Gutsy so probably the newest wine. I keep trying to run one .exe, but it also freezes when I try to configure wine. This lends me to believe that this is a bug with wine on Gutsy over and issue with the .exe file.

---

### Post by misfitpierce on 2007-10-20
Gutsy has 1 version back currently I believe.... Go to [http://winehq.com](http://winehq.com) and get the newest one from there and add their repos. New one runs perfect from them on my machine.

---

### Post by CapitanYochua on 2007-10-20
Thanks! (: I'm doing it now. I'll post if I continue to have a problem.

---

### Post by CapitanYochua on 2007-10-20
It continues to freeze, any ideas? ):

---

### Post by Banacek on 2007-10-20
How does Ubuntu manage with Cedega?

---

### Post by CapitanYochua on 2007-10-20
I haven't tried it.

---

### Post by CapitanYochua on 2007-10-20
It's definitely wine that's just messing up in gutsy. I tried running another .exe file, and this didn't work either. Any other Gutsy users experience such an enormous issue with wine?

---

### Post by whatteaux on 2007-10-21
I was. It wasn't a completely 'hard' hang; I was able to switch to a text console and kill the windows EXE or wine, and I was back in business. But it was definitely a dead blank/black screen, with no response at all.

After I switched to the NVidia driver, it's working fine (starts much faster than on Edgy or Feisty).

---

### Post by koma77 on 2007-10-21
I'm having problems with wine in Gutsy as well.
I think it's the same problem: wine freezes from time to time.

For me it is related to moving the mouse and clicking in the wine application. So I think it has to do with xserver-xgl or something like that.

Sometimes I can get out of the hang by simply pressing shift-tab, but sometimes it's completely hung.

I have an ATI X800 card...

---

### Post by XRzero4 on 2007-10-21
having wine issues in gutsy too...
duwnloaded it using terminal, followed the instructions at winehq, all well until...
I get this:

[B]W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems


[/B]

... and this after i've already run apt get update. so I tell it:

**sudo apt-get install wine**

which it does, but then I get:

[B]WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? 
[/B]

Did you get this message too???

---

### Post by mgmiller on 2007-10-21
I think you just need to add the GPG key.  Try pasting this into a terminal:
(Make sure you paste the entire line, including the - at the end)
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

It should add the key and the error message should stop.

It should still install ok though, even with the error message.

---

### Post by buzzmandt on 2007-10-21
everyone should be following this page to install wine:[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) and don't forget the part that says: > First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Once installed, first thing to do is to run```
winecfg
``` from terminal, this will set up the virtual c:\ drives and initiate wine.

If you're having trouble with exes after running winecfg, try running the exe's from terminal, Example:  wine teamspeak.exe

This will usually display error messages in the terminal window, sometimes helpful, sometimes not, but it's a start

---

### Post by fyrefly on 2007-10-21
I have installed the new version for Gutsy, but when I run winecfg or try to run any exe from the terminal, my entire computer freezes. I have tried with cxoffice after giving up on wine, but the same issue [computer freezes]. I tried uninstalling and doing a fresh install, but it didn't help.

Has anyone resolved the issue?

---

### Post by CapitanYochua on 2007-10-21
I did all those command. I have tried running programs or configuring through the terminal, but it still freezes. So this problem is still unsolved for me.

---

### Post by koma77 on 2007-10-22
For me the freezing exists only on some applications, others seem to run fine.
It does not matter if I run in windowed mode or whatever.

I guess it's a bug in Wine and not related to desktop effects as I first suspected...

---

### Post by davidsrsb on 2007-10-22
wine 0.9.47 is working just the same under Gutsy as it was under Feisty for me.
I am using the basic appearance graphics effects.

---

### Post by fyrefly on 2007-10-22
I'm not running beryl or compiz, but still wine & cxoffice freeze

---

### Post by Enverex on 2007-10-22
Paste the output of "glxinfo" please. Also make sure you're using ALSA in winecfg and don't have any other sound drivers ticked.

---

### Post by ed-koala on 2007-10-22
Hmmm, I'm not having any problems yet with Wine in Gutsy.  I installed mine thru Synaptic, and I noticed it was not the latest distro, just one less.  I have a custom built PC, with an NVidia graphics card--restricted driver installed.

I am not running any desktop effects or eye candy ... perhaps that may be a reason?  Other than a driver issue, can't figure another issue that would cause your problems, but I'm new to Ubuntu and am still learning.

---

### Post by redenex on 2007-10-22
Well, system is stuck when I run winecfg...... I tried many methods to install wine, still the same result! Is there anyway I can install previous version of Wine on Gutsy? (It was working all fine on Feisty)/:confused:

---

### Post by CapitanYochua on 2007-10-22
> **Enverex said:**
> Paste the output of "glxinfo" please. Also make sure you're using ALSA in winecfg and don't have any other sound drivers ticked.

Output of glxinfo:
[http://paste.ubuntu-nl.org/41731/plain/](http://paste.ubuntu-nl.org/41731/plain/)

---

### Post by vladk2k on 2007-10-26
One more unsatissfied client here:

System running gutsy, updated from feisty. Installed wine through "Add/Remove Applications..." (but could just as well have installed through *apt-get instal wine*) and it freezes my computer.

Both trying to run wine or winecfg, so no "changing to ALSA in winecfg"

The freeze is almost total, meaning that the whole X-server freezes, No Ctrl+Alt+Fx to change to CLI. Luckily, I have another computer and can log on through ssh. Here are some other behaviours:
sudo /etc/init.d/gdm stop  <-- doesn't do anything, although it says [OK]
sudo killall x  <-- doesn't do anything

I finally caught it, by doing ```
ps -aux | grep wine
```
it got me this:```
vladk2k  10284 82.8  1.7 2653448 8312 ?        R    10:48   0:19 rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
```
so sudo kill -9 10284 and everything is back to normal (if I don't stop gdm, the system becomes responsive again, no fuss)

It's not the audio driver, since I've tried moving wineoss.drv.so and it doesn't help.

However, I DO have a VIA S3 Unichrome (onboard) graphics adapter on that system and so the xorg.conf file has the driver "via" there. I cannot change it to "vesa", since after restarting X I don't get any graphics just a long line of odd characters (currently the sign for british pound, but it changes sometimes) that keeps appearing and disappearing as the x-server restarts until I kill it with *gdm stop*

---

### Post by TeaSwigger on 2007-10-26
The only thing I know of (so far) which lets a frozen WINE freeze the OS are video issues. Fix them - "just say no to frozen wine." From what I gather WINE, a user-level process, shouldn't be able to freeze an OS... evidently except in the case of an underlying problem in X like the video config. 

> **vladk2k said:**
> However, I DO have a VIA S3 Unichrome (onboard) graphics adapter on that system and so the xorg.conf file has the driver "via" there. I cannot change it to "vesa", since after restarting X I don't get any graphics just a long line of odd characters (currently the sign for british pound, but it changes sometimes) that keeps appearing and disappearing as the x-server restarts until I kill it with *gdm stop*

Well... video issues are present here too.

Also as a reminder, run wineprefixcreate after any installation, upgrade or major change, and then open winecfg.

And to kill a frozen wine, run this command: 
```
wineserver -k
```
It's a handy "just in case" in my Fluxbox menu:
```
 [exec] (WINE Stopper - Put a Cork In It!) {wineserver -k} 
```

---

### Post by CapitanYochua on 2007-10-26
How are you supposed to kill a frozen wine if you can't even open the terminal?

---

### Post by vladk2k on 2007-10-26
> **CapitanYochua said:**
> How are you supposed to kill a frozen wine if you can't even open the terminal?

install SSH server, go to another PC and ssh into it... well, I guess it pays to have 6 computers **and** a wifi phone with putty on it :)


So how can I fix it? *dpkg-recongure xorg* doesn't letshow me the option to change the video driver and/or resolutions (I also tried with the --unseen parameter, still no go), if I change it manually all hell breaks loose, and wine still won't start.

---

### Post by drawman on 2007-10-26
I can't even install Gutsy because I get this 'can't resolve' message:

[http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:) Could not resolve 'wine.lowvoice.nl' 
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl' 
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl' 

Maybe this is somehow related.

---

### Post by cocoa_tigra on 2007-10-26
I'm having the same problem with wine after upgrading to gutsy, it freezes x completely, even with winecfg.. I also have a VIA S3 Unichrome graphics adapter, it seemes that only with this one wine creates a freeze. 
Anyone any ideas on how to solve this one?

---

### Post by nu2this on 2007-10-28
I just tried that wineprefixcreate it froze up my PC too. Also I do'nt have a 2nd PC. So any other ideas?

---

### Post by koma77 on 2007-10-28
I've found that for my freeze, sometimes I can make it work again by activating the expo plugin in compiz... Odd, I know...

---

### Post by nu2this on 2007-10-29
I just need wine to work. The  app I need is IE4Linux the reason I need that is to keep an eye on my modem. My connection goes like this PC>Modem>wall. I know there are other ways to do that. This however is for the Comcast techs that need it. I personally took off Windows a long time ago & Comcast don't know Linux. So I  reiterate does anybody here know how to fix this?

---

### Post by CapitanYochua on 2007-10-31
There were updates in the update manager today that seemed wine related. I was hopeful that it would resolve the issue, but I am still having the same problem. ):

---

### Post by bandy on 2007-10-31
I too have had the problem of wine completely freezing a machine with an S3 Unichrome video adapter in Gutsy.

Wine has worked well for me on a number of other computers using other graphics systems.

It would appear to me that the problem relates to the S3 Unichrome system in Gutsy

---

### Post by CapitanYochua on 2007-10-31
I don´t have that. And it doesn´t work for me.

---

### Post by smellydog on 2007-11-09
I have a three year old Averatec 2370.  It uses the VIA driver for my X and my computer freezes up to no keyboard or mouse input.  It started doing this after i upgraded to Feisty from Edgy, and it continues after a fresh install of Gusty and a fresh installation of wine from synaptic.  I am clueless...

---

### Post by mgmiller on 2007-11-10
I tried a Gutsy Live Cd on one of the computers at my work.  They all have integrated S3 graphics.  All goes well until I try to use wine.  Total system lock.  No keyboard or mouse.  Only way out was to hit the reset button on the computer.  ](*,)

---

### Post by FlipJones on 2007-11-11
I, too, am having the same problem.
I'm fairly new to linux, I've just started the day of the final Gusty release. I'm running a dual-hard drive, dual-boot setup with 720 MB of RAM and an AMD Athlon 2700+.

Everytime I attempt to run wine or winecfg, I end up with an almost total computer freeze...no mouse, keyboard etc.

Any Ideas?

---

### Post by mgmiller on 2007-11-12
> **FlipJones said:**
> I, too, am having the same problem.
I'm fairly new to linux, I've just started the day of the final Gusty release. I'm running a dual-hard drive, dual-boot setup with 720 MB of RAM and an AMD Athlon 2700+.

Everytime I attempt to run wine or winecfg, I end up with an almost total computer freeze...no mouse, keyboard etc.

Any Ideas?

You didn't mention what video card you have.  Most of the people with this problem seem to have S3 graphics.  If that's the case, a quick (but not free) fix would be an inexpensive AGP or PCI-e (depending on your mobo), Nvidia video card.

---

### Post by FlipJones on 2007-11-13
That could be part of my problem, I've got integrated graphics..

Is that reason enough for wine to crash?

---

### Post by mgmiller on 2007-11-13
It seems to be, if the integrated graphics are S3.  They are in my case and wine is unusable as a result.  I think almost everyone reporting this problem has integrated S3 graphics.  I have Gutsy running on another machine with a separate Nvidia video card and have no problems with wine.

---

### Post by fyrefly on 2007-11-13
I installed Wine Doors and it seemed to fix the locking problem:

[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

---

### Post by bandy on 2007-11-13
Thanks for the thought.

I had S3 Unichrome graphics on this machine and Wine refused all attempts to work.
Changed it for an old Asus (ATI) 9200SE, configured it as Mach8, 36, 64 and Rage because the 9200 driver couldn't be found and Wine now installs and runs perfectly.

The problem, for me therefore, was the S3 graphics.

---

### Post by smellydog on 2007-11-22
OK, i got my wine to work now.  All i did was that i changed the Via driver back to the old Vesa driver in xorg.conf.  I did not have the memory to run the fancy compiz anyway, so i am not missing anything, only gaining.

---

