---
title: "How to compile xserver-xorg-video-nv for (L)Ubuntu 13.04"
date: 2013-05-15
forum: Apple Hardware Users
---

### Post by ccINC on 2013-05-15
Hi guys,

I wanted to give 13.04 a try Yesterday.
On 12.04 I could compile xserver-xorg-video-nv packages from the Natty archive repo's.
But (obviously) this isn't working for 13.04.
I need to have NV because Nouveau just isn't working for me.

After checking to see if the nouveau packages are installed, I checked xorg.conf to ensure that everything is set-up correctly.
And even if I boot with Linux nouveau.modeset=0 I get blurry/vague/ugly picture on my screen.

My machine is a Mac G5 dual core with Nvidia Geforce 6600.
Is there a way to compile NV on 13.04 from a current repository, I know there's no binary/.deb for PPC (hoping there is, but no such luck).
So can I please get some help, because I know the NV works for me.

Or perhaps someone else has another suggestion for me?

Many thanks in advance.

---

### Post by ccINC on 2013-05-16
Why is Nvidia always a problem for PPC Architecture and not for i686 or x86_64 Architectures?

---

### Post by str8bs on 2013-05-17
> **ccINC said:**
> Why is Nvidia always a problem for PPC Architecture and not for i686 or x86_64 Architectures?

Because you haven't fixed it and neither have I. :p The Intel/AMD folks have the proprietary driver option and there are more of them so more bugs likely get reported and actively worked on.
What I mean is the community hasn't fixed it. This is just my opinion.

Xorg -configure is deprecated. If one is using an xorg.conf file or extra boot parameters, they are using a WORKAROUND. NV is no longer supported which makes that also a workaround.
For every "type this" or "copy this xorg.conf" used without bugs being reported, there is no way the problem will be resolved. 
Granted, I acknowledge the pain and effort required to capture appropriate data for graphics related problems is a lot (maybe too much) to ask of most users.
I'm no where near a developer, but consider their perspective: A bug report that just says "blank screen" on Mac model whatever is like saying:"Hey Ms./Mr. developer, could you spend the precious time you are donating to dig through several thousand lines of code and take a guess at why my screen is blank?"
 I'm not saying there is anything wrong with helping each other out on the forums and noting workarounds, but developers can't solve problems or support hardware if they don't know it exists. In my opinion, those folks are miracle workers given what they accomplish with the information provided to them.

In short, if we care about support for certain hardware, our fate is in our own hands.
*note PPC graphics use the same chips as the others. They may have some quirks due to the fruit company's fondness for selling dongles, but it isn't like we are needing developers to completely rewrite drivers.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://wiki.ubuntu.com/X/Debugging](https://wiki.ubuntu.com/X/Debugging)

RE: your first post
I haven't tried NV on 13.04, but it may work better with nvidiafb. Worst case, you should always be able to revert to FBDEV with any card.
[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F)

Str8

---

### Post by ccINC on 2013-05-26
Many thanks in advance str8bs.
Very much appreciated.
Very much true NV is a workaround.
I'll most definitly will go and see if there hasn't been any bug filed allready (highly unlikely I think), but if not I will file a bug on Launchpad.

As for my Mac G5, I went back to 12.04, got the NV working and configured my yaboot.conf so I kinda workedaround too :)
Thanks again.

---

