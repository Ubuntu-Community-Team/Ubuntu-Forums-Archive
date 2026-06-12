---
title: "Flash broken again"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by DMK62 on 2008-04-09
Wasn't sure where to post this so move it if necessary.

It appears that the issues with the flashplugin-nonfree is back again. It's the md5sum error and message that the plugin is NOT installed. I checked launchpad and its currently confirmed.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

From a recent post by Saïvann Carignan

Setting back to confirmed in Gutsy and Hardy, md5sums mismatch happens again because of new 9.0.124.0 release.

Let's hope this one gets fixed asap.

Dale

---

### Post by gandaran on 2008-04-09
> **DMK62 said:**
> Wasn't sure where to post this so move it if necessary.

It appears that the issues with the flashplugin-nonfree is back again. It's the md5sum error and message that the plugin is NOT installed. I checked launchpad and its currently confirmed.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

From a recent post by Saïvann Carignan

Setting back to confirmed in Gutsy and Hardy, md5sums mismatch happens again because of new 9.0.124.0 release.

Let's hope this one gets fixed asap.

Dale

thanks for the information, I just installed the new 9.0.124 version, it's very easy to install, all you have to do is uninstall your current flash and disable ubufox firefox extension, go to youtube or any flash webpage and click install on that missing plugin message, it installs in the home .mozilla plugins folder.

---

### Post by joshrobinson on 2008-04-09
i run hardy, and the new updated version just came through the repo's not too long ago
should be there soon

---

### Post by Crafty Kisses on 2008-04-09
Hopefully soon they get it fixed, I really thought this issue was annoying in 7.10.

---

### Post by joshrobinson on 2008-04-09
> **Codename said:**
> Hopefully soon they get it fixed, I really thought this issue was annoying in 7.10.

its even more annoying running 64bit...

there should be a new package in gutsy anytime
but if anyone running gutsy is impatient and whats to fix this themselves, you can patch it yourselves

this howto: [https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=(debdiff)]("https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=(debdiff)") tells you how to fix a package with a .debdiff file

and heres the .debdiff file you would be using
[http://launchpadlibrarian.net/13270881/flashplugin-nonfree_9.0.124.0ubuntu1_gutsy-proposed_rev2.debdiff]("http://launchpadlibrarian.net/13270881/flashplugin-nonfree_9.0.124.0ubuntu1_gutsy-proposed_rev2.debdiff")

the debdiff file is thanks to xtknight over at launchpad
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/214341]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/214341")

---

### Post by Crafty Kisses on 2008-04-09
Yeah, I run Dapper on my desktop, so I really don't have a problem with my desktop, which my desktop is my main computer, but my laptop runs 7.10, and when I went anywhere I couldn't use flash sites, it was really annoying, but they fixed it, so I was cool with it.

---

### Post by joshrobinson on 2008-04-09
> **Codename said:**
> Yeah, I run Dapper on my desktop, so I really don't have a problem with my desktop, which my desktop is my main computer, but my laptop runs 7.10, and when I went anywhere I couldn't use flash sites, it was really annoying, but they fixed it, so I was cool with it.

why are you still running dapper if you dont mind me asking?
because of the LTS support?

---

### Post by Crafty Kisses on 2008-04-09
> **joshrobinson said:**
> why are you still running dapper if you dont mind me asking?
because of the LTS support?

Yeah, and plus for some reason I like it better than 7.10, not sure why, but when Hardy comes out, I'll be switching, it's time for me to switch, also Kiba-Dock runs with Dapper, which is cool, I really wish Kiba-Dock would run with 7.10, but yeah you're right, mostly for the LTS.

---

### Post by Baby Boy on 2008-04-09
Argh, this damn flash plugin doesn't work for me. I've downloaded and installed the following version after the one that Ubuntu recommends (9.04 something) didn't work:

flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb

Alas, even with that, when I try to play a YouTube video I get the message I should install Flash. Please give me a hand here.

Distro: Ubuntu Gutsy Gibbon 7.10 64bit

---

### Post by gandaran on 2008-04-09
> **Baby Boy said:**
> Argh, this damn flash plugin doesn't work for me. I've downloaded and installed the following version after the one that Ubuntu recommends (9.04 something) didn't work:

flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb

Alas, even with that, when I try to play a YouTube video I get the message I should install Flash. Please give me a hand here.

Distro: Ubuntu Gutsy Gibbon 7.10 64bit
 
to late my friend, if you have a amd64-bit ubuntu version, you'll have to wait until the package is fixed, uninstall any bad flash package installed now and when the fix comes out, update synaptic first or use this command « sudo apt-get update » so you can have access to the fix then install the flashplugin-nonfree in synaptic

---

### Post by Baby Boy on 2008-04-09
> **gandaran said:**
> to late my friend, if you have a amd64-bit ubuntu version, you'll have to wait until the package is fixed, uninstall any bad flash package installed now and when the fix comes out, update synaptic first or use this command « sudo apt-get update » so you can have access to the fix then install the flashplugin-nonfree in synaptic
Shoot. The 9.0.124 version that supposedly works is only available as the 32bit version. Can't I at least *downgrade* Flash and install some of the previous versions that do work? Some time ago when I was still using Ubuntu 7.10, Flash worked fine. Now after a rather lengthy period of Windows comeback, I switch to Ubuntu again and bam - I'm just in time to get the broken flash. #-o I've uninstalled this broken version by the way.

---

### Post by joshrobinson on 2008-04-09
did you try patching it with the instructions i posted on the first page?

---

### Post by mocha on 2008-04-09
I haven't tried with this latest 124 version, but do you guys know that you can simply go to Adobe's flash download page and get whatever version you want, open the deb with an extractor, take out the libflashplayer.so file and move it to the directory that your web browser looks for plugins in.  I do this to test the new versions.  Just rename the end of your older version in case you need to go back to it, like libflashplayer.so.r48 or something like that.  This is also a good way to use different versions of the plugin with different browsers.  Opera is broken with 115 but Firefox isn't, so I use 48 with Opera and 115 with Firefox.

---

