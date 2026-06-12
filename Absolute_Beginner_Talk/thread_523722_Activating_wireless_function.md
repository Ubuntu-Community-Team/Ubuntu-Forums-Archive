---
title: "Activating wireless function"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by kvmusic on 2007-08-12
I recently tried Freespire and it connected flawlessly to my old Motorola Notebook Adapter - WN825G on my old HP Pavilion ze4125.

My main machine is a 2006 iBook... and my HP is something I would like to have Ubuntu on it.

Once again... I tried Freespire, but I feel that Ubuntu is a much more solid OS it seems, so I loaded it onto my HP last night.  Sadly... the wireless set up isn't as easy as Freespire.

I've opened the Network and I've noticed that the "wireless" function isn't "checked" like the "Wired Connection" tab is.

Btw... I just fired up Ubuntu and I noticed that the "wireless" tab is now gone in the Newtwork Settings area.  Bummer...

2 things...

How do I activate the 'wireless" function and then connect wirelessly?

Secondly... how do I get my 'wireless properties' back into my Network Settings?

I'm a 100% noob... please keep that in mind.  THANK YOU kindly in advance for your help and assistance!

---

### Post by designwiz on 2007-08-12
hmm i had a tough timeusing the gnome-network-manager too... its kinda sucks for wireless interface.. you can try an alternative called wicd.. (works flawlessly for me)

Making sure your wireless network is on..

Step1. 
Download the latest .deb file.> [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) If you are running Feisty Fawn, you’ll have to remove network-manager - you can do this from Synaptic, or from the terminal by running>  “sudo aptitude remove network-manager”. With either option, the network-manager-gnome package should get removed automatically as well. Then just double click the .deb you downloaded

Step2
After installation, run the wicd from Applications-->Internet-->Wicd

Step3
You should be able to connect 2 wifi.. press referesh to rescan..also do have a look at prefernces tab

To run it
Hit alt-F2 and type in “/opt/wicd/gui.py”. This is the main window, where you can adjust settings and connect to networks. It should also appear under Applications > Internet > Wicd in GNOME.

How can I get the tray icon to appear?

Hit alt-F2, and run “/opt/wicd/tray-edgy.py” (or /opt/wicd/tray.py if you’re using 1.3.0 or later). In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the “Startup Programs” tab, click the “New” button. Give it a name (”Wicd” works fine). For a command, enter “/opt/wicd/tray-edgy.py”. In KDE, run the following command from a terminal: “sudo ln -s /opt/wicd/tray-edgy.py ~/.kde/Autostart/tray-edgy.py”. Under either desktop environment, you can open the main window by right clicking the tray icon and choosing “Connect...” (or simply by left-clicking it if you are running version 1.2.8 or later).

Why doesn't my WEP key work?

Sometimes this can be fixed by putting quotation marks " " around the key, inside the text box.
How do I get Wicd to recognize my wireless card?

In the main window, click the “Preferences” window. Make sure your card is listed beside “Wireless Interface”. Some common values are wlan0 and eth1. You can adjust your WPA settings here as well.
How do I connect to a network?

Open the main window. Click on the word “Connect” underneath the name network you wish to connect to. For further options, click on the name. You’ll now see a check box to “Automatically connect to this network” as well as some information about the network. Clicking on “Advanced options” will allow you to set a static IP address/DNS and a password (if the network is encrypted).

For more info on Wicd visit
> [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

Hope this helps
Peace Out \\//

---

### Post by MenZa on 2007-08-12
Right, as far as I can read, it seems that you have not run Freespire, Ubuntu or any Linux/NIX OS on your HP before? Can you confirm this? If this is the case, you may have to install drivers, which can be a complicated process if you're new to Ubuntu (but that's why we're here!).

---

### Post by kvmusic on 2007-08-12
Good info... thanks guys!!!

On Freespire... YES, I installed it once, but wanted Ubuntu because the Community here is solid and the OS seems very stable.

More info from me later on...

THANKS SO MUCH...

---

### Post by designwiz on 2007-08-12
No Probs.. Good Luck with Ubuntu!

---

### Post by kvmusic on 2007-08-12
I'm on the road right now... I'll be home this evening to download drivers, etc.

If my wireless won't work with the Motorola card... I'll look into getting a different card.  AND... I'm sure I'll return to the forum.  Well... either way, I'll let you all know how things turn out!

This is great that you guys have made a 'noob' forum available... it's making a difference.  Kudos to the Ubuntu Team & Community!!!

---

### Post by MenZa on 2007-08-12
> **kvmusic said:**
> This is great that you guys have made a 'noob' forum available... it's making a difference.  Kudos to the Ubuntu Team & Community!!!

Converting from Windows/OS X to Linux can be quite a difficult barrier to overcome, and even the ones of us who seem like we know everything about Linux have gone through the same process of learning, step by step.

---

### Post by leadpan on 2007-08-12
Wow Wicd kicks ****!  :)
After trying hundreds of linux wireless tools, Wicd was the easiest and quickest wifi tool to use!  I hope there will be a Wicd for KDE soon.

---

### Post by kvmusic on 2007-08-12
If it's ok the ask... what is a Wicd?

---

### Post by imdano on 2007-08-12
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

It's an alternative to NetworkManager, which is the default network management program in Ubuntu.  You should probably worry about making sure your driver situation is more or less squared away before trying to switch, though.  I *think* your card uses a Broadcom chipset.  Whats the output of the following terminal commands? ```
sudo lshw -C network
lspci -nn
```

---

### Post by kvmusic on 2007-08-12
Okie dokie... I've been able to reconnect (just got home) with the discussion here and I'll start to follow the instructions from designwiz.

Wish me luck :)

---

### Post by MenZa on 2007-08-13
> **imdano said:**
> [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

It's an alternative to NetworkManager, which is the default network management program in Ubuntu.  You should probably worry about making sure your driver situation is more or less squared away before trying to switch, though.  I *think* your card uses a Broadcom chipset.  Whats the output of the following terminal commands? ```
sudo lshw -C network
lspci -nn
```

Ooh, pretty---I need to try that on my laptop once I decide to boot that up!

---

