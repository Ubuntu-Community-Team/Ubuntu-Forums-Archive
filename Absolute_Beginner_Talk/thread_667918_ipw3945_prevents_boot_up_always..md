---
title: "ipw3945 prevents boot up always."
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by SaJellish on 2008-01-14
Hello all,
     I have a dv6600 series HP laptop. I had lots of trouble installing 7.10 so I reverted back to 7.04. The installation worked as a peech and I had not issues at all. I formatted the / with RieserFs as opposed to ext3. Everything worked out fine as it detected my Vista (which made me very happy) and I was able to complete installation without any glitches. 
   But after installation was over PC got rebooted I can boot into Vista but not into Linux. I always get the following error : **ipw3945 error sending LEDS_CMO timeout after 500 ms**
   Problem occurs irrespective of the fact that wireless is ON or OFF.
   I don't know if I even want to use wireless LAN and the biggest issue is I cant even boot into my Linux even once. There are a couple of solutions for the said problem but, forgive my naivety, I don't know how to use sudo when I cant even boot.
     Any help will be deeply appreciated.........
Thanks and Regards,
          SaJe

---

### Post by angryfirelord on 2008-01-15
Looks like something funky with the ipw3945 driver. Let's see if the iwlwifi driver will work better.

First thing is you need to be able to boot into Ubuntu. If recovery mode does not work, then pop in your Ubuntu LiveCD and mount Ubuntu's / partition.

Now, we must blacklist the old module. Run this:
```
sudo gedit /etc/modprobe.d/blacklist
```
(If you're using the LiveCD, then make sure you're editing the installed Ubunu partiton, not the LiveCD)
Scroll down to the bottom. Add this line at the end:
```
blacklist ipw3945
```
Save and exit. Next, run:
```
sudo gedit /etc/modules
```
Add at the end:
```
iwl3945
```
Save and exit. Try loading Ubuntu normally.

---

