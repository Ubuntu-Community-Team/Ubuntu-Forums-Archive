---
title: "MacBook White (5,2) Freezes at Grub"
date: 2009-04-25
forum: Apple Hardware Users
---

### Post by zszinegh on 2009-04-25
Hello Everyone,
My attempts to run Xubuntu 9.04 (or 8.10) have so far been unsuccessful.

I have followed all the instructions found in the various threads for dual-booting OSX and Ubuntu. I have tried 32bit versions of Xubuntu 8.10 and 9.04, and 64bit 9.04. The installation goes fine (booting the LiveCD requires acpi=off) but after multiple reboots and selecting Linux from the reFlt menu, it always locks up as soon as the Grub menu comes up. Only way out is to powerdown.

This is a brand new MacBook, less than a week old. (4GB Ram, 250GB HD)

I have seen a few other threads mentioning this problem, but so far no solutions. If anyone has some insight into this, other than just pointing back to the same threads containing the various installation instructions, which I have read and re-read numerous times, it would be greatly appreciated.

Thanks
Miki

---

### Post by cyberdork33 on 2009-04-25
you can try booting via efi. Sounds like another unresolved issue with the 5,2 macbooks. Probably should file / add-to a bug

---

### Post by zszinegh on 2009-04-25
Thanks for the reply. How do I boot via EFI, are their instructions somewhere I can use?

Thanks

---

### Post by cyberdork33 on 2009-04-25
> **zszinegh said:**
> Thanks for the reply. How do I boot via EFI, are their instructions somewhere I can use?

Thanks
[http://ubuntuforums.org/showthread.php?t=1046568](http://ubuntuforums.org/showthread.php?t=1046568)

---

### Post by zszinegh on 2009-04-26
Thanks for the link, I was reading that yesterday. Can I do all the source compiling under OSX, (since I have X11), or do I have to do this on another Linux box? Any chance there is an precompiled version somewhere for OSX already?

Thanks

---

### Post by zszinegh on 2009-04-26
I've never download anything from SVN before, so I'm not sure exactly what and where to get it. I'm doing everything from my MacBook so I could use some guideance to get me going.

Or should I just wait until these issues get resolved with regards to the 5,2 MAcBook?

Thanks

---

### Post by cyberdork33 on 2009-04-27
> **zszinegh said:**
> I've never download anything from SVN before, so I'm not sure exactly what and where to get it. I'm doing everything from my MacBook so I could use some guideance to get me going.

Or should I just wait until these issues get resolved with regards to the 5,2 MAcBook?

Thanks
there are binaries posted in the EFI thread.

---

### Post by nvaytet on 2009-07-10
Hi there,

I had exactly the same problem on a dual boot with ubuntu on a macbook 5,2 and finally today someone fixed it for me.
Basically, for the dual boot OSX - Ubuntu you have to follow exactly the info here [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation).
But then, you have to install GRUB2 to replace GRUB. Don't know if you can do it directly after the install before rebooting (probably, would be more practical). Anyway, the way i did it was to shut down the computer after the Ubuntu install and then reboot onto the Ubuntu Live CD.
You should then chroot into your linux file system. Something like:
```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sda3 /mnt/ubuntu
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev /mnt/ubunutu/dev
chroot /mnt/ubuntu

```
The install GRUB2
```

sudo aptitude install grub2

```
It should ask you if you want to remove GRUB and install GRUB2, just say yes.
You might need to grub-update or something.
Then when you reboot, select linux from refit and grub2 menu should load. For some reason, i still have to edit the boot command (press 'e') to add "acpi=off" at the end of the command, but after that, ubuntu boots fine. I guess i'll try looking at the grub menu (/boot/grub/menu.lst) but it seems to me the acpi=off option is already there.

Hope this helps someone.

---

### Post by nvaytet on 2009-07-10
Hello again,

I figured out the "acpi=off" thing.
For some reason, they were present in the /boot/grub/menu.lst entries but not in the /boot/grub/grub.cfg entries. All i did was to add "acpi=off" by hand in the various entries of the grub.cfg file and it now works.

---

### Post by Kuhnaydeein on 2009-09-09
Hey guys, I know this is going to be kinda 'off-topic' but I'm an Education Technology Supply re-seller, and an associate's customer has asked for memory for a "Macbook 5,2" and we can't find what that means exactly.  Which model Number is it?

Any help would be greatly appreciated!

You can reach me directly at BRIAN at MACX dot com if you know the answer.  Thank You!

---

### Post by nock1 on 2011-07-09
add maxcpus=1 to the boot statement due to a bug. This is better than acpi=off

---

### Post by johnmurrayvi on 2011-07-10
> **nvaytet said:**
> Hello again,

I figured out the "acpi=off" thing.
For some reason, they were present in the /boot/grub/menu.lst entries but not in the /boot/grub/grub.cfg entries. All i did was to add "acpi=off" by hand in the various entries of the grub.cfg file and it now works.

Did you run ```
sudo update-grub
``` after you had added "acpi=off"? Which file did you add that to?

> **Kuhnaydeein said:**
> Hey guys, I know this is going to be kinda 'off-topic' but I'm an Education Technology Supply re-seller, and an associate's customer has asked for memory for a "Macbook 5,2" and we can't find what that means exactly.  Which model Number is it?

Any help would be greatly appreciated!

You can reach me directly at BRIAN at MACX dot com if you know the answer.  Thank You!

Should be 'MB881*/A'. RAM is 667 MHz PC2-5300.

---

