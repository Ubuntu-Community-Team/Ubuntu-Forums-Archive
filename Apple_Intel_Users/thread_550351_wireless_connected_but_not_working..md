---
title: "wireless connected but not working."
date: 2007-09-13
forum: Apple Intel Users
---

### Post by ic3warm on 2007-09-13
I have a core 2 duo processor and ubuntu is great and all but the wireless wont work. I installed the madwifi drivers and all and then i can find my wireless and check the roaming mod box and then i will get a wireless signal and i enter my password and it says its connected but my web browser and stuff do not work. Please help, i have searched but the other posts arent like my problem. Thanks.

screenshot of "connected" wireless 
[http://s189.photobucket.com/albums/z190/bowser401/?action=view&current=Screenshot-1.png](http://s189.photobucket.com/albums/z190/bowser401/?action=view&current=Screenshot-1.png)

---

### Post by rivalarrival on 2007-09-14
Can you browse to your access point's web interface? (usually 192.168.1.1)

Can you ping anything on your local network?  How about an IP on the internet? (64.233.167.99 is one of Google's)

If not, I would try temporarily turning off encryption at the access point and on the computer... I've had that problem a few times on several different machines, where it said I was connected but no data would pass because I was using the wrong key.

---

### Post by tehexile on 2007-09-16
>  Can you browse to your access point's web interface? (usually 192.168.1.1)

Can you ping anything on your local network? How about an IP on the internet? (64.233.167.99 is one of Google's)

i have the same problem, tried both of these and they didn't work.

> 
If not, I would try temporarily turning off encryption at the access point and on the computer... 

how do you do this?

---

### Post by Kzap333 on 2007-09-23
> **tehexile said:**
> i have the same problem, tried both of these and they didn't work.



how do you do this?

I have the same problem I think. I NEED help.

---

### Post by cyberdork33 on 2007-09-23
Since a version of the module is included with the Ubuntu restricted modules package, you need to make sure you block the original module from loading to allow your custom module to load instead:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

If that doesn't help matters, you might try different versions of the source, it seems 2695 is working for most people.
[http://snapshots.madwifi.org/madwifi...0070829.tar.gz]("http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz")

---

### Post by Kordesh on 2007-10-23
I have the same problem as the person above. I can get a connection using the firmware cutter (i have everyones favorite wireless chipset -_-) but I can't actually get a connection to anything. There's no security outside of mac filtering on the access point, and the device is still listed on the filter as one allowed access. Unfortunately I can't try using ndiswrapper because while I can get the common files Gutsy doesn't seem to have any utils that will work for it at all. I'm about ready to give up after crawling the net for six hours and reinstalling and restarting to get it to finally go through :(

---

### Post by cyberdork33 on 2007-10-23
> **Kordesh said:**
> I have the same problem as the person above. I can get a connection using the firmware cutter (i have everyones favorite wireless chipset -_-) but I can't actually get a connection to anything. There's no security outside of mac filtering on the access point, and the device is still listed on the filter as one allowed access. Unfortunately I can't try using ndiswrapper because while I can get the common files Gutsy doesn't seem to have any utils that will work for it at all. I'm about ready to give up after crawling the net for six hours and reinstalling and restarting to get it to finally go through :(

Which is everyone's favorite chipset? Broadcom?

the appropriate ndiswrapper-utils to use:
```
sudo aptitude install ndiswrapper-utils-1.9
```

---

### Post by subferno on 2007-10-23
I am having the same problem with the Santa Rosa MBP.

I have used the 2695 driver and disabled the restricted moduels.

---

### Post by Kordesh on 2007-10-25
> **cyberdork33 said:**
> Which is everyone's favorite chipset? Broadcom?

the appropriate ndiswrapper-utils to use:
```
sudo aptitude install ndiswrapper-utils-1.9
```

I've been having trouble getting the utils )=. I'll try that out though sometime tonight.

---

### Post by ward83 on 2007-10-25
I was able to get mine working (BCM4328 chipset) using ndiswrapper and a dell windows driver. Download this driver from Dell:
[http://ftp.us.dell.com/network/R140746.EXE](http://ftp.us.dell.com/network/R140746.EXE)

Unzip it using:
```

unzip R140746.EXE

```

It will unzip a bunch of exe files which are unneeded. We just want the drivers in the 'DRIVER' directory.

Then, follow the steps outlined in this howto:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

Hope this helps

---

