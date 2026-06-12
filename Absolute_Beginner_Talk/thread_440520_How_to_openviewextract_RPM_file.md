---
title: "How to open/view/extract RPM file?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by evaldas on 2007-05-11
Hi,

I want to view and extract some files from RPM archive, but File Roller (archive manager) on Gnome says "archive type not supported". I believe I should install some plugin for File Roller, but I don't know it's name.

Thanks

---

### Post by taurus on 2007-05-11
You need alien to convert .rpm to .deb.

---

### Post by Dr Small on 2007-05-11
1.) sudo apt-get install alien
2.) sudo alien name_o_file.rpm

This will convert your RPM to a DEB and then you can install the deb with:

3.) sudo dpkg -i name_o_file.deb


Dr Small

---

### Post by evaldas on 2007-05-11
I don't want to install anything. I just want to see what are the files in that RPM archive and extract them for viewing (for example some image file or script).

---

### Post by sisco311 on 2007-05-11
to extract all of the files in the RPM file to the current directory:
```
rpm2cpio **package.rpm** | cpio -dimv
```

---

### Post by evaldas on 2007-05-11
thank you, sisco311

---

### Post by Endolith on 2008-04-20
> **evaldas said:**
> I want to view and extract some files from RPM archive, but File Roller (archive manager) on Gnome says "archive type not supported". I believe I should install some plugin for File Roller, but I don't know it's name.

Go to Synaptic and look for file-roller.  Right-click it and see "suggested packages".  Install the RPM related packages from there, and file-roller will be able to open RPMs.  This should be installed by default, in  my opinion.  It's misleading to have .rpm files "associated" with file-roller when it can't actually open them.

---

### Post by johnconnor on 2008-06-19
> **Endolith said:**
> Go to Synaptic and look for file-roller.  Right-click it and see "suggested packages".  Install the RPM related packages from there, and file-roller will be able to open RPMs.  This should be installed by default, in  my opinion.  It's misleading to have .rpm files "associated" with file-roller when it can't actually open them.
Hi! Which ones exactly? I installed cpio but it still doesn't work...

---

