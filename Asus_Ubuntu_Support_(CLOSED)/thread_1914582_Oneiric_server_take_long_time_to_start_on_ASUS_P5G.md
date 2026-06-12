---
title: "Oneiric server take long time to start on ASUS P5G41T-M LX"
date: 2012-01-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ziotibia81 on 2012-01-24
Hi!

I'm installing Oneiric server on a pc with motherboard ASUS P5G41T-M LX.

When I turn on pc i see grub menù and, when kernel start, screen remain black for a long time. I can see messages on screen when kernel star finish and stat init scripts.

So I can't see kernel messages and discover because kernel take long time to start.

My /etc/default/grub :

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"


```

Enabling  "GRUB_TERMINAL=console" I can see kernel messages but they go outside the screen and I'm not able to completly read they.... So I prefer messages on framebuffer.

Someone has any idea?

---

