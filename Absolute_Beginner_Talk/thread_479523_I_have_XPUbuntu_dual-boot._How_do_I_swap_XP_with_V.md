---
title: "I have XP/Ubuntu dual-boot. How do I swap XP with Vista?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Get_Ya_Wicked_On on 2007-06-20
Can someone explain how I can do this?  I am going to have to mount the an iso image for Vista installation since I do not have a burner. But how can I erase my XP to have room to install Vista on?

Can I just tell the Vista installation to reformat my sda2 (XP) and install there, not touching ubuntu??

I am aware I will have to redo GRUB but I'm more or less concerned about it not wiping out ubuntu

---

### Post by Get_Ya_Wicked_On on 2007-06-20
bump

---

### Post by crispy_420 on 2007-06-20
I think you would just reformat the partition/drive with xp on it and go from there. And as you mentioned, you will need to redo grub as windows like to trash it.

What happens when you put the Vista disc in the drive when XP is running? Does it give you the option to "downgrade" to Vista?

---

### Post by Get_Ya_Wicked_On on 2007-06-20
Well, see that's the thing.  The actual Vista installation will be mounted on a virtual drive. 

i'm not too familiar with doing this, so I don't know if I can mount it, and then restart the computer and have it load the virtual drive. 

Also, couldn't I just get the Vista installation to wipe out XP's partion and do all that good stuff without it touching Ubuntu?

Appreciate the help....

---

### Post by whiteguysamurai on 2007-06-20
I would back everything up and start anew.

---

### Post by atria on 2007-06-20
It is not exactly a simple process, but here goes:
Boot windows vista, format your existing ntfs partition and install vista on it.

Your grub bootloader will break after that because vista will overwrite it. You'll need to reinstall grub. Boot into your ubuntu livecd and do these:

1) Mount your existing ubuntu partition
2) chroot into it
3) run source /etc/profile to reload env variables
4) execute grub-install /dev/sdx

where hdx/sdx is your bootable/primary hard disk.

---

### Post by Get_Ya_Wicked_On on 2007-06-20
Yeah, but can Vista just wipe out (and reformat for itself) an existing XP partion during its own install procedure?

And how does mounting an iso to a virtual drive work? After doing that, can I restart the computer and have it boot to Vista installation?

---

### Post by arpegiator on 2007-06-20
> **Get_Ya_Wicked_On said:**
> And how does mounting an iso to a virtual drive work? After doing that, can I restart the computer and have it boot to Vista installation?

Doh! Ofcourse not dude, a virtual drive is a software application.
How did you expect to run a software application from the bios? (thinking before you ask never hurt anyone, the word virtual should have been a BIG hint)

---

### Post by Get_Ya_Wicked_On on 2007-06-20
"Better to ask & be a fool than to not and be a bigger one."

What an ***.

---

### Post by Get_Ya_Wicked_On on 2007-06-20
Well in keeping with saying: does that mean it is impossible to install Vista via running it off a virtual drive?

Like I said, I don't know too much about mounting and to my knowledge Vista wouldn't be able to access, well do anything anyway, to the hard drive as it will be running while XP is booted.

---

### Post by arpegiator on 2007-06-20
> **Get_Ya_Wicked_On said:**
> Well in keeping with saying: does that mean it is impossible to install Vista via running it off a virtual drive?

yes, it's impossible.

---

