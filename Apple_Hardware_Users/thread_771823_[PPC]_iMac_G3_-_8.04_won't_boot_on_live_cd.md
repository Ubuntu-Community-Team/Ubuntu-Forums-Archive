---
title: "[PPC] iMac G3 - 8.04 won't boot on live cd"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by ZomGie75 on 2008-04-28
I've tried several times to boot the live cd on my iMac G3.  When I boot it i do:
```
live video=ofonly
```
Which worked when I installed Ubuntu 8.04 on my iBook G4.  I get a screen full of system and hardware information of the computer listed along the left, and [OK] all along the right matched with all but 3-4 of them.
Do I just need to wait?  Or is there something else I need to do to get this loaded properly?

If you need any more information, please ask.

---

### Post by stream303 on 2008-04-28
Which G3 iMac do you have, and how much memory?  Have you tried the "alternate" non-live installer?  If you have a very early iMac, you may be running into either an 8gb or 128gb partitioning limit if you have upgraded the drive...

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

How did it work if you just used the defaults and let yaboot time out without any additional kernel parameters and continue on... ?

---

### Post by ZomGie75 on 2008-04-30
> **stream303 said:**
> Which G3 iMac do you have, and how much memory?  Have you tried the "alternate" non-live installer?  If you have a very early iMac, you may be running into either an 8gb or 128gb partitioning limit if you have upgraded the drive...

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

How did it work if you just used the defaults and let yaboot time out without any additional kernel parameters and continue on... ?

"iMac G3/266 (Fruit Colors) 266 MHz PowerPC 750 (G3)"

It just went to a black screen and doesn't load at all (no noises).  30 minutes later it is still at a black screen.

---

### Post by stream303 on 2008-05-02
How much memory is in that box?

This might help determine if you can run Ubuntu at all, use Xubuntu, or if it is very minimal ram at 128 mb or less, you might be better off with a custom server install with a lightweight gui.

Be sure to see this helpful faq:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Let us know how it goes!

---

### Post by keith.burgoyne on 2008-06-24
I have a similar issue with my iMac. I was able to install Xubuntu-Hardy without issue, using an alternate install disc from on of the Xubuntu daily builds of Hardy (taken after hardy went stable). When it tried to boot my computer on the new installation, however, it passed through yaboot normally, started booting the kernel, flashed a white screen and then immediately went black. I can hear the hard drive disengage and the screen shuts off. 

I'm not quite sure where the issue lies. 

Any tips are welcome. Thanks!

---

### Post by stream303 on 2008-06-24
G3's especially need manual configuration of their monitor frequencies in /etc/X11/xorg.conf file.  This means that after installation, you have to go back in and edit it.

At the second-stage of the yaboot boot: prompt, interrupt the countdown by hitting -tab- .  You can now type

```
rescue-powerpc
or
Linux single
```

to get to a single-user prompt.  When asked to where to drop yourself into a shell, typically start at /dev/hda3, and if that doesn't work, just try again and work your way up if you don't know where the root partition is.

Once you've got a shell, you need to edit the /etc/X11/xorg.conf file to use the known good monitor frequencies.

You can use ```
sudo vi /etc/X11/xorg.conf
``` or ```
sudo nano -w /etc/X11/xorg.conf
```

(If you don't know the vi editor, be sure to get some practice first, or just use the more graphical nano editor.  Note: on my machines, I couldn't get nano to work in single-user mode, so I had to rely on vi)

From there, you make edits to your file with the freqs shown in the previous faq something like this:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        [b]HorizSync   58-62
        VertRefresh  75-117[/b]
