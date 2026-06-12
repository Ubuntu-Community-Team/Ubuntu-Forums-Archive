---
title: "Flash in Ubuntu"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by BlueEight on 2007-10-30
I tried to install flash using the tutorial from "http://www.psychocats.net/ubuntu/flash" but in the middle of it, my computer froze, so I restarted it. Now, when I go to the web page to reinstall flash, it now says, "package flash non-free is already installed restart firefox to complete" I restart firefox, but when I go back to the web page, the same thing happens. Does anyone know how fix that?

---

### Post by Maestro23 on 2007-10-30
Have you tried to completely remove the plugin and install it again?

---

### Post by BlueEight on 2007-10-30
How do I remove it? I thought about doing that, but I didn't know how since I'm new with ubuntu.

---

### Post by Six_Digits on 2007-10-30
BTW, Maestro23, is flash in any repositories or synaptic? He would have to uninstall through firefox, right?

---

### Post by BlueEight on 2007-10-30
How would I uninstall it through firefox?

---

### Post by FXEF on 2007-10-30
> **BlueEight said:**
> How would I uninstall it through firefox?

In Firefox click Tools > Extensions. Then un-install from there.

---

### Post by BlueEight on 2007-10-30
Under tools, there's only web search, downloads, add-ons, error console, page info, and clear private data. I checked all of them, and none had Flash in it.

---

### Post by FXEF on 2007-10-30
> **BlueEight said:**
> Under tools, there's only web search, downloads, add-ons, error console, page info, and clear private data. I checked all of them, and none had Flash in it.

I think you might have a later version than I have. Click add-ons.

---

### Post by BlueEight on 2007-10-30
I did, the only thing there is "ubufox," the "firefox theme" and the "english pack"

---

### Post by Maestro23 on 2007-10-30
> **Six_Digits said:**
> BTW, Maestro23, is flash in any repositories or synaptic? He would have to uninstall through firefox, right?

Yeah, its in the Repositories.

> Synaptic: Search for flashplugin-nonfree, mark for install and apply.

Command line: sudo apt-get install flashplugin-nonfree


---

### Post by BlueEight on 2007-10-30
So, I typed in "sudo apt-get install flashplugin-nonfree" and I got "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

---

### Post by Maestro23 on 2007-10-30
> **BlueEight said:**
> So, I typed in "sudo apt-get install flashplugin-nonfree" and I got "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

Must be from your failed attempt earlier at installing the plugin.  In terminal try:

> sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade

---

### Post by BlueEight on 2007-11-01
Well, I did "sudo dpkg --configure -a" but the connection keeps timing out. I've tried it multiple times.
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--09:50:20--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 1.0.0.0
Connecting to fpdownload.macromedia.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.
Edit: Finally, after 8 retrys, I got:
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 flashplugin-nonfree

---

### Post by greg963 on 2007-11-01
try sudo apt-get install -f instead of dpkg-configure -a

---

### Post by BlueEight on 2007-11-01
I got :
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Maestro23 on 2007-11-01
> **BlueEight said:**
> I got :
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Try: **sudo rm -f /var/lib/dpkg/lock**

---

### Post by BlueEight on 2007-11-01
Ok, I did that, then put in "sudo apt-get install -f"
The response was:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  airstrike-common fgfs-base simgear0 plib1.8.4c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by BlueEight on 2007-11-01
Does anyone know how to uninstall the flash player that I have?

---

### Post by mike102282 on 2007-11-01
Go to add/remove select it and unckeck the box??

---

### Post by greg963 on 2007-11-01
if you restarted in the middle of the install you likely didn't complete the install

did you try
sudo apt-get install flashplugin-nonfree

again after removing the dpkg pid file?

---

### Post by BlueEight on 2007-11-01
O_o I feel infinitely retarded.

---

### Post by greg963 on 2007-11-01
So did you get it working?

---

### Post by BlueEight on 2007-11-01
No, actucally. I "successfully" installed it, then restarted firefox and it still said that I needed to install Adobe flash player. I clicked install and it said "flashplugin-nonfree" already installed.

---

