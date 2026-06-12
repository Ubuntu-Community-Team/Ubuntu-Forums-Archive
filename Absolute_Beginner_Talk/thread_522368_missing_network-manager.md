---
title: "missing network-manager"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by becominglumberg on 2007-08-10
So, last night, I decided that since I now use a wire for ethernet, I didn't want to have to see the network-manager icon in the system tray.

Due to some previous glasses of sangria, I used:

sudo apt-get remove network-manager

So now I have no access to the internet at all at home (at work right now), and don't know how to reinstall network manager the best way without a network connection. Any ideas?

---

### Post by Ek0nomik on 2007-08-10
> **becominglumberg said:**
> So, last night, I decided that since I now use a wire for ethernet, I didn't want to have to see the network-manager icon in the system tray.

Due to some previous glasses of sangria, I used:

sudo apt-get remove network-manager

So now I have no access to the internet at all at home (at work right now), and don't know how to reinstall network manager the best way without a network connection. Any ideas?

I am not positive, but network-manager is probably on the Ubuntu install disc.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Look for:  "You may also want to uncheck (or untick) the CD-ROM/DVD source".

You should be able to install it from the disc and be set.

If you don't want the icon in the panel, right click on it and hit 'Remove'.

---

### Post by Majorix on 2007-08-10
You didn't have to uninstall it... You could only remove it from the panel.

Anyways that package comes on the live cd as it is a part of the base system. Search for it among the .deb packages.

If not found, use the live cd and go to packages.ubuntu.com and from there find the .deb package. Then burn it to a cd or something and you can finally go back to your original system and install it using the cd.

Good luck.

---

### Post by becominglumberg on 2007-08-10
Okay, now i am really confused. Apparently, when I restarted (for the second time) everything is hunky dory. I don't know why in the world that would work, and it goes against everything I know about software, but I don't care. Thanks for your help guys!

---

