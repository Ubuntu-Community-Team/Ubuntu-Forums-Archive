---
title: "Refit question"
date: 2011-09-01
forum: Apple Hardware Users
---

### Post by rmcellig on 2011-09-01
I would like to disable startup from one of my external USB drives. This is what appears in my Refit config file. What exactly do I have to change in order for my Mac to either boot from my Linux or internal Mac partition? Both partitions reside on my internal iMac drive.



# Disable menu options for increased security. These are intended for a lab
# environment where the administrator doesn't want users to mess with the
# operating system. List the names for the options you want to hide from
# the boot menu. Currently supported:
#  shell       - remove the EFI shell
#  tools       - remove all EFI tools (shell and gptsync)
#  optical     - no booting from optical drives
#  external    - no booting from external disks or USB flash drives
#  internal    - no booting from internal disks; this setting is not
#                 recommended because it locks you out of all operating
#                 systems installed on the internal hard disks.
#  singleuser  - remove the submenu options to boot Mac OS X in single-user
#                 or verbose modes
#  hwtest      - remove the submenu option to run Apple Hardware Test
#  all         - all of the above, except for 'internal'
#
#disable external optical shell singleuser
#disable all

---

### Post by Opie Wick on 2011-09-01
Not having ever used Refit I am not exactly sure but, if you hold the [Option] key during the boot process, you will get a menu in which you can choose what media to boot off of. I believe that this is part of the EFI bootloader NOT Refit. The caveat here is that your Linux partition will be labeled "Windows" - don't worry it is really your Linux partition.
If that is not what you are looking for, than I think that a clearer explanation of your problem and desire is needed. Good luck!

---

### Post by rmcellig on 2011-09-01
Here is my issue in more detail. When I start up my iMac I see the Refit menu with the icons for Linux, My Mac (internal drive), as well as my external USB drive which also runs Mac OS as a cloned backup. If I restart my Mac without doing anything, it boots into the external D instead of the internal drive in my iMac.There has to be a way to comment out the refit config file so that refit does not boot from any external drives. I see that option in the config file I posted above but I am just not sure how to comment it out. Do I just have to remove the # mark?

---

### Post by linuxopjemac on 2011-09-01
I would add the line
```
external
```

---

