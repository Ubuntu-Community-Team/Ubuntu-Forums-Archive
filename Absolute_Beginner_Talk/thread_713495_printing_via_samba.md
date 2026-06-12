---
title: "printing via samba"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by karuzo on 2008-03-02
Hello all,
     I am all satisfied with ubuntu except for printing through samba.
When i first installed ubuntu (about 2 months ago) ubuntu recognized a printer over a workgroup connected to a windows xp computer.
At some point the printer just stopped showing.
I can no longer see the printer nor reinstall it.
I am still considering myself new at this. I tried to find a solution within these forums but nothing really seems to either relate to my problem nor solve it.
I really don't care about sharing folders/files between the computers, just the printer.
Thanks,
     Doron

---

### Post by spiderbatdad on 2008-03-02
It is possible your password to access the printer through windows expired. As I am sure you know, windows has to be configured properly as well as, ubuntu. It is also possible smb.conf got reconfigured during an update. Have you read the comprehensive samba guide...it's not the greatest, but it sheds some light on the windows aspects of the share; also, the ubuntu permissions are not correct in this guide. Beyond that, the first half is good: [https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

This guide should also be much help: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you still have trouble, consider posting your /etc/samba/smb.conf  and cupsd.conf files.

---

### Post by karuzo on 2008-03-03
> **spiderbatdad said:**
> It is possible your password to access the printer through windows expired. As I am sure you know, windows has to be configured properly as well as, ubuntu. It is also possible smb.conf got reconfigured during an update. Have you read the comprehensive samba guide...it's not the greatest, but it sheds some light on the windows aspects of the share; also, the ubuntu permissions are not correct in this guide. Beyond that, the first half is good: [https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

This guide should also be much help: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you still have trouble, consider posting your /etc/samba/smb.conf  and cupsd.conf files.
Thanks - I'll look into that and get back if I cannot resolve this still.
Thanks,
    Doron

---

