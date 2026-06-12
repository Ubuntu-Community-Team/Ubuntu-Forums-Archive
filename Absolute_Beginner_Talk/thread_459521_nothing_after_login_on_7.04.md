---
title: "nothing after login on 7.04"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by mwilsonemt on 2007-05-30
I attempted to upgrade to 7.04 and my computer hung durring the install.  I had to do a hard reset and didn't get anyting with kurnel 2.6.17-11, so tried 2.6.17-11 safe mode with no luck.  I then tried 2.6.17-10 and was able to get back in and everything was working well.  I went to preform updates and everything loaded well.  upon restart, kurnel 2.6.20-15 had been loaded.  I tried booting ubuntu from every option I was given and was able to log in, but nothing happens after that.  I am still able to get into a cammand line, but I  don't know what I'm doing from there.  can someone please help me.  although i have been using ubuntu for about 6 mo., I have not done much other than the basics.

---

### Post by dbbolton on 2007-05-30
first, try this: go to the command line and type ```
sudo aptitude update
```
then ```
sudo aptitude upgrade
```
to make sure that all your packages are sound.

---

### Post by mwilsonemt on 2007-05-31
OK, so I tried both commands, both retrived some udates/upgrades, but I still have nothing after the login on the GUI.  I tried running them a second time for the hell of it and the upgrade returned a bunch of dependency problems while processing:
Acpid
ubuntu-desktop
acpi-support
powermanagement-interface
gnome-power-manager
gnome-session

---

### Post by dbbolton on 2007-05-31
ok, do this command:
```
aptitude dist-upgrade
```

---

### Post by mwilsonemt on 2007-05-31
Ok, I tried aptitude dist-upgrde and I now have a new kurnel, but I still only have a blank tan screen after I log in.  After compleating dist-upgrde, I still got the same error message about discrepancy problems while processing the same itims from before.

---

### Post by dbbolton on 2007-06-01
> **mwilsonemt said:**
> Ok, I tried aptitude dist-upgrde and I now have a new kurnel, but I still only have a blank tan screen after I log in.  After compleating dist-upgrde, I still got the same error message about discrepancy problems while processing the same itims from before.
ok. try to reinstall the packages that are giving you problems:

```
aptitude reinstall ubuntu-desktop
```

what it seems like to me, is that your system is working fine, but you might be having some kind of problem specific to the gnome session.

---

### Post by mwilsonemt on 2007-06-01
I tried to reinstall each package individualy and am still getting the same descrepancy problems error.  Should I just do a reinstall?

---

### Post by dbbolton on 2007-06-01
if you don't have anything to lose, go for it.

---

### Post by alan tait on 2007-06-07
Total newbie here, so don't trust me. I get the blank tan screen all the time, unless I hit Options>Change Session>Gnome, after which I get it SOMETIMES. Beats me. I'm on an HP pavilion with ATI radeon 9000, if it makes any difference.

---

