---
title: "ndiswrapper?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-09-07
I installed trendnet driver with ndiswrapper, but it didn't show up in the menu. I tried to re-install it,but it tells me that it's all ready installed. Is the driver supposed to show up in the menu? Does your driver show up in the menu?

---

### Post by swoll1980 on 2007-09-07
All I want to know is if your driver shows up in this menu. You don't have know why mine isn't showing up in mine. I just want to know if this is why my wireless isn't working. Can some one please tell me if there wireless driver shows up in the menu thats in the picture posted on this thread. Please.

---

### Post by splintercellguy on 2007-09-07
The GTK utility is worthless. The best way is to do the ndiswrapper driver install from command-line: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by cubeist on 2007-09-07
Before setting up ndiswrapper you should first verify whether you can use wireless without ndiswrapper.  If you run "lspci" in the terminal you can see the exact model of your wireless chipset.  Once you know that you can search the web to see if other users have successfully got it working and if it needs ndiswrapper.  If you are sure that you need ndis then try the tutorial posted by "splintercellguy" above...

---

