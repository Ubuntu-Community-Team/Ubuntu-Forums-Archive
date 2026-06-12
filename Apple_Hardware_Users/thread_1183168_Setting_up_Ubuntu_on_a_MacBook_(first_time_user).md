---
title: "Setting up Ubuntu on a MacBook (first time user)"
date: 2009-06-09
forum: Apple Hardware Users
---

### Post by circyn on 2009-06-09
Hi there, 
I've just started using Ubuntu on my MacBook and I'm a little lost.  I've partitioned my Hard Drive and can access Ubuntu via Boot Camp but I have two problems I can't resolve - 

1)  I can't set up my wireless internet connection.  I have entered the SSID, WEP Key etc but I can't get a connection.

2)  I can't get any Windows based applications to run in Ubuntu - it keeps failing to extract the setup.exe files.

Any ideas?  Any help would be greatly appreciated.  I want to be able to run Windows apps for research but without using Windows and I need my Mac for the design work I do.

Thank you very much

Chris

---

### Post by superdan006 on 2009-06-09
> **circyn said:**
> 

2)  I can't get any Windows based applications to run in Ubuntu - it keeps failing to extract the setup.exe files.


You're using Wine, right?

---

### Post by tiagobt on 2009-06-09
What is the model of your MacBook?

To find out, paste the following command into a terminal window:
```
sudo dmidecode -s system-product-name
```

Linux doesn't run Windows programs natively. You can install a Windows emulator with the following command:
```
sudo apt-get install wine
```

Then, enter the folder where the file **setup.exe** is located and run it:
```
cd [COLOR="Green"][folder where the file is located][/COLOR]
wine setup.exe
```

---

### Post by cyberdork33 on 2009-06-11
> **circyn said:**
>  1)  I can't set up my wireless internet connection.  I have entered the SSID, WEP Key etc but I can't get a connection.
There is documentation for your mac version that will help you get everything working. Please start here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

As for the windows applications, they do not "just run" in Linux. You have to try Wine, or use a VM with Windows installed.

---