EndSection
```

In addition you may want to disable glx and/or dri as shown in the faq.  Even then, you may want to change your video driver in the Device section to either ati, radeon, or r128.

---

### Post by keith.burgoyne on 2008-06-26
Thanks for the quick reply!

I've done some digging and testing, and it seems that this issue happens before X even starts; the kernel doesn't finish booting before the system locks.

I tried installing only the base system from the Xubuntu Hardy disc. I was able to then boot the installation, but had no desktop environment. I installed all the XFCE4 packages:

```
apt-get update; apt-get install xfce4-*
```

But that left me with only a half-baked xfce desktop. To get X to start, I used stream303's xorg.conf suggestions, which worked very well (thanks!).

I then installed xubuntu-desktop, which pulled in a large number of packages (including a new kernel). After rebooting, the computer froze like usual. 

It looks like there is an issue with iMac g3s and the most recent Ubuntu PPC kernel (unsure of the version number, since I cannot start the iMac to check). By doing a base install and getting an older kernel, it seems the iMac will boot without issue. Is there a way to permanently tell apt to not update the kernel?

---

### Post by stream303 on 2008-06-26
That's the thing that worries me - the Xubuntu Hardy release you are using for a base install is only a late-beta, and no actual Xubuntu ppc hardy release has shown up, although they *may* be updating the xubuntu-desktop metapackages.

Since xfce4 seemed to work as a limited window manager, but when xubuntu-desktop metapackages are installed, it croaks, it may be pointing to the xubuntu-desktop and it's interaction with the system as a whole.  Hard to say.

Seems that Xubuntu is in a state of transition, so can you get by with an Ubuntu install, and reducing it's footprint by using wireframe-windows, using PcManFM as a file manager, etc?

I'd see if you can reproduce the problem with Ubuntu, as it may not actually be a kernel issue, but an interaction with xubuntu-desktop, which appears to have lost support with the xubuntu community for ppc.  I could be wrong, but the lack of a formal hardy release for Xubuntu ppc worries me.

---

### Post by avtolle on 2008-06-26
Stream303, I'm going to second your thought there. While "playing around" with my Cube which is dedicated to that function, I did a server install and put the full Xubuntu-desktop package on it. It froze my system, and until I removed it, no joy. Trying the minimal Xfce4 type install didn't create any problems, but I had other reasons to ditch it. Putting the full Ubuntu desktop package on top the server exhibited similar problems, BTW, while e.g., doing a Fluxbox installation as suggested in "my favorite Wiki page" ran just fine. I've wondered if it is gdm on the Ubuntu side that causes the problem; likely should have tried xdm with the bare-boned xfce4 install, but didn't. 

Sorry for the rambling nature of this.

---

### Post by stream303 on 2008-06-27
> **avtolle said:**
> Putting the full Ubuntu desktop package on top the server exhibited similar problems, BTW, while e.g., doing a Fluxbox installation as suggested in "my favorite Wiki page" ran just fine.

Now that's interesting.  Look at it this way - with a custom install using a server kernel with 8.04, at least the kernel is going to receive security updates for 5 years on your desktop box!  Depending on your security situation, this might be a good deal, even if your desktop software stopped getting updates 2 years prior. :)

As for Xubuntu-desktop locking up - don't forget that along with just the plain old xfce4 package, be sure to check out other xfce4-* accessories that might spruce things up just enough without having to load the xubuntu desktop for you...

> Sorry for the rambling nature of this.

Don't be - custom builds for ppc is a very nice way to go and can sidestep some of the problems that go untackled.  It calls into question the need for trying to duplicate 100% of the canned-distribution, when alternate solutions, especially for older/slower/quirky hardware might be the better choice.

I guess this might deserve a thread of it's own from a philosophical standpoint, but instead of trying to resolve a lockup issue for years, say in the fictitious case of Synaptic, could it be just as easy as doing it manually once a day, or put into /etc/crontab with this example of using the cli?

```
sudo apt-get update
sudo apt-get upgrade
```

Menus not working in your window manager?  How about:

```
firefox &
```

I guess you see where I'm going with this.  At some point, even Fluxbox can appear "bloated".

Maybe it was my turn to ramble. :)

---

