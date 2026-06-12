---
title: "Transfering Ubuntu to a new machine"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by opticsnake on 2008-03-20
I have an old computer with two hard drives. One has Windows XP on it and the other is Ubuntu. I boot using a GRUB screen.

I'm now building a new computer and will be installing Windows XP on the main HD. What I want to know is whether my Ubuntu drive will work in my new machine if I simply pull it from the old one and install the drive in the new one.  And if so, what other procedures/precautions do I need to observe?

I could reformat and reinstall but, I have a ton of data on my Ubuntu drive that I don't want to have to transfer elsewhere first. Any help would be appreciated.

---

### Post by Het Irv on 2008-03-20
It can be done, I know this from expericence.  When I did it, I had to get a bootloader for my Windows partition because I could not get GRUB to come up.  Once I got it to boot I didn't have any problems because of the transplant.

---

### Post by opticsnake on 2008-03-20
That's great! Do you happen to know a good location where I can get info on the windows bootloader or the process I need to follow in order to get it to work?

---

### Post by Het Irv on 2008-03-20
A friend had a copy of Acronis's bootloader that I "borrowed", but I don't dual boot any more.  I tried restoring GRUB over the Windows MBR, but it never seemed to work.  I am not sure where to point you on this one.

---

### Post by opticsnake on 2008-03-20
Thanks again for the help. I'll be trying this out this weekend. I'll be sure to post any progress that I make.

---

### Post by Het Irv on 2008-03-20
I'll keep watching, but I might not get back on till Monday.

---

### Post by JEdwardP on 2008-03-22
In a bit of a turn from the point of the original post, what is the best way to copy an existing Ubuntu installation from one hard drive to another in the SAME machine?

I started out with Ubuntu on a single, small hard drive, and now I'd like to copy that installation to the bigger drive I just added to the machine, then delete the original installation from the smaller drive.

Thanks in advance for any advice

---

### Post by Het Irv on 2008-03-24
One way to do this would be to Use QuickStart (see sig).  If you made a full backup of the orginal and then did a fresh install on the new, and restored the backup. That should work.

---

### Post by JEdwardP on 2008-03-26
Thank you, Irv,

I did the back-up, which Quickstart seems to have done remarkably well. Am I correct in assuming that a FULL backup automatically included GRUB, such that once I wipe the original installation from the smaller drive, I should have no trouble booting from the newer installation on the larger drive, or dual-booting if I eventually install WinXP on the smaller?

I ask because I'm not sure whether the fresh installation defaults to putting GRUB on the drive it's actually installing to, or on the original drive.

---

### Post by Het Irv on 2008-03-26
If the larger drive is the first drive in the boot order, that is where GRUB will be installed.

---

### Post by JEdwardP on 2008-03-27
Thanks again, Irv

Save for a mildly annoying side-effect of the Quickstart restoration, all went exceedingly well. So well, in fact, that I used the method on both my machines.

---

### Post by Het Irv on 2008-03-28
What happend with QuickStart?

---

### Post by JEdwardP on 2008-03-30
This isn't a bug, I'm sure, just a result I didn't expect in my ignorance of the program. I had expected the restore function to exactly restore my system to its previous state, which I've no doubt it would've done were I not in the habit of uninstalling about half a dozen of Ubuntu's default applications.

For example, I uninstall EoG and replace it with Mirage. Although QuickStart did restore my installation of Mirage, the fresh installation obviously included EoG. The restoration put back whatever config files  inform the system EoG was removed, but it could not remove the EoG files, which the fresh install deposited.

The result was that, although EoG's files were on my drive, synaptic reported it as not being installed, its menu icons were present but blank, and neither EoG nor Mirage were set as the default image viewer.

This set of circumstances was repeated for all default applications I had previously uninstalled (Tomboy being another example). As synaptic did not report these apps as installed, I had it install them, and immediately uninstall them again. This restored my system exactly to its previous state.

Thanks once again for your help. In the eight months that I've used Ubuntu as my primary OS, I've rarely failed to find or receive an answer to my questions in these forums.

---

### Post by Het Irv on 2008-03-31
Yeah, these forums are great. I am going to post your last post on the QuickStart thread if I don't see it when I read it in a few minutes, so that everyone using it knows about this action.

---

### Post by mdpalow on 2008-04-01
> **JEdwardP said:**
> This isn't a bug, I'm sure, just a result I didn't expect in my ignorance of the program. I had expected the restore function to exactly restore my system to its previous state, which I've no doubt it would've done were I not in the habit of uninstalling about half a dozen of Ubuntu's default applications.

For example, I uninstall EoG and replace it with Mirage. Although QuickStart did restore my installation of Mirage, the fresh installation obviously included EoG. The restoration put back whatever config files  inform the system EoG was removed, but it could not remove the EoG files, which the fresh install deposited.

The result was that, although EoG's files were on my drive, synaptic reported it as not being installed, its menu icons were present but blank, and neither EoG nor Mirage were set as the default image viewer.

This set of circumstances was repeated for all default applications I had previously uninstalled (Tomboy being another example). As synaptic did not report these apps as installed, I had it install them, and immediately uninstall them again. This restored my system exactly to its previous state.

Thanks once again for your help. In the eight months that I've used Ubuntu as my primary OS, I've rarely failed to find or receive an answer to my questions in these forums.

Hi...

What's you've mentioned with QuickStart isn't a bug, but simply a limitation in the TAR back-up function. Because QuickStart does ask you to restore Live CD first, you will get the default apps. in the restore. Since most people don't do a lot of uninstalling of the default apps., it probably isn't considered a big deal to most.

You could however, do a fresh install and get Ubuntu just the way you want it (WITHOUT having removed anything) to include all the programs you want.

Then make a QuickStart back-up of everything. Then go in and remove the apps you don't want. At least this way, your SPM config files would be right if/when you ever had to restore everything. Using this method, I would think you could restore everything and then go in and remove the half dozen apps you don't like and be done in a jif.

I won't be watching this thread, so PM me if you have any questions on QuickStart. I just came over here because I wanted to see what was going on when I read a post by Het Irv in my thread. :)

Thanks and good luck!

---

### Post by The Spy on 2008-04-18
Is it possible to just use the account transfer that is on the Live CD, and have it work?

---

