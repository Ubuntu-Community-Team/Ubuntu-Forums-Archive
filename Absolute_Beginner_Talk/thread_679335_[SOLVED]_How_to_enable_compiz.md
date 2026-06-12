---
title: "[SOLVED] How to enable compiz?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by TRANQU111TY on 2008-01-26
I installed it from this post '[Huge List of the Best Open-Source Apps]("http://ubuntuforums.org/showthread.php?t=535260&highlight=libdvdread")' and this is what happens when I try to start it:
```

j@j-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

Nothing really happens after that. Help please :)

I have an ATI Radeon X1900XT with drivers installed.

---

### Post by LaRoza on 2008-01-26
What version of Ubuntu are you using?

Compiz is there by default in 7.10, and is in System->Preferences->Appearance and under the Visual Effects tab.

```

sudo aptitude install compizconfig-settings-manager

```

You might want to plugins for it too. Search in Synaptic.

---

### Post by TRANQU111TY on 2008-01-26
Thanks. When I select Extra it says says: **The Composite extension is not available**.

---

### Post by st33med on 2008-01-26
Ugh. Sorry if I am not contributing, but the ATI drivers are a mess. They do not work well with compiz. I think there is a thread somewhere in the forums, but, I don't know where.

---

### Post by TRANQU111TY on 2008-01-26
Thanks guys, it's OK I've got it working now. [http://ubuntuforums.org/showpost.php?p=3562227&postcount=10](http://ubuntuforums.org/showpost.php?p=3562227&postcount=10)

Basically
```

sudo gedit /etc/X11/xorg.conf
```

Put 1 instead of 0 in the last section so it looks like this:

```
EndSection
Section "Extensions"
Option "Composite" "1"
EndSection
```

```
sudo apt-get install xserver-xgl
```

Control-Alt-Backspace

Credit and thanks to maxxym! :)

---

### Post by st33med on 2008-01-26
Just make sure you mark this as solved!

---

### Post by Chutch on 2008-01-26
.

---

