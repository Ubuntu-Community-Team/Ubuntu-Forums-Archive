---
title: "Installing Ubuntu next to XP. What to do with Grub?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Silverstarme on 2007-08-20
Installinh Ubuntu next to Windows. There are enough guides for it on the internet, but even after reading it they leave with some unanswered questions.
The partition part won't be the problem, as I have 5GB unassigned unformatted diskspace availeble. My main question remains is what do with Grub? Is it better to install it on the MBR or is it better to let XP have it? Do I need to anything special to Grub or will the installer auto write the correct values to Grub to proper detect XP and boot it. The main windows partition is NTFS formatted.
Any links to a clear guide are also welcome.

---

### Post by oilchangeguy on 2007-08-20
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Silverstarme on 2007-08-20
That still does not answer what do with Grub. My question is: What is best installing Grub on the MBR or not (letting XP have the mbr)? Remember after installing Ubuntu I still want to have access to Windows.
-edit- It seems I am a to lousy reader. The answer is clear to do NOT install Grub on the MBR, unless someoen else suggest otherwise.

---

### Post by oilchangeguy on 2007-08-20
> **Silverstarme said:**
> That still does not answer what do with Grub. My question is: What is best installing Grub on the MBR or not (letting XP have the mbr)? Remember after installing Ubuntu I still want to have access to Windows.

you will still have access to windows. ubuntu overwrites windows boot loader with grub (grand unified boot loader).

---

### Post by Hobo Joe on 2007-08-20
> **Silverstarme said:**
> That still does not answer what do with Grub. My question is: What is best installing Grub on the MBR or not (letting XP have the mbr)? Remember after installing Ubuntu I still want to have access to Windows.

Ubuntu will detect that you have Windows, and will automatically install GRUB in the proper spot with the proper configuration.

---

### Post by mikeyphi on 2007-08-20
> **Silverstarme said:**
> Installinh Ubuntu next to Windows. There are enough guides for it on the internet, but even after reading it they leave with some unanswered questions.
The partition part won't be the problem, as I have 5GB unassigned unformatted diskspace availeble. My main question remains is what do with Grub? Is it better to install it on the MBR or is it better to let XP have it? Do I need to anything special to Grub or will the installer auto write the correct values to Grub to proper detect XP and boot it. The main windows partition is NTFS formatted.
Any links to a clear guide are also welcome.

oilchangeguy has pointed to an excellent guide.

The MBR is too small a space to hold Grub, what happens - if you allow the installer to do its thing - is that the MBR is changed to point to where Grub is installed, so on Bootup the MBR is read (as always) this points to the Grub which loads and gives you the option of choosing to load ubuntu or any other OS on your system. 
Just let the installer do its job!

---

### Post by Silverstarme on 2007-08-20
Well ubuntu runs fine and well and I still can boot to XP. I just let the installer do it job and it worked out fine. Now I finally got use for that 5gb of space where I did now what the <censored> to do with it (I used first for the windows swap file, which I now again moved to the main partition).

---

