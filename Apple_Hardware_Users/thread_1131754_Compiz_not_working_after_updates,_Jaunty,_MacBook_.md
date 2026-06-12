---
title: "Compiz not working after updates, Jaunty, MacBook 4.1"
date: 2009-04-21
forum: Apple Hardware Users
---

### Post by Claritux on 2009-04-21
Compiz worked out of the box with Jaunty on my MacBook 4.1, but after installing the latest updates I can't get it to work.

Here's a terminal output:
```
***********:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
```

---

### Post by bludimnd on 2009-04-21
> **akshov said:**
> Compiz worked out of the box with Jaunty on my MacBook 4.1, but after installing the latest updates I can't get it to work.

Here's a terminal output:
```
***********:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
```

Same problem here with Macbook Air.

Just noticed it now. It says Desktop effects could not be enabled.

---

### Post by cyberdork33 on 2009-04-21
The PCIID of your graphics card is blacklisted (for some reason). I don't remember the config file, but this happened before to some people, and you can comment out the PCIID for your card in the appropriate file and get it to work again.

---

### Post by Claritux on 2009-04-21
I've temporary solved the problem by running
```
SKIP_CHECKS=yes compiz
```

A more permanent solution would be appreciated

---

### Post by cyberdork33 on 2009-04-21
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

### Post by bludimnd on 2009-04-22
> **cyberdork33 said:**
> [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)


Doesn't work.

I get this:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by bludimnd on 2009-04-22
> **bludimnd said:**
> Doesn't work.

I get this:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

Follow these instructions:

[http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php](http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php)

It will then work.

---

### Post by cyberdork33 on 2009-04-22
> **bludimnd said:**
> Doesn't work.
did you reboot?

Anyway, the other method you found is what I was referring to earlier.

---

### Post by Claritux on 2009-04-22
OK, I got it working by using the instructions on the site bludimnd referred to. :) Thank you guys!

---

### Post by bludimnd on 2009-04-22
> **cyberdork33 said:**
> did you reboot?

Anyway, the other method you found is what I was referring to earlier.

No I didn't reboot. Maybe that was it.

The commenting out is the permanent solution.

---

