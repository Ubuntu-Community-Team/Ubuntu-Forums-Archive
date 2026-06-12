---
title: "how do i access my os x partition in qemu?"
date: 2008-12-23
forum: Apple Hardware Users
---

### Post by Hume's doona on 2008-12-23
i have a dual boot set up *on a mac* and need to occasionally access files from my os x partition... to save rebooting i just want to run a VM in qemu *on mac hardware so it's legal*...

rebooting is a pain when i just need one figure from a spreadsheet that i wrote before i had ubuntu installed.

thanks
dan

---

### Post by cyberdork33 on 2008-12-24
> **Hume's doona said:**
> i have a dual boot set up *on a mac* and need to occasionally access files from my os x partition... to save rebooting i just want to run a VM in qemu *on mac hardware so it's legal*...

rebooting is a pain when i just need one figure from a spreadsheet that i wrote before i had ubuntu installed.

thanks
dan
Need some clarification.

qemu is not a VM, it is a cpu emulator. Depending on what you are trying to do, it may not be the best solution to accomplish your goal.

You are confusing about what OS is running where. Are you running qemu in OSX? If so, what OS are you running in qemu? Or are you trying to run OSX in qemu and running that in another OS?
:confused:

---

### Post by Hume's doona on 2008-12-24
that would explain why i couldn't get it working!

so i installed virtualbox in ubuntu ultimate 2.0. now i just need to know how to access my leopard partition through virtualbox.

> Or are you trying to run OSX in qemu and running that in another OS?
yep, sorry if i didn't word it well. i'm trying to fully migrate to linux from mac os x, but for now i will still need to access some things from my mac os x leopard partition. so i am trying to run os x leopard (which has it's own partition) as a virtual machine inside ubuntu ultimate linux.

do i also need vmdk to do this?

---

### Post by hanzomon4 on 2008-12-25
Do You need access to certain apps, or just data? If you only need files off hat partition you can mount the partitions in Ubuntu. You can't use OS X in a vm unless it's altered. You can run OS X server in OS X on parallels and vmware fusion I believe but not in Ubuntu on a mac.

---

### Post by Hume's doona on 2008-12-26
yep, just data, not applications.

thanks for that

---

### Post by cyberdork33 on 2008-12-28
> **Hume's doona said:**
> yep, just data, not applications.

thanks for that

yep, I think your best bet is dual booting.

---

