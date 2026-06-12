---
title: "network manager and update icon disappear"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-10-23
i delete the network manager , update icon and something called notification area from my panel by careless. i have read these post [http://ubuntuforums.org/showthread.php?t=197834](http://ubuntuforums.org/showthread.php?t=197834) [http://ubuntuforums.org/showthread.php?t=454792](http://ubuntuforums.org/showthread.php?t=454792) [http://ubuntuforums.org/showthread.php?t=180945](http://ubuntuforums.org/showthread.php?t=180945) and tried their methods but still doesn't work. i can only find ''network monitor'' -- not '' network manager'' from the 'add-to-panel'' window. i re-added the notification area but ''network manager'' and ''update'' icon still don't appear.
also, my utorrent (with wine) disappears. i cannot remember how to make it again.
 here is my screenshot 
[[img]http://img3.freeimagehosting.net/uploads/59cd3a7f08.jpg[/img]](http://www.freeimagehosting.net/)

---

### Post by brk3 on 2007-10-23
To make network manager start you need to run 'nm-applet'. You can add it to system->preferences->seesions to make it start on boot.  
To reenable updates I think you need to do that in system->administration->software sources. 
Keep in mind the icon will only show when there are updates to install.

---

### Post by afeasfaerw23231233 on 2007-10-23
i get back the utorrent icon now

---

### Post by afeasfaerw23231233 on 2007-10-23
should it be like this ?
i also want to know what is that notification area means. it is just a usless ## like a seperator
[[img]http://img3.freeimagehosting.net/uploads/1cae3d5858.jpg[/img]](http://www.freeimagehosting.net/)

---

### Post by brk3 on 2007-10-23
exactly :)

---

### Post by afeasfaerw23231233 on 2007-10-23
but it still doesn't work. nothing has changed

---

### Post by afeasfaerw23231233 on 2007-10-23
Bumpbump

---

### Post by brk3 on 2007-10-23
have you logged out and logged in again?

---

### Post by afeasfaerw23231233 on 2007-10-23
not yet, currently it's upgrading to 7.10. i'll try it tomorrow and tell the result, thanks!

---

### Post by afeasfaerw23231233 on 2007-10-24
it works again, thanks!

---

### Post by aantn on 2007-11-15
I had the same problem and I solved it with:

```
sudo apt-get install update-notifier
```

update-notifier had gotten uninstalled when I removed notification-daemon.

---

