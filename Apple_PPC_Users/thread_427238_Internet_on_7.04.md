---
title: "Internet on 7.04"
date: 2007-04-29
forum: Apple PPC Users
---

### Post by i_a_coops on 2007-04-29
Well, I have Edgy on my dual boot powermac, but I hardly use it because it's internet connection is a liability, Firefox won't work, and unfortunately the connecion isn't reliably enough for Portage to update applications, or get a different web browser! GAIM works sporadically and when I ping google for example I generally get 2 out of 5 successful pings. I'm not looking for a fix, i've tried a lot to fix this, including everything everyone recommends about ipv6, but nothing seems to work!

Anyway, I was wondering if it was worth getting Feisty, or is it likely that I'll have the same problems? I'd value  someone else's opinion on this before I blow my next months download limit! Thanks.:) 

Oh yeah, one other thing, atm I have to start the machine up in network mode and hold down option to get into Ubuntu, I can't seam to make Bootstrap the default startup disk :( 


:guitar:

---

### Post by SectionThree on 2007-05-05
In Feisty, a sporadic internet connection is a quick fix. There should be a little network icon in the top menu bar by default. Click it and you'll get a menu that lets you connect if you aren't already (I don't think Edgy had that feature, but I could be wrong)

Anyway, to get the bootstrap running again do:

sudo ybin -v

If you see "/dev/hda# has been blessed with holy penguin pee," it means you're set.

If not, go here:
[https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)

---

