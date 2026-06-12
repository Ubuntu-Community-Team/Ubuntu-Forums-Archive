---
title: "Ugraded to 7.10 and crashed! help?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by AcademyKP03 on 2007-10-19
i'm an absolute beginner - please be gentle ... I've been using Fiesty for my business .... and absolutely ran into no problems .... so when I saw that I could upgrade to 7.10 I did so w/out hesitation .... I then rebooted and to my horror .... nothing came up .... the orange loading bar just sat there for about 5 minutes about 1% complete and then I recieved the following:

udevd-event [2776]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5Ubunutu7) Built-in shell (ash)

Enter 'help' for a list of Built-in commands.

(initramfs)

--------


So then I ran it in safe mode and it said this:

Alert!  /dev/disk/by-uvid/67f22f19-cd 93-4622-83880c01a44e423a4 does not exist.  Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5Ubunutu7) Built-in shell (ash)

Enter 'help' for a list of Built-in commands.

(initramfs)


PLEASE, ANY HELP OR ASSISTANCE WOULD BE APPRECIATED!

THANKS IN ADVANCE

Warmly,

John

---

### Post by Sef on 2007-10-19
> i'm an absolute beginner - please be gentl

If someone is not gentle with you, let a mod know and we will deal with that person.

> BusyBox v1.1.3 (Debian 1:1.1.3-5Ubunutu7) Built-in shell (ash)

GRUB got messed up.   It is probably pointing to something other than hda1 or whatever boot device you have.

Options:

1) Go into GRUB and change it so is booting to the correct device.

2) Download [Super GRUB Boot Disk ]("http://supergrub.forjamari.linex.org/")and reinstall GRUB.

3) Read [Recovering Ubuntu after Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub").   It has various ideas including using Super GRUB.

---

### Post by AcademyKP03 on 2007-10-19
Okay,

so what is that program (super grub) that you described?  How do i make it run when I can't get the OS system to boot?

Do i download it - burn it onto a CD?

Just wondering ... remember, complete newbie here ........

thanks

---

