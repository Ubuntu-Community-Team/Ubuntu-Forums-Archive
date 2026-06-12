---
title: "TiPB-400: LiveCD will not start installer"
date: 2007-10-20
forum: Apple PPC Users
---

### Post by Dale1990 on 2007-10-20
I've tried to use the Ubuntu Desktop, Ubuntu Server, Xubuntu Desktop and now the Ubuntu alternate CD with no success. 

When holding down the C key I get to the yaboot menu (I think that's what it is). I've tried the default install, expert, cli and check.  None work. The cli and check display a log of sorts. The last line is "adb: starting probe task...". It never moves from here. The log also mentions using an unsupported resolution 1152x768, if that matters.

Any ideas? I managed to switch my old G3-400 iMac over to Ubuntu a few days ago with no real drama. This PowerBook is not happy about this.

Help, please.

---

### Post by ubuntubrian on 2007-10-20
The latest version that I can get to boot is Feisty as a live CD. I run Dapper and it works fine. Apparently there are lots of kernel issues with Gutsy and PPC so I'd advise trying Dapperuntil the bugs get worked out.

---

### Post by Dale1990 on 2007-10-20
I forgot to mention that I was using Feisty. I'm not an early adopter :)

I can try going down to Dapper... maybe that'll work. This machine is going to be nothing more than a glorified LAMP server anyway.

---

### Post by Dale1990 on 2007-10-20
UPDATE

I tried using the Dapper alternate CD and I get the same problem. The startup gets to "adb: starting probe task..." then dies.

Any ideas? I really want this thing to work.

---

### Post by Dale1990 on 2007-10-22
It just hit me that the ADB it is referring to is probably the built-in keyboard and track pad - yeah, I can be that slow :). Only problem is that neither of these work (thanks to my cat). I have to use USB for the keyboard/mouse. 

Could it be that because the trackpad/keyboard is messed up, the module is hanging up? How would I change the startup to get rid of that step?

Thanks!

---

### Post by Dale1990 on 2007-10-23
Are there any flags I can use at the boot prompt to keep the ADB module from loading?

Please help. I really want to get this old laptop back into service.

Thanks!

---

### Post by Dale1990 on 2007-11-17
I'm back again.

Anybody have any idea how to get this thing working?

I tried to install Xubuntu to the laptop in Firewire Target mode from my iMac. Everything worked except yaboot could not be installed. 

I tried booting the TiPB from the LiveCD as a rescue install and it failed in the same place.

---

### Post by Dale1990 on 2007-11-17
And, I'm going to try Fedora - maybe its LiveCD will work.

---

### Post by Dale1990 on 2007-11-17
I copied the boot strap partition from my working iMacG3 over to the TiPB in Taget Disk mode and it will try to start by itself but dies at a black screen in the same place the LiveCD does - no on-screen log however.

---

### Post by kugn on 2007-11-17
I followed the fix here and it's worked for me since
[http://ubuntuforums.org/showpost.php?p=3614279&postcount=58](http://ubuntuforums.org/showpost.php?p=3614279&postcount=58)

---

### Post by Dale1990 on 2007-11-18
The LiveCD I am using (Xubuntu Dapper) does not have a live-nosplash option. I'll try downloading Gutsy so I can try this but I am not hopeful.

This machine also won't boot from a DVD so Fedora is out the window.

:(

I am not happy.

---

