---
title: "Headless Install"
date: 2010-08-11
forum: Apple Hardware Users
---

### Post by 2-7offsuit on 2010-08-11
I have a G4 Powerbook with a bad graphics card. I plan on setting it up as a home file server. I'd like to install Ubuntu Server on it. Right now I'm able to install OSX 10.4 server by gaining ssh access while it's booted from the install cd. It doesn't appear that this is possible from the Ubuntu Live CD. Is there another way to do it? Before you answer that, the bigger question is: can I even install Linux of any kind without accessing the Open Firmware screen?

---

### Post by 2-7offsuit on 2010-08-12
If it helps, I also have another working G4 PB that I can use to set this one up. If I do the installation on it, then put the drive back in the one without a screen, would that work? or is there still something that would need to be configured in the Open Firmware?

---

### Post by linuxopjemac on 2010-08-12
That would probably work, good idea.

---

### Post by 2-7offsuit on 2010-08-12
> **linuxopjemac said:**
> That would probably work, good idea.

It will!? What about Open Firmware? That's the part that's confusing me. Does it need to be configured in any way in order to boot Linux? (I was planning on removing OSX completely.)

---

### Post by shawnhcorey on 2010-08-13
> **2-7offsuit said:**
> It will!? What about Open Firmware? That's the part that's confusing me. Does it need to be configured in any way in order to boot Linux? (I was planning on removing OSX completely.)

I have a PowerBook G4.  Its BIOS, Open Firmware, is configured to boot from hard disk or CD.  To boot from any other device, you need to go through Open Firmware.  If you install Ubuntu on it, it should configure itself to boot from hard disk automatically.

BTW, the bootloader for PPCs is yaboot, not GRUB or LiLo.

---

