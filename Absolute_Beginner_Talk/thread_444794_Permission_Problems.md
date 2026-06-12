---
title: "Permission Problems"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-05-15
For some reason I can't use this command ```
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev
```

Because of this error; ```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Any suggestions ?

---

### Post by sisco311 on 2007-05-15
```
sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev
```

---

### Post by tarchy on 2007-05-15
: Couldn't find package x-window-system-dev

---

### Post by tarchy on 2007-05-15
Shitttt...whats wrong with my OS :P

---

### Post by Bachstelze on 2007-05-15
Try xorg-dev instead.

---

### Post by tarchy on 2007-05-15
Since it could not find the windows dev thing, I deleted it from the command line and it's installing now..

---

### Post by Bachstelze on 2007-05-15
Yes but if it was there, that's probably because you need it...

---

### Post by tarchy on 2007-05-15
Same error with xorg-dev

---

### Post by rich.bradshaw on 2007-05-15
what are you trying to compile?

---

### Post by tarchy on 2007-05-15
Yeah, I'd say so o_o.

I guess I will try continue with the instalation and see what happens.

How do I do this?

Change to the location where the WineCVS.sh is lying and start it with:

sh WineCVS.sh

---

### Post by tarchy on 2007-05-15
> **rich.bradshaw said:**
> what are you trying to compile?

Honestly I have no idea.

---

### Post by tarchy on 2007-05-15
Whilst trying to install Steam; ```
tarchy@tarchy-desktop:~$ wine msiexec /i SteamInstall.msi
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!

```

---

### Post by sgtbob on 2007-05-17
I downloaded a tar file into my Ubuntu 6.06 system and was able to open and use it.  I then decided I no longer wanted the file, so moved it to Trash.  I tried to remove a similar item by uninstalling it in synaptic and that worked OK, but the following is an issue I am unable to resolve.

When I try to 'delete from trash', I get a permissions error that I am not the owner.  In clicking on properties, I do see that it belongs to 'root'. So, how does one get to be root so I can change the permissions and allow me to delete it from the trash? Do I move the file back to a folder and then do the synaptic uninstall?:confused:

Bob

---

