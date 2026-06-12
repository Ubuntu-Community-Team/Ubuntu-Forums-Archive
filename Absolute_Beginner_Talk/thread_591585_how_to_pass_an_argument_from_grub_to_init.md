---
title: "how to pass an argument from grub to init"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ksleurs on 2007-10-25
I'd like to pass a certain argument/parameter from grub to a startup script.

More precisely:
in /etc/init.d there is a script called xorg which selects the correct xorg.conf file based on an argument XORG=single or XORG=dual

in /etc/rc2.d there is a symbolic link called S01xorg to the xorg script in init.d

now I want to have two items in GRUB menu.lst: one with the argument XORG=single and another with XORG=dual to select the appropriate X setup.

This does not work at the moment. Startup hangs a a certain point and I get a text console instead of my gnome X windows. When I eliminate the argument in the grub menu saying XORG=single, it boots ok, but of course the right conf file does not get loaded. So I guess there is something wrong with passing the arguments to init.

Code of /etc/init.d/xorg:
```

#!/bin/sh
case $XORG in
    single)
        # if PARAM== single
        cp /etc/X11/xorg.conf.single /etc/X11/xorg.conf
        echo "Single Screen Setup : Enabled"
    ;;
    dual)
        # if PARAM== dual
        cp /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
        echo "Dual Screen Setup : Enabled"
    ;;
    *)
        #default conf here
       echo "Default Screen Setup"
    ;;
esac
exit 1

```

Item in /boot/grub/menu.lst
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic, Single Monitor
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=33a5dac8-e719-48e8-a63
b-a34f6c3ba5e2 ro splash XORG=single
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```

---

### Post by nelson.bolanos on 2007-10-27
I'm not sure if this will help you, but why don't you place that script on runlevel 5, and create the registry on GRUB by runlevel....

just a thought :D

---

### Post by ksleurs on 2007-10-31
That's an idea... If I get it right, your solution is putting a script which copies one xorg.conf in one runlevel and a script that copies the other xorg.conf in another runlevel and creating different grub entries for different runlevels?

And how do I do the last thing: getting grub to choose between runlevels?

---

