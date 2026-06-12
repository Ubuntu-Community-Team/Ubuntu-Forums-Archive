---
title: "Ubuntu dumps to login screen when loading profile"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Wayren on 2007-04-05
Oh boy, do I have a good one for you all. I consider this a newbie-ish question, hence why it's in this forum. So my situation is this. When I try to login to Ubuntu, the OS boots to the login window just fine. However when I enter my credentials it starts to load, gets to the Gnome screen where it shows each of my startup items loading, then dumps to a black screen with a blinking cursor and then back to the login screen. Trying to boot into GNOME Failsafe gets me the same results. 

This all started after my computer was rebooted. On this machine I dual boot with Windows XP and Ubuntu 6.10. I was in Windows when it decided to lock up, Control - Alt - Delete failed me and I ended up powering the bloody thing off before booting back up into Ubuntu. Trouble is that I think Windows didn't successfully or completely unmount my /home partition. I have a partition set aside for my /home folder and load it into Windows using Ext-IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) in order to access my MP3s, documents, images, etc. in either OS. After the machine was powered back on and I started booting into Ubuntu I got the fsck screen stating a volume had not been unmounted successfully (I think). So it checked my /home partition which is /dev/sdb2 first off. And it failed "with exit code 1." It then checked my Linux partition and that passed OK. Booting into Windows I can see the files on the /home partition and access them (though can't copy them oddly enough) so I know everything is still there. 

I tried booting into the recovery console to run fsck but then realized I didn't know exactly what options to run it with. I unmounted the volume first off (I happened to notice that when i accidentally just typed "mount" it listed stuffage it had mounted and /dev/sdb2 had "error" in parenthesis.) and then tried just a fsck on /home but it said it was clean. I then ran it as fsck -f /home and it went through the 5 step process but the issue remained. So! Yeah. My apologies for this long post but I wanted to include as much info as possible. Any ideas?

---

### Post by Rashkae on 2007-04-05
> **Wayren said:**
> Oh boy, do I have a good one for you all. I consider this a newbie-ish question, hence why it's in this forum. So my situation is this. When I try to login to Ubuntu, the OS boots to the login window just fine. However when I enter my credentials it starts to load, gets to the Gnome screen where it shows each of my startup items loading, then dumps to a black screen with a blinking cursor and then back to the login screen. Trying to boot into GNOME Failsafe gets me the same results. 

This all started after my computer was rebooted. On this machine I dual boot with Windows XP and Ubuntu 6.10. I was in Windows when it decided to lock up, Control - Alt - Delete failed me and I ended up powering the bloody thing off before booting back up into Ubuntu. Trouble is that I think Windows didn't successfully or completely unmount my /home partition. I have a partition set aside for my /home folder and load it into Windows using Ext-IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) in order to access my MP3s, documents, images, etc. in either OS. After the machine was powered back on and I started booting into Ubuntu I got the fsck screen stating a volume had not been unmounted successfully (I think). So it checked my /home partition which is /dev/sdb2 first off. And it failed "with exit code 1." It then checked my Linux partition and that passed OK. Booting into Windows I can see the files on the /home partition and access them (though can't copy them oddly enough) so I know everything is still there. 

I tried booting into the recovery console to run fsck but then realized I didn't know exactly what options to run it with. I unmounted the volume first off (I happened to notice that when i accidentally just typed "mount" it listed stuffage it had mounted and /dev/sdb2 had "error" in parenthesis.) and then tried just a fsck on /home but it said it was clean. I then ran it as fsck -f /home and it went through the 5 step process but the issue remained. So! Yeah. My apologies for this long post but I wanted to include as much info as possible. Any ideas?

There are probably easier ways to go about this, but this is how I usualy deal with these pesky situations.  Boot as normal, but instead lf logging in with GDM, press CTL_Alt_F1 to switch to console.  Log in.  sudo killall gdm.  then run xinit to start X with just a command consle.  Now try gnome-session.  It should fail again, but hopefully will leave some more helpful error messages in the console.

Fixing your problem is probably a matter of finding a file in your ~/ that gnome is chocking on, like .ICE(something authority) and deleting it.  When you have it working again, reboot. (sudo reboot)

---

### Post by Wayren on 2007-04-06
> **Rashkae said:**
> There are probably easier ways to go about this, but this is how I usualy deal with these pesky situations.  Boot as normal, but instead lf logging in with GDM, press CTL_Alt_F1 to switch to console.  Log in.  sudo killall gdm.  then run xinit to start X with just a command consle.  Now try gnome-session.  It should fail again, but hopefully will leave some more helpful error messages in the console.

Fixing your problem is probably a matter of finding a file in your ~/ that gnome is chocking on, like .ICE(something authority) and deleting it.  When you have it working again, reboot. (sudo reboot)

On your advice I tried starting gnome-session as you mentioned. When I do this I get the following message in the terminal:

(gnome-panel:10862): libgnomevfs-WARNING **: Failed to open session DBUS connection: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

I'm not finding anything in my /home directory with a .ICE in the name. This issue appears to just be an issue with Gnome though because I remembered that I had KDE installed as well and decided to give it a shot. When selecting KDE as my session and logging in KDE loads fine and functions properly.

---

### Post by Rashkae on 2007-04-06
Try creating a new user and log in as that user.  That will at least tell you if your problem is in the home directory or something else in the system.. Unfortunately, I don't know how to correct the error you're getting.

---

### Post by Ocxic on 2007-04-06
are you using beryl???
I've noticed that everytime i try to launch beryl manager the same thing happens to me, I just get dumped backl to my login screen

---

### Post by Wayren on 2007-04-06
Gah, I can't believe I hadn't thought of that. Disabling start up programs that is. I think I'll try disabling Beryl and see what happens when I try to login.

---

### Post by Ocxic on 2007-04-06
now I'm getting a n error whenever i load beryl-manager, something about libc6.so

---

### Post by Ocxic on 2007-04-06
ok I just intsalled a bunch of update and now it's working again, it seems apt, and aptitude are fighting with eachither, everytuime I use atitude it removes a bunch of pacakges, and then beryl wont worl, but if i let upt update and install thos packages again everythiung works.

heres a list of the pacakges i installed to get going again:

libwxbase2.6-0 (2.6.3.2.1.5ubuntu0.1)
libwxgtk2.6-0 (2.6.3.2.1.5ubuntu0.1)
python-crypto (2.0.1+dfsg1-1.2build1)
python-twisted (2.4.0-2)
python-twisted-bin (2.4.0-2)
python-twisted-conch (1:0.7.0-1)
python-twisted-core (2.4.0-2)
python-twisted-lore (0.2.0-1)
python-twisted-mail (0.3.0-1)
python-twisted-names (0.3.0-1)
python-twisted-news (0.2.0-1)
python-twisted-runner (0.2.0-1build1)
python-twisted-web (0.6.0-1)
python-twisted-words (0.4.0-1)
python-wxgtk2.6 (2.6.3.2.1.5ubuntu0.1)
python-wxversion (2.6.3.2.1.5ubuntu0.1)
python-zopeinterface (3.2.2-0ubuntu1.1~proposed1)

---

### Post by Wayren on 2007-04-06
Woo! Found the answer. Appears there were similar issues going around. This worked for me:

[http://ubuntuforums.org/showpost.php?p=2413335&postcount=3](http://ubuntuforums.org/showpost.php?p=2413335&postcount=3)

---

