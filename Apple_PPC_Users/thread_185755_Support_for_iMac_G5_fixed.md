---
title: "Support for iMac G5 fixed?"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by gwon on 2006-06-01
Has support for the iMac G5 been fixed in this release?

Problems before:

[list][*]Sound server caused an unresponsive GDM login screen that could only be entered by finding a way into the file system and deleting esd.
[*]no thermal control, so the fans were on full speed (and sound) all the time.[/list]

---

### Post by comcor on 2006-06-01
I don't believe the thermal issue has been fixed.  I noticed when I first loaded the live cd, that the after a few minutes, the fans would slowly build up steam until they were full on, and not shut off until the system was rebooted.  This also happened when I loaded the alternative CD and went to install it manually.  I aborted the installation because there was no way I was going to run the G5 if I had to put up with the noise of the fans on full speed.

---

### Post by gwon on 2006-06-01
There is definitely a kernel patch available somewhere, I'll have a look into it.

---

### Post by glennric on 2006-06-01
I have been running Dapper on a G5 for some time.  However, I had to do remove the power pc sound module to avoid the inevitable lockup if anything tried to use sound.  It still doesn't work.  There is some fan control.  The fans will run for a few minutes and then be off for a few minutes at regular intervals.

---

### Post by anamorphic on 2006-06-02
This is a link to a patch for Hoary Hedghog which was supposed to fix the iMac G5 fan issue: [http://ozlabs.org/pipermail/linuxppc64-dev/2005-September/005629.html](http://ozlabs.org/pipermail/linuxppc64-dev/2005-September/005629.html)

Does anyone know if this has been incorporated into Dapper Drake, or is it still something we should add to our installations manually?

---

### Post by Torrance on 2006-06-02
Fan control is not fixed.

The LiveCD locks up at the same place 5.10 locked up - I think it's still the sound server issue. I haven't tried doing a standard installation yet.

---

### Post by Torrance on 2006-06-02
> Does anyone know if this has been incorporated into Dapper Drake, or is it still something we should add to our installations manually?

Thermal/fan control for 1st and 2nd generation iMacG5s is built into the 2.6.15 kernel but for some strange reason the Ubuntu devs haven't enabled it. It could be enabled by recompiling the kernel - but this is beyond most users and shouldn't be necessary.

---

### Post by ACoolie on 2006-06-02
The fan issue means nothing if we can't get passed the esd issue. I am still having issues with sound and it crashes at the login screen still. It actually logs in, but that is just due to the login timeout. Anyways, I tried crashed gnome and moved /usr/bin/esd to /usr/bin/oldesd, but that still didn't stop the crash. I'll try again later.

It is quite sad and disappointing how far Ubuntu has come but it still has no support at all for a large group (possibly the largest) of Mac users.

---

### Post by megabenman on 2006-06-04
There was a way to boot a live CD on an iMac G5 in breezy (fans still on full speed though). I don't remember how to do it, but I should have some notes about it somewhere.

If anybody knows what I'm talking about, does it work on dapper drake?

---

### Post by gwon on 2006-07-06
I'm bumping this in the hope that others (with more knowledge than me) find it just as rediculous that we still can't install Ubuntu on an iMac G5..

---

### Post by Lutz Mueller on 2006-07-06
having the same problem here, downloaded 6.06 desktop powerpc a couple days ago and regardless of what I try, I end up with a brown screen, a frozen cursor and my fans on high.

Haven't found a way to get a login, so I'm definitely stuck. This shouldn't be this hard.

My iMac G5 is 2nd gen (pre-iCam).

Lutz

---

### Post by RoadTripDK on 2006-07-07
This doesn't seem to only be the case with iMac G5's. I am experiencing the same problems with my G5 single (PowerMac 9.1) and I have heard of problems with G5 duals as well. Debian Sarge and Etch also have problems (some similar, some different). I am a big Debian fan and am playing a wait and see game at this point. Fedora Core 5 works without a hitch (sound is disabled), but I want my Debian based distro.

I find it hard to understand that developers can bring themselves to release a PPC version of (in this case) Dapper, when there are problems (bugs) carried over from one version to the next. I have also seen on the net (I think it was at [http://www.ppcnux.com/](http://www.ppcnux.com/) )  a rep from Cannonical stating that problems with the new installer were to be expected and that we as end users should be happy about the improvements that follow with the new installer.

If there are problems with Dapper, whether installer, thermal control, sound support or something else, it is called a bug and not an improvement as far as I am concerned.

Less spin, more self criticism and better product control please!!!

---

### Post by sirrahn on 2006-07-13
I agree, I have no idea how ubuntu can release this as a final version when it doesn't actually work - it would be better to simply not release the mac version, acknowledge that it's not ready, and save a lot of people from wasting their time.

---

### Post by rasec on 2006-07-13
Just out of curiosity, which kernel do you guys run on your g5? I read on a different thread that the kernel updates only install properly for people running g5's, and when I went to look for any differences between the g4 and g5 kernel installer scripts I noticed that there was only a smp kernel availble for the g5. You might want to verify that you're using that kernel even if you have a single processor. 

To see which kernel you're running, do a "uname -a" and it should say something like 2.6.15-26-powerpc.

---

### Post by gwon on 2006-07-19
We could probably give that a shot if the developers could get us a system that would let us boot as far as a terminal.

All that the developers would have had to do to get iMac G5's booted to a working gnome desktop (minus sound and with fans on full) would be to give the option to disable the sound daemon during installation. This would have been obvious if they had noticed **the exact same complaints** about the last release (which I had to release a howto ([click](http://ubuntuforums.org/showthread.php?t=130040)) for, just to get people to a useable desktop).

Obviously with no sound and fans on full it wouldn't exactly be perfect, but at least their **final** release would boot.

I'd like to know how the developers managed to miss that the PPC release of their product **doesn't run on most modern PPC computers**.

---

### Post by Torrance on 2006-07-25
**Has anyone managed to get Ubuntu up and running on an iMac G5??**

I can handle the lack of audio, and I can handle the lack of fan control (even though the kernel has fan control support)... but I haven't even been able to get a working system going (I had more luck with Ubuntu 5.10).

---

### Post by ebischoff on 2006-08-30
Hi all,

I have succeeded in having fan control on an iMac G5 work. The solution is described here:
[http://opensource.bureau-cornavin.com/fans/](http://opensource.bureau-cornavin.com/fans/)

It has been tested on a Yellow Dog 4.1, but that should apply to a Ubuntu distribution as well.

It requires you to recompile the kernel. Hopefully, the correct settings for the kernel would be defined in a next version of Ubuntu, making that need to recompile the kernel disappear.

I have heard about a solution to the sound problem too. I'm currently investigating it. If that works out, I'll publish it at the same address.

I hope that helps,

Ã‰ric

---

### Post by ebischoff on 2006-08-30
Hi all,

Yup, the sound can work too on a iMac G5. Method is explained at the same address.

I hope that helps,

---

### Post by mike_hore on 2006-08-30
I'll copy what I just wrote in another thread:

This bug is fixed in the current Edgy Knot 1 -- it was filed as bug 23445.  The screen resolution needs in terminal:
sudo dpkg-reconfigure -phigh xserver-xorg

but I haven't figured out how to actually use it yet.  The fan isn't fixed yet.

But at least some progress is being made (with a bit of agitation from several of us  :-)

Cheers,  Mike.

---

