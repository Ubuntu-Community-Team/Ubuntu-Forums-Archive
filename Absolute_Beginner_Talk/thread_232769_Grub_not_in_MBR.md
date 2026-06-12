---
title: "Grub not in MBR"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by kokotullio on 2006-08-09
Is it possible to place grub in another place than that ?
I prefer to use other boot-managers to handle the system.
With 6.06 version I'm not able to do that.
It's the ONLY defect, both in Ubuntu, Kubuntu and Xubuntu.
Hello to you all. (Was my first post);)

---

### Post by steve.horsley on 2006-08-09
Not possible to install elsewhere with the live CD installer. I believe that the "alternateve" text mode installer gives the option of putting grub on a floppy, or in the root partition of the Ubuntu install, in which case other bootloaders can boot the Ubuntu partition which then runs the grub bootloader.

---

### Post by wjp.reg on 2006-08-09
> **kokotullio said:**
> Is it possible to place grub in another place than that ?
I prefer to use other boot-managers to handle the system.
With 6.06 version I'm not able to do that.
It's the ONLY defect, both in Ubuntu, Kubuntu and Xubuntu.
Hello to you all. (Was my first post);)

I was under the impression that if you create a /boot partition (of a 100MB or a little more; along with / and /home let's say), ubuntu will install there, therby avoiding your MBR.

I had a similar concern not to disturb the windows MBR on my laptop with a factory restore partition.

I now have a dual boot system using the above.

---

### Post by kokotullio on 2006-08-09
I've tried. Forced because I had a third partition formatted ext3(an old ubuntu installation, I experiment ...), gparted pretend to mount. (usually I do /, /home and swap)
I choose to mount /boot. Finally grub jump on MBR just the same.
I must say I always prefer the old LILO.:(

---

### Post by kokotullio on 2006-08-09
> **steve.horsley said:**
> Not possible to install elsewhere with the live CD installer. I believe that the "alternateve" text mode installer gives the option of putting grub on a floppy, or in the root partition of the Ubuntu install, in which case other bootloaders can boot the Ubuntu partition which then runs the grub bootloader.
Loading I press esc then, if I choose enter, the boot is like the one in the first place(graphic), if I try to insert something else (eg. expert etc.) the system refuse asking for the REAL boot ...
I thought to achieve to text mode there. What I'm missing ??
:confused: 
Thanks.

---

### Post by kokotullio on 2006-08-13
The answer is : downloading the alternate install cd.:rolleyes:

---

### Post by cmmgmg on 2006-08-16
Just a few questions related to this situation:

[LIST]
[*]Was this omission of a choice to install to boot partition a conscious one, and if so what is the rationale behind this?
[*]Is there a possibility for the developpers to put that option into the installer for the next version? Is there a place where such a request can be made? (and has it been made already by others, or are there so few of us annoyed at this strange misbehavior of the installer?)
[*]Where to download that 'alternate version'? Only found links to 'regular' and dvd downloads (maybe didn't look lond enough though)
[/LIST]

Installing Mandriva and SuSE for a try-out was quite painless and let me the option to install grub in the boot partition. I would hope that one day the same could be said for future versions of Ubuntu.

Thank you.

---

### Post by TMR on 2006-08-16
I have left my Win MBR on Primary Hard drive intact.  I installed GRUB on a CF card (a floppy or CD would do).  I set the bios to boot from the CF card if it is present.  Then I can put the CF card in and boot Ubuntu, or take it out and it boots Windows.  If I didn't have ExtIFS installed on Windows (which lets me see the Ubuntu drive) you wouldn't even know ubuntu is there.

I explained how to do it on my CF card as boot key thread, which I started, but managed to figure out after a bit of work.  The main problem was booting windows, which needs to be mapped to (hd0) when your primary HDD will come up as (hd1) if you boot from another device.

TMR

---

### Post by TMR on 2006-08-16
PS: All those who want to do funny stuff with the MBR should be downloading the 'alternate install'.  I think Ubuntu is perfectly correct to have a basic install which doesn't ask about GRUB and MBRs which would mystify many new adoptees. If you want more control over the install, use the alternate install.  Maybe the only criticism of Ubuntu is that the download site should emphasise that the alternate install allows more control over the install but requires more knowledge.

<slight teasing>
But really, if you didn't find this option before you installed Ubuntu you were either in too much of a hurry to install a new O/S to be sure of doing it properly, or you don't know enough to be fiddling with GRUB.  (I learned the hard way!)
</slight teasing>

TMR

---

### Post by cmmgmg on 2006-08-17
[QUOTE=TMR]I think Ubuntu is perfectly correct to have a basic install which doesn't ask about GRUB and MBRs which would mystify many new adoptees.[/QUOTE]
I understand about 'hiding' more complicated stuff.
But there's not much reason not to hide these in an 'advanced' section, a quite common practice in software/os installations, rather than furnishing a separate install cd just to compensate for what should easily be available on the main cd/dvd.

So of course one can use the alternate cd (or dvd if there's one)... just scratching my head as to why they would, say, allow to install grub on a removable media as you did, and completely shut out the option to do a boot partition install, and reserve this for a special install cd.

[QUOTE=TMR]<slight teasing>
But really, if you didn't find this option before you installed Ubuntu you were either in too much of a hurry to install a new O/S to be sure of doing it properly, or you don't know enough to be fiddling with GRUB.  (I learned the hard way!)
</slight teasing>[/QUOTE]
heh... guess i had that coming. :rolleyes: 

In fact, was looking only at dvd versions and couldn't find it.
Now saw there were alternate *cds *(not dvds). My mistake. :redface: 

I might not be well-versed in *grubness*, I won't contest this. Which is one of the reasons to contain it in the os' boot partition and let my usual bootloader take over, as it does very well for the others.

As for being in a hurry. Well, never test-tried ubuntu, despite the hype.
So much for hurriness...

---

