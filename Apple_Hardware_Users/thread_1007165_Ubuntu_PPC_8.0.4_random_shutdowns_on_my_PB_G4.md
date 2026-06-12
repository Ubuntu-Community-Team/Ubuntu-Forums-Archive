---
title: "Ubuntu PPC 8.0.4 random shutdowns on my PB G4"
date: 2008-12-10
forum: Apple Hardware Users
---

### Post by el_heffe on 2008-12-10
First off- thanks to everyone who got me to this point- I am  booting INTO ubuntu now and its wonderful.  Have some getting used to ahead of me, but I want this to work.  My setup is this;

&#8226; PB G4 1ghz 1.25g ram
&#8226; crap *** internet(im deployed to iraq...)
&#8226; Installed Gutsy, upgraded to 8.0.4

During the upgrade my computer would shut down.  Not a slow meandering shutdown but OFF like a light switch.  I am not sure which log exactly to look at but I looked at several and didn't notice anything overly odd.  This still happens wether I am sitting at the computer or away from it.  It seems only to happen during anything resembling an upgrade.

Not to sure where to go from here, and when I get back into my ubuntu side I will post the error I get when I do an upgrade now.  Oh- this is NOT a ram issue because this is only in Ubuntu when I am upgrading.  I have used my OS X side for years no issue and still no issue, but Ubuntu is being poopy.  So- I want to take the thorn out of its side and make it happy on my computer!  Thanks for any help solving my annoying shutdowns.

AFAIK this is not a duplicate, so roshambo me if it is.

---

### Post by el_heffe on 2008-12-10
OK, so I have booted into Ubuntu and it borked on me.  Not sure why but my network adapter crapped out and the windows were all sorts of out of whack.  in order to get the network working again I just restarted and started into the Gnome FAILSAFE session.  I took a screenshot to show what I was talking about in regards to the windows being weird.

The command I had to run before when I was having the upgrade issues was this:

sudo dpkg --configure -a

There was an error when I opened the update panel and it told me to do that.  I can post any logs needed now that I have access to them.
I was going to attach the screenshot, but it crashed firefox when I tried. *sigh*

---

### Post by tiresia on 2008-12-10
I'm sorry, that you got this problem upgrading your system. 
Sometimes it is better to reinstall a new system, instead of upgrading the old one.
If you don't find any better solution, you can just download Hardy for PPC and install it.
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
Do not forget to backup your /etc/X11/xorg.conf file before installing.
If you decide to install 8.10, be aware of this:
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by el_heffe on 2008-12-10
> **tiresia said:**
> I'm sorry, that you got this problem upgrading your system. 
Sometimes it is better to reinstall a new system, instead of upgrading the old one.
If you don't find any better solution, you can just download Hardy for PPC and install it.
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
Do not forget to backup your /etc/X11/xorg.conf file before installing.
If you decide to install 8.10, be aware of this:
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)
I have that and my yaboot.conf backed up, so heres to corssing my fingers. Just when I thought it was going well it shutdown on me.  Took a while(all afternoon) to download the 148mb in updates then it takes a nose dive.  Will keep at it and see whats what.  As for downloading the new system, something like that would be a lot harder for me than trying to upgrade because it is a nightmare to download anything larger than small chunks of the updates...

---

### Post by tiresia on 2008-12-10
There are also very small Installer-CD (Hardy is 14 MB)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
If your internet connection is stable, you can start from a minimal CD and download the system during the installation.

---

### Post by el_heffe on 2008-12-11
I will give the minimal a try.  I have narrowed the shutdowns to over heating.  I have noted that other people with PowerBook 12" have the same issues I have- overheating, lack of brightness control & sleep.  I will be home within a month or two, so I am debating on waiting until then when I have fast internet access that doesnt inject crap into my downloads.  I'll keep trying random stuff for now though.  :D

---

### Post by stream303 on 2008-12-12
Sounds like the cpu is running at 100% all the time. The cpu frequency scaler, powernowd, is often misconfigured.  About half-way down this page is the file you can edit to fix powernowd:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

There is a way to fix this, but the easiest way is to just download and install (via synaptic or apt-get) **cpudyn**  Installing this will automatically replace powernowd, and you should be able to see your cpu throttle down.

The other thing is that a rogue process is eating up the cpu, which you can check with top, or my favorite alternate, htop.

---

### Post by el_heffe on 2008-12-13
> **stream303 said:**
> Sounds like the cpu is running at 100% all the time. The cpu frequency scaler, powernowd, is often misconfigured.  About half-way down this page is the file you can edit to fix powernowd:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

There is a way to fix this, but the easiest way is to just download and install (via synaptic or apt-get) **cpudyn**  Installing this will automatically replace powernowd, and you should be able to see your cpu throttle down.

The other thing is that a rogue process is eating up the cpu, which you can check with top, or my favorite alternate, htop.

Thats a trip- just what I was thinking so I opened Synaptic and search for cpu and am installing that as we speak.  As for a rogue process taking my time- I generally am just updating or installing.  For example- just got xubuntu installed.  Really like it a whole whole lot.  The only question I have left is that there are these two weird black bars in my top Panel.  They have always been there, and they blink.  

Will report more after cpud is installed.  Hopefully it fixes my issue. \\:D/

---

### Post by el_heffe on 2008-12-14
OK, I installed cpudyn, restarted, and left it running with just evolution going while I slept.  Woke up and it was shutdown, so I'm still at a loss as to what the hell is shutting me down.  *sigh*

On the other hand- I love xubuntu!

---

### Post by stream303 on 2008-12-14
What worries me is that Xubuntu 8.04 is no longer available from the ports, and I even question whether updates are coming down for it - see my recent post about that.  If updates are coming down, they may not be the ones needed for the XFCE4 environment!  (I have not confirmed that yet)

It might be possible to catch something in the logs, but I have to honestly say that I don't think Xubuntu ppc has what it takes anymore.

And now that Xubuntu Intrepid 8.10 is available, quite a few users are having problems just executing files even when it is installed properly.

So what to do?  Give Debian's XFCE4 version a shot, which is still enthusiastically supported.  (Xubuntu is a custom XFCE4 anyway.)  All that you've learned here is nearly applicable to Debian anyway.

I'm the LAST person to just suggest switching distros, as I really find that a weak substitute for support, but in the case of wanting to work in the XFCE4 environment on ppc, I think it might be the smart thing to do.

If you want to try it, grab either the "stable" 4.0r5 Etch-n-Half release, or go with Lenny-Testing:

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

All you need is the first CD-1, and there is a special image just for XFCE4, which I'm sure you'll love if you liked Xubuntu - just scroll down to see it once you get to the images.

We've got enough issues on ppc as it is, and I'd hate to see you banging your head against the wall over possible desktop-environment issues in 8.04 and 8.10 that might not get worked out due to lack of resources.

---

### Post by el_heffe on 2008-12-14
Yar, I may just keep using this for now as-is.  I will be back home in a month or so and then I will have real internet again, not this "dail-up on a LAN" crap.  I will try out the Debian when I get home.  Thanks! :D

---

