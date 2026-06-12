---
title: "Permission denied....but why?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by rikoshay on 2005-12-28
Hi, 

Linux newbie trying desperately to get wireless working on an Acer Aspire 5021WLMi with an onboard broadcom. I understand the problem is actually switching the card on and for this you require the use of the acer_acpi program by Mark Smith. Having downloaded the program and successfully compiled and installed it I get a "permission denied" error when trying to activate the wireless.

```
rik@lappy:~$ sudo modprobe acer_acpi
rik@lappy:~$ echo "enabled : 1" > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Permission denied
rik@lappy:~$ cd /proc/acpi/acer
rik@lappy:/proc/acpi/acer$ ls -l
total 0
-rw-r--r--  1 root root 0 2005-12-28 11:56 bluetooth
-rw-r--r--  1 root root 0 2005-12-28 11:56 mailled
-rw-r--r--  1 root root 0 2005-12-28 11:56 version
-rw-r--r--  1 root root 0 2005-12-28 11:56 wireless
rik@lappy:/proc/acpi/acer$


```

Can any kind person tell me where I'm going wrong?

Cheers:)

---

### Post by kaamos on 2005-12-28
you do not have write permission, only read. This should work:
```
sudo su
echo "enabled : 1" > /proc/acpi/acer/wireless
exit
```

You can lean how to read the "-rw-r--r--" parts from here [https://wiki.ubuntu.com/FilePermissions](https://wiki.ubuntu.com/FilePermissions)

Hope this helps. :)

---

### Post by rikoshay on 2005-12-28
Writing this over my wireless connection! Thank you kaamos and thank you Mark Smith!:D 

Now if I can just work out how to get WPA-PSK working and load the wireless on startup....

Cheers.

---

