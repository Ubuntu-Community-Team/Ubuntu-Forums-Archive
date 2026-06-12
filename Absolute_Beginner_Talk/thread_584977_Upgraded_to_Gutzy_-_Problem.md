---
title: "Upgraded to Gutzy - Problem?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-10-21
Hi:
I just read AI's post about doing a clean install - after I upgraded last night.  (Oh well.)

It was interesting.  Throughout the install I got messages that Gutzy could not install:
libpam0g
libpam-modules
login
base-files
bash
passwd
adduser
fuse-utils
ntfs-3g
ssl-cert
cupsys
dbus

Gutzy cited dependancy problems as the reason.  After all this I got the message that the upgrade could not be installed and that the system could be in an unusable state.  It wanted me to report a bug against update manager and to include the files in /var/log/dist-upgrade.

The install continued on for awhile but then just disappeared before it got to cleanup.  I rebooted, holding my breath and the system did come up.  I did a lsb_release -a and it reports I am running gutzy.  A few things look different, but all seems to work.  My hard drive is missing about a gb of free space though.

Not sure what to do now.  Leave it alone, or clean install?

Any thoughts out there?

Thanks,
Ziffnabb

---

### Post by mikeyphi on 2007-10-21
You might want to check with Synaptic and install those packages if not there?
Perhaps a look here: [http://www.ubuntulinux.org/getubuntu/releasenotes/710tour](http://www.ubuntulinux.org/getubuntu/releasenotes/710tour)
to check if everything is installed?

---

### Post by ziffnabb on 2007-10-21
Hmmm, I've just tried to do an update, and there are 2 compiz related updates there that are greyed out.  Might have to do the clean install.

Ziffnabb

---

