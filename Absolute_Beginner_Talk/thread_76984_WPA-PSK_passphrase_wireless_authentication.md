---
title: "WPA-PSK passphrase wireless authentication"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by Ford Prefect on 2005-10-16
I have a D-Link DWL G520 REV. B wireless card.
I need a way to make it work with wpa-psk passphrase wireless authentication.

I have searched everywhere for this over the past 2 months, and have found nothing.

If this is even possible (I hope it is) then I will also need to make my computer access the internet through an external modem connected to the wireless router.



The only reason I am not using ubuntu (or any other distro for that matter) is  because I can't access the internet from my computer when I am running Linux.

I have ubuntu on a second hard drive in my machine and I don't like having to plug it in just so that I can word process something on Linux instead of windows.

Furthermore, can anyone reccomend any good books that explain how to use linux for a beginner?

---

### Post by kane77 on 2005-10-16
This is all I had to do to get it working 

1. System Menu -> Administration -> Networking
2. Wireless Networks will be the top option
2a. Click Setup (or it might be "Properties")
2b. Type in your wireless network name 
2c. Usually, change Static IP to DHPC
3. Click Save
4. Now highlight the Wireless Network under Networking Admin, and click Activate

Hope that helps, sorry it's not exact.

The books I have are - A prctical guide to linux, Linux for dummies 6th edition, Hungry minds - Debian GNU Linux Bible, Sams Tech yourself linux in 24 hours... Hope they are useful to your needs...

---

### Post by alper_tr on 2005-10-16
We definetely need WPA-PSK support out of box. I am trying for the last 2 days to get WPA-PSK to work, it fails and fails...

None of the things described in the forums are working... at least they are not simple.. Why can't we have that on Gnome menu/system/networking... and when we edit having the option to choose wpa-psk insted of wep.. 
Is it really that hard???

---

