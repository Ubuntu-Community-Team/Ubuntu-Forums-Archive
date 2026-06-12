---
title: "Suspend+Hibernate not working on U50"
date: 2011-07-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by redFlameStar on 2011-07-27
hi guys,
I install Ubuntu 11.04 on my ASUS U50 was :D that ubuntu liked my laptop until I close the lip. Either Suspend nor Hibernate works; screen goes black, fan keeps spinning, and power light stay on. I move around a lot so it's a really big pain in the side. I'm to the point of going back to Win7 fully. Any help would be great.
Thanks

---

### Post by Toz on 2011-07-27
Lets go for the possible easy fix first. Have a look at the solution posted at: [http://ubuntuforums.org/showpost.php?p=9180298&postcount=7]("http://ubuntuforums.org/showpost.php?p=9180298&postcount=7")

Reference link: [http://robbyx.net/blog/?p=190]("http://robbyx.net/blog/?p=190")

---

### Post by redFlameStar on 2011-07-27
i kinda do and don;t understand, Seems like a work around not a fix.

---

### Post by Toz on 2011-07-27
Yes, it is a workaround. There is a bug in the current kernel versions where usb3 ports prevent suspend functionality - here is one such bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998") (see post #61) - there are others if you search for them. I've used this fix a number of times to fix suspend issues. The workaround in the above link is actually easier to implement - you should give it a try to see if it works. If it doesn't, you can just delete the file and try something else.

Here is how to implement the workaround.

1. Open a terminal window and type in the following:
```
sudo gedit /etc/pm/sleep.d/20_custom-xhci_hcd
``` (type in your password when prompted to be granted permissions to create the file)

2. Copy/paste the following into the gedit window:
```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".
TMPLIST=/tmp/xhci-dev-list

case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/xhci_hcd/ | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
              # Unbind xhci_hcd for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind xhci_hcd for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/xhci_hcd/bind
    done
    rm $TMPLIST
        ;;
esac
```

3. Save and exit the file.

4. We need to make the file executable. To do so, type the following in the terminal window:
```
sudo chmod 755 /etc/pm/sleep.d/20_custom-xhci_hcd
```

5. Now try to suspend.

What this file does is it unbinds the usb3 drivers from the kernel prior to suspend and reattaches them during resume.

---

### Post by redFlameStar on 2011-07-28
My laptop doesn't have a USB3 port, but i tried the fix anyway and didn't work. Have any other ideas??

---

### Post by Toz on 2011-07-28
Ok. Lets try some kernel parameters. See this link for instructions on setting kernel parameters ([https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")).

Try these kernel parameters:
- acpi_osi=Linux
- acpi_osi=\"Linux\"

Also, attempt a suspend and after reboot to recover system, post back the contents of the following files:
- /var/log/pm-suspend.log
- /var/log/kern.log
- /var/log/kern.log.1

and the results of the following commands:
```
lsmod
ls /sys/bus/pci/drivers/xhci_hcd/
```

---

### Post by OpenSage on 2011-09-21
> **redFlameStar said:**
> hi guys,
I install Ubuntu 11.04 on my ASUS U50 was :D that ubuntu liked my laptop until I close the lip. Either Suspend nor Hibernate works; screen goes black, fan keeps spinning, and power light stay on. I move around a lot so it's a really big pain in the side. I'm to the point of going back to Win7 fully. Any help would be great.
Thanks





I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time (although I never hibernate, so don't know if it will fix that). Hope this helps some people.\\:D/

---

