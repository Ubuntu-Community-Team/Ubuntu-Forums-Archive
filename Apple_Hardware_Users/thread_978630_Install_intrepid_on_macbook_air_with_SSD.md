---
title: "Install intrepid on macbook air with SSD"
date: 2008-11-11
forum: Apple Hardware Users
---

### Post by gillesbg on 2008-11-11
I have a macbook air with 60GB SSD
I tried to install Ubuntu 8.10 32 from the live cd
The install went fine.
When I rebooted after install, it remains stuck at the first greyish screen that appears immediately after the mac sound a second after setting power on.

Then I installed  Kubuntu 8.04 32 (which had been running fine before)
Under Kubuntu 8.04, I updated all packages and asked a network version update to Kubuntu 8.10 under Adept.
Again the install went fine but when I rebooted after install 
I got stuck  with a widget containing the error message 
"Cannot parse theme file /usr/share/apps/kdm/themes/kubuntu"
There is a clickable button to say OK but the mouse and track pad 
do not respond.

Any clue?

---

### Post by cyberdork33 on 2008-11-11
reinstall 8.10. It has the best support for you machine. Be sure to install grub to the root partition rather than the MBR (this is done by clicking the "Advanced" button on the final window of the installer).

Follow the directions here to get it booting:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

You can also get documentation for your Mac here:
[https://help.ubuntu.com/community/MacBook%20Air%201%2C1%20and%20Intrepid](https://help.ubuntu.com/community/MacBook%20Air%201%2C1%20and%20Intrepid)

---

### Post by stream303 on 2008-11-11
Back-burner tip because of the SSD disk:

Once you get it up and running, you may want to change the kernel scheduler to "deadline" instead of the default, cfq, since there are no moving parts on the SSD.

On my netbook that has an SSD, I just appended

```
elevator=deadline
```

to the end of the kernel line in grub, although there are probably better ways of defining this in grub so you don't have to do it on every kernel update.

(Update- I'm losing track of time it seems:)
[http://ubuntuforums.org/showthread.php?p=5392654](http://ubuntuforums.org/showthread.php?p=5392654)

---

### Post by gillesbg on 2008-11-12
> **cyberdork33 said:**
> reinstall 8.10. It has the best support for you machine. Be sure to install grub to the root partition rather than the MBR (this is done by clicking the "Advanced" button on the final window of the installer).

Follow the directions here to get it booting:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)


Instructions on the link above worked fine for me.
More precisely:
in the last window of installer 
 select "Advanced" button
 chose to install grub on /dev/sda
 complete installation
 reboot with rEFIT
 start partition tool
 update partition tool
 reboot on disk

Thanks to those who helped!

---

