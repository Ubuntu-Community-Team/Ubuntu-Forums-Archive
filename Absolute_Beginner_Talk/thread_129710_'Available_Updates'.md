---
title: "'Available Updates'"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by fairdoes on 2006-02-14
I get an icon telling me there's 'Available Updates' of about 50 megabytes, every time I logon to my desktop.

 With a dial up connection this would take forever, so do I need to do it? Also, hardinfo (the system monitor) tells me my system is ** Debian GNU /Linux testing/unstable** which is news to me!

 Will this say 'stable' if i download and install all the updates?:confused: 

 Help appreciated.:)

---

### Post by Kapre on 2006-02-14
[QUOTE=fairdoes]I get an icon telling me there's 'Available Updates' of about 50 megabytes, every time I logon to my desktop.

 With a dial up connection this would take forever, so do I need to do it? [/quote] 

I would agree with you that at dial-up this will take you forever. The reason that you see this everytime is because your ubuntu was setup to monitor if there are update(s) available. This will only show (pop-up) whenever you enter the i-net.

> Also, hardinfo (the system monitor) tells me my system is ** Debian GNU /Linux testing/unstable** which is news to me!

 Will this say 'stable' if i download and install all the updates?:confused: 

 Help appreciated.:)

Linux (in general) is always a work in progress (meaning there will always be updates - stable or non stable). it wouldn't automatically mean stable if you d/ all the updates but it will make it a little bit stable.

Also, do you have breezy or dapper?

K

---

### Post by carlosqueso on 2006-02-14
I believe that your system monitor thinks you're using Debian Unstable because that's what Ubuntu is based upon.   It shouldn't be a problem.   As far as the updates, you probably should download them, as they are valuable security fixes, but you don't need to.  The update manager will keep popping up if you don't though.

---

### Post by fairdoes on 2006-02-15
Thanks folks, I'll download the lot, but I hope it doesn't undo anything I've already set up, like the modem!

Thanks for the link to unix commands - i was just about to search:)

P.S. I have Breezy - CD arrived about 2 weeks ago

---

### Post by Mr.X on 2006-02-15
When i had to do updated with things with my old modem (28.8kbps had from 1996-2005-lol..), i just left overnight.
Usually best option.

---

### Post by fairdoes on 2006-02-16
Thanks Mr. X, It's good to know I can't do any harm with updating - cos I'm completely new to Linux. 

Your isp was in a different class to mine - after an hour the connection has usually broken ...:twisted:

---

### Post by fairdoes on 2006-02-17
I spent all day yesterday getting the updates. It sort of worked but my modem vanished and i had to reinstall it.

Today the updates icon has reappaeared and announced 20+ megabytes of security updates, including the kernel (linux-image-2.6.12-10-386) version 2.6.12-10.28.

I think this is he update that removes my modem, so will I lose the modem again if i download this? there's no information about what security issues it is updating, just 

[b]This package contains the Linux kernel image for version 2.6.12 on
386,
the corresponding System.map file, and the modules built by the packager.
It also contains scripts that try to ensure that the system is not left in
a unbootable state after an update.

If you wish to update a bootdisk, or to use a bootloader to make
installing and using the image easier, we suggest you install the latest
fdutils (for formatting a floppy to be used as boot disk), and LILO, for a
powerful bootloader. Of course, both these are optional.

Kernel image packages are generally produced using kernel-package,
and it is suggested that you install that package if you wish to
create a custom kernel from the sources.[/b]

which I don't understand at all.

---

### Post by kombipom on 2006-02-17
The updates do come in pretty regularly and I know it would drive me nuts on dial-up.  If you are not too concerned about security, you can stop the update manager bugging you and leave your system as is.  Go to System->Administration->Update Manager click Preferences and then Settings and you can either set the updater to check every few days rather than every day or switch it off altogether.

---

### Post by jobezone on 2006-02-17
[QUOTE=fairdoes]I spent all day yesterday getting the updates. It sort of worked but my modem vanished and i had to reinstall it.

Today the updates icon has reappaeared and announced 20+ megabytes of security updates, including the kernel (linux-image-2.6.12-10-386) version 2.6.12-10.28.

I think this is he update that removes my modem, so will I lose the modem again if i download this? there's no information about what security issues it is updating, just 

[b]This package contains the Linux kernel image for version 2.6.12 on
386,
the corresponding System.map file, and the modules built by the packager.
It also contains scripts that try to ensure that the system is not left in
a unbootable state after an update.

If you wish to update a bootdisk, or to use a bootloader to make
installing and using the image easier, we suggest you install the latest
fdutils (for formatting a floppy to be used as boot disk), and LILO, for a
powerful bootloader. Of course, both these are optional.

Kernel image packages are generally produced using kernel-package,
and it is suggested that you install that package if you wish to
create a custom kernel from the sources.[/b]

which I don't understand at all.[/QUOTE]
In the update-manager, if you click a package, it's changelog shows up in the bottom window. In synaptic, you can select a package, then choose in the menu Package->Changelog .

---

### Post by fairdoes on 2006-02-17
1. I am concerned about security.

2. I can't see 'changelog' in my post?:confused: 

Apparently I **can** do harm with updating - viz lose my modem and be unable to boot my computer.

Is there a mailing list for when a stable version is published on CD, please?

---

