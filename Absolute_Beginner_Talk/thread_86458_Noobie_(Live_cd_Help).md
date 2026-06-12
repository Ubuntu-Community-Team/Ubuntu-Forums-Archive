---
title: "Noobie (Live cd Help)"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by R@tman on 2005-11-05
Ok im new to linux and would like to learn about it all i have ever used is windows.

I tried the live cd at 5.10 work and it worked fine .

i brought it home and tried it on this computer and it stopped at "starting Hot Plug Subsytem" i have no idea what this means ?

could someone please explain to me what it means ?


Regards  R@tman

---

### Post by Cufishing on 2005-11-05
Welcome.
Lets start at the begining. Do you have CD as first boot?
If not, you need to boot from CD on a cold start. 'Some' machines give you a boot sequence if you tap the F8 key during boot up.  If not, go into BIOS and set it for CDROM as 1st boot device.

Ensure network cable is plugged in, etc.

From the boot screen just hit enter, and allow it to run.

If it fails again, pyhsically inspect the disc for damage, it could have gotten scratched, and is no longer readable.

Lastly, not all disc's are created equal, your drive may not like it. Try another disc.

---

### Post by nsa_767 on 2005-11-05
Hey there, 

This is going to sound silly, but are you sure it has stopped at starting the hotplug sub-system? Sometimes this sub-system takes a very long time to start up, depending on how many usb-devices you have on your system.

Hot-plug, as I understand it, tries to recognise usb-devices connected to your PC. Thus, it might also be that you have some usb-device that Ubuntu really doesn't like. Though I somehow doubt that.

Just try and unplug some usb-devices, thing that you don't really need immediately (e.g. webcam).

---

### Post by R@tman on 2005-11-05
i have no probles with the cd it work fine 

Hello ok i managed to disable the onboard sound and i got past  the hotplug subsystem  but now it stops on my gfx card saying it cant load it (ATI x800XL)

---

