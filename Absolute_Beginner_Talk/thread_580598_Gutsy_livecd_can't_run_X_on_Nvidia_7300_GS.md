---
title: "Gutsy livecd can't run X on Nvidia 7300 GS"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by the_darkside_986 on 2007-10-18
I have not been able at all to get X to run from the liveCD of 7.10 properly. It uses the "nv" driver by default, so I expect a basic desktop with no fancy effects--but instead I get a blank screen that does not quit and kick me to another tty. There was an error in the x log file about "AIGLX: screen 0 is not DRI capable" but I fixed that by modding my xorg.conf file to disable aiglx and composite and even with no error messages in the log, I still get an empty black screen when trying to use X.

I have no idea how to fix it. I thought the CD might be bad but the check cd function didn't report any errors and the md5 of the iso was good. I'm redownloading from a mirror and I will burn it using Ubuntu's tools instead of my hacked up FreeBSD installation, which could be a problem.

But is there anything else I can do if the CD is actually valid and error-free? Others with nvidia cards say the "nv" driver worked just fine and loaded without compiz effects. Any help would be nice.

---

### Post by nonewmsgs on 2007-10-18
use the command md5 /media/cdrom and compare it to a md5 from a download site.  try vesa, but i'm still downloading my gutsy now.

---

### Post by radthad on 2007-10-18
I'm getting the same issues with on an ATI X1300 Pro.  If you're trying to install, rather than just using the LiveCD, the only work around I know right now is to install 7.04 and upgrade to 7.10.

---

### Post by the_darkside_986 on 2007-10-18
That sucks. Is there any chance that they will release a fixed live CD? I'm not about to try to do a dist-upgrade or waste time using the alt CD.  The servers are too overloaded for any package management stuff such as dist-upgrade and I'm afraid i'd be stuck trying to configure my wireless card without a GUI if I use alt-CD.

---

### Post by the_darkside_986 on 2007-10-18
> **nonewmsgs said:**
> use the command md5 /media/cdrom and compare it to a md5 from a download site.  try vesa, but i'm still downloading my gutsy now.

Sorry I didn't see your post. I tried vesa but it does the exact same thing. Blank screen, even if i turn off the AIGLX and composite options in xorg.conf.

[crap. can someone merge this double post? sry]

---

### Post by the_darkside_986 on 2007-10-19
I checked the CD so I'm sure the CD is working just fine.  I still can't get X to work though. Anyone have any suggestions on how to make not display a blank screen? I already disabled  AIGLX in the ServerFlags section and disabled "Composite" in the Extensions section, of xorg.conf? Anything else I should put in xorg.conf?

---

### Post by patrickthebold on 2007-10-23
> **the_darkside_986 said:**
> That sucks. Is there any chance that they will release a fixed live CD? I'm not about to try to do a dist-upgrade or waste time using the alt CD.  The servers are too overloaded for any package management stuff such as dist-upgrade and I'm afraid i'd be stuck trying to configure my wireless card without a GUI if I use alt-CD.
The Alt-CD doesn't really ask you any hard questions.  None about the network.

---

### Post by the_darkside_986 on 2007-10-23
Well it is no problem now since I finally fixed it by entering values from my Feisty xorg.conf. But there seems to be something terribly wrong with the xorg.conf generator... it guessed my monitor refresh rates wrong and wrote some stuff wrong. i'm using freebsd mostly now anyway since gutsy has too many problems at the moment.

---

