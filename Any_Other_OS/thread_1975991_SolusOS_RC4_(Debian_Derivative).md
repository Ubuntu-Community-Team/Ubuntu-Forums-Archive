---
title: "SolusOS RC4 (Debian Derivative)"
date: 2012-05-08
forum: Any Other OS
---

### Post by ikeydoherty on 2012-05-08
Hi, I'm Ikey Doherty. Some of you may remember me from when I created LMDE
all that time back. I'm working on my own project now and have released
RC4 of SolusOS.

It's a Debian Stable based distribution with updated applications. Quick overview:

[LIST]
[*]Firefox 12.0
[*]Thunderbird 12.0.1
[*]LibreOffice 3.5.3.2
[*]VLC 2.0.1
[*]PlayOnLinux 4.0.18
[*]Openshot 1.4.2-2
[*]Minitube 1.7
[*]Dropbox installer by default
[/LIST]
Quite a number of recent applications exist in our repos, which total to 5.5GB right
now, we've only got 32-bit right now but we intend to release 64-bit alongside the
final release.


SolusOS features the Gnome 2.30 desktop environment with a custom built kernel
(3.0.0-ck1-solusos1) with PAE, preempt, BFS, and we make use of prelink/preload.
It's a pretty fast system invariably using around 120MB of RAM idle :)


It also features a FirstRunWizard that helps with setting up your connection, firewall,
updates and automatic installation of proprietary graphics drivers.


There has been a massive amount of interest in SolusOS, so much so that we had
to upgrade our servers to cope with the strain! :) I'd recommend it to anyone
who just wants to squeeze some juice out of their computer, was worried about
getting too close and personal with Debian before or for those just wanting a Debian
based distro that pretty much just works as is.


If you're going to download bear in mind that it does include multimedia codecs
by default, so you might wanna check the policy in your country on that first. As
previously stated its 32-bit only now (for the next week or so) but uses a PAE
kernel so you can see all of your RAM.


If you want to check it out, the URL is [http://www.solusos.com/download](http://www.solusos.com/download)


Happy distro hopping! :)

---

### Post by sffvba[e0rt on 2012-05-08
I have never seen such a polished looking Gnome 2...

...must ... resist ....urge... to... install... :p


404

---

### Post by ikeydoherty on 2012-05-08
> **not found said:**
> I have never seen such a polished looking Gnome 2...

...must ... resist ....urge... to... install... :p


404

Thank you very much! :) Go on it won't hurt :D

---

### Post by Zato-1 on 2012-05-08
> **not found said:**
> I have never seen such a polished looking Gnome 2...

...must ... resist ....urge... to... install... :p


404

Try it out, you wont regret it :)
I have been using it since early alpha stages and I gotta say that Im very impressed. The distro is a piece of art :)

---

### Post by ikeydoherty on 2012-05-08
> **Zato-1 said:**
> Try it out, you wont regret it :)
I have been using it since early alpha stages and I gotta say that Im very impressed. The distro is a piece of art :)

Many kind words today, thank you very much :D

---

### Post by sffvba[e0rt on 2012-05-08
Was browsing the site and forum... I am glad to hear that you will be switching to Gnome 3 when Debian does and that you are not going to be flogging a dead horse :)

Oh, very nice site and forum too.

Everything I have seen about the OS looks decent, after putting it through its paces in a VM I will check back with some more thoughts (but that can take anything from a week to a month the way things are going at the moment).


404

---

### Post by Antman on 2012-05-09
Now that the final version has been released, I just put this on my spare laptop this morning via live USB. The install was flawless and went without a hitch. The desktop is very smooth and quick.

After I get back home, I'm going to test it out.

---

### Post by Uncle Spellbinder on 2012-05-09
Looks very interesting. Though I'd prefer a rolling-type release, I may just have to try this out.

Will Firefox continue to be updated as Mozilla releases updates?

---

### Post by shuttleworthwannabe on 2012-05-10
Ikey--does this kernel have the patch for Intel chips--v3.0.0 overheats and fans just blows. I will take it for spin if this problem is resolved.

---

### Post by Zato-1 on 2012-05-11
> **Uncle Spellbinder said:**
> Looks very interesting. Though I'd prefer a rolling-type release, I may just have to try this out.

Will Firefox continue to be updated as Mozilla releases updates?

Yes, Firefox will continue to be updated, just like any other most commonly used applications. As for the SolusOS release type, Ikey has something nice planned for the future :)

---

### Post by Uncle Spellbinder on 2012-05-11
> **Zato-1 said:**
> Yes, Firefox will continue to be updated, just like any other most commonly used applications. As for the SolusOS release type, Ikey has something nice planned for the future :)

