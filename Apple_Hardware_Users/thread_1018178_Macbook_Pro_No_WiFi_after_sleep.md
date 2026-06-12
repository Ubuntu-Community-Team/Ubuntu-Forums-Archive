---
title: "Macbook Pro: No WiFi after sleep"
date: 2008-12-21
forum: Apple Hardware Users
---

### Post by skullmunky on 2008-12-21
I have a Macbook Pro, running Kubuntu Intrepid i386.  After suspend/resume, the wifi stops working.  I figure I need to make some modules unload and then load - but which ones?  

I rmmod'ed and then modprobed these:

```

ath_pci wlan_ccmp wlan_scan_sta ath_rate_sample wlan ath_hal

```

---

### Post by cyberdork33 on 2008-12-22
Please use the "Before You Post" link in my signature to properly identify your Mac version.

---

### Post by skullmunky on 2008-12-26
MacBookPro1,1

---

### Post by Rog-Mahal on 2008-12-27
It looks like you're using the madwifi driver, I believe Intrepid comes with the newer ath9k driver installed, perhaps you want to uninstall madwifi and switch over?

As a more direct answer to your question, I've had a similar problem and found that removing and reloading ath_pci will control all the other modules.

---

### Post by cyberdork33 on 2008-12-28
> **Rog-Mahal said:**
> It looks like you're using the madwifi driver, I believe Intrepid comes with the newer ath9k driver installed, perhaps you want to uninstall madwifi and switch over?

As a more direct answer to your question, I've had a similar problem and found that removing and reloading ath_pci will control all the other modules.

since he has a 1,1 he might be using the ath5k, just a check to make...

---

### Post by skullmunky on 2008-12-30
thanks, ath_pci worked.  I did two things:

in /etc/pm/config.d, I added a file with this line:

```

SUSPEND_MODULES="ath_pci"

```

edited /etc/default/acpi-support, added it to the list of module to remove and reload during sleep: 

```

MODULES="ath_pci"

```

---

### Post by Link00seven on 2008-12-31
What do you title the file when you add the new file to those directories?

---

### Post by hyperboloid on 2008-12-31
> **Link00seven said:**
> What do you title the file when you add the new file to those directories?

In *nix terminology, references such as /etc/pm/config.d and /etc/default/acpi-support ARE file names. In *nix, it is common to provide the complete pathname to a file, that is what the poster in the previous post was doing. So you need to edit those files and add the indicated lines. You can use "sudo gedit <path/name>" from a terminal to make the edits. (Replace <path/name> with the actual pathname of the file you wish to edit.)

A *nix file system is a tree with / at the root. Each folder in / is a branch of the tree. One of the brnaches is /etc. In /etc is a subfolder named pm, and its pathname is /etc/pm. And so on. Every folder and file has a unique pathname. When running commands on a terminal, the full pathname is often used to refer to the file in question.

---

### Post by cyberdork33 on 2008-12-31
I think you can name the file what you like in /etc/pm/config.d/

---

### Post by skullmunky on 2009-01-02
Sorry, should have been more clear.  That's correct, you can call the file that's in /etc/pm/config.d anything you want.  Mine is called "10suspend_modules".

How did I come up with that name?  If you look in /etc/pm/config.d there should be one file already, called "00sleep_module".  If you read that file it says that it tells the system which sleeping system to use, which can be either "kernel", "uswsusp", or something called "tuxonice".  The default, "kernel", is working for me, so I left that alone.

The way the directory works is that the system reads all the configuration files in it, in order.  Starting my file with "10" as a prefix means it will get read after the one that starts with "00".  

There are a lot of configuration directories in Linux which work similarly; you can add and remove files to configure individual options instead of having to edit a single master configuration file, or registry, or what have you.  Often it doesn't matter at all what you call the files, but in this case the order can be important.

---

### Post by Link00seven on 2009-01-02
Thanks for clearing that up guys. I'm new to Ubuntu and trying to figure out how to get around and whatnot.

EDIT: I made the changes but they didn't seem to work (my wireless still doesnt work after suspend). I use the WICD manager (if that matters) and I'm on a Macbook Pro 3.1 (I just noticed above the original poster had 1.1 model). Any ideas?

---

### Post by fbugnon on 2009-02-17
Great!

I running Ubuntu 8.10 under a MacBook Pro 1,1 and was having the same problem to reconnect to a wireless network after coming back from sleep.

I followed skullmunky's instructions (Dec 30, 2008) and it works perfect now.

Just clearing up a bit in case someone's having trouble finding where to edit the second file he mentioned (/etc/default/acpi-support).  The part to edit should look like this (including the change):

[INDENT](...)
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES="ath_pci"
(...)
[/INDENT]

Cheers to all.

---

