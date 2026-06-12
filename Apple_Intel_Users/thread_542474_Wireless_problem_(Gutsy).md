---
title: "Wireless problem (Gutsy)"
date: 2007-09-04
forum: Apple Intel Users
---

### Post by kmldqj on 2007-09-04
I just installed Gutsy (and updated to most recent packages) today on my MacBook Pro C2D (old C2D, not the Santa Rosa version). I installed MadWifi from the subversion repository. nm-applet was able to list all the available networks, but I cannot connect to my network (with WPA2-Personal encryption). I thought maybe WPA2 isn't supported, so I disabled all encryption and passwords, and it still didn't work. 

At this point I think maybe nm-applet is broken, so I tried to use System >> Administration >> Network in the Gnome menu to configure wireless. From the output of "iwconfig" it seemed ath0 was able to associate with the access point, but it wasn't able to obtain a correct IP address via HDCP, Another interesting thing is that after I did this, 2 new interfaces show up in "ifconfig": ath0:avah and wifi0 (before this there were only eth0 and ath0). 

Any help is appreciated. I would love to use Ubuntu on my laptop, but wireless access is essential to my work. Thanks!

---

### Post by ThufirHawat on 2007-09-04
I was also considering installing Gutsy, as Feisty is obviously unable to deal with WPA2 on a MacBook Pro [I know, I have tried every weird "recipe" without success], but if what the previous poster writes is not due to some  procedural mistake, then Gutsy does not offer any solution either, at least not so far.
I am therefore very interested to possible replies to this post.

Cheers,

Thufir Hawat

---

### Post by benanzo on 2007-09-04
This must be a problem with the wireless chipset in the new MacBook or Pros, because I've been running Gutsy on my first-gen MacBook since Tribe 2 without any wireless problems.  I've just been using the Madwifi version shipped in linux-restricted-modules.  I've experienced no problems with NetworkManager or nm-applet.  This includes full WPA2 support.  Also, the difference with ath0 and wifi0 is that (to my knowledge) wifi0 is the low-level interface that sends/receives packets and ath0 is what NetworkManager interacts with for IP/config issues.  Normally the user shouldn't interact with wifi0 at all.  ath:avah is the interface that Madwifi uses to interact with avahi/bonjour devices on the network.  I've not had a chance to test it, but it's neat that it's there by default now.

---

### Post by ThufirHawat on 2007-09-04
To Benanzo:

I am glad your MacBook can do WPA2.
Actually mine is also, I believe, a first generation MacBook -Pro- 15", with Core 2 Duo (one of the dumbest terminology for CPUs I ever saw, as Core 2 Duo processors are not the same as Core Duo) CPUs at 2.33 GHz and Atheros wireless chips.
So it is not the Santa Rosa, or whatever it is called the new MBP.
I am in the same hardware situation as the first poster.

---

### Post by kmldqj on 2007-09-04
> **benanzo said:**
> This must be a problem with the wireless chipset in the new MacBook or Pros, because I've been running Gutsy on my first-gen MacBook since Tribe 2 without any wireless problems.  I've just been using the Madwifi version shipped in linux-restricted-modules.  I've experienced no problems with NetworkManager or nm-applet.  This includes full WPA2 support.  Also, the difference with ath0 and wifi0 is that (to my knowledge) wifi0 is the low-level interface that sends/receives packets and ath0 is what NetworkManager interacts with for IP/config issues.  Normally the user shouldn't interact with wifi0 at all.  ath:avah is the interface that Madwifi uses to interact with avahi/bonjour devices on the network.  I've not had a chance to test it, but it's neat that it's there by default now.

Thanks for the information. By "first-gen MacBook" I am assuming that yours is Core Duo instead of Core 2 Duo?

---

