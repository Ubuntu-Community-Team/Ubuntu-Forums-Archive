---
title: "Critical temperature reached 127C Auto Shutdown"
date: 2013-05-02
forum: Any Other OS
---

### Post by sites on 2013-05-02
I have a motherboard with a bad temp sensor or something, because the bios always reports 127 degrees.  It's not 127 degrees.  I've tested several cpu's & heatsink/fan combos.  I'm running Mint/Lucid right now & there are no problems, but if I install let's say... Debian sid... or a spin-off, then I run into this *"Critical temperature reached 127C Auto Shutdown"* problem with thermal_sys.  I'm assuming this is a feature of the newer kernel.  Any attempt to install Windows invokes Dikembe Mutumbo as well.  Is there a safe way to disable this from killing the boot process so that I may enjoy siduction on this limper system?  It's an older quad Phenom cpu, plenty of ram, & i want to keep it on the bench.  Any ideas?

---

### Post by gordintoronto on 2013-05-02
Since it's a problem with the motherboard, it might be useful to identify the motherboard. If you don't know, you can run this command:
sudo lshw | more
the motherboard identification should be in the first couple of lines.

You might want to go through the BIOS settings with a fine-tooth comb to see if there's a possibility of help there. I have found that I can find motherboard manuals online, even for name-brand computers.

---

### Post by Perfect Storm on 2013-05-02
Moved to Other OS/Distro Support.

---

### Post by tgalati4 on 2013-05-02
Try repairing the thermal diode.  If it is open (cracked) then the BIOS will assume the worst.  If you are good with microsoldering, you can simply short it with some solder.  The diode is typically under the CPU on the motherboard, but it could also be a bad diode or thermister in the CPU itself and there is no way to repair that.  There might be some settings in BIOS to set the warnings to above 127C.

---

### Post by sites on 2013-06-05
> **gordintoronto said:**
> Since it's a problem with the motherboard, it might be useful to identify the motherboard. If you don't know, you can run this command:
sudo lshw | more
the motherboard identification should be in the first couple of lines.

You might want to go through the BIOS settings with a fine-tooth comb to see if there's a possibility of help there. I have found that I can find motherboard manuals online, even for name-brand computers.

Biostar TA790GXE V6

Believe me, I have turned the BIOS inside out trying to fix this.

> **tgalati4 said:**
> Try repairing the thermal diode.  If it is open (cracked) then the BIOS will assume the worst.  If you are good with microsoldering, you can simply short it with some solder.  The diode is typically under the CPU on the motherboard, but it could also be a bad diode or thermister in the CPU itself and there is no way to repair that.  There might be some settings in BIOS to set the warnings to above 127C.

Nope.  Others have had similar shutdown issues while running their system, but I'm having this problem while trying to install an OS.  If I use the old Lucid based Mint drive, it works.  If I try to install anything newer, auto shutdown & i auto pissedoff.

---

### Post by tgalati4 on 2013-06-05
You can file a bug with Ubuntu and follow it and see what happens.  It looks like you are stuck with an older kernel until a patch is released.

---

