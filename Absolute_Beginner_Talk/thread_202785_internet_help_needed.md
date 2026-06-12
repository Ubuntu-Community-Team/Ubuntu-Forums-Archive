---
title: "internet help needed"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by Stromham on 2006-06-24
i need to install ndiswrapper and then my linksys cd, but when i install ubuntu i will not have any internet connection, now the file is a .tar.gz, is it possible to put this file onto a cd and install it on the computer? how exactly do i use ndiswrapper??

---

### Post by hajk on 2006-06-24
Why do you need to install ndiswrapper via a tar.gz file? It is already included in the kernel modules, just load it with "sudo modprobe ndiswrapper".

---

### Post by Stromham on 2006-06-24
can you further explain how i would use it to install my wireless card?

---

### Post by hajk on 2006-06-24
Sure, you should also install the ndiswrapper-utils package (it is on the liveCD), make sure that the liveCD is listed as a repository in /etc/apt/sources.list (it still is if you haven't changed it after the initial install of Dapper).

Next you have to install the Windows driver for your wireless device, it is on the Linksys CD and should have an .inf extension. There may also be a similarly named file with a .sys extension. If there are different drivers for various Windows versions, then just pick one (or try a different one if there are problems). Copy the driver files to your home directory, and work from there.

The install is done from your home directory with the command "sudo ndiswrapper -i xxxxx.inf", where you replace the xxxxx with the driver name. Then you must make sure that ndiswrapper is automatically loaded at boot with the command "sudo ndiswrapper -m".

If you haven't already loaded the ndiswrapper module, then do it now with "sudo modprobe ndiswrapper". Insert the wireless device, and then check whether everything is loaded with the command "sudo ndiswrapper -l" (the letter l), and it should tell you whether it is loaded and the device present. 

Finally, open System -> Administration -> Networking menu, and a wireless interface should be visible there: highlight it, select Properties, enable the interface and select your essid, enter the WEP key, and choose DHCP. With Properties set up, activate the interface, and make sure to select it as default.

Good luck!

---

### Post by Gaute65 on 2006-06-24
Read [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

