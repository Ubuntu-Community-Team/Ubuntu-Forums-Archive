---
title: "I made a boneheaded noobie mistake"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by el_poderoso on 2007-08-24
I was trying to fix a synaptic touchpad that stopped working on my laptop by editing my /etc/x11/xorg.conf file and I added one line I shouldn't have.

  I know what I have to edit out, but when I try to boot the machine, I get an ugly blue screen of death letting me know that my x-server, ain't gonna be serving nothing.

Is there anyway I can get to the /etc/x11/xorg.conf file and edit out the offensive text? HELP!!

---

### Post by Qrk on 2007-08-24
Press <ctrl><alt>F1 (or anything not F7 I believe), you should be able to log in with your username and password.

From there, you can edit your xorg.conf file with:

```
sudo nano /etc/X11/xorg.conf
```

and remove the offending line.

---

### Post by HermanAB on 2007-08-24
Hmm, and once you have it working, make a backup of the /etc directory:
$ sudo tar -zcvf /root/etc.tgz /etc

To my mind a good distribution should do that for you at the end of the install process!

Cheers,

Herman

---

### Post by bigfox on 2007-08-24
If all else fails and you are unable to fix the xorg.conf file you can try this.

sudo dpkg-reconfigure -phigh xserver-xorg

That reverts the xorg.conf to a default state.

Then reboot.

After that, you can reload you graphics driver in the Restricted Driver Manager.

(Note, this method also seams to work when you change your video card and need to change the driver)

---

### Post by el_poderoso on 2007-08-24
Thank you for your help. I fixed this in a very creative way. I had a distro of Freespire. I loaded it as a live desktop and edited the file in the live CD version of freespire.

Crazy. Your solutions were better, but this worked.

---

### Post by Felix21685 on 2007-08-24
> **el_poderoso said:**
> Thank you for your help. I fixed this in a very creative way. I had a distro of Freespire. I loaded it as a live desktop and edited the file in the live CD version of freespire.

Crazy. Your solutions were better, but this worked.

wouldn't a ubuntu live cd done the same thing?
just wondering.

---

