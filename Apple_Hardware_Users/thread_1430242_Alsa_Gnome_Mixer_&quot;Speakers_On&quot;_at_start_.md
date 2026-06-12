---
title: "Alsa Gnome Mixer &quot;Speakers On&quot; at start up (How to) ??"
date: 2010-03-15
forum: Apple Hardware Users
---

### Post by RVB Pïxels on 2010-03-15
Hi,
How can I force "Speakers On" in alsa gnome mixer at start-up ?
Every time I must open alsa mixer to check the box.

Also, is there a way to do the same with Powermac tumbler, because often it doesn't load and I get Keylargo instead and no sound at all, without the possibility to check the boxes for the speakers (they stay blank)

By-the-way I'm very new to all this using Ubuntu 9.10 on Mac. However, long time Mac user, 12 years or so...
I maybe havn't given enough info so please tell what is needed and how to go about getting it.

Regards,
RVB Pixels

---

### Post by linuxopjemac on 2010-03-15
Try this one:

```
sudo alsactl store
```

[http://alsa.opensrc.org/index.php/Using_alsactl_to_preserve_volume_state](http://alsa.opensrc.org/index.php/Using_alsactl_to_preserve_volume_state)

---

### Post by RVB Pïxels on 2010-03-15
> **linuxopjemac said:**
> Try this one:

```
sudo alsactl store
```[http://alsa.opensrc.org/index.php/Using_alsactl_to_preserve_volume_state](http://alsa.opensrc.org/index.php/Using_alsactl_to_preserve_volume_state)


Tried it but I don't even get asked for my password !!
I don't seem to have "*alsactl* installed in [I]/usr/bin"
[/I]Also, I'm afraid to try what they mention on the link you gave as I'm not sure which driver is being used as sometimes it loads and somtimes not.
[I]

Regards,
RVB Pixels
[/I]

---

### Post by linuxopjemac on 2010-03-15
alsactl is in alsa-utils
```

sudo apt-get install alsa-utils
```

---

