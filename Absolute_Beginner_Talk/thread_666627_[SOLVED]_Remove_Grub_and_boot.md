---
title: "[SOLVED] Remove Grub and boot"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by amantonas on 2008-01-13
I've got a Dell Latitude cpx and It's messed up. My friend formatted the drive, and now grub has an error 22 whenever I try to boot it. So I think, I'll just install Ubuntu over it. So I pop in the disk, and it goes straight to grub. So I think I just have to go into the setup and change it so the CD boots first. So I go in, and It freezes. Is there anything that I can do to fix this stuff?

---

### Post by SOULRiDER on 2008-01-13
Installing Ubuntu will overwrite GRUB with a working one. 
Did it freeze when booting or did it not boot from the CD at all?

---

### Post by timbounceback on 2008-01-13
Have you tried Super Grub Disk?

---

### Post by amantonas on 2008-01-13
It didn't boot from the Cd, so I went in the bios setup, and It froze!

---

### Post by SOULRiDER on 2008-01-13
The BIOS froze? :? Try again.

---

### Post by amantonas on 2008-01-13
It won't let me do anything in the bios setup.

---

### Post by Omnios on 2008-01-13
> **amantonas said:**
> I've got a Dell Latitude cpx and It's messed up. My friend formatted the drive, and now grub has an error 22 whenever I try to boot it. So I think, I'll just install Ubuntu over it. So I pop in the disk, and it goes straight to grub. So I think I just have to go into the setup and change it so the CD boots first. So I go in, and It freezes. Is there anything that I can do to fix this stuff?
 
 Grub starts from the mbr and looks for the grub info on the Ubuntu partition. Reinstalling Ubuntu will defintly fix this.
 
 As for the biosy locking up. Havent heard anything partaining to linux doing that.

---

### Post by Dr Small on 2008-01-13
The BIOS freeze is definataly not because of the GRUB error.
The hard drive boots after the BIOS is read, so maybe it is a hardware failure problem somewhere.

I have seen this before, and it was a bad modem, or the sound card wasn't seated properly in the PCI slot, causing an error in the bootup process.

If you are having BIOS problems, check hardware first, as it can not be from the reformatted Hard drive.

Dr Small

---

### Post by amantonas on 2008-01-13
Well, the usb port is missing a black plastic chip, but I don't thing that affects anything.

---

### Post by amantonas on 2008-01-14
I just flashed in a new bios, and it does the same thing. What should I Do?

---

### Post by amantonas on 2008-01-14
I flashed in the new bios, and it still freezes, but it gave me a new one time boot menu, so im good

---

### Post by SOULRiDER on 2008-01-14
But did you manage to reinstall Ubuntu or at least can you boot into your current OS?

---

### Post by amantonas on 2008-01-15
Yeah, I have a dual boot of ubuntu  and vectorlinux

---

### Post by SOULRiDER on 2008-01-16
Ok then, please mark the thread as solved so we dont keep comming back :P
If you dont know how to do that check this out: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

