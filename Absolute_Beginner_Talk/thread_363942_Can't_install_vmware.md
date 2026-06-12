---
title: "Can't install vmware"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Icarus3000 on 2007-02-17
I have searched the forums for hours trying to find a solution to my problem, but to no avail.  I hate to start a new thread on the topic, but since I haven't found a solution to my problem, I didn't know what else to do.

This is what I did:

sudo apt-get install vmware-player

It starts installing, but gets to a point where it says:

Starting VMware services:
   Virtual Machine Monitor          failed
   Virtual Ethernet                     failed
Module vmnet is not loaded.  Please verify that it is loaded before running this script.

After searching, I see that this isn't such an unusual problem, but the next step usually recommenced is to run /usr/bin/vmware-config.pl.  That's where I run into a problem, since "vmware-config.pl" doesn't seem to exist on my machine.

At this point, the "vmware player" now exists under Applications>System Tools, BUT when I try to load a vmx file, I get an error message saying "Could not open /dev/vmmon: no such file or directory".

Doe anyone have any advice on what I should try next?

Thanks!
Icarus

---

### Post by Icarus3000 on 2007-02-17
Nevermind... I solved my own problem.

First I completely removed any trace of any file called "vmware" from my computer.

Then I followed the guide here: [https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player) using the Tarball from the vmware website.

Now vmware installs and loads just fine.

Now I am having another problem though - windows XP won't boot through VMWare, as it freezes at a BSOD with an error message saying "STOP 0x0000007B".

I have read about this problem before, and have seen two suggested solutions. But neither seem to apply to me:

1.  Make sure scsi drive is set to FALSE in the .vmx file.  It is.
2.  Set the ide drive to the default in the windows xp hardware profile.  It is.

I'll keep searching the forums, but if anyone has a suggestion, I'd be happy to test it out!

Thanks again,
Icarus

---

