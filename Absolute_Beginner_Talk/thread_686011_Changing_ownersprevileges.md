---
title: "Changing owners/previleges"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by dsherburn on 2008-02-02
Hi,
I've loaded WINE and am able to run Seaclear, a windows based Nav software in Ubuntu. Seaclear "looks" at a serial port GPS to get nav data. The software won't "see" the data from the com port, if I'm logged in as my "username". However, if I log in as "root", the program is able to see the nav data come in over the serial port. So, it would seem to be a owner or privilege setting as "root" has access to TTYS0 and "username" doesn't? How can I give "username" the same ownership of the serial ports as "root" has?

Thanks in advance......
Dan

---

### Post by scorp123 on 2008-02-02
> **dsherburn said:**
>   So, it would seem to be a owner or privilege setting as "root" has access to TTYS0 and "username" doesn't? How can I give "username" the same ownership of the serial ports as "root" has? Check your current permissions, e.g. 
```
cd /dev
ls -al ttyS0
``` ... Output from my system here: ```
> ls -al ttyS0
crw-rw---- 1 root dialout 4, 64 2008-02-01 09:24 ttyS0
``` So the device belongs to "root" on my system, but members of the group "dialout" may also read from and write to it. Let's check groups here: ```
groups myusernamehere
``` ... gives on my system (things may look different on your system ...): ```
> groups scorpsusername
scorp : scorp adm dialout fax cdrom floppy tape audio dip video plugdev scanner netdev lpadmin powerdev admin fuse vmware 
```

Now let's suppose you want to give your user access to /dev/ttyS0 without risking to cripple your system in any way ... I'd go this route:

1. check what the permissions on the /dev/ttyS0 device are (see above)

2. adjust those permissions slightly in your favour, e.g. ```
cd /dev
sudo chmod g+rw ttyS0
sudo chgrp dialout ttyS0
``` ... your "ttyS0" should have the same group permissions now as mine.

3. make your user account member of the "dialout" group if it isn't already. The GUI way to do this: **System > Administration > Users and Groups **  ... then click onto your username and click the "Properties" button ... a new window should open showing you all the details of your user account. If you look closely: The window is divided by three tabs on top: "Account", "User Privileges" and "Advanced" ...  => go to "Privileges" and now for the sake of simplicity just tick all the checkboxes there. Don't worry .. your account still won't be so insanely powerful as the "root" account. Especially make sure that the checkbox for "Connect to the Internet using a modem" is ticked OK.

Login and logout and enjoy your new privileges.

The shell way:  ```
sudo usermod -a -G dialout yourusernamehere
``` ... as you can see it's waaaay faster to do this via the shell. Login and logout and you should now have access to /dev/ttyS0 ...

---

### Post by dsherburn on 2008-02-02
Scorp123,
Thanks for the detailed reply! Can you recommend a good source for a summary of the "command line" entries?

There may be another issue, however. I did all of that, and the program still says "can't open com 1" when booted under username. I wonder if there is another privilege (file?) I need to add....?

Anyway, we're making progress and thanks a bunch for your attention to the newbie questions!
Dan

---

### Post by scorp123 on 2008-02-02
> **dsherburn said:**
>  Can you recommend a good source for a summary of the "command line" entries?  The manual.  ```
man name-of-command-you-wonder-about
``` ... You don't really think I knew e.g. that "usermod" command syntax by heart? :) Nope. I looked it up before responding to your posting: ```
 man usermod
``` ... And voila, all the infos I needed were right there on the first page.

Another useful command:  **apropos**

Let's suppose you want to do something but for the life of you .. you just can't remember the command's name. "apropos" to the rescue: Chances are you still remember what the command was about, right?  So let's assume you want to know about "bluetooth" because that's the topic the program you are looking for has to do with. If I do that here I get this nice list: ```
> apropos bluetooth
/etc/bluetooth/hcid.conf (5) [hcid.conf] - Configuration file for the hcid Bluetooth HCI daemon
bluetooth-applet (1) - GNOME applet for prompting the user for a bluetooth passkey (PIN)
bluetooth-properties (1) - GTK dialog for managing properties of the bluez bluetooth stack
ciptool (1)          - Bluetooth Common ISDN Access Profile (CIP)
dund (1)             - BlueZ Bluetooth dial-up networking daemon
hciconfig (8)        - configure Bluetooth devices
hcid (8)             - Bluetooth Host Controller Interface Daemon
hcid.conf (5)        - Configuration file for the hcid Bluetooth HCI daemon
hcitool (1)          - configure Bluetooth connections
hid2hci (8)          - Bluetooth HID to HCI mode switching utility
hidd (1)             - Bluetooth HID daemon
obexpushd (1)        - receive files with OBEX protocol via Bluetooth or IrDA
pand (1)             - BlueZ Bluetooth PAN daemon
sdpd (8)             - Bluetooth SDP daemon
ussp-push (1)        - send file via bluetooth with the object push protocol
``` .. et voila, the system will spit out the names of every installed program that has something to do with this topic plus the "chapter" number this stuff has in the manuals. So let's assume that the program I was looking for is "dund" ... Having now its name I can lookup its manual:  ```
man 1 dund
``` ... The number is optional ... There are cases where a function call from the programmer's section might have the same name as a system command .. Example: ```
> apropos time
time (1)             - run programs and summarize system resource usage
time (7)             - overview of time
``` ... So via the number you tell the system which of those two manuals you want to read, e.g. **man 1 time** will explain the system command "time" to you, whereas **man 7 time** will explain the concept and principles of time measurement on Linux (which is interesting to read too!!) ...


**Armed with the "apropos" and "man" commands you can find out anything you want on your Linux system.** :)

---

