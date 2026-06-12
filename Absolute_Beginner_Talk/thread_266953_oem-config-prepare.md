---
title: "oem-config-prepare"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-28
can someone tel me what this line actually does?

oem-config-prepare

i cant find anything on google.
after i installed it told me to run this line when i was happy with the configuration.
i have done it and it says somethng about the next startup.

im hoping it does something to the tempory oem user.
this user cant write to the file system and im desperate to so i can install things from there.

if this has nothing to do with removing this problem can someone please tell me how to create a new user with full privilages.
last time i deleted oem and made a new user i got to the login screen and it told me the new user had nothing in or on the home file.
i couldnt log on at all and had to reinstall.

someone plz help coz this is the third time iv asked.
once on another forum though

---

### Post by Average Joe on 2006-09-28
Apparently you have chosen the OEM (Original Equipment Manufacturer) install when you installed Ubuntu from the CD. I think this install is actually meant for computers that are to be sold with Ubuntu pre-installed on it.

This installation creates the account 'oem', and is obsolete once you have created your own account. So you probably got a message saying:

"Once the system is configured to your satisfaction, run 'sudo oem-config-prepare'. This will cause the system to delete the temporary 'oem' user and ask the end user various configuration questions the next time it boots."

So the 'oem-config-prepare' command just removes the 'oem' account that you probably don't need anymore anyway.

I am not sure what administrative rights the 'oem' account has though. It seems to me that with this account it should be possible to create a new account. Are you sure you tried 'sudo' before doing anything that requires administrative rights?

Hope this helps.

---

