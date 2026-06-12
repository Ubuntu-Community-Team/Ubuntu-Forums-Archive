---
title: "troubles of triple boot on Macbook white"
date: 2009-03-31
forum: Apple Hardware Users
---

### Post by genal on 2009-03-31
hello all,
I just bought the early-2009 Macbook white(5,2) a couple days ago, and I am getting mad by the troubles...here is the flow of my installation:
1. install osx 10.5.6 & partition disk (EFI/OSX/LINUX/WINDOWS)normally
2. install rEFIt and execute an "analyze" action & reboot
3. boot up by Vista cd and formatted to NTFS(partition WINDOWS) & perform synchronization of GPT and MBR
4. reboot by XP cd and install normally
so far, dual boot works fine
5. install ubuntu 8.04 with "apci=off" option, during the installation, freezed... and tried again, finished normally...:confused: could anybody tell me the reason please?
and now the rEFIt can recognize the Linux installation, but the MBR is not the same with GPT, and I can't launch linux (system freeze after grub menu)

what should i do to make the triple system work?
BTW, i met the "no smoking"-like symbol while osx was booting, and the xp showed "ntosXXXX.exe is damaged", after many many rebooting of macbook, turn back to normal...what's wrong?
:mad::mad:

---

### Post by cyberdork33 on 2009-03-31
> **genal said:**
> hello all,
I just bought the early-2009 Macbook white(5,2) a couple days ago, and I am getting mad by the troubles...here is the flow of my installation:
1. install osx 10.5.6 & partition disk (EFI/OSX/LINUX/WINDOWS)normally
2. install rEFIt and execute an "analyze" action & reboot
3. boot up by Vista cd and formatted to NTFS(partition WINDOWS) & perform synchronization of GPT and MBR
4. reboot by XP cd and install normally
so far, dual boot works fine
5. install ubuntu 8.04 with "apci=off" option, during the installation, freezed... and tried again, finished normally...:confused: could anybody tell me the reason please?
and now the rEFIt can recognize the Linux installation, but the MBR is not the same with GPT, and I can't launch linux (system freeze after grub menu)

what should i do to make the triple system work?
BTW, i met the "no smoking"-like symbol while osx was booting, and the xp showed "ntosXXXX.exe is damaged", after many many rebooting of macbook, turn back to normal...what's wrong?
:mad::mad:

Please follow instruction here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by genal on 2009-04-01
many thanks!

---

