---
title: "Linux Mint 14 boot freeze after upgraded to Gnome 3.8"
date: 2013-04-10
forum: Any Other OS
---

### Post by Ophie on 2013-04-10
After an exhausting search both on google and on the forum for some kind of answer to this problem, I still can't seem to get in the system as it hangs at boot loading. Specifically, the Linux Mint logo and the dots seem to load at first, but stop after a while and nothing happens. 
The only odd thing I did was upgrading from gnome 3.6.2 to 3.8 and doing a reboot. Since then it just doesn't want to play ball.

I tried adding nosplash noquite to the grub boot option, but after resuming boot I was greeted with a blank screen. So no tangible information as to what is causing the problem, it worked fine all day.

Some specifics: Asus core i3 laptop and radeon hd card with linux mint 14 cinnamon version with gnome environment.

EDIT: Managed to access the boot.log. It seems to be hanging on Checking battery state, though it gives the a ok. 

```
* Checking battery state...            [128G [122G[ OK ]
```

---

### Post by Vontux on 2013-04-12
> **Ophie said:**
> After an exhausting search both on google and on the forum for some kind of answer to this problem, I still can't seem to get in the system as it hangs at boot loading. Specifically, the Linux Mint logo and the dots seem to load at first, but stop after a while and nothing happens. 
The only odd thing I did was upgrading from gnome 3.6.2 to 3.8 and doing a reboot. Since then it just doesn't want to play ball.

I tried adding nosplash noquite to the grub boot option, but after resuming boot I was greeted with a blank screen. So no tangible information as to what is causing the problem, it worked fine all day.

Some specifics: Asus core i3 laptop and radeon hd card with linux mint 14 cinnamon version with gnome environment.

EDIT: Managed to access the boot.log. It seems to be hanging on Checking battery state, though it gives the a ok. 

```
* Checking battery state...            [128G [122G[ OK ]
```

I don't know if this would be of help, but I heard about a problem the guys on the Linux Mint podcast were having when playing around with Open Suse 12.3. One of them mentioned that there seemed to be some kind of bug in the latest version of gnome that caused it not to allow the system to boot if it ran into any errors and there was no other desktop environment to fall back on to boot into instead. When he installed with a kde disc and then installed gnome, gnome ran fine. Could you perhaps get it to boot into CLI mode and try apt-get to install mate or some other desktop environment to provide gnome with a fallback option?

---

