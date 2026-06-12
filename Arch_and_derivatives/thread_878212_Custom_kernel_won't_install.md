---
title: "Custom kernel won't install"
date: 2008-08-02
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-08-02
This is my first time making a kernel from scratch (aka without ABS) and while it compiles fine, it won't install giving me the error
```
>>> Updating module dependencies. Please wait ...
>>> MKINITCPIO SETUP
>>> ----------------
>>> If you use LVM2, Encrypted root or software RAID,
>>> Ensure you enable support in /etc/mkinitcpio.conf .
>>> More information about mkinitcpio setup can be found here:
>>> http://wiki.archlinux.org/index.php/Mkinitcpio

>>> Generating initial ramdisk, using mkinitcpio.  Please wait...
==> Building image "default"
==> Running command: /sbin/mkinitcpio -k -quad -c /etc/mkinitcpio.conf -g /boot/kernel26quad.img
error: optional argument to '-k' begins with a '-'
  you probably don't want this....aborting.
mkinitcpio: usage
  -c CONFIG        Use CONFIG file. default: /etc/mkinitcpio.conf
  -k KERNELVERSION Use KERNELVERSION. default: 2.6.25-ARCH
  -s NAME          Save filelist. default: no
  -b BASEDIR       Use BASEDIR. default: /
  -g IMAGE         Generate a cpio image as IMAGE. default: no
  -a NAME          Append to an existing filelist. default: no
  -p PRESET        Build specified preset.
  -m MESSAGE       Print MESSAGE before passing control to kinit.
  -S SKIPHOOKS     Skip SKIPHOOKS (comma-separated) when building the image.
  -v               Verbose output. Default: no
  -M               Display modules found via autodetection.
  -L               List all available hooks.
  -H HOOKNAME      Output help for hook 'HOOKNAME'.
  -h               This message.
==> FAIL
==> Building image "fallback"
==> Running command: /sbin/mkinitcpio -k -quad -c /etc/mkinitcpio.d/kernel26quad-fallback.conf -g /boot/kernel26quad-fallback.img
error: optional argument to '-k' begins with a '-'
  you probably don't want this....aborting.
mkinitcpio: usage
  -c CONFIG        Use CONFIG file. default: /etc/mkinitcpio.conf
  -k KERNELVERSION Use KERNELVERSION. default: 2.6.25-ARCH
  -s NAME          Save filelist. default: no
  -b BASEDIR       Use BASEDIR. default: /
  -g IMAGE         Generate a cpio image as IMAGE. default: no
  -a NAME          Append to an existing filelist. default: no
  -p PRESET        Build specified preset.
  -m MESSAGE       Print MESSAGE before passing control to kinit.
  -S SKIPHOOKS     Skip SKIPHOOKS (comma-separated) when building the image.
  -v               Verbose output. Default: no
  -M               Display modules found via autodetection.
  -L               List all available hooks.
  -H HOOKNAME      Output help for hook 'HOOKNAME'.
  -h               This message.
==> FAIL

```I've looked in all the files and have not found any '/sbin/mkinitcpio -k -quad -c /etc/mkinitcpio.conf -g /boot/kernel26quad.img' command. Where would it be? If I need to upload all the files I will.


*.install file
```
# arg 1:  the new package version
# arg 2:  the old package version

KERNEL_VERSION=-quad

post_install () {
  # updating module dependencies
  echo ">>> Updating module dependencies. Please wait ..."
  depmod -v $KERNEL_VERSION > /dev/null 2>&1
  # generate init ramdisks
  echo ">>> MKINITCPIO SETUP"
  echo ">>> ----------------"
  echo ">>> If you use LVM2, Encrypted root or software RAID,"
  echo ">>> Ensure you enable support in /etc/mkinitcpio.conf ."
  echo ">>> More information about mkinitcpio setup can be found here:"
  echo ">>> http://wiki.archlinux.org/index.php/Mkinitcpio"
  echo ""
  echo ">>> Generating initial ramdisk, using mkinitcpio.  Please wait..."

  /sbin/mkinitcpio -p kernel26quad
}

post_upgrade() {
  pacman -Q grub &>/dev/null
  hasgrub=$?
  pacman -Q lilo &>/dev/null
  haslilo=$?
  # reminder notices
  if [ $haslilo -eq 0 ]; then
    echo ">>>"
    if [ $hasgrub -eq 0 ]; then
      echo ">>> If you use the LILO bootloader, you should run 'lilo' before rebooting."
    else
      echo ">>> You appear to be using the LILO bootloader. You should run"
      echo ">>> 'lilo' before rebooting."
    fi
    echo ">>>"
  fi

  if grep "/boot" /etc/fstab 2>&1 >/dev/null; then
    if ! grep "/boot" /etc/mtab 2>&1 >/dev/null; then
      echo "WARNING: /boot appears to be a seperate partition but is not mounted"
      echo "         This is most likely not what you want.  Please mount your /boot"
      echo "         partition and reinstall the kernel unless you are sure this is OK"
    fi
  fi

  # updating module dependencies
  echo ">>> Updating module dependencies. Please wait ..."
  depmod -v $KERNEL_VERSION > /dev/null 2>&1
  echo ">>> MKINITCPIO SETUP"
  echo ">>> ----------------"
  echo ">>> If you use LVM2, Encrypted root or software RAID,"
  echo ">>> Ensure you enable support in /etc/mkinitcpio.conf ."
  echo ">>> More information about mkinitcpio setup can be found here:"
  echo ">>> http://wiki.archlinux.org/index.php/Mkinitcpio"
  echo ""
  echo ">>> Generating initial ramdisk, using mkinitcpio.  Please wait..."
  
  /sbin/mkinitcpio -p kernel26quad
}

op=$1
shift

$op $*

```

---

### Post by alanhaggai on 2008-12-07
mkinitcpio's -k switch should have the kernel version following it. For example:

```
mkinitcpio -k 2.6.27.8
```

---

