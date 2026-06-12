---
title: "hdparm not functioning correctly"
date: 2012-06-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nj_peeps on 2012-06-12
have been trying to solve this problem for the past year or so. I have been though the [forums]("http://ubuntuforums.org/showthread.php?t=1488614") and [bug trackers]("https://bugs.launchpad.net/bugs/568120"),  and any of the solutions that I have found do not seem to work.  I  think this is because my issue is a bit unique.  I have a desktop with  two RAID arrays, one mounted at root (/), and one that is mounted at  /home.  I have set hdparm to spindown the drives for the /home array  after 10 min of idle time.  After ten min of idle, hdparm will report  the drives in standby, but the drives are still spinning. :confused:

If I issue a sudo hdparm -y /dev/sd[c-g] via the terminal (when the  drives are in Active/Idle), the drives will spindown.  I have tried  using the Debian Squeeze version of hdparm, the old ver. from 9.10, and  tried playing with rules for udev, all to no avail.  ](*,)  I am not sure what I am missing, or what else to look for at this point.

This worked prior to upgrading to 10.04.  Would upgrading to 12.04 help?  Has anyone else experienced this issue?

_Hardware and Config info:_
OS: Ubuntu 10.04.3 (64 bit), current updates.
MB: Asus Rampage II Extreme (latest BIOS) (ICH10R SATA/PATA controller)
HDD's: sd[a-b] Seagate ST3320920AS
HDD's sd[c-g] Seagate ST3750630AS

RAID config:
/ RAID 1 (MB softraid using dmraid)
/home RAID 5 (using mdadm)

BIOS config:
drives sd[a-b] are configured as a RAID 1
drives sd[c-f] are configured as standalone drives (non-RAID)
drive sdg is connected to the "7th" SATA port configured as AHCI (not part of the softraid controller)

---

### Post by nj_peeps on 2012-07-30
bump.

---

