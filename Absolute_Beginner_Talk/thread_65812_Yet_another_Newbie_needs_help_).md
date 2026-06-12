---
title: "Yet another Newbie needs help :)"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by NZ-Wanderer on 2005-09-15
HI all, brand new to Linux, getting sick of all the rubbish associated with Windows, so decided to try Linux, and the word around is that Ubuntu is good for beginners :)

I downloaded and installed "Breezy Badger" as I like to have the latest.. - Everything went fine so it seems.

Got notified of updates, so I did the install of them (all 234 of them) but right at the end after it told me I could close the window (which I did) up popped the following error:

> Failure to run /usr/bin/update-manager as user root:
child terminated with 208 status
As I said above, all I have done is install Breezy, and done the update, I haven't even tried changing my resolution etc yet...

Apart from that, everything seems to be working fine...

I went into the Synaptic Package Manager to have a nose around typed in Nvidia in the search function and it said there was a 1.0.7667 I could install.. - However when I checked on the Nvidia site itself, it tells me there is a 1.0.7676..
Do I go with whats in the Package Manager or download the new one from Nvidia??

There was a couple of other questions I had, but I found the answers to them while nosing around through this great forum :) :)

Regards - John...

---

### Post by SilentCacophony on 2005-09-15
Hello. I'm fairly new to linux myself.

I've run across that error message when I didn't run apt-get as root. If you use apt-get, make sure to  use sudo before it to run it as root. Synaptic should prompt you for your password, as I recall, as does aptitude package manager, which is what I use.

Personally, I haven't had any problems with the packaged nvidia driver.

---

### Post by NZ-Wanderer on 2005-09-15
[QUOTE=SilentCacophony]Hello. I'm fairly new to linux myself.
I've run across that error message when I didn't run apt-get as root. If you use apt-get, make sure to  use sudo before it to run it as root. Synaptic should prompt you for your password, as I recall, as does aptitude package manager, which is what I use.
Personally, I haven't had any problems with the packaged nvidia driver.[/QUOTE]
 Thanks for the reply :)

not got as far as investigating apt-get yet - just clicked on the update icon on the bar up the top to get all the updates.

Will install the packaged driver and ignore the one on the Nvidia site for now them  - hehe here is where I get to type my very first command into the terminal after I use the package manager...

Crosses fingers :)

---------------------------------------

Update: well that was nice and painless.. - did the package manager, then the command prompt, then the reboot, and I get a huge Nvidia logo on startup now...
Just can't seem to find anywhere to set Nvidia settings (or don't they have such a thing in Ubuntu??)

---

### Post by SilentCacophony on 2005-09-15
Ah, I don't run with the default gnome desktop, so I don't have the update icon any more. You can check for updates in Synaptic package manager manually if the updater is giving you problems, though. Synaptic is installed by default.

---

### Post by hashimoto on 2005-09-15
Welcome! Hope you enjoy your new operating system. 

Please remember that Breezy is still in works, will have almost daily updates and may not function properly or might even break occasionally with the updates. Hope you have enough patience if that happens. Hoary, being stable, could have been a better choice...

---

### Post by NZ-Wanderer on 2005-09-15
Thanks for the welcome, you bunch seem real friendly around here, I just know I going to enjoy my visits...
Yup, I realised that Breezy was still in Beta, and it not due out officially till October, but I tend to like getting things soon as they are released (I do that with windows stuff) - I guess I am just a glutton for punishment, as I actually enjoy all the things that might and sometimes can go wrong, sorta keeps this old brain functioning good...
Soon as the Mailing CD thingie opens again I gonna request the official release, but thought I might as well get started trying to learn some things in the meantime...

Just nosing through the starter guide for the earlier version at the moment trying to figure out why I can't see any Nvidia settings to set and why the firewall I installed via the package Manager isn't showing up either... :)

Regards - John...

---

### Post by NZ-Wanderer on 2005-09-15
Well I followed the instructions in the starter guide for the earlier version, and after I rebooted I got my Nvidia Setup in the menu :) :)

Too late now, needs sleep, so tomorrow I gots to try to track down why the firewall not showing itself...

---

### Post by SilentCacophony on 2005-09-15
AFAIK, linux firewalls pretty much just edit iptables (which act as packet filters,) so I'm not sure you'd see anything from the firewall.

For info, try typing 'man name-of-firewall' in a terminal, substituting the name of the firewall as shown in the package manager, or just type the name in order to execute it.

You can add launchers to the top gnome bar for things which do not show up in the menus, which is a known problem with gnome right now.

---

