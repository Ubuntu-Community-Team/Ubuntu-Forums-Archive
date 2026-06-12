---
title: "Feisty isn't so Feisty."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2007-04-21
Well, I'm not impressed so far really. I can't get past the desktop cd or alternate one. The Desktop CD freezes when I try to open the installer (same issue with 6.10) and the alternate CD can't get past mounting itself correctly, well it mounts detects hardware and falls over. 

No bad burns, checked 100%. Anyone else had similar issues?

---

### Post by HowardDrake on 2007-04-21
I've been using it since the Beta and its been ultrasmooth for me.

---

### Post by Joseaa on 2007-04-21
Once the installation came to a halt when I disconnected my external hard disk. Other than that I've never experienced any problems with installation at all.

---

### Post by borris.morris on 2007-04-21
My laptop would overheat and stall installation. Is that your case?

---

### Post by old_geekster on 2007-04-21
Try the upgrade method.  Here is the command I used:

sudo update-manager -c -d

It worked for me twice.  My rig is running smoother than with XP Pro.

---

### Post by Rackerz on 2007-04-22
Well looks like it was the Kernel again, still not supporting my Jmicron controller. noacpi, acpi=off and nolapci are the commands needed.

---

### Post by Zaosyn on 2007-04-22
I had an experience close to this when I was wanted to install Ubuntu.

I had 6.06 discs, and a 7.04 disc.

Well when ever I tried to run the installation on either it would reboot my PC after the kernel loaded. I had to eventually go into TEXT mode in 6.06 and boot up to a live mode doing typeing: Boot: live acpi=off

It would boot Ubuntu 6.06 in a live version and I had to install Ubuntu from there. From there I had to upgrade from downloading 6.10 and installing that, and then upgrading from 6.10 to 7.04 via the upgrade manager.

This may be what you have to do.

---

