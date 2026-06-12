---
title: "Black screen boot &amp; repo AWOL on G5 single w/Hardy Heron."
date: 2008-05-29
forum: Apple Hardware Users
---

### Post by casbahdk on 2008-05-29
I am running Hardy Heron (PPC) on my G5 single, but have the following two issues:

1) When I boot, the screen blacks out until log-in prompt.
2) I am having problems with repositories going AWOL:
```
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-powerpc/Packages.gz  404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-powerpc/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I have tried both the "Main" and "Denmark" repositories.

Cheers,

---

### Post by stream303 on 2008-05-29
What machine is it exactly?
[http://www.everymac.com/](http://www.everymac.com/)

On my G5 iMac with an nvidia card, I had the same problem of black screen until gdm login.  That was cured by initially using the nosplash parameter at the second-stage yaboot boot: prompt (hit -tab- to stop the countdown) and issuing:

```
Linux nosplash
```

Now the dmesg scrolls by at boot time.  Maybe this will help. If it works we can make it permanent by putting it into /etc/yaboot.conf and issuing a ybin.

Ubuntu PPC is officially a port, so you may need to go in and edit our /etc/apt/sources.list file to point to the ubuntu ports at ports.ubuntu.com

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

then sudo apt-get update.

In my installation, all the ports now show up in the third-party tab, rather than the main tab in software sources.

---

### Post by casbahdk on 2008-05-29
My G5 is [here]("http://www.everymac.com/systems/apple/powermac_g5/stats/powermac_g5_1.8.html"). The ```
Linux no splash
``` didn't work. I still get a black screen. It does boot normally however, so I can't complain too much :)

The /etc/apt/sources.list file seems to point to the ubuntu ports. At least the "third party software tab in the Synaptic repositories prefs seem to point correctly to ports. The problem appears to be the radio buttons for main restricted, etc. under the "ubuntu software" tab.

Cheers

---

### Post by stream303 on 2008-05-30
Now that we're in port status, I don't think anyone is using the main software sources tabs anymore.  At least all of mine are unchecked.

Was that a typo with no splash?  It should be just one word,
```
Linux **nosplash**
```

Good deal on the nvidia card.  Have you looked into adding the FPDither option to your /etc/xorg.conf and see if the display looks just a bit sharper, especially in small details / fonts?

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        **Option          "FPDither" "true"**
EndSection
```

This really helps out low-to-mid range lcd's when using the opensource nv nvidia driver..

---

### Post by casbahdk on 2008-05-30
Yeah, that was a typo, doh!

What does the transfer to "ports" mean in practice for Apple hardware? Is this only PPC or is it a problem for Apple Intel boxes as well? I assume it means that the ports are given a lower priority? Will Ubuntu at some point stop supporting all Apple hardware?

Thanks for the xconf tip, it works like a charm :)

Cheers

---

### Post by stream303 on 2008-05-30
> **casbahdk said:**
> What does the transfer to "ports" mean in practice for Apple hardware? Is this only PPC or is it a problem for Apple Intel boxes as well? I assume it means that the ports are given a lower priority? Will Ubuntu at some point stop supporting all Apple hardware?

Like the Sparc port, it only means that you can't buy a commercial support contract from Canonical for it, and is now supported by the community.  Bugs in the port will no longer affect the release of the main architectures that you can buy support for.  It appears that as long as there are devs interested in the ppc architecture who continue to put out community-supported releases, we should be ok - and many Ubuntu devs are also Debian devs, so I think the community is healthy.  So now that means our sources will show up as "third party" rather than being in the main source tabs.  I'm not that worried about it - there are other fine ppc distributions, but no reason to panic and switch.  If anything, all the experience with Ubuntu is easily transferable to Debian, or Fedora, or other community-supported distros.  I see a lot of cheerleading for other distros based upon this lack of a clear definition of what's going on, but it hasn't seemed to stop any Ubuntu release for ppc yet.

> Thanks for the xconf tip, it works like a charm :)

I always recommend trying that if you have an nvidia card and using the opensource nv driver with a lower-quality lcd, regardless of architecture.  Apparently this might not be needed on very high quality lcd displays - I'd love to see the difference if any on an Apple Cinema display for example.

Glad the machine seems happier now...

---

