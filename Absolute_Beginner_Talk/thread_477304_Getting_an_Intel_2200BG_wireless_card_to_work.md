---
title: "Getting an Intel 2200BG wireless card to work"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by pi3832 on 2007-06-18
I'm running Xubuntu 7 on a refurbished T30 ThinkPad, and I can't seem to get the wireless to work.

I gave up on the Cisco Aironet wireless card that came with the T30, and have replaced it with an Intel 2200BG card.  I used the bootable image file from [Command-Tab]("http://www.command-tab.com/2006/02/26/unauthorized-wireless-cards/") to run **no-1802.com** and clear the BIOS error for using a "non-IBM" wireless card.  The 2200BG now works fine with WPA under XP.

Since I'd fiddled with the wireless settings while I still had the Cisco card installed, I deleted the Xubuntu partition and re-loaded it.  I used the GUI package manager to load all of the available updates for the system.  Wireless manager and wpa_supplicant are both loaded.

According to [this page](http://linux-wless.passys.nl/query_part.php?brandname=Intel), the 2200BG should be supported using the **ipw2200** driver.

According to [this page](http://hostap.epitest.fi/wpa_supplicant/), the **ipw2200** driver should be supported by wpa_supplicant.

What should I check/do next?  Should I try the manual wpa-supplicant configuration detailed [in this thread](http://ubuntuforums.org/showthread.php?t=47406)?  How would I go about checking what driver is being loaded for the wireless card?

Any help is appreciated.

---

### Post by jda1701 on 2007-06-18
First verify that HAL finds your 2200BG.

If this returns any lines with Intel Pro 2200BG then your hardware was found successfully.
```
lspci | grep 2200
```

Make sure the ipw2200 module is loaded
```
lsmod | grep ipw2200
```


If the module is not loaded then
```
modprobe ipw2200
```

If there are no errors
```
insmod ipw2200
```

Lets see if that helps.

---

### Post by pi3832 on 2007-06-18
Thanks.  The T30's at home.  I'll give that a shot tonight.

---

### Post by coffeecat on 2007-06-18
The Intel 2200BG wireless chipset works absolutely out of the box in Ubuntu Feisty so long as you use the Network Manager applet - wpa and all. No mucking about with wpa-supplicant or the command line needed.

I don't know whether NM comes with the default install of Xubuntu (I should imagine it would), but in Ubuntu NM is a panel applet and so easy to set up.

There are two things to consider if you use NM. It can't cope with a hidden ESSID and it nags you for a keyring password before it connects every time you boot up, unless you [use this excellent hack]("http://ubuntuforums.org/showthread.php?t=463639").

---

### Post by pi3832 on 2007-06-19
> **jda1701 said:**
> First verify that HAL finds your 2200BG.

If this returns any lines with Intel Pro 2200BG then your hardware was found successfully.
```
lspci | grep 2200
```

Make sure the ipw2200 module is loaded
```
lsmod | grep ipw2200
```

No love.

Hardware is detected, module is loaded.  Checked firmware, and it's the latest release AFAICT.

I fiddled the /etc/network/interfaces file, and the wireless shows up in the Network Manger GUI, but it only lists WEP.  Now, I need to convince it to use WPA.

---

### Post by pi3832 on 2007-06-19
> **coffeecat said:**
> The Intel 2200BG wireless chipset works absolutely out of the box in Ubuntu Feisty so long as you use the Network Manager applet - wpa and all. No mucking about with wpa-supplicant or the command line needed.

I don't know whether NM comes with the default install of Xubuntu (I should imagine it would), but in Ubuntu NM is a panel applet and so easy to set up.

There are two things to consider if you use NM. It can't cope with a hidden ESSID and it nags you for a keyring password before it connects every time you boot up, unless you [use this excellent hack]("http://ubuntuforums.org/showthread.php?t=463639").

Xubuntu does come with NM.  The only thing I didn't know to check was whether the ESSID is hidden or not.

And apparently I may be a complete dumbass in that I think everything I need is listed in [this sticky](http://ubuntuforums.org/showthread.php?t=318539) in the Wireless forum.  I'll try that tonight, if I get the chance.  (I'm babysitting. :roll:)

---

### Post by pi3832 on 2007-08-28
I put my laptop on the shelf for a few months.

This past weekend I tried [wicd]("http://wicd.sourceforge.net/wiki/doku.php?id=faq") instead of Network Manager.  It was painless, and now the wireless works easily.

If you're having trouble with wireless, I highly recommend trying [wicd]("http://wicd.sourceforge.net/wiki/doku.php?id=faq").

---

