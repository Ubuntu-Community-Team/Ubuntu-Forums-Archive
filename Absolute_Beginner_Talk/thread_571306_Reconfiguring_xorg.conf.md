---
title: "Reconfiguring xorg.conf"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Mad_Max_1412 on 2007-10-09
Guys,

I've been trying to install nvidia drivers without much luck,  basically getting a kernel mis-match error when rebooting.

Anyway, to resolve the issue, I'm following the suggestion in the xorg.conf file where it says to run the command:

sudo dpkg-reconfigure -phigh xserver-xorg

I noticed that when I did, the first question about my graphic card has a list of entries such as nv, nvidia etc but I've noticed either a black face, a white face or a 1/2 next to each entry.

What do these mean?

Regards

---

### Post by Joeb454 on 2007-10-09
I'm not sure what the things you're seeing are, but I can tell you that nv is the open-source driver, and nvidia is the proprietary driver for the gfx cards.

*Somebody correct me if I'm wrong :)*

---

### Post by overlord.gaurav on 2007-10-09
Why don't you simple try this:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
And for the driver part, personally I would suggest you to use "Envy".

---

### Post by Mad_Max_1412 on 2007-10-09
Many thanks. I used Envy and it was so much easier.

I just need to remember to uninstall the driver before upgrading to Ubuntu 7.10 when it comes out.

Cheers

---

