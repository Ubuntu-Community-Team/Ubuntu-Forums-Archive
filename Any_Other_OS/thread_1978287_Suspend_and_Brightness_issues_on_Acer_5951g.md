---
title: "Suspend and Brightness issues on Acer 5951g"
date: 2012-05-11
forum: Any Other OS
---

### Post by davelosm on 2012-05-11
Hey people, 

I have an Acer 5951g and I'm having a couple of problems with brightness and suspend. 

Brightness altering simply doesn't work. When I try to suspend, the laptop goes to sleep fine, but on trying to wake it up, power comes back on, and the screen seems as if it is coming back on, but remains black but a bit brighter than 'off black' if that makes sense. 

Has anyone had any luck fixing this with this model? I've tried various things but none specific to the 5951g and none that have shown any improvement. 

I already posted on Mint Forums as I'm running Mint 11, but was unable to get any help. Any help here would be very much appreciated. 
Cheers.

---

### Post by Perfect Storm on 2012-05-11
Moved to Other OS/Distro Talk.

---

### Post by shuttleworthwannabe on 2012-05-11
> **davelosm said:**
> Brightness altering simply doesn't work. 

Will this help (albeit for Dell Vostro)? See if it helps. [http://ubuntuforums.org/showpost.php?p=11663269&postcount=1](http://ubuntuforums.org/showpost.php?p=11663269&postcount=1)

---

### Post by davelosm on 2012-05-11
Thanks for the response, 

Didn't work, just messed up my graphics, so reverted back to what I had in /etc/default/grub which is:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux i915.i915_enable_rc6=1 "
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by davelosm on 2012-05-18
Bump :)

Any help would be amazing.

---