Hmmmmm. "something nice planned for the future" - my curiosity is in high gear. :)

Any word an when a 64 bit release is due?

---

### Post by VanR on 2012-05-11
> **Uncle Spellbinder said:**
> Hmmmmm. "something nice planned for the future" - my curiosity is in high gear. :)

Any word an when a 64 bit release is due?

Probably any day now. I'm running the 32-bit final version while I'm waiting for 64-bit. I like it very much. Having some problems with flash in firefox on youtube, but not that big of a deal. I'm sure it will get worked out eventually.

---

### Post by ikeydoherty on 2012-05-15
Regarding the 64-bit it will be out in the next week or so.
Work has already begun and I've built most of the packages
already :)

It will feature the same kernel config and optimisations and I gotta
say its ungodly fast!!

---

### Post by malspa on 2012-05-15
@ ikeydoherty - Very pleased to see this distro out there. I might never even install it -- no real attachment to GNOME 2 here -- but I do love Debian Stable and anything based on it (pretty happy with Stable, Mepis, and SalineOS right now). SolusOS looks great, from what I've seen of the screenshots and from the various comments about it that I've read.

For anyone interested, along with the screenshot tour at the solusos.com site, there's a nice one here: [http://gnuman.com/solusos-1-screenshots/](http://gnuman.com/solusos-1-screenshots/)

I do believe that SolusOS is gonna quickly become one of the most popular distros in LinuxLand. Great work!

---

### Post by TBABill on 2012-05-15
The age of apps and older kernels in Debian Stable have been reasons some users stick with more regularly released distros, but it looks like Ikey has bridged the gap between an aging distribution with newer kernel, apps, etc. That's a perfect blend when a user wants stability without feeling a bit behind in the age of their browsers, office apps and other items that improve and release frequently.
 
Time for a VM to test this one out. Easy proprietary driver installation on Debian and low resource usage? And codecs included? And built off a stable release and no chaos of LMDE's update process maturation? From the looks and sounds of it you could have quite a winner on your hands. Once the 64 bit version drops I'll be testing for sure!

---

### Post by Antman on 2012-05-15
> **ikeydoherty said:**
> Regarding the 64-bit it will be out in the next week or so.
Work has already begun and I've built most of the packages
already :)

It will feature the same kernel config and optimisations and I gotta
say its ungodly fast!!

Awesome!! Can't wait to get the 64bit version on my Dell!!

:guitar:

---

### Post by Uncle Spellbinder on 2012-05-15
Out of curiosity, what real difference is there between 64-bit and 32-bit? I'm running 32-bit SolusOS Eveline and it's pretty damned solid. Will I notice any improvement by replacing my 32-bit install with a 64-bit install?

---

### Post by forkandles on 2012-05-16
For Classic Gnome lovers and Desktop users everywhere it is worth giving SolusOS a test run in a spare part of your hard drive.

SolusOS also has a First Run Wizard with firewall and graphics driver options etc.

I am using it at the moment and apart from crashing flash, everything works just fine.
There is a simple solution however.

In terminal:
Code:
sudo rm /etc/adobe/mms.cfg


Here are 3 reviews of SolusOS:

