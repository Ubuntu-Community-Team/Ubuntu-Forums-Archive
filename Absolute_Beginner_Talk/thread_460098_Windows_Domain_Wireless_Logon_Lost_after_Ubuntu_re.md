---
title: "Windows Domain Wireless Logon Lost after Ubuntu reboot"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Jeneral22 on 2007-05-31
Hello all,

This is rather complex and I wasn't receiving any search results so perhaps my search wasn't worded correctly.

I have a dual boot Ubuntu WinXp at work. The laptop is an IBM Thinkpad A30 with built in Wireless card. When I boot to XP I log onto our work domain cellectfoam however if I first boot Ubuntu and then reboot or shutdown and boot up with WinXP and I attempt to log on the computer flashes a warning that the domain controller cannot be contacted. I then use my local account on the computer and boot without a problem and the wireless works great and I am able to use all network resources. The only way I have found to repair the domain logon is to do a system restore from the admin (local account) and reboot then everything works as before until I run Ubuntu again and the problems return.

Any help would be appreciated. I am just getting into Ubuntu and wish I had more knowledge because I would convert the whole damn place!

Thanks

---

### Post by steve.horsley on 2007-05-31
Does it happen if you fully poser off the laptop instead of resetting? I wonder if Ubuntu is leaving the hardware in a sate that Windows doesn't like.

Could it be time related? Maybe the time needed to do a restore is taking you past some timeout of something else on the network. I ask because I can't see how having run Ubuntu can directly affect the configuration stored by XP.

---

### Post by Jeneral22 on 2007-06-01
I believe that Ubuntu is leaving the wireless in a state that isn't happy for XP. I have tried rebooting and a full shutdown but the problem continues. I have had to use System Restore and now the XP installation is a little screwy. I am not worried I could always just reinstall XP because it is due for one soon anyway.

thanks.

---

### Post by Jeneral22 on 2007-06-01
Some additional information: I was able to fix my XP logon finally but the steps I had to take might assist in a fix for the bigger problem. I had to Delete my computer account from Active Directory then unjoin the domain on my local PC - reboot - then rejoin the computer to the Active Directory Domain. This fixed the problem of the XP after Ubuntu restart. I am not sure if Ubuntu is coming up strange on the Windows Server 2003 which then causes the server to in essence block my PC when I logon to the domain through XP?

Weird...

Thanks for looking

---

