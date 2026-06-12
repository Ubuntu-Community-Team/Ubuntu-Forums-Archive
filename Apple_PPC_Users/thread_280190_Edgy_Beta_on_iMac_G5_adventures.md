---
title: "Edgy Beta on iMac G5 adventures"
date: 2006-10-19
forum: Apple PPC Users
---

### Post by mike_hore on 2006-10-19
Hi folks,

I posted an earlier version of these comments on the Edgy forum, but with no replies in nearly 24 hours I'll have to conclude that Mac folks just don't go there much  ;-)

Anyway, I've finally had time to install Edgy Beta on my iMac G5 (Rev A, 17" screen). The dreaded "freeze on install" is indeed fixed, and I can skip partitioning if I'm already set up just by choosing "manual partitioning" then accepting the given values.

However I'm a bit disappointed since a couple of other long-standing issues are still with us:

1. The fans still run at full speed. This has been getting batted around the forums for many months, including several posted fixes (which seem to involve kernel recompilation, and which I can't avail myself of since I'm only on dialup at present).

2. The preferred 1440x900 screen resolution isn't supported "out of the box". It doesn't appear in the list in the "Screen Resolution" dialog. I tried adding it in the Screen section of xorg.conf, but 1440x900 wasn't recognised and was ignored.  After a lot of trial and error, I now have a good fix for this, so I'll post it here as it might help others:

In terminal, do
sudo dpkg-reconfigure -fgnome -phigh xserver-xorg

The -fgnome gives you a proper gnome dialog instead of the primitive default one which I've never figured out how to use.  The -phigh prevents a lot of unnecessary questions being asked.

In the first screen of the dialog, DO NOT accept the default driver!  This will make X inoperable and you'll have no video.  Scroll down to "nv", which is the correct one.

In the next screen, check the resolutions you want.  That's it, you're done.  Once you reboot your new resolutions will be available.

But still, it would have been nice if this had Just Worked out of the box...

Cheers,  Mike.

---

### Post by mph66 on 2006-10-19
Does this fix the fan problem as well, or is there another workaround for that?

Thanks for posting this fix!

-Marc

---

### Post by stmiller on 2006-10-19
The fan control is NOT enabled in the kernel that ubuntu provides, for dapper and now also for edgy! But support is there in the kernel. Why they still have this problem, is a good question. Fedora, Suse, other all have this figured out. But not ubuntu.

Here is a how to (post #5) for recompiling a new kernel.

[http://ubuntuforums.org/showthread.php?t=232908&highlight=powermac+g5+fans](http://ubuntuforums.org/showthread.php?t=232908&highlight=powermac+g5+fans)


Bug report here:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34723](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34723)

I have been trying to figure out what exact person makes the ppc linux kernel images for ubuntu. I wish we could get this information to them!

What is worse is that the new Edgy disc does not boot at all on my powermac G5. I get a total kernel panic!

---

### Post by Saba on 2006-10-20
Sorry to bother... I d tried several times to follow carefully the steps with my iMAC, but right after i write "parted" it only appears 2 options where one is for the CD (V. 6.06) and the other is for apple, but is only 1kb ? so I do all the stps untill I have to write "resize MINOR....etc" and then I get the message: "Error no number selected".

I did disable Journal. Also when I run LIVE CD and I start to install, even though I go back when it gets to partioning, no shells appears and O have to open the terminal myself.

Im already thinking I have to bakup and start from scracht. But I give it my last chance wrinting to you to see if there is any other solution.
Actually after many trials I ended up installing Ubuntu from scratched but I cannot get the partiotion right to reinstall OSX. Is there any other way?


Thanx!
Saba

---

### Post by mike_hore on 2006-10-20
> **Saba said:**
> Sorry to bother... I d tried several times to follow carefully the steps with my iMAC, but right after i write "parted" it only appears 2 options where one is for the CD (V. 6.06) and the other is for apple, but is only 1kb ? so I do all the stps untill I have to write "resize MINOR....etc" and then I get the message: "Error no number selected".

I did disable Journal. Also when I run LIVE CD and I start to install, even though I go back when it gets to partioning, no shells appears and O have to open the terminal myself.

Im already thinking I have to bakup and start from scracht. But I give it my last chance wrinting to you to see if there is any other solution.
Actually after many trials I ended up installing Ubuntu from scratched but I cannot get the partiotion right to reinstall OSX. Is there any other way?


Thanx!
Saba

Hi Saba,

I'm not totally sure what you're trying to do, but here's what I did to get a dual boot system (OSX and Ubuntu):

1. Totally backed up my OSX system.

2. Ran the installer (it was Edgy Knot-1 I think).  Did "manual partitioning".  I can't remember sll the details now (I'm not at home) but I seem to recall there's a boot partition and another one for yaboot, then the Linux swap partition.  Then I allocated 12G for Linux (ext3), and all the rest as HFS+ for OSX.

3. Completed installation.  Ubuntu ran.

Of course OSX wasn't installed since partitioning had wiped everything.  I was able to reboot using my external Firewire backup drive, and Disk Utility could see the partitions on my main drive.  So then I could restore my OSX system to the right place, and I was in business!

To do any new installations now, I don't need to repartition -- when it gets to the partitioning step, I choose "manual partioning", and just accept the existing values.  OSX is unaffected.

HTH,  Mike.

---

### Post by LMP900 on 2006-10-21
Thanks for the information! Although I do not have plans to install Ubuntu (or any other OS for that matter) on my iMac G5 anytime soon, I'm glad that there are some improvements on the iMac front.

---

### Post by Torrance on 2006-10-21
Yep, the fans issue has been a longstanding bug that has been reported in Launchpad for the last three versions of Ubuntu! Considering the work-around is a simple tick-box when configuring the kernel, you would think this would be fixed!!

I will re-write my [iMacG5 How To]("http://ubuntuforums.org/showthread.php?t=248238") for the fans once Edgy comes out - hopefully even newbies will be able to get their systems nice and quiet (except those poor people with Rev C iMacs).

---

