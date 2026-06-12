---
title: "[SOLVED]Shutdown does not power off computer in Kodachi"
date: 2023-08-07
forum: Any Other OS
---

### Post by blackwolf-oz9 on 2023-08-07
```

[LIST=1]
[*]EDITOR=gedit sudoedit /etc/default/grub 
[/LIST]

```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -d -s 2> /dev/null || echo Kodachi`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash zswap.enabled=1 zswap.compressor=lz4"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/etc/grub.d/backgrounds/grub.png"

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
```

Do I follow this ? [https://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](https://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)

I see two lines of GRUB_CMDLINE_LINUX  ?? 

The error message is [815.289051] shutdown[1] : Failed to wait for process: Protocol error
Thanks!

**SOLVED by installing Nvidia driver.

---

### Post by blackwolf-oz9 on 2023-08-07
Well I did the edit & left the second repeated line. No difference, & yes have Nvidia

---

