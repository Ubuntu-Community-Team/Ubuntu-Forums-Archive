---
title: "Boot problems after VMware server install"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Chamelion on 2007-06-02
I am running Feisty, celeron 2.8, 2 hard drives. second drive XP, 1 gig ram.
I recently installed VMware server through Automatix. 
I put 'Sabayon Linux' on it. It sort of worked, even though very slow and the VMware tools refused to install.
On next boot up things became a little strange. While booting VMware came up a lot and the boot process finally stopped saying that some drivers for VMware could not be found.
I had to pull the plug, started the computer again in "safe mode".  I then removed Sabayon but was not able to remove VM. 
After that the computer would boot again and I removed every last trace of VMware.
Now I frequently have the graphical boot up interface stopping about a third way into the boot process. When I press alt ctrl delete I get a message saying that alt,ctrl delete went to fast (That is not exact, but something to that extant) and then 'the computer will now reboot'. 
Then it stops.
After turning of by holding down the button for about 5 seconds and restarting the automatic boot will get me back in.
I am sorry if all of that sounds a bit confusing. Is there any way to repair the loader. I have Super Grub Disc but am not to sure how to use it. Feisty otherwise works much better for me then Edgy ever did and I really do not want to loose it.:(
I am still trying to get my head around command lines etc. and would need very detailed instructions. 
Thanx heaps in advance:)

---

### Post by ajmorris on 2007-06-02
> **Chamelion said:**
> I am running Feisty, celeron 2.8, 2 hard drives. second drive XP, 1 gig ram.
I recently installed VMware server through Automatix. 
I put 'Sabayon Linux' on it. It sort of worked, even though very slow and the VMware tools refused to install.
On next boot up things became a little strange. While booting VMware came up a lot and the boot process finally stopped saying that some drivers for VMware could not be found.
I had to pull the plug, started the computer again in "safe mode".  I then removed Sabayon but was not able to remove VM. 
After that the computer would boot again and I removed every last trace of VMware.
Now I frequently have the graphical boot up interface stopping about a third way into the boot process. When I press alt ctrl delete I get a message saying that alt,ctrl delete went to fast (That is not exact, but something to that extant) and then 'the computer will now reboot'. 
Then it stops.
After turning of by holding down the button for about 5 seconds and restarting the automatic boot will get me back in.
I am sorry if all of that sounds a bit confusing. Is there any way to repair the loader. I have Super Grub Disc but am not to sure how to use it. Feisty otherwise works much better for me then Edgy ever did and I really do not want to loose it.:(
I am still trying to get my head around command lines etc. and would need very detailed instructions. 
Thanx heaps in advance:)

before re-installing grub, try in a terminal:
```
sudo grub-update
```

---

### Post by Chamelion on 2007-06-02
I tried 
[HTML]sudo grub-update[/HTML]
It comes up with 'command not found', both in normal terminal and in root terminal.

---

### Post by Chamelion on 2007-06-02
Is it possible to uninstall Grub through Synaptic and reinstall? Would that possibly fix my problem?

---

### Post by ajmorris on 2007-06-04
> **Chamelion said:**
> Is it possible to uninstall Grub through Synaptic and reinstall? Would that possibly fix my problem?

yeah, in synaptic, do a **complete removal** of grub or grub2 whichever one you use, then install it again.

See if that works :)

---

