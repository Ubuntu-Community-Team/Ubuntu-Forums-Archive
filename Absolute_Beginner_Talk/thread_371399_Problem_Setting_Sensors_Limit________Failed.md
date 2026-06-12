---
title: "Problem: Setting Sensors Limit        Failed"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-26
I used Synaptic to install S**etting Sensors Limit**. It obvioulsy did not install correctly. I wonder what I forgot? Are there any dependencies that I may have missed? I installed "everything" that I could fine that had something to do with sensors that were listed immediatley below the main install file.

When I boot up I get the following message ***before*** entering the username and password to get into Linux:

**Setting Sensors Limit   **[COLOR=Red]*Failed*[/COLOR]

When I run "**sudo sensors-detec**t" in terminal I get the following:

kittyhawk63@kittyhawk63:~$ sudo sensors-detect
Password:
** No i2c device files found. Use prog/mkdev/mkdev.sh to create them**.
kittyhawk63@kittyhawk63:~$

Any suggestions on how I go about following terminal's advise to: Use** prog/mkdev/mkdev.sh **to create i2c devices? 
It seems clear that I need Terminal to locate i2c devices to have **Setting Sensors Limit** to function properly.

Thanks for any help you can give.
KH

---

