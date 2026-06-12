---
title: "PCManFM, unable to mount (possible gamin problem)"
date: 2009-02-10
forum: Arch and derivatives
---

### Post by smartboyathome on 2009-02-10
I am using PCManFM, and when I try to mount a partition listed in the Location sidebar, it gives me a couple blank error boxes and then says Directory doesn't exist. I tried this with both a created directory and no created directories, and both throw the same error. When the drives are mounted manually, though, it will go to them. Could this be a problem with gamin? Or has anyone else had this error?

---

### Post by handy on 2009-02-10
For all its worth, I'm using gamin & manually mounting unmounting with Worker & it works ok.

---

### Post by smartboyathome on 2009-02-10
Well, it may have something to do with HAL permissions. When I try to use E17's places plugin, it gives me this:
```
Can't mount device.
org.freedesktop.Hal.Device.PermissionDeniedByPolicy
org.freedesktop.hal.storage.mount-removeable no
```
Could I have somehow screwed this up? :(

---

### Post by der_joachim on 2009-02-11
On the arch forums there is a number of threads with issues comparable to yours. I have the same problem, but have not found a satisfactory answer yet.

---

### Post by smartboyathome on 2009-02-11
> **der_joachim said:**
> On the arch forums there is a number of threads with issues comparable to yours. I have the same problem, but have not found a satisfactory answer yet.

Ah, ok, thanks for letting me know. :)

---

### Post by Toffeeapple on 2009-02-12
Hello.

I had the same problem but with thunar, I think it's something to do with the newer version of hal, 0.5.11-7. Look in /var/cache/pacman/pkg and see if you have a previous version there. I'm using 0.5.11-4 with no problems.

Alternatively build it from abs and fiddle with that, maybe that will work too : )

---

### Post by kerry_s on 2009-02-12
have you tried adding yourself to the hal group?
i had no problems when i had hal running.

---

### Post by smartboyathome on 2009-02-12
> **Toffeeapple said:**
> Hello.

I had the same problem but with thunar, I think it's something to do with the newer version of hal, 0.5.11-7. Look in /var/cache/pacman/pkg and see if you have a previous version there. I'm using 0.5.11-4 with no problems.

Alternatively build it from abs and fiddle with that, maybe that will work too : )

Will do when I have a little more time.

> **kerry_s said:**
> have you tried adding yourself to the hal group?
i had no problems when i had hal running.

Just tried it, didn't work. Same error.

---

### Post by der_joachim on 2009-02-12
More info, fresh from the Arch forums:

[http://bbs.archlinux.org/viewtopic.php?id=65070](http://bbs.archlinux.org/viewtopic.php?id=65070)

I haven't tried it yet. An a poster already commented in the thread linked above, the status of the fix is unknown. Is it a patch or does HAL have to be configured differently in the future?

---

### Post by doorknob60 on 2009-02-13
> **smartboyathome said:**
> Well, it may have something to do with HAL permissions. When I try to use E17's places plugin, it gives me this:
```
Can't mount device.
org.freedesktop.Hal.Device.PermissionDeniedByPolicy
org.freedesktop.hal.storage.mount-removeable no
```
Could I have somehow screwed this up? :(

I get that too trying to mount my flash drive in Dolphin and PcmanFM...meh I hope this gets fixed soon kinda annoying.

---

### Post by der_joachim on 2009-02-13
I solved my USB mounting issues for now. This was fixed on my Slim + Openbox + LXDE + PcManFM desktop, so this fix is entire on-topic.

First, open /etc/pam.d/login as root and add the following line:
```

session         optional        pam_ck_connector.so

```

Then open ~/.xinitrc in your favorite text editor and change the line
```

exec startlxde

```
to
```

exec ck-launch-session startlxde

```

Reboot (or restart the relevant services. I chose the first option). 

Note: I based this fix on the following threads:
[http://bugs.archlinux.org/task/12221](http://bugs.archlinux.org/task/12221)
[http://bbs.archlinux.org/viewtopic.php?id=65070](http://bbs.archlinux.org/viewtopic.php?id=65070)
[http://bbs.archlinux.org/viewtopic.php?pid=497602#p497602](http://bbs.archlinux.org/viewtopic.php?pid=497602#p497602)

---

### Post by ghindo on 2009-02-13
I am receiving a similar error message with Thunar.  I'm getting:```
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
org.freedesktop.hal.storage.mount-removable no <-- (action, result).
```

---

### Post by ubersolid on 2009-02-14
I changed my login manager from entrance to gdm, and that solved the issue for me. Wouldn't work any other way. On two computers.
I get the Xlib thing too on my laptop, but that is nothing to worry about according to some mailing list which adress I forgot :).

---

### Post by gjoellee on 2009-02-14
I do not know a lot about this, but maybe fam will work better then gamin? I use fam, and have no problems pcmanfm mounting

---

### Post by ubersolid on 2009-02-14
> **gjoellee said:**
> I do not know a lot about this, but maybe fam will work better then gamin? I use fam, and have no problems pcmanfm mounting
I use fam, haven't tried gamin.

---

### Post by smartboyathome on 2009-02-14
> **gjoellee said:**
> I do not know a lot about this, but maybe fam will work better then gamin? I use fam, and have no problems pcmanfm mounting

FAM didn't work for me either, for some reason. At least with gamin, it shows my drives in PCManFM. ;)

---

### Post by wolfvorkian1 on 2009-02-15
This may be related but I hadn't tried to mount a usb flash disc in a couple weeks. Last night neither the desktop or the laptop which have nearly identical versions of Arch on them could accomplish the feat per Thunar. Hal wouldn't do nor would the computer allow me to manually mount the device. 

I fiddled around reformatting the flash disc, etc and that didn't help. Thanks to Toffeeapple's post, I was able to find the older version of Hal in ABS and build it . The downgrading of Hal solved my problem.

---

### Post by Toffeeapple on 2009-02-15
Don't forget to add 'hal' to the 'IgnorePkg line in /etc/pacman.conf or it'll just get updated next time you do -Syu.

I just hope that what ever it is is some sort of bug thing that might get corrected in an update rather than a it being a 'feature' of some sort. as some of the other workarounds I've come across are a bit long-winded and complicated.. que lio!

: )

---

### Post by Barrucadu on 2009-02-15
This is how I fixed it:
[list]
[*]Stop hal
[*]Upgrade hal to the latest version
[*]Change /etc/PolicyKit/PolicyKit.conf to this:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match action="org.freedesktop.hal.storage.mount-removable">
        <return result="yes"/>
    </match>
</config>
```
[*]Start hal
[*]Restart X
[/list]

Mounting of USB thingies now works again.

---

### Post by ghindo on 2009-02-15
How do you stop HAL?

**EDIT:**  Also, is the above fix working for anybody else?

---

### Post by smartboyathome on 2009-02-15
Use this command as root:
```
/etc/rc.d/hal stop
```

---

