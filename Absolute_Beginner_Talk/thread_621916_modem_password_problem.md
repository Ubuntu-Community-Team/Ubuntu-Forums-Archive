---
title: "modem password problem"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by ubiubi on 2007-11-24
Hi

I've just installed ubuntu 7.10. No internet connection.!
I am also running XP on the same system and internet works fine! After visiting this forum I tried to download firmware and extraction ware for the "THOMSON speedtouch330 modem" (from XP) which I then transfered to Ubuntu. A waste of time! cutting and pasting commands into the terminal at various stages resutled in messages like "file/directory does not exist etc...

Finally I downloaded a members file "usbads/modemmanager_0.5.386.deb"

Great!  It gave me a modem icon at the top of the screen which asked me to type in my ISPs internet connection "username" and "password". Everytime I try to connect it says I have an incorrect password/username. I've tried unplugging the modem before and after retyping in the info. Remember these codes work fine on XP! Finally I rand my ISP (wanadoo.fr) and the only confirmed the codes.

I was playing around at the beginning before I installed "usbads/modemmanager_0.5.386.deb"
and I was asked to put in these codes. At the time I didn't realise the significance and used any old codes.I have now idea/ recollection how I arrived at that prompt originally and now I'm at a complete loss as to what I can do!

Any ideas?

Many thanks just in case!

---

### Post by FreewheelinFrank on 2007-11-24
I suspect that you have created a file with the wrong username and password info somewhere.

There's a thread for the ADSL Modem Manager here:

[http://ubuntuforums.org/showthread.php?t=585647](http://ubuntuforums.org/showthread.php?t=585647)

You could read through that thread for information, or post a question there.

As you say you've just installed Ubuntu, it might be easier to do a clean install and then install the modem manager.

Be sure to get the latest version which is usbadslmodemmanager_0.5.8_i386.deb

EDIT: The original ADSL USB Modem Manager thread:

[http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)

---

### Post by ubiubi on 2007-11-25
hi Freewheelinfrank, thanks for your time!

I tried to do a clean install. I used the command        pkill -9 usbadslmodemmanager

This was accepted. I rebooted the machine and discovered the modem icon still present. I tried to install the package again and it stated that I was trying to reinstall an existing package! So I suppose the command I used did not remove the existing modem manager software and I feel i'm going nowhere fast. 

Any suggestions?

Thanks for you help.

---

### Post by FreewheelinFrank on 2007-11-25
Well, I'm not exactly an expert- but I think the way to uninstall is to type-

sudo dpkg -r usbadslmodemmanager

in the terminal.

If you post in the ADSL USB Modem Manager thread, it's very possible that Steven Harper (the author) may reply- he's been very helpful to me and others trying to connect to the internet with a USB modem.

I bought a modem/router in the end just to get a hassle-free connection. I'm pretty sure I used the command above to remove the Modem Manager when I no longer needed it.

You said in your original post: 'I've just installed ubuntu 7.10'. As a last resort, you could always do a clean install of Ubuntu- if it's a recent install anyway, you won't have made many changes to the original settings, I expect.

Try uninstalling the Modem Manager first, and posting a question on the Modem Manager thread.

Good luck! Hope you get connected soon!

---

### Post by ubiubi on 2007-11-26
Hi again

I finally managed to do a clean install of the modem manager - still no connection. I suppose my only hope is to do the clean install of ubuntu - gulp! This terrrifies me. I don't want to erase XP in the process. I'm exploring using fixmb from the windows recovery console.  - oh my god!

Thanks for the advice

---

### Post by zabien1970 on 2007-11-26
Try installing Wicd
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by JBAlaska on 2007-11-26
If the above does not work, have a look at this;
```
http://steve-parker.org/speedtouchconf/
```

---

### Post by FreewheelinFrank on 2007-11-26
> **ubiubi said:**
> Hi again

I finally managed to do a clean install of the modem manager - still no connection. I suppose my only hope is to do the clean install of ubuntu - gulp! This terrrifies me. I don't want to erase XP in the process. I'm exploring using fixmb from the windows recovery console.  - oh my god!

Thanks for the advice

I'm assuming you have dual boot with a Linux partition like me, with the Linux partition divided into /, /home and Swap.

Just run the live CD again and overwrite the / partition with a fresh install of Ubuntu.

If that worries you, post here and wait for a response:

[http://ubuntuforums.org/showthread.php?t=585647&page=7](http://ubuntuforums.org/showthread.php?t=585647&page=7)

Somebody will probably know the likely location of the file containing the wrong username/password info.

---

### Post by ubiubi on 2007-11-29
Hi
 I4m having problems installing my speedtouch 330 modem. This is my second installation of ubuntu 7.1
In the first installation (With the help of usbadslmodemmanagerXXX.deb  -- it's the latest version) I finally got a modem logo up top and a posative synchronisation status, but I had problems with mt ISP passwords. Following advice from this forum I did a clean install of Ubuntu and this time I get no icon up top.  The hardware manager recognises the speedtouch exists but refuses to connect it. When I go Administration<network settings<modem connection<properties<enable connection and then ener al the ISP details I cannot press the OK button to confirm everything (It's greyed out) so? what can I do. All this has been done after first installing the above package. I don't understand why it should be diffferent this time. This is killing my enthusiasm for the OS. Help me please!!!!!:(

Many thanks for any help

---

### Post by fineas on 2007-11-29
This maybe useful [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch). It's from the HELP menu of our distro

---

### Post by ubiubi on 2007-12-01
Hi all who gave advice. Problem solved. Re-installed ubuntu and ran usbadslmodemmanager from the terminal (package manager had no effect!) It works like a charm!

Thanks for your help

---

### Post by FreewheelinFrank on 2007-12-01
Glad to hear it.

---

