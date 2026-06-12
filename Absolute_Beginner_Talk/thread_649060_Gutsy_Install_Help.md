---
title: "Gutsy Install Help"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Incognitia on 2007-12-24
Having bought a new computer, old laptop having suffered a catastrophic mootherboard failure and not seemed worth repairing, I decided the extra £55 for a Windows disk was a bit steep, so I'd try running it in Ubuntu.
I'd used Ubuntu before on my laptop, as a dual-boot with XP, so I thought I could probably manage the installation process...
I downloaded an iso of Gutsy for a 64-bit, ran an MD5 check on it, burnt to a cd, checked the disk.
So then I put the disk in the new computer and fire it up; gets past BIOS and to the first Ubuntu screen.
Now, whether I select 'Install', or 'Check Disk' or 'Start in Safe Graphics Mode', I get a message 'No Visual Input' and then the screen goes blank.

The hardware is an Athlon X2 on an Asus M2N-X board, with an ASUS EN 8400 GS graphics card.

Any suggestions? I've been waiting two months for the new computer to arrive, now I just want to be able to USE it.
Thanks in advance.

---

### Post by taurus on 2007-12-24
Try the alternate CD if you want to install Gutsy on your new machine.

---

### Post by sowelie on 2007-12-24
I had a similar issue with my video during install.  Try adding 'noapic' to the boot options from the live disc menu.  You'll have to do this on your first boot once it's installed too.  Once you install the restricted drivers, you can remove the option.  From the live disc menu, hit F6 and add noapic before the '--'.

---

### Post by Incognitia on 2007-12-24
noapic didn't work, sadly.
Am currently downloading (79%...) the alternate cd.
I'll post back with results on installing from that as soon as I get the chance. My thanks to both for swift replies.

---

