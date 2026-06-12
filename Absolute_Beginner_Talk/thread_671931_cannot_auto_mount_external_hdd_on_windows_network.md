---
title: "cannot auto mount external hdd on windows network"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by EnterTheDarkSide on 2008-01-19
hi,

I have an external hdd connected to my winxp machine, the hdd is fat32. i was able to mount the hdd to my ubuntu with this line in the shell: sudo mount -t smbfs //myWindowsCom/E /mnt/E.

However i wanted the hdd to be automatically at boot, and so i modified the fstab file with this line: //myWindowsCom/E /mnt/E smb defaults 0 0

That entry in the fstab file did not mount the ext hdd for me. Can someone shed some light please?

---

### Post by bethebunny on 2008-01-19
The issue is with the "defaults" part. There is an option to automatically mount on boot (I believe that option is just "auto"), so change "defaults" to "auto" *should* work (there may be some issues with user privileges, also fixed in that option list). Check man fstab or man mount for available options.

---

### Post by EnterTheDarkSide on 2008-01-19
hi bethebunny,

thanks for your reply. I modified fstab with the following line:
//familycom/E /mnt/E smbfs auto,user=<myUbuntuUsername>,password=<myUbuntuPassword> 0 0

but still I'm unsuccessful when trying to mount at boot time. I probably should of mention to you that ubuntu is on my laptop and I'm connecting to my router thru a wireless card using ndiswrapper. If my syntax in the fstab is correct then could this be a case where the fstab is loading before ndiswrapper? I configure ndiswrapper to load automatically at boot time in /etc/modules.

thanks

---

