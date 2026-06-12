---
title: "startup/shutdown automatic commands"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by heinz57 on 2007-09-10
hi, I was wondering if there are scripts or something that I can edit, so that a command happens at startup and shutdown.

The reason is that I use thunderbird on both windows and ubuntu. So on startup it would be nice for all of the windows thunderbird files to be copied to ubuntu, and on shutdown have the ubuntu files be copied onto the windows thunderbird (i think fiesty has NFTS writing capabilities, if i remember correctly). I know the files are compatible because it works when i manually copy them.

thanks

---

### Post by swoll1980 on 2007-09-10
you need to install ntfs-config from synaptics to write the files. You can write a script to do that and run it at start-up and shut-down it would'nt be to complicated either just  give the files the same name in ubuntu and windows when it copys the file it will overwrite the old one. I'm not sure exacly what the script would look like but learning the things on this website will help out alot   [www.linuxcommand.org](www.linuxcommand.org)

---

### Post by sumguy231 on 2007-09-10
Actually, you can just use the profile manager to pick up on your Windows profile provided that your Windows partition is mounted in Ubuntu:

[http://kb.mozillazine.org/Roaming_profile#How_can_I_share_a_fixed_profile.2C_such_as_on_dual-boot_machines.3F](http://kb.mozillazine.org/Roaming_profile#How_can_I_share_a_fixed_profile.2C_such_as_on_dual-boot_machines.3F)

---

