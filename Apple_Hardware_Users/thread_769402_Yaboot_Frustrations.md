---
title: "Yaboot Frustrations"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by macminiman on 2008-04-26
Hi,
I'm running a Mac Mini G4 (1.25GHz) with 1GB RAM. I wanted to give Ubuntu another shot after being disappointed with previous versions. For once, the Desktop version (aka LiveCD) worked and I could explore Ubuntu Hardy Heron (8.04). I decided that I would install it to an external drive that is running on firewire. To make things simpler, I just wiped the disk and dedicated the entire disk to Ubuntu. Everything went well until it came to install the bootloader. It failed here and the syslog told me nothing. Thinking it could have been something to do with the Desktop cd, I downloaded the Alternate Install CD and tried to install it, but the same thing happened. Is there anyway to boot manually from the OpenFirmware and fix the yaboot partition? Is there a way to install yaboot manually from a rescue livecd?

Thanks so much for any help!
Craig

---

### Post by stream303 on 2008-04-26
Yep - you have to manually edit your external yaboot.conf.  Check this out from the archives where I put it on a small external firewire:

[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

You can use the "alternate" disk to get to a rescue prompt, just stop it at the second-stage boot: prompt, hit -tab- to stop the countdown and specify one of the options like

```
Linux rescue
```

and get to a root shell in /dev/sda3 

Hopefully there's something in that thread that'll get you up and running...

oops - you probably won't have to use the ofboot line anymore.. Don't forget to hold down the ALT/Option key upon boot to choose it after the ybin is successful..

---

### Post by macminiman on 2008-04-28
> **stream303 said:**
> Yep - you have to manually edit your external yaboot.conf.  Check this out from the archives where I put it on a small external firewire:

[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

You can use the "alternate" disk to get to a rescue prompt, just stop it at the second-stage boot: prompt, hit -tab- to stop the countdown and specify one of the options like

```
Linux rescue
```

and get to a root shell in /dev/sda3 

Hopefully there's something in that thread that'll get you up and running...

oops - you probably won't have to use the ofboot line anymore.. Don't forget to hold down the ALT/Option key upon boot to choose it after the ybin is successful..

Whew... Sorry it took me so long to respond. It worked! Finally, after a lot of head banging i'm in Ubuntu...now off to solve the other issues at hand :guitar:

And I'll give you a thanks if I figure out how.

---

### Post by stream303 on 2008-04-28
> **macminiman said:**
> And I'll give you a thanks if I figure out how.

Glad it worked!  Just being here is thanks enough. :)

One thing that is frustrating is that I can never seem to get nano to work properly in the rescue shell - for some reason I can't seem to find the right terminal emulation, ie TERM=vt100 etc.  I have to rely on vi, which I know, but I can't get that emulation to be perfect either, so there is a lot of editing, cat'ing to check, editing again ... :)

I'll have to experiment more to find the right terminal emulation to get nano right when in the rescue shell...

I'll have to pass the thanks on to the original guys that helped ME out with firewire here a few years ago..

---

