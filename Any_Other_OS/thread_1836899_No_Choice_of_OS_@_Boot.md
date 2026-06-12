---
title: "No Choice of OS @ Boot"
date: 2011-08-31
forum: Any Other OS
---

### Post by bug67 on 2011-08-31
I have Linux Mint 10 Installed.  I just got through installing [Dream Studio]("http://dream.dickmacinnis.com/forum/") in a "side by side" configuration.  However, When I reboot the system, I am not given a choice of OS's to boot into.  The machine just boots straight into Mint...no Grub menu, nothing.  What happened and how do I fix?  Thanks in advance.

**_EDIT_**:

I figured out if I hold the "Shift" key at start-up, I get to the Grub menu.  By the way, it's Grub version 1.98 if that makes a difference.  However, *there is no option listed for the Dream Studio OS*.  Mint and Mint Recovery are the only options listed.  What the heck?

---

### Post by bug67 on 2011-09-01
Nobody?

Dream Studio is essentially Ubuntu 11.04 if that helps.

---

### Post by macinnisrr on 2011-09-01
Try this, boot into Mint, then open a terminal and run "sudo update-grub". You should see some feedback saying that grub has found your Mint install, a memtest application and finally Dream Studio (Ubuntu 11.04).

---

### Post by Zeta-K on 2011-09-08
> **macinnisrr said:**
> Try this, boot into Mint, then open a terminal and run "sudo update-grub". You should see some feedback saying that grub has found your Mint install, a memtest application and finally Dream Studio (Ubuntu 11.04).

If that doesn't work, try chrooting into your partition, then updating grub

---

### Post by bug67 on 2011-09-08
> **Zeta-K said:**
> If that doesn't work, try chrooting into your partition, then updating grub

Thank you for trying to help. I have no idea what you're talking about but, thanks. 

I've put this on the back burner for now. There are other issues with Natty. I'm going to keep things the way they are for now.

---

