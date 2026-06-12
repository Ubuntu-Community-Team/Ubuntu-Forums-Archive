---
title: "Wireless Troubles Inspiron 6000 ubuntu 6.10"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Luddy on 2006-10-28
Hello, I am having trouble getting wireless to work since I did a clean install of 6.10.  It was working fine with WPA in 6.06.

I did
```
sudo apt-get network-manager network-manager-gnome
```

but when i click on the icon in the top right the only thing it had to choose from is wired networks.

here is some information:
```
luddy@luddy-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      unassociated  ESSID:"LUDDYWiFi"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6C6F-6C62-6561-7232-3200-0000-00   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

Also I should probably note that my wireless light is not lit on the laptop and pressing FN F2 to turn it on does nothing.  I don't remember if it did with 6.06

Does anyone have any suggestions?  It almost seems as if my wireless card isn't activated since there is no option when i click on the network manager icon.  Thank you.

---

### Post by dbeltr1 on 2006-11-01
I didn't have any problems with 6.06 either. Worked like a charm. However, in 6.10 the internal wifi (Intel Pro 2915 a/b/g) wasn't enabled. I checked the Device Manager (Administration > Device Manager)to make sure it was recognized. It was. I then checked the wireless connection settings (Administration > Networking) and selected Properties for the Wireless connection and saw that it was not enabled. 

Although I selected to enable, I wasn't getting the ESSID (i'm sitting in my living room 4 feet awat from the wifi router). 

I typed in my ESSID and my network password and poof.....if worked.

Hope this helps.

---

