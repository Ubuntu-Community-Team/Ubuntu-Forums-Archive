---
title: "Setting Up My Hardware in Ubuntu"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Dalai Calama on 2006-06-29
Well, I've been left feeling completely out of my depth. :P

First, and greatest problem, is the wireless network card. The Device Manager seems to detect it, but I can't connect to the internet, and the information in the network tools are blank, as in the screen shots below:

[img]http://img350.imageshack.us/img350/842/screenshot7cp.png[/img]
The loopback interface, whatever that may be. :P

[img]http://img331.imageshack.us/img331/7346/wirelessinterface9fr.png[/img]
The Wireless Interface, complete with no information.

For what it's worth, the Wireless Card is a D-Link DWL-520+, that I know works, as it is what I'm on the internet now, on Windows, and it is listed on the Wiki as "Just Works". Except it doesn't seem to have done.

EDIT: I've removed the other problems, as the wireless one is the most urgent, and it'll be a lot easier to fix the other troubles after I can connect to the internet. Right now, I have to try and memorise the commands, or copy paste them into a text file, log out, log in to ubuntu, try them, log out, log back in to windows, look for more help. Not fun :P

---

### Post by Scunizi on 2006-06-30
For your wireless card check [http://ubuntuforums.org/showthread.php?t=158720&highlight=520](http://ubuntuforums.org/showthread.php?t=158720&highlight=520) & [http://ubuntuforums.org/showthread.php?t=130084&highlight=520](http://ubuntuforums.org/showthread.php?t=130084&highlight=520) & [http://ubuntuforums.org/showthread.php?t=109375&highlight=520](http://ubuntuforums.org/showthread.php?t=109375&highlight=520) they may lead you in the right direction.

As for your Video drivers... The easiest way is to install the drivers in Synaptic then comment out with a "#" the DRI line in /etc/X11/xorg.conf.  You'll have to use this to edit it "sudo gedit /etc/X11/xorg.cong" and then look for the DRI line and preface it with "#" (without the quotes of course).  

I'll leave the rest for someone more experienced.

---

### Post by Dalai Calama on 2006-06-30
[quote=Sunizi]As for your Video drivers... The easiest way is to install the drivers in Synaptic then comment out with a "#" the DRI line in /etc/X11/xorg.conf. You'll have to use this to edit it "sudo gedit /etc/X11/xorg.cong" and then look for the DRI line and preface it with "#" (without the quotes of course).[/quote]

Gah what? :P

Me no understand :P

---

### Post by angkor on 2006-06-30
[QUOTE=Dalai Calama]Gah what? :P

Me no understand :P[/QUOTE]

The nvidia drivers for your graphics card are available in the repositories.

See this howto to enable the ones you need.

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

After you've enabled the repositories, open up a terminal and copy paste these two commands:

```
sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx
```

If these two packages are installed you can enable the nvidia driver with:

```
sudo nvidia-glx-config enable
```

All you need to do after that is log out and log in again.

You can see if the driver is working with:

```
glxinfo | grep direct
```

The output should be: direct rendering: Yes

---

### Post by Dalai Calama on 2006-06-30
Well, I feel slightly stupid, as I realised I had not even looked at Networking, only Network Tools, and there I could set up my network details.

However, it still doesn't work.

It seems to connect to the network, and says that it has sent, and recieved a very small amount of data (14 KiB, and 8 B, respectively). But I still can't connect to the internet.

---

