---
title: "Disable splash screen?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-09-03
Is there a way to disable the bootup splash screen (The one after grub with the Ubuntu logo and the Orange loading bar) so that i get the boot text instead (Like with Slax)?

---

### Post by SOULRiDER on 2007-09-03
Youll have to remove 'quiet' and 'splash' fromt he boot options. You will ahve to edit /boot/gtub/menu.lst

---

### Post by chuy_max on 2008-03-22
> You only have th change a line in /boot/grub/menu.lst and rewrite the grub
bootloader.

There are two solutions.
- The first one will remove the spash screen.
- The second one will make the splash screen a bit more informational.

- So here's solution one:

For this open a terminal my right-click on the desktop and choosing 'Terminal'
Edit /boot/grub/menu.lst by starting an editor as superuser root:
 sudo gedit /boot/grub/menu.lst

Remove 'quiet' and 'splash' in the follwing part of menu.lst:
Note: depending on your setup there might be more options not only quiet and
      splash. Don't delete this other options, only delete quiet and splash.

  ## additional options to use with the default boot option, but not with the
  ## alternatives
  ## e.g. defoptions=vga=791 resume=/dev/hda5
  # defoptions=quiet splash

to:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

So by removing the defoption 'quiet splash' entry the splashscreen wil not be
used anymore

After you've done the changes you have to initialize the new grub bootloader
entry. Again in a terminal start:
 sudo update-grub

You will see that grup rewrites it's boot entry.
So we're done.
You may now close the Terminal and reboot the system to see the changes

- And solution two:

Only change
  # defoptions=quiet splash
to
  # defoptions=splash

So you still have a splash screen but it will give information about the
startup proecess.

After you've done the changes you have to initialize the new grub bootloader
entry. Again in a terminal start:
 sudo update-grub

SOURCE: [https://answers.launchpad.net/ubuntu/+question/7197](https://answers.launchpad.net/ubuntu/+question/7197)

---

