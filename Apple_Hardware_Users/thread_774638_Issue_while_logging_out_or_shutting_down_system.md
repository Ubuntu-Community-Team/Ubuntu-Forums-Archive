---
title: "Issue while logging out or shutting down system"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by AlainJLEB on 2008-04-29
Hi there,

I have upgraded my alumni iMac24 from 7.10 to 8.04 easily, but following this I am facing several issues:
[LIST]
[*]When logging off or shutting down system from KDE, I never get back the KDM screen or it never restarts/stops. I have to press the power button a few seconds to stop it brutaly. It seems there is someone else facing a similar iss - see [here]("http://ubuntuforums.org/showthread.php?t=770722") - but there is no extra information available. I have searched the xorg and kdm logs which look clean, as the syslog is as well. I'm using xorg with fglrx ATI extension.
[*]The keyboard mapping is not correct, but this is discussed in this [thread]("http://ubuntuforums.org/showthread.php?t=767246").
[/LIST]

Any help would be highly appreciated ... the most annoying thing is the first one, as the only way to log in as a different user is to ... reboot by removing the power supply :(

Thanks
Alain

BTW: is it normal to have the 2 following packages installed at the same time?
xorg-driver-fglrx
xserver-xorg-video-ati
Could they be the root cause of the issue?

---

### Post by macaholic on 2008-04-29
I'm pretty sure that is an ATI driver issue, one that was supposed to be fixed in 8-3, but I'm still ahving the same problem. You could try downloading the latest driver and building packages yourself, tutorial [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0"), but that always has its own risks.
P.S. Having the intel xorg installed will not affect things a bit, so don't worry about that.

---

### Post by cyberdork33 on 2008-04-29
> **AlainJLEB said:**
> When logging off or shutting down system from KDE, I never get back the KDM screen or it never restarts/stops. I have to press the power button a few seconds to stop it brutaly. It seems there is someone else facing a similar iss - see [here]("http://ubuntuforums.org/showthread.php?t=770722") - but there is no extra information available. I have searched the xorg and kdm logs which look clean, as the syslog is as well. I'm using xorg with fglrx ATI extension.
try killing atieventsd and then shutdown... I think it is related to that.
```
sudo killall atieventsd
```

> **AlainJLEB said:**
> BTW: is it normal to have the 2 following packages installed at the same time?
xorg-driver-fglrx
xserver-xorg-video-ati
Could they be the root cause of the issue?
Perfectly normal... the second package is the open ati driver that is part of Xorg... unfortunately it does not support your graphics card.

---

### Post by macaholic on 2008-04-29
> **cyberdork33 said:**
> try killing atieventsd and then shutdown... I think it is related to that.
```
sudo killall atieventsd
```


Yes cyberdork, you are correct, it is ati events daemon process not shutting down correctly. Killing the process works for shutting down properly, however,sometimes when you kill the process logging out or restarting X still fails.

---

### Post by AlainJLEB on 2008-04-30
> **cyberdork33 said:**
> try killing atieventsd and then shutdown... I think it is related to that.
```
sudo killall atieventsd
```


Perfectly normal... the second package is the open ati driver that is part of Xorg... unfortunately it does not support your graphics card.

Well, I have already tried that solution, but it does not solve that strange behavior; I have in fact remove the launch of atieventsd using ```
sudo /usr/sbin/update-rc.d -f atieventsd remove
```

Now, another question: if I want to update the driver following the advise from macaholic, should I remove something first?

---

### Post by cyberdork33 on 2008-04-30
check if envy is using the latest driver first... that is the easiest way to install later drivers.

---

### Post by AlainJLEB on 2008-04-30
> **cyberdork33 said:**
> check if envy is using the latest driver first... that is the easiest way to install later drivers.

I've just tried envy, which claims that latest version is 8.3 ... but nothing happens, I guess linked to this python error:
```
envyng-qt
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Driver ATI is selected
TESTING CONNECTION
OK: Connection is available
Applybutton clicked
Selected action is automatic
Selected driver is ATI
Save packages is 0
Build only is 0

python pulse.py ati
```

---

### Post by macaholic on 2008-04-30
Often times Envy will either not install the drivers properly, and usually isn't on the current version for a while. I would suggest installing them manually, it isn't that difficult.

---

### Post by cyberdork33 on 2008-04-30
> **macaholic said:**
> Often times Envy will either not install the drivers properly, and usually isn't on the current version for a while. I would suggest installing them manually, it isn't that difficult.
actually it usually is... several people have lots of problems with this.

here is the guide i usually attempt when doing this manually:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method)

---

### Post by russo.mic on 2008-05-01
This is related to a post I recently put up about this in Kubuntu, as Cyberdork's advice for this has helped me.

Russo

---

### Post by AlainJLEB on 2008-05-02
I have installed manually the latest version of the ATI drivers following this [procedure]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0").  The shutdown is now working fine, despite the fact that the display while shutting down is weird. It seems that synchronisation is not correct, but at least it is stopping fine.

The last point is that I'm still not able to switch to a different user. This seems to block the PC.

---

