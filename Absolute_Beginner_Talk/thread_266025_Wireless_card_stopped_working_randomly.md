---
title: "Wireless card stopped working randomly?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-09-26
I have had a my wireless setup for my laptop for some while now, but for some reason something odd has occurred. When I turn on my laptop, the wireless card would automatically be started + detected, and I knew this because the led would light up. For some reason, it doesn't automatically start anymore. I am forced to run sudo modprobe ndiswrapper, then go into network tools and set up the wlan0 all over each time I turn on my laptop.

How can I fix this?

I believe it may have been from running packet sniffers. If you need me to list all the ones I downloaded and attempted to run, let me know.

---

### Post by dmizer on 2006-09-26
sounds like a kernel update or something wiped out your previous configurations.  you'll probably just need to add ndiswrapper to your /etc/modules again.
```
sudo echo ndiswrapper >> /etc/modules
```

it could also be that an update added a kernel module that's attaching itself to your card instead of ndiswrapper.  if that's the case, you'll probably have to blacklist that.

take a look at dmesg and see if there are any errors or hints there.

---

