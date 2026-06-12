---
title: "Using Ubuntu 15.10 on Macbook and Broadcom wireless stops working after reboot"
date: 2015-11-22
forum: Apple Hardware Users
---

### Post by radar2 on 2015-11-22
I have 15.10 installed on a Macbook Pro.

Wireless works perfectly after installing the Broadcom driver using [COLOR=#000000]sudo apt-get --reinstall install bcmwl-kernel-source

But after rebooting the wireless card is not detected and I don't have the wifi option under Network Manger. If I reinstall [/COLOR][COLOR=#000000]bcmwl-kernel-source it starts working and is fine until I reboot again.

I've read through a few threads that discuss blacklisted drivers and have followed their advice including purging all wireless drivers and reinstalling, but this has not solved the problem.

Can anyone suggest possible solutions?

Thanks![/COLOR]

---

### Post by Hyltixa on 2015-11-22
Hello!

what modell of macbook pro do you have ? :)

---

### Post by grahammechanical on 2015-11-22
Please post the output of these 2 commands

```
iwconfig
rfkill list
```

Regards

---

### Post by radar2 on 2015-11-23
> **grahammechanical said:**
> Please post the output of these 2 commands

```
iwconfig
rfkill list
```

Regards

Thanks, output is:

```

iwconfig
lo        no wireless extensions.
enp0s10        no wireless extensions.


rfkill list
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

> **Hyltixa said:**
> Hello!

what modell of macbook pro do you have ? :)

Hi, it's a 2010 Macbook Pro.

Is anyone able to suggest any solutions based on this output?

iwconfig
lo        no wireless extensions.
enp0s10        no wireless extensions.


rfkill list
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by howefield on 2015-11-25
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by radar2 on 2015-11-27
Sorry to bump, but any suggestions on how to fix this issue?

---

### Post by BobUgh on 2015-12-08
I was running Ubuntu 12.04 LTS [edit: it wasn't the Mac specific release] on a 2010 MacBook Pro 13" for a short time a week or two ago, and got a similar result. The first time I booted up, wireless wasn't working, I went (via GUI) to system settings > additional drivers ; it recommended broadcom wireless&#8230; I clicked to do it, after some time it finished then reported "You will have to reboot for new settings to take effect" (or something like that.) But wireless immediately worked after installing the broadcom driver, I didn't need to reboot. If I did reboot, wireless didn't work.

I gave up. I eventually plan on installing Ubuntu 14.04 LTS on it, (and dual boot), as [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) says that version of Ubuntu is the recommended for MacBookPro 7,1 ?

Have you had wireless work with any version of Ubuntu on your 2010 MacBook Pro?

The page [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages) has a different support matrix and is apparently in need of updating. Somewhere else I thought I saw a recommendation to just use the latest version, but I can't find that now, and I'm not sure if it meant latest LTS version.

To complicate things, I just got a dual band wireless N usb adapter just so I can connect at 300Mbs on the 5 GHz band, I wonder how OSX or Ubuntu is going to react to that. For me, it could make this internal broadcom problem moot.

---

### Post by dellboy56 on 2015-12-12
Hello there thread user i got same macbook as you haha anyways to get your wifi working as this worked for me get your usbkey and stick it in then go to pools/main/d/dkms install that then go back to pools restricted bcmwl then bcmwl.deb click that install it then your wifi should work let me know if this helped and mark your thread as solved

---

