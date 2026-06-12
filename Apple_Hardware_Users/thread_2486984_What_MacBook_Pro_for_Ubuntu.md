---
title: "What MacBook Pro for Ubuntu"
date: 2023-05-18
forum: Apple Hardware Users
---

### Post by roastedcoffeebean on 2023-05-18
Hi everyone. New to the forum here. 

As a personal project, I'd like to install Ubuntu on a vintage MacBook Pro. It's unclear to me what version is fully (or mostly) compatible and with all hardware working. I can see this documentation, but it seems to be out of date. 

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

From what I gather, the last MBP version that can run linux properly is 10,1 (albeit with caveats). There's not much documentation, and it seems in the documentation of other distros they have found out some extra workarounds.

Does anyone have any experience with this, and can recommend a MBP version?

Also, once I install an ubuntu version, will I be forever stuck in that kernel due to compatibility issues?

Thank you :D

---

### Post by nuke on 2023-07-19
Please note that the wiki says "it is recommended to install the latest official LTS Ubuntu version."

Suggestion is to use the most recent LTS version and use the Live version to try out how it runs on your hardware.  Of course it will run slower since it's running from USB or CDROM.

If it works OK, the use that version as to install.  

There are a number of guides that might be helpful.  I am starting on a similar quest to install Ubuntu on an older iMac so I know that there are a number of old (perhaps outdated) wiki pages.

---

### Post by DuckHook on 2023-07-20
> **roastedcoffeebean said:**
> …will I be forever stuck in that kernel due to compatibility issues?

Linux is actually pretty good at sustaining backward compatibility, so even the newest kernels ought to work for you.

However, if they do not, then it is a very bad idea to stick with an old, obsolete, EoL kernel. Since the kernel is the very heart and soul of an OS, EoL kernels are the most easily attacked and, once compromised, your whole system is open to the scumbags. One must never run a kernel that is out of support.

If your vintage MacBook Pro is so ancient that it cannot run a supported version of Ubuntu, then I would suggest trying something like Debian or Arch (though this last is not for the faint of heart)—or some other distro that still supports 32&#8209;bit architecture.

If you can't find anything current that will run on it, then I strongly suggest that you just retire it. It's not worth the high risk of getting pwned just to revive an old machine.

You could very well also find that, even with a safe supported kernel, the machine runs like a snail on downers and isn't worth your time.

---

