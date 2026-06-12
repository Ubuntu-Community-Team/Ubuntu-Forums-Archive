---
title: "Changing from a different Linux"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Arctues on 2007-05-28
I want to intstall Ubuntu on a computer that has mandrake 10 Linux on it, along with Win98(kept there to make sure the computer is working properly) I want to overwrite the Mandrake with Ubuntu. Not sure what to do or what I will encounter. The current config uses LILO to select the OS to boot.  Any suggestions or help as to where to look for this answer.

I am fairly well computer literate but linux tends to throw me some. Thanks for any help!

---

### Post by AAM on 2007-05-28
put in the LiveCD and install. You may find that you have problems with the Desktop loading because of various config files being set for KDE, but just do the normal install thing first. Just reformat the root (/) directory within the Custom install option. Win98 will remain and be listed in the GRUB that overwrite LILO in the MBR.

---

