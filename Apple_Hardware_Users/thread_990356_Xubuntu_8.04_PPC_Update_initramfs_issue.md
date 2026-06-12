---
title: "Xubuntu 8.04 PPC Update initramfs issue"
date: 2008-11-22
forum: Apple Hardware Users
---

### Post by LaSelvaBeach on 2008-11-22
So, I've been running 8.04 successfully on my PPC iMac G3 (400 MHz, slot-loader) for about a few months now.  After installing the latest update and rebooting, my box goes into initramfs shell.  When I first hopped on the Ubuntu band wagon and ran into the initramfs i would just give up and try another version (Ubuntu/different versions) but after a few months, i have files that I don't want to lose!

How can I get my box back up and running again?  All of the initramfs issues that I have found up until now are in regard to new installation problems.

Any ideas?

---

### Post by stream303 on 2008-11-22
Interesting.  So even though you are way past the initial install, did you have to re-apply this:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%208.04%20PowerPc%20alternate%20install](https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%208.04%20PowerPc%20alternate%20install)

I'm not sure if the radeonfb reference applies in your situation with the ati rage card you might have...

Like you say, it may be something else...

---

### Post by LaSelvaBeach on 2008-12-12
howdy,

so i hadn't tried the cd/rescue solution from that link.  I just did and after getting to the liveCD prompt, i type "rescue" and am told "unable to open file, Invalid device".

Still no dice and I haven't found any similar issue.  Any ideas, anybody?

---

### Post by stream303 on 2008-12-12
Before it drops you into the intramfs-shell, does it give you an error message?  If so, what is the error?  Maybe we can pin it down that way.

---

### Post by LaSelvaBeach on 2008-12-12
It goes into yaboot, then the ramdisk loads, then the xubuntu splash screen starts, and finally it pops into initramfs.

---

### Post by stream303 on 2008-12-13
You could try stopping yaboot at the second-stage of the boot: prompt by hitting TAB.  Then at the commandline tell it not to use a splashscreen:

```
Linux nosplash
```

Maybe this will get you a bit further, but I wonder if continuing on with Xubuntu is worth it?

I see no download images available for Xubuntu 8.04, which makes me wonder if there are *any* updates coming down for it for those that do manage to upgrade!  Any 8.04 Xubuntu users getting updates??

Previously, Xubuntu abruptly stopped their beta program just a day or two short of actual release of 8.04, and nothing further came down the line.  That ticked me off taking us that close to release trying to test bugs, etc and then just dropping the whole thing without declaring an official release.  I think many just figured the last-beta should be considered the real Xubuntu 8.04 release.

Now, with Xubuntu Intrepid 8.10, there are definite problems just getting programs to execute properly even when the install is up and running.

I think that Xubuntu is a fine program, and the members really do put in a lot of hard work to polish XFCE for us, but I think they really just don't have the resources for it.  It is tough enough for Ubuntu, and perhaps even more so for Xubuntu - which is a shame since that is *precisely* the environment needed for low-mem machines like early G3 iMacs, etc!

At any rate, I'd be tempted to try with Ubuntu proper, and then maybe see if installing the xubuntu-desktop works a little better.

Frankly, I'm wondering if the smart move is to just use Debian's XFCE4 for powerpc in either stable Etch 4.0r5 or Lenny-Testing:

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

Just grab the XFCE4-specific CD-1 and you'll be good to go.

I've got nothing against Xubuntu themselves, but if the resources aren't there - they aren't there!

---

### Post by LaSelvaBeach on 2008-12-13
so i did go ahead and run through seeing what would happen with each of the tab options (live-nosplash, live-nosplash-ppc, etc) and still no results.

I can go into open firmware, can i do anything from there?

As fer other distros/flavors, I was on Xubuntu when I first begin this interesting voyage known as Linux, got enough RAM to support Ubuntu, and out of curiousity to see if my comp could run quicker/gooder, tried out the newest Xubuntu hence my current pickle.  I'll check out that Debien link I suppose, but does this mean that I lose all of the stuff that was on my computer?  I would have backed it up had I known that updates are possibly lethal to OS.

---

