---
title: "Ubuntu Package List For Fresh Install Question"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by ityro on 2007-10-08
When I use the Instructions provided by the site shown below to create a list of installed Ubuntu Packages while preparing for a fresh install I get a file as displayed in the attached Screen Shot. As you  can see the instructions to "Install"  are not aligned in the list.  The tab setting seems to depend on the length of the package name. Is that normal? 

THANKS for your time.

SITE:
[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

INSTRUCTION:
dpkg --get-selections | grep -v deinstall > ubuntu-packages

MY SYSTEM:
Dual-boot XP/Ubuntu 7.04 on a HP/Compaq nx9010 notebook 
w/40GB HDD and Iomega 80GB usb HDD. ATI Display: PCI Bridge 
[GP 340M] Radeon IGP 330M/340M/350M RS200/RS200M AGP Bridge 
[IGP 340M].

---

### Post by jfinkels on 2007-10-09
Unfortunately, you have not attached a screenshot!

The output of ```
dpkg --get-selections | grep -v deinstall > ubuntu-packages
``` should return a list of installed packages, and should redirect that output to a text file called 'ubuntu-packages'.

To install all the packages listed in the text file 'ubuntu-packages', do ```
sudo dpkg --set-selections < ubuntu-packages && sudo dselect
```

---

### Post by ityro on 2007-10-10
Sorry for the Screen Shot and that it took so long to get back to you. My ISP is upgrading and does not stay up long enough for me to make a reply. Here is the screenshot and thanks for your response.
 



MY SYSTEM:
Dual-boot XP/Ubuntu 7.04 on a HP/Compaq nx9010 notebook 
w/40GB HDD and Iomega 80GB usb HDD. ATI Display: PCI Bridge 
[GP 340M] Radeon IGP 330M/340M/350M RS200/RS200M AGP Bridge 
[IGP 340M].

---

### Post by jfinkels on 2007-10-10
Most whitespace (including tabs and spaces) doesn't matter to programs that read from a file in this manner. As long as each line consists of the name of the package followed by it's selection state (in this case, the state is "install"), dpkg will set the selections just fine!

---

### Post by stchman on 2007-10-10
> **ityro said:**
> When I use the Instructions provided by the site shown below to create a list of installed Ubuntu Packages while preparing for a fresh install I get a file as displayed in the attached Screen Shot. As you  can see the instructions to "Install"  are not aligned in the list.  The tab setting seems to depend on the length of the package name. Is that normal? 

THANKS for your time.

SITE:
[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

INSTRUCTION:
dpkg --get-selections | grep -v deinstall > ubuntu-packages

MY SYSTEM:
Dual-boot XP/Ubuntu 7.04 on a HP/Compaq nx9010 notebook 
w/40GB HDD and Iomega 80GB usb HDD. ATI Display: PCI Bridge 
[GP 340M] Radeon IGP 330M/340M/350M RS200/RS200M AGP Bridge 
[IGP 340M].

If you are just wanting to see what packages are installed then type the following:

```
dpkg -l > ~/pack_install.txt
```

This will give you a list of all installed packages in a text file in your home folder.

---

### Post by ityro on 2007-10-10
Thank you jfinkels that's what I wanted to know! And thank you stchman for another tool.

THANK YOU BOTH FOR YOUR TIME.

---

