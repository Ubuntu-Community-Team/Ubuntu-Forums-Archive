---
title: "Upgrade to Feisty from DVD (using Dapper)"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2007-08-11
I'm using Dapper on my notebook, dual-booted with XP. I have Feisty on a magazine DVD and want to upgrade in the simplest way possible.

The DVD is bootable, that is I can install directly from DVD, but I want to upgrade, rather than clean install.

Any suggestions?

---

### Post by bwtranch on 2007-08-11
Clean install is recommended. The reasons for that are too numerous to mention. But, you can trust me on this one.

---

### Post by bwtranch on 2007-08-11
Oh, I just noticed you are from Australia. I LOVE Australia! I used to listen to the Brisbane radio over the internet. I am going to get there some day. If they ever let me out of this country. Maybe I could immigrate to Canada and then get out that way, or maybe Alaska.

Sorry, not to make this off topic. Make sure that you update your dependencies in Synaptic after the upgrade. There, that should do it :)

---

### Post by Ptero-4 on 2007-08-11
You should really install clean instead of updating, the reason is that from dapper to edgy they changed the sysv init system to upstart and dist-upgrade always chokes because of version conflicts on several init-dependant packages.

---

### Post by bwtranch on 2007-08-11
Wow dude that is awesome. Thanks! I could have thought of many reasons, but I didn't know about that one. Hat's off!

---

### Post by mdsmedia on 2007-08-12
Thanks guys. Clean install it is, then.

---

