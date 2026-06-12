---
title: "inconsistent install locations"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by droogy on 2006-08-23
Why do ubuntu programs install to so many different locations?  some are in /home/<user directory> and others are in /usr and some in /opt.

Why isn't it more consistent?  ie. windows has My Programs and the majority of programs go there.

---

### Post by BagOBones on 2006-08-23
Welcome to the the wacky world of unix/linux.

Think this is bad, try using more than one distro, depending on how something packaged the config files could almost be anywhere.

---

### Post by nalmeth on 2006-08-23
It's actually a ruthlessly organized system.

The user shouldn't be messing around, looking for system files to delete.

The PACKAGE MANAGEMENT SYSTEM should be the interface which the user deals with.

If you're compiling apps, use checkinstall rather than make install so it can be easily removed if needed.

The hidden folders in your /home are configuration files, rightly separated from system files so you don't need to run applications as root.

---

