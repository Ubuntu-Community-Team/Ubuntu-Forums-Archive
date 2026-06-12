---
title: "&quot;starting hotplug subsystem hang&quot;"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by hepkat63 on 2006-04-14
Hi,
I have just installed Ubuntu and when it gets to 'starting hotplug subsystem' it hangs and will not go any further.  I have looked through the forum and using control C - can bypass loading of this subsystem - but this is not really good enough.  I read somewhere else, that my onboard soundcard is probably causing this problem - again, not good enough.
I have an Acer AcerPower FG (sk30) with onboard 5.1 sound.  Is there a sound driver I can download somewhere which will fix this please?
I have reloaded ubuntu four times, each with different options, but this 'hanging' continues.  Last try was:  linux noapic nolapic acpi=off pnpbios=off

---

### Post by dbw on 2006-04-14
IF you want to keep the hotplug system from participating in the boot process, check out this excellent [howto]("http://ubuntuforums.org/showthread.php?t=89491&referrerid=48700"), which describes how to modify your boot process.  I do not know how to fix hotplug.

---

