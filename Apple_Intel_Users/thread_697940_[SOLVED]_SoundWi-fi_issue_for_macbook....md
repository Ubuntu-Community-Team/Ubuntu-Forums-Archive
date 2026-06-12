---
title: "[SOLVED] Sound/Wi-fi issue for macbook..."
date: 2008-02-15
forum: Apple Intel Users
---

### Post by k3y5rmy1if3 on 2008-02-15
ugh...I feel so stupid. when i installed ubuntu, i chose the english us keyboard layout, and didn't see that there was a macbook keyboard layout...do you think that could be the reason that my sound/wifi isnt working? and if so...will i have to reinstall ubuntu to fix it?

---

### Post by cyberdork33 on 2008-02-15
> **k3y5rmy1if3 said:**
> ugh...I feel so stupid. when i installed ubuntu, i chose the english us keyboard layout, and didn't see that there was a macbook keyboard layout...do you think that could be the reason that my sound/wifi isnt working? and if so...will i have to reinstall ubuntu to fix it?
No.

Which Macbook do you have? 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by k3y5rmy1if3 on 2008-02-17
I have  the newest gen 13' macbook with no superdrive and 1 gig of ram. i've been trying to set up ndiswrapper for quite a while and it hasnt been working. also, every time i try to edit the file to make the sound work, it won't let me save the changes, and says i am not authorized to do this.

---

### Post by marsmissionaries on 2008-02-17
The wifi card is a new atheros chipset. you will need to compile a madwifi snapshot from source. it must be from svn.

---

### Post by k3y5rmy1if3 on 2008-02-17
im really sorry...i know it must be irritating when people new with ubuntu ask these questions...would it be possible if you could provide a link, or simple instructions on how to do this...im quite unfamiliar w/ the os, and wouldnt want to make any vital mistakes...i appreciate ur help

---

### Post by cyberdork33 on 2008-02-17
> **k3y5rmy1if3 said:**
> im really sorry...i know it must be irritating when people new with ubuntu ask these questions...would it be possible if you could provide a link, or simple instructions on how to do this...im quite unfamiliar w/ the os, and wouldnt want to make any vital mistakes...i appreciate ur help
Don't worry about it, you do not have an Atheros Chipset anyway, you have broadcom. There is a section in the wiki to get your Wifi card working.
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

For configuration files, most have limited permissions setting to prevent unauthorized and accidental changes. When you edit a file you should make a backup first, then make your edits. You will need 'root' (administrator) access to these configuration files to save it. This can be done by running a command using sudo. For example, if I wanted to edit my /etc/fstab file which controls which partitions are mounted where on system startup, I would run:
```
sudo gedit /etc/fstab
``` This runs the 'gedit' command as root, and additionally, I pass the path and filename of the file I want to edit to gedit.

There is a fix for the Wi-Fi card, and the sound in the linked wiki page. good luck!

---

### Post by k3y5rmy1if3 on 2008-02-17
hey thx for the info, i managed to get the sound working...though i'm having a bit of trouble installing the wireless...it works fine up to the point where i have to install the bcmwl5 driver...and when i type;sudo ndiswrapper -l, it says that bcmwl5 is an invalid driver...do you have any idea y?

---

### Post by cyberdork33 on 2008-02-17
> **k3y5rmy1if3 said:**
> hey thx for the info, i managed to get the sound working...though i'm having a bit of trouble installing the wireless...it works fine up to the point where i have to install the bcmwl5 driver...and when i type;sudo ndiswrapper -l, it says that bcmwl5 is an invalid driver...do you have any idea y?
you need to remove that driver, and install the one from the wiki page.
```
sudo ndiswrapper -r bcmwl5
```

---

### Post by k3y5rmy1if3 on 2008-02-17
but...bcmwl5.inf is the one on the wiki page...unless it's R151517.EXE which it still says is an invalid driver

---

### Post by cyberdork33 on 2008-02-17
> **k3y5rmy1if3 said:**
> but...bcmwl5.inf is the one on the wiki page...unless it's R151517.EXE which it still says is an invalid driverDelete the one you have and try again as it is apparently not working correctly. The driver from Dell (R151517.EXE) should work. You have to extract the files from the package and use the bcmwl5.inf file found inside.

---

### Post by k3y5rmy1if3 on 2008-02-17
well it wont install R151517.exe because its a .exe file...im not entirely sure what to do...i followed the exact instructions on the page...the output for sudo ndiswrapper -l is

bcmwl5 : driver installed
        device (14E4:4328) present
r151517.exe : invalid driver!

i then type in the other commands...and restart x...but no luck  

;-(

---

### Post by k3y5rmy1if3 on 2008-02-17
well now im pretty sure that the bcmwl5 driver is installed...however when i put "ndiswrapper" at the bottom of the boot list, and reboot...nothing happens

---

### Post by cyberdork33 on 2008-02-17
> **k3y5rmy1if3 said:**
> well it wont install R151517.exe because its a .exe file...im not entirely sure what to do...i followed the exact instructions on the page... The page instructs you how to extract the exe file (which is actually a zip file) and use the files inside.

> **k3y5rmy1if3 said:**
> well now im pretty sure that the bcmwl5 driver is installed...however when i put "ndiswrapper" at the bottom of the boot list, and reboot...nothing happensFrom your ndiswrapper -l output, it looks as though you managed to get it. 

You should check that the ndiswrapper module is loaded:
```
lsmod |grep ndiswrapper
```

And check if the device is recognized:
```
iwconfig
```

If the device does not show up, try issuing these commands, then rebooting again:
```
sudo ndiswrapper -masudo ndiswrapper -mi
```

---

### Post by k3y5rmy1if3 on 2008-02-17
YAY!!! IT WORKS! Omg thank you so much for all your help, i really appreciate, and there's no way i could have done it myself...its really great that there's a huge ubuntu community to help other people out in situations like this.

---

### Post by cyberdork33 on 2008-02-17
> **k3y5rmy1if3 said:**
> YAY!!! IT WORKS! Omg thank you so much for all your help, i really appreciate, and there's no way i could have done it myself...its really great that there's a huge ubuntu community to help other people out in situations like this.
please mark as solved.
(The option is available at the top of the page, under "Thread Tools")

---