[http://kbd-thinkingoutloud.blogspot.co.uk/2012/05/solusos-debian-stable-for-everyone.html](http://kbd-thinkingoutloud.blogspot.co.uk/2012/05/solusos-debian-stable-for-everyone.html)

[http://www.linuxandlife.com/2012/05/solusos-eveline-review-awesome-debian.html](http://www.linuxandlife.com/2012/05/solusos-eveline-review-awesome-debian.html)

[http://www.mikeermel.com/](http://www.mikeermel.com/)

The third one gives background info for SolusOS and its developer, Ikey Doherty, formerly with Linux Mint Debian Edition.

Extract:
&#8220;.... where SolusOS really shines is how it provides a steady foundation, but uses current releases of software packages. 
So everyone using SolusOS is getting the best of both worlds&#8201;&#8212;&#8201;a very stable distro that offers current and fresh applications&#8221;.

Ikey also comments:

**We'll** **be using Gnome 3 classic mode with a lot of modifications**. **It will look and act exactly the same as our Gnome 2 setup**, requiring no hardware acceleration. I've begun porting the older panel/applet libraries to use GTK3 and D-BUS meaning we won't lose any of the functionality previously found.
Long story short, **you'll be using the latest system and you won't be able to tell the difference**".

---

### Post by ikeydoherty on 2012-05-16
The 64-bit, even on my feeble little laptop, is seriously drawing all the juice
it can. I'm personally astounded by the performance, so I would say if you
have the 64-bit capability a switch would definitely be in order.

Just a sidenote, I sincerely regret not involving myself with the Ubuntu
community a lot sooner than this, it is a most welcoming and friendly
community. Kudos to you guys.

---

### Post by TBABill on 2012-05-16
Ikey, if the success of LMDE and your work on Mint KDE (and many fans following them) are any indication, SolusOS will rise quickly in popularity. Debian speed with Ubuntu-type ease of use with drivers...exactly what so many have hoped for.
 
Curious question...how good is font rendering in SolusOS compared to Ubuntu? Debian's fonts improved some time ago, but if memory serves me correctly Ubuntu's font rendering still had a bit of an upper hand.

---

### Post by Zato-1 on 2012-05-16
> **TBABill said:**
> Ikey, if the success of LMDE and your work on Mint KDE (and many fans following them) are any indication, SolusOS will rise quickly in popularity. Debian speed with Ubuntu-type ease of use with drivers...exactly what so many have hoped for.
 
Curious question...how good is font rendering in SolusOS compared to Ubuntu? Debian's fonts improved some time ago, but if memory serves me correctly Ubuntu's font rendering still had a bit of an upper hand.

SolusOS has Ubuntu font rendering by default. :)

---

### Post by Uncle Spellbinder on 2012-05-16
> **ikeydoherty said:**
> The 64-bit, even on my feeble little laptop, is seriously drawing all the juice
it can. I'm personally astounded by the performance, so I would say if you
have the 64-bit capability a switch would definitely be in order.

Thanks, Ikey. Really looking forward to the 64-bit release then. I'll do a fresh install. ;)

---

### Post by ikeydoherty on 2012-05-23
Just released the RC1 of SolusOS Eveline 64-bit :)

---

### Post by irv on 2012-05-23
> **ikeydoherty said:**
> Just released the RC1 of SolusOS Eveline 64-bit :)

OK, I just burned the DVD and booted into the Live OS, and it looks good. I only have one issue, but it is the same with any of the Ubuntu releases. I have a Dell Inspiron 1521 and the problem is the wifi card. Not Solus fault. If and when I install it, I have a fix for that problem but I have to be on the wire to fix it and right now I am on my wireless.
I wish I would have seen this Thread yesterday because I just cleaned up my hard drive and enlarged one of my partitions by deleting one. I went from 4 partition to 3. I may try to install it on a new 32gig SD card if my BIOS will boot it. Right now I am running Ubuntu 12.04 w/Unity, (loving it) and Ubuntu Studio 12.04 w/Xfce and Windows 7 (which I never seem to use but it is paid for so I keep it around).
With that said, all I can say is Look'en Good.

---

### Post by sdibaja on 2012-05-23
> **Uncle Spellbinder said:**
> Hmmmmm. "something nice planned for the future" - my curiosity is in high gear. :)

Any word an when a 64 bit release is due?

RC1 was released today (Wednesday, May 23 2012)
It is running very well, total migration was easy... some things are even noticeably faster than the speedy 32bit version

RC2 is probably going to be released tomorrow.

---

### Post by irv on 2012-05-24
I checked my BIOS and I won't be able to boot from my SD card so I will pick up a USB memory stick and install it on there. I don't want to re-do my hard drive again to install it there. I want to do this just for testing and am going to keep Ubuntu with Unity as my main OS. I have had this version since the release of Alpha 1 back in December. I know there are people who do not like Unity, but I have really grown to like it and now I don't want to be without it.

---

### Post by irv on 2012-05-25
OK I ran out yesterday and picked up a 8gig USB memory stick and installed Solus on it. I had a little problem with my wifi card but got it working. I am using a Dell Inspiron 1521 with a Bcom card 4311. Before going through the steps I needed I forgot to install DKSM which is in the package manager. It wouldn't hurt to include in the main install. I believe it is needed by some wifi card to install the card driver.
After doing this these are the steps I followed:
1. I uninstalled “bcmwl-kernel-source” package,

```
sudo apt-get remove bcmwl-kernel-source
```

2. I installed “firmware-b43-installer” package

```
sudo apt-get install firmware-b43-installer
```

3. I installed “b43-fwcutter” packager

```
sudo apt-get install b43-fwcutter
```

4. I typed into the terminal:

 ```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

This was the out put:
> # which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

This got the wifi care going.
The only other problem I had was when I shut down the computer it hung on the shut down and I had to run a fix on the memory stick. But it is fix and working again.
Over all it looks good and I will play around with it more but in the meantime I will still be using Ubuntu 12.04 Unity. which I love.

---

### Post by Dlambert on 2012-05-25
If they could make debian testing look that good...then I'd download it. But the age of apps bother me.

---

### Post by sdibaja on 2012-05-31
age of apps = Stable
You can install any bleeding edge app you like

testing vs solus (Stable)... kinda like comparing White and Black?

---

