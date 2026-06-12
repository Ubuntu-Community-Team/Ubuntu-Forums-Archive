---
title: "Display problems"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Necis on 2008-03-14
I'm pretty new to Linux, I read up on it, and looked at some pictures of the OS and thought it looked pretty good, I gave it a whirl on the LiveCD, than I decided to Install it. I installed Ubuntu, I had no problems, I logged in and than I download the ATI drivers by going to System-Administration-Restricted Drivers Manager. Now when I start my computer up and gets passed the normal bios stuff, my monitor says, "Mode Not Supported":(. I would really like to use Ubuntu, so any help would be greatly appreciated :)

---

### Post by smurphy_it on 2008-03-14
The modeline is not listed in your xorg.conf file.  This you are going to need I'd say for your specific type of monitor.

You are probably going to have to reconfigure your video driver to the defaults, then start configuring it again.

Easiest way.  Jump into a terminal and type:

sudo /etc/init.d/./gdm stop

Then Hit Ctrl-Alt-F1 Or Ctrl-Alt-F2

Login and type sudo dpkg-reconfigure xserver-xorg

Then type sudo /etc/init.d/./gdm start

You may have to hit Ctrl-ALt-F7 to get back into X-Windows.

---

### Post by freebios on 2008-03-14
you can try the dvd iso build it may have a different driver version.  it's one of the links ont the bottom of the download page options list, give it a shot and use the 32 bit installer, you'll have more luck.

---

