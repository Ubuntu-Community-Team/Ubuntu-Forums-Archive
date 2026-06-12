---
title: "Frozen at 'configuring apmd'"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by IainT on 2006-02-08
After my earlier trouble I burned a new cd which I have checked and it is valid, and the install has gone fine, until it told me to remove cd and reboot and then it tried to install further packages. It has frozen on 61% whilst trying to configure apmd.

I'm assuming that at this point I have an OS of sorts, and that I can make this work from here. Right? If I reboot will I get a command line and the option to try and continue the install from here?

Thanks in advance.

---

### Post by IainT on 2006-02-08
Apologies for responding to my own post.

Here is what I figure I am going to do - reinstall Ubuntu but with the server option. Stop me if I basically already have this, and installing the further packages is what makes the difference between desktop and server, and merely failing to install further packages basically means I have a server install.

Then I'll follow the instructions found here - [http://www.ubuntuforums.org/showpost.php?p=627578&postcount=17](http://www.ubuntuforums.org/showpost.php?p=627578&postcount=17)

---

### Post by IainT on 2006-02-08
Well, I attempted the following - sudo apt-get install ubuntu-desktop - it crashed.

Figuring now that it is the apmd program that is causing this I did my research and installed from the server install a very basic gnome set-up. This worked, and I was in. From there I have installed several more programs via the terminal, and then figured out what synaptic was for, and that made it a lot easier.

Although this is supposed to be easy, I figure I must have some sort of hardware conflict, and managed to get around it. Not to be too self-congratulatory, but I'd never used a terminal type thing before doing this, other than to ping websites that weren't working.

Next step is to get my wireless PCMCIA card back off a friend and try and install that. From there I may move over to XFCE.

---

### Post by Pragmatist on 2006-02-08
You might want to try: ```
apt-get update
``` and then ```
apt-get dist-upgrade
```  This way you should have a full system.  Then you might want to check your power settings in your BIOS relating to APM.  Then you could use synaptic or apt-get to insure you have whatever power-saving packages you need.

---

