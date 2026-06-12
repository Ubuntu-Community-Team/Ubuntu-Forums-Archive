---
title: "How do I load a needed kernel module?"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by K0LO on 2006-03-20
I'm trying to get WPA-Personal encryption working on my wireless card. I am able to get it to work using WPA-PSK with TKIP. However, I've been unable to get AES encryption to work.

The kernel module needed is ieee80211_crypt_ccmp and I can find the executable driver on my system.

If I do an lsmod command, I can see that the iee80211_crypt_tkip module is loaded, but the ieee80211_crypt_ccmp is not.

What controls the loading of kernel modules and how can I get the one I need to load?

Mark

---

### Post by Kurt` on 2006-03-20
I know you can use the `modprobe` command to load modules.

Maybe giving `man modprobe` a look will help you. That's all I can offer you though.

---

### Post by cilynx on 2006-03-20
```

modprobe module_name

```
or
```

insmod /path/to/module/file

```
to remove:
```

rmmod module_name

```

---

### Post by az on 2006-03-20
[QUOTE=K0LO]
What controls the loading of kernel modules and how can I get the one I need to load?

Mark[/QUOTE]
Discover and hotplug autodetect and load modules when you boot.  Hotplug monitors system messages and loads modules accordingly.  In Dapper, HAL (hardware abstraction layer) and Udev take care of that.

If the modules needs to be loaded and is not loaded, it is a bug.  Are you able to try it on Dapper?  If so, and if it still doesn't work, a bug report would be excellent!

If you file the bug for breezy, it probably won't get fixed because everything is being poured into Dapper.

---

### Post by K0LO on 2006-03-21
Thanks, guys, for your prompt responses. Even though I didn't make my question clear enough, you hit the nail on the head Azz.

I can load the module ieee80211_crypt_ccmp manually using modprobe, but it doesn't get loaded automatically. Since the other module for TKIP encryption was loaded automatically, I wondered what mechanism controlled this. Judging from your response, it's hotplug.

Now that I understand that I can read more about how hotplug works and perhaps figure it out. It's probably just something that I'm doing wrong.

I haven't tried Dapper yet; I was waiting for the formal release, but perhaps I should try. Most of the features on my IBM X41T worked out-of-the-box using the current release of Kubuntu 5.10, but I'm still struggling with encrypted wireless and hibernation issues, but making some progress. Thanks again for your help.

Mark

---

### Post by GSBecker.de on 2006-05-03
Hi Mark,
you may want to add the module into /etc/modules for loading the module at boot-time.
Sebastian

---

