---
title: "Linux Mint 11 hangs at &quot;Stopping Boot Sequence Auditing&quot;"
date: 2011-11-05
forum: Any Other OS
---

### Post by GaiChi on 2011-11-05
This is my first post here, so excuse me for that.

So yesterday I decided to mess with my Linux Mint installation. I don't remember the specifics, but I installed a shitload of software and also tried changing the bootup animation. I restarted my computer and it wouldn't load. The parts that stuck out for me in the code while booting up were the parts reffering to FnFX
```
...
Starting Battery statistics collector: battery-stats-collector.
Starting Toshiba hotkeys utils: FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel.
...
```

and the very ending. Everything else seemed normal.

```
...
 * Starting anac(h)ronistic cron
 * Stopping anac(h)ronistic cron
 * Starting anac(h)ronistic cron
 * Stopping anac(h)ronistic cron
 * Stopping boot sequence auditing

```

However, I investigated both of these leads but there was very little referring to these and the places that did, didn't work.

I'm relatively new to Linux in general (just over a month now) but I think I have a pretty good general idea of how it works. But I have honestly no idea what could be wrong.

---

### Post by Perfect Storm on 2011-11-05
Moved to Other OS/Distro Talk.

---

### Post by irv on 2011-11-05
> So yesterday I decided to mess with my Linux Mint installation. I don't remember the specifics, but I installed a shitload of software and also [COLOR="Red"]tried changing the bootup animation[/COLOR]. I restarted my computer and it wouldn't load. The parts that stuck out for me in the code while booting up were the parts reffering to FnFX

It sound like you messed something up with the tried changing the bootup animation. I believe the quickest way to fix this is to do a re-install and start from scratch. After you get every think going just install a few packages at a time this way if you have a problem you can isolate problems that might come up.

Also when you start changes things to do with bootup be careful if you don't know what you are doing, ask question first.

One thing you can try is to boot in recovery mode and run some utilities to fix installed software. And then try to reboot.

---

### Post by GaiChi on 2011-11-05
> **irv said:**
> It sound like you messed something up with the tried changing the bootup animation. I believe the quickest way to fix this is to do a re-install and start from scratch. After you get every think going just install a few packages at a time this way if you have a problem you can isolate problems that might come up.

Also when you start changes things to do with bootup be careful if you don't know what you are doing, ask question first.

One thing you can try is to boot in recovery mode and run some utilities to fix installed software. And then try to reboot.

I was afraid of that. I guess I shouldn't really complain though, I don't have too many files on that partition anyways.

Thats what I was doing normally, but I just went a little crazy yesterday, heh heh. :)

I read a tonne of forum posts and like how tos regarding it so I thought I understood it well enough, but I guess not.

That was actually the first thing I tried. :( Oh well! Thanks a lot anyways. :)

---

### Post by irv on 2011-11-05
Don't feel bad we all do things like this. I can't tell you how many times I messed something up, but if you don't try you will never learn. Right now I have 4 OS's on my laptop and I am always trying new ones.
Waiting for the beta release of Ubuntu 12.04 so I can bug test it.

---

