---
title: "Wireless on G4 PowerBook"
date: 2008-01-11
forum: Apple PPC Users
---

### Post by tedir on 2008-01-11
I have come this far; my wireless card finds all the networks around me, but when I set encryption and type password it will not connect.

The NetworkManager is trying to connect, but the lights just stay grey. Not even the light that is supposed to indicate that it has found the network is lit.

Anyone with the same problem, or have any idea on how to fix this?

Ted

---

### Post by guidop on 2008-01-11
If you _can_ connect _without_ encryption, your problem is probably due to the network-manager (or knetworkmanager) endian bug in the ppc build.

You can uninstall the network manager, and use a different program such as WICD for a work around.

See these threads:

[http://ubuntuforums.org/showthread.php?t=564866](http://ubuntuforums.org/showthread.php?t=564866)

[http://ubuntuforums.org/showthread.php?t=526901](http://ubuntuforums.org/showthread.php?t=526901)


If you are still running Edgy, as your signature indicates, I also suggest you upgrade to Feisty (not Gutsy) with backports, to have the most stuff working out of the box.  The only method of upgrading that worked for me was to edit my /etc/apt/sources.list file, replacing edgy with feisty, then running:
```

$ sudo apt-get update        # Verify no errors, problems usually are in sources.list file.
$ sudo apt-get dist-upgrade  # Also removes unneeded packages. Answer any config questions.
$ sudo apt-get -f install    # Check upgrade, in case there are additional packages.
$ sudo dpkg --configure -a   # In case additional packages need default configuration.

```

You can also use the tool at this link to generate a sources.list file:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)


If you have an older Powerbook with the ADB trackpad, take a look at this thread, too:
[http://ubuntuforums.org/showthread.php?t=380884](http://ubuntuforums.org/showthread.php?t=380884)

---

### Post by tedir on 2008-01-13
Thanks! I have actually upgraded to Feisty, but hadn't updated my signature.

Will try the WICD.

---

